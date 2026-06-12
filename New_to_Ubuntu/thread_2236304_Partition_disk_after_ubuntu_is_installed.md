---
title: "Partition disk after ubuntu is installed"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by aaron50 on 2014-07-25
Hi all,

I just installed ubuntu server onto an old laptop I have lying around. I am creating a test media server, so I know what I am doing when I build a nice one. When I installed ubuntu I chose to automatically partition with LVM. I chose to use 20gb of my 100gb hard drive. I got samba to work with my pcs last night, but I don't want to put all my media on the root partition. I would like to basically create a new hard drive with my 80gb I have left over. How do I go about partitioning and setting up the other part of my hard drive. Code would be great, or a website with step by step instructions as I am very new to Linux/ubuntu. I know it is probably not recommended to use the hard drive that the root is on, but like I said this is a test system and I am just trying to use my available resources. Thank you so much in advance for any help.

---

### Post by JeQhdMD on 2014-07-25
Download a decent "Live Distro" designed for disk mgmt:   [http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted)

---

### Post by aaron50 on 2014-07-25
Thank you for the advice. I am really looking to do this all through the command line without a gui. If that is what this is I apologize, can you give me some more information on this and what it is? Thanks

---

### Post by MidnightGrey on 2014-07-25
ahh you installed ubuntu already correct?
So you should already have gparted installed (it comes with ubuntu).

what version of ubuntu are you running?

---

### Post by aaron50 on 2014-07-25
14.04 is my version. I believe I set it up correctly. Like I said I am brand new to Linux and ubuntu command line. I followed many step by step guides and most said let use partition automatically with LVM or whatever and only use about 20gb for the server. So I am trying to be able to use the other 80 and point my samba to it so that people on my network can only access the media part of the server and not the root or anything.

---

### Post by JeQhdMD on 2014-07-25
A live disk (or usb flash-stick) is a full Linux OS on read-only media.  It's generally considered the safest way to manipulate hdd partitions, tables, flags, file types, labeling, etc.   Most use gui desktop as visualizing the hdd can help in cleaner operations.

gParted has the standard CLI bash interface and the gui.  If you view the Ubuntu Software Center app, and search for parted, you will see the basics including screenshot.

Here is another link to something that "may" help accomplish your end goal??, but I'm not experienced in CLI disk mgmt (other than the basics commands).  Here's the link:

[https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb)

---

### Post by deadflowr on 2014-07-25
Advice in post #2 is the best option.
You need to have the partition that will be resized unmounted.
If you are running the system, then you can't unmount it to resize.

I would suggest something like puppy linux, simple and easy.

Beyond that, though, Ubuntu should have parted installed for you.

simple run
```
man parted
```
to get the manual for how use it.
More here probably
[http://www.thegeekstuff.com/2011/09/parted-command-examples/](http://www.thegeekstuff.com/2011/09/parted-command-examples/)

For the record, though, Ubuntu's live session cd/dvd/usb comes with gparted, so you can resize partitions with it on a live session, but it does not get installed on the system.
This is only for the desktop version, not the server version. Server version wouldn't have any need for a gui program, or a live session for that matter.

---

### Post by oldfred on 2014-07-26
If you installed with LVM, you cannot use gparted. You have to use LVM tools.
LVM is a logical partition scheme that overlays the physical partitions.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by gordintoronto on 2014-07-26
My choice: use the entire disk with no LVM. For a server on a small hard drive, I see no advantage to multiple partitions.

---

