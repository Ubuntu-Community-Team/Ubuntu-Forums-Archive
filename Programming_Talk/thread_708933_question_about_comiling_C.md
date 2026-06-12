---
title: "question about comiling C"
date: 2008-02-26
forum: Programming Talk
---

### Post by thungmail on 2008-02-26
hi
I am totally new to Ubuntu. I tried to compile C code and i got the message:
tuan@tuan-laptop:~/Desktop/C$ cc -o hello hello.c
/usr/bin/ld: cannot open output file hello: Permission denied
collect2: ld returned 1 exit status
tuan@tuan-laptop:~/Desktop/C$ 
Can somebody tell me what it said and how to fix the problem
Tuan

---

### Post by LaRoza on 2008-02-26
See the sticky, which has a link for this.

---

### Post by thungmail on 2008-02-27
sorry i am totally lost

---

### Post by dwhitney67 on 2008-02-27
Although highly unlikely, my guess is that you do not have permissions to create a file (in this case, the 'hello' executable) in the directory where you are operating in.

Using the following command, make sure that your 'C' directory has the appropriate permissions that allow you to create new files within it.
```
$ ls -l ~/Desktop
```

The output should look something like this (for the 'C' directory):
```
drwxr-xr-x 2 tuan tuan 4096 yyyy-mm-dd hh:mm C
```

If this is not the case, with respect to the 'drwxr-xr-x', then fix the permissions using this command:
```
$ chmod 755 ~/Desktop/C
```

P.S.  I assume that you have installed onto your system the C and C++ compiler/linker.  If not, then run this command:
```
$ sudo apt-get build-essential manpages-dev
```

---

