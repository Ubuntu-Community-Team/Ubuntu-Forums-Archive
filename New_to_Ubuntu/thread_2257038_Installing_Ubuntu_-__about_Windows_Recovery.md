---
title: "Installing Ubuntu - ? about Windows Recovery"
date: 2014-12-16
forum: New to Ubuntu
---

### Post by Salij on 2014-12-16
On the instructions for dual-booting Ubuntu, it says:

"[COLOR=#333333][FONT=Ubuntu]Have a Windows recovery CD/DVD available"

[/FONT][/COLOR]The only option that I can see that my computer (Lenovo Ideapad with Windows 8) offers me, is to create a Recovery USB, not a CD/DVD, and my computer did not come with a recovery CD. Will I have to request one from the manufacturer, or can I use a USB?

---

### Post by Gordonbp531 on 2014-12-16
USB is fine. You should have made one as soon as you bought the machine :-)
Just out of interest, what model of Ideapad? (I have a U410 running Ubuntu 14.04 and Windows 8.1 as dual boot)

---

### Post by Mark Phelps on 2014-12-16
Also do NOT use the option to install alongside Win8, as that will allow the installer to shrink the Win8 OS partition, and that can cause filesystem corruption -- preventing you from rebooting Win8 to repair it.  If that happens, you will NEED the Recovery USB in order to do Startup Repair.

---

### Post by spiffymoo on 2014-12-17
Ive never had file system corruption using along side option. and you can boot into win 8 using install along side option. im duel booting utopic and win 7 i used alongside option.

---

### Post by Gordonbp531 on 2014-12-17
Windows 8 is a bit different from Windows 7. There are quite a number of recorded incidents where the Ubuntu installer has been allowed to create the unallocated space which has courrupted the Windows 8 boot.
The received wisdom is to create the free space within Windows 8 using Disk manager, and then choosing the "something else" option in the Ubuntu installer. 
Plus the fact that the Ubuntu installer doesn't see Windows 8 as an installed OS anyway.
See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564").

---

### Post by MartyBuntu on 2014-12-17
The ideal thing would be to image the drive before you install your Linux distro.
That way you could always roll back in case something bad happens with the installation.

---

### Post by Darth Riker on 2014-12-18
> **MartyBuntu said:**
> The ideal thing would be to image the drive before you install your Linux distro.
That way you could always roll back in case something bad happens with the installation.

Agreed. There are a few free tools out there which you can use to do this (just as a start: [http://lmgtfy.com/?q=free+imaging+software](http://lmgtfy.com/?q=free+imaging+software)) :)

My personal tool of choice when making an image of a Windows machine is Macrium Reflect Free.

---

