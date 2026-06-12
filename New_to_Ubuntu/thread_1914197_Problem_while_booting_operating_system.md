---
title: "Problem while booting operating system"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by roopeshmicasa on 2012-01-23
Hi, 
I am facing a problem with my OS. Ubuntu is not showing up, while booting I get a black screen with this message 


mount:mounting/dev/disk/by-uuid/27ef6c5d-5e4f-4246-aef3-a38d53f0425eon /root failed: file too large
mount: mounting/dev on/root/dev failed:No such file or directory 
mount: mounting/sys on/root/sys failed:No such file or directory 
mount: mounting/proc on/root/proc failed:No such file or directory 
Target file system doesn't have /sbin/init
No init fount. Try passing init= bootarg 


BusyBox v1.13.3 (ubuntu 1:1.13.3 - 1ubuntu11)
built- in shell (ash)
enter 'help' for a list of built - in commands 

(initranfs)_


I don't know how to get rid of this problem. Someone please help!!, I have lods of physics documents in there and I can't access them. 

Also is there any way I can access my files in ubuntu via windows OS. I have dual boot Windows+Ubuntu. 

Help will be much appreciated. Thanks in advance.

---

### Post by SuaSwe on 2012-01-23
Hello there!

I'm not sure about the booting issue itself (though suspect the "file too large" aspect may be related) but you may well be able to access your files still. I personally have not had any joy with the applications you can in theory use to allow Windows to "see" Linux partitions, however if you can burn a LiveCD you should be able to boot from it, select "Try Ubuntu", enter the desktop environment and from there use the window manager (Places > Home Folder) to view your Ubuntu partition(s), and move files from Ubuntu to Windows. Let us know how this goes and if you need any help/it doesn't work!

---

### Post by nipunshakya on 2012-01-23
Hello.First off all, warm welcome to the forums.
Before you repair your grub, i suggest you to boot into a LiveCD, select the "Tyr Ubuntu" thing, and have a live session going on. After that, you copy all your important data stuffs to dvd/external hdd and then be safe with your data. After you do that, read below:
If you are in a dual boot machine, i suggest you read the following:
[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)
elseif you are simply running ubuntu,i would suggest you read the following:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) or
[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair](http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair)

Hope they help you out. Goodluck

goodluck.

---

### Post by roopeshmicasa on 2012-01-25
> **SuaSwe said:**
> Hello there!

I'm not sure about the booting issue itself (though suspect the "file too large" aspect may be related) but you may well be able to access your files still. I personally have not had any joy with the applications you can in theory use to allow Windows to "see" Linux partitions, however if you can burn a LiveCD you should be able to boot from it, select "Try Ubuntu", enter the desktop environment and from there use the window manager (Places > Home Folder) to view your Ubuntu partition(s), and move files from Ubuntu to Windows. Let us know how this goes and if you need any help/it doesn't work!

Hi [SuaSwe]("http://ubuntuforums.org/member.php?u=789466"),

Unable to mount the drive and can't backup things ....
Any clue...
When running in LiveCD I tried opening drive (Linux partition) containing files but as soon as I tried to open drive it showed me the massage 

" Unable to mount: File too large"

How to get rid of this...I don't want to loose my documents :(.....Help!!!!

---

### Post by roopeshmicasa on 2012-01-25
> **WinuxUser said:**
> Hello.First off all, warm welcome to the forums.
Before you repair your grub, i suggest you to boot into a LiveCD, select the "Tyr Ubuntu" thing, and have a live session going on. After that, you copy all your important data stuffs to dvd/external hdd and then be safe with your data. After you do that, read below:
If you are in a dual boot machine, i suggest you read the following:
[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)
elseif you are simply running ubuntu,i would suggest you read the following:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) or
[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair](http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair)

Hope they help you out. Goodluck

goodluck.


Hi [WinuxUser]("http://ubuntuforums.org/member.php?u=1225351"),

Unable to mount the drive and can't backup things ....
Any clue...
When running in LiveCD I tried opening drive (Linux partition)  containing files but as soon as I tried to open drive it showed me the  massage 

" Unable to mount: File too large"

How to get rid of this...I don't want to loose my documents :(.....Help!!!

When I tried mounting it in terminal to fix boot loader ...I get this massage

" Error: File to large "

Please help and I really need those files exactly in the condition I left in there...Is there any other way to backup files...

---

### Post by nipunshakya on 2012-01-26
> **roopeshmicasa said:**
> ....Is there any other way to backup files...

Read these:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
 the second link tells you how to backup and restore your grub as well.....try those once

