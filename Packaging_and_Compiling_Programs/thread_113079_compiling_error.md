---
title: "compiling error"
date: 2006-01-05
forum: Packaging and Compiling Programs
---

### Post by nofx1510 on 2006-01-05
root@ubuntu:/home/hax/gtkmm/gtkmm-2.2.12# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

having trouble trying to get gtkmm-2.2.12 installed. Also i have this C compiler cannot cresate executables error when it try to compile other sources. Really need some help tryed to do sudo apt-get install gcc but i already have the newest version. Also when i try to install gtkmm threw synaptics i am missing some repos so if i could get the repos that would be great.

---

### Post by coredump on 2006-01-05
Could you try writing a very simple "hello, world" program and then compiling it, and see what happens?  Then, post a reply with any error messages that you get from that compilation step.

---

### Post by kairu0 on 2006-01-05
```
sudo apt-get install build-essential
```

And then try it again.

---

### Post by CONFIQ on 2006-01-07
hey, installing build-essential did help me.
Thank you :)

---

