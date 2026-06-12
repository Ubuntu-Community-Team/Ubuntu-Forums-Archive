---
title: "USB connected HDD's recognized some times, not some times in 12.04"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-02-02
I have been testing several older HDD's that been collecting here to determine which work, and which do not. I am using a USB kit consisting of an external power supply with a molex and a cable with a USB male on one end and an EIDE adapter on the other. I am plugging the USB into the back of the computer.

The first thing I notice is that 10 of 12 HDD's are not recognized at all by a Ubuntu 12.04 computer. However all but two of the 10 show data transfer when plugged in (the cable glows red at the adapter when data is being transferred.) AFAIK all the drives but two were working when put into the drawer.

So the first question is, are the 10 drives, which I thought were good, bad or is there an issue, such as formatting, which keeps them from being recognized, and if so what might that/those issue/s be? BTW, I have tried a combination of Master, Slave, and Cable Select and AFAICT, it doesn't matter how the jumper is set.

Secondly, for the two drives that do work, they are not consistently recognized. For example, if I reboot the machine, and plug in one of the "non-working" drives, then try one of the working drives, they are usually not recognized. But if I reboot with them plugged in, they are recognized. Or if I reboot, then plug in the working drive before trying another drive, it is recognized.

Anyone shed any light on this?

---

### Post by bc.haynes on 2014-02-02
Are you using the same USB port for all drives? I read a post (don't remember where) that someone han an external HDD that worked in the USB 2.0 port, but not in a USB 3.0 port. That's about all I have to offer. I'm a noob.

---

### Post by Odyssey1942 on 2014-02-02
same port

---

### Post by J_Me on 2014-02-02
Are your drives being 'ground' properly by isolating any bare metal parts. Also it maybe that your drives do work but are not automatically mounted 'cat /proc/partitions' will list anything plugged in, mounted or not. You can use that in conjunction with 'mount' to get more info.

---

### Post by squakie on 2014-02-02
Try the following each time you put a different drive in the external setup:

-open a terminal (ctrl/alt/F1)
- type:

sudo blkid <press enter>

Is the disk listed?

sudo df -g <press enter>

Is the disk listed?

if not, install gparted:

sudo apt-get install gparted <pess enter>

usse your normal userid and password (the password is not echoed to the screen)

you only need to do this once.

then for each disk:

sudo gparted <pess enter>

On the top bar, on the left, click the first option, then go down to devices - is the disk listed?  If you click on the disk you can see if it is partitioned or not.  If there is a red circle with a white exclamation point in it then it probably means you need to create a partition table.  This can happen, for example, on drives that have been "wiped".  DO NOT MAKE ANY CHANGES UNLESS YOU KNOW WHAT YOU ARE DOING AND BE *SURE* YOU ARE ON THE CORRECT DRIVE - OTHERWISE YOU CAN RENDER YOUR INSTALL USELESS AND HAVE TO REINSTALL.

---

### Post by squakie on 2014-02-02
I should also mention the following:

If you have created a mount statement for this external drive, be careful of using /dev/sd"x".  This can change with USB devices.  Also, you don't want to mount by UUID in this case as each drive will have it's own UUID (mounting a known USB drive by UUID is the recommended way).

---

### Post by Odyssey1942 on 2014-02-02
J_Me and Squakie

Thanks for all the tips and clear step by step explanations

None of the "dead" drives responded to any of those commands.

Also " sudo df -g " returned an error message (no such parameter "g", I think it was. )

Is there any point in trying to boot with them connected to an internal EIDE cable, or would that create boot issues?

Or would you conclude that they are all dead?

---

### Post by Odyssey1942 on 2014-02-02
It occurred to me that I should try the known "good" drives.

Without rebooting the computer, the only command that showed me that something was there was

```
cat /proc/partitions
```

which listed the good drives as sdb.

But neither blkid nor gparted could detect them.

---

### Post by varunendra on 2014-02-02
> **Odyssey1942 said:**
> I have been testing several older HDD's that been collecting here to determine which work, and which do not. I am using a USB kit consisting of an external power supply with a molex and a cable with a USB male on one end and an EIDE adapter on the other. I am plugging the USB into the back of the computer.
Is the USB cable short enough? Extra length of the USB cable is the most common cause for all the symptoms you mentioned.

Is the external Power Supply powerful enough to supply sufficient power to the drives? Low power, especially the 5 volts supply, is the next most common cause for all the symptoms you mentioned.

The best and safest way to check if the drives themselves are functional or not is to directly connect them to the internal IDE ports (if you have them). There is no harm or added complexity in doing so.

> I have tried a combination of Master, Slave, and Cable Select and AFAICT, it doesn't matter how the jumper is set.
It won't matter as long as you are using it via the USB kit. It _WILL matter when connecting internally_. It seems you already know how and when to set it to what, usually CS is okay, or for some not-so-smart BIOS, manually setting it to Slave when there is another one connected to the same cable as Master (or vice-versa).

---

### Post by Odyssey1942 on 2014-02-02
I have two of these kits and have used both. No way to know if the power is sufficient because, as I understand it voltage needs to be tested under load to get a true reading. My multimeter will only give an unloaded voltage.

The USB cable is about 26" long. In your opinion is that too long?

I will try a flat cable and try to mount them internally. This will reqiure a shutdown and power off since I will be hooking up an IDE cable. Will work on this tomorrow and let everyone know how I get on.

---

### Post by varunendra on 2014-02-02
> **Odyssey1942 said:**
> The USB cable is about 26" long. In your opinion is that too long?
Nope, it sounds perfect. I used to have one with a detachable USB cable (male on both ends), and the default one was exactly 1 Mtr long and worked okay. Sometimes, when the drives had problem with it, I had 'invented' a new, shorter one (about half mtr long) which was originally an HP printer cable (of a superb quality) cut to less than half of its original length.

> I will try a flat cable and try to mount them internally. This will reqiure a shutdown and power off since I will be hooking up an IDE cable. Will work on this tomorrow and let everyone know how I get on.

I'd be curious to know the outcome. :)

---

### Post by squakie on 2014-02-03
Also - it should be df -h  so....

sudo df -h <press enter>

If nothing shows for this for your drives, then there are other problems.

You could try:

sudo mount -a

then

sudo df -h

I haven't tried this with ext4, etc., drives - I've been usiing external drives on which I have NTFS file systems.  I have a spare 250GB external drive - I'll try that and see if it works if ext4.

---

### Post by squakie on 2014-02-03
Ok, I just took a spare external drive I had (EIDE drive in case with it's own power, connects to PC via USB) and created an ext4 file system on it.  For some reason, df -h doesn't show it, but sudo blkid definitely shows it.  Note that a "new" drive doesn't mean it shows last in the list - mine always show first.  The df -h shows my external NTFS file system I use for XBMC, but not the empty etx4 file systen.  sudo blkid shows both.  

So, try putting one of your drives in, type:

sudo mount -a

sudo blkid

copy and paste the screen results from that back in a reply here.

---

### Post by Odyssey1942 on 2014-02-03
```
robert@intel-i3-550:~$ sudo mount -a
[sudo] password for robert: 
robert@intel-i3-550:~$ sudo blkid
/dev/sda1: UUID="C660AE4F60AE4651" TYPE="ntfs" 
/dev/sda5: UUID="610b6bad-b19e-466e-adce-a58eefdb09c4" TYPE="ext4" 
/dev/sda6: UUID="be977b8a-9a13-4451-85b4-3129e3bb75d6" TYPE="swap" 
/dev/sda7: UUID="1e8f803a-e357-4bc7-a964-c82659423b59" TYPE="ext4" 
/dev/sda8: UUID="31f143b0-c6d8-46ef-af23-ecb14ca42da5" TYPE="ext4"
```

gparted basically shows the same (only sda)

I unplugged the drive, and plugged in a known "good" drive and got this:

```
Error opening /dev/sdb: No such device or address
robert@intel-i3-550:~$ sudo mount -a
robert@intel-i3-550:~$ sudo blkid
/dev/sda1: UUID="C660AE4F60AE4651" TYPE="ntfs" 
/dev/sda5: UUID="610b6bad-b19e-466e-adce-a58eefdb09c4" TYPE="ext4" 
/dev/sda6: UUID="be977b8a-9a13-4451-85b4-3129e3bb75d6" TYPE="swap" 
/dev/sda7: UUID="1e8f803a-e357-4bc7-a964-c82659423b59" TYPE="ext4" 
/dev/sda8: UUID="31f143b0-c6d8-46ef-af23-ecb14ca42da5" TYPE="ext4"
```

So even a known good drive doesn't show up as a "second" event after a reboot.

Now going to restart the computer and see if it recognizes it on reboot. So will post this now as I fear it will not survive the reboot. Will edit with what comes up.

Edit: Exactly the same. However, there was an error message during boot up (still during black screen) referring to an error regarding sdb, so the computer DOES know that the drive is there.

Going to find an IDE cable and try a driect conncection to the mobo.

---

### Post by Odyssey1942 on 2014-02-03
Well, to say that was an instructive exercise would be a masterpiece of British understatement.

With the exception of 1 drive, all of the "unknown" drives showed up with all three commands when plugged directly into the mobo.

That one, and the two that I had noted as probably dead, did show up with the command

```
cat /proc/partitions
``` For whatever value it may have, I noted the description for one of them as 

Major - Minor - # blocks - name
11 -       0 -        1048575 - sr0
8 -         16 -    39082680 - sdb

but did not show up with the blkid or gparted command.

So I learned that the USB "kits" that consist of a USB cable with an IDE connector on one end and a male USB on the other and a separate power supply with a molex for the drive, but no controlling electronics (as in an external enclosure), are unreliable in the extreme,

And now have a question. These three drives that "cat /proc/partitions" alone found, are they dead or what? I don't understand why they show up for this command, but do not for the other two, but I don't know what they are looking for.

And, this could be a good time to "zero" out the drives with ```
dd if=/dev/zero of=/dev/driveidentifierhere (in this case sdb)
``` A second question is once zero'd, do they retain their format, but just with zeros? Is there any reason not to do this?

---

### Post by squakie on 2014-02-03
> =Odyssey1942;12918825]Well, to say that was an instructive exercise would be a masterpiece of British understatement.

With the exception of 1 drive, all of the "unknown" drives showed up with all three commands when plugged directly into the mobo.

That one, and the two that I had noted as probably dead, did show up with the command

```
cat /proc/partitions
``` For whatever value it may have, I noted the description for one of them as 

Major - Minor - # blocks - name
11 -       0 -        1048575 - sr0
8 -         16 -    39082680 - sdb

but did not show up with the blkid or gparted command.

It's possible the drives have been zeroed and have not partitions - what did gparted say?

> So I learned that the USB "kits" that consist of a USB cable with an IDE connector on one end and a male USB on the other and a separate power supply with a molex for the drive, but no controlling electronics (as in an external enclosure), are unreliable in the extreme,

I didn't realize that's what you were using - I assume it's just one of those really small cards in no case.  I personally, and it's just my opinion and experience, have found these to be pretty worthless unless you buy one that is quite expensive, not the cheap ones like you see on Ebay.  The best, as far as I'm concerned - get the external enclosure that is self powered.  It's been a while since I looked, but I *think* you can pick something like that up new around $20 or so, more for a more name-brand one. ;)

