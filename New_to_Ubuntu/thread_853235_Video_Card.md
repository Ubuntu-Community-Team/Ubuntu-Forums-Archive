---
title: "Video Card"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by jimi_hendrix on 2008-07-08
:guitar:

hi all

recently ive been experementing with some free games to run on linux like
battle for wesnoth and nexuiz

wesnoth works perfectly, but when i try to run nexuiz and sauerbraten, i get green blue purple and pink fuzzy glitchy graphics

i am using a at mobility radeon hd 3470 card

i have NOT installed a linux driver for the card yet...may this be the problem?

help please

---

### Post by damis648 on 2008-07-08
Try System>Administration>Hardware Drivers and check the box next to your card?

---

### Post by jimi_hendrix on 2008-07-08
ok and 1 more thing...how do i know if i have a 64 bit OS or a 32 one?

---

### Post by damis648 on 2008-07-08
Run
```
uname -a
```
in terminal. You will receive an output like:
```
Linux damian-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 **i686** GNU/Linux
```
The i686 means 32-bit.. so would i368, i586, etc everything starting with "i". Anything else, 64-bit.

---

### Post by jimi_hendrix on 2008-07-08
i got 

x86_64 GNU/Linux

so thats 64 bit?

---

### Post by damis648 on 2008-07-08
Yep.

---

### Post by arloth on 2008-07-08
Yes, as damis648 said, make sure you're using the accelerated video driver.  A good way to check is to run ```
glxinfo | grep "direct"
``` in a terminal window and make sure it says yes.  If it says no, then your driver likely isn't loaded properly.

---

