---
title: "Very basic questions"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Anonono on 2008-09-13
I'm about to jump in to the wonderful world of Ubuntu (8.04 is downloading now), and I have some basic questions for you.

1: I have two HDD's: One for Windows XP, and one is blank, which I will be using for Ubuntu. It should be fine just to give Ubuntu the majority of it, and install it onto that, right?

2: If Ubuntu is installed on a different drive than Windows, will it still come up with a menu at startup asking which OS to boot? And if I am in one OS, how would I switch to another?

3: To update from 8.04 to 8.10 (When it's released), could I just go into the updates screen in 8.04 and download an upgrade?

Thanks to anyone that answers.

---

### Post by Zzl1xndd on 2008-09-13
Welcome to Linux and Ubuntu

1) that should be fine I had this setup for a while, but Ubuntu should install its boot loader on the Primary drive.

2)Simply restarting and it will give you the menu to select an OS

3)yes you can upgrade to 8.10 that way but you may have to select in your repositories to alert you when then new version is out, As this is a Long Term support release. (8.04 that is)

---

### Post by Anonono on 2008-09-13
But the problem is that the Windows drive doesn't have alot of space left, and the other has heaps. Could there be any problems installing it to the blank drive?

---

### Post by Zzl1xndd on 2008-09-13
The boot loader is a very small file, the GRUB (Linux boot loader) loader will replace you present Boot loader, it will not take up any noticeable hard drive space as the MBR (master boot record) can't be written to normally anyway.

---

### Post by hyper_ch on 2008-09-13
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by Anonono on 2008-09-13
> **tweakedenigma said:**
> The boot loader is a very small file, the GRUB (Linux boot loader) loader will replace you present Boot loader, it will not take up any noticeable hard drive space as the MBR (master boot record) can't be written to normally anyway.
Okay, so how could I install GRUB on the Windows HDD, but have all the Ubuntu files on the blank HDD?

And I'm sorry about the topic title... :oops:

---

### Post by bodhi.zazen on 2008-09-13
go with the default settings ... grub should then be configured automagically.

---

### Post by Anonono on 2008-09-13
As in the default settings in the installer?

---

### Post by kansasnoob on 2008-09-13
I would start here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You'll notice that there are guides for both using the Live CD and the Alternate CD. You'll likely use the Live CD (Graphical install) and there is not an exact tutorial there tailor-made for you, but you need to have a very good understanding of how Ubuntu identifies drives and partitions:

For instance you can forget about Drive C, Drive D, etc. Ubuntu will see drive 1, partition 1 as sda1 or possibly hda1. Drive 2, partition 1 would be sdb1 .......... drive2, partition 2 would be sbd2, etc. The b in sdb = drive #2, the 1 in sdb1 = partition #1. Clear as mud:confused:

I'd start with:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

But it can be misleading because it talks about partitioning that you won't need to do, but it describes using "manual partitioning" which you'll definitely want to use so you can be sure to select the proper drive. And it also gives you a preview of how the Live CD looks!

But I'd also look at this:

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

Because it does deal with multiple hard drives, but you'll likely be using the Live CD to install. The principles are the same but it looks different!

It's definitely worth spending a couple of days studying than being someone that says, "Yikes, I wiped out my Windows and all my stuff"!

Oh, and run the live CD first, choosing: "Try Ubuntu without changes to your computer" before ever starting! I suggest doing so a few times! Get the feel of it, ask more questions!

---

### Post by gregphil on 2008-09-13
I understand your fear, and it can be justified at times.

However the ubuntu Live CD has an option (once you burn the iso and boot to CD) to allow installing ubuntu to a hard disk.  This is a step by step GUI install that asks a bunch of questions (without touching your disk drives) and finally gets to a "Ready to Install" step where you get to say Yes or No one last time.

Some of the early questions are "which partition should I install on?" and it will give you a list of possible choices.  It will offer to re-partition and format the partition chosen, either manually or automatically (a guided install).  I would recommend you let it do a guided install to your entire 2nd (non-Windows) disk.

One final thing the installer defaults to doing is putting the bootloader (GRUB) in the MBR of the active boot disk (which would be your Windows disk).  So the bootloader ends up at the start of your Windows disk and all the rest of ubuntu ends up on the partition you selected earlier.  You CAN choose to override this and either not install a boot loader, or select which disk to put the bootloader on.  At the Step where it says "Ready to Install" STOP and look at the lower right of the screen.  There is an "Advanced" button there which will allow you to change the boot loader options, if you want to.

If your BIOS allows you to select the "boot order" and disk to boot from (a big if) you could choose to install the GRUB bootloader to the 2nd disk.  This would mean your Windows disk remains untouched.  Then you would need to go into the BIOS to select which disk to boot from (1st for Windows or 2nd for GRUB).

