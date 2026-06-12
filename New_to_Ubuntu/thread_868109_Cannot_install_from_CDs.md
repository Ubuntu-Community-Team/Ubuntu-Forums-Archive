---
title: "Cannot install from CDs"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Petshopman on 2008-07-23
Last week I purchased a new Laptop without an operating system with the intention of installing Ubuntu. I had previuosly installed version 7.04 on 2 old PCs at the end of last year without any difficulties. I tried installing this version but it just stops after the 2nd window. It also will not run from the CD. I went out and bought the latest version 8.04 and this does the same it gets to the 2nd window and freezes. In an attempt to see if the laptop was Okay I installed a copy of XP without any probelems. I tried to load Ubuntu after XP to dual boot but it still will not install.
I've requested a new 8.04 from Linux magazine but not yet received.
Laptop Spec.
15.4" TFT screen

		

Intel T2370 Dual Core Mobile 1.73GHz

		

2GB memory

		

160GB hard drive

		

DVD writer

		

M672 Vista Premium Optimised Graphics

Has anyone any ideas please?

---

### Post by northern lights on 2008-07-23
As for the "why?" I have no idea, yet there are (at least) two alternative ways to install:

1. Download the "AlternateCD" (w/ a text-based installer) from [www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download"). Check the radio box!

2. Or, from your windows donload unetbootin from [lubi.sourceforge.net/unetbootin.html]("http://lubi.sourceforge.net/unetbootin.html"). Choose, "Ubuntu 8.04 NetInstall", reboot. Run the installer. Easiest method if XP is still installed.

---

### Post by Xerp on 2008-07-23
I'd guess on that SiS Mirage 3 M672. It certainly won't work with Compiz fusion.

---

### Post by LowSky on 2008-07-23
> **Petshopman said:**
>  I tried installing this version but it just stops after the 2nd window. It also will not run from the CD. I went out and bought the latest version 8.04 and this does the same it gets to the 2nd window and freezes.  

first off what 2nd window? While booting before getting to the prompt screen or while using a LiveCD edition and trying to install? Just anything about the last screen you read before it freezes.


Thanks

---

### Post by mkvnmtr on 2008-07-23
You might want to check that your memory is good. Freezing like that could be lack of memory. 2 GB is way more than enough but if it is not good or has been replaced in a used laptop it could be the source or your problem.

---

### Post by Petshopman on 2008-07-24
Thanks for coming back. It is in fact, the 3rd screen. The orange bar moves about 4 segments and stops while booting from 7.04. When trying 8.04 it doesn't move at all.

---

### Post by northern lights on 2008-07-24
okay. Fair enough - the installer hangs.

Is your XP installation functional? If so go for unetbootin (see above), simple and efficient.

---

### Post by hyper_ch on 2008-07-24
did you check the cd for defects?

---

### Post by Petshopman on 2008-07-24
The CDs are from UK Computer magazines. Version 7.04 has been used to install on 2 old PCs without any problems. This is why this is so frustrating.
I have downloaded "Unetbootin" and downloaded 8.04. Rebooted and now get the option for XP or Ubuntu. Choose Ubuntu and the following screens appear:
Screen 1.
Bootin GRLDR...
Starting cmain()...



Screen 2
Press 'Esc' to enter the menu... 1



Screen 3
Booting 'Unetbootin'

(hd0,0)
Filesystem type is ntfs, partition type 0x7
[Linux-bz image, setup 0x2a00, size 0x1d21d8]
[Linux-initrd @ 0x1f873000, 0x77ccec bytes]
loading


Screen 4
Ubuntu
Orange loading bar stops a 3 & a half segments as it does trying to run or install from the live CD.
XP will open without any problems.
Any help will be much appreciated.

---

### Post by northern lights on 2008-07-24
If you utilize unetbootin to install a downloaded .iso, you eliminate the chance of a bad burn.

So now we know it wasn't the CD itsself.

However, I didn't mean for you to use unetbootin that way. Instead of making it install from an .iso, choose the "8.04 NetInstall" from the dropdownmenu. It's text-based only and given its different nature might not run into the same problem...

---

### Post by phidia on 2008-07-24
At the livecd boot menu press the F4 key (some keyboards differ I believe though) 
And then enter one of these boot options > noapic or apci=off
It's worth a try.

---

