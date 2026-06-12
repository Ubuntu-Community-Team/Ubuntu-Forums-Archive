---
title: "I've messed up my computer trying to install"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by Alecmag on 2012-08-23
I'm freaking out right  now. I was trying to install Ubuntu on my windows 7 laptop, and when I  was working on the install something went wrong and now when I boot up  it doesn't go into Windows.
  I chose "something else" on the install screen and tried to resize a partition but I don't know what happened. 
  It still says that windows 7 is on this machine but it doesn't give  me the option to "install inside windows" anymore. Something is wrong. I  don't know what I'm doing.
  Please let me know if any more information is needed.

---

### Post by Bucky Ball on 2012-08-23
Welcome.

Sounds like you are attempting a Wubi install if you are looking for an option to install inside Windows, yet choosing 'Something Else' is related to a hard drive install, which is not 'inside Windows' but installed to a partition. 

Did you resize the Windows partition when you chose 'Something Else'? If so, this can seriously screw the MBR, but that is fixable (Win7 should be resized with it's own software). You could try with Boot Repair. If you boot from the LiveCD, get online, install Boot Repair from Software Centre (yes, it will install even on a Live boot), and give that a go to start.

Please give more detail: Release number, Wubi/Desktop/Alternate install. ;)

PS: If you're up to it, installing, running and posting the results of this would give us an exact picture of what's going on with your machine:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

PPS: Just while I think of it; if you already had four primary partitions on the drive and tried to add a fifth after resizing Win, that complicates things further. Try and post the boot info. ;)

---

### Post by Alecmag on 2012-08-23
> **Bucky Ball said:**
> Welcome.

Sounds like you are attempting a Wubi install if you are looking for an option to install inside Windows, yet choosing 'Something Else' is related to a hard drive install, which is not 'inside Windows' but installed to a partition. 

Did you resize the Windows partition when you chose 'Something Else'? If so, this can seriously screw the MBR, but that is fixable. You could try with Boot Repair. If you boot from the LiveCD, get online, install Boot Repair from Software Centre (yes, it will install even on a Live boot), and give that a go to start.

Please give more detail: Release number, Wubi/Desktop/Alternate install. ;)

Ok thank you. It's Ubuntu 12.04, and it wasn't Wubi, I was trying to install to a partition. I'm concerned about putting a different live CD on my flash drive, because if I don't have ubuntu on here my computer wouldn't boot.

 I can't find anything called "boot repair" in the software center

It seems I've messed up pretty badly. The "disk utility" tool is showing a TON of "free space".

I don't really know what I'm doing, so this may be a bad idea, but I could install ubuntu so it's more stable and frees up my USB flash drive, then make a get a windows live USB and reinstall? That seems a bit drastic, but honestly it looks like I've somehow gotten rid of the Windows partition. I can try to get a couple of screenshots if that would help?

