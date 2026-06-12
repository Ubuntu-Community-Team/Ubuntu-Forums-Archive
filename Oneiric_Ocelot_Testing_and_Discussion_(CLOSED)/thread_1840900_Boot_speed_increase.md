---
title: "Boot speed increase?"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Xgen on 2011-09-08
Hmm...I wonder what magic they did - oneiric was taking twice as long as natty to boot from burg to usable desktop on an SSD drive (20 seconds as opposed to 10). Now it takes 7 - 8 seconds... ;)

---

### Post by MacUntu on 2011-09-08
My systems are completely fu**ed up. PC takes 25 seconds, notebook 42 seconds to boot - both with a SSD.

I did a fresh install on the PC and it booted up in 10 seconds, then I installed all the stuff I had on the old system, copied back my config and /home and boom, back to crappy boot time. :D

---

### Post by Jack Brown on 2011-09-08
mine takes [SIZE=3]&#8734;[/SIZE] secs to boot now





Edit: not quite after all, as it booted up just now but i only see the background with dots. the one right before unity panel appears and right before i can use it for anything.

oh wait it made the ubuntu sound now.

but i can only see the mouse pointer...

looks like errors in my hard drive  

ata1.00:status {DRDY ERR}
ata1.00 error:{UNC}
exception Emask 0x0 SAct
irq_stat 0x40000008

...
...
...


end_request: I/O error, dev sda, sector 377811945


agh bad sectors? poor old hard drive?

at least ubuntu 11.10 was able to recover a bit.  good sign.

---

### Post by Xgen on 2011-09-08
I switched back to the basic grub to test and it takes 15 -16 seconds. The only difference in burg is the line: 'gfxpayload=keep.'

---

