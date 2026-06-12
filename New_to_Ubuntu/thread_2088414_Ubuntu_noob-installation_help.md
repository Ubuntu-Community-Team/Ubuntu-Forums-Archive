---
title: "Ubuntu noob-installation help"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by DoABarrelRoll on 2012-11-26
Hello everybody, I am attempting to install Ubuntu on my HP Pavilion Dv7 notebook.

At first I made the mistake of using wubi.exe to install it from Ubuntu.com. It wasn't until I started Googleing after the fact that I realised that I shouldn't have used it. I set aside 30gb for the install using wubi. After a little while I tried to uninstall it using wubi. This worked for me earlier, but not this time. If you run wubi.exe in windows after installing Ubuntu, it will tell you that another version has been detected and needs to uninstall. So I hit uninstall and didn't continue with the setup, just quit. Well I rebooted my laptop and it asks me still if I want to boot to windows or Ubuntu. Selecting Ubuntu just boots normally into windows. Also it would seem that I lost my 30gb hard drive space. Weird thing is, I still have all of my normal boot partitions. C:/ (windows) D:/ (HP recovery] HP Tools and my CD ROM drive. Nothing else.

So I decided to run a boot disk. Using videos on YouTube I learned how to dual boot via a CD and during the setup wizard on all of those videos the first option on the setup is "Install Ubuntu alongside Windows" however my prompt reads "Install Ubuntu INSIDE windows" 

Selecting that option brings up a screen with some lines of text on it with a few things to the right of the screen that read "[OK]"

After about 20 seconds from the time I press install inside windows it gives me those messages and then pops the CD drive open and does nothing. No error messages or anything like that. 

Any ideas? My overall goal here is to have Windows 7 and Ubuntu 12.04 both installed on my laptop. I don't need to be able to see my windows files inside ubuntu & vice versa, just have them both running.

So is there a way i can wipe the wubi installation & reclaim my 30gb without having to use HP recovery and nuke my whole windows install? Also anyway to remove the option to boot to ubuntu after I boot the laptop seeing as how it doesn't work anyways? I would like to have as much of a clean install as I can at this point.

Thanks in advance for any tips you guys & gals might have for me. I'm currently at work so I can't grab screenshots or anything like that at the moment. If you need some screenshots just let me know and I will post them by 5pm eastern time today. Currently 12pm. Thanks again. :)

Computer Specs:
HP Pavilion dv7 notebook PC. Intel core i5-2410m CPU @ 2.30ghz. 64bit operating system windows 7 home premium. It says I have 8.00gb installed memory (ram)

Overall goal: Install Ubuntu with 100gb hard drive space to build pure Android Open Source Project(AOSP) ROMs.

---

### Post by 2F4U on 2012-11-26
> o is there a way i can wipe the wubi installation & reclaim my 30gb  without having to use HP recovery and nuke my whole windows install? 

Wubi should be removed by the Windows mechanisms:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

> So I decided to run a boot disk. Using videos on YouTube I learned how  to dual boot via a CD and during the setup wizard on all of those videos  the first option on the setup "Install Ubuntu alongside Windows"  however my prompt reads "Install Ubuntu INSIDE windows"

What did you download? The default install medium reads "... alongside Windows" and this means you need at least one additonal partition for Ubuntu. The default install media can be found here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You have to burn it to a DVD or USB stick and boot from it.

---

### Post by DoABarrelRoll on 2012-11-26
Thanks for the quick response! I will check out that link for uninstalling wubi's dirty work. :p

I downloaded 12.04 from the Ubuntu homepage. However I burned it to a CD-R, not a DVD. I don't have blank DVD's. Could that be the issue? Regardless, I will try again from a USB stick.  I will try to get you a picture of the installer, as well. Thanks again.

---

### Post by arpanaut on 2012-11-26
If you already have 4 primary partitions on your HDD then the installer will only offer installation "inside" windows.