> And now have a question. These three drives that "cat /proc/partitions" alone found, are they dead or what? I don't understand why they show up for this command, but do not for the other two, but I don't know what they are looking for.

And, this could be a good time to "zero" out the drives with ```
dd if=/dev/zero of=/dev/driveidentifierhere (in this case sdb)
``` A second question is once zero'd, do they retain their format, but just with zeros? Is there any reason not to do this?

Not sure - maybe the no-partitions thing - if the drive has been zeroed, such as with the dd command, there is no partition table left on the drive.  

So, if you use dd to zero the drive, be aware of a few things:

- add a bs= to the dd command to override the default block size (I think that's 512).  I've used some pretty huge blocksizes on a couple of large drives (bs=16M) and they do run quicker.  I'm not sure if that's a good idea or not, but it seems to work.

- zeroing the drive removes EVERYTHNG - this includes the partition table.  If you use dd like that to zero the drive, you will need to do something to recrate a partition table - even if there are no actual partitions defined after you do so.  One such way to do this iis:

- sudo gparted
- On it's menu bar, "GParted" is the first option.  You want to click on this, go down to devices and select the device you want to work with.  BE SURE TO GET THE CORRECT DRIVE!!!!!!
- device should show with a red circle as well - this indicates there is no partition table
-now on the men u bar, go over to the selection "Device", click on it and select "Create partition table"
- thedefaults should be ok (it creates a MS-DOS type partition table)
- click the green check mark to apply the change and wait for it to complete

Other than that, without being there to physically see the drives and see what is happening it's hard for me to know.  For each of the drives that DOESN'T show when you try to list the partitions, run gparted, select the device and take a snapshot (the entry is in the menus for this), then attach those snapshots back here to a reply telling us what they are.

---

### Post by Odyssey1942 on 2014-02-03
> It's possible the drives have been zeroed and have not partitions - what did gparted say?

Some of the drives had a structure like that shown in the box just above your question. Those two lines were at the end of the list of partitions on sda. I am unsure whether sro and sdb are indicating a partition. Others showed actual partitions.

I ran your instructions at the bottom and everything went well until I clicked on Apply. I did it on two different drives and in neither case did I see a green check mark. Exactly when and where in the process does it appear.

After I clicked on Apply, it returned to exactly the same screen as before I went to Device/Create Partition Table. In other words, it did not seem to affect the drive at all.

Did I miss something? Thanks.  

Will reply separately on the snapshots. May take a bit of time and I wanted to keep this going while you are still around.

---

### Post by squakie on 2014-02-04
Obviously the drive you have in the attachment already has a partition table as it already has an NTFS partition.  In my experience at least, when a drive did not have a partition table there was a red circle with a white or something exclamation mark in it.  If you don't see something like that in gparted, then chances are the drive already has a partition table.  What I was trying to say in the previous post is onlly create the partition table after you have zeroed the drive - check gparted after zeroing a drive and you should see the red circle and then you can (must) create a partition table.  If you already have partitions showing on a drive, then the drive already has a partition table.

The green check mark in gparted that I was talking about is in front of the "Apply" on the menu line - at least on my screen it is a light green.

I'm pretty much out of ideas here, and would like to leave this to someone with far more knowledge than me.  Just trying to help, but I think this is way beyond my knowledge base.

---

### Post by Odyssey1942 on 2014-02-04
Squakie, I guess it was my turn to not read closely. When you asked: > Other than that, without being there to physically see the drives and see what is happening it's hard for me to know. For each of the drives that DOESN'T show when you try to list the partitions, run gparted, select the device and take a snapshot (the entry is in the menus for this), then attach those snapshots back here to a reply telling us what they are. I should have restated that the drives simply do not show up at all in gparted, i.e., the only drive that shows in gparted is the system drive.

Given this state of non-visibility, I guess I assumed that you wanted to see a screenshot of one of the drives which did show up in gparted and so attached that screenshot.

The following for anyone, not just Squakie:

Anyway, I was playing around with the zero'd drives this morning, noticed "Device Information" under "View", clicked on it and saw that opposite "Partition Table" it showed msdos, so it looks like the instructions which I followed did the trick. That it did so instantaneously threw me. Here is a screenshot of gparted showing one of the "zeroed" drives.

[CENTER][ATTACH=CONFIG]250092[/ATTACH][/CENTER]

So I decided to format it EXT4 and here is a screenshot of my choices:

[CENTER][ATTACH=CONFIG]250091[/ATTACH][/CENTER]

Reason for including this is that I was unsure of a couple of choices I made and wanted those choices to be seen as part of this discussion. The uncertain points are:

1) "Free space preceeding" had a default value of "1" MiB. I left that alone not having any idea of what other I might enter. What is the best choice, default or another number and why that other number?

