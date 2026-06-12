---
title: "File sharing - How to?"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by flyfishingphil on 2014-03-16
Did quite a bit of 'net research and did more here but not having much luck in finding what I need, good directions that start with "Turn power on then...."

I have a laptop and currently have a divided HD with Ubuntu 12.04 on one side and Win7 on the other. Recently was convinced by a "tech" that the Surface RT was the best all around tablet to get as it would "plug right into Ubuntu for file sharing, etc". Major misrepresentation, to say the least.

What I would like to do, if possible, is set up file sharing on my home network between the RT 8.1 and the Ubuntu on the laptop.

Anybody know of simple, easy to follow, step-by-step instructions to getting this accomplished?

Tried doing the Samba download from the Ubuntu Software Center but didn't find it listed anywhere after the download. Is there a trick there I need to know about or somewhere else I need to go to get it?

Thanks for any assists.

ffp

---

### Post by bab1 on 2014-03-16
> **flyfishingphil said:**
> Did quite a bit of 'net research and did more here but not having much luck in finding what I need, good directions that start with "Turn power on then...."

I have a laptop and currently have a divided HD with Ubuntu 12.04 on one side and Win7 on the other. Recently was convinced by a "tech" that the Surface RT was the best all around tablet to get as it would "plug right into Ubuntu for file sharing, etc". Major misrepresentation, to say the least.

What I would like to do, if possible, is set up file sharing on my home network between the RT 8.1 and the Ubuntu on the laptop.

Anybody know of simple, easy to follow, step-by-step instructions to getting this accomplished?

Tried doing the Samba download from the Ubuntu Software Center but didn't find it listed anywhere after the download. Is there a trick there I need to know about or somewhere else I need to go to get it?

Thanks for any assists.

ffp

I find [this explanation]("http://www.jonathanmoeller.com/screed/?p=4169") helpful.

---

### Post by flyfishingphil on 2014-03-16
Thanks for the tip, and I may be wrong, but I get the impression this is a one way method. It opens up my laptop so other computers can view the files I have on the laptop but doesn't "seek out" other computers and allow file sharing from there. 

I have a new tablet that I carry with me and want to be able to connect to my home network with the tablet, turn on the Ubuntu laptop and "see" my tablet so I can transfer files from the tablet to the laptop.

Also looking at just forgetting that effort and using my Lexar 32GB thumb unit but I just plugged that in and the Ubuntu doesn't open that either.

What am I doing wrong? Put a simple test file on the tablet, transferred to the Lexar, plugged it into the laptop and all I got was a red light flash on the Lexar and cannot view anything on it.

---

### Post by bab1 on 2014-03-16
> **flyfishingphil said:**
> Thanks for the tip, and I may be wrong, but I get the impression this is a one way method. It opens up my laptop so other computers can view the files I have on the laptop but doesn't "seek out" other computers and allow file sharing from there. 

The default Ubuntu install has the client side software installed.  The part that I recommended is the Samba server side.  With the server installed you should be able to *serve files*.  The default install has the software to find and use the server.
> 
I have a new tablet that I carry with me and want to be able to connect to my home network with the tablet, turn on the Ubuntu laptop and "see" my tablet so I can transfer files from the tablet to the laptop.  
If you want the Ubuntu laptop to see the tablet you will need to install the server component on the tablet also.  This will make the 2  machines both clients and servers.

You will need to set up a VPN to use Samba outside of your LAN.  Samba is not for use across the Internet with a VPN tunnel.> 

Also looking at just forgetting that effort and using my Lexar 32GB thumb unit but I just plugged that in and the Ubuntu doesn't open that either.

What am I doing wrong? Put a simple test file on the tablet, transferred to the Lexar, plugged it into the laptop and all I got was a red light flash on the Lexar and cannot view anything on it.
Look at the File System on the left side of the Nautilus File manager.  At the the bottom should be the Lexar.  With the Lexar plugged in -- post the output of this```
df -h
```

---

### Post by flyfishingphil on 2014-03-17
Apparently I didn't have Nautilus so I installed the Nautilus Actions Configuration Tools from the Ubuntu Software Center. Don't see anything in the Nautilus window so posted the df -h in terminal and here are the results:

