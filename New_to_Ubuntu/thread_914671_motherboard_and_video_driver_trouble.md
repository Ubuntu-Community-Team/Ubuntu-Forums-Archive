---
title: "motherboard and video driver trouble"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by vague jayhawk on 2008-09-09
I need help.  

I Ubuntu working just fine on one of my computers.  Then the motherboard intermittently crashed.  I had to replace it.  It was a pain - but no real problem.  Everything plugged back in I booted it back up.  The new motherboard has an integrated video card and the resolution settings were bugging me.  Given the successes earlier in the day I was feeling brave and I downloaded and installed the restricted driver and did a reboot.  

Now the computer starts, I get the ASUS logo, I get the grub message, Ubuntu starts loading up, the logo pops up and the bar goes across, then nothing.  Blank.

---

### Post by bobnutfield on 2008-09-09
Have you tried booting into safe graphics mode to remove the misbehaving driver?  What video chipset is in the motherboard?

---

### Post by vague jayhawk on 2008-09-09
I am ashamed to say that I am not sure how to boot into safe mode.  I can't find it in The Official Ubuntu Book that I bought.

The motherboard is an ASUS M2A-VM.  Directions states it comes with ATI Radeon x1250 graphics.

---

### Post by bobnutfield on 2008-09-09
When your grub screen comes up, hit the esc key quickly and you will see a list of available boot entries.  One of them will be safe graphics mode.  Highlight that and hit enter.  Graphics will be bad, but usable and you can remove unwanted drivers.

---

### Post by vague jayhawk on 2008-09-09
It looks like I currently have 5 separate kernels.  

2.6.22-15-generic (recovery mode)

2.6.20-16-generic (recovery mode)

non recovery modes of those and then something that says memtest86+

---

### Post by SunnyRabbiera on 2008-09-09
you may want to preform a reinstall after a backup, there is a chance that not all the parts are clicking here.

---

### Post by vague jayhawk on 2008-09-09
I would love to get to the spot that I can get to my files to back them up.  

I am currently getting a message 

root@matilda:~#

I am not sure how to proceed from there.

---

### Post by bobnutfield on 2008-09-09
SunnyRibbiera has got a point.  It may be better to just reinstall since you have changed motherboards.  I can tell you from my own experience that changing motherboards, even if it is the same model and chipset, wreaks havoc on a current install.  It looks like you are running Gutsy from your kernel selections,  To back up your files, you can do from the command line depending on where you want to back them up to.  If you have a USB stick with a large enough capacity, that may be the easiest and we will be glad to help you do that.

Also, consider upgrading to Hardy.  It is a much more up-to-date kernel.

---

