---
title: "Using a Windows Partition"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by rebeccabunz on 2013-06-14
Hello,

I have just installed Ubuntu 12.04 on a Toshiba Satellite L750. Using VirtualBox I have installed a Windows 7 Ultimate partition. I have also changed my settings to have the desktop rotating cube. I was wondering if it is possible to change it so that one face of the cube runs as the Windows 7 partition instead of having to go through the VirtualBox everytime. 

Second, I am trying to install Microsoft Offcice from a disk but the Windows Partition will not recognize the disk drive on my computer. How do I change it so that the Windows partition can recognize when I insert a disk intended for a windows computer. 

I am not very good with computer language so please answer in as simple a manner as possible. 

Thank-you so much for your help.

---

### Post by cincinnatus13 on 2013-06-14
So you have Virtualbox running inside of Linux right? So all you should have to do is go full screen with the Windows 7 on one side of the cube if I'm thinking of it correctly. Then just use ALT+arrow (IIRC) to rotate the cube to your linux sides.

Second, IIRC (haven't used Virtualbox in a while) you just need to be sure that the CD drive is enabled in the settings of Vbox. Should be under the USB menu I believe.

---

### Post by rebeccabunz on 2013-06-14
Thank-you for your response! What ended up working was to go into VirtualBox znd click onto the windows partition. Click settings. Then click the storage tab on the side. At the bottom of the storage tree column there are four icons. I clicked the one with the cds and plus sign (the first one), then clicked add CD/DVD Device. I choose "Leave Empty". Highlight the Empty CD spot under the Storage tree column and then choose the picture of the CD on the far right hand side. Then I choose Host Drive. Then clicked okay and exited the settings. The CD was then recognized in the My Computer Folder.

---

