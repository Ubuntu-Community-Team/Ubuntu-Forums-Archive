---
title: "Help, Ubuntu CD does not start/load."
date: 2017-09-24
forum: New to Ubuntu
---

### Post by unn1234 on 2017-09-24
I have laptop HP Pavilion DV6700, hard drive failed. Originally had Windows Vista Ultimate on it. Installed a new hard drive 500GB SATA (original was 250GB). I have recovery discs but they they did not work. Researching the net tells me that those recovery Cds can be used only on the OEM hard drive. So decided to install Ubuntu. The computer has a brand new HD with no operating system. Formatted the HD with Gparted, only one partition (Problems described below remain same before and after formatting). When powered on, the laptop goes to a cursor in the left upper corner of screen and nothing else. The boot order is set to the DVD drive in bios. I have already reset the bios to default, no change.

I downloaded Kubuntu 17.04 (and Ubuntu 17.04), burned the .iso to DVD (about 1.6GB size) using Imgburn on a different, working, laptop with Windows 8.1. There are 14 items (folders & file) in the DVD. So, I assume it is a good DVD.

I insert the Ubuntu or Kubuntu (same problems with both) DVD in the PC and turn power on. The screen goes to a flashing cursor. I hear the sounds of the DVD drive working, a few times. Then nothing happens. I have left it to work for more than an hour. Nothing happens,the cursor keeps flashing. The DVD drive is able to start the recovery CD (but does not finish) and other bootable CDs.

QUESTION: how can I install Ubuntu on this computer. I do not have a free standing CD of windows vista to install on it and do not want to spend the money to buy one. And I am not even sure if I will be able to install it on this PC. I am able to load the mini windows XP on it from Hiren's boot CD 15.2. I am able to load Ultimate CD for Windows. 

Please help me salvage this PC, with some way to install Ubuntu. Thanks.

---

### Post by ian-weisser on 2017-09-24
Go into BIOS and select the proper boot media.
Look at your boot screen(s) carefully for the instructions on how to get into BIOS.

---

### Post by unn1234 on 2017-09-24
Already did. CD drive is the first boot. It makes the noise also after cursor shows.

---

### Post by mastablasta on 2017-09-25
the DVD part of the drive might be broken. you can try to install with network installer (wired connection and unlimited broadband is very much recommended here): [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)
this will get you to command line basic OS. from there, depending on what desktop you want you can install it by using:
```
sudo apt-get install ubuntu-desktop
```

replace ubuntu desktop with lubuntu-desktop, xubuntu-desktop, kubuntu-desktop... and many others out there (windows managers, tiled windows etc).

