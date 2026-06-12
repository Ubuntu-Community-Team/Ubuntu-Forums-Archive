---
title: "[php]preg replace and round function"
date: 2009-06-28
forum: Programming Talk
---

### Post by wertyuiop408 on 2009-06-28
i finally found how to do functions in preg replace using the e modifier, but when using the round fucntion i find that its treating a decimal point not as numeric and makes it a 0.

e.g 6.7, the preg replace would make it 607

```
$Text = preg_replace("/(.+?)/e",
             "''.round('\\1').''",
             $Text);
```

---

### Post by wertyuiop408 on 2009-06-28
bump

---

### Post by Reiger on 2009-06-28
Your matching pattern isn't greedy enough. preg_replace() finds exactly 3 matches for the input string '6.7' with your pattern: namely '6', '.', and '7'.

---

