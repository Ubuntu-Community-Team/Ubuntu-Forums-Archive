---
title: "Install Ubuntu 14.04 on USB stick with further programs"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by gotqn on 2014-07-19
There are many answers about this that did not work for my situation. So, I am looking for up-to-date tutorial explaining how this can be done.

----------


I have the following:


 - Ubuntu 14.04
 - USB 2.0 and USB 3.0 ports
 - USB 2.0 stick with Ubuntu 14.04
 - USB 3.0 empty stick 


and want to install the 14.04 on the USB 3.0 empty stick. Then, I want to install the new AMD Catalyst™ 14.6 beta drivers on it and [sgminer][1]. Finally, SSH for remote access and drivers [Ethernet][2] driver as well.


That's all what I need.


So, is it possible to install the drivers and programs that I need and when I use the USB stick in other machine to expect they will work?


Also, I have try to install the Ubuntu 14.04 on the USB 3.0 stick - it takes a lot of time and finally it says "error loading operating system". 






  [1]: [https://github.com/sgminer-dev/sgminer](https://github.com/sgminer-dev/sgminer)
  [2]: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

---

### Post by yancek on 2014-07-19
How are you trying to install Ubuntu?  Is this a regular install to a partition on the flash drive?  If I remember correctly, you need about 7GB.  Or, are you using unetbootin or similar software to install it to the flash drive as a Live CD?  You can do that and select persistence so that you can modify it and add some software after it is put on a flash drive.  The second option is more likely to work on other computers.

---

### Post by oldfred on 2014-07-19
This will create a flash drive that boots with BIOS or UEFI.
But if you install a proprietary video driver it may not work on other computers unless they also use that driver. Similar issue if you have to use any other proprietary drivers.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)


This is now very old, so no idea if similar things can be done now:
 Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

---