Check out the first link in this post: [http://ubuntuforums.org/showpost.php?p=12354382&postcount=5](http://ubuntuforums.org/showpost.php?p=12354382&postcount=5)

EDIT: Follow what Mr. Phelps says below!

---

### Post by Mark Phelps on 2012-11-26
> **DoABarrelRoll said:**
> Hello everybody, I am attempting to install Ubuntu on my HP Pavilion Dv7 notebook.

At first I made the mistake of using wubi.exe to install it from Ubuntu.com. It wasn't until I started Googleing after the fact that I realised that I shouldn't have used it. I set aside 30gb for the install using wubi. After a little while I tried to uninstall it using wubi. This worked for me earlier, but not this time. If you run wubi.exe in windows after installing Ubuntu, it will tell you that another version has been detected and needs to uninstall. So I hit uninstall and didn't continue with the setup, just quit. Well I rebooted my laptop and it asks me still if I want to boot to windows or Ubuntu. Selecting Ubuntu just boots normally into windows. Also it would seem that I lost my 30gb hard drive space. Weird thing is, I still have all of my normal boot partitions. C:/ (windows) D:/ (HP recovery] HP Tools and my CD ROM drive. Nothing else.
Wubi doesn't create a partition; instead, it creates a file INSIDE an existing partition.  So, you wouldn't see any more partitions.

> Any ideas? My overall goal here is to have Windows 7 and Ubuntu 12.04 both installed on my laptop. I don't need to be able to see my windows files inside ubuntu & vice versa, just have them both running. You will NOT have them BOTH running at the same time; instead, you will have to boot into one or the other.

> So is there a way i can wipe the wubi installation & reclaim my 30gb without having to use HP recovery and nuke my whole windows install? Also anyway to remove the option to boot to ubuntu after I boot the laptop seeing as how it doesn't work anyways? I would like to have as much of a clean install as I can at this point.
As mentioned, with a Wubi installation, you remove Ubuntu just like you would remove any Windows application.

Since you apparently want to keep Win7 working, BEFORE you try anything else, read through the material below and print it off to have it handy:

Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Shuudoushi on 2012-11-26
> **Mark Phelps said:**
> Wubi doesn't create a partition; instead, it creates a file INSIDE an existing partition.  So, you wouldn't see any more partitions.

You will NOT have them BOTH running at the same time; instead, you will have to boot into one or the other.


As mentioned, with a Wubi installation, you remove Ubuntu just like you would remove any Windows application.

Since you apparently want to keep Win7 working, BEFORE you try anything else, read through the material below and print it off to have it handy:

Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

If this has worked please make sure to mark this issue as [Solved]. Thank you!

---

### Post by DoABarrelRoll on 2012-11-26
> **Mark Phelps said:**
> Wubi doesn't create a partition; instead, it creates a file INSIDE an existing partition.  So, you wouldn't see any more partitions.

You will NOT have them BOTH running at the same time; instead, you will have to boot into one or the other.


As mentioned, with a Wubi installation, you remove Ubuntu just like you would remove any Windows application.

Since you apparently want to keep Win7 working, BEFORE you try anything else, read through the material below and print it off to have it handy:

Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

Thank you for the very informative reply! Not Solved yet, but getting there...

Since I uninstalled Ubuntu via wubi.exe as explained before, there is no Ubuntu option anywhere in Add or Remove/ Uninstall Programs. I will try to do it manually as explained on the wiki page. Hopefully that will solve the problem of my computer still asking me if I want to boot to Windows or Ubuntu. Like I said, I'm sure the install is gone, but it still asks which OS to boot to and if I select Ubuntu it goes to windows normally.

- After some reading I see that there is only 4 partitions available and the computer already has all 4 in use which explains why I couldn't install "alongside" windows. Thank you.

- I realize that I cannot have both OS running at the same time. I just meant I want to ability to boot into either one I choose. "Capable of running either" is what I should have said. Sorry for the confusion. 

- Copy everything from HP Tools to Windows partition. So would that be as easy as dragging + dropping all of the files in HP Tools to C:/? Could I just make a new folder in C:/ - call in HP Tools and move the files in there?

- After the files from HP Tools have been moved to windows partition, using the disk management tool, remove the partition for it. I assume this is so that I have a free partition for Ubuntu to run on?

- Using the same disk management tool I should shrink the windows partition in order to give room to the new partition for Ubuntu to run on. Okay how likely are problems like "making windows unbootable"? That cannot happen. So assuming it's safe using the built in manager, would I need to create a new partition at this point or will the boot disc do that for me after I try to install it again?

Restoring windows to its present state if any problems arise would be ideal. This is a little confusing to me though. 

- When you say to hook up an external drive, do you mean another hard drive? I don't have one... If any sort of data stick can be used, I have a USB flash drive or an Android phone (bootloader unlocked+rooted) I could hypothetically use as storage. 

Or does that program write the backup to a CD? It's kind of hard to tell from your post because you say to hook up to another drive for it to make the backup, but then continue on to say that you can restore windows from the boot CD you just made. :confused: Maybe I'm just stupid.. ](*,)

- Wouldn't using the Windows Backup Manager to make a recovery CD do pretty much the exact same thing as the steps you listed above?

- Why do I need to delete the recovery partition if I am deleting the other HP Tools partition? I figured deleting HP Tools would leave me with 1 free partition. Wouldn't shrinking Windows give the now free partition enough room? If at all possible I would really like to leave D:/Recovery in place. 

I currently have 588GB free of 683GB and am trying to give my Linux install 100GBs. 

Sorry for being a noob. I usually don't mess with this kind of stuff. Electronics are expensive. However rooting and hacking my Samsung Galaxy Nexus has got me interested in software development, so here I am. Hopefully you understand. :KS