EDIT: Ok, I'll run the boot info program. Thank you
EDIT2: Here is what the bootinfoscript returned: [http://pastebin.com/5F65HSu2](http://pastebin.com/5F65HSu2)
EDIT3: Here is a screenshot of the disk utility tool: [http://i.imgur.com/OtPAl.png](http://i.imgur.com/OtPAl.png)
EDIT4: Here is a screenshot of the install tool: [http://i.imgur.com/yAcIk.png](http://i.imgur.com/yAcIk.png)

---

### Post by Bucky Ball on 2012-08-23
Yea, not sure what's gone on there but suspect it had something to do with the Win resize using Gparted. I see no Win either. Which partition was it on? It's confusing in there, wiser heads might come up with other solutions, but I would attempt Boot Repair in the first instance. It may be installable from a Live boot from Soft Centre, but is also available as ISO to create bootable media. Win could just be hiding and the outputs are misleading!

Next, seems you do have a recovery partition remaining. Run that, which will return to default factory and reinstall Windows, then resize the Win partition with its own software. Then install Ubuntu to the free space. 

Best: Make a couple of copies of the recovery disks from that partition (there should be instructions how to do this from manufacturer), wipe the drive (this can be done from a Live boot using Gparted, making sure partitions are unmounted by right clicking first), install Win, install Ubuntu. ;)

---

### Post by Alecmag on 2012-08-23
> **Bucky Ball said:**
> Yea, not sure what's gone on there but suspect it had something to do with the Win resize using Gparted. I see no Win either. Which partition was it on? It's confusing in there, wiser heads might come up with other solutions, but I would attempt Boot Repair. It could just be hiding and the outputs are misleading!

Next, seems you do have a recovery partition remaining. Run that, which will return to default factory and reinstall Windows, then resize the Win partition with its own software. Then install Ubuntu to the free space. 

Best: Make a couple of copies of the recovery disks from that partition (there should be instructions how to do this from manufacturer), wipe the lot, install Win, install Ubuntu. ;)

Ok thank you for your help. I honestly have no idea how that happened. Obviously I butchered it somehow though. Again, I really appreciate the help I was panicking so badly I actually forgot about the recovery partition! I'm actually not entirely sure how to run that but I should be able to get that from some googling.

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> Ok thank you for your help. I honestly have no idea how that happened. Obviously I butchered it somehow though. Again, I really appreciate the help I was panicking so badly I actually forgot about the recovery partition! I'm actually not entirely sure how to run that but I should be able to get that from some googling.

I think you can use the Windows CD to be able to boot into the Recovery Console or there might be a key you have to press to give you the option to be able to enter the Recovery Console.

---

### Post by Bucky Ball on 2012-08-23
@Shadius: Yea, it is a key combo at boot pretty sure. That kicks in the recovery partition and away you go ...

---

### Post by Alecmag on 2012-08-23
The key combination (F11) is telling me that I need a recovery disk, which I don't think I have. I can look around, but I'm not sure if I do.

---

### Post by Bucky Ball on 2012-08-23
There should be another that boots the recovery partition. The disk it is looking for is a product of that partition and if you didn't manually make them they probably don't exist (I always make two copies and put them back in the box with receipt before doing anything with a new machine!)

When it asks, you can't point it at the partition, by any chance?

Have you got a manual or can you search for one for your machine online? If you haven't already?

---

### Post by Shadius on 2012-08-23
Before trying the Recovery Console, you might want to try Boot-Repair. The link is in my signature. It seems some form of a system recovery is still left on the hard disk drive. The BootInfoScript is still showing that Windows is installed to *sda* so you can probably try using Boot-Repair to restore the MBR and get back Windows! I'd try that before trying Recovery Console.

---

### Post by Alecmag on 2012-08-23
Ok I'm going to try the Boot-Repair and while that's working I'll try to find a manual online in case it doesn't work.

Thank you both so much for the help.

EDIT: Ran boot-repair, it gave me this URL: [http://paste.ubuntu.com/1163287/](http://paste.ubuntu.com/1163287/)
and I'm about to restart

EDIT2: That doesn't seem to have helped. Just starts a black screen with a blinking underscore _ in the top left.

Can a recovery disk be made without access to windows? And if so can it be put on a flash drive instead of a CD/DVD?

---

### Post by drmrgd on 2012-08-23
> **Shadius said:**
> Before trying the Recovery Console, you might want to try Boot-Repair. The link is in my signature. It seems some form of a system recovery is still left on the hard disk drive. The BootInfoScript is still showing that Windows is installed to *sda* so you can probably try using Boot-Repair to restore the MBR and get back Windows! I'd try that before trying Recovery Console.

I'm a little concerned about the Parted screenshot from above and the parted -l results in the Bootrepair script:

```
Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  1049kB  1016kB  primary
2      1049kB  210MB   209MB   primary  ntfs         boot
3      210MB   103GB   102GB   primary
4      735GB   750GB   15.5GB  primary

```This is definitely Oldfred's turf, but to me it looks like the Windows Boot partition is still there and fine, but the data partition has been erased and is now just sitting as unallocated space.  Let's see how this goes, but I'm worried you're staring down the barrel of a Windows reinstall.

---

### Post by Shadius on 2012-08-23
Here's a guide for [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). What you want to do is restore your MBR to *sda* so look for the option to do that. I believe it's in **Advanced Options**. Uncheck the *Reinstall GRUB* box. You don't want to reinstall GRUB. Check the *Restore MBR* box. If you have another other questions, post back. Screenshots would help us help you better also.

---

### Post by Alecmag on 2012-08-23
> **Shadius said:**
> Here's a guide for [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). What you want to do is restore your MBR to *sda* so look for the option to do that. I believe it's in **Advanced Options**. Uncheck the *Reinstall GRUB* box. You don't want to reinstall GRUB. Check the *Restore MBR* box. If you have another other questions, post back. Screenshots would help us help you better also.

Ok here are screenshots of the 3 available tabs of boot-repair:
[http://i.imgur.com/v0FO2.png](http://i.imgur.com/v0FO2.png)
[http://i.imgur.com/Dpgwp.png](http://i.imgur.com/Dpgwp.png)
[http://i.imgur.com/yQnZf.png](http://i.imgur.com/yQnZf.png)

If all that's right I'll run it again, but at this point I haven't changed anything so it would be the same as the first time I ran it.

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> Ok here are screenshots of the 3 available tabs of boot-repair:
[http://i.imgur.com/v0FO2.png](http://i.imgur.com/v0FO2.png)
[http://i.imgur.com/Dpgwp.png](http://i.imgur.com/Dpgwp.png)
[http://i.imgur.com/yQnZf.png](http://i.imgur.com/yQnZf.png)

If all that's right I'll run it again, but at this point I haven't changed anything so it would be the same as the first time I ran it.

Was Windows on partition 3? You want to restore the MBR to where Windows was installed. I'm assuming it may be *sda* (without any partition number).

---

### Post by Alecmag on 2012-08-23
> **Shadius said:**
> Was Windows on partition 3? You want to restore the MBR to where Windows was installed. I'm assuming it may be *sda* (without any partition number).

Clicking on "Partition booted by the MBR: sda3" gives me the option to change sda3 to "sda 1 (Windows 7(boot))" or "sda4"

Should I change it to sda1?

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> Clicking on "Partition booted by the MBR: sda3" gives me the option to change sda3 to "sda 1 (Windows 7(boot))" or "sda4"

Should I change it to sda1?

Yes, I believe so.

---

### Post by Alecmag on 2012-08-23
Ok here's the new link boot-repair gave me: [http://paste.ubuntu.com/1163335/](http://paste.ubuntu.com/1163335/)

I'm not sure if it's any different than the first. Rebooting now.

EDIT: No luck, this time after the HP splash screen I got an error saying (I can't remember word for word, but it was basically this): "No operating system available. Please insert a boot disk and press any key"

This looks bad.

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> Ok here's the new link boot-repair gave me: [http://paste.ubuntu.com/1163335/](http://paste.ubuntu.com/1163335/)

I'm not sure if it's any different than the first. Rebooting now.

Hopefully, this will give you back the ability to boot into Windows.

---

### Post by Alecmag on 2012-08-23
It didn't work. It says that there's no operating system available, and to insert a disk and press any key. I gave up and booted back into ubuntu. This isn't looking good.

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> It didn't work. It says that there's no operating system available, and to insert a disk and press any key. I gave up and booted back into ubuntu. This isn't looking good.

Indeed, that isn't good. That basically means that there is no OS on the hard disk drive. Seems that you will have to go reinstall Windows, unless someone else knows of another way of fixing this. The only way I can see now is to reinstall Windows. Sorry :(

---

### Post by Alecmag on 2012-08-23
> **Shadius said:**
> Indeed, that isn't good. That basically means that there is no OS on the hard disk drive. Seems that you will have to go reinstall Windows, unless someone else knows of another way of fixing this. The only way I can see now is to reinstall Windows. Sorry :(

Ah. That sucks. So how do I do that? Do I have to buy a new copy of Windows? I've never done this before.

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> Ah. That sucks. So how do I do that? Do I have to buy a new copy of Windows? I've never done this before.

Well, you can buy Windows or you can just install Ubuntu to the hard disk drive.

---

### Post by Alecmag on 2012-08-23
> **Shadius said:**
> Well, you can buy Windows or you can just install Ubuntu to the hard disk drive.

Ok, I'll install Ubuntu so I have an actual OS installed until I can get windows.

Thank you all again very much for your help.

---

### Post by Alecmag on 2012-08-23
One more quick question, I'm installing Ubuntu now ("replace windows 7") and I get this error: [http://i.imgur.com/bxJ7p.png](http://i.imgur.com/bxJ7p.png)

I think this is the same error I got last time I was trying to install. What do I do from here? Just ignore, or is there something I have to do to fix it?

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> One more quick question, I'm installing Ubuntu now ("replace windows 7") and I get this error: [http://i.imgur.com/bxJ7p.png](http://i.imgur.com/bxJ7p.png)

I think this is the same error I got last time I was trying to install. What do I do from here? Just ignore, or is there something I have to do to fix it?

Wait, when trying to install Ubuntu, did it detect that there was an OS on the system already?

---

### Post by Alecmag on 2012-08-23
> **Shadius said:**
> Wait, when trying to install Ubuntu, did it detect that there was an OS on the system already?

This time? Yes it recognizes that Windows 7 is/was installed. [http://i.imgur.com/ZNQ9R.png](http://i.imgur.com/ZNQ9R.png)

What's interesting is that this is what the screen looks like now, but earlier today the very first time I went to install, I believe the the top option said install "inside" windows 7 (If that's not possible, I may be mistaken) and after that but before the last reboot a few minutes ago, I didn't have that option at all, just Replace or "Something else"

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> This time? Yes it recognizes that Windows 7 is/was installed. [http://i.imgur.com/ZNQ9R.png](http://i.imgur.com/ZNQ9R.png)

What's interesting is that this is what the screen looks like now, but earlier today the very first time I went to install, I believe the the top option said install "inside" windows 7 (If that's not possible, I may be mistaken) and after that but before the last reboot a few minutes ago, I didn't have that option at all, just Replace or "Something else"

That would mean that Windows 7 is somewhere on your hard disk drive then! All might not be lost!

---

### Post by Alecmag on 2012-08-23
> **Shadius said:**
> That would mean that Windows 7 is somewhere on your hard disk drive then! All might not be lost!

That is good! Any ideas as to what I should try next?

---

### Post by Shadius on 2012-08-23
> **Alecmag said:**
> That is good! Any ideas as to what I should try next?

Try to post a screenshot of GParted. 

From the Ubuntu LiveCD (selecting **Try Ubuntu**), run the following commands:

```
sudo fdisk -lu
```
then

```
sudo parted -l
```

---

### Post by Alecmag on 2012-08-23
> **Shadius said:**
> Try to post a screenshot of GParted. 

From the Ubuntu LiveCD (selecting **Try Ubuntu**), run the following commands:

```
sudo fdisk -lu
```then

```
sudo parted -l
```

[http://i.imgur.com/hwwro.png](http://i.imgur.com/hwwro.png)

[http://i.imgur.com/6c7i6.png](http://i.imgur.com/6c7i6.png)

Edit: I'm leaving the house for a bit, but I'll be back later tonight. Thank you for your help so far!

---

### Post by Jerry N on 2012-08-23
If you still want Windows 7 on your machine, I would suggest that you NOT start installing Ubuntu at this point.  It appears that your restoration partition is still there.  You need a Windows repair disk (should be down-loadable from somewhere) that will allow you to use that restoration partition to return your computer to its original factory condition.  Then you will be faced with the fact that you already have 4 partitions (HP does that to you!) and you will have to remove one of them before you can consider installing Ubuntu.  You should use the Windows 7 tools to shrink the Windows partition.  I suggest saving the contents of the HP tools partition somewhere.  You can then boot the Ubuntu live disk and use gparted to create an extended partition in the space liberated by shrinking Windows (Do not use the Windows tools to create the extended partition).  Then in the extended partition create a primary partition to hold Ubuntu, a swap partition, and a small partition for the HP tools files that you saved previously.  You can create a primary partition for Home if you desire.  Then you will be ready to install Ubuntu, using the"something else" option.  All this is exactly what I did on my HP Mini 210, although I am using Mint 12 LXDE rather than Ubuntu.

Jerry

---

### Post by Shadius on 2012-08-23
This is where I'm a bit confused. The Ubuntu installer detects another OS, but I don't know how to get it back.

---

### Post by oldfred on 2012-08-23
You have a couple of issues. One is dynamic partitions. When in Windows and you create additional partitions it does not use the standard extended partition and create logicals but converts to dynamic partitions. Something like LVM is in Linux. It allows logical partitions that may then be different than the actual physical partiitons. But it is only Windows, does not work with Linux and does not work with some Windows repair tools.

Windows should have said you were converting from basic to dyamic. And Windows considers it a one way conversion. They say backup, repartition and restore is the only way to go back to basic partitions. The backup part is very important, but some third party tools will convert back and most have not had issues converting.
```

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 [COLOR=Red]SFS[/COLOR]
/dev/sda2               2,048       409,599       407,552  42 SFS
/dev/sda3    *        409,600   200,409,599   200,000,000   b W95 FAT32
/dev/sda4       1,434,785,792 1,465,147,119    30,361,328  42 SFS

```

SFS means it is dynamic and the NTFS partitions are inside the logical partitions which then are not shown.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by westie457 on 2012-08-23
@Alecmag

READ THIS THROUGH COMPLETELY before doing anything.

Having seen your last two screenshots the situation is very bleak.

Do not attempt to install anything to your hard drive. ATM the best chance you have of recovering anything to get Windows back is boot into Ubuntu in try mode, connect to the internet and install 'testdisk'.

Testdisk is an app written to recover deleted partitions and hopefully the files they contain. Full instructions can be found here. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

If testdisk successfully recovers your partitions you are about halfway to a full recovery.

Next while still in the Live Ubuntu start gparted and select the 'recovery' partition, right-click and select 'Manage Flags'. In the pop up window put a check mark in the box marked 'boot'. This will make that partition the only one your computer will start with. Close out of the small window then click 'apply', close gparted and reboot your computer.

You should then be able to reset Windows to how it left the factory. Come back here and recheck this thread on how to install Ubuntu. Others have already posted here on how to do this.

If testdisk is unable to restore the original partition table then Windows has been completely destroyed and the only way to get it back is to either purchase a Windows install DVD or buy recovery DVDs from the manufacturer.

I had to do something similar to this a few days ago on my Acer laptop. This time I was lucky, it worked for me.

Edit ------------------------------------------------------------------------

Oldfred got in before me. Try his solution first if not successful try mine.

---

### Post by oldfred on 2012-08-23
I do have one link where with only 4 partitions, testdisk also has worked. 

But I generally subscribe to Windows tools for Windows and Linux tools for Linux, but sometimes the Windows tools do not work and we do use Linux tools for Windows.

---

### Post by Alecmag on 2012-08-23
Do Windows tools like Partition Master still work even though I'm in Ubuntu right now without access to Windows, or should I use Testdisk?

EDIT: Also, tomorrow I'll have access to another PC with windows, so I'm gonna try to make a recovery disk and see if that helps.

---

### Post by cryptotheslow on 2012-08-24
No you generally can't use Windows tools from within Ubuntu.

Testdisk can find information about previously deleted or altered partitions and rewrite the partition table to effectively recover them (provided they haven't been overwritten).

It is in the Ubuntu repositories - so from your LiveCD you can install it by opening a Terminal and entering:
```
sudo apt-get install testdisk
```

Then follow the step by step instructions at the site westie457 linked too. At least up to the point of running a Quick Search and Deeper Search. Post back what it finds.

That said - I am not sure if Testdisk supports Windows dynamic partitions yet (I haven't tried it) - but no harm in doing the search stages to see what it can find - just don't use any of the options to rewrite the partition table unless you are sure!

---

### Post by YannBuntu on 2012-08-24
Hello

1) Ubuntu install has failed (there is no Linux partition on your system) because of the SFS partitions, and probably messed up things. ( [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/748993](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/748993) )

2) Your Windows is broken (no winload file any more)

If i were you, i would:
- boot on an Ubuntu CD, choose "Try Ubuntu", and backup documents on external disks (or DVDs)
- if some documents are not visible, try to recover them via TestDisk as suggested above
- then format the entire disk (in non-SFS partitioning), then reinstall Windows, then install Ubuntu (not via Wubi)

---

### Post by Alecmag on 2012-08-24
> **YannBuntu said:**
> Hello

1) Ubuntu install has failed (there is no Linux partition on your system) because of the SFS partitions, and probably messed up things. ( [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/748993](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/748993) )

2) Your Windows is broken (no winload file any more)

If i were you, i would:
- boot on an Ubuntu CD, choose "Try Ubuntu", and backup documents on external disks (or DVDs)
- if some documents are not visible, try to recover them via TestDisk as suggested above
- then format the entire disk (in non-SFS partitioning), then reinstall Windows, then install Ubuntu (not via Wubi)

Ok, luckily I had all the files I need already stored on an external hard drive. Should I just not bother with TestDisk then? 

Also, are there any other steps I need before reinstalling windows, or should it be ok? I'm just wondering because it seems like there are some remains of windows left, will the reinstall overwrite everything safely?

---

### Post by YannBuntu on 2012-08-24
you're lucky :)
now all you have to do is:
1) (not sure if needed) convert your disk in standard (non-SFS) via TestDisk or MiniTool Partition Wizard or EASEUS Partition Master (see Oldfred links above)
2) via Gparted, format your disk, and create the partitioning you want, eg: 
  - sda1 for Windows (~30GB, NTFS, put a boot flag on it)
  - sda2 for Ubuntu (~20GB, EXT4)
  - the rest for documents
3) Reinstall Windows (it should install in sda1)
4) Install Ubuntu in sda2

---

### Post by Alecmag on 2012-08-24
> **YannBuntu said:**
> you're lucky :)
now all you have to do is:
1) (not sure if needed) convert your disk in standard (non-SFS) via TestDisk or MiniTool Partition Wizard or EASEUS Partition Master (see Oldfred links above)
2) via Gparted, format your disk, and create the partitioning you want, eg: 
  - sda1 for Windows (~30GB, NTFS, put a boot flag on it)
  - sda2 for Ubuntu (~20GB, EXT4)
  - the rest for documents
3) Reinstall Windows (it should install in sda1)
4) Install Ubuntu in sda2

Ok I think I'm going to wait a while before I install Ubuntu again. I realize that this doesn't normally happen, but my main priority right now is getting WIndows back to normal.

How do I know if I need to convert with TestDisk or MiniTool?

---

### Post by YannBuntu on 2012-08-24
Try to format your disk via Gparted.
If any error, or if the disk remains in SFS, do 1)