Im not sure how your partitions are, nor know if its a dual-boot or a single boot machine, nor do i know any specs of your h/w. So its better if you would provide a snapshot of your current partition schemes and clarify your machine's specs

---

### Post by SuaSwe on 2012-01-27
Hi roopeshmicasa,

I saw your other post about this issue in General Help - you mention that you still require assistance with this issue however you do not appear to have answered to WinuxUser's last message, which may help you resolve the problem. It's not looking great that you're not able to mount your old drives using the LiveCD, but often it's possible to recover partitions even when something has gone badly wrong. Read the articles in WinuxUser's last post for more details!

---

### Post by ajgreeny on 2012-01-27
From the live CD/USB system open a terminal and run ```
sudo e2fsck /dev/sdx#
``` where sdx# is your corrupt ubuntu partition.  That may fix the filesystem problems for you.

I have never heard of or seen that error message you get when trying to mount the partition.  To run e2fsck the partition must be unmounted, but that does not seem as though it will be a problem to you at the moment.

---

### Post by roopeshmicasa on 2012-01-27
> **WinuxUser said:**
> Read these:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
 the second link tells you how to backup and restore your grub as well.....try those once

Im not sure how your partitions are, nor know if its a dual-boot or a single boot machine, nor do i know any specs of your h/w. So its better if you would provide a snapshot of your current partition schemes and clarify your machine's specs

 Sorry but I am not that Techie, so, if you can also guide me how to take snapshot of partition I would be very grateful. Also I have no idea about machine's specs, please help me in this as well. Please consider that I am just a person who is slaved to computers for some of my simple wok and doesn't have any idea about how it works :(  . I am using windows currently, so, please give me step by step guide to tell you about the things you are asking.


I read both of the links given above by you. The second one is about backing up system first and then restoring it again. I think I Never backed up anything, so, restoring is not possible as guided. First link is about the same concept where you first back things (os) in something called .tar and then restore back. It also has something where I can rescue by making image of the corrupt drive. I don't have any free storage drive where I can make image and then workout on the lost (kindof) files. 



I think there is some problem with the linux partition and it is so messed up that I can not even access it.

---

### Post by roopeshmicasa on 2012-01-27
> **ajgreeny said:**
> From the live CD/USB system open a terminal and run ```
sudo e2fsck /dev/sdx#
``` where sdx# is your corrupt ubuntu partition.  That may fix the filesystem problems for you.

I have never heard of or seen that error message you get when trying to mount the partition.  To run e2fsck the partition must be unmounted, but that does not seem as though it will be a problem to you at the moment.


I ran the command suggested by you but still the problem isn't resolved. Still can't mount it and get the same message: Unable to mount: File too large. 

Here is the output of the command 

e2fsck 1.41.11 (14-Mar-2010)
Found invalid V2 journal superblock fields (from V1 journal)
Clearing fields beyond the V1 journal superblock
/dev/sdb1: recovering journal
Backingup journal inode block information 
Adding dirhash hird to filesystem 
/dev/sdb1 contains a file system with errors, check forced
Pass 1: checking inode, blocks and sizes
Pass 2: checking directory structure
Pass 3: checking directory connectivity 
Pass 4: checking reference count
Pass 5: checking group summary information

/dev/sdb1: *****FILE SYSTEM MODIFIED*****
/dev/sdb1: 230063/2883584 files (0.3% non-contiguous), 1994923/11528389 Blocks

---

### Post by roopeshmicasa on 2012-01-27
> **SuaSwe said:**
> Hi roopeshmicasa,

I saw your other post about this issue in General Help - you mention that you still require assistance with this issue however you do not appear to have answered to WinuxUser's last message, which may help you resolve the problem. It's not looking great that you're not able to mount your old drives using the LiveCD, but often it's possible to recover partitions even when something has gone badly wrong. Read the articles in WinuxUser's last post for more details!

Thanks for suggestion and grateful to your advices. Btw, you are good at finding duplicate thread :). 
Sorry but I am feeling panicked and want this problem to evaporate as soon as possible.

---

### Post by nipunshakya on 2012-01-27
> **roopeshmicasa said:**
>  I am using windows currently, 

I think there is some problem with the linux partition and it is so messed up that I can not even access it.

