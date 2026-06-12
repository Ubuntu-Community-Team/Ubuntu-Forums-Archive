---
title: "Segfault in libginac-1.4.so.0.0.3 with intel compilers"
date: 2009-03-06
forum: Packaging and Compiling Programs
---

### Post by Dougie187 on 2009-03-06
Hey Everyone,

Not sure if anyone else has ran into this issue, it is new for me. But anyways, I was just going to compile some basic fortran code that I need for my research (btw, it compiles fine with gfortran, and it compiled with ifort about a month and a half ago) and I get this message.

```
ifort: error #10106: Fatal error in /opt/intel/Compiler/11.0/081/bin/ia32/fortcom, terminated by segmentation violation
```

Obviously this is with version 11.081 of the intel compilers. 

Now, in syslog and dmesg after trying to compile I get the following message

dmesg
```
fortcom[28185]: segfault at b7d0d000 ip b7dcf342 sp bfca9ac0 error 4 in libginac-1.4.so.0.0.3[b7d21000+265000]
```

syslog
```
Mar  6 15:35:26 douglt kernel: [27189.089676] fortcom[28239]: segfault at b7d5b000 ip b7e1d342 sp bfff9610 error 4 in libginac-1.4.so.0.0.3[b7d6f000+265000]
```

These last two issues make me thing that its not a problem with the intel compilers, but its with libginac... Also I tried changing my LD_PRELOAD variable to different versions of libginac but it didn't change anything.

So any help would be much appreciated. Let me know if you need anymore information.

---

### Post by Dougie187 on 2009-03-06
Nevermind... this is kind of a stupid problem and solutions... but for some reason it seems having

export LD_PRELOAD="/usr/lib/libginac-1.4.so.0"

in my bashrc broke it. Granted I needed this to use the symbolic kit for octave.

---

