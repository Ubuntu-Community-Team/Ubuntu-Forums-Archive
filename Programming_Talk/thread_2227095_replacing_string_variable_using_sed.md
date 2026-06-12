---
title: "replacing string variable using sed"
date: 2014-05-30
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-30
Hello,
I've been trying to replace a string with another using sed, and still haven't been able to get it to work, especially since it contains shell variables.

I googled around a bit, and the common fix seems to be, to replace single quotes with double. I've tried this but still doesn't work

```

IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ cat replace.sh
word=mynewjavapath
original="export JAVA_HOME=/usr/lib/j2sdk1.5-sun"


sed "s/$original/$word/g" test.txt

```

This is the output I get
```
IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ ./replace.sh 
sed: -e expression #1, char 25: unknown option to `s'

```

---

### Post by spjackson on 2014-05-30
Your problem is that $original evaluates to a string containing / and the same character is used to delimit the strings, with resulting confusion. What I would do in this case is:
```
sed "s#$original#$word#g" test.txt
```
There may be a more general solution. (This case would fail if one of the strings contained #.)

---

### Post by IAMTubby on 2014-05-30
> **spjackson said:**
> Your problem is that $original evaluates to a string containing / and the same character is used to delimit the strings, with resulting confusion. What I would do in this case is:
```
sed "s#$original#$word#g" test.txt
```
There may be a more general solution. (This case would fail if one of the strings contained #.)
Thanks spjackson.
Worked :)

---