flyfishingphil@flyfishingphil-Satellite-L305:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        83G   14G   65G  18% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           580M  1.2M  579M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  288K  1.5G   1% /run/shm
/dev/sda2       138G   82G   57G  60% /media/SQ004816V03

Also, after installing the Nautilus, I now don't see the thumb drive when I go to Places > Computer. What did I do wrong now?

---

### Post by bab1 on 2014-03-17
> **flyfishingphil said:**
> Apparently I didn't have Nautilus so I installed the Nautilus Actions Configuration Tools from the Ubuntu Software Center. Don't see anything in the Nautilus window so posted the df -h in terminal and here are the results:

```
flyfishingphil@flyfishingphil-Satellite-L305:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        83G   14G   65G  18% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           580M  1.2M  579M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  288K  1.5G   1% /run/shm
/dev/sda2       138G   82G   57G  60% /media/SQ004816V03
```

Also, after installing the Nautilus, I now don't see the thumb drive when I go to Places > Computer. What did I do wrong now?

It would have been right below this```
/dev/sda2       138G   82G   57G  60% /media/SQ004816V03

```...I assume you can see that partition in Places > Computer.

Let's look using a different method.  With the Lexar drive plugged in, post the output of this```
sudo parted -l
```...that's a lowercase ell ( l ).

---

### Post by flyfishingphil on 2014-03-17
First, all I see in Places > Computer are: 250 GB HD (doesn't show partition), CD-DVD Drive, Generic-Multi-Card (now showing again) and File system.

SUDO PARTED -L provides this:

Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs            diag
 2      1574MB  149GB   148GB   primary   ntfs            boot
 3      149GB   242GB   92.9GB  extended
 5      149GB   239GB   89.8GB  logical   ext4
 6      239GB   242GB   3081MB  logical   linux-swap(v1)
 4      242GB   250GB   7779MB  primary   ntfs            hidden


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdc: 31.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.4GB  31.4GB  primary  fat32        boot, lba

I see the LEXAR shows on that sudo and notice the Partition Table: msdos.

Now what? And thanks much for the assist.

---

### Post by bab1 on 2014-03-17
> **flyfishingphil said:**
> First, all I see in Places > Computer are: 250 GB HD (doesn't show partition), CD-DVD Drive, Generic-Multi-Card (now showing again) and File system.

SUDO PARTED -L provides this:

Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs            diag
 2      1574MB  149GB   148GB   primary   ntfs            boot
 3      149GB   242GB   92.9GB  extended
 5      149GB   239GB   89.8GB  logical   ext4
 6      239GB   242GB   3081MB  logical   linux-swap(v1)
 4      242GB   250GB   7779MB  primary   ntfs            hidden


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdc: 31.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.4GB  31.4GB  primary  fat32        boot, lba

I see the LEXAR shows on that sudo and notice the Partition Table: msdos.

Now what? And thanks much for the assist.

Everything (all partitions) are part of (mounted to) the file system.  Expand the File System and look for *media*.  Under media you should see at least this:  SQ004816V03.  You should also see the Lexar partition (USB stick).

The Lexar should be auto mounted at either /media/<username>/<UUID> or /media/<UUID>

You can check the UUID's for all the partitions with *blkid*.  Post the output of this```
sudo blkid -c /dev/null -o list
```

---

### Post by flyfishingphil on 2014-03-17
Opened up the File System and found the SQ004816V03 but that's all. Opened up the SQ and lots of listings there but NO Lexar showing anywhere

Here are the results on the sudo

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    TOSHIBA SYSTEM VOLUME (not mounted) 34B05C96B05C6102
/dev/sda2  ntfs    SQ004816V03 /media/SQ004816V03 0CD68C1CD68C0862
/dev/sda4  ntfs    HDDRECOVERY (not mounted) 4832240A3223FC16
/dev/sda5  ext4             /              de431376-da02-426a-9420-2ad5d98c6add
/dev/sda6  swap             <swap>         9d9c1db3-602c-4a3a-9626-7028614d2845
/dev/sdc1  vfat    RECOVERY (not mounted)  D87B-F514

Next step? (Thanks again. People wonder why I prefer Ubuntu.)

---

### Post by bab1 on 2014-03-17
> **flyfishingphil said:**
> Opened up the File System and found the SQ004816V03 but that's all. Opened up the SQ and lots of listings there but NO Lexar showing anywhere

Here are the results on the sudo

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    TOSHIBA SYSTEM VOLUME (not mounted) 34B05C96B05C6102
/dev/sda2  ntfs    SQ004816V03 /media/SQ004816V03 0CD68C1CD68C0862
/dev/sda4  ntfs    HDDRECOVERY (not mounted) 4832240A3223FC16
/dev/sda5  ext4             /              de431376-da02-426a-9420-2ad5d98c6add
/dev/sda6  swap             <swap>         9d9c1db3-602c-4a3a-9626-7028614d2845
/dev/sdc1  vfat    RECOVERY (not mounted)  D87B-F514

Next step? (Thanks again. People wonder why I prefer Ubuntu.)
You can see the Lexar at the bottom of the list.  Did you name it RECOVERY?

Post the output of ```
cat /etc/fstab
```

What version of desktop are you using?

---

### Post by flyfishingphil on 2014-03-17
I don't remember naming it recovery but I just checked it on the tablet and it shows it as RECOVERY. Maybe I need to put it into that, format it and rename it?

RE: Desktop version. The tablet is the Surface RT (I know-bad purchase) running RT 8.1 and the laptop is partitioned and running Win 7 Home  Premium and Ubuntu 12.04 are the OS's but the desktop on Ubuntu is the "Original" style versus the newer one with all of the stuff down the left side.

Here is the sudo report:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=de431376-da02-426a-9420-2ad5d98c6add /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9d9c1db3-602c-4a3a-9626-7028614d2845 none            swap    sw              0       0
(if that means anything!)

ffp

---

### Post by bab1 on 2014-03-17
> **flyfishingphil said:**
> I don't remember naming it recovery but I just checked it on the tablet and it shows it as RECOVERY. Maybe I need to put it into that, format it and rename it?

I wouldn't format it. VFAT works with Windows, Apple, and Linux with no problems.  NTFS only works with Windows and Linux and EXT only works with Linux for the most part.
> 
RE: Desktop version. The tablet is the Surface RT (I know-bad purchase) running RT 8.1 

Windows RT machines are cheap.  I've contemplated getting one..., but I have enough toys right now.  For instance I have a Philips Velo with Windows CE v1 that I still play with.
> 
[and] the laptop is partitioned and running Win 7 Home  Premium and Ubuntu 12.04 are the OS's but the desktop on Ubuntu is the "Original" style versus the newer one with all of the stuff down the left side.

Did you install something or is this just the fallback mode. I'm using the fallback mode on 12.04.  By default it comes with Nautilus as the File Manager.  All of my USB sticks (flash drives) auto mount and show up using the LABEL as the ID.  I can also find it in the File System at /media/LABEL.
>  

Here is the sudo report:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=de431376-da02-426a-9420-2ad5d98c6add /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9d9c1db3-602c-4a3a-9626-7028614d2845 none            swap    sw              0       0
```
(if that means anything!)

