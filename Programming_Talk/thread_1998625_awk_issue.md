---
title: "awk issue"
date: 2012-06-07
forum: Programming Talk
---

### Post by Drenriza on 2012-06-07
Hi guys.

I have a for loop where i have the following code
```
password=$(awk 'NR==$count' 'test' |awk '{print $2}')
```

to grab a specific part of a line in each line. By hand this works fine and dandy.
But when i echo the $password in the for loop it's blank.

Has this something to do with you cannot use the $count inside the awk statement?

Kind regards.

Solved

---

