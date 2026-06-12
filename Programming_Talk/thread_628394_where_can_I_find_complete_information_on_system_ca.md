---
title: "where can I find complete information on system calls for Linux 2.6.23"
date: 2007-12-01
forum: Programming Talk
---

### Post by RaistlinU on 2007-12-01
I am trying to do some experiment on system call. I want to find a complete system call table, listing the data type of arguments, return value for each system call on Linux 2.6.23. I can only find some documents on 2.2 or 2.5. Could somebody give me some information on this? Thanks.:popcorn:

---

### Post by iTony on 2008-09-11
I am also interested in how to do that since I couldn't find the system call tables where it normally is and anywhere near. I'll keep looking too

---

### Post by dwhitney67 on 2008-09-11
This is one of the sites that came up when I Googled for "man page":
[http://linux.die.net/man/](http://linux.die.net/man/)

Does this help?

---

### Post by slavik on 2008-09-11
/usr/include/asm/unistd.h has a table of syscalls.

---

