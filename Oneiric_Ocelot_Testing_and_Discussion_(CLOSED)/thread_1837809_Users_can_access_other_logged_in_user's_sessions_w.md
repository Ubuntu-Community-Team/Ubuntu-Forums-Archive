---
title: "Users can access other logged in user's sessions w/out password"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-09-02
I think this is really odd that any user, inc. a guest,  can go to any other logged in user's session directly without having to enter that user's password. (by clicking on that user's name in the user menu

With the exception of guest I see the same in natty so maybe that's the way intended but considering the "switch from ..." does require a password by going to login screen it seems wrong to allow direct access.

(there may be a graphical glitch or 2, usually temp, otherwise one can do whatever they wish in the other user's session.

---

### Post by lucazade on 2011-09-02
speechless :o
that usermenu born bad

---

### Post by mc4man on 2011-09-02
I have a bug on it, though because this is also allowed in natty (exception guest) thought maybe invalid
[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/837490](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/837490)

Additionally, other than some current graphical issues (nvidia) w/ the lock screen, it also can be bypassed

---

### Post by dino99 on 2011-09-02
have run valgrind about indicator-session (gtk-logout-helper) and got lot of:

 object doesn't have a symbol table

and other: CRC mismatch

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/839371](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/839371)

---