---

### Post by Alecmag on 2012-08-24
> **YannBuntu said:**
> Try to format your disk via Gparted.
If any error, or if the disk remains in SFS, do 1)

Ok I'll try that as soon as I get Windows ready to install. I really appreciate the help here.

---

### Post by oldfred on 2012-08-24
The longer you run with SFS the less chance you have of converting back without the full backup, erase drive and restore. Since you only have a few partitions, it would be best to use the Windows tools and convert it back now. It should recover it entirely with  EASEUS Partition Master which I believe you download as a bootable repair disk. 

If you have good backups I would do conversion back now, even if not installing Ubuntu now as even some Windows repair tools do not seem to  work fully with dynamic partitions.

---

### Post by Alecmag on 2012-08-24
[http://www.partition-tool.com/landing/home-download.htm](http://www.partition-tool.com/landing/home-download.htm)

The free home edition doesn't appear to have a bootable disk.

Do I have to use a conversion tool even to just give up and reinstall windows? I've got an ISO, I just need to make a CD/flash drive for it.

EDIT: So regarding the Gparted formatting, this is what it currently looks like: [http://i.imgur.com/xXpMc.png](http://i.imgur.com/xXpMc.png)

So I want to take the huge 600+gb partition (sda1) make a separate partition of ~30gb and format that to NTSF, and put a boot flag, and the remaining ~600gb is all for storage? Do I have to do anything special with the storage partition?

This is a screenshot I grabbed of Gparted's info on the sda1 partition: [http://i.imgur.com/B5LKI.png](http://i.imgur.com/B5LKI.png)

EDIT2: What program do I use for mounting/burning on Ubuntu?

EDIT3: I installed testdisk, and it's analyzing my HDD. I don't really know what I'm doing, so I may have questions soon about some of the prompts.

---

### Post by Alecmag on 2012-08-24
Alright this is what TestDisk returned: [http://i.imgur.com/J9pAe.png](http://i.imgur.com/J9pAe.png)

EDIT: Wait, wasn't the point of conversion to make the disks all non-SFS? Because GParted and TestDisk are both saying NTFS. I'm not sure if that means anything though, I'm a bit lost.

---

### Post by oldfred on 2012-08-24
The difference is physical partitions vs. logical partitions. 

Either way your Windows is in a NTFS partition, but another layer of logic is added so the physical boundaries do not apply. 

Testdisk is looking at the physical partitions which in Windows is basic partitions not dynamic.  It finds the old separators so you may be able to restore as long as all the data in the new logical partitions does not span more than one physical.

---

### Post by Alecmag on 2012-08-24
> **oldfred said:**
> The difference is physical partitions vs. logical partitions. 

Either way your Windows is in a NTFS partition, but another layer of logic is added so the physical boundaries do not apply. 

Testdisk is looking at the physical partitions which in Windows is basic partitions not dynamic.  It finds the old separators so you may be able to restore as long as all the data in the new logical partitions does not span more than one physical.

And I need to restore them to reinstall Windows? Sorry, I'm quite new at all this. What would happen if I tried to install Windows right now?

How do I go about trying to restore them, and what do I do if I can't?

---

### Post by oldfred on 2012-08-24
Do not know. The Windows official instructions were to back up everything, erase partitions and reinstall. But if you have vendor recover or other partitions you may want to make sure to back those up or write the DVD set that was the image of your drive as purchased.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

---

### Post by Alecmag on 2012-08-24
> **oldfred said:**
> Do not know. The Windows official instructions were to back up everything, erase partitions and reinstall. But if you have vendor recover or other partitions you may want to make sure to back those up or write the DVD set that was the image of your drive as purchased.

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

As far as I can tell, all of the methods in the article are from Windows, which I can't do. I tried to install EaseUs using WINE, but it gave me an error and wouldn't launch. Is there a way I can erase partitions from Ubuntu? I don't have any direct backups, but every important file is backed up on an external HDD. It will be mildly inconvenient to reinstall, but not too bad.

Thank you so much for your help so far. It seems we're almost done here one way or the other.

---

### Post by oldfred on 2012-08-24
Can you open gparted from liveCD? Then you should be able to delete the partitions, but maybe the dynamic will not delete? 

Most just recover one way or another back to basic partitions.

---

### Post by Alecmag on 2012-08-24
> **oldfred said:**
> Can you open gparted from liveCD? Then you should be able to delete the partitions, but maybe the dynamic will not delete? 

Most just recover one way or another back to basic partitions.

[http://i.imgur.com/OE2Q4.png](http://i.imgur.com/OE2Q4.png)

If I right click on either of these it gives me the option to delete. I do this to both, then boot from a Windows disk/flash drive and reinstall?

EDIT: Do you happen to know if it will work to mount the iso on my flash drive and then boot from that? If not, is there enough room on a CD or will I need a DVD? I don't think I have any blank DVDs around so it would be much easier to use a flash drive or a CD.

EDIT2: Nevermind that last part, I've found some guides. I just want to make sure about deleting the partitions before I proceed.

---

### Post by Terl on 2012-08-24
That does not look good.  Windows 7 install has 2 partitions, one around 100MB (the boot piece) and the other for the rest and I only see one NTFS partition in the screenshot of about 67MB used.

I fear you may have damaged your windows install.

---

### Post by Alecmag on 2012-08-24
> **Terl said:**
> That does not look good.  Windows 7 install has 2 partitions, one around 100MB (the boot piece) and the other for the rest and I only see one NTFS partition in the screenshot of about 67MB used.

I fear you may have damaged your windows install.

Yeah at this point I've accepted I'm going to need to reinstall. Just verifying some of the details to be safe since I'm not experienced at this at all.

---

### Post by Terl on 2012-08-24
If you have to reinstall and are going to dual boot, the best is to install Windows 7 first.  When you install you can set the disk partitions at that time to leave some unallocated so you already have the space for Ubuntu.

Once Windows is in then you can install Ubuntu.  I am assuming you want the side-by-side, dual boot and not a WUBI install...

---

### Post by Alecmag on 2012-08-24
> **Terl said:**
> If you have to reinstall and are going to dual boot, the best is to install Windows 7 first.  When you install you can set the disk partitions at that time to leave some unallocated so you already have the space for Ubuntu.

Once Windows is in then you can install Ubuntu.  I am assuming you want the side-by-side, dual boot and not a WUBI install...

For now I'm just going to leave it at Windows, I may dual boot later though. I'm not entirely sure what went wrong during the Ubuntu install that caused this, but I'd rather not repeat it.

---

### Post by Terl on 2012-08-24
I understand completely.  A tip for the future, if you want to try again, use windows to shrink itself and create a partition.  The tools are in control panel.  It is safest to use windows tools to work with windows.  And I always dfrag and clean up the disks before I shrink anything....and make backups of important stuff first (I read about a guy who lost all his wedding photos--not a good way to start that off!)

Another idea is to use VirtualBox in windows and install Ubuntu there if your pc has the specs to do that.  I run CentOS on my windows side and it all works well.  It is quite nice in seamless mode.

---

### Post by Bucky Ball on 2012-08-24
OP has stuff backed up and can do a clean install of Windows without issue.

* Delete all partitions with Gparted;
* Install Windows on the first disk, first partition on a primary partition using the software in the Win installer to create partitions for Windows only, leaving the rest free space;
* Install Ubuntu on the free space (choose 'Something Else' at partitioning and create an extended partition with the free space then create your logical drives inside that if you want control over the partitioning, /, /home, /swap for instance).

You're done. This will tell you everything you need to know:

[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

---

### Post by oldfred on 2012-08-25
The issue that converted partitions to dynamic was using Windows to create more than 4 partitions. It automatically converts to dynamic not the extended with logical partitions.

Use Windows to shrink the NTFS partition with Windows 7 or Vista, but use gparted or Linux tools to create partitions for Linux.

---

