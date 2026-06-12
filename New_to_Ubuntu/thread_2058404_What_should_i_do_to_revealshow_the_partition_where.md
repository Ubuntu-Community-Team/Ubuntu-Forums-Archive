---
title: "What should i do to reveal/show the partition where i installed the Ubuntu?"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by Strzz on 2012-09-15
I'm recently installed my pc with a copy of Ubuntu 12.04 LTS.
When i install it, i'm using the second partition of my HDD,
1 st partition 85GB with Windows Xp Professional installed there.
2 nd partition 155GB with the ubuntu,

#1
The problem is, i can't open/show the 2nd hard drive partition where i installed the ubuntu. Only the 1st partition which i installed Windows XP Professional Shows up at the taskbar. Does anyone know how to show the 2nd partition?

#2
This morning(in Indonesia time), i'm trying to connect my laptop HDD to get some data from there. On 1st boot, i tried to open it via Windows Xp. It was a success, but after that, i installed some programs and it requires a restart. After i restart, the windows asked me to do a CHKDSK, there was 30errors found on the laptop HDD, the CHKDSK fixed it. But, when it entered Windows XP(finished loading), it gave me an error message on a blue screen similar to the BSOD, "the /windows/system32/ is corrupt". And the windows restarted it self. ending in the same blue screen again and again.
Did anyone knew a way to fix the windows via ubuntu? Or a way to let me play windows games?

My PC spec:
Acer Aspire E500
Pentium IV @3.20GHz
Ram 2GB DDR2 V-Gen
ASUS Nvidia GeForce EN8500GT Silent Magic 512MB PCI-E
Seagate Baracuda 250GB (dont know how many RPM this HDD got) Have 2 partitions 1st Windows XP Professional, 2nd Ubuntu 12.04 LTS "Precise Pangolin"
Seagate Momentus 500GB @5400rpm (have 2 partitions: 1st Windows, 2nd Data)

---

### Post by yoreei on 2012-09-15
Hi and welcome to the forums!
#1a
You can view your partitions with almost any file system manager (this is something like *My Computer* on Windows). The problem is that I don't know which one you are using so let's install thunar first. Open the console and type:
```
sudo apt-get install thunar
```Then start thunar by typing
```
thunar
```in the console.
This is a file manager that I am sure shows your partitions on the left pane. You will probably find your Ubuntu and Windows partitions there.
#1b
Alternatively, if you don't want to install anything and are comfortable with the console, just open it and type 
```
cd /
```This will lead you to the root (Ubuntu) partition.
Then to see what is there type:
```
ls
```To open a folder type:
```
cd foldername
```to run a file type:
```
./filename
```#2a
In my opinion you probably have malware on you windows system. I can't think of any other way to repair it except from the Windows CD. If this doesn't work or you don't have one (Windows CD) you should probably ask this on a Windows forum.

#2b
To run Windows software on Linux I personally use [Wine]("http://www.winehq.org/"). There are other layers that allow this but they are all based on Wine.
To install Wine type:
```
sudo apt-get install wine
```To run a Windows executable (.exe file) you (in most cases) just click on it. If this doesn't work, find a way in your file system manager to choose with which application to open this file and choose wine.

**!WARNING!** If you are using Ubuntu 64 bit you should open the application with 
```
wine64
```or you will not have sound. Everything else would be fine, though.
For more info check [http://wiki.winehq.org/FAQ#head-60c5de309a53bb8ed07d8af1ca26db129334cb43](http://wiki.winehq.org/FAQ#head-60c5de309a53bb8ed07d8af1ca26db129334cb43)
;)

---

### Post by critin on 2012-09-15
> **Strzz said:**
> "the /windows/system32/ is corrupt"[/COLOR]**. And the windows restarted it self. ending in the same blue screen again and again.
Did anyone knew a way to fix the windows via ubuntu? Or a way to let me play windows games?

