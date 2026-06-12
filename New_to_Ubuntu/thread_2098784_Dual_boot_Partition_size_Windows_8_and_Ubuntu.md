---
title: "Dual boot Partition size Windows 8 and Ubuntu"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by bmbiehler on 2012-12-27
I have a 4+ year old Compaq Presario CQ40-215WM, AMD Athlon X2 QL-62 / 2.0 GHz ( Dual-Core ) CPU, 3GB RAM, 160GB HDD, ATI Radeon HD 3200 Video card.  I am currently running 64Bit Windows 8 Pro and had the system running Ubuntu 12.04LTS.  Now I want best of both worlds and dual-boot.
  First-off, How big should I make my partition for Ubuntu?  I am a new user to Linux and want to learn, but I still daily need Windows until I get fluent.  Bear in mind my HDD is just 160GB.
  Second, I was running Ubuntu 12.04 because it worked with my ATI video card and proprietary drivers were available, but is the upgrade to 12.10 recommended if I can't get the proprietary drivers to work?
  Thirdly, any upgrades you would suggest for my laptop, it isn't the newest, but it runs well and has some life left.

---

### Post by oldfred on 2012-12-27
Welcome to the forums.

How big is Windows 8? It used to be the minimum for 7 was 20, with 30 or more usually suggested depending on what you want to do. Somewhere I thought I saw Windows 8 wants twice as much as 7?

I install Ubuntu in 25GB but do keep almost all data on shared data partitions But only use 9GB with lots of software and .wine for Picasa using almost 2GB of the 9GB. 
When still booting XP I had a lot of data in a shared NTFS partition. Now all new data goes into a Linux data partition.

From live flash drive click on all partitions to mount them and post this:

df -h

Also:
       WARNING for Windows 8 Dual-Booters on hibernation issues
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by chubble10 on 2012-12-28
> **oldfred said:**
> How big is Windows 8? It used to be the minimum for 7 was 20, with 30 or more usually suggested depending on what you want to do. Somewhere I thought I saw Windows 8 wants twice as much as 7?

The minimum is 20GB for 64-bit. (See the system requirements: [http://windows.microsoft.com/en-GB/windows-8/system-requirements]("http://windows.microsoft.com/en-GB/windows-8/system-requirements"))

---

### Post by Cheesemill on 2012-12-28
I would recommend sticking with 12.04, as support for your graphics card has been dropped for 12.10.

---

### Post by audiomick on 2012-12-28
> **bmbiehler said:**
> First-off, How big should I make my partition for Ubuntu? 
I prefer to install Linux with a separate partition for /home. This can be simply re-mounted and re-used if you should have to re-install the Linux. 

The idea of using an NTFS data partition for files that you want to acces from both systems is a good one. If you do this, and are systematic about storing your files here, your /home can be pretty small too.

If you want your Linux install to hibernate properly, you will need to have a swap partition a tiny bit bigger than your RAM. You currently have 3GB RAM, so 3.1GB should be enough. The reason is that the hibernate function writes the RAM contents into the swap space to be recovered on re-boot. If that function is not important to you, about 1GB of swap should be more than enough.

I would (including a separate /home, and that you save all your files to an NTFS data partition) do something like this

30 GB for Win8
15GB mounted to / for the Linux system
15GB mounted to /home for the Linux home folder
3.1GB swap

The rest as NTFS data partition.

I have read of someone making his /home partition as small as 1GB and using symlinks to everything, but I think that is pushing things to extremes.

> 
  Second, I was running Ubuntu 12.04 because it worked with my ATI video card and proprietary drivers were available, but is the upgrade to 12.10 recommended if I can't get the proprietary drivers to work?

12.04 is a Long Term Support version. It will be supported for the next 3 years, as far as I know. There is no reason to update to the next version other than wanted to have the "newest". If your system works well, and you are concerned about hardware support on newer versions, stay with 12.04.

If you get itchy fingers, you can always try the newer release from a USB stick or CD to see if things work before installing it.

>   Thirdly, any upgrades you would suggest for my laptop, it isn't the newest, but it runs well and has some life left.

I would think about some more RAM if it were possible, but that is probably not really neccessary. If the machine is performing well for you, leave it as it is.

---

### Post by bmbiehler on 2012-12-28
Thank you for your responses.  I pretty much just Installed 12.04LTS 64bit.  As far as the partition, I just went with the option to Load along side with Windows 8 option, pretty much divided my hard drive in half, try it for a while and change it if I want more space either way later.  I probably will get some more RAM, it is on sale today on Amazon, 8GB is my max.  Thanks for the support, I will probably need more help in the future.

---

### Post by audiomick on 2012-12-28
> **bmbiehler said:**
> Thank you for your responses.  I pretty much just Installed 12.04LTS 64bit.  As far as the partition, I just went with the option to Load along side with Windows 8 option, pretty much divided my hard drive in half, try it for a while and change it if I want more space either way later.  I probably will get some more RAM, it is on sale today on Amazon, 8GB is my max.  Thanks for the support, I will probably need more help in the future.


That sounds great. Have fun with Ubuntu.

---

### Post by verzx on 2012-12-28
You will most likely be using Windows a lot more so i'd say go for 100gb windows and 60gb Ubuntu.

---

