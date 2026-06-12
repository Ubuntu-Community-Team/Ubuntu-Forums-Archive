---
title: "How to install lubuntu on SD Card"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by alfianabdi on 2013-04-30
I have a mini-PC which is completely a black-box. All I now is it has many usb ports,no hard disk drive, and one SD Card slot.
I was wondering how to install any OS on SD Card. 
I have tried LINUXMINT, and it didn't even boot from my bootable usb flashdisk (created using linuxlive usb creator) 
I have waited forever, nothing happen after the first option on screen.
I thought it was too heavy for my SD Card, so i looked for light-weight OS, and my choice came to LUBUNTU
Could somebody tell me how to install LUBUNTU on SD card?
I am just a novice in linux, I have once or twice installed UBUNTU on normal PC (on hardisk drive), but never on SD Card.
Will it be the same as to install UBUNTU? 

Thank you in advance :)

---

### Post by MoebusNet on 2013-04-30
I found this discussion on "Ubuntu on SD Card":

[http://ubuntuforums.org/showthread.php?t=2027552](http://ubuntuforums.org/showthread.php?t=2027552)

I believe these instructions should also apply to installing to a SD card:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You can research more at:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by C.S.Cameron on 2013-04-30
I am running my EEE PC from SD card.
(Some older computers will not boot SD cards but it sounds like yours will).
Installing to SD is similar to installing to internal drive.

Following is step by step how to install 12.04 on a 8GB SD card:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the SD card.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language.
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4500 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hibernation)

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the SD card. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your SD card.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You may do an update-grub later.

---

### Post by monkeybrain2012 on 2013-04-30
Why the /Windows partition with FAT format? It is not necessary.

---

### Post by C.S.Cameron on 2013-04-30
> **monkeybrain2012 said:**
> Why the /Windows partition with FAT format? It is not necessary.

The FAT32 partition is optional just in case you want to transfer files to or from a Windows computer, (some people still use SD cards for such a purpose).

---

### Post by alfianabdi on 2013-05-01
thank you very much :)
i have tried it, but the problem occur here 
I just realized my CPU wasn't Intel or AMD,it was Vortex86MX
when i tried to boot, i have this message :
**the kernel requires the following features not present on the cpu cmov**
what does it mean?

---

### Post by mörgæs on 2013-05-02
A processor with CMOV is required for all recent Buntus. You might be able to find another distro which does not require CMOV, but I don't think it will be easy.

---

