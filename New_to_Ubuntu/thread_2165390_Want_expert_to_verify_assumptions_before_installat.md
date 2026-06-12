---
title: "Want expert to verify assumptions before installation"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by maxws43 on 2013-08-04
Want an Ubuntu expert to verify some assumptions before I attempt to  install.  I am currently using Windows XP.  With support for XP ending I  do not want to continue using it.  Instead of going to the expense in  both time and money of upgrade Windows I am looking at Ubuntu.  I have  an old PC (Pentium 4) with XP on disk A (80 GB).  Disk B  (320 GB) has 80 GB free at the beginning and the rest is used for data.    I want to install Ubuntu on disk B, and then when I am sure I can do  everything I need to do on Ubuntu replace disk A with a new larger disk  for additional data storage.  Questions: 

1:  Is 80 GB enough for Ubuntu 12.04 and swap?
2:  With 4 GB memory is 8 GB the correct swap size (read swap should be 2 times memory)?
3:  Am I correct in assuming that putting the dual-boot on B will allow me to remove disk A with no problems?
4:  I read that Ubuntu can only read NTFS.  I have some old USB drives  formatted in FAT32 and some old backup info on floppies (from before USB  drives).  Do I have to convert all that to NTFS before I delete  Windows?
5:  Will WINE allow me to run any Windows utility I can not find a replacement for?  Would that fix item 4?

Any suggestions would be appreciated.

---

### Post by MG&amp;TL on 2013-08-04
I wouldn't call myself an expert (all volunteers here!), but in answer to your questions:

[LIST=1]
[*]Yes, you won't use very much of that at all. 
[*]No, that's a rule of thumb. 4GB RAM is more than enough, so 8GB of swap will probably be overkill. 2GB in my experience is more than sufficient for all installations. 
[*]Yes, if you install Ubuntu on disk B, it won't touch disk A at all and will just see it like any other drive you plug in. 
[*]No, Ubuntu can read FAT as well. I have previously had issues with floppies not mounting automatically, but it is perfectly possible to do it manually. 
[*]WINE is not a 'magic bullet': it runs some (I would be tempted to say most) programs perfectly, some imperfectly, and some not at all. Check out [http://appdb.winehq.org/](http://appdb.winehq.org/) 
[/LIST]

However, I would not recommend Ubuntu for a Pentium IV, I imagine that the interface will be too much for the machine. I would suggest Xubuntu (light) or Lubuntu (lightest) instead, which are identical to Ubuntu but come with a lighter interface.

---

### Post by uc50_ic4more on 2013-08-04
1) 80GB is plenty! I have my installation on a 10GB partition.
2) If you have 4GB of RAM I cannot see the old 2:1 ratio of swap to RAM being anywhere near necessary. "Should" is used loosely when determining how much swap you need.
3) As long as you haven't set your installation to use disk A for anything important (ie. your "/" partition, "/home" or swap) you ought to be fine.
4) My Ubuntu installation has no issues writing to NTFS. I think you'd want the "ntfs-utils" package.
5) WINE is hit and miss. Their web site has a pretty comprehensive list of what does and does not work.

I note the post above mine recommends against using the full Ubuntu experience with a P4. I have used Ubuntu on a P4 and it has worked, but I wouldn't call it "snappy". When installing for others with P4 systems I usually install the Gnome fallback interface ("gnome-session-fallback"?) Xubuntu'd be a great alternative.

---

### Post by steeldriver on 2013-08-04
Just a couple of points that I don't think anyone has mentioned yet

2) if you plan on hibernating the system, you need at least as much swap as physical RAM i.e. 4GB (even though the system may rarely benefit from that much swap space while running)

3) the installer may default to installing the grub boot loader on your A disk - in which case the system will become unbootable if you subsequently remove that disk (although that situation would be repairable, using a live CD or USB to reinstall grub to disk B)

---

### Post by ebyeby6 on 2013-08-04
> **steeldriver said:**
> 3) the installer may default to installing the grub boot loader on your A disk - in which case the system will become unbootable if you subsequently remove that disk (although that situation would be repairable, using a live CD or USB to reinstall grub to disk B)

I really think that part of the installer should be much more obvious, clearer, warning lights etc. I have rendered a machine unusable because I didn't pay close enough attention to the grub installer selection that is automatically populated. maxws43, just be careful during install at this step:  [http://pix.toile-libre.org/upload/original/1349879961.png](http://pix.toile-libre.org/upload/original/1349879961.png). You will need to select "Something else" and select the drive manually.

---

### Post by oldfred on 2013-08-05
Good points by all above. And you do have to use the something else option to get the choice to install the grub2 boot loader to sdb. Otherwise with all the auto install options it installs the boot loader to sda. Some suggest just disconnecting drive if you are willing to do that.

