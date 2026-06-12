---
title: "Cannot install Ubuntu 16.04 (Dual boot with Windows 10)"
date: 2016-08-27
forum: New to Ubuntu
---

### Post by xali3n on 2016-08-27
[ATTACH=CONFIG]270907[/ATTACH]
This is my Device Management window. I have shrunk my Windows Partition which leaves 96GB for Ubuntu. My BIOS is UEFI as can be seen here:
[ATTACH=CONFIG]270908[/ATTACH]
When I hold shift then reboot I can open Ubuntu in a trial version from my USB stick. However when I press Install Ubuntu 16.04, I get an error message that says Ubuntu requires at least 8.4GB to be installed and the current storage only has 8GB, maybe because my USB drive has 8GB capacity

I am not sure what the problem is but maybe it is because Ubuntu cannot see my open partitions. 
Any help would be appreciated as I really would like to dual boot Windows 10 and Ubuntu.

---

### Post by yancek on 2016-08-27
Have you fully shut down windows and turned off hibernation before trying to install.  Select the option to "Try Ubuntu" and go to the Desktop and open a terminal and use gparted (sudo gparted) to see if the various partitions and unallocated space are shown.  If you are able to see the partitions after turning off hibernation, select the Something Else option as the Instalaltion Type.

---

### Post by mook765 on 2016-08-27
In addition to yancek's suggestions, please read this:
[http://askubuntu.com/questions/450677/ubuntu-14-04-not-detecting-free-space](http://askubuntu.com/questions/450677/ubuntu-14-04-not-detecting-free-space)

---

### Post by xali3n on 2016-08-27
> **yancek said:**
> Have you fully shut down windows and turned off hibernation before trying to install.  Select the option to "Try Ubuntu" and go to the Desktop and open a terminal and use gparted (sudo gparted) to see if the various partitions and unallocated space are shown.  If you are able to see the partitions after turning off hibernation, select the Something Else option as the Instalaltion Type.

I have opened gparted and this is what it shows me, any idea how to advance from this?
[ATTACH=CONFIG]270909[/ATTACH][ATTACH=CONFIG]270910[/ATTACH]

---

### Post by RobGoss on 2016-08-27
First and foremost, make a backup of any important files and data before you attempt to dual boot your machine I've seen many people loose entire OS's doing this it's best to be safe then sorry 

When dual booting Ubuntu and Windows, you will be given the option to install Ubuntu along side Windows, If this is the option you want choose it and the installer with take care of all the partitioning and swap partition for you, which in some cases is much easier for some users

I like to do my own partitions this gives you control of how much space each partition will have, if the installer does it for you it will decide for you and you will have to live with it. I think it's best to do your own partitioning because you have a better understanding how things work and learn at the same time

If you already created a partition and want to use it for your Ubuntu installation load up the live **DVD** or** USB** and when it loads in to the live session choose the installation option and then choose something else, this will allow you to choose that partition you created and begin installing Ubuntu on that partition. You will also have to create a swap partition as well.

What is a swap partition
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Hope this helps

---

### Post by mook765 on 2016-08-27
If you used the Windows built-in disk-manager to shrink the partition then you have a kind of dynamic disc (LDM). Ubuntu-installer will not recognize this disk.
Read in the link i posted before, it will give you a solution...

---

### Post by RobGoss on 2016-08-27
> **xali3n said:**
> I have opened gparted and this is what it shows me, any idea how to advance from this?
[ATTACH=CONFIG]270909[/ATTACH][ATTACH=CONFIG]270910[/ATTACH]


Your seeing this because it looks like it's displaying your USB disk space there should be the option to choose the partition you want to install Ubuntu on. I've gotten this option many times when installing Ubuntu on some of my machines I often have to reboot my machines and start the installation from scratch when this happens not sure what this happens

---

