---
title: "Can't install G95 compiler on LUBUNTU or XUBUNTU"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by ramsesny on 2013-06-09
Hi everyone.

Whether I use my Lubuntu 13.04 (Raring Ringtail) or Xubunto 12.10 (Quantal Quetzal) virtual machine installation, I get the same problem when I try using my g95 compiler ([http://ftp.g95.org/g95-x86-linux.tgz](http://ftp.g95.org/g95-x86-linux.tgz))...

The error is:

**ld: cannot find crt1.o: No such file or directory**
**ld: cannot find crti.o: No such file or directory**

I am not sure if this means that those files are missing, can't be found because the path is wrong, or something else is happening?  And then, I will need help in resolving this issue. 
Thank you very much.

---

### Post by steeldriver on 2013-06-09
They should be in either

```

$ find /usr -name crt?.o
/usr/lib/i386-linux-gnu/crtn.o
/usr/lib/i386-linux-gnu/crti.o
/usr/lib/i386-linux-gnu/crt1.o

```
for 32-bit systems or
```

$ find /usr -name crt?.o
/usr/lib/x86_64-linux-gnu/crt1.o
/usr/lib/x86_64-linux-gnu/crtn.o
/usr/lib/x86_64-linux-gnu/crti.o

```

for 64-bit systems - in either case they are provided by the libc6-dev package, I think

Is there any particular reason you can't use the standard gfortran compiler?

---

### Post by ramsesny on 2013-06-09
Ok, thanks! Yes, I do have the crt?.o files in the /usr/lib/i386-linux-gnu/ directory.

Is the problem then that the g95 compiler is not finding the correct path to those files? How would I go about remedying that? I imagine I may have to tamper with environmental variables although I am not very familiar with those yet.

I prefer to use g95 on my LINUX guest because it is the same compiler I use on my Windows host. That way I avoid compiler compatibility issues.

---

### Post by steeldriver on 2013-06-09
Well I think the problem fundamentally is that the *binary* tarball of g95 is built against gcc 4.0.x which expects to find those files somewhere else (the path is likely built in when gcc is compiled)

You could try setting the gcc LIBRARY_PATH variable when you invoke it  - for example

```
LIBRARY_PATH=/usr/lib/i386-linux-gnu/ bin/i686-pc-linux-gnu-g95 helloworld.f90
```

or

```

export LIBRARY_PATH=/usr/lib/i386-linux-gnu/ 

bin/i686-pc-linux-gnu-g95 helloworld.f90

```

---

### Post by ramsesny on 2013-06-10
Thank you Steeldriver. That worked!

---

