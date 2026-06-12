---
title: "GCC #include (.h)  files"
date: 2008-02-04
forum: Programming Talk
---

### Post by novice36 on 2008-02-04
Where can I get a list of the "#include header (.h)" files for GCC with brief descriptions. I already have a list in my file system. What I need are brief descriptions of what they are used for. Particularly - for BIOS interrupts and LINUX OS  interrupts.

---

### Post by amingv on 2008-02-04
Try these:

In C:

[http://en.wikipedia.org/wiki/Category:C_headers](http://en.wikipedia.org/wiki/Category:C_headers)

In C and C++:

[http://everything2.com/index.pl?node_id=954272](http://everything2.com/index.pl?node_id=954272)

Of course, that's not all of the headers... If you have a list of some others, I'm sure you can find information on them on Google.

Also, next time post in the programming forums.

---

### Post by nfm on 2008-02-07
Hi,
GNU C Library is an excellent source of standard library functions, [http://www.gnu.org/software/libc/manual/](http://www.gnu.org/software/libc/manual/)
To make use of any Linux functions look into Linux system calls.
In order to use BIOS functions, you will need to know the memory address of a particular BIOS function and do some bit-wise operations.
"Linux System Programming" by O"Reilly is an excellent book for system and library calls/functions.
I never got any BIOS functions/interrupts to work, I didn't find any manuals or documentations explaining how it's done. I know that some of the material is covered in embedded programming books.

---

