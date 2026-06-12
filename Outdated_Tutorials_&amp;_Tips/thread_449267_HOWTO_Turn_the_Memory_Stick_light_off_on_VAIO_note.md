---
title: "HOWTO: Turn the Memory Stick light off on VAIO notebooks in Feisty"
date: 2007-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by MonkeyWrench32 on 2007-05-20
Ever since I upgraded my VAIO VGN-FS660/W to Feisty the Memory Stick light on the front panel would always stay on.  If you don't use it (like me), here's an easy way to turn that darn thing off.

**Warning**: This may disable other memory card readers.

1. Open up your friendly terminal and enter: ```
lsmod | grep tifm
```
2. Now enter this:```
gksudo gedit /etc/modprobe.d/blacklist
```
3. At the end of the file, enter each module listed on the lsmod output one at a time with "blacklist" proceeding it.  Here's mine: ```
# Disable Memory Stick
blacklist tifm_sd
blacklist tifm_7xx1
blacklist tifm_core
blacklist mmc_core
```
4. Save, reboot, and voila!

---

### Post by tash0 on 2007-05-20
its really helpfull. tnx.:D

---

### Post by purpzey on 2007-05-21
When you say it might affect other memory card readers, this would apply to USB ports (i.e. Thumb-Drives), would it?

NOTE: This is a great idea though, that light has been driving me crazy

Thanks.

---

### Post by MonkeyWrench32 on 2007-05-21
Well, since SD and MMC modules are being blacklisted, then other SD and MMC cards may not work.  Other memory cards may fall into the same situation.  USB thumb drives should be fine, though.

---

### Post by insane2600tt on 2008-01-14
Thanks a lot for this fine guide :-) i'm writing to ask how to TURN ON that light without rebooting. I would like to turn on or off that light in a bash script that i wrote to alert me of a new email. This is pretty usefull when your lid is closed for example and you don't want to open and reopen when you're waiting for a message..

thanks in advance to everybody!


cheers,
Indaco88

---

### Post by insane2600tt on 2008-01-14
> **insane2600tt said:**
> Thanks a lot for this fine guide :-) i'm writing to ask how to TURN ON that light without rebooting. I would like to turn on or off that light in a bash script that i wrote to alert me of a new email. This is pretty usefull when your lid is closed for example and you don't want to open and reopen when you're waiting for a message..

thanks in advance to everybody!


cheers,
Indaco88

ops, just to know.. i use to turn that light off dynamically using the command:
sudo rmmod tifm_sd && sudo rmmod tifm_7xx1


same question, how to turn it on dynamically? :-)

---

