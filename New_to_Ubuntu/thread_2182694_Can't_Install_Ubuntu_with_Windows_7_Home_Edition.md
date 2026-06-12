---
title: "Can't Install Ubuntu with Windows 7 Home Edition"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by harsha2 on 2013-10-22
Hello Friends,
I' m new to ubuntu. I try to install Ubuntu in my laptop alongside windows, using a bootable usb drive. But it always restart the mechine when select to install ubuntu with windows. I try some solutions in internet, but i didnt work....Could anyone please help me.

Laptop - HP- Pavillion DV6-3105tx

Thank you

---

### Post by fantab on 2013-10-22
Post the screen-shot of your Hard disk and partitions from Windows.
Can you boot ubuntu and "Try Ubuntu without installing? If you can then do so, open Terminal [ctrl+alt+t], run the following commands and post its output here:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by mastablasta on 2013-10-22
that's in windows disk manager.

if windows came preinstalled you likely have all 4 primary partitions occupied. ther eis a solution for that. but first post the data *fantab* requested, so we don't make a mess here.

---

### Post by 3rdalbum on 2013-10-22
Can you please describe in more detail exactly what you are doing and what happens before the computer restarts?

There are a number of different ways to install Ubuntu, so please tell me which one it is:

1. You insert the Ubuntu CD while Windows is running, it brings up a window which gives you the option to install Ubuntu "within" Windows. (by the way, this is not recommended anymore; it will work with Windows 7 but it's not a good way to install Ubuntu)

2. You insert the Ubuntu CD, reboot the computer and boot the computer from the CD. After a few minutes of loading, you're brought to a screen that asks you if you want to Install Ubuntu or Try Ubuntu.

---

### Post by harsha2 on 2013-10-22
Currenty laptop boot in Windows.  I want to create a dualboot with ubuntu. HDD is 500GB. there were 4 partitions. I created 40GB seperate partition and kept it as unallocated. then i boot laptop using a usb disk and try to install ubuntu. But the selection to Install ubuntu with Windows wont go further. When i select that option and click continue the laptop restart. some times that coutinue button appears as restart.

---

### Post by harsha2 on 2013-10-22
here are the images. 
[http://postimg.org/image/hvnd6l3vb/](http://postimg.org/image/hvnd6l3vb/)
[http://postimg.org/image/6xoewm2rb/](http://postimg.org/image/6xoewm2rb/)

---

### Post by fantab on 2013-10-22
If you've created 40GB partition as the fifth partition then Windows would have converted the HDD from 'Basic' to 'Dynamic'. Dynamic Disks will NOT work with Linux. A screen-shot from Windows Disk Management showing Partitions will confirm this.

The 'msdos' partition table has only four Primary partitions limit. To overcome this we use an Extended Partiion, which is a primary partition and acts as a container for Logical Partitions. Within an Extended Partition we can have 100 or more Logical Partitions. Linux can boot from a Logical Partition but Windows can't. More on this later...

But first you need to delete that fifth partition and reconvert the partitions to 'Basic'. BackUp all your important Data first.
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by harsha2 on 2013-10-22
These are the partitions view in ubuntu.
[http://postimg.org/image/eq34ov0c7/](http://postimg.org/image/eq34ov0c7/)

---

### Post by fantab on 2013-10-22
Gparted (from Ubuntu) will not show the 'Basic' or 'Dynamic' information. 'Dynamic' is a Window's proprietory feature and Linux won't work with it.

---

### Post by harsha2 on 2013-10-23
Thanks for your help... I installed Ubuntu.

---

