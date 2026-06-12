---
title: "Obtain lock"
date: 2006-12-31
forum: Programming Talk
---

### Post by Kiwinote on 2006-12-31
Hello,
I am writing a program which uses commands related to apt. I would like to be able to obtain the lock in /var/lib/dpkg/lock so that the user can't damage their system by running more than one apt program at once. Does anyone have ideas on how to do this?
Thanks,
Kiwinote

---

### Post by Kiwinote on 2006-12-31
Ideas?

---

### Post by bernied on 2006-12-31
It looks like you just need to have the file open.

---

### Post by bernied on 2006-12-31
...but I'm a bit dumb on how you'd do this - would depend on what langugae you're writing in.

It looks like you just need the lsof command to show it as being in use, though
```
root@shinym:/var/lib/dpkg# lsof /var/lib/dpkg/lock
COMMAND    PID USER   FD   TYPE DEVICE SIZE    NODE NAME
adept_man 6789 root   10uW  REG   3,65    0 1157275 /var/lib/dpkg/lock
```

---

### Post by Kiwinote on 2006-12-31
Thanks for the idea, but allas:
```
kiwinote@Kiwinote:~$  sudo lsof /var/lib/dpkg/lock
COMMAND   PID USER   FD   TYPE DEVICE SIZE   NODE NAME
<myprog>5476 root    4r   REG    3,4    0 289173 /var/lib/dpkg/lock
synaptic    5629 root    7uW  REG    3,4    0 289173 /var/lib/dpkg/lock
```
Any other ideas? Would it have to do with the difference in FD, whatever that is? I really can't work it out, the file is always empty and even this doesn't work :confused: 

BTW I'm writing in c++ and used the following code to open the file:
```
fstream lock("/var/lib/dpkg/lock",ios::in);
lock.close();
```

---

### Post by bernied on 2006-12-31
FD=File Descriptor
From man lsof

not that that will necessarily help very much

---