2) "Free space following" had a default value of "0" MiB. I left that alone not having any idea of what other I might enter. What is the best choice, default or another choice and why that other choice?

3) "Align to" had a default value of "MiB". I left that alone not having any idea of what other I might enter. What is the best choice, default or another number and why that other number?

Finally, here is a screenshot of gparted view of the drive following the formatting. 

[CENTER][ATTACH=CONFIG]250090[/ATTACH][/CENTER]

I notice that also the line on the right 2/3's of the screen clearly show the format to be EXT4, the device description on the left shows the "Partition Table" to be "msdos". I conclude that the nature of the Partition Table and the format might be different. Any clarification on this will be appreciated.

---

### Post by varunendra on 2014-02-04
I have seen 4 GB hard disk before (and made fancy mirrors of its platters), but am thrilled to see a working one :)

Anyway, trying to explain what you saw in gparted :

The grey coloured area in the first screenshot 'Represents' the Total Space available on your Hard Disk.

The White area with Blue borders in your 2nd and 3rd screenshots 'Represents' the 'Partition' that you created in that area.

The Yellow area within this White area is the "Used" or "Reserved" space on the partition (Linux by default reserves 5% of the total partition space for 'root' (user account) on EXT partitions).

The big black arrow-heads at the beginning and end of that blue-bordered bar in the 2nd screenshot are 'Handles' provided by Gparted interface which you can 'Grab and drag' to increase or decrease the length of the bar representing the partition (thus increasing or decreasing the size of the partition). Of course it is just an abstract representation of the actual physical area of the partition and nothing real on the drive.

