---
title: "Netbook setting up advice"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by TealLeader on 2012-02-05
Hi all,

I'm a complete beginner to Linux has recently decided to learn through Ubuntu on my new Acer Aspire One AO722 netbook. I want to install it as a dual-boot alongside Windows 7 Home Premium and need some help with the partitions.

1. Can I partition the hard drive using a bootable USB Ubuntu installer? If not, how would I go about doing so without a disc-tray?

2. Through the threads I've read, many mention a "Home" or "Personal Data" partition alongside Windows and Ubuntu system partitions. How does this partition work and how is it accessible to the operating systems?

3. I also read about a "Swap" partition. Can someone elaborate on that?

4. Finally, how should I partition the 500GB drive? I plan to keep Windows since I need Office for schoolwork and some other multimedia programs so I don't want to completely cripple the Windows part of the machine.

---

### Post by robgraves on 2012-02-06
1) Yes you can partition the drive via a USB Live Ubuntu session, just launch gparted from within the Live sessionn and you can many any changes you need to to the hard drive.

2) If you set up a home partition at /home then if you ever need to reinstall over the root partition / then you wont lose or have to recopy your personal data kept in your home partition, if this partition is a ext2, ext3, ext4 or really any format other than ntfs or fat16 fat32, then windows will not recognize it, as windows does not like to acknowledge partitions that are outside of its known formats.

3)The swap partition is less of an issue these days as computers have much more RAM, but the idea of the swap partition is to have hard drive space that is used for additional RAM as virtual memory, the OS will "swap out" tasks to this swap partition, I personally have a swap partition that is essentially never used, I believe the general idea is to have a swap partition 1 to 1 and a half times your total RAM if you ever needed to hibernate the system all of the contents of the RAM could be stored within the swap partition.

4) Up to you.

---

### Post by serge_o on 2012-02-06
> **TealLeader said:**
> Hi all,

I'm a complete beginner to Linux has recently decided to learn through Ubuntu on my new Acer Aspire One AO722 netbook. I want to install it as a dual-boot alongside Windows 7 Home Premium and need some help with the partitions.

1. Can I partition the hard drive using a bootable USB Ubuntu installer? If not, how would I go about doing so without a disc-tray?

2. Through the threads I've read, many mention a "Home" or "Personal Data" partition alongside Windows and Ubuntu system partitions. How does this partition work and how is it accessible to the operating systems?

3. I also read about a "Swap" partition. Can someone elaborate on that?

4. Finally, how should I partition the 500GB drive? I plan to keep Windows since I need Office for schoolwork and some other multimedia programs so I don't want to completely cripple the Windows part of the machine.


two pieces of advice

1. when running a USB Ubuntu installer, you may (or may not if you are lucky) run into a problem when you see the line "SYSLINUX 4.........bunch of numbers and stuff" and the netbook hangs. this happenes to some netbooks, if you have this - write here in this about this, there is a solution here in forum.


2. be careful with partitioning the drive - many netbooks come with drives where all 4 primary partitions are already used - that is, you can not just add another partition - you have to delete one of the factory partitions.  if this is the case - you can post here the description - we could help with that. because if you do not have enough experience with partitions - deleting partitions could be dangerous.


3. if you really need your windows, you should back up your factory hard drive - so that you can always restore it if anything goes really wrong (nothing is wrong or should be wrong with ubuntu - I run ubuntu on netbooks myself - but a backup is always handy). do you have a computer where you can store the whole harddrive of your acer?

when I installed Ubuntu alongside Win 7 Home Premium on an HP mini netbook with a 200GB Harddrive, I just did a full backup of the drive with Acronis True Image and copied that to my "big" home computer. 
If anything happens I can restore the drive exactly as it was before I installed Ubuntu.

beware : Backing up the hard drive is not the same as backing up just files. The backup of the hard drive saves all the partitions and partitioning info, so that you have an EXACT copy of the drive. i.e. after restoring this copy nobody even knows there ever was Ubuntu on the netbook.

Excuse me for this lengthy piece of advice - but I just want to make sure you have a good Ubuntu experience and dont break your Windows.

---

### Post by serge_o on 2012-02-06
> **TealLeader said:**
> Hi all,

