---
title: "Installation problem Part2"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by petejbm on 2012-07-26
Hi, I could not install Ubuntu 12.04 until I was successful in getting trial to install but when I tried to install from the desk-top it goes to partition mgr and asks which partition, When I select one it asks me to select the file system. I have tried each FS in turn and each time I get error saying ;cannot find root file system. Go to Pm and select from menu.

Can anyone help please and advise what I am doing wrong.
I have since tried many times to install both trial and full but once again I am unsuccessful.

Petem

---

### Post by androssofer on 2012-07-26
> **petejbm said:**
> Hi, I could not install Ubuntu 12.04 until I was successful in getting trial to install but when I tried to install from the desk-top it goes to partition mgr and asks which partition, When I select one it asks me to select the file system. I have tried each FS in turn and each time I get error saying ;cannot find root file system. Go to Pm and select from menu.

Can anyone help please and advise what I am doing wrong.
I have since tried many times to install both trial and full but once again I am unsuccessful.

Petem

sounds like you are trying to do a custom partition.. is this necessary? 

here is a step by step guide that might help:

[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by petejbm on 2012-07-28
Hi and thanks for that info. Yes I am doing custom install as I have other stuff on two additional partitions and I do not want to wipe the whole disc.

I have read you info and I get as far as selecting the'other' button. That is where it goes haywire.
I then get Gpartition Mgr up showing my partitions. Good so far. I select the partition that I have set a boot and hit continue. I get a message that says 'Cannot find root file system. Please correct in Partition mgr'.
I have tried all the file systems available in the PM but get the same message each time. I assume that since I am using disc to install the system is aware of this and I do not have to mount the disc reader?

thanks
Petem

---

### Post by vipulkumar7 on 2012-07-28
i think you must use ext4 and atleast  give 2 gb for root directory "/ " and also use LVM at least 500 MB Try this it might help you :) :)

---

### Post by oldfred on 2012-07-28
You have to choose a partition, what format (ext4) and where to mount it /, swap, /home are the most common defaults.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Examples with screenshots. Installer version has not changed hardly at all, so version is not critical to examples:
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Install 12.04 side by side
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by arpanaut on 2012-07-28
I think this is the part you are missing:

---

### Post by petejbm on 2012-07-31
Thanks for the additional info. I have set partition to Ext4 but for the mount point I do not get a choice of the directories. All I get is a choice of partitions sda1, sda2 et al. I am trying to use sda1 which has 10GiB space all empty.

I have set additional partition for swap-file 2.5GiB

---

### Post by oldfred on 2012-07-31
From gparted you will not get the choices, just the capability to create partitions.

Then in the installer (Something Else) you can choose the partition, what format, and what mount point to use the partition as such as / (root). 

The installer does not have all the capabilities of gparted, so I always used gparted first. But installer does a lot more than it used to, so you do not have to use gparted first.

---

### Post by critin on 2012-07-31
> **arpanaut said:**
> I think this is the part you are missing:

> **petejbm said:**
> Thanks for the additional info. I have set partition to Ext4 but for the mount point I do not get a choice of the directories. All I get is a choice of partitions sda1, sda2 et al. I am trying to use sda1 which has 10GiB space all empty.

I have set additional partition for swap-file 2.5GiB

Look at the image link posted in above post.  See the red section with the mouse hovering?  That is (the mount point) what you want to choose.  Click it and it will go back to install in the partition you've chosen.  This is on the iso install page, **not in** gparted. ** Choose everything** from the install pages.  ext4,  journal file system, mount point, etc.

10 GiB is pretty small though it will work.

---

### Post by petejbm on 2012-08-13
Thanks again OldFred, I have now read your image of installation and it still freezes.

I have thus removed the 'quiet' and 'splash' and watch the installation process.

All goes well with 'OK' until the last output is 'crash report submission deamon' which is ok then it freezes.
I have to force switch off the try again.

I have used f6 and selected those items as suggested in f1 and have set vga=771 but still no good.

I do not even get as far as the second image in the install process.

HELP

---

### Post by oldfred on 2012-08-13
the vga= settings are obsolete. Normally it is nomodeset if a video issue, but may be some other settings instead or in addition to:

vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by petejbm on 2012-10-07
Hi aal, it is me again. New thought. Firstly does Linux use device drivers like Windows?
I managed to get Ubuntu 12.04 loaded and installed at last - don't know how but after push and pull here and there it installed and I managed to use it immediately. Then when I shut down and then attempted to restart guess what! You guessed - the thing froze again and refused to boot.
All the files and directories are there but I think there is a driver problem. I use NVidea Geforce go and while I was using the beast and adding add-on I got advice window showing three NVidia drivers - the one that I was using (174 I think) and then another that was recommended. So I chose the recommended one and continued to use the system without rebooting. After shutting dowm and rebooting that is when it froze. Can anyone advise how to get updated drivers for NVidia. I have been on their web site selected the drivers for my Acer but Linux does not recognise the setup.exe file

petejbm

---

### Post by petejbm on 2012-10-07
> **oldfred said:**
> the vga= settings are obsolete. Normally it is nomodeset if a video issue, but may be some other settings instead or in addition to:

vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Hi oldfred, very useful information there. I have tried nomodeset and vga=771 without success.
When vga set to 771 I noticed the difference on screen so that ok but when loading from disk it runs till output :-  eth0: tg3_reset_hw cannot enable BUFMGR is output.
Any ideas please
Pete

---

### Post by will1982 on 2012-10-07
> **petejbm said:**
> Hi aal, it is me again. New thought. Firstly does Linux use device drivers like Windows?
I managed to get Ubuntu 12.04 loaded and installed at last - don't know how but after push and pull here and there it installed and I managed to use it immediately. Then when I shut down and then attempted to restart guess what! You guessed - the thing froze again and refused to boot.
All the files and directories are there but I think there is a driver problem. I use NVidea Geforce go and while I was using the beast and adding add-on I got advice window showing three NVidia drivers - the one that I was using (174 I think) and then another that was recommended. So I chose the recommended one and continued to use the system without rebooting. After shutting dowm and rebooting that is when it froze. Can anyone advise how to get updated drivers for NVidia. I have been on their web site selected the drivers for my Acer but Linux does not recognise the setup.exe file

petejbm

Linux mainly uses open source drivers, not windows ones

---

### Post by petejbm on 2012-10-19
Hi all, firstly thanks to all those who have been patient and provided me with a wealth of information.

The story now is that at last I have managed to get V12.04 installed and running.
I believe the problem was the NVidia drivers as I had previously downloaded Windows drivers from ACER website.
These I kept trying to install. I now believe thatthey caused problems. So now I use the default drivers and all appears to be well.
So thanks again all

---

### Post by petejbm on 2012-10-19
:p> **petejbm said:**
> hi, i could not install ubuntu 12.04 until i was successful in getting trial to install but when i tried to install from the desk-top it goes to partition mgr and asks which partition, when i select one it asks me to select the file system. I have tried each fs in turn and each time i get error saying ;cannot find root file system. Go to pm and select from menu.

Can anyone help please and advise what i am doing wrong.
I have since tried many times to install both trial and full but once again i am unsuccessful.

Petem

---

### Post by petejbm on 2012-10-22
Just when I thought that everything was OK, the laptop plays up again.

I notice that to get UBUNTU to start up I have to go to Windows Vista install disc and install sound card driver. Then run problem solver. This causes the screen to freeze but when I switch off and the run ubuntu it starts up ok.

I have tried suspend and that restarts, mostly. but if I close down it freezes in the close down sequence.

So although I can fudge the start-up it is not the best scenario.

Any advice please
:(

---

### Post by petejbm on 2012-10-22
And another.
I have just updated 12.04 and after installed the files I need to restart the computer.

Well I tried and again it just freezes. I get the GRUB text asking me to run UBUNTU Linux 3.2.0-33-generic-pae
or recovery mode.
In recovery mode I check files, make free space and try to repair broken packages. In the latter it says file system up to date and asks me if I want to upgrade. When I say (n) it then goes and gives a long speal about error in downloading files.
just thought that I should mention all this.
I have then tried resume normal and it freezes part way through

---

### Post by petejbm on 2013-09-18
Hi all, the saga continues. I sometimes manage to get 13.4 booted up by deviouys means of using the help facility but rarely. Most often when booting up all appears to go well until just before complete when it freezes with the following error
[860-662343] tg3 0000:04:00.0 eth1:tg3_reset_hw cannot enable BUFMGR
can anyone explain this please and what can I do to resolve this issue
regards
pete

---

### Post by oldfred on 2013-09-18
It looks like your Ethernet is tg3, but supposedly an update was done in 2010 to fix similar issues.

What system is this?

One solution here?
[http://ubuntuforums.org/showthread.php?t=2078320](http://ubuntuforums.org/showthread.php?t=2078320)

---

