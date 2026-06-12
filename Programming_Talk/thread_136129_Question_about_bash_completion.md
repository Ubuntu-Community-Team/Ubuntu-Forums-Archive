---
title: "Question about bash completion"
date: 2006-02-25
forum: Programming Talk
---

### Post by Guest1234 on 2006-02-25
In my office I have tcsh and if for example I typed the following commands(in this order):

find . --max-depth 1 -type f -exec rm \{} \;
ls programming

and then I type:
"fi" and then the up key then it will complete to "find . --max-depth 1 -type f -exec rm \{} \;"

on bash in my ubuntu if I type the "fi" and then the up key it will complete me to "ls programming" since its the most recent command.

How do I configure my bash to act like tcsh in this matter?

---

### Post by kabus on 2006-02-25
add this to your ~/.inputrc : 

```
"\e[A": history-search-backward
"\e[B": history-search-forward
```

---

### Post by jerome bettis on 2006-02-25
if you type !xyz it will do the most recent command that starts with xyz

---

### Post by Guest1234 on 2006-03-03
Thanks guys it worked :)

---