This graph representation of the partition(s) AND the numeric fields below are TWO DIFFERENT WAYS to manipulate the Size and Position of the partitions, existing or the ones about to be created.

The above means, and what you can notice yourself by experimenting, if you Resize or Move the partition using its Bar representation, the Numeric fields below will automatically be updated accordingly. Similarly, if you change values in the Numeric fields instead, the Size/Position of the Bar Representation (of the partition) will get changed accordingly.

This Abstract Representation of the Hard Disk Space and the Partitions is meant to present a Simplified View of the relatively more complex actual (Cylindrical) system of partition layout on the Hard Disk.

Gparted takes care of all the Logical details to arrange partitions the way you want, and the Logic Card + Physical mechanism of the Hard disk take care of its actual physical implementation on the disk.

Now to answer your questions more precisely -
> **Odyssey1942 said:**
> 1) "Free space preceeding" had a default value of "1" MiB. I left that alone not having any idea of what other I might enter. What is the best choice, default or another number and why that other number?
It is the unallocated space Before the start of the partition. Usually it is zero, but sometimes it IS kept 'At least' 1 MB, I guess it depends on Partition Type (Primary vs Extended, as well as Filesystem on it). Unless you have future plans for this unallocated space, it is best to keep it to minimum possible (which is what Gparted offers by default, if it showed 1 MB, you can't make it lesser). There is nothing wrong in making it more than 1 MB though, but without a valid reason, it is just wastage of space.

The 1 MB is probably necessary for maintenance tasks for some particular types of partitions, I'm not sure.

> 2) "Free space following" had a default value of "0" MiB. I left that alone not having any idea of what other I might enter. What is the best choice, default or another choice and why that other choice?
This is "How Much Space" you want to 'Leave' after the partition.