---

### Post by Shuudoushi on 2012-11-26
You may also want to try to uninstall grub (Ubuntu's boot loader). For the life of me i can not remember how to do that though... However! Google is your friend! :D

---

### Post by DoABarrelRoll on 2012-11-26
Nevermind, ignore. Seems I got my old install erased! Thank you!!!

Now I just need to get my partitions sorted out. PC no longer asks what OS to boot to, awesome.

So now can I just copy + paste everything in HP Tools partition to C:/ and delete the HP Tools partition, shrink windows and then install Ubuntu? :D

---

### Post by Shuudoushi on 2012-11-26
Make sure you mark this thread as [SOLVED] (Top of the page in thread options.) Also don't shrink the partion to much!

---

### Post by DoABarrelRoll on 2012-11-26
Thanks, again... I will as soon as I consider it solved... ;)

Still not sure why I need to delete D:/Recovery. ..?

Okay So the PC does not belong to me alone, it's a family laptop. 3+ people use it. The wife doesn't care what I do so long as I don't ruin Windows or delete her files. As long as I have a way to recover everything I should be fine, but I really don't want to delete the recovery partition JUST IN CASE. I will make a system repair CD as well as a system image via Windows 7 > Control Panel > System & Security > Backup and Restore 

So basically now my only question is - can I install Ubuntu 12.04 ALONGSIDE Windows 7 using the following method;

1. Copy all files from ```
(H:)HP_TOOLS
``` to ```
(C:)Local Disk
```
2. Using ONLY the Windows built in disk manager to delete the now empty HP_TOOLS partition
3. Using the same disk manager, shrink the windows volume by 100gb. (because I wish to use 100gb for the Linux install)
4. Boot into the Ubuntu boot disk I created earlier.
5. Select install alongside Windows + select 100gb for install. 
6. ????
7. Profit 

?

Also, to revert back (delete ubuntu) without having to use my recovery partition or backup CD's, could I simply remove the ubuntu partition, make a new one in its place name it HP_TOOLS and replace all of the files from C: drive? Would that put me back to a pre-linux state? Or at least close enough that someone who isn't very tech savvy (even less than myself) couldn't notice? Thanks... no more questions for you after this, I promise. :p 

Thanks so very much again to all of you who helped me out. It means a lot! :D

---

### Post by DuckHook on 2012-11-26
> **DoABarrelRoll said:**
> So now can I just copy + paste everything in HP Tools partition to C:/ and delete the HP Tools partition, shrink windows and then install Ubuntu?

+1 to Mark Phelps' very complete instructions. He answers all of your above questions.

MAKE SURE you back up all important data first. So many of the desperate pleas for help on this forum could have been avoided if the user had just backed up before doing critical procedures like resizing partitions. Backing up your data is always the first step in any unknown situation.

---

### Post by DoABarrelRoll on 2012-11-26
Trust me I always backup before anything major. Learned that from Android lol. I just read that wubi was a good way to try it out before you actually dual boot, but whatever. My mistake. I shouldn't have used it in the first place. All good now, though. We can pretend I never used it at all. B)

I read through Mark's reply. I am still slightly confused. I just need to know why I should delete my Recovery partition (As Mark instructs to do) if I can just delete HP Tools? 

Please correct me if I am mistaken, but...

From my understanding, I need a single free partition to truly dual boot on this laptop. From the OEM, my laptop has 5 partitions. In the same order as in disk manager. 

1. C:
2. H: HP_TOOLS
3. E: (cd-rom drive)
4. D: Recovery
5. System

In order to dual boot I need to set one of those aside for ubuntu, yes? So why am I being instructed to delete Recovery partition? I really, really, ***_REALLY_*** don't want to touch that partition if I absolutely 100% don't have to. 

Simply want to know if I can relocate the files inside H: HP_TOOLS - to C:, then remove H:, shrink Windows partition by 100gb and use that H: partition for Ubuntu...? Marks instructions involve removing the recovery partition which I am openly not trying to do unless there is absolutely no other way.

Again sorry for not getting a grasp on this right away. It's my first time trying to do anything like this on a laptop or computer.

---

### Post by oldfred on 2012-11-26
You do not have to delete recovery, but if you have a good Windows backup as Mark has suggested you do not need the recovery partition. The only time you might want it is to restore computer to like new and sell it. It erases everything and returns it to as purchased including all the cruft and none of the updates. Better to use the backup he suggested. We also have seen a few users accidentally boot into the recovery and damage system.

But you only need one available primary partition to become the extended partition. The you can create as many logical partitions in the extended you want or use the default install which uses the unallocated space left from shrinking Windows to install / (root) & swap. Do not create partitions with Windows.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

