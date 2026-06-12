---
title: "Monitor not showing anything for some minutes"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by ubuntu27 on 2008-06-05
Hello everyone, fellow Ubunteros and GNU/Linux users.
Its been a while since I asked a question here.

I been having a big problem for five months now.

Whenever I turn on the computer, nothing shows-up on the computer for at least three minutes or more.
I have to restart over and over again. Sometimes Out of luck, it shows in less than two minutes.

Today I had to restart five times. :(


I am dual-booting Windows XP Home Edition and Debian Sid. Since the screen doesn't show anything, I restart by using the keyboard ( Alt+F1, Control+Alt+Delete)

The Tower shows that it is in motion since the light is on&off constantly.



My computers Spec. are as follows:

CPU: Intel Celeron 2.60 GHz
RAM: 1 GB

In Windows XP's device manager it shows, Intel 82845G/GL/GE/PE/GV Graphic Controller

The monitor.. I don't know what monitor I have. It says "MAG" on the front. Its a 17 inch monitor though.

My computer is from Compaq

**Compaq S4200NX**


I'm thinking that the problems lies in my monitor...
But I don't wan to jump into any conclusions. 
What do you guys think?


Thank you in advance.

---

### Post by spiderbatdad on 2008-06-06
Have a look at your dmesg:```
dmesg > ~/Desktop/dmesg.txt
```See if the kernel suggests using some parameters to help with hardware detection.

Some people have reported drastic improvement simply by removing --quiet splash.

---

