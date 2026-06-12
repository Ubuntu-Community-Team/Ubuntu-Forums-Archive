---
title: "need some help with x-org"
date: 2011-08-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-08-13
okay i know i have the wrong setting. when i shutdown or reboot the screen display shrinks to a 1/4 of my monitor. how can i fix. would appreciate any help their are some smart people always on the testing forms. tks in advance

---

### Post by Harry33 on 2011-08-14
Firstly you could check whether you have this file installed:
/etc/X11/xorg.conf

It is basically not needed anymore, so you could rename it to xorg.backup and then try to reboot.

---

### Post by cariboo on 2011-08-14
I have a system running dual monitors that does the same thing, but only on the left hand monitor, the right side one displays the normal sized screen on shutdown.

---

### Post by lucazade on 2011-08-14
Does this happen only when plymouth splashscreen is enabled?
try to see if it is related to plymouth by removing "splash" from grub kernel params at boot time.

---

