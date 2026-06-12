---
title: "disk read error"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by jerzydirtracer on 2008-05-01
Hello, everyone has probably heard of this, I loaded Ubuntu on my garage computer, I loaded it to the hard drive, I used the entire partition option, I reboot, change the bios to load the hd 1st, and I get a disk read error invalid boot disk, I played around with jumpers, bios, cables, etc. to try to get it to boot. I even reloaded a couple of times. I did the same thing on my laptop with the same disk and it works flawless, even after 3 months. Is there an option that I can access from live to change the boot or make the hd bootable? Also, the files and system were copied to the hard drive. The hd is an older 30 gig WD drive. 

Thanks
Bob

---

### Post by superprash2003 on 2008-05-01
why dont you install it instead of copying?

---

### Post by rny629 on 2008-05-01
I'm having the same problem after i just downgraded back to Gustsy 7.10.
I can say that I did the install w/ my IDE and SATA together(install on the SATA Windows on IDE) and now i have the problem. My 1st install i just had my SATA drive with the install and no IDE on the system and it booted off the cd. After Installing the OS keep the Boot Cd in when it reboots, then click on the Boot off 1st HD. It should show an installation on the bottom left of the screen for Grub.(at least that's how i remember it) then it's going to boot up. After the initial boot and your on the desktop pop out the cd. next time you reboot  Grub 1.5 should kick in. that's the bios loader(i'm guessing???)
Hope I helped...

:popcorn:

I gotta reinstall mine for the same reason. can't find a post that shows anything.

just found some info:

[http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu](http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu)

---

