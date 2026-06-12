---
title: "2 beginner questions"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by electroblaze1989 on 2008-05-27
Hi.

I have 2 questions before i start installing Ubuntu.

1)I have a Turion 64 processor. Does this imply i should download the 64 bit counterpart of this OS?

2)My laptop came with Windows XP Home preinstalled. I am reluctant to remove this installation incase my siblings wish to use Windows. Can i install Ubuntu with this OS installed? Is it absolutely necessary to do it in another hard disk partition? It will mean moving a lot of files to make 4 GB free on my second partition.

Plz reply to these as soon as possible as i can't wait to get started.

Thanks.

---

### Post by adobrakic on 2008-05-27
I think only the really new computers are 64bit, you most likely have 32bit.

and yes, you can dual boot, that's what i do. and idk why it would take a lot to move the files, the ubuntu installation does it by itself. and i recommend 10gb, not 4.

---

### Post by sharks on 2008-05-27
1) u can install both 32 bit and 64 bit.

2) First put the live c ,boot it , open gparted from system--->administration and create a new partition of minimum 6 gb. change it as ext3. yes u can dual boot xp and ubuntu after install.

---

### Post by damansandhu on 2008-05-27
hi , you can install both 32 bit and 64 bit versions depending on your choice.
You can have both xp and ubuntu installed but u need to create atleast 4 - 5 gb for system files , some space for your home folder and some swap partition depending on your ram size.

---

### Post by kesman on 2008-05-27
> **adobrakic said:**
> I think only the really new computers are 64bit, you most likely have 32bit.

and yes, you can dual boot, that's what i do. and idk why it would take a lot to move the files, the ubuntu installation does it by itself. and i recommend 10gb, not 4.

Please don't answer if you don't know. Turion 64-bit is 64-bit processor, and you can install either 32-bit or 64-bit version of ubuntu.

---

### Post by cdtech on 2008-05-27
> 1)I have a Turion 64 processor. Does this imply i should download the 64 bit counterpart of this OS?

If it states 64 then you can take advantage of the speed.

> 2)My laptop came with Windows XP Home preinstalled. I am reluctant to remove this installation incase my siblings wish to use Windows. Can i install Ubuntu with this OS installed? Is it absolutely necessary to do it in another hard disk partition? It will mean moving a lot of files to make 4 GB free on my second partition.

Do you mean second drive?

You can just create a partition within Window's (using Window's) and have Ubuntu utilize that partition you created.

---

### Post by dopple on 2008-05-27
You may want to try installing VirtualBiox and installing XP on that. This means your siblings will have to go through an extra step to get to theirs and forces them to open Ubuntu to get to XP. They may find they like Ubuntu.

---

### Post by cdtech on 2008-05-27
> **dopple said:**
> You may want to try installing VirtualBiox and installing XP on that. This means your siblings will have to go through an extra step to get to theirs and forces them to open Ubuntu to get to XP. They may find they like Ubuntu.

What a salesman, :lolflag:

---

### Post by dopple on 2008-05-27
Do I get any commission for that?:)

---

### Post by electroblaze1989 on 2008-05-27
Okay i got the 64 bit part alright...thanks a ton.

But i'm a little confused as to the second part.

Do you guys mean that if during installation i ask Ubuntu to create a drive partition in say C: where i have 20 GB free, it will not affect existing files on that drive? i have never partitioned before so i really do not know.

My siblings aren't very technology friendly so they might not take the switch kindly. But yes they are used to multiple-boot as not long ago i had two versions of Windows running on my desktop.

---

### Post by dopple on 2008-05-27
It shouldn't affect it, but it's always worth backing up just to be on the safe side.

---

### Post by kesman on 2008-05-27
Exactly. If you have spare 20gig on your primary drive(C:), then you can shrink the existing partition and leave the rest of the disk unpartitioned. Then ubuntu will install itself onto that and you will get a menu at boot-up prompting you to select either ubuntu or windows.

---

### Post by cheesypoof on 2008-05-27
Start > Run > compmgmt.msc

Shrink your XP partition, so there is enough space for Ubuntu.

On Install make sure you use the "guided - use the largest continuous free space" option.

