---
title: "Making a workable copy of Ubuntu boot drive to a raid array"
date: 2022-01-12
forum: New to Ubuntu
---

### Post by couzin2000 on 2022-01-12
I have this home server box (an old Compaq i5) running 18.04.6 LTS. I have it setup just right, I don't want to lose anything or have to restart from scratch. I'd just like to shut down the server, hook the drive up to some other machine, then make a copy onto another drive.

So my target machine would be using 2x 128Gb SSDs. I'll configure them into a RAID 1 array, so if one goes down, I can copy the remaining one and start back up.

So how to go about this? I'm guessing I'll have to use a USB key to boot into some OS (like Ubuntu) and decide what to copy... but to make it bootable? Not sure how to go about this with modern software. 

ALSO: Once my system is copied over to my RAID drives, if I boot into that array, will the OS detect the changes in hardware automatically? Or will I have to do some leg work? (there's not much in there, cpu, mobo, drives, and that's it - I access this PC from Teamviewer, usually).

Anyone have a *reliable *and *easy *step-by-step?

Thanks!

---

### Post by TheFu on 2022-01-12
I would use LVM.  Do a normal install with LVM to 1 disk, then modify the LVs to be a mirror/RAID1 - I think lvconvert is the command, but there will be other LVM commands necessary to get to that point on the 2nd drive's partitions.

Using LVM requires reading and *understanding*.  Step-by-step is asking for failure because of 1 tiny thing that is different on your system from what the author wrote.

I've moved disk arrays to new hardware 3 times.  Don't recall having issues, but that's my hardware, not yours.  YMMV.

x2go doesn't rely on a 3rd party to allow connections or provide authentication.  With x2go, you have control over the auth-keys and it feels 2-3x faster than any rdp/vnc method.  When people switch, they say, "it is like night and day. Can't believe I waited so long." Only the ssh port (use a non-standard port on the WAN router) needs to be open and secured. That is a well-known thing. Easy to accomplish.

If the system doesn't have any GPU, then you'll need to setup every Ubuntu install to work without GPU support, even for just a text console. That is not the default. A GPU isn't required post-install.

---

### Post by couzin2000 on 2022-01-13
Sounds very complex to me. And although I totally get the "read and understand", I am SO not familiar with any of the terms you used. Had to Google "LVM" to figure it out. 

That said, I AM able to run a full install, then reconfigure. Considering the machine is primarily used as storage, hosting a Minecraft server for my son and hosting a Plex server  (which is the most important thing, which got completely annihilated by an unrequest updgrade, thanks Plex), then I am pretty sure restarting from scratch is the way I'll go. 
Thanks for taking the time and putting things in perspective for me!

---

### Post by TheFu on 2022-01-14
I suspect you don't know what RAID1 really is.  If a disk fails, then the other one should keep working WITHOUT ANY CHANGES by any operator.  It is a complex thing, especially the boot parts.  
Then a replacement drive is acquired to replace the failed disk, you have to tell the RAID array that it is failed, then removed, then install the new drive (sized to be the same or larger), get the partitions to be exactly the same size, and add the new partition to the RAID array.  Last is waiting for the rebuild as data is automatically put onto the new storage ... while still working and available on the old storage.

There are 2 reasons for RAID.
* Added performance
* High Availability (keep running after 1 failure)
We still need backups. RAID never replaces the need for backups.  In fact, sometimes RAID arrays get confused and the only answer is to wipe and create a fresh array from backups.  

RAID is a pain.  There is pain at creation time and there is pain when something bad happens, but their won't be unscheduled outages.  After a failure, you'll want to schedule an outage to correct whatever the issue was.

There are 3 types of RAID
* Fake-RAID (motherboard stuff)
* Hardware RAID ($400 LSI cards, be certain you always buy a spare, identical, card or you may never get access to your data if the HBA fails)
* Software RAID (LVM, mdadm, ZFS, btrfs)

Of those three, home users should avoid the first 2.  

Fake RAID has all the liabilities of HW-RAID (tied to specific hardware) and none of the performance.

