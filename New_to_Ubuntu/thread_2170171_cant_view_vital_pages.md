---
title: "cant view vital pages"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by mikel2 on 2013-08-25
hey guys im  reading the info pages about system calls and in the beginning of the page they say "For a list of the Linux system calls, see syscalls(2)." well i typed that
and get command not found error what should i do as well as other commands like :"errno"

---

### Post by TheFu on 2013-08-25
**$ man man**
That will explain everything.  There are many subtle ideas in man pages, so study that carefully to get the most out of the "man" manpage.  You might want to use "**apropos**" when you aren't certain which command to use - it searches all manpages.

**man syscalls** will let you see the manpage for syscalls.
"info pages" where created by the emacs guys who had ideas that man pages weren't as clear. Time has proven they were wrong, IMHO. 99% of all Linux commands are in the man pages. 1% use info pages.

BTW, reading man pages should be taught on the first day of using Linux.  The amount of information contained in the man pages is unbelievable. It does take a little time to learn to read them, but once you do, no command on any unix system anywhere in the world will be hard again.

---

### Post by stinkeye on 2013-08-25
Install man2html. Allows you to browse and search man pages in your web browser.
```
sudo apt-get install man2html
```

Once installed, goto and bookmark this address in your web browser....
```
http://localhost/cgi-bin/man/man2html
```

---

### Post by coldraven on 2013-08-25
Or view online
[http://linux.die.net/man/2/syscalls](http://linux.die.net/man/2/syscalls)

---

### Post by TheFu on 2013-08-25
> **coldraven said:**
> Or view online
[http://linux.die.net/man/2/syscalls](http://linux.die.net/man/2/syscalls)

or type "**man syscalls**" into any search engine.
Of course, any man page or other help may NOT be for the specific system you are on, unless it is the actual man page ON THE SYSTEM.

---

### Post by Impavidus on 2013-08-26
The number in brackets (the 2 in syscalls(2)) refers to the section where the man page can be found. Some pages are present in multiple sections, and by default you'll get the first. For example```
man printf
man -s1 printf
```both give the man page for the shell command **printf** in section 1, whilst```
man -s3 printf
``` gives the man page for the C function **printf()** in section 3.

---

