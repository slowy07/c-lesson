## decode ways (medium)

**solution 1 DP**
```
dp[i] = 0
dp[i] += dp[i - 1]  if S[i] != '0'
dp[i] += dp[i - 2]  if i != 0 && S[i - 1] != '0' && (S[i - 1] - '0') * 10 + S[i] - '0' <= 26
```

```cpp
class Solution {
public:
  int numDecodings(string s) {
    int pre2 = 0, pre1 = 1;
    for (int i = 0; i < s.size() && pre1; ++i) {
      int cur = 0;
      if (s[i] != '0') cur += pre1;
      if (i != 0 && s[i - 1] != '0' && (s[i - 1] - '0') * 10 + s[i] - '0' <= 26)
        cur += pre2;
      pre2 = pre1;
      pre1 = cur;
    }
    return pre1;
  }
};
```