Download a software called ext2explore and see if you can backup your data first(haven't tried mounting a corrupt filesystem, but still give a try)...lets do that stuff first and then think of what shall we do next with your corrupt linux okay....Goodluck.
[http://www.softpedia.com/get/System/File-Management/ext2explore.shtml](http://www.softpedia.com/get/System/File-Management/ext2explore.shtml)

---

### Post by roopeshmicasa on 2012-01-27
> **WinuxUser said:**
> Download a software called ext2explore and see if you can backup your data first(haven't tried mounting a corrupt filesystem, but still give a try)...lets do that stuff first and then think of what shall we do next with your corrupt linux okay....Goodluck.
[http://www.softpedia.com/get/System/File-Management/ext2explore.shtml](http://www.softpedia.com/get/System/File-Management/ext2explore.shtml)

Thanks :) was able to retrieve files. This is exactly what I was looking for, to backup things from linux partition, simple and sweet software :). Again, A big Thanks. 

Now, I can play with my linux partition. Suggest me steps to fix this error.

---

### Post by SuaSwe on 2012-01-27
Have you backed up all the data you need? If so you could just run a completely fresh wipe-and-reinstall on the whole drive (using a LiveCD or LiveUSB - just follow instructions to install Ubuntu); provided you don't have another operating system such as Windows installed on the same machine, in which case a bit more care will need to be taken! What do you wish to achieve? Would a full reinstall tempt?

---

### Post by nipunshakya on 2012-01-27
> **roopeshmicasa said:**
> Thanks :) was able to retrieve files. This is exactly what I was looking for, to backup things from linux partition, simple and sweet software :). Again, A big Thanks. 

Now, I can play with my linux partition. Suggest me steps to fix this error.

Okay now, with all your data backed-up, i would suggest you boot into ubuntu-11-10's liveCD now...
From there, run gparted(type it in bash and it'll come up). This application will show your current system partition scheme. Hit the key labeled 'Print Scrn' on your keyboard. This will print the current screen with your gparted opened. Save the file and post the result here....

I suggested you this so that you can re-install ubuntu in a new partition. So first lets see how you have partitioned so that we can make necessary adjustments first.

Regards,WinuxUser

---

### Post by Miljet on 2012-01-27
Gparted is also pretty good at repairing partitions, especially discrepancies between the partition table and the actual partitions. Just highlight the partition that contains Ubuntu and click on "Check for Errors."

I'm not sure at this point if you have a partition problem or a corrupt file system, but it won't hurt to try it.

---

### Post by roopeshmicasa on 2012-01-31
> **WinuxUser said:**
> Okay now, with all your data backed-up, i would suggest you boot into ubuntu-11-10's liveCD now...
From there, run gparted(type it in bash and it'll come up). This application will show your current system partition scheme. Hit the key labeled 'Print Scrn' on your keyboard. This will print the current screen with your gparted opened. Save the file and post the result here....

I suggested you this so that you can re-install ubuntu in a new partition. So first lets see how you have partitioned so that we can make necessary adjustments first.

Regards,WinuxUser

Hi, 
Here are the screenshots you asked. 

[http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-1.png](http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-1.png)
[http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot.png](http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot.png)



Please I really need to try to  fix this problem before fresh installation. Just want to give a try if this can be fixed without installing new copy of ubuntu.

Here is another link to a user who is facing similar problem 

[http://ubuntuforums.org/showthread.php?t=1699493](http://ubuntuforums.org/showthread.php?t=1699493)

---

### Post by roopeshmicasa on 2012-01-31
> **Miljet said:**
> Gparted is also pretty good at repairing partitions, especially discrepancies between the partition table and the actual partitions. Just highlight the partition that contains Ubuntu and click on "Check for Errors."

I'm not sure at this point if you have a partition problem or a corrupt file system, but it won't hurt to try it.

Here are the screen shots of your advice to repair system drive. Hope you will find something out of it. 

[http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-2.png](http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-2.png)
[http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-3.png](http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-3.png)
[http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-4.png](http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-4.png)
[http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-5.png](http://i1114.photobucket.com/albums/k538/tmicasa/Screenshot-5.png)

---

### Post by nipunshakya on 2012-02-03
if you really intend to fix this error, u try running boot info script and post your results here..till now i didn't know you had 2 hard disks.... your screenshots made me think hard....so its better u run boot info script...

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Regards,WinuxUser

---

### Post by roopeshmicasa on 2012-02-17
> **WinuxUser said:**
> if you really intend to fix this error, u try running boot info script and post your results here..till now i didn't know you had 2 hard disks.... your screenshots made me think hard....so its better u run boot info script...

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Regards,WinuxUser

Hi 
Sorry for replying little late. I was bit busy with some work. Here is the output of boot info script. Have a look at into the attached file and see if something can be done.

---

### Post by oldfred on 2012-02-19
Boot script does not really show anything other than the error on mounting.

Since the e2fsck did something the first time I might try that again.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