If you let GRUB be installed in the MBR of the Windows disk it will (normally) notice the Windows install already there and add a Windows line to the bootloader menu that will appear at boot time.  So you can select ubuntu or Windows to boot to, without changing the BIOS boot order.  This has the slight drawback that if you ever decide to erase the ubuntu disk you won't be able to boot to Windows (because part of the GRUB bootstrap ends up on the 2nd disk) This can be fixed (if you don't panic) by rewriting the Windows disk MBR (use Windows recovery disk and fdisk -MBR).  This restores the Windows bootloader that GRUB overwrote.

So in summary you can probably just follow the ubuntu Live CD install default prompts and the only choice you need to pay close attention to is the partition you choose to install on.

Good luck.

---

### Post by Anonono on 2008-09-14
Okay, so it turns out they aren't two separate HDD's, they're just two partitions of the same disc. 
I'm a bit stuck as to what do to now (I'm at the partition part of the Live CD Installer). If I choose the 'Use entire disc' like you said, it will overwrite the Windows partition. 
If I choose the first option (Guided - Resize SCSI3 (0,0,0), partition #3 (sda) and use freed space), what will that do? It's the one with the interactive table slider, but I don't know what it does.
If I choose 'Manual', it comes up with 'dev/sda' as the main option, with 'dev/sda1', 'dev/sda2', and 'dev/sda3' as sub-options of 'dev/sda'. 1 & 3 are formatted with fat32, and 2 is NTFS.
The actual drive is around 160gb, and the two partitions (That I thought were seperate drives) should be about 80gb each. 'dev/sda1' is 8381MB, and it's used 4000MB. 'dev/sda2' is 77580MB, with 'Unknown' used up. 'dev/sda3' is 78732MB, with 33MB used (This should be the blank one). Should everything be fine if I select 'dev/sda3'? And what would 'dev/sda1' be?
I know this is probably going overboard, but I really want to make sure my System doesn't stuff up.

---

### Post by rraj.be on 2008-09-14
> **Anonono said:**
> 
If I choose the first option (Guided - Resize SCSI3 (0,0,0), partition #3 (sda) and use freed space), what will that do? It's the one with the interactive table slider, but I don't know what it does.

This will allocate space for windows and ubuntu equally on the hard disk.

So you can have both your windows and ubuntu without any problem automaticaly and it is simplest way.

> 
If I choose 'Manual', it comes up with 'dev/sda' as the main option, with 'dev/sda1', 'dev/sda2', and 'dev/sda3' as sub-options of 'dev/sda'. 1 & 3 are formatted with fat32, and 2 is NTFS.

/dev/sda is the hardisk name give to your hard disk.If you have two more hard disks then it will be listed like sdb and sdc etc.. . 

If you are choosing manual then you should select the partition in which you want to install ubuntu.

In this there are 4 things to follow.

1)select the partition you want to install and select EDIT.

2) Select the check box use this partition.

3) Formate the partition to Ext3

4) Set the mount point to /

> 
The actual drive is around 160gb, and the two partitions (That I thought were seperate drives) should be about 80gb each. 'dev/sda1' is 8381MB, and it's used 4000MB. 'dev/sda2' is 77580MB, with 'Unknown' used up. 'dev/sda3' is 78732MB, with 33MB used (This should be the blank one). Should everything be fine if I select 'dev/sda3'? And what would 'dev/sda1' be?


You can choose sda3 as it is the free partition in which you want to install.

Select that partition and select Edit and follow the 4 steps givena bove.

Good luck. :)

---

