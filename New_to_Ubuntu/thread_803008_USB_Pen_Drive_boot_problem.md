---
title: "USB Pen Drive boot problem"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by dm6257 on 2008-05-21
I installed Ubuntu 8.04 on a 2 GB PNY USB pen drive and get the following error messages immediately after boot starts:
 Unknown keyword in syslinux.cfg
 Could not find kernel image: linux
 boot:

I followed the directions from [www.pendrivelinux.com](www.pendrivelinux.com) and the Ubuntu installation documentation.

Has anyone else experienced this problem?

dm6257

---

### Post by quelx on 2008-05-21
I just did this today following the instructions here:
[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/)

It worked with no issues.  It looks like you need to 
> Move everything from the isolinux folder into the root of the drive. So, if your USB thumbdrive’s letter is F, as in our earlier example, move all the files from F:\isolinux\ into F:\

---

### Post by dm6257 on 2008-05-22
I moved the casper directory to the root so syslinux could find vmlinuz and initrd.gz.  It worked fine until the end when I got a shell for initramfs.

---

### Post by Ubristow on 2008-09-01
I also have the problem with 

Unknown keyword in syslinux.cfg
Could not find kernel image: linux
boot:

appearing when I attempt to boot Ubuntu 8.04 from a USB flash drive.

I followed the instructions in the PenDriveLinux forum [here]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/") which is for a persistent install from Windows. It went according to plan as far as I could tell.

Without modification, Ubuntu would fail with the above message on an Abit NV8 mobo with  the latest BIOS. I had to identify the USB drive as a USB Zip drive for it to be recognised at all.

Same USB drive boots to Ubuntu on an Asus EEE PC900, the sub-notebook  with 9" screen and SSDs. There are screen issues and WiFi driver issues, but it booted.

I have since checked that all of the isolinux directory is actually in the root - and found that it was there as part of the install process. I also copied vmlinuz and initrd.gz from casper to the root. That made no difference.

---

### Post by C.S.Cameron on 2008-09-01
Try installing to pendrive just as you would to HDD.
2 GB is a bit small for ubuntu but EEEXubuntu works ok on that size.
I find Xubuntu 8.04 works better on thumbdrive than Ubuntu 8.04.
Hardy seems to hang a bit more on TD than gutsy did.

---

### Post by Ubristow on 2008-09-02
> Try installing to pendrive just as you would to HDD.You are right. The doco says you need 4Gb for that.

---

### Post by Ubristow on 2008-09-29
About the problem report in Post #4. I have resolved the issue. I had to set the BIOS to boot from the pen drive on the assumption that there was another HDD found on the system in addition to the fixed HDDs. The options in the BIOS were ambiguous (to me anyway) about how to boot from a USB pen drive as if it were a hard drive. That option was covered by the choice of the order of HDD to boot from. All other removable drive types were covered by the choice of boot device and that is where the option to choose USB floppy and USB ZIP are found.

All good!:D

---

### Post by The Cog on 2008-09-29
I have been using the script isostick.sh quite happily.
There seem to be a number of slightly different versions floating around though. I attach a copy of the one I have been using. The command goes something like (still in my bash history):
**sudo isotostick.sh intrepid-desktop-i386.iso /dev/sdc1**

---

### Post by C.S.Cameron on 2008-09-29
I think that the BIOS on most late model computers just sees a flash drive as another hard drive.
On older computers I am lucky to get a flash drive to be recognized as USB HDD without the use of a boot cd.

---

