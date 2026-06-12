---
title: "[SOLVED] cannot gain root access anylonger 0.o"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by icecloud on 2008-08-19
ok so i installed some things through my terminal and it allowed me to put in my password and get root access; well now when i'm trying to do something else and type su to gain root access and type in my password it sits there for a second and then says incorrect password....but i can login to my pc and everything....and i know i havent typed it wrong 12 times. anyone know whats going on?

---

### Post by eye208 on 2008-08-19
root doesn't have a password in Ubuntu. Type "sudo su" and use your normal user password instead.

---

### Post by DGortze380 on 2008-08-19
> **icecloud said:**
> ok so i installed some things through my terminal and it allowed me to put in my password and get root access; well now when i'm trying to do something else and type su to gain root access and type in my password it sits there for a second and then says incorrect password....but i can login to my pc and everything....and i know i havent typed it wrong 12 times. anyone know whats going on?

the root account is disabled by deafult in ubuntu. It is possible to enable it, but it is isn't support and I can't tell you how here.

use the sudo command for what you want to do.

---

### Post by Separ on 2008-08-19
"sudo su" works fine but if you want to use "su" then you could always type ```
sudo passwd
``` and change the password that way.

---

### Post by icecloud on 2008-08-19
i used sudo su and no problems from there so i'll go with that but thanx for the quick responses guys or gals >:?)

---

### Post by alienexplorers on 2008-08-19
first question are you sure your caps lock is not on?
Second question, did you run any programs that might have reset your password?

---

