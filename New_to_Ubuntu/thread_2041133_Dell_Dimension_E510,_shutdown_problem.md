---
title: "Dell Dimension E510, shutdown problem"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by GCapo on 2012-08-11
I hope someone can point me in the right direction, because I have been researching my problem for over a month on and off.  I installed Ubuntu 12.04 onto a 6yr old Dell Dimension E510.  Everything works fine except for shutting down.  

So far I have:
-tried all terminal commands, but only restarts the system

-replaced the CMOS battery because I thought it was a clock problem.  My BIOS clock keeps going 4 hours ahead.  Saw that this may be due to Linux changing clock to UTC and things not syncing up causing the problem.

-changed the grub
Find the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and make it exactly like this 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
save the document and then

Any ideas in which direction to research would be appreciated.
Regards,

---

### Post by marlow59 on 2012-08-11
even ```
sudo shutdown -P NOW
``` doesn't work? what is your exact problem actually, you are not able to shutdown your computer ?

---

### Post by GCapo on 2012-08-12
marlow59 - yes it will not shut down it will only restart.  The command you provided only restarts and I have tried I think all shutdown terminal commands.

---