ffp
This tells me that the flash drive HAS NOT been added to the fstab file.  This means it should be auto mounted via UDISKS.

I'll bet you tinkered with the system enough to stop the udisks routines from working.  I'm thinking of the Nautilus stuff you installed.  Nautilus should have been there by default.  Of course if you installed MATE or something like that it might have caused the automount problem.

You should be able to mount the USB stick creating a mount point```
sudo mkdir /media/stick
``` ...and then mounting the device manually```
sudo mount -t vfat LABEL=RECOVERY /media/stick -o defaults,uid=1000,gid=1000
```

To unmount it you use ```
sudo umount /media/stick
```

---

### Post by flyfishingphil on 2014-03-17
Got the 12.04 about 3 weeks after it came out. Don't remember seeing Nautilus at that time and don't remember uninstalling it. Have the Nautilus Configurations and the file manager Gnome portion in there so do I need to do something there to make it "see" the thumb drive? Is the sudo you showed "automatic" or do I have to do the sudo entry every time I want to read the stick or remove it?

---

### Post by bab1 on 2014-03-17
> **flyfishingphil said:**
> Got the 12.04 about 3 weeks after it came out. Don't remember seeing Nautilus at that time and don't remember uninstalling it. Have the Nautilus Configurations and the file manager Gnome portion in there so do I need to do something there to make it "see" the thumb drive? Is the sudo you showed "automatic" or do I have to do the sudo entry every time I want to read the stick or remove it?

