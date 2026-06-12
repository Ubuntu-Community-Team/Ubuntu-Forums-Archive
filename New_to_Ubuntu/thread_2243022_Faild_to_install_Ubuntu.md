---
title: "Faild to install Ubuntu"
date: 2014-09-05
forum: New to Ubuntu
---

### Post by Mats_Blide on 2014-09-05
Hi,

Tried to install Ubuntu dual boot together with already installed W7 on a brand new 
HP probook.

Followed the instructions: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I can boot installation from CD/DVD.

I can select install.

I can chose install side by side

Free diskspace, internet connection etc. required is OK

When finally selecting when continue I am asked to remove boot media
and press enter to continue. The PC restarts and boots up Windows
without any questions asked !?!?

What am I doing wrong? :-)

Rgds,
Mats

---

### Post by newb85 on 2014-09-05
Sounds like the MBR wasn't installed in the right place.  The easiest way to fix it is probably to use Boot Repair.  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2014-09-05
The behavior you are reporting would be expected if you installed the Ubuntu Grub bootloader improperly.  If you did not install it to the master boot record, this would happen as windows is not capable of booting Linux unless you use third party software or correctly, manually edit the windows boot files.  To get information about drives/partition, boot files and related information, go to the site below and download and run the bootinfoscript.  It will need to be done from the Ubuntu installation medium after selecting the Try Ubuntu option and getting to a Desktop as it is a bash script.  You will obviously need an internet connection.  If you can get to the site and download, make sure you read the instructions first which are in a link in the Description box near the top of the page:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

It will not take any action to try to repair but simply output a results.txt file which you can post here for assistance.

---

### Post by egeezer on 2014-09-05
At some point the installation medium should have asked where to install GRUB, or at the very least noted in the running line at the bottom of the installation windows that it is "Installing Grub" and later "Running Grub update".  Did either of those appear?

---

### Post by fantab on 2014-09-06
Boot Ubuntu dvd/usb, and 'Try Ubuntu'...
Open Terminal [ctrl+alt+T] and post the output of:
```
sudo parted -l
```

---

