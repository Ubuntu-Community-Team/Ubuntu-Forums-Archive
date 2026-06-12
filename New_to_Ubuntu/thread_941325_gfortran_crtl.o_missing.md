---
title: "gfortran crtl.o missing"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by TideMan on 2008-10-08
I'm not sure if this is a Ubuntu or a gfortran problem.
I've installed gfortran and I can compile just fine, but when I come to link, I get this message:
```
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

```
I can't find crtl.o anywhere.
Can anyone help?

---

### Post by TideMan on 2008-10-08
I had used the method described here:
[wiki]("http://ttp://gcc.gnu.org/wiki/GFortranBinaries32Linux")
which involved downloading a .bz2 file and unpacking.

Instead, I should have used the Synaptic Package Manager described here:
[//https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")
which sorts out the dependent libraries etc for you.

Lesson learned.....

---

