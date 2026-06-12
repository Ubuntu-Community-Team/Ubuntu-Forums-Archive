---
title: "Questions about installing Ubuntu on Lenovo laptop that has Win7 on it"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by s1baker on 2012-12-06
hi,
I have been using Ubuntu on my desktop for two years, and now I have bought a Lenovo Thinkpad laptop ( 64 bit, 4G ram ) that has Window 7 on it, and I want to run Ubuntu on it. I want to keep Win7 on this laptop, so I have some questions:

1) It is a 300 gig HD. It has a Lenovo recovery partition on it called "Q:" that is about 15 gigs. The rest is Windows 7 on "C:". Will installing Ubuntu "side by side" with Windows7 mess up the recovery partition? I have also heard that there may be problems with the boot block. ( I had rather not run Ubuntu inside of Windows using VirtualBox )

2) I have a 32 gig SD card that I could put Ubuntu on. Can the laptop boot the Ubuntu system from the card reader? and if I did this, would it not mess up my "C:" and "Q:" partitions? As a matter of fact, I think I would rather try this option if it would work.

---

### Post by oldfred on 2012-12-06
Only a few newer computers directly boot SD cards. If yours will you can install to it.
Almost all computers in the last 6 years boot from USB flash devices. You then can install the liveCD/flash drive to test if Ubuntu works. You can add persistence to save some info. And if flash drive is 8GB or more you can do a full install.

USB flash or SD will not be as fast as a hard drive, but will be functional with 4GB of RAM as once a program is loader it is running in RAM. Linux caches activity in RAM so many things do not have to be reloaded. You can change a few settings to reduce writes which also help speed things up.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
       [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

    
If your current Windows 7 is in BIOS/MBR mode you do have the issue of all 4 primary partitions being used. You then do have to backup the vendor recovery or vendor utilities partition to give you room to install Ubuntu.

Lubuntu is a lighter weight version for older systems. But being lightweight will load faster.
       HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

---

### Post by s1baker on 2012-12-06
The laptop was bought 6 months ago new, so I guess there will not be an issue there. Have 4 gigs of ram and the card is 32 gigs. 

I have booted the laptop into bios and can see that there is an option there to select the boot device, so I guess the card will show up there after I get it installed. Also, I downloaded the "linuxliveusb.exe" for Win7, it ( I think ) is supposed to make the .iso bootable off the card.

Also, I think I am going to install Xubuntu, smaller footprint and I want xfce desktop.

---