a short guide with pics (old but i think still valid): [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
more info: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

you can also try one of the boot options such as for example nomodeset.: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

also please provide us with system specs. the boot CDs you mention should have some system configuration output available, if i am not mistaking.

easiest to install to an empty hard drive (unformatted) and then just use the option that uses the whole disk. it will all be done automatically.

---

### Post by unn1234 on 2017-09-25
Thanks guys. First I should have told you that I have poor understanding of technology. Although I have used computers for long time and have from time to time tried fixing software problems with the help of people like you on the net, I still have hard time following complex issues. I will try to give you some more information so you can help me. Some of this may be repetition of what I have already stated in my initial post. Thank you for all your time.

I have HP DV6700 laptop, new blank hard drive, so no operating system (original OS was Win vista ultimate. I am unable to install OS with recovery CDs (it gives certain errors). Powering the PC brings a blank screen with cursor flashing in left upper corner and no further progress. In the bios, the boot order is already set to CD drive to be the first.

The CD drive is not broken because it can load other bootable Cds (Hiren's Boot CD, Ultimate boot disk, Gparted) and the recovery CD. I did format the HD to a single partition using the "seagate utility" in one of these Cds. Also did it with Gparted.

Since no OS, no internet access on this PC, so cannot install any thing directly from internet. Only can download on another machine and then copy to CD and boot this HP from that CD.

The Ubuntu 17.04 or Kubuntu 17.04 .iso DVDs (around 1.6GB size and have 13 folders) are supposed to be bootable. But neither boot the computer. Because it cannot boot the computer, I cannot progress any further.

The Ultimate boot CD has a utility called "mini windows XP" which can be loaded and the computer is in windows XP (this is all in a virtual drive in Ram). I don't know if I can remove the boot CD and still be able to continue working in that windows environment. If that is so, is there a way I can install Ubuntu in that environment?

I will be happy to give any other specific info you may need to help. I appreciate your time.

---

### Post by unn1234 on 2017-09-25
UPDATE: Sorry about duplicate post above. I mentioned "Mini windows XP" above. With mini XP loaded, I am able to connect to web with direct wired connection. In this environment I see 3 drives: 1. B: Ram drive size 851 MB. X: local disk (perhaps also a RAM drive), no size specified, C: my new hard drive 465GB size (properties show NTFS format). I tried downloading Kubuntu 1.7GB file. First time It did not complete. I believe it was being saved in X: which being RAM drive (total RAM in PC 2GB) was insufficient in size. There is no option of changing the save location. When I tried again the default Opera in this environment kept crashing and did not even start the download. In order to continue using this environment I have to leave the original Cd in the drive so I cannot use my Ubuntu Cd to install. I looked into possibility of making USB stick ubuntu. It creates a bootable USB stick. However my HP does not have choice of making USB as the boot device in the bios. This utility does give me dos prompt (X:\i386\system32\flashing cursor. How do I proceed from here to install ubuntu? Thanks.

---

### Post by ian-weisser on 2017-09-25
I'm not sure why you detoured through "Mini Windows XP". It seems entertaining but not useful.

Nothing has changed: Your install CD seems corrupt. Download and burn a new one on a good system.

---

### Post by Impavidus on 2017-09-25
Could be a bad burn or a bad download. Make sure that after downloading you check the md5sum. The bootable disk should also have a self test (if booting proceeds far enough). Sometimes you need some boot options, mostly depending on the details of your hardware.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) (a bit old, but mostly correct I think)

Do you see the small logo with a keyboard and a human?

Most computers from the Windows Vista age can also boot from a usb drive. That may be more reliable.
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick
[/URL]
Note that formatting your hard drive as NTFS is useless. Ubuntu cannot be installed on that, but the installer will reformat it to something more useful.

---

### Post by mc4man on 2017-09-25
I'd suggest you start over & either use the 16.04.3 image or the 14.04.5 image. 17.04 would be a very poor introduction to Ubuntu & from some viewpoints just plain poor release altogether.

16.04.3 image was available on the same page as 17.04 - 
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
if you needed a 32 bit install then go here, ubuntu-16.04.3-destop-i386.iso
[http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/) 

14.04.5 is available here -
[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

Just to see tried ImgBurm thru wine, worked fine with both 14.04.5 & 16.04.3, can't see how you'd not burn correctly with it, though make sure it shows using ISO9660 (Bootable), Joliet as in screen

Edit: that some pretty old hardware, you may be better off with Xubuntu or worst case Lubuntu

---

### Post by unn1234 on 2017-09-25
Thank you every one for your input. I was talking to some one at work about this and he told me that there is frequent problem with installing of 64 bit, try 32 bit. So downloaded 32 bit 17.04. It installed without any problems. Mc4Man: I thought latest edition would be better than previous and not worse. Is there significant difference and should I change and install older version. Do I need to remove new version and then install older version.

I was also searching for a manual/ user guide for Kubuntu. The only one I found I believe is for version 6.10. Is there a recent one available or will this older one will suffice? Now comes the job of learning how to use Kubuntu. Can I continue to present questions about "how to use" in this forum or some other subforum? Thank you.

---

### Post by mörgæs on 2017-09-25
I would suggest that you stay with 17.04. In all of my installs it has been completely error free. 

Besides, it's always better to trust your own observations than what some poster is writing - including me :-)

---

### Post by mastablasta on 2017-09-26
> **unn1234 said:**
> Thank you every one for your input. I was talking to some one at work about this and he told me that there is frequent problem with installing of 64 bit, try 32 bit. So downloaded 32 bit 17.04. It installed without any problems. Mc4Man: I thought latest edition would be better than previous and not worse. Is there significant difference and should I change and install older version. Do I need to remove new version and then install older version.

you can overwrite the install. 16.04 would then be better. not sure how long the support for 32 bit will last. they are slowly dropping it. 16.04 is LTS and supported until 2021. 

releases between LTS are supported for 9 months only then you need to (or rather should) upgrade. but you won't know what the upgrade will bring for your PC.

we still do not know what specifications you have (CPU etc.). in any case good that you got it working. if you have a 64bit CPU then it really probably was a bad download or burn.

[QUOTE]
I was also searching for a manual/ user guide for Kubuntu. The only one I found I believe is for version 6.10. Is there a recent one available or will this older one will suffice? Now comes the job of learning how to use Kubuntu. Can I continue to present questions about "how to use" in this forum or some other subforum? Thank you.

Kubutnu otherwise have their own forums, but there is no manual for it as i know. however it's applications are doccumented by the KDE project: [https://www.kde.org/products](https://www.kde.org/products)

also commands are (in 99%) the same in all desktop version.

---

