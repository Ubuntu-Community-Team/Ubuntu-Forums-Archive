---
title: "valgrind fatal error"
date: 2012-09-10
forum: Programming Talk
---

### Post by snowlizard31 on 2012-09-10
I've just now installed valgrind on ubuntu  I've installed valgrind on my mac osx before with no errors but I've got some on ubuntu can someone help me figure out whats wrong. How do I get a long term solution I don't understand what the 2nd solution do I have to replace a dynamic linker?

```


snowlizard@snowlizard-iMac:~/programming$ valgrind ./ex2
==3541== Memcheck, a memory error detector
==3541== Copyright (C) 2002-2012, and GNU GPL'd, by Julian Seward et al.
==3541== Using Valgrind-3.8.0 and LibVEX; rerun with -h for copyright info
==3541== Command: ./ex2
==3541== 

valgrind:  Fatal error at startup: a function redirection
valgrind:  which is mandatory for this platform-tool combination
valgrind:  cannot be set up.  Details of the redirection are:
valgrind:  
valgrind:  A must-be-redirected function
valgrind:  whose name matches the pattern:      strlen
valgrind:  in an object with soname matching:   ld-linux-x86-64.so.2
valgrind:  was not found whilst processing
valgrind:  symbols from the object with soname: ld-linux-x86-64.so.2
valgrind:  
valgrind:  Possible fixes: (1, short term): install glibc's debuginfo
valgrind:  package on this machine.  (2, longer term): ask the packagers
valgrind:  for your Linux distribution to please in future ship a non-
valgrind:  stripped ld.so (or whatever the dynamic linker .so is called)
valgrind:  that exports the above-named function using the standard
valgrind:  calling conventions for this platform.  The package you need
valgrind:  to install for fix (1) is called
valgrind:  
valgrind:    On Debian, Ubuntu:                 libc6-dbg
valgrind:    On SuSE, openSuSE, Fedora, RHEL:   glibc-debuginfo
valgrind:  
valgrind:  Cannot continue -- exiting now.  Sorry.







```

---

### Post by conradin on 2012-09-10
try giving the absolute path to your program.
[https://wiki.ubuntu.com/Valgrind](https://wiki.ubuntu.com/Valgrind)

---