My PC spec:
Acer Aspire E500
Pentium IV @3.20GHz
Ram 2GB DDR2 V-Gen
ASUS Nvidia GeForce EN8500GT Silent Magic 512MB PCI-E
Seagate Baracuda 250GB (dont know how many RPM this HDD got) Have 2 partitions 1st Windows XP Professional, 2nd Ubuntu 12.04 LTS "Precise Pangolin"
Seagate Momentus 500GB @5400rpm (have 2 partitions: 1st Windows, 2nd Data)

You'll  most likely need to insert the windows cd and choose'repair' if you can.  Some files are missing, probably the boot.
Do you have a restore partition on the computer that yu can get to when the Bios screen comes up?  Do you remember seeing it there?

After windows is repaired and working, you will want to reinstall ubuntu--it sounds like it didn't install correctly.

---

### Post by critin on 2012-09-15
> #1
The problem is, i can't open/show the 2nd hard drive partition where i  installed the ubuntu.[COLOR=Blue]** Only the 1st partition which i installed Windows  XP Professional Shows up at the taskbar.**[/COLOR] Does anyone know how to show  the 2nd partition?

#2
This morning(in Indonesia time), i'm trying to connect my laptop HDD to  get some data from there. On 1st boot, i tried to open it via Windows  Xp. It was a success, but after that, i installed some programs and it  requires a restart.

A question please.  What do you mean by 'TASKBAR'?  

 #1.  Do you mean that the boot screen does not show ubuntu **and** Windows so you can't boot into ubuntu?  It only shows XP?

#2  You opened ubuntu files from the [COLOR=Blue]file manager 'TASKBAR'  via XP successfull[/COLOR]y?  You then installed a program into a ubuntu file from XP and that messed up Windows?

So you weren't able to boot into ubuntu from the boot screen ever?
I'm just a little confused.  Sorry...I don't want to steer you wrong.

---

### Post by Bashing-om on 2012-09-15
struzz; Hi ! welcome to the forum.

problem solving, to me, is one-step-at-a-time.
1. Boot into the install cd  -try ubuntu- open terminal ctl+alt+t =>
     from the terminal post the out put of:
```

sudo fdisk -lu
sudo parted -l

```(those are lower case "L's")
 this shows your disk "layouts" and insures I am aware of what we are working with.
2. Repair your windows with window's chkdsk utility. (advise me if you can no longer boot into windows. and will fix booting first)
3. Then we will get the boot into our grub difficulties resolved with the live cd.

see tutorials:
[howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/]("http://ubuntuforums.org/howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/")
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)


We are all eager to assist and get the situation resolved such that you are ubuntuin'[INDENT]kind regards <==BDQ
[/INDENT]

---

### Post by Strzz on 2012-09-15
> **yoreei said:**
> Hi and welcome to the forums!
#1a
You can view your partitions with almost any file system manager (this is something like *My Computer* on Windows). The problem is that I don't know which one you are using so let's install thunar first. Open the console and type:
```
sudo apt-get install thunar
```Then start thunar by typing
```
thunar
```in the console.
This is a file manager that I am sure shows your partitions on the left  pane. You will probably find your Ubuntu and Windows partitions there.
#1b
Alternatively, if you don't want to install anything and are comfortable with the console, just open it and type 
```
cd /
```This will lead you to the root (Ubuntu) partition.
Then to see what is there type:
```
ls
```To open a folder type:
```
cd foldername
```to run a file type:
```
./filename
```#2a
In my opinion you probably have malware on you windows system. I can't  think of any other way to repair it except from the Windows CD. If this  doesn't work or you don't have one (Windows CD) you should probably ask  this on a Windows forum.

#2b
To run Windows software on Linux I personally use [Wine]("http://www.winehq.org/"). There are other layers that allow this but they are all based on Wine.
To install Wine type:
```
sudo apt-get install wine
```To run a Windows executable (.exe  file) you (in most cases) just click on it. If this doesn't work, find a  way in your file system manager to choose with which application to  open this file and choose wine.