Hardware RAID worth having is that which has a tiny battery to ensure those last bits of data are flushed to the storage if there is a power issue. HW-RAID used to be faster than all the other forms, but that changed about 15 yrs ago.  So, the key reason to use HW-RAID has been removed, yet the dependency on having a spare card available is still there.  Enterprises have spare cards in their data centers under contract to be swapped in by the vendor. Home users cannot do that for cost reasons.

That leaves SW-RAID.  mdadm and LVM share much of the same code for RAID aspects, but I don't know of any easy way to install Ubuntu with mdadm.  To install with LVM is just a checkbox.  ZFS isn't quite ready to be used for the OS and booting under Ubuntu and BTRFS isn't safe specifically for uses that cross multiple disks. There's a long Ars Technica article about btrfs which explains why.  So that leaves us with LVM being the easiest to install that can support RAID.

Hopefully, that explains my answer and process of elimination.  

There are hundreds of LVM tutorials on the internet. The bad news is that there aren't any GUIs to setup or manage LVM.  The good news is that LVM is the same on all Linux distros.  LVM on SuSE, Ubuntu, RHEL, Debian are all the same using the same commands with the same options.  The best way to learn LVM is to setup a virtual machine with some tiny virtual disks and try things out.  Take notes, since there are clear hierarchical things required for LVM setups.  PVs, VGs, LVs are the core objects.  For most needs, an LV is the same as a partition, but much more flexible.  Increasing the size of an LV is trivial, provided the VG has unallocated space available. Reducing the size of an LV is a hassle. This means that initial sizing of LVs should be small. PVs come from disk partitions. I always use a 1-for-1 connection.  VGs are made up of 1 or more PVs.  By default, Ubuntu will create 1 PV, 1 VG, and 2 LVs during an install.  1 LV will be for swap and the other, root, will be much too large for everything else.  The root LV should be less than 40G in size, since it should only hold the OS and nothing else. So, immediately after boot, we need to resize the 'root' LV smaller from whatever junk the installer made.  At the same time, we probably want to create a few other LVs to hold /home, some data areas and perhaps /var.  Remember that resizing an LV larger is 1 command of about 5 seconds and the system can be running.  Resizing an LV smaller requires taking the system down and booting from alternate media, almost always.  Allocate storage to an LV *as needed*, not before.  When resizing, don't forget the --resize-filesystem option in the same command. That will make it 1 command, not 2 and faster.  Also, this resize option only works with ext4 file systems, so if you decide to use some other file system like XFS, expect many things to need 2 commands, not one.

Get all that setup before going into the LVM-RAID configuration.  At this point, I'd have to go read up on LVM RAID. It isn't something I do often.  But logically, it would involve adding a 2nd disk with a PV to the VG and telling the existing LVs they need to become RAID1/mirror LVs. LVM would recognize which PVs are different and ensure that RAID1 LVs are on separate disks. There are all sorts of parameters with RAID, chunk size is one of the most important for performance. Every storage system works best at a specific chunk size. I don't know of any reliable way to determine the best size except through testing, since your controller, you storage and your access modes all determine the 'best' value.

BTW, don't use USB connected storage for any RAID.  You'll thank me later. USB connections seem to fail and cause problems with RAID much, much, more often. USB is great for backup storage, but not for HA stuff.

---

### Post by couzin2000 on 2022-02-06
> **TheFu said:**
> I suspect you don't know what RAID1 really is.  

Well... I suspect you don't know how truly clear your thoughts are on the subject. Thank you for the RAID class, you're put a lot of things into perspective.
That said, running RAID at this point is done from the controller on my motherboard, and for my usage even this seems pointless, with regards to RAID1. So having run RAID0 for a long time, I just striped the volume and intalled Ubuntu straight on top. At least I gain SOME perfomance and space. 

At this point I'm not too worried about the OS's copy being lost; it is strictly there to run the show, and give access to the additional drives. If I had more command-line knowledge beyond chown, sudo apt install and the likes, I'd probably run it headless. But I'm not familiar enough yet and I keep reading about commands and watching YT videos about those. For now, it's Ubuntu Desktop. 

