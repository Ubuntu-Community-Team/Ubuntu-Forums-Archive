---
title: "[SOLVED] [python]Best way to get string after certain characters?"
date: 2008-05-28
forum: Programming Talk
---

### Post by days_of_ruin on 2008-05-28
```
IconTheme=Human
```
What would be the best way to get whatever is past the right most "="?

---

### Post by Lau_of_DK on 2008-05-28
> **days_of_ruin said:**
> ```
IconTheme=Human
```
What would be the best way to get whatever is past the right most "="?

How about

```


line.split("=")[1]


```

Edit: If line contains "description=value", then .split("=") will break it up into to strings, line[0] which contains everything before "=" and line[1] which contains everything after "=", you can split with any character you want.

/Lau

---

### Post by days_of_ruin on 2008-05-28
Thanks!I knew there had to be a simple way to do this.
:guitar:

---

