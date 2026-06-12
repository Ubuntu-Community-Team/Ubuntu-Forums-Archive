---
title: "Compilation problems"
date: 2008-06-27
forum: Packaging and Compiling Programs
---

### Post by Thesuperchang on 2008-06-27
Hello, I've finally made the switch to Ubuntu. So far so good except for the fact I don't know how to compile my programs.:( It was working for me for about two attempts will not work anymore.

[http://img50.imageshack.us/img50/1558/screenshotir2.png](http://img50.imageshack.us/img50/1558/screenshotir2.png)

Any suggestions?

---

### Post by Thesuperchang on 2008-06-27
Never mind, I used this command;
sudo -s ./make.gcc
The command executes but apparently I've got errors in my makefile?

---

### Post by WW on 2008-06-27
> **Thesuperchang said:**
> Never mind, I used this command;
sudo -s ./make.gcc
The command executes but apparently I've got errors in my makefile?

The file **make.gcc** is not a program that you run.  It is a file that you give to the **make** command.  Try this:
```

make -f make.gcc

```
You should not need sudo to do this.

---