In the default install of Ubuntu 12.04, GNOME is the window manager and Gnome's Nautilus is the default File Manager.  If you saw folders and files graphically then it is (was) using Nautilus.   You can check to see if indeed the file manager is Nautilus by opening your home directory and right clicking on help> about.If [this]("https://apps.ubuntu.com/cat/applications/precise/nautilus-actions/") is what you are referring to, then this applies> Nautilus actions is an extension for Nautilus, the GNOME file manager. It allows the configuration of programs to be launched on files selected in the Nautilus interface.

I can't tell you what is causing the stick to not be recognized or how to fix that.  In the past when this happened to me, I found it easier and less time consuming to just reinstall.  Did you modify the way Nautilus operates with the Nautilus Actions app?

Yes, those are manual instructions to mount the Lexar stick at a mount point you created.  You will have to mount and unmount the

---

### Post by flyfishingphil on 2014-03-17
Went to File Manager > About and it reads Nautilus 3.4.2.  Yes, your link "this" is what I show installed. Do I need to uninstall and reinstall the Nautilus?

RE: The stick. That's why I wondered about doing a Format and making sure it is xFat32. I wonder if the RT did something that makes it "RT friendly" but not for anything else. The reason I wonder is it renamed it "Recovery" and I wonder if it was formatted to work as an outside recovery source in case of crash. I'll play around with that a bit and come back in if that proves to be a solution.

---

### Post by bab1 on 2014-03-17
> **flyfishingphil said:**
> Went to File Manager > About and it reads Nautilus 3.4.2.  Yes, your link "this" is what I show installed. Do I need to uninstall and reinstall the Nautilus?

No you do not want to re-install Nautilus.  What you installed are extensions for Nautilus and if you leave them alone there should be no problems.
> 

RE: The stick. That's why I wondered about doing a Format and making sure it is xFat32. I wonder if the RT did something that makes it "RT friendly" but not for anything else. The reason I wonder is it renamed it "Recovery" and I wonder if it was formatted to work as an outside recovery source in case of crash. I'll play around with that a bit and come back in if that proves to be a solution.
If you reformat the stick I would reformat it to NTFS.  Both Ubuntu and Windows RT will recognize it.  Stranger things than RT changing things on a partition have happened.  But I have to admit it usually has human help.  :-)

Try reformatting the stick.  It can't hurt it.  I assume you will use the "Disk Utility" to do the formatting.

---

### Post by flyfishingphil on 2014-03-17
OK here's where it all is.

First I figured I'd try an SDHC card in an adaptor and see what I could accomplish using that. I can copy files from the RT, switch it over to Ubuntu and read it with no problem. Next I thought "So why not do the Recovery on the card?" No can do Buckaroo on the RT. It demands the flash drive for that so I ran out and got a couple of 16 GB's on sale. Got home, plugged one in, did the Recovery bit and Viola! the recovery files are on the 16GB "stick".

Second, did a format on the 32GB "stick", (set to NFST) transferred a file on the RT to the stick, switched over to Ubuntu and "Generic device" shows up with no way to open. I am now about to shoot the RT, the laptop and myself, but had another idea.

Third step: Grabbed my wife's Win 7 only, put the stick in there and renamed it to its original name, Lexar. Stuck it in the Ubuntu and it popped open with no problem, able to open the file I stuck in there and ejected properly.

Conclusion: The simple way is the best answer for the complex problem. Restore to original and it works!

I greatly appreciate all of the help and, more importantly your patience with a dummy, on finding the solution to the problem. We may not have done it directly here but you did provide enough info to find the cause/solution.

Thanks again for all of the assist. Here's hoping this might help you help another down the road. 

Call it SOLVED!

ffp

---