I'm a complete beginner to Linux has recently decided to learn through Ubuntu on my new Acer Aspire One AO722 netbook. I want to install it as a dual-boot alongside Windows 7 Home Premium and need some help with the partitions.

1. Can I partition the hard drive using a bootable USB Ubuntu installer? If not, how would I go about doing so without a disc-tray?

2. Through the threads I've read, many mention a "Home" or "Personal Data" partition alongside Windows and Ubuntu system partitions. How does this partition work and how is it accessible to the operating systems?

3. I also read about a "Swap" partition. Can someone elaborate on that?

4. Finally, how should I partition the 500GB drive? I plan to keep Windows since I need Office for schoolwork and some other multimedia programs so I don't want to completely cripple the Windows part of the machine.


As to "how you should parition the drive" - remember one thing. Windows CAN NOT (well it can but in a rather perversive way - lets rather say it can not) access Linux Partitions, but Linux CAN access Windows Partitions natively. i.e. you just see windows partitions with no problems and can access all the files.


That is why it makes sense make rather small partition for Ubuntu - say 20% of the drive - 100GB and leave the rest for windows.  You can access all the Movies,Music etc on the windows part. from Ubuntu - that is no problem.

I did like this: out of 250 GB :   80 for Ubuntu, and the rest for Windows.

This way you always have all your files in Windows and in Ubuntu.

---

### Post by serge_o on 2012-02-06
> **robgraves said:**
> 1) Yes you can partition the drive via a USB Live Ubuntu session, just launch gparted from within the Live sessionn and you can many any changes you need to to the hard drive.


can he really make ANY changes like resizing NTFS parts? 
I mean he would certainly need to resize NTFS because windows takes the whole drive.
AFAIK resizing NTFS only works in specialized tools like Acronis, but does gparted or Ubuntu installer do the trick?

---

### Post by TealLeader on 2012-02-06
> **serge_o said:**
> two pieces of advice

1. when running a USB Ubuntu installer, you may (or may not if you are lucky) run into a problem when you see the line "SYSLINUX 4.........bunch of numbers and stuff" and the netbook hangs. this happenes to some netbooks, if you have this - write here in this about this, there is a solution here in forum.


2. be careful with partitioning the drive - many netbooks come with drives where all 4 primary partitions are already used - that is, you can not just add another partition - you have to delete one of the factory partitions.  if this is the case - you can post here the description - we could help with that. because if you do not have enough experience with partitions - deleting partitions could be dangerous.


3. if you really need your windows, you should back up your factory hard drive - so that you can always restore it if anything goes really wrong (nothing is wrong or should be wrong with ubuntu - I run ubuntu on netbooks myself - but a backup is always handy). do you have a computer where you can store the whole harddrive of your acer?

when I installed Ubuntu alongside Win 7 Home Premium on an HP mini netbook with a 200GB Harddrive, I just did a full backup of the drive with Acronis True Image and copied that to my "big" home computer. 
If anything happens I can restore the drive exactly as it was before I installed Ubuntu.

beware : Backing up the hard drive is not the same as backing up just files. The backup of the hard drive saves all the partitions and partitioning info, so that you have an EXACT copy of the drive. i.e. after restoring this copy nobody even knows there ever was Ubuntu on the netbook.

Excuse me for this lengthy piece of advice - but I just want to make sure you have a good Ubuntu experience and dont break your Windows.

Thanks for the detailed advice! I'd rather be safe than sorry. And yes, I do plan to do a full backup of the hard drive out of the box and copy it to my external hard drive before doing anything. The netbook is still coming in the mail so I'm just gathering background info before messing about. Regarding your point 2, how would I know if the hard drive is already partitioned?

---

### Post by serge_o on 2012-02-09
> **TealLeader said:**
> Thanks for the detailed advice! I'd rather be safe than sorry. And yes, I do plan to do a full backup of the hard drive out of the box and copy it to my external hard drive before doing anything. The netbook is still coming in the mail so I'm just gathering background info before messing about. Regarding your point 2, how would I know if the hard drive is already partitioned?


When you launch ubuntu live - you can use the utility named GPARTED to partition the drive. There you will see how many primary partitions you've got. if there are 4 - you will have to delete one of them.