Next time you restart, you should have the menu to select which operating system to boot into. You can edit the default booting operating system by modifying your grub file on ubuntu. Unfortunately I forgot the location of it.

---

### Post by dopple on 2008-05-27
/boot/GRUB/menu.lst
Change this to say which operating system you want to load 1st, how long you have to select it etc.

---

### Post by oedha on 2008-05-27
you can not use the whole 20 GB......windows still needs some space to run
manage your partition wisely........and dont forget to defrag your windows before you install ubuntu
maybe use only up to 10GB...for linux and swap partition
you can use [http://gparted.sourceforge.net](http://gparted.sourceforge.net) to manage your partition
:)

---

### Post by electroblaze1989 on 2008-05-27
I suppose i can change that using XP also, isn't that correct?
so basically i just proceed directly with the installation and when asked, i ask the installer to create a partition out of my existing drive. It will create a partition and leave my files as they are in  the now shrunken partition.
Plz tell me one final time if i have got it right.

---

### Post by cheesypoof on 2008-05-27
Remember when we are talking about partitions, understand that they are separate from each other. What you are doing is splitting your hard drive into sections. Once you shrink the XP partition, free space is created. If you use the "guided - use the largest continuous free space" option in the ubuntu install, it will not overwrite your xp files. This is because to the installer, your xp partition is not free space. If I were you, I would definitely use the Disk management tool in Windows to shrink your partition instead of anything else. Good luck, make sure to post if you are successful or have any other questions.

---

### Post by electroblaze1989 on 2008-05-27
I am still not getting the hang of the partition thing...i'm really sorry...
if you can please guide me to a tutorial if one is available , i'd be really grateful. i'm not able to use Gparted as there is no executable file in there. am i supposed to use it in some other way?

---

### Post by cheesypoof on 2008-05-27
Your hesitation to follow through with this is making me nervous, almost like you might unintentionally mess something up. Maybe a Wubi install is your best option for now until you develop a more complete understanding.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Wubi Guide

[http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

The key difference between a traditional install and Wubi is that with Wubi, your ubuntu is on your windows partition. There is no risk of overwriting by the way with this method.

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
Good general knowledge set for switching from windows.

---

### Post by electroblaze1989 on 2008-05-27
the thing is i have already downloaded the iso file and it will take me more 8 hours for that 700MB download....i don't have a very fast internet connection...don't worry i won't mess up..i'll just need the instructions in general to set up a disk partiton..i'll tell you how things stand

HDD size :  60GB
Free Space :  ~20GB
Partition recommended by guys over here was 10GB at least..

now just tell me stepwise how to do it...

---

### Post by electroblaze1989 on 2008-05-27
Ps. i though Ubuntu was free...then why do we need live cd? i'm downloading from here

[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)

---

### Post by billgoldberg on 2008-05-27
> **electroblaze1989 said:**
> Hi.

I have 2 questions before i start installing Ubuntu.

1)I have a Turion 64 processor. Does this imply i should download the 64 bit counterpart of this OS?

2)My laptop came with Windows XP Home preinstalled. I am reluctant to remove this installation incase my siblings wish to use Windows. Can i install Ubuntu with this OS installed? Is it absolutely necessary to do it in another hard disk partition? It will mean moving a lot of files to make 4 GB free on my second partition.

Plz reply to these as soon as possible as i can't wait to get started.

Thanks.

1) you could install the 64bit, but I would suggest using the 32bit (better documention and support).

2) you could use the new wubi installer (installs ubuntu from within windows without the need for partitioning).

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by dopple on 2008-05-27
Here's a step by step tutorial which explains how to use the partitioner that comes as part of the setup process. [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
I never had any problems with using this (I'm still a virtual noob too) but like I said, backup and also defrag xp. 10GB is fine for a partition although I can guarantee you will out grow this in no time once you start moving over to Ubuntu more and more.

---

### Post by sayakb on 2008-05-27
Give 10GB to / and some more to /home. You will virtually never use up the entire /

---

### Post by sayakb on 2008-05-27
> **electroblaze1989 said:**
> Ps. i though Ubuntu was free...then why do we need live cd? i'm downloading from here

[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)

Unless you have downloaded the Alternate install CD, it is infact the LiveCD that you're downloading.

---

