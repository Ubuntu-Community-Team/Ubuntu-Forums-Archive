---
title: "ubuntu 11.10 live session works installation fails"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by Arthur Millar on 2011-11-14
hello 
i recently tried ubuntu 11.10 on my newish hardware 
the live session from my pendrive works great but after I have installed it the graphics go weird 

is there anyway i can fix it?
Thanks

---

### Post by anewguy on 2011-11-14
We should probably try to find out what type of video adapter you have so we can see if something special needs to be done.

The first thing you should do:

- boot up the live session
- open up the terminal - just click on the topmost button on the menu that pops in from the side and type ter - you'll see terminal there
- type:
lspci | grep VGA
- post that output back here in a reply

The second thing I would do:

- at boot get the grub menu by pressing the shift key (I *think* that's it for 11.xx) several times as the machine itself is booting, before the OS boots.  If you have dual-boot, then the boot menu should already be showing
- highlight a boot line and then edit it (follow the menu on the screen for what keys to press)
- add nomodeset to the boot line
- tell it to boot (again, follow the menu on the screen for what keys to press)

Does it work any better?

Dave ;)

---

### Post by Arthur Millar on 2011-11-16
Hello Dave
Thanks for the reply 
Adding nomodeset to payload$ worked

---

### Post by anewguy on 2011-11-18
Glad that worked for you.  Do you know how to make that a permanent change - if not we can walk you through that as well.

Dave ;)

---

