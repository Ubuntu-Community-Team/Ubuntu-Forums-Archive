---
title: "Problems using the dbm database in C"
date: 2006-10-14
forum: Programming Talk
---

### Post by theDentist on 2006-10-14
I am trying to use the dbm database (gdbm and ndbm)and wrote a simple program to see if I was successful in defining the data types and functions with the correct headers and libraries.  I successfully defined the DBM and datum types using the gdbm-ndbm.h header ( I am using Ubuntu )but get an undefined error when I code the functions, like for example, dbm_open().  I would have thought the functions would have their prototypes in the same header?  Can anyone give me advice concerning headers that I need, or any libraries when I run the compiler.   :( 

Peter

---

### Post by Woei on 2006-10-16
> **theDentist said:**
> I am trying to use the dbm database (gdbm and ndbm)and wrote a simple program to see if I was successful in defining the data types and functions with the correct headers and libraries.  I successfully defined the DBM and datum types using the gdbm-ndbm.h header ( I am using Ubuntu )but get an undefined error when I code the functions, like for example, dbm_open().  I would have thought the functions would have their prototypes in the same header?  Can anyone give me advice concerning headers that I need, or any libraries when I run the compiler.   :( 


Well, you're not giving us much to go on apart from an 'undefined' error. You really should've included gcc's error output. libgdbm is quite a small library, and it comes with a pretty good tutorial:
```

apt-get install libgdbm-dev pinfo
pinfo gdbm

```

What you're probably missing is **-l gdbm** as a switch to your gcc invocation. Something like ```
gcc foo.c -o bar -Wall -pedantic -lgdbm
``` should do. Basically, you have to tell gcc (or rather, the linker invoked by gcc) explicitly to link the gdbm library with the object code from your program. See *man ld* for a discussion.

---

