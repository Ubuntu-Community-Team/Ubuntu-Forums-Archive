---
title: "error compiling on a remote server from ubuntu"
date: 2010-11-24
forum: Packaging and Compiling Programs
---

### Post by kpthecoder on 2010-11-24
Hi,  I am trying to compile a program on remote unix server to which i am connected using ssh.
for a sample file when i try running the command :

[rohan] cdn_proj > gcc sample.c

I am getting the error as follows:

Undefined                                      first referenced
 symbol                                                in file
getch                                                    /var/tmp//cccJvefm.o
prinf                                                     /var/tmp//cccJvefm.o
clrscr                                                   /var/tmp//cccJvefm.o
ld: fatal: Symbol referencing errors. No output written to a.out
collect2: ld returned 1 exit status
[rohan] cdn_proj>gcc sample.c

It would be grateful if some one could help.
I have tried using cc, g++ but got the same error.
Thanks

---