### Post by Anonono on 2008-09-15
Okay, well, installed it, but during the last few percent, it came up with an error (It was something like this, I can't quite remember it): 'Could not find/boot (Can't remember which) GRUB on 'dev/sda2'. This is a fatal error'.
Before the error, and during the installation menus, when it came up with the 'Advanced' button , I clicked it, and it came up with the 1 -3 dev/sda options to install GRUB to. '1' was Windows NT/98/XP (Something like that), and 2 was XP Home. I chose XP Home, and installed.
After the error, I shut down, removed the disc, and started it up again. I booted into Windows safely, as it seems the default bootloader was not affected.
What should I do now? Reformat the 'Ubuntu' partition to fat32, and go through the process again, but this time installing GRUB on 'dev/sda 1' (Windows NT)or just leave the 'Advanced' setting alone?

---

### Post by rraj.be on 2008-09-15
> **Anonono said:**
> 
Before the error, and during the installation menus, when it came up with the 'Advanced' button , I clicked it, and it came up with the 1 -3 dev/sda options to install GRUB to. '1' was Windows NT/98/XP (Something like that), and 2 was XP Home. I chose XP Home, and installed.
After the error, I shut down, removed the disc, and started it up again. I booted into Windows safely, as it seems the default bootloader was not affected.
What should I do now? Reformat the 'Ubuntu' partition to fat32, and go through the process again, but this time installing GRUB on 'dev/sda 1' (Windows NT)or just leave the 'Advanced' setting alone?

Just start the ubuntu Live cd and start the installation again and leave those advanced options related to GRUB installation to default.

This will install grub in default manner.. :)

---

### Post by Anonono on 2008-09-15
So, should I reformat the Ubuntu partition to fat32 before I do that?
**EDIT:** I tried to do this, but I can only select NTFS when I right click it and select 'Format' in XP. Should it be okay to format it in this?

---

### Post by rraj.be on 2008-09-15
> **Anonono said:**
> So, should I reformat the Ubuntu partition to fat32 before I do that?
**EDIT:** I tried to do this, but I can only select NTFS when I right click it and select 'Format' in XP. Should it be okay to format it in this?

 You cant formate any partition to ext3 in windows.

Just boot into live cd and during selection of partition

select

`1) use this partition

2) formate to ext3 journalling file system.

---

### Post by Anonono on 2008-09-16
Okay, I just let the settings for GRUB go to default, and the exact same thing happened.

Help.

---

### Post by Elfy on 2008-09-16
If the install has failed on installing grub try to do it like this.
Run the livecd and open a terminal -

```
sudo grub
find /boot/grub/stage1
```

This should return a location - use this location in the next command, for example hd2,1

```
root (hdx,y)
setup (hdx)
quit
```

If you get errors please post them.

---

### Post by Anonono on 2008-09-17
> **forestpixie said:**
> ```
sudo grub
find /boot/grub/stage1
```
When I typed in this, I got this: 'Error 15. File not found', or something similar to that. Now what?

---

### Post by Elfy on 2008-09-17
Can you run the livecd and then this command from a terminal

```
sudo fdisk -l
sudo mkdir /mnt/tmp
```
The firsat command will show you your partitions - one of them will be linux - it will be sdxy - in the next command replace xy with the number you get from the fdisk command

```
sudo mount -t ext3 /dev/sdxy /mnt/tmp
```

Now run these commands, if necessary and post the outputs - will tell us what you have in your menu list and boot folder

```
cat /mnt/tmp/boot/grub/menu.lst
```
IF that tells you no file, run these

```
ls /mnt/tmp/boot
ls /mnt/tmp/boot/grub
```

---

### Post by Anonono on 2008-09-17
None of those worked. The first one didn't return any numbers, and everything else came up with 'No such file or directory'.

---

### Post by AlesUbu123 on 2008-09-17
I know it may be irrelevant but are you using any specific computer? Lenovo maybe?

---

### Post by Anonono on 2008-09-17
Acer, actually.

---

### Post by AlesUbu123 on 2008-09-17
I think your problem could be related to acer recovery partition (you know that 8 Gb /dev/sda1 partition?). I have found a thread dealing with this:
[http://ubuntuforums.org/showthread.php?t=632598]("http://ubuntuforums.org/showthread.php?t=632598")

But before following these instructions please wait for the opinions of some other forum members. I am not 100% this is the right thing to do and I wouldn't want to mess up your computer :)

---

### Post by Anonono on 2008-09-17
Yeah, I have that partition. What is it used for?

---

### Post by AlesUbu123 on 2008-09-17
It is reserved for complete recovery of your system. You probably can press some button during the startup and you get the option to completely restore you computer to original state in case anythig goes wrong. 
I think you probably wish to keep that option and post #8 in the thread I posted previously shows how to keep it (and also have Ubuntu installed on your laptop).

---

### Post by Anonono on 2008-09-17
It's a desktop, actually, but that shouldn't matter.
Thanks for that link, and the information about the partition. It might come in handy one day.

---

### Post by waspbr on 2008-09-17
this is how i would have installed it:

[LIST]
[*]Pop the live CD in at start up and load it up

[*]Click on the install icon

[*]Select your regional/language/keyboard settings

[*]Choose a manual install

[*](Delete your previous ubuntu partition it should be labeled ext3)

[*]Make a new partition, size it to be more 2x the ammount of ram you have, then set it as a swap partition (linux-swap) if u haven't already made one at a previous install attempt

[*]Use the remainaing space to make a new partition

[*]Set it to be a journalized ext3 partition

[*]At the mount point option select type /

[*]Review, see that you have one windows partition (probably ntfs), one smaller recovery partition (probably ntfs), one swap partition and one main ubuntu partition (journalized ext3). the ubuntu partition and the swap partition should be both.

[*]If everything checks out, press next,fill in you login information, forget the advanced options and carry on.

[*]Go make yourself some coffee or get yourself a beer while the thing installs. 

[*]Once done, reboot. the system should boot to a grub screen that is going to allow you to chose with OS you want to boot into.

[*]Fasten your seat-belts and enjoy the ride.
[/LIST]

This youtube video illustrates what you should do (despite it being from an earlier version of ubuntu).[http://www.youtube.com/watch?v=oVOsHrYF9XI]("http://www.youtube.com/watch?v=oVOsHrYF9XI")

---

