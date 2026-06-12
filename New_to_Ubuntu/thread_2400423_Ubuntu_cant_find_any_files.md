---
title: "Ubuntu cant find any files"
date: 2018-09-05
forum: New to Ubuntu
---

### Post by jimmyjojr on 2018-09-05
Hey all I'm super new to ubuntu and need some help

whenever i try to locate any files i get the "no such file or directory exists" error

even trying cd Desktop returns this error.

any help would be greatly appreicated

---

### Post by &amp;KyT$0P# on 2018-09-05
What method of locating files are you trying to use?

---

### Post by jimmyjojr on 2018-09-05
Ive been using the cd <file/directory here>

---

### Post by &amp;KyT$0P# on 2018-09-05
Please post the output from running each of these commands in the Terminal where the cd command fails -
```
pwd
ls -la
```

---

### Post by jimmyjojr on 2018-09-05
pwd outputs:

/home/jimmyjojr

ls -la outputs:

total 8
drwxr-xr-x 0 jimmyjojr jimmyjojr  512 Sep  5 21:59 .
drwxr-xr-x 0 root      root       512 Sep  5 21:56 ..
-rw-r--r-- 1 jimmyjojr jimmyjojr  220 Sep  5 21:56 .bash_logout
-rw-r--r-- 1 jimmyjojr jimmyjojr 3771 Sep  5 21:56 .bashrc
-rw-r--r-- 1 jimmyjojr jimmyjojr  807 Sep  5 21:56 .profile
-rw-r--r-- 1 jimmyjojr jimmyjojr    0 Sep  5 21:59 .sudo_as_admin_successful

---

### Post by &amp;KyT$0P# on 2018-09-05
[FONT=Courier New]cd Desktop[/FONT] is failing because you don't have a Desktop folder in your home folder.  In fact you don't have any folders inside your home folder.

If you haven't lost any data that is supposed to be there, you could just create the folders you want.

---

### Post by sporksrule on 2018-09-05
If it is a newly created user and you are using the GUI, logout and log back in, the missing folders might be automatically generated.

---