Now I'm installing a new drive. I wanna check my thought process about this. please read and let me know. 
[LIST]
[*]I physically install new drive in the chassis and connect SATA power and SATA data cable
[*]boot to Ubuntu normally
[*]from GUI run "Disks"
[*]create a FAT32 partition (I'm choosing FAT32 to be able to remove this drive and hook it up to a Windows or Apple system if the server machine fails, as I own both)
[*]create a new mount point using [FONT=Courier New]sudo mkdir /drives/storage1[/FONT] (this is where things get cloudy for me)
[*]run [FONT=Courier New]sudo chown -R couzin2000: /drives/storage1[/FONT]
[*]run [FONT=Courier New]sudo mount /dev/sdb1 /drives/storage1[/FONT]  (I also modify fstab but I omit this here) 
[/LIST]
And after ALL that... the drive remains the property of [FONT=Courier New]root:root[/FONT] and I am unable to access, read, write or execute anything. 
I'm guessing I missed something. Should I have created the partition with some other tool? or using [FONT=Courier New]su[/FONT]-level access?

---

### Post by oldfred on 2022-02-06
FAT32 is only for smaller partitions. It cannot store any file over 4GB.
Games & video files may be larger?

Years ago I was running a compressed backup file to a FAT32 partition. Even though system seemed to have more data, my backup was always 4GB. Back then there were not even warnings that file was truncated. I was lucky I did not need backup. But no more compressed backups, so I can easily access data and only FAT32 for very small partitions like ESP - efi system partition.

---

### Post by TheFu on 2022-02-06
FAT32 shouldn't be used. There are too many reasons to list them all.
I've never used "Disks", sorry.
FAT32 doesn't work with chown. Neither does NTFS nor exFAT.  You need to use, for lack of a better term, native Linux file system if you want chown or chmod to work.  Accessing any ext4 disk is easy from almost any computer.  All you need is a Linux boot/install flash drive.  Any Ubuntu "Try Ubuntu" & installation flash drive works.  You don't need to worry about access to this data, so just use ext4. It will be faster and easier to manage from Linux.  chown/chmod will work.

If you insist on having a physical disk, with partitions (always, always, have partitions) that can be physically connected to both Windows and MacOS, I think you are screwed. Chown will never work.

I've posted in these forums 
a) which file system to pick for which purposes
b) how to mount storage in an fstab [Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843) and [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) 

Some storage terms: [Https://ubuntuforums.org/showthread.php?t=2467190&p=14059532#post14059532](Https://ubuntuforums.org/showthread.php?t=2467190&p=14059532#post14059532)
 
If you don't have a good, specific, reason NOT to use ext4, choose that file system.

---

### Post by couzin2000 on 2022-02-06
> **oldfred said:**
> FAT32 is only for smaller partitions. It cannot store any file over 4GB.
Games & video files may be larger?

Years ago I was running a compressed backup file to a FAT32 partition. Even though system seemed to have more data, my backup was always 4GB. Back then there were not even warnings that file was truncated. I was lucky I did not need backup. But no more compressed backups, so I can easily access data and only FAT32 for very small partitions like ESP - efi system partition.

You're absolutely right and I knew that. I should have known I'd forgotten one small detail.

---

### Post by couzin2000 on 2022-02-06
> **TheFu said:**
> FAT32 shouldn't be used. There are too many reasons to list them all.
I've never used "Disks", sorry.
FAT32 doesn't work with chown. Neither does NTFS nor exFAT.  You need to use, for lack of a better term, native Linux file system if you want chown or chmod to work.  Accessing any ext4 disk is easy from almost any computer.  All you need is a Linux boot/install flash drive.  Any Ubuntu "Try Ubuntu" & installation flash drive works.  You don't need to worry about access to this data, so just use ext4. It will be faster and easier to manage from Linux.  chown/chmod will work.

If you insist on having a physical disk, with partitions (always, always, have partitions) that can be physically connected to both Windows and MacOS, I think you are screwed. Chown will never work.

I've posted in these forums 
a) which file system to pick for which purposes
b) how to mount storage in an fstab [Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843) and [Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) 

