---
title: "Freecom DVB-T not able to tune channels under ubuntu 8.10"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by DominicF on 2008-11-29
Hi,

I just made (another) fresh install of ubuntu 8.10 with the aim to setup a new Mythtv box.  I'm using the Freecom DVB-T stick with the id  "14aa:0221 AVerMedia (again) or C&E AVermedia DVBT Tuner Dongle".  I've had this working before under ubuntu 8.04 and 7.10.

The hardware gets recognised (amber light appears) but I'm not able to tune into channels using the application kaffeine.  Durring tuning in Kaffeine the green light flashes (on the DVB stick) but there's no signal lock and no channels are detected.

Comparing the results of "lsusb" and "dmesg | grep dvb" of my existing 7.10 system and the new 8.10 system the outputs are the same.

I need some advise how to debug this issue.

---

### Post by DominicF on 2008-12-03
I gave-up on the Freecom DVB-T USB stick and purchased a Nova-T 500 PCI card - this works great.

---

### Post by philinux on 2008-12-03
According to post #5 it should work but driver needs installing. However he doesn't explain how he did this.
[http://ubuntuforums.org/showthread.php?t=999016](http://ubuntuforums.org/showthread.php?t=999016)

---

### Post by rogerp1 on 2009-02-26
I followed post #27 on this page and it worked for me

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=665315&page=3](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=665315&page=3)

---

