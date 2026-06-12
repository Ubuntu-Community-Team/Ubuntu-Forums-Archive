---
title: "how to stop root logging on at startup (linaro 12.11)"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by cutSn8 on 2013-02-12
New to linux, using Linaro Ubuntu 12.11 on an Odroidx2 (see [http://odroid.foros-phpbb.com/t1999-linaro-ubuntu-1211-for-odroid-x2](http://odroid.foros-phpbb.com/t1999-linaro-ubuntu-1211-for-odroid-x2)) - like Raspberry Pi and just as fun.  When I boot, the systems starts with me /my non-root user account ('linaro') logged in to the  the graphical user interface (is it unity?), and the root user is also logged in to two shell consoles (when I start terminal and type 'who' it shows root logged in at two consoles, as well as me 'linaro').  I would like to change the start up so I begin in a simpler shell (bash?, not the gui) and no-one is logged on yet - is this possible?  (Why? Well I don't want root logged in on my system unless it's me doing it, and to play around with remotely logging on to the device it may help if the gui isn't loaded). 

Thanks muchly for any help

Ps my odroidx2 has an emmc card, and I gather that there is some  software installed on that device which I know nothing about, up to and including not knowing if it relates at all to the above.  I bought the card with the board, android 4.x preinstalled, and installed the 25-Jan-2013 version of linaro ubuntu to a sd card following the directions set out at the above url / related links.

---

### Post by CharlesA on 2013-02-12
Can you post the output of who?

---

### Post by cutSn8 on 2013-02-12
```
linaro@linaro-ubuntu-desktop:~$ who
root     ttySAC1      2013-02-12 04:05
root     tty1         2013-02-12 04:05
linaro   tty7         2013-02-12 04:05
linaro   pts/0        2013-02-12 06:07 (:0.0)
linaro@linaro-ubuntu-desktop:~$
```

---

### Post by CharlesA on 2013-02-12
ttySAC1 looks to be an Android boot console, at least according to [this]("http://www.kernelconcepts.de/~arne/odroidx/readme.txt").

tty1 is the first TTY, you should be able to access it by hitting ctrl + alt +f1 on your keyboard. The rest looks normal.

---

### Post by cutSn8 on 2013-02-12
Thanks, when I press alt-ctrl-F1 then screen appears to freeze (cant move mouse or anything), no screen/console appears; alt-ctrl-F7 returns me to linaro's gui.

---

### Post by CharlesA on 2013-02-12
It could be something to do with the way the OS is setup as both those root logins are at the same time as your GUI login.

Maybe someone with experience with this distro can help you out, as I have never heard of it before.

---