**!WARNING!** If you are using Ubuntu 64 bit you should open the application with 
```
wine64
```or you will not have sound. Everything else would be fine, though.
For more info check [http://wiki.winehq.org/FAQ#head-60c5de309a53bb8ed07d8af1ca26db129334cb43](http://wiki.winehq.org/FAQ#head-60c5de309a53bb8ed07d8af1ca26db129334cb43)
:wink:

Thx for the reply.
I think i'll stick with the #1a option since i haven't got the time to study how to use the commands on terminal yet. XD
As  for the use of wine, i already installed wine, but i couldn't search  for the game/software files which i installed at the 2nd partition(the  partition where i installed Ubuntu previously). It only appeared as C  for the 1st and Z for the ubuntu files with no trace of the folders  which were on the D drive(2nd partition on windows).


> **critin said:**
> You'll  most likely need to insert the windows cd and choose'repair' if you can.  Some files are missing, probably the boot.
Do you have a restore partition on the computer that yu can get to when the Bios screen comes up?  Do you remember seeing it there?

After windows is repaired and working, you will want to reinstall ubuntu--it sounds like it didn't install correctly.

It didn't have a recovery partition. And i don't have the installation disc. I'll find another way then.
But it made me wondering, the first time that error occured is on my laptop which has a cracked Wind 7 Ultimate. Then after my laptop was disabled(unable to run Puppy linux and Wind7, i connected the HDD to this PC. After a while, the windows Xp freezes, when i restarted the system, it gave a BSOD like error message.
I really needed some of the files from my laptop's HDD, to finish my assignment. I haven't tried to access that damned HDD from ubuntu because i'm afraid the ubuntu will also be affected by that malware too.

Sorry for the questions that's not linked to linux/Ubuntu. I haven't got the chance to back up those data, because i don't have any spare HDD or DVDs. LOL

---

### Post by Strzz on 2012-09-15
> **critin said:**
> A question please.  What do you mean by 'TASKBAR'?  

 #1.  Do you mean that the boot screen does not show ubuntu **and** Windows so you can't boot into ubuntu?  It only shows XP?

#2  You opened ubuntu files from the [COLOR=Blue]file manager 'TASKBAR'  via XP successfull[/COLOR]y?  You then installed a program into a ubuntu file from XP and that messed up Windows?

So you weren't able to boot into ubuntu from the boot screen ever?
I'm just a little confused.  Sorry...I don't want to steer you wrong.

Oh yeah, i'm sorry.. I don't remember the bar on the left side of the screen in Ubuntu. is it Unity?

#1. It shows. The problem is, when i already got logged in on Ubuntu, there was only 1 Drive, the 85GB partition, the partition where my windows XP was installed. The other partition doesn't shows up. What should i do to make it appeared on the Ubuntu?

#2 Nvm about that question then.. it's not an error caused by linux. i just wondering if there's any way to fix windows, from linux without using any repair CDs. Maybe, someone who already got into this kind of situation before.

I'm able to boot to linux. I just haven't got the time to learn how to use the terminal and the commands as well.

sorry for the misleading questions asked, mate. i think my english is not that good.

---

### Post by Strzz on 2012-09-15
> **Bashing-om said:**
> struzz; Hi ! welcome to the forum.

problem solving, to me, is one-step-at-a-time.
1. Boot into the install cd  -try ubuntu- open terminal ctl+alt+t =>
     from the terminal post the out put of:
```

sudo fdisk -lu
sudo parted -l

```(those are lower case "L's")
 this shows your disk "layouts" and insures I am aware of what we are working with.
2. Repair your windows with window's chkdsk utility. (advise me if you can no longer boot into windows. and will fix booting first)
3. Then we will get the boot into our grub difficulties resolved with the live cd.

see tutorials:
[howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/]("http://ubuntuforums.org/howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/")
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)


We are all eager to assist and get the situation resolved such that you are ubuntuin'[INDENT]kind regards <==BDQ
[/INDENT]
 
For the #1 answer,
I typed in the "sudo fdisk -lu", there's a * beside /dev/sda1, what does that means?
Is it because only that drive that shows up on the "Home Folder">Devices?
I'm wondering why the /dev/sda2 partition doesn't shows up on the Devices tab. Is there any way to make it appear?

When i typed in the "sudo parted -l" command, it gave out a message like this:
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.
Ignore/Cancel?

What should i type in?

As for the #2 & #3, i'm not having any problem with the booting. 

But, i'm having an other problem for installing a driver for my GF 8500GT Silent Magic and installing java for Ubuntu. Already downloaded the .tar.gz(Graphic Card driver) and the .run(Java installer). but don't know how to install them.

---

### Post by mcduck on 2012-09-15
> **Strzz said:**
> Oh yeah, i'm sorry.. I don't remember the bar on the left side of the screen in Ubuntu. is it Unity?

#1. It shows. The problem is, when i already got logged in on Ubuntu, there was only 1 Drive, the 85GB partition, the partition where my windows XP was installed. The other partition doesn't shows up. What should i do to make it appeared on the Ubuntu?

There's nothing to do, you are already seeing that partition every time you access your home directory, or any other location in the file system.

---

### Post by Strzz on 2012-09-15
> **mcduck said:**
> There's nothing to do, you are already seeing that partition every time you access your home directory, or any other location in the file system.

I only see 1 partition, The 85GB ones that i installed Windows before. But the 160GB partition where i installed ubuntu doesn't appeared. I was wondering how to make the 160GB partition shows up on the Unity bar or on the "Home Folder" Device tab.

---

### Post by Bashing-om on 2012-09-15
Oh me....

fdisk => "*" indicates what partition you are booting from.
parted => are you invoking the command from the live cd ?
unity/home folder=> gives access to file systems and files  -- not devices.
devices => from live cd use Gparted to look at the partitions (devices) on your system ..be careful what you do in Gparted ...one slip of the thoughts and your system is gone!
cli commands are more specific (must know what you are seeking).

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by lwalper on 2012-09-15
Same question. I installed 12.04 beside a WinXP installation thinking there would be a dual boot option. Didn't see that option anywhere on the installation and on restart the WinXP OS laods as normal. I don't see the Ubuntu installation anywhere??

So, I restarted with the installation USB stick in place - boot from the stick and tells me "there is already Ubuntu installed - what do you want to do? Reinstall or (... and some other options). I elected to reinstall. Restart again comes to a normal WinXP OS without a second boot option and no Ubuntu installation files visible in my file manager. Where do the files go?

---

### Post by lwalper on 2012-09-15
It appears that Ubuntu creates and installs into its own partition which is formatted in ext4 (and which Windoz can't read). I have WinXP installed on drive hd0 and Ubuntu installed itself on the second HDD (hd1). I have adjusted the BIOS to boot to hd1 which opens the grub and gives me the option to boot into XP or Ubuntu. I am now (at this very moment) working in Ubuntu.

---

### Post by Bashing-om on 2012-09-15
@ lwalper;
  You do good !  As you now know ..grub has default install position/ That position is modifiable at installation...a lot depends on what drive your bios is set to boot to !

enjoy ubuntu !
[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Strzz on 2012-09-15
> **Bashing-om said:**
> Oh me....

fdisk => "*" indicates what partition you are booting from.
parted => are you invoking the command from the live cd ?
unity/home folder=> gives access to file systems and files  -- not devices.
devices => from live cd use Gparted to look at the partitions (devices) on your system ..be careful what you do in Gparted ...one slip of the thoughts and your system is gone!
cli commands are more specific (must know what you are seeking).
[INDENT]hth <==BDQ
[/INDENT]
What exactly i must do on gparted? I've experimented using Gparted on My laptop's HDD and it went well(for the puppy linux). LOL

---

### Post by critin on 2012-09-15
Strzz,   Is the XP cracked also?  

> It didn't have a recovery partition. And i don't have the installation disc. I'll find another way then.

But it made me wondering, the first time that error occured is on my  laptop which has **[COLOR=Blue]a cracked Wind 7 Ultimate.[/COLOR]** Then after my laptop was  disabled(unable to run Puppy linux and Wind7, i connected the HDD to  this PC. After a while, the windows Xp freezes, when i restarted the  system, it gave a BSOD like error message.

So you're using the same hdd that froze with Win7?  Don't you think that could be your problem?  Microsoft won't allow it to run if you mean 'cracked' the way I mean it.

Install a fresh copy of ubuntu right over windows--you'll love it.  (except for the lack of windows games)

---

### Post by Strzz on 2012-09-15
> **critin said:**
> Strzz,   Is the XP cracked also?  

.

So you're using the same hdd that froze with Win7?  Don't you think that could be your problem?  Microsoft won't allow it to run if you mean 'cracked' the way I mean it.

Install a fresh copy of ubuntu right over windows--you'll love it.  (except for the lack of windows games)

The XP is not cracked, because i got the PC from my "wealthiest" relative. Hahaha~

No, the HDD that froze with win7 is the one from my laptop, The 500GB HDD.
For countering the lack of windows games, i already have a collection of offline flash games which i got from ahkong.net. XD Now, i just have to find a stand alone player for flash games..>.<

---

### Post by critin on 2012-09-15
> **Strzz said:**
> I only see 1 partition, The 85GB ones that i  installed Windows before. But the 160GB partition where i installed  ubuntu doesn't appeared. I was wondering how to make the 160GB partition  shows up on the Unity bar or on the "Home Folder" Device tab.

When you boot into ubuntu (the 155--160GB partition), you will see the 85gb win partition in the side bar.  You won't see ubuntu's partition there because you are using it.  When you boot into win (the 85 gb partition), you won't see it there, but you will see the 155-160 gb ubuntu.

> 
The problem is, i can't open/show the 2nd hard drive partition where i  installed the ubuntu. Only the 1st partition which i installed Windows  XP Professional Shows up at the taskbar. Does anyone know how to show  the 2nd partition?

You're already on it.  The files are listed under their titles, docs, pics, downloads, etc.  The desktop you see IS the second, ubuntu partition.

This is what you have...
> 
1 st partition 85GB with Windows Xp Professional installed there.
2 nd partition 155GB with the ubuntu,

---

### Post by critin on 2012-09-15
> **Strzz said:**
> The XP is not cracked, because i got the PC from my "wealthiest" relative. Hahaha~

No, the HDD that froze with win7 is the one from my laptop, The 500GB HDD.
For countering the lack of windows games, i already have a collection of offline flash games which i got from ahkong.net. XD Now, i just have to find a stand alone player for flash games..>.<

Good!!  lol
But you did plug in the 500 gb hd with the corrupted system?  Try taking it out and see if that helps this smaller drive.  Can you see it from the file system sidebar?  Did you leave corrupted win7 on it?

You're bringing in too many separate issues and the thread is getting confusing.  Why not open separate threads for each problem so the answers can be clearer and on point?

---

### Post by Strzz on 2012-09-15
> **critin said:**
> When you boot into ubuntu (the 155--160GB partition), you will see the 85gb win partition in the side bar.  You won't see ubuntu's partition there because you are using it.  When you boot into win (the 85 gb partition), you won't see it there, but you will see the 155-160 gb ubuntu.



You're already on it.  The files are listed under their titles, docs, pics, downloads, etc.  The desktop you see IS the second, ubuntu partition.

This is what you have...
I see.. Thanks a lot, mate. This really explains a lot. I've read somewhere, it says i could install ubuntu on a Flash drive and if there is any unused memory, it could be used for storing data, so i thought that this rule works as well on HDDs.

Ok. I'll make a separate thread for other problems that i'm going to ask later.
Thx for the reminder.

---

### Post by Strzz on 2012-09-15
> **critin said:**
> When you boot into ubuntu (the 155--160GB partition), you will see the 85gb win partition in the side bar.  You won't see ubuntu's partition there because you are using it.  When you boot into win (the 85 gb partition), you won't see it there, but you will see the 155-160 gb ubuntu.



You're already on it.  The files are listed under their titles, docs, pics, downloads, etc.  The desktop you see IS the second, ubuntu partition.

This is what you have...
  Is there a way to make the sda2 appear? Do i have to resize it using Gparted? If i resized the partition, would it ruin the Ubuntu installed in it? How many GB do i have to give to the Ubuntu partition? Considering, i would have some software for multimedia and audio-visual processing.

---

### Post by critin on 2012-09-15
> **Strzz said:**
> I see.. Thanks a lot, mate. This really explains a lot. I've read somewhere, it says i could install ubuntu on a Flash drive and if there is any unused memory, it could be used for storing data, so i thought that this rule works as well on HDDs.

Ok. I'll make a separate thread for other problems that i'm going to ask later.
Thx for the reminder.

Sure, you can use the 500 gb for storage.  Did you delete windows?  Delete it and use the whole disk--great idea!

---

### Post by critin on 2012-09-15
> **Strzz said:**
> Is there a way to make the sda2 appear? Do i have to resize it using Gparted? If i resized the partition, would it ruin the Ubuntu installed in it? How many GB do i have to give to the Ubuntu partition? Considering, i would have some software for multimedia and audio-visual processing.

I thought we just settled that?  
First partition is sda/1,   winXP  
second partition is sda/2 or 3--  Ubuntu  (or whatever it says in gparted or disk utility)  You'll have a swap partition, it's tiny. ignore it and don't change it.

first hdd disk is sda,  XP and ubuntu
Ssecond hdd is sdb.  500 storage  (with corrupted win7, hd not being used)


 1 st partition 85GB with Windows Xp Professional installed there.
2 nd partition 155GB with the ubuntu,                      

Gparted resize?  for what, the 500gb hd?  If so, please start a new thread.

---

### Post by Strzz on 2012-09-15
> **critin said:**
> I thought we just settled that?  
First partition is sda/1,   winXP  
second partition is sda/2  Ubuntu

first hdd disk is sda,  XP and ubuntu
Ssecond hdd is sdb.  500 storage


                              1 st partition 85GB with Windows Xp Professional installed there.
2 nd partition 155GB with the ubuntu,                      

Gparted resize?  for what, the 500gb hd?  If so, please start a new thread.

Using Gparted for resizing the sda2? Because the unused space is around 100GB, it would be a waste not to use it to store files, right? Lets put aside the 500Gb first. I won't be using it, since it has an errored Win7 and puppy linux.

---

### Post by critin on 2012-09-15
> **Strzz said:**
> Using Gparted for resizing the sda2? Because the unused space is around 100GB, it would be a waste not to use it to store files, right? Lets put aside the 500Gb first. I won't be using it, since it has an errored Win7 and puppy linux.

With a windows partition involved I'm not going to try to help resize.  I can do my own, but I can't break someone else's install.  There is always the danger of messing up windows boot, so start a new thread--all right?  

Why not practice partitioning on the 500 gb since there's nothing on it?  You've a good opportunity to teach yourself a very important part of using linux.

---

### Post by mcduck on 2012-09-16
> **Strzz said:**
> Using Gparted for resizing the sda2? Because the unused space is around 100GB, it would be a waste not to use it to store files, right? Lets put aside the 500Gb first. I won't be using it, since it has an errored Win7 and puppy linux.

All the files you store in your home and all the programs you install are already going to that partition, you really don't have to do anyting at all, you are already using the partition all the time. :D

Edit: Perhaps you are just confused about the way how Linux (and really any other operating system than Windows) doesn't list all available partitions and assign them drive letters (such as C:, D: and so on)? When you open a file manager and click the "File System" entry in the side panel, you are accessing the root directory of the partition where Ubuntu is installed to. So that's more or less the same as if you'd go to "C:" drive on a Windows system.

---

### Post by critin on 2012-09-16
> **Strzz said:**
> Using Gparted for resizing the sda2? Because the unused space is around 100GB, it would be a waste not to use it to store files, right? Lets put aside the 500Gb first. I won't be using it, since it has an errored Win7 and puppy linux.

You don't really have 'extra' 100 gb space.  It IS being used.  The hdd is 250gb total.  Windows takes 85gb of that, ubuntu takes the rest- 165.  You will fill that up by adding pics, music, videos, downloading stuff, writing, etc.  You've given ubuntu plenty of room to grow and that's good.  

You don't need to partition just to add storage space, it's already there--100+ gbs worth.

If you want to partition so you can add a third os system, you can, but I suggest you learn as much as you can about partitioning first.  Besides, you have a 500 gb hd that's not being used--use that.  You've spent a lot of time getting this install setup, take time to enjoy and learn it.

---

