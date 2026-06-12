---
title: "I have some Problem in the instalation for qmail"
date: 2005-12-10
forum: Repositories &amp; Backports
---

### Post by jguerra1977 on 2005-12-10
Helo my name is Joel and i am a new user in the linux world.

I try to compile qmail like step by step qmail but i receive a error from my server and need to know if somebody here can help me.

This is error mesage than i receive from the server.

root@ubuntu:/usr/local/src/qmail/qmail-1.03# make setup check
./load auto-str substdio.a error.a str.a 
substdio.a(substdo.o): En la funciÃ³n `allwrite':
substdo.c:(.text+0x36): referencia a `errno' sin definir
collect2: ld devolviÃ³ el estado de salida 1
make: *** [auto-str] Error 1
root@ubuntu:/usr/local/src/qmail/qmail-1.03# 

If someone want to write me please send me e-mail to [email]linux@tcarrier.net[/email]

---

### Post by RHAnthony on 2008-04-29
I am getting this same error, after doing the apt-get install build _essentials command that everyone's recommended.

Any other thoughts from the more experienced guys out there?

Are there no pre-compiled packages for qmail out there?

---

