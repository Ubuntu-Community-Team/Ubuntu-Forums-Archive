---
title: "bash : string variable replacement"
date: 2007-01-09
forum: Programming Talk
---

### Post by dens57 on 2007-01-09
Hello,

I have this :

VAR2='test2
VAR1='test1 $VAR2 test3'
echo $VAR1

the result is : test1 $VAR2 test3

but I would like to have : test1 test2 test3

I'm not a bash expert, it will be really great !

thanks

---

### Post by gpolo on 2007-01-09
you need to use " " instead of ' '

---

### Post by Tomosaur on 2007-01-09
Try this instead:
VAR2="test2"
VAR1="test1 $VAR2 test3"
echo $VAR1

The single quotation tells Bash to leave it alone, so it won't use the variable, it'll treat the variable name as a string.

---

### Post by dens57 on 2007-01-09
Thanks a lot, it works fine.

---