---

### Post by I2k4 on 2012-02-09
The official instructions are here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

but I can't see why a real beginner would willingly salt Linux onto a hard drive when a lot can be learned about various alternatives using Live USB.  The one thing left out of the official instructions at Step 2 is that the Pendrive installer can set "Persistence" which permits saving settings and software installs between reboots.  A Persistent Live USB runs a little slower and won't last forever (gets bugs eventually) but is a great way to test alternative operating systems without installing the eternal GRUB boot loader on the hard drive.  The OS needs a couple of GB on the USB drive and the rest should be set as "Persistent" memory.

I've decided after experiments on Lubuntu (LXDE lightweight) for my Acer One and am still playing with Mint on Persistent Live USB for my main PC.  The main idea is experiment - there are more differences between all these versions than meets the eye on first impression.  Linux is a lot more fun when the hard drive you depend on is not at risk.

---

### Post by serge_o on 2012-02-10
> **I2k4 said:**
> The official instructions are here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

but I can't see why a real beginner would willingly salt Linux onto a hard drive when a lot can be learned about various alternatives using Live USB.  The one thing left out of the official instructions at Step 2 is that the Pendrive installer can set "Persistence" which permits saving settings and software installs between reboots.  A Persistent Live USB runs a little slower and won't last forever (gets bugs eventually) but is a great way to test alternative operating systems without installing the eternal GRUB boot loader on the hard drive.  The OS needs a couple of GB on the USB drive and the rest should be set as "Persistent" memory.

I've decided after experiments on Lubuntu (LXDE lightweight) for my Acer One and am still playing with Mint on Persistent Live USB for my main PC.  The main idea is experiment - there are more differences between all these versions than meets the eye on first impression.  Linux is a lot more fun when the hard drive you depend on is not at risk.

this is a good point - maybe it is a good idea to try a live system, unless you are completely sure you want linux on the system.

by the way - did you encounter the "syslinux hangs" problem with Acer One?

---

### Post by I2k4 on 2012-02-10
If you're asking me, I've never had any problem with any Live USB install using the Pendrive installer and Persistence - at first for many reboots the Live USB works exactly like a "real" install whenever the USB is in place, but eventually they seem to develop bugs like failing to find the computer's hard drive or suddenly deciding some password is required when no password was ever defined.  So I don't say Live USB is a reliable substitute for a real install, but it's an excellent no risk way to try out versions with full system functionality.

As for the current dual boot hard drive installation of Lubuntu 10.10 on my Acer One, no problems so far (knock on wood).  My only beef is Lubuntu's assortment of preinstalled software was not what I want, and I spent too much time uninstalling and then installing different programs:  Mint LXDE for me has much better Day 1 software.

---

### Post by serge_o on 2012-02-11
> **I2k4 said:**
> If you're asking me, I've never had any problem with any Live USB install using the Pendrive installer and Persistence - at first for many reboots the Live USB works exactly like a "real" install whenever the USB is in place, but eventually they seem to develop bugs like failing to find the computer's hard drive or suddenly deciding some password is required when no password was ever defined.  So I don't say Live USB is a reliable substitute for a real install, but it's an excellent no risk way to try out versions with full system functionality.

As for the current dual boot hard drive installation of Lubuntu 10.10 on my Acer One, no problems so far (knock on wood).  My only beef is Lubuntu's assortment of preinstalled software was not what I want, and I spent too much time uninstalling and then installing different programs:  Mint LXDE for me has much better Day 1 software.

I was asking about problems because there is a known issue with netbooks and USB boot. Good that you have none. 

Tell me, what is the reason for you to use 10.10 and not 11.10 on your ACER? Do you think that the newest version will run slower on a netbook? or is it because of unity?

I personally installed a normal 11.10 Ubuntu on my girlfriend's netbook HP (I personally run normal laptops and desktops also with 11.10) - and it runs rather ok, but sometimes I guess it is slower than it should be.
Did you have a bad experience with 11.10/11.04 so that you use 10.10?

for me one of the reasons not to use 10.10 was that they stuck with mozilla FF 3. and I wanted that my distro has the newest mozilla FF

---