Some storage terms: [Https://ubuntuforums.org/showthread.php?t=2467190&p=14059532#post14059532](Https://ubuntuforums.org/showthread.php?t=2467190&p=14059532#post14059532)
 
If you don't have a good, specific, reason NOT to use ext4, choose that file system.

Again - thank you. I knew there was something I was missing. I definitely take a look at your posts. I'll also ask this:
If and when my server goes up in smoke... i would theoretically be able to access the contents of these drives after having lost the user accounts, so long as I gain access via sudo or root... correct? Because in the event this occurs, I'll have to at least be able to read the contents (meaning my permissions will at least be open to 'read' by 'everyone')... if ext4 can be read from a Mac I'll be fine.

---

### Post by TheFu on 2022-02-06
If the drive is not harmed in your pile of smoke, yet, any Linux USB-boot can access it, provided they support the file system you choose.  ext4 is as close to universally supported as I know in the Linux world. In the last 15 yrs, I can't think of any reasonable, linux desktop/server, that cannot mount and access ext4 partitions.  I'm sure some embedded Linux boxes won't, but that isn't your question.  If you have an ARM box (raspberry pi) or odroid or any x86 Linux, then ext4 can be mounted and accessed.

---

### Post by couzin2000 on 2022-02-06
I thank you for your help in making an illuminated choice. I'll be formatting with ext4. At least the data is salvageable, and that's what I need. I realize my skills aren't that sharp in the Linux realm, but now I have a better understanding. I may end up buying into tape backups, as the data I have is starting to get a little bigger than I expected.
Thanks again!

---

### Post by couzin2000 on 2022-02-06
So after all the help I received from TheFu, I was able to do almost everything through command-line.[LIST]
[*]Booted up the server
[*]**CTRL-ALT-T** to open Terminal
[*]ran [FONT=Courier New]sudo fdisk -l[/FONT]
[*]found that I had 2 drives I had previously trioed to attach in FAT format. Both these drives ([FONT=Courier New]/dev/sdb[/FONT] and [FONT=Courier New]/dev/sdd[/FONT]) weren't mounted.
[*]ran [FONT=Courier New]sudo fdisk /dev/sdb[/FONT]
[*]from inside [FONT=Courier New]fdisk[/FONT], deleted the present partition using [FONT=Courier New]d[/FONT]
[*]from within [FONT=Courier New]fdisk [/FONT]ran [FONT=Courier New]g [/FONT](for a GPT partition LABEL)
[*]from within [FONT=Courier New]fdisk[/FONT], ran [FONT=Courier New]n [/FONT]with all defaults (to max out the drive's partition size) -- note: fdisk warned me that the old partition was still there (because I hadn't written any changes to disk yet)
[*]from within [FONT=Courier New]fdisk [/FONT]ran [FONT=Courier New]w [/FONT]to write all changes
[*]ran [FONT=Courier New]sudo fdisk -l[/FONT] and found my [FONT=Courier New]sdb [/FONT]disk had a [FONT=Courier New]sdb1 [/FONT] ext4 partition which ran the size of the drive.
[*]ran [FONT=Courier New]sudo mkfs.ext4 /dev/sdb1[/FONT] to format the drive AS ext4 filesystem
[*]I basically ran the exact same commands for [FONT=Courier New]/dev/sdd[/FONT], which became [FONT=Courier New]/dev/sdd1[/FONT] as ext4 filesystem
[*]To mount the drives, had to create a folder as a mount point, so ran [FONT=Courier New]sudo mkdir /mnt/storage1[/FONT] and [FONT=Courier New]sudo mkdir /mnt/storage2[/FONT]
[*]ran [FONT=Courier New]sudo mount /dev/sdb1 /mnt/storage1[/FONT] [SIZE=1](or better yet run [FONT=Courier New]sudo mount UUID=blablablabla /mnt/storage1[/FONT] and remember to add the same to [FONT=Courier New]fstab[/FONT] later on)[/SIZE]
[*]ran [FONT=Courier New]sudo mount /dev/sdd1 /mnt/storage2[/FONT]
[*]THEN ran into [FONT=Courier New]fstab [/FONT](which I'd never done), so I did [FONT=Courier New]sudo nano /etc/fstab[/FONT] and added [FONT=Courier New]/dev/sdb1 /mnt/storage1 defaults 0 2[/FONT]  and [FONT=Courier New]/dev/sdd1 /mnt/storage2 defaults 0 3[/FONT] to the file (I also deleted any entries that I had written from GUI that stayed there for no reason and that mentioned "Storage 1" or "Storage 2" which was impractical because of the capital and the space...)
[*]And in the end, to be able to share the drives, I ran [FONT=Courier New]sudo chown couzin2000: /mnt/storage1[/FONT] and [FONT=Courier New]sudo chown couzin2000: /mnt/storage2[/FONT], which changed the ownership to ME (FINALLY!)
[*]for final verification ran [FONT=Courier New]sudo mount -a[/FONT]  --- no mistakes were seen. 
[/LIST]

I believe I did this the right way.
Anyone reading this, these were old drives that I connected once the Ubuntu install was completely done. I was reading all the files off the drives so I copied them elsewhere and ran all this to ensure my drives are like new when I reboot the next time.

I'll be looking for more info on sharing through smb,. because somehow my Windows 10 machine can't manage the logon data correctly. I enter the proper username and password, yet they don't work. I do SEE the drives though, which already an impressive feat to me!

EDIT: I finally got around to adding my own user to the smb service in Ubuntu. Ran [FONT=Courier New]sudo smbpasswd -a couzin2000[/FONT] and was immediately able to login from Windows 10. Yay!

---

### Post by TheFu on 2022-02-07
> **couzin2000 said:**
> I thank you for your help in making an illuminated choice. I'll be formatting with ext4. At least the data is salvageable, and that's what I need. I realize my skills aren't that sharp in the Linux realm, but now I have a better understanding. I may end up buying into tape backups, as the data I have is starting to get a little bigger than I expected.
Thanks again!

Tape backup is probably too costly unless you have 100TB+ of data.  Below that size, just get 8+TB disks. I've seen 16TB ones recently and did some cost analysis. The 8TB are still cheaper per TB.  The sorted $/TB in my study a few weeks ago (I looked at this in 2022).  The first 2 were off-brand. 
$16.2500
$16.6667
$17.5000
$18.3333
$18.5625
$19.0000
$19.1667
$20.0000
$21.3333
$24.1667
$24.1667
$24.5556
$25.0000
$25.0000
$25.0000
$25.0000
$25.6667

3+... whatever were
Seagate BarraCuda 8TB
Seagate 12TB HDD Exos X14 
Seagate 16TB HDD Exos X16 
Western Digital DC HC550 18TB 
WD HGST 18TB  NP DC HC550
WD 18TB Elements Desktop HDD

I've been burned by Seagate a few times and remember them lying about design faults for over a year, so they will never, intentionally, get another penny from me. As you can see, they are cheaper in an attempt to regain market, but it has been about 15 yrs since they were caught lying and people like me remember. I wouldn't expect others to hold the same grudge as me. I think the Seagates that are 10TB or larger turned out to be on par quality of other makers. Check the stats from BackBlaze's quarterly reports. Don't trust my memory.

---

### Post by TheFu on 2022-02-07
```
ran sudo mount /dev/sdb1 /mnt/storage1
ran sudo mount /dev/sdd1 /mnt/storage2
```

This is NOT the correct method, long term.  

The order of file system mounts is a timing thing with the kernel and often changes based on what is installed or if USB devices are changed or if a new kernel with different timings gets installed.  Using a UUID or LABEL will ensure you get the same storage mounted to the same location every time.   My links above say to use LABELs, mainly because UUIDs don't convey any real information to humans.  LABELs are set by us so we'll know by looking in the fstab exactly which storage device it is. For example, you might specify in the LABEL the physical slot used for an internal NVMe SSD or which slot in your disk array a drive uses.  UUIDs don't tell us anything.  For example, what is different between these UUIDs?
```
afb02f7f-367c-41b5-92d9-c0ab27a88ed0
 and
554810b2-a02a-4ac7-943e-96550f85ed71
```
I know because I can see the LABEL or I can look at where they are mounted.  But when one of those fails, it is just missing, so it would be helpful to see the other disk's information.  With a LABEL, I can say SLOT1-4TB and SLOT2-2TB for the LABELs. Isn't that much more useful?  Some of my systems have 10 HDDs connected. When 1 fails, my cheap external array doesn't have a red "failed" light next to the non-working disk. It doesn't have any lights related to disks working or failed, actually. There is a dim blue light showing that eSATA is being used. Not really useful.

If you can reboot the system AND it has any level of GPU, then you can use almost any Ubuntu desktop install ISO in "Try Ubuntu" mode and run gparted. That's the best/easiest way that I know to setup partition tables, partitions, format with file systems (if not using volume management), and set a LABEL on each file system. All from a GUI.
Having a bootable flash drive with a current Ubuntu available on it is mandatory.  There are ways to setup multi-boot flash drives so you can have 10 - 40 different ISOs from which to choose, but I've found more than about 5 to be a waste.

---

### Post by couzin2000 on 2022-02-08
> **TheFu said:**
> ```
ran sudo mount /dev/sdb1 /mnt/storage1
ran sudo mount /dev/sdd1 /mnt/storage2
```

This is NOT the correct method, long term.  
 ...
With a LABEL, I can say SLOT1-4TB and SLOT2-2TB for the LABELs. Isn't that much more useful?  Some of my systems have 10 HDDs connected. When 1 fails, my cheap external array doesn't have a red "failed" light next to the non-working disk. It doesn't have any lights related to disks working or failed, actually. There is a dim blue light showing that eSATA is being used. Not really useful.

Good point. But I do have the physical disk labeled the same way; "[FONT=Comic Sans MS]Storage 1[/FONT]" "[FONT=Comic Sans MS]Storage 2[/FONT]". I label them immediately with a sharpie when I get them. So the mount points are associated with the disk no matter where they are. So I am consciencious of this point.

I found the UUIDs of both drives by using [FONT=Courier New]sudo fdisk -l[/FONT]. Copied them to a text file (cause I can't remember that code, man).
Now the correct use of [FONT=Courier New]mount[/FONT] would be... [FONT=Courier New]sudo mount UUID=blablablablabla /mnt/storage1[/FONT] ?

---

### Post by oldfred on 2022-02-08
You can see labels & UUIDs:
[FONT=monospace][COLOR=#000000]lsblk -e7 -o model,name,fstype,size,fsused,label,partlabel,mountpoint,uuid [/COLOR]

You can see all the ways to mount:
ls -F  /dev/disk/by-* 

Shows various examples.
[https://wiki.archlinux.org/title/fstab](https://wiki.archlinux.org/title/fstab)

If I mount by device, I may end up with wrong device.
My system has flash drive as sdf, but if still plugged in on reboot it is sda and then every other drive changes one letter.
UEFI/BIOS determines drive order. And that also can vary if one drive is seen before the other when booting.
[/FONT]

---

### Post by couzin2000 on 2022-02-08
> **oldfred said:**
> You can see labels & UUIDs:
[FONT=monospace][COLOR=#000000]lsblk -e7 -o model,name,fstype,size,fsused,label,partlabel,mountpoint,uuid [/COLOR]

You can see all the ways to mount:
ls -F  /dev/disk/by-* 

Shows various examples.
[https://wiki.archlinux.org/title/fstab](https://wiki.archlinux.org/title/fstab)

If I mount by device, I may end up with wrong device.
My system has flash drive as sdf, but if still plugged in on reboot it is sda and then every other drive changes one letter.
UEFI/BIOS determines drive order. And that also can vary if one drive is seen before the other when booting.
[/FONT]

Awesome. Thanks! I managed to find the UUID by using sudo blkid. Seems to have worked. 
I'm currently adding a third drive, so this is just at the right time.

---

### Post by TheFu on 2022-02-08
> **couzin2000 said:**
> Good point. But I do have the physical disk labeled the same way; "[FONT=Comic Sans MS]Storage 1[/FONT]" "[FONT=Comic Sans MS]Storage 2[/FONT]". I label them immediately with a sharpie when I get them. So the mount points are associated with the disk no matter where they are. So I am consciencious of this point.

I found the UUIDs of both drives by using [FONT=Courier New]sudo fdisk -l[/FONT]. Copied them to a text file (cause I can't remember that code, man).
Now the correct use of [FONT=Courier New]mount[/FONT] would be... [FONT=Courier New]sudo mount UUID=blablablablabla /mnt/storage1[/FONT] ?

You sharpie label means nothing to the OS. At some point, it will be wrong and what you think is mounted to X will not be.  Beware.
The UUID was brought to us by the same minds that brought us XML.
LABELs were brought to us by other humans.

Just sayin'.   Use labels, if you are human. ;)  Let the computers deal with UUIDs in their automation until we can get around to putting labels there instead.

---