Not too many dual drive install examples, a couple of older ones, but install process is essentially the same across all recent versions if in BIOS mode not the new UEFI mode.
       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by grahammechanical on 2013-08-05
What graphic adapter do you have? I have seen a massive improvement in running Ubuntu by putting in a high specified graphic card. People mention the CPU & the RAM but I think that the power of the graphic adapter and the amount of memory it has is just as important to how well an OS appears to run.

Regards.

---

### Post by maxws43 on 2013-08-06
> **oldfred said:**
> Good points by all above. And you do have to use the something else option to get the choice to install the grub2 boot loader to sdb. Otherwise with all the auto install options it installs the boot loader to sda. Some suggest just disconnecting drive if you are willing to do that.

Not too many dual drive install examples, a couple of older ones, but install process is essentially the same across all recent versions if in BIOS mode not the new UEFI mode.
       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Oldfred, thanks for the information.  Looking at the instructions they start by deleting everything from sdb.  My sdb has an empty 80GB primary partition and then a 240 GB extended partition which is 2/3 full of data.  Do I have to delete the extended partition or can I split the 80 GB for system and swap?  (The data is all backed up except for a 30GB Window system backup, but a reload would be lengthy.)  That would put the swap in a primary versus a logical partition.  Is that OK?  

I think the best place for the boot loader is sdb.  Then when I am ready to delete Windows I should have no problem booting directly to Ubuntu.  Or am I missing something?

---

### Post by oldfred on 2013-08-06
If you use gparted in advance or manually partition sdb, and have enough room for / (root) about 25GB suggested but can be 10 to 25GB and swap at 2GB just to have some. Since you have other data partitions you may not need the separate /home  that we sometimes suggest.

I always try to make the install to a drive have boot loader and all necessary system folders so that drive can boot without any other drive. If other drive fails entry in fstab for a data partition may give an error but system will boot. If boot loader  is on one drive and system on another you need both drives to alway work to boot. Of course having a live installer or other Linux repair flash drives is also a good idea.

---

### Post by pyroph2 on 2013-08-06
Do you recommend disk paritioning *before *installation or the automatic partitioning during installation is enough to use Ubuntu without any problem?

---

### Post by 1clue on 2013-08-06
I'm not going to repeat stuff that's been said a bunch of times, but I have a couple pointers.

First, make sure you get a 32-bit download.  You probably already knew that.  :)
Second, you might want to look at a lightweight distro, like Lubuntu or Xubuntu.  Ubuntu is aimed at heavier processors IMO.

---

### Post by oldfred on 2013-08-06
If you have unallocated space and an available primary partition the auto install does work, but it chooses partition sizes for / (root) and swap. 
I have always preferred more control so I partition in advance, but if a new user the auto install works just fine.

---

### Post by JDorfler on 2013-08-06
I wrote this while back.  This more than likely will help you.  Just click [here]("http://jdorfler.blogspot.com/2008/09/dual-booting-xpubuntu-and-keeping-them.html").

---

### Post by SuperFreak on 2013-08-06
Not sure if this was mentioned but you can "Test Drive" Ubuntu or one of it's derivatives like Xubuntu with a live disc. So once you have decided what OS you want and burned the ISO to disc  just insert it into your CD drive and boot to CD (you may have to adjust boot order in BIOS). This will allow you to 1) see how it runs on your system and 2) see if you like it before actually installing it.

---

### Post by kevdog on 2013-08-07
I always partition my disks with Gparted rather than the installer based partitioning method.  Gparted gives better control, and frankly its very simple to use.

---

### Post by kurt18947 on 2013-08-07
I am something of a serial installer, different distros etc.  I haven't created a swap *partition *in years, even on machines with 2 GB.RAM.  If I feel the need for swap, I create a swap* file.*  I've installed htop and monitored memory usage while performing my normal tasks and don't recall the last time RAM actually used exceeded 1 GB.  I don't use "heavy" apps often though.  'MSDOS' formatted disks can only have 4 primary partitions and I don't use hibernate,  I use suspend which does not require a swap partition.  Cold boots take less than 1 min. so if I'm going to unplug a laptop for any length of time I just shut down.

---

### Post by calebbohon on 2013-08-13
It depends on what situation you have. If it is something complicated, like what [**[COLOR=#000000]maxws43[/COLOR]**]("http://ubuntuforums.org/member.php?u=1844738") wanted to do, then use the partitioner during instalation to set it up exactly how you want it. 

However, if you just want to remove the current operating system or do a basic dual boot situation then the auto partitioning should work fine. (But do a back up of your critical files before just in case.)

---

