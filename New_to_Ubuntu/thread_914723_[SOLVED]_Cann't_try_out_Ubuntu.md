---
title: "[SOLVED] Cann't try out Ubuntu"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by lpvmc on 2008-09-09
As a newbie with Ubuntu I ordered the 8.04.1 LTS Desktop Edition CD and put it in to see and try what Ubuntu is about. As instructed I put in the CD and restarted my Toshiba Satellite M70-168 but nothing happened. After a while the CD drive stopped and .... nothing; as always the computer started with windows.

Thanks in advance

---

### Post by jemate18 on 2008-09-09
> **lpvmc said:**
> As a newbie with Ubuntu I ordered the 8.04.1 LTS Desktop Edition CD and put it in to see and try what Ubuntu is about. As instructed I put in the CD and restarted my Toshiba Satellite M70-168 but nothing happened. After a while the CD drive stopped and .... nothing; as always the computer started with windows.

Thanks in advance

SETUP your BIOS and set the primary boot device to your CD or DVD Drive

---

### Post by iaculallad on 2008-09-09
> **lpvmc said:**
> As a newbie with Ubuntu I ordered the 8.04.1 LTS Desktop Edition CD and put it in to see and try what Ubuntu is about. As instructed I put in the CD and restarted my Toshiba Satellite M70-168 but nothing happened. After a while the CD drive stopped and .... nothing; as always the computer started with windows.

Thanks in advance

Make sure that your system is set to boot on it's CD/DVDROM at boot time.

---

### Post by jemate18 on 2008-09-09
> **lpvmc said:**
> As a newbie with Ubuntu I ordered the 8.04.1 LTS Desktop Edition CD and put it in to see and try what Ubuntu is about. As instructed I put in the CD and restarted my Toshiba Satellite M70-168 but nothing happened. After a while the CD drive stopped and .... nothing; as always the computer started with windows.

Thanks in advance

The reason for your situation is that:
1. At bootstrap or boot, your BIOS searches for the device on which to look for your OS
2. Your BIOS is configured and setup up to first look at your HD.
3. Since you have your Windows on your HD, the BIOS loads your windows since your BIOS settings about device boot priority is set to HD.

Solution for this is posted above

---

### Post by lpvmc on 2008-09-09
First, thanks for the quick replies and explanation.

Changed the boot order, CD/DVD drive first now, saved the settings, restarted and .... Windows again. Restarted one more time but with the same result.

Any more suggestions?? Thanks in advance!!

---

### Post by jemate18 on 2008-09-09
> **lpvmc said:**
> First, thanks for the quick replies and explanation.

Changed the boot order, CD/DVD drive first now, saved the settings, restarted and .... Windows again. Restarted one more time but with the same result.

Any more suggestions?? Thanks in advance!!

Do you have any other DISTRO LiveCD? If you have, try booting it. If it boots successfully your Ubuntu LiveCD has the problem.......and needs another download and burn....

---

### Post by stalkingwolf on 2008-09-09
at boot try hitting F12.  On some machines this will give you
a one time boot menu.

Also if you have more than one CD/DVD rom make sure you have the live cd
in the right drive.

---

### Post by redseventyseven on 2008-09-09
On some machines, different keys take you to the boot menu. Try F5 or F8 as well.

The other thing to check is whether you saved your settings when you changed your BIOS setup. This might seem a bit obvious but I've seen some BIOS setup menus that don't make it immediately obvious whether you're exiting with or without saving.

---

### Post by lpvmc on 2008-09-09
Hi jemate18,

You mean like any CD with a specific program on it like Acronis, as an example. Or should it be a cd with an OS on it?

Hi stalkingwolf/redseventyseven,

Will try your suggestions later; so thanks!!

---

### Post by Bölvaður on 2008-09-09
yes it should have OS on it. Something like a live-cd which is an OS that can be booted from a cd, most linux distros have that feature nowdays.

---

### Post by lpvmc on 2008-09-09
In that respect I only have my Windows restore CD and the ubuntu CD. So that's it??

---

