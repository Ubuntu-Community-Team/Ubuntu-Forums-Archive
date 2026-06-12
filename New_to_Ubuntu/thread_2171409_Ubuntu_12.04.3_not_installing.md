---
title: "Ubuntu 12.04.3 not installing"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by nova23 on 2013-08-30
I am trying to install Ubuntu 12.04.3 64 bit on my Dell laptop, I have Windows 7 professional version already installed, when I mount the iso and try to install Ubuntu, it does nothing absolutely nothing. I tried with both 32 and 64 bit versions. I even tried 13.04, same thing, does nothing. Please help....

---

### Post by Impavidus on 2013-08-30
Not sure what you're trying...

You can [burn the iso to a DVD]("https://help.ubuntu.com/community/BurningIsoHowto") or [to a USB stick]("https://help.ubuntu.com/community/Installation/FromUSBStick") and boot the computer from it. You may have to change the boot order in the BIOS. It should start an Ubuntu live session, from which you can install. You may need some preparatory work in Windows to get enough unallocated drive space (=space on your hard drive not associated with any partition).

---

### Post by Jonathan Precise on 2013-08-30
> **nova23 said:**
> I am trying to install Ubuntu 12.04.3 64 bit on my Dell laptop, I have Windows 7 professional version already installed, when I mount the iso and try to install Ubuntu, it does nothing absolutely nothing. I tried with both 32 and 64 bit versions. I even tried 13.04, same thing, does nothing. Please help....

Do you know if you have UEFI on your laptop?

---

### Post by su:bhatta on 2013-08-30
Please give details about "it does nothing".

Are you using DVD or USB? Have you read about UEFI, if not this is a help page : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) OR 

If you are getting any screen like a purple screen with a "man=Keyboard" sign at botton then you can try 'nomodeset'. If you get that purple screen then we will get to how to use 'nomodeset'.

If you get a black grub screen then it might be due to EFI.

---

### Post by nova23 on 2013-08-30
@Impavidus: I am using daemon tools... I didnt burn to a cd or boot using USB...
@Jonathan Precise: I do not know whethere my laptop has UEFI or not... is there a way to find out
@bhattabhishek: I double click wubi.exe, my cursor turns to "working in the background" for few seconds and then the cursor turns normal.... thats it with every version of Ubuntu I tried

---

### Post by nova23 on 2013-08-30
And I also download wubi.exe alone and tried installing, like with iso files nothing happened

---

### Post by su:bhatta on 2013-08-30
Wubi is discontinued if I am not mistaken.I don't know if it will work, so cannot help you there. 

 If you want to install Ubuntu 13.04 or try a live session to see if it works with your machine then it is suggested to either burn a DVD or a USB and boot your computer with the DVD or USB and then you can choose between "Try/Install Ubuntu"

---

### Post by su:bhatta on 2013-08-30
Check this page, it has some details about how to find out if you laptop has EFI:

[http://ubuntuforums.org/showthread.php?t=1979625](http://ubuntuforums.org/showthread.php?t=1979625)

---

### Post by oldfred on 2013-08-30
The ISO in Windows cannot just be mounted and run. You have to create a DVD or USB flash drive and reboot system to install it.
It does not fit on CDs anymore, so you need DVD, but instructions are the same.

 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

From flash drive you then reboot computer and boot into Ubuntu. It should give two choices Install or use as liveCD. Best to test in live mode to make sure it works with your system.

Examples of installs with screen shots.


 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