If you are planning to create more than one partition, keep the size of the current one to what you want, and leave the rest of the space for the other partitions (that you'd be creating after this one).

So usually we don't focus on this amount. Instead we focus on the size of the partition we are creating, and in the process of defining the partition's size (or resizing it), this "Free Space" is automatically adjusted.

> 3) "Align to" had a default value of "MiB". I left that alone not having any idea of what other I might enter. What is the best choice, default or another number and why that other number?
I'm not very sure about this, explaining by my 'assumption'.

"Align to" just defines the entity that should be considered a "Boundary" for aligning the partition's start/end points. Your defined values may be slightly adjusted to meet this 'Boundary'.

For example, if you choose "Cylinder", the partition size and position would be adjusted so that it starts on a new Cylinder (not where the last partition ended) and ends on a Cylinder just before the one where the next partition started.

If you choose "MiB", the size of the partition would be rounded to Megabytes. This is something that happens anyway, since the value in dragging-to-resize action also varies in MiBs not in its decimal places (at least that's what appears in Gparted).

If you choose "None", the size and position would be kept exactly how you adjusted (via the Numeric fields or by dragging the graphical bar handles).

> I notice that also the line on the right 2/3's of the screen clearly show the format to be EXT4, the device description on the left shows the "Partition Table" to be "msdos". I conclude that the nature of the Partition Table and the format might be different.
Yes it is different, but is probably not the "Nature" that you understand. It seems you are thinking of the Filesystems (FAT, NTFS, EXT2/3/4 etc.). Those things decide the "File-Keeping system" on the disk (or partition). The "Partition Table" decides the "**Partition-Keeping** system" on the disk (how partitions would be created, kept, accessed, their layout, limitations etc.).

The "msdos" type Partition Table means the traditional, "PC-Compatible" MBR (Master Boot Record) system. Some other Partition Table types are GPT, Humax, Solaris etc. All of them have different Partition layout schemes, limitations etc.

While even a quick description about 'All' the features/limitations of "msdos" or MBR type partition table can take more than a thousand words, its main aspects you should know are -

1) There can be no more that 4 partitions on it. It was due to its small size (512 Bytes) where only a very limited information could be stored.
2) To overcome the above limitation, the concept of 'Primary' and 'Extended' partitions was introduced. For the MBR, an Extended partition is just ONE partition, while for the operating system, it is a container in which there can be many 'Logical' partitions.
3) MBR can not address more than 2TB disk space. In order to address larger disks, more advanced Partition Tables (like GPT) must be used.