### Post by I2k4 on 2012-02-11
I tested a lot of alternatives on Live USB over the last year or so, and found the 11.x versions of Lubuntu and even more Ubuntu/Unity 11.04/11.10 noticeably slower than 10.10 on the netbook.  I sometimes joke that I think between Unity and Gnome 3 Ubuntu versions (and Mint 12) are going through a sort of "Vista" phase, a major and more demanding but still half-baked OS rebuild, and they're leaving a lot of users behind.  

I haven't had problems keeping Firefox and Chrome up to date with Synaptic PM - the only terminal command I routinely use is:

sudo apt-get updates 

and that seems to goose the packages.  (I also learned to add "ppa" repositories to Synaptic to get other things.)  

I don't personally like Unity and as I wrote above prefer Mint preinstalled packages and its general look and feel, and so far am liking Mint 11 LXDE as a dual boot candidate for my main machine.

---

### Post by serge_o on 2012-02-12
> **I2k4 said:**
> I tested a lot of alternatives on Live USB over the last year or so, and found the 11.x versions of Lubuntu and even more Ubuntu/Unity 11.04/11.10 noticeably slower than 10.10 on the netbook.  I sometimes joke that I think between Unity and Gnome 3 Ubuntu versions (and Mint 12) are going through a sort of "Vista" phase, a major and more demanding but still half-baked OS rebuild, and they're leaving a lot of users behind.  

I haven't had problems keeping Firefox and Chrome up to date with Synaptic PM - the only terminal command I routinely use is:

sudo apt-get updates 

and that seems to goose the packages.  (I also learned to add "ppa" repositories to Synaptic to get other things.)  

I don't personally like Unity and as I wrote above prefer Mint preinstalled packages and its general look and feel, and so far am liking Mint 11 LXDE as a dual boot candidate for my main machine.

I see. maybe I should try 10.10 on the netbook, too. because 11.10 is rather slow (nevertheless - 11.10 is faster than the factory win7 install on that netbook, so changing to ubuntu was a gain in performance nevertheless).

as to keeping firefox up-to-date - up to date and "newest version" are different things.
when you do apt-get update in 10.10 you normally get the "up to date version" of the old firefox 3.6.xx. You can check on this - just look the version up in firefox-help-about firefox menu.  My up-to-date 10.10 Ubuntu shows 3.6.xx, but the current version of firefox is already 9.0.   that is, ubuntu 10.10 is stuck with the december 2010 version of firefox (if they did not change anything).
this is one of the disadvantages of ubuntu - a distro is locked within a major package version - so that you basically never get a newer version with an older distro(through apt-get  - if you want to you can download/compile manually or you  have to change distro for that)

chrome is a different story, as all google products are. they are always the newest version.

OOPS: I just checked and saw that firefox is now the latest version in 10.10, it installed with the last system update. nice.

---

### Post by TealLeader on 2012-02-12
> **I2k4 said:**
> Linux is a lot more fun when the hard drive you depend on is not at risk.

I guess I was getting ahead of myself. You're right, I shouldn't risk the drive just for initial learning. Thanks for the sober second thoughts. :)

The net book finally came but I currently don't have a USB large enough off of which to run Ubuntu comfortably. Is Wubi a good alternative or is that also risky for my hard drive?

---

### Post by PhilGil on 2012-02-13
No, Wubi won't pose a risk to your Window install. Your Ubuntu system is contained in a single Windows file. Because of that, Wubi isn't recommended for long-term use, but it will give you very good idea of what a native Ubuntu install will feel like.

---

### Post by I2k4 on 2012-02-14
I've had no experience with Wubi - my guess has been that on top of already slow W7 on my netbook it would be a strain and hard to gauge comparative performance.  USB is slower than HDD, but you get a pretty good feel for the zip of different Linux versions against each other and against Windows. The version 10 Ubuntu and Mint installs are all faster on USB than Windows 7 on HDD.

FYI, re Firefox, I used this to get the beta channel into Synaptic:

sudo add-apt-repository ppa:mozillateam/firefox-next
sudo apt-get update

I'm running FF11 beta in Linux (I don't go past FF9 in Windows because I like Cooliris image browser, which is slow to catch up with these new releases.)

---

