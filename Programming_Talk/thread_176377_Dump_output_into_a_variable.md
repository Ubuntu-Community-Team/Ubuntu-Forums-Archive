---
title: "Dump output into a variable"
date: 2006-05-14
forum: Programming Talk
---

### Post by jaykup on 2006-05-14
How would I go about dumping output from a command into a variable

Something like x=`date` but I want the output of date stored as x,  not for the script to run "date" each time x is called.

I'm using bash.

---

### Post by louis_nichols on 2006-05-14
that IS the right way. If you do x=`date` and then echo $x you'll se that the time and date are always the same, which means date isn't run, but the value stored into x.

---

### Post by cgjones on 2006-05-14
```
x=$(date)
```

---

### Post by jaykup on 2006-05-14
You're right.  I made the script wrong :( errrrr

Thanks.

---

