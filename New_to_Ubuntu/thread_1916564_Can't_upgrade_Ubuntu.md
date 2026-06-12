---
title: "Can't upgrade Ubuntu"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by olasca on 2012-01-28
Hello, 

I am using Ubuntu 8.04 and I have decided that it is time to upgrade to the more recent versions.  I have gone into the update manager and clicked on check.  The update manager then informs me that some of the repositories may not be valid.  If I click OK the update manager does not find any new updates and subsequently I am unable to upgrade to 9.04.  What can I do to upgrade my system? 

Thank you.

---

### Post by mastablasta on 2012-01-28
it might be better to do a fresh install of an LTS edition or you can still upgrade if you wish: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

upgrade should work relatively ok if you didn't do any major changes. if you are using any PPA or proprietary driver i suggets you disable the PPA and uninstall the drivers before doing the upgrade.

---

### Post by QIII on 2012-01-28
Both 8.04 and 9.04 have reached End Of Life and are no longer supported, which means it is probably not worthwhile to upgrade -- even using mastablasta's link.

It would probably be best to back up your important files and do a complete, fresh installation of a newer version.

---

### Post by fantab on 2012-01-28
> **mastablasta said:**
> **it might be better to do a fresh install of an LTS edition **

It IS better if you do a clean install of the newer or latest Ubuntu version. 12.04 LTS will anyways release in April 2012, so you can either wait until then and 'clean install' 12.04 or meanwhile if you want to test unity or gnome-shell try 11.10. 

Whatever you do BACK UP your DATA first.

---

### Post by olasca on 2012-01-28
Thank you. 

I attempted to follow the instructions regarding the EOLUpgrades but the terminal spits back this:

Checking for a new ubuntu release
current dist not found in meta-release file
No new release found

How would one go about doing a clean upgrade?  I have all data backed up.  

Thank you again,

---

### Post by grahammechanical on 2012-01-28
We do a fresh install the same way as we installed Ubuntu the first time. We download the Ubuntu image file (ISO) and burn it to a CD/USB stick and then boot from that. We can then try Ubuntu to see if there will be any problems with our hardware and also install Ubuntu.

[http://www.ubuntu.com/download]("http://www.ubuntu.com/download")

What partitions do you have on the hard disk? Is your home folder on a /home partition? Are you dual booting with another OS?

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

Regards.

---

### Post by olasca on 2012-01-29
Hello, 

I know this is pretty basic stuff, but the last time I downloaded this I did it from a purchased CD.  I am trying to perform the clean install from a USB as I do not have access to a CD burner at the moment.  I downloaded the ISO (Ubuntu-11.10-desktop-i386.iso) and placed it on my USB drive.  I then ran System-->Administration-->Create USB Start-Up Disk.  I restarted the computer and changed the boot menu to state: 

1. USB-ZIP
2. Bootable Hard Drive
3. CD/CD-ROM

All other options were not present.  When it booted it went to the black screen with white letters and stated the following: 

SYSLINUX 3.63 Debian-2008-07-15 CBIOS Copyright (C) 1994-2008 H. Peter Anvin Unknown keyword in configuration file.  Boot: _ 

The underscore after "boot:" was blinking.  

How do I proceed so that I can clean download from the flash drive? 

Thank you,

---

### Post by nipunshakya on 2012-01-29
@olasca:
 Hi. If you want to boot using USB, please go through the following:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://techie-buzz.com/foss/create-bootable-ubuntu-usb-disk.html](http://techie-buzz.com/foss/create-bootable-ubuntu-usb-disk.html) or the following:
[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

Hope those help you out....Goodluck.
Regards,WinuxUser

---

### Post by olasca on 2012-01-29
Hello, 

Thank you.  Just finished the upload and am now running Ubuntu 11.10.  Quite an improvement from the 8.04 that I have been running.  The fix was simply to delete the ui from the syslinux exe.  

Thank you all for your help, 

Olasca

---

### Post by nipunshakya on 2012-01-29
Glad to help you...Happy Linuxing.

Regards,WinuxUser

---