If you are interested in details, Wikipedia may be a perfect place to start (and probably finish) : [https://en.wikipedia.org/wiki/Master_boot_record](https://en.wikipedia.org/wiki/Master_boot_record)
Of course feel free to ask if you have specific questions regarding your case or doubts.

**PS:**
Since you are creating fresh partition tables/partitions on the disk and there is no important data to save on it, feel free to experiment with Gparted on it. The worst that may happen is that you'd have to recreate the partition table and partitions on it. :)

---

### Post by SeijiSensei on 2014-02-04
> **Odyssey1942 said:**
> I am unsure whether sro and sdb are indicating a partition.

If you mean /dev/sr0, that's the name of the first optical disk device in your machine. As for /dev/sdb, that refers to the entire second ("b") hard drive.  The first partition on the drive is called /dev/sdb1.  If you run a partitioner like fdisk or gparted, you use a command like "sudo fdisk /dev/sdb" that tells fdisk to use the entire second drive.

I suggest you use dmesg or scan /var/log/syslog when you add the unknown drives and see what Linux reports about their condition.  For IDE drives first try using "sudo dmesg | grep hd". On my rather elderly server this returns output that starts with
```

    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
hda: WDC WD800BB-75FJA1, ATA DISK drive
hdc: Lite-On LTN486S 48x Max, ATAPI CD/DVD-ROM drive
    ide2: MMIO-DMA , BIOS settings: hde:pio, hdf:pio
    ide3: MMIO-DMA , BIOS settings: hdg:pio, hdh:pio
hde: SAMSUNG SP1604N, ATA DISK drive
hdf: SAMSUNG SP1604N, ATA DISK drive
hdg: SAMSUNG SP1604N, ATA DISK drive
hdh: SAMSUNG SP1604N, ATA DISK drive

```
It detects the two motherboard IDE controllers and assigns the primary Western Digital hard drive to /dev/hda and the Lite-On CD-ROM to /dev/hdc.  There is also an outboard IDE card that provides two more IDE controllers to which are attached four Samsung drives.  There is much more to this log, but you'll see right away if Linux can detect the devices at all and, if so, what kinds of errors they may have.  For instance one of my Samsungs has a couple of bad sectors that show up via dmesg like this:
```

hdf: dma_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
hdf: dma_intr: error=0x40 { UncorrectableError }, LBAsect=296070678, high=17, low=10858006, sector=296070656
end_request: I/O error, dev hdf, sector 296070656

```
These occur on just three adjacent sectors so I don't bother to clean them up.  I'd have to bring the machine down, run badblocks, then make sure I can resync the MD array the drive belongs to.  I just let Linux log the errors when they happen and move along.

If you don't get any relevant output with "sudo dmesg | grep hd" try "| grep sd" instead.  My server is running CentOS 5.8 with kernel 2.6.18 and supports the [older "hd/sd" distinction]("http://www.tldp.org/HOWTO/Partition-Mass-Storage-Definitions-Naming-HOWTO/x99.html"). Nowadays everything is an "sd" device, even IDE hard drives.

---

### Post by squakie on 2014-02-05
As I mentioned earlier, whenever I've zeroed a drive I've had to use gparted, Device main menu, Create partition table submenu to put a partition table on it before I could use it.  If you used something along the lines of:

sudo dd bs=4M if=/dev/zero of=/dev/<your_device_here>

It would zero the drive, which wipes out the partition table as well.  If for some reason the instructions you followed did not require you to create a partition table, I'd like to see those instructions myself.

---

### Post by Odyssey1942 on 2014-02-05
Wow! What amazingly informative and helpful replies. Apology for going silent, but allergy attack put me down. As soon as I can concentrate, I will study both of these, make lots of notes for future re-learning, and come back if any questions. Thanks.

---

### Post by squakie on 2014-02-05
Not a problem!!  Everything here is volunteer, so it works in a combination of your speed and how much time people have to reply.  Sorry about the allergy thing - I have a pretty bad case of COPD and here I live in Minnesota where it is oh so warm ;).  The cold air is just completely closing down my lungs.  There is only so much inhalers and a nebulizer can do.  And to think I brought this all on myself for smoking a LOT of cigarettes each day for 40 years!  And you guys all thought I was dumb on the forum!  ;) ;)

At any rate - just get better - we'll be here when you are ready!

---

