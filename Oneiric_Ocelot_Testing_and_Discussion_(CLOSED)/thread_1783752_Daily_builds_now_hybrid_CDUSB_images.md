---
title: "Daily builds now hybrid CD/USB images"
date: 2011-06-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-06-16
The daily ISOs for the Ubuntu Oneiric development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs.  :D

SOURCE:  [https://lists.ubuntu.com/archives/ubuntu-devel/2011-June/033495.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-June/033495.html)  (ubuntu-devel mailing list)

> 
**Colin Watson** cjwatson at ubuntu.com 
*Wed Jun 15 21:22:34 UTC 2011*

[B][COLOR="Red"]As of tomorrow's daily builds, all Oneiric amd64 and i386 CD images on
cdimage.ubuntu.com can also be written directly to a USB device.[/COLOR][/B]  You
can still use usb-creator if you need to enable persistent storage on
the USB stick, but if all you need is to install from the stick then
this simplifies the process.

There is a small size cost to this feature; part of this is partition
alignment to 1MB "cylinders" (since the image now has to simultaneously
look like a CD and a partitioned USB disk), and part of it is a second
directory tree whose size is roughly proportional to the number of files
in the image.  On the server CD (and probably the alternate CD too,
though I haven't measured that), this came out to about 5MB, but as luck
would have it I found a way to save about the same amount by hardlinking
some files together, so the size there stays roughly the same.  On the
desktop CD, unfortunately, we lose about 1MB (although I consider myself
to have "paid" for this by way of the 2MB or so we gained by switching
to live-build ...).  If this becomes a problem close to release time,
then we may be able to shave off a bit at the possible cost of some
USB-booting compatibility on a few machines by dropping the 1MB
alignment.  See the recent thread on pkg-libburnia-devel for details.

I realise that we're behind a number of other major distributions on
this.  The delay was because (like Debian) we couldn't simply use
isohybrid because that would break jigdo downloads, so we had to switch
to xorriso as the CD image generator on these architectures for its new
JTE support, and by the time all that landed in Debian I didn't really
want to cram it into 11.04.  

See [http://blog.einval.com/2011/01/07#isohybrid_CDs](http://blog.einval.com/2011/01/07#isohybrid_CDs) for the gory details,
and thanks a lot to Steve, Thomas, and George for their hard work on
that.

Please file bugs on [https://bugs.launchpad.net/ubuntu-cdimage](https://bugs.launchpad.net/ubuntu-cdimage) if this
change causes the image to stop working on machines where it previously
worked.

Cheers,

-- 
Colin Watson                                       [cjwatson at ubuntu.com]




**[SIZE="3"][COLOR="DarkOrange"]HOWTO:[/COLOR] [COLOR="Blue"]Write Oneiric amd64 or i386 Daily Build CD/USB images directly to USB stick[/COLOR][/SIZE]**


Install zsync package (if missing)
```
sudo apt-get install zsync
```

Acquire zsync Daily Build ISO (choose your architecture)
```
[http://cdimage.ubuntu.com/daily-live/current/]("http://cdimage.ubuntu.com/daily-live/current/")
```

Update zsync Daily Build ISO (for example)
```
zsync http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.iso.zsync
```

Determine where your USB Flash Drive resides, using fdisk (from a terminal)
```
vindsl@Zuul:~$ **[COLOR="Blue"]sudo fdisk -l[/COLOR]**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20964824    10482381   83  Linux
/dev/sda2       156296446   312575999    78139777    5  Extended
/dev/sda3        20965376   154189823    66612224   83  Linux
/dev/sda4       154189824   156295167     1052672   82  Linux swap / Solaris
/dev/sda5       156296448   177268735    10486144   83  Linux
/dev/sda6       310474752   312575999     1050624   82  Linux swap / Solaris
/dev/sda7       177270784   310472703    66600960   83  Linux

Partition table entries are not in disk order

**[COLOR="Blue"]Disk /dev/sdb: 3926 MB, 3926949888 bytes[/COLOR]**
121 heads, 62 sectors/track, 1022 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
```

Or, use a GUI Disk Utility (from the desktop)

[IMG]http://vindsl.com/images/Screenshot_at_2011-08-27_18:14:02.png[/IMG]

Write updated ISO directly to USB Flash Drive (for example)
```
sudo dd if=oneiric-desktop-i386.iso of=/dev/sdb
```

If you feel adventurous, adding the following seems to speed up the writing process considerably
```
sudo dd if=oneiric-desktop-i386.iso of=/dev/sdb **[COLOR="Blue"]oflag=direct bs=1048576[/COLOR]**
```

Configuring the BIOS in your PC, so it boots from a USB stick, is left as an exercise in the second-order coefficient.  :)

---

### Post by coffeecat on 2011-06-16
I'm probably being extremely dense here, but if one doesn't use usb-creator, how exactly does one write the ISO directly to the USB drive? Tbh, I'll be glad to not have to use usb-creator. The Natty version prompts you no less than three times for your password during the process of writing an ISO to a USB that need reformatting.

---

### Post by m.rankovic on 2011-06-16
from: [http://blog.einval.com/2011/01/07#isohybrid_CDs](http://blog.einval.com/2011/01/07#isohybrid_CDs)

"What does this mean for end users?

Instead of having to specially prepare USB sticks for the installer, you can now simply use dd to write the image straight to the raw stick, e.g.:

**# dd if=debian-testing-i386-netinst.iso of=/dev/sdX**"

---

### Post by coffeecat on 2011-06-16
> **m.rankovic said:**
> from: [http://blog.einval.com/2011/01/07#isohybrid_CDs](http://blog.einval.com/2011/01/07#isohybrid_CDs)

Yes, I thought it might be dd. I missed the link in VinDSL's quote of Colin Watson. Sorry about that and thanks.

---

### Post by jerrylamos on 2011-06-16
> **coffeecat said:**
> I'm probably being extremely dense here, but if one doesn't use usb-creator, how exactly does one write the ISO directly to the USB drive? Tbh, I'll be glad to not have to use usb-creator. The Natty version prompts you no less than three times for your password during the process of writing an ISO to a USB that need reformatting.

Coffeecat,

I use gparted to format 2 partitions on the USB, the first F32 for the image and the 2nd EXT3 labeled casper-rw for persistent.  I've had trouble trying to get usb-creator to behave.  Ubuntu install has screwed me up as well so I use gparted before doing an install.

I then just plain flat copy the .iso to the first partition on the USB.

I add the following to /etc/grub.d/40_custom
```

menuentry "Ocelot sdb1 USB" {
set isofile="/boot/iso/oneiric-desktop-i386.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper persistent iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

```
then sudo update-grub.

This has been working for me.  Note you can put the .iso into a folder on the hard drive example /boot/iso which is a bit faster than the USB.  In either case size of the daily build is no longer an issue.  I even boot the .iso from a hard drive and install to a 2nd hard drive or a USB hard drive.  I haven't tried installing to the same hard drive as the .iso is on.  Chicken.

Now this is all before the changes Colin mentioned.  I'm doing a zsync right now.

Coffeecat, I'd appreciate it if you could interpret colin's explanation to us ordinary testers.

Thanks, Jerry

---

### Post by Grenage on 2011-06-16
> **VinDSL said:**
> The daily ISOs for the Ubuntu Oneiric development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs.  :D

SOURCE:  [https://lists.ubuntu.com/archives/ubuntu-devel/2011-June/033495.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-June/033495.html)  (ubuntu-devel mailing list)

Fantastic news, and something I've been waiting for.

---

### Post by jerrylamos on 2011-06-16
Just did a zsync on the 16 June to a folder on the hard drive, and booted the .iso with grub2 O.K. as usual.

So I don't know what Colin & crew have done or what to do to take advantage of it?

This entry is from the usual way I boot .iso as given in my previous post.  I've put the .iso on a USB and boot the same way, but so far haven't been stung by just booting the .iso from the hard drive.  Famous last words.

Progress, nm applet successfully connected wireless today.  It's been crashing.

I did get a lightdm crash but it's still running.  Crash report in process...launchpad bug #796272.

Jerry

---

### Post by coffeecat on 2011-06-16
> **jerrylamos said:**
> Coffeecat, I'd appreciate it if you could interpret colin's explanation to us ordinary testers.

I don't think it needs that much interpreting. Perhaps, like me, you missed this bit:

>   Instead of having to specially prepare USB sticks for the installer, you can now simply use dd to write the image straight to the raw stick, e.g.: 
# dd if=debian-testing-i386-netinst.iso of=/dev/sdX 

Obviously, substituting the Ubuntu ISO filename for the debian one.

---

### Post by fjgaude on 2011-06-16
I dd copied the i386.iso daily of today to a fresh 4G thumb and when I booted the msg "no operating system", repeated over and over.

Any help? Thanks!

---

### Post by jerrylamos on 2011-06-16
> **fjgaude said:**
> I dd copied the i386.iso daily of today to a fresh 4G thumb and when I booted the msg "no operating system", repeated over and over.

Any help? Thanks!

I can't tell from your note whether you added the above to /etc/grub.d/40_custom?

And then did the sudo update-grub?

On the fresh 4G thumb, did you partition it with gparted and format it, first partition to F32?  A fresh USB might come formatted I don't know how, example F16 which I've had no luck with.

Do note that I used hd(1,1) for the USB drive which is how it comes up on my pc.  You should be able to tell from gparted whether it is /dev/sda or /dev/sdb (as mine is) or /dev/sdc which it is on another of my pc's.

Jerry

---

### Post by jerrylamos on 2011-06-16
> **coffeecat said:**
> I don't think it needs that much interpreting. Perhaps, like me, you missed this bit:



Obviously, substituting the Ubuntu ISO filename for the debian one.
Thanks, coffeecat, but my experience dd is an ancient brutal command while there are some protections built into copy....

Once having the .iso copied, should be able to do a zsync if the USB has enough space for two .iso files.  Maybe?

Jerry

---

### Post by coffeecat on 2011-06-16
> **fjgaude said:**
> I dd copied the i386.iso daily of [SIZE=3]**today**[/SIZE] to a fresh 4G thumb and when I booted the msg "no operating system", repeated over and over.

Any help? Thanks!

** cough - cough ** :wink:

> **VinDSL said:**
> [quote="Colin Watson"][COLOR=Red]As of **[SIZE="3"]tomorrow[/SIZE]**'s daily builds[/COLOR][/quote]

---

### Post by coffeecat on 2011-06-16
> **jerrylamos said:**
> Thanks, coffeecat, but my experience dd is an ancient brutal command while there are some protections built into copy....

Brutal or not, dd does a byte by byte copy which is what is needed, whereas cp (I presume you mean cp by "copy") does a file copy, which is of no use in this situation. As fas as I understand it.

---

### Post by fjgaude on 2011-06-16
I formatted the /dev/sdd with ext2. This is my 40_custom file:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ocelot iso" {
#set isofile="/boot/iso/oneiric-desktop-amd64.iso"
set isofile="/dev/ssd1"
#loopback loop (hd2,2)$isofile
loopback loop (hd3,1)$isofile
#linux (loop)/casper/vmlinuz boot=casper persistent iso-scan/filename=$isofile 
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
} 
```

Have to run now, but likely I'll wait and do a new daily tomorrow. I can see what I've done wrong.

Thanks for the inputs.

---

### Post by Starks on 2011-06-16
Hybrid ISO works beautifully.

You need to make sure that there are no partitions on the USB before dd'ing.

---

### Post by donniezazen on 2011-06-16
Will Windows user have to use unetbootin or may be image writer for hybrid images? Why is their no 64 bit AMD version as of daily image?

---

### Post by jerrylamos on 2011-06-16
> **Starks said:**
> Hybrid ISO works beautifully.

You need to make sure that there are no partitions on the USB before dd'ing.
?
So I took a 2 GB USB stick and made two partitions:

1 partition Fat32 with boot flag
1 partition Ext2 labelled casper-rw

Then did

#! /bin/bash
# [http://blog.einval.com/2011/01/07#isohybrid_CDs](http://blog.einval.com/2011/01/07#isohybrid_CDs)
df
echo "check USB device address?" 
echo "is it /dev/sdd1?"
read temp
sudo dd if=oneiric-desktop-i386.iso of=/dev/sdd1
echo "any messages?"
read temp
#! exit

The dd took a while.

Booted on the USB stick which said:

isolinux.bin missing or corrupt

then promptly fell through to usual grub boot on the hard drive.

Let me try again with format and nothing else on the USB stick.

Did simple format from Desktop.  Did the dd.  Booted and got

missing operating system

I think I'll go back to my usual copying the .iso and using 40_custom.

Jerry

---

### Post by nm_geo on 2011-06-16
Going forward this process for making a bootable thumb drive is going to save time and be much more efficient for development testers.  I just created one using today zsync image with dd and it was faster for me and only required one sudo command.  It booted clean as a whistle by the way the stick was fat32 format or raw (as bought).  I am a big fan already.. to the devs  GOOD ONE  Only one partition as stated earlier by Starks ..on a 16GB flash drive -- wasteful huh?

---

### Post by fjgaude on 2011-06-16
Okay, no partitions, no sdd1 just sdd formated to FAT32... will give it a try and report back Friday. To format likely requires at least one partition, eh?

---

### Post by nm_geo on 2011-06-16
> **fjgaude said:**
> Okay, no partitions, no sdd1 just sdd formated to FAT32... will give it a try and report back Friday. To format likely requires at least one partition, eh?
   Only one partition... as Starks said. Mine was fast to write.. as I see it..

By the way you will see no activity in the terminal while the dd is taking place, but if your flash has a light blinking it is working.  I made mine while I was working in my Lucid then booted right into the flash drive OO... Extra cool..

---

### Post by Starks on 2011-06-16
NO PARTITION.

Not a single partition. You are supposed to dd to a RAW, UNPARTITIONED drive.

sdd, not sdd1, because there is no sdd1

---

### Post by Grenage on 2011-06-17
Why worry about existing partitions, wouldn't writing the image to the drive remove any existing partitions?

---

### Post by VinDSL on 2011-06-17
I finally got a chance to 'burn' a hybrid image tonight, and it worked as advertised.  

I started with a new USB thumb drive - $8.00 USD for 4GB at Walmart.  LoL!

After doing a DD & reboot, I got the "Missing operating system" message that Jerry reported (above).

Next, I re-formatted the USB thumb drive using GParted (fat32 msdos).  This time it booted just fine.

Not happy to leave well enough alone... 

Next, I deleted everything on the USB thumb drive, e.g no partition - DD & reboot.  This worked fine too.

Here is the command that I used:

```

sudo dd if=oneiric-desktop-i386.iso of=/dev/sdb

```

After 3-4 minutes, this response popped up:

```
1452632+0 records in
1452632+0 records out
743747584 bytes (744 MB) copied, 114.48 s, 6.5 MB/s

```

...and all was good.

Pretty slick!  Sure beats burning coasters...  :D

---

### Post by jerrylamos on 2011-06-17
> **Starks said:**
> NO PARTITION.

Not a single partition. You are supposed to dd to a RAW, UNPARTITIONED drive.

sdd, not sdd1, because there is no sdd1
Starks, how do you make a "raw" drive?  I'm not going to buy a new one every day, and most of the ones here at the stores have something on them.

I'll try sdb or sdc or sdd (Ubuntu seems to be somewhat random in choice).

Thanks, Jerry

---

### Post by jerrylamos on 2011-06-17
> **nm_geo said:**
> Going forward this process for making a bootable thumb drive is going to save time and be much more efficient for development testers.  I just created one using today zsync image with dd and it was faster for me and only required one sudo command.  It booted clean as a whistle by the way the stick was fat32 format or raw (as bought).  I am a big fan already.. to the devs  GOOD ONE  Only one partition as stated earlier by Starks ..on a 16GB flash drive -- wasteful huh?

Faster??  My .iso is in /boot/iso on a hard drive.  I select zsync exec right there on the spot, then reboot, and since Grub menu already has the 40_custom it comes right up.

No dd involved.  No time wasted.

Now I do have to check the state of casper-rw if there is one.  Sometimes new builds can re-use what's in casper-rw, sometimes I get a black screen.  To be safe either format it while the zsync is going on or just don't have one.

That's for testing frequently, every day when I have time.  Now for distributing Ubuntu to new users who have a pc that can boot from USB, then it's simpler than crawling thru Startup Disk Creator.

For now I'll let someone else test this capability.

Jerry

---

### Post by VinDSL on 2011-06-17
> **jerrylamos said:**
> Starks, how do you make a "raw" drive?

For the sake of discussion, I'll tell you what I did.

[LIST]
[*]I unmounted my USB thumb drive (/dev/sdb)

[*]Opened GParted

[*]Clicked on /dev/sdb

[*]Right-clicked the partition (only had one)

[*]Choose Delete & Apply
[/LIST]

Afterwards, GParted reported (basically) 4GB unallocated, e.g. nothing else.

AFAIK, that's as raw as it gets!  :)

Really, when you think about it, it only makes sense to wipe it clean.

When you burn an ISO to CD/DVD, you don't have to partition it.

My theory is, the same applies to 'burning' a hybrid image to a thumb drive.  ;)

---

### Post by sparker256 on 2011-06-17
> **VinDSL said:**
> For the sake of discussion, I'll tell you what I did.

[LIST]
[*]I unmounted my USB thumb drive (/dev/sdb)

[*]Opened GParted

[*]Clicked on /dev/sdb

[*]Right-clicked the partition (only had one)

[*]Choose Delete & Apply
[/LIST]

Afterwards, GParted reported (basically) 4GB unallocated, e.g. nothing else.

AFAIK, that's as raw as it gets!  :)

Really, when you think about it, it only makes sense to wipe it clean.

When you burn an ISO to CD/DVD, you don't have to partition it.

My theory is, the same applies to 'burning' a hybrid image to a thumb drive.  ;)
When I use startup disk creator I always erase the drive and make a 2G persistence on a 8G thumb drive.

Bill

---

### Post by el_koraco on 2011-06-17
wouldn't it be easier to right click on the mounted flash drive icon on the desktop, and select "format"?

---

### Post by sparker256 on 2011-06-17
> **soham_1207 said:**
> Will Windows user have to use unetbootin or may be image writer for hybrid images? Why is their no 64 bit AMD version as of daily image?
It appears that the old amd64 has become amd64+mac and I have used a oneiric-desktop-amd64+mac.iso from 061611 with startup disk creator and had good results. I am zsyncing a oneiric-desktop-amd64+mac.iso from 061711 as I type so this will be another test.

Bill

---

### Post by coffeecat on 2011-06-17
> **Grenage said:**
> Why worry about existing partitions, wouldn't writing the image to the drive remove any existing partitions?

Indeed. +1

With the greatest of respect, there are some unnecessary complications being posted. I have just dd'd this morning's 64-bit ISO to a previously-used pendrive. It took less than 5 minutes.

The pendrive already had Maverick live on it created by startup disc creator. Fdisk -lu gave me:

```
Disk /dev/sdc: 2063 MB, 2063597568 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b3998

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62     4027519     2013729    c  W95 FAT32 (LBA)
```I didn't even bother to unmount it, but instead:

```
sudo dd if=oneiric-desktop-amd64+mac.iso of=/dev/sdc
```That took about 3 minutes. Then, re-running fdisk:

```
Disk /dev/sdc: 2063 MB, 2063597568 bytes
19 heads, 24 sectors/track, 8838 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ed4826c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          64     1444439      722188   17  Hidden HPFS/NTFS
```Different start sector and different filesystem code (NTFS? :o), so the partition table has clearly been replaced by the dd command. Proof and pudding, of course: the pendrive boots up just fine on my laptop to a usable 3d Unity desktop. Until I opened Gparted, that is, when the GUI promptly crashed. :lol: Downloading the alternate ISO now.

---

### Post by floydsp on 2011-06-17
Thank You so much coffeecat for this post now even I can understand this!

Am giving it a try now

floydsp

---

### Post by teh603 on 2011-06-17
> **Starks said:**
> NO PARTITION.

Not a single partition. You are supposed to dd to a RAW, UNPARTITIONED drive.

sdd, not sdd1, because there is no sdd1You do realize that this makes about half of the USB sticks out there useless, because they come pre-partitioned in a way that parted can't seem to remove?

---

### Post by fjgaude on 2011-06-17
No joy here. I've tried everything, raw, fat32, dd... I get OS loading, can't determine /c/h/s, os must be loaded first.

I think some of us have something different in the BIOS or whatever that the new hybrid approach simply doesn't work. At least not with the i386. Will try the mac amd64 latter today. Have other work to do now.

---

### Post by nm_geo on 2011-06-17
> **jerrylamos said:**
> Faster?? My .iso is in /boot/iso on a hard drive. I select zsync exec right there on the spot, then reboot, and since Grub menu already has the 40_custom it comes right up.
 
No dd involved. No time wasted.
 
Now I do have to check the state of casper-rw if there is one. Sometimes new builds can re-use what's in casper-rw, sometimes I get a black screen. To be safe either format it while the zsync is going on or just don't have one.
 
That's for testing frequently, every day when I have time. Now for distributing Ubuntu to new users who have a pc that can boot from USB, then it's simpler than crawling thru Startup Disk Creator.
 
For now I'll let someone else test this capability.
 
Jerry
 
Jerry I should have been more clear in what I was saying.  The writing to the stick with dd versus building from Startup Disk Creator is a faster, more efficent process.  
 
Your booting from a folder on the hard drive, I understand is much quicker than using a flash drive to boot from.  However, most new users will not be booting the testing iso like you do, and if I am building them a live flash drive dd'ing will be the process I select.  
 
We know there are a number of testers who are checking the daily builds to see if they boot cleanly with almost every daily update.  Seems to me this dd process and zsync will be very efficent and save mucho time. 
 
 +1  from this end of the planet..  I Like It.

---

### Post by coffeecat on 2011-06-17
> **coffeecat said:**
> Downloading the alternate ISO now.

... which I wrote to the same pendrive (without wiping it), with:

```
sudo dd if=oneiric-alternate-amd64+mac.iso of=/dev/sdc
```Again, it took a few minutes only and I used the pendrive to install Oneiric to a spare partition, from which I can boot into a  Unity desktop which is more stable than from a daily a few days ago. Onward and upward!

> **teh603 said:**
> You do realize that this makes about half of the USB sticks out there useless, because they come pre-partitioned in a way that parted can't seem to remove?

Have a look at my earlier post #30 - I picked this point up. You do not need a raw, unpartitioned flash drive. You do not need to re-partition it. You do not need to do anything to it except run the dd command.

But what are these flash drives that parted can't remove the partitions from? I've never come across one. If you have a flash drive that is partitioned in a problematic way, simply use Gparted to write a new partition table = end of old partitions.

---

### Post by nm_geo on 2011-06-17
> **coffeecat said:**
> ... which I wrote to the same pendrive (without wiping it), with:
 
```
sudo dd if=oneiric-alternate-amd64+mac.iso of=/dev/sdc
```Again, it took a few minutes only and I used the pendrive to install Oneiric to a spare partition, from which I can boot into a Unity desktop which is more stable than from a daily a few days ago. Onward and upward!
 
 
 
Have a look at my earlier post #30 - I picked this point up. You do not need a raw, unpartitioned flash drive. You do not need to re-partition it. You do not need to do anything to it except run the dd command.
 
But what are these flash drives that parted can't remove the partitions from? I've never come across one. If you have a flash drive that is partitioned in a problematic way, simply use Gparted to write a new partition table = end of old partitions.
 
Thanks for the update coffecat on the alternate iso creation with the dd process.  
 
I usually install my testing versions from the alternate iso.  It works better for me and doesn't lock-up the install during the migration assistant option that I never select  anyway.

---

### Post by teh603 on 2011-06-17
> **coffeecat said:**
> But what are these flash drives that parted can't remove the partitions from? I've never come across one. If you have a flash drive that is partitioned in a problematic way, simply use Gparted to write a new partition table = end of old partitions.Kubuntu's Partition Editor hangs at 0% if I try to do anything to a USB stick, for some reason. Its been doing that since at least 10.04, possibly longer.

---

### Post by coffeecat on 2011-06-17
> **teh603 said:**
> Kubuntu's Partition Editor hangs at 0% if I try to do anything to a USB stick, for some reason. Its been doing that since at least 10.04, possibly longer.

Curious. I doubt it's to do with the actual flash drives, though. What does Kubuntu use as a partition editor? I've not used Kubuntu for a little while. Is it Gparted themed for KDE, or Qtparted (if that's still around), or something else?

---

### Post by Starks on 2011-06-17
> **jerrylamos said:**
> Starks, how do you make a "raw" drive?  I'm not going to buy a new one every day, and most of the ones here at the stores have something on them.

I'll try sdb or sdc or sdd (Ubuntu seems to be somewhat random in choice).

Thanks, Jerry

I've already explained this.

You delete all partitions on the drive and don't create any before the dd.

After you dd the image, you can create partitions with the remaining space.

---

### Post by teh603 on 2011-06-17
> **coffeecat said:**
> Curious. I doubt it's to do with the actual flash drives, though. What does Kubuntu use as a partition editor? I've not used Kubuntu for a little while. Is it Gparted themed for KDE, or Qtparted (if that's still around), or something else?Not sure, but I just filed a bug on it.

---

### Post by fjgaude on 2011-06-17
> **Starks said:**
> I've already explained this.

You delete all partitions on the drive and don't create any before the dd.

After you dd the image, you can create partitions with the remaining space.

I've done exactly what you suggest and still no joy! Will keep looking for what goes wrong as it tries to boot.

---

### Post by el_koraco on 2011-06-17
> **teh603 said:**
> Not sure, but I just filed a bug on it.

Isn't Kubuntu's partition editor generally... not up to the task?

---

### Post by jerrylamos on 2011-06-17
> **el_koraco said:**
> Isn't Kubuntu's partition editor generally... not up to the task?

I usually do 
apt-get install gparted
which has been working.  I don't see any "raw image" selection so I don't do a hybrid USB boot, I just boot from the hard drive from a folder /boot/iso which is where I do the zsync, so no dd required.

Jerry

---

### Post by fjgaude on 2011-06-17
I took raw image to be unallocated, i.e., no partition table.

---

### Post by seeker5528 on 2011-06-17
> **jerrylamos said:**
> I usually do 
apt-get install gparted
which has been working.  I don't see any "raw image" selection so I don't do a hybrid USB boot, I just boot from the hard drive from a folder /boot/iso which is where I do the zsync, so no dd required.

If your flash drive was sdb, sdb would be the "raw" disk, you don't create it, it just is, sdb1, sdb2, etc... would be partitions on the disk.

If you have partitions outside of the area that will be over-written, the MBR of the flash drive will be overwritten and part of the MBR is reserved for the partition table so you will probably lose access to all partitions on the flash drive, testdisk might be able to find and rewrite them, but it's better to plan ahead.

Later, Seeker

---

### Post by arpanaut on 2011-06-17
Are we not talking apples and oranges here, ie. USB-HDD and USB-Flash Drives
 Is not this hybrid CD/USB images thing much more to accommodate installing to CD's & Flash drives more so than USB-HDD's

I may be mistaken but I think that Jerry is talking USB-HDD and others are talking USB-Flash Drives. 
Now it should work regardless of which one is used, but I would think it is not appropriate for USB-HDD it would seem to be a waste of capacity on the HDD. I wouldn't want to be destroying the partition table on my USB-HDD every time I dd'ed the new daily image.

Does there need to be a better definition as to what these images are meant to be used for?

I am booting my daily images with the method promoted by Jerry and it works well on HDD, Haven't tried it yet with these new images on a Flash Drive.

---

### Post by fjgaude on 2011-06-17
I dd to a flash drive; I have the .iso on a HDD partition just like Jerry. Neither work now with the daily builds.

I have to wait and get the released Alpha 2 when it comes out on 30 June. I had no trouble with the Alpha 1, but couldn't update it on a flash drive. I never got the persistent feature to work either on HDD or on flash drive. So... I wait!

---

### Post by arpanaut on 2011-06-17
LOL I haven't found that I would want anything  to Persist on any of the daily's as of yet, but that is something else.
I too await a usable image, maybe at A2. <lame attempt at humor>

---

### Post by jerrylamos on 2011-06-17
> **arpanaut said:**
> Are we not talking apples and oranges here, ie. USB-HDD and USB-Flash Drives
 Is not this hybrid CD/USB images thing much more to accommodate installing to CD's & Flash drives more so than USB-HDD's

I may be mistaken but I think that Jerry is talking USB-HDD and others are talking USB-Flash Drives. 
Now it should work regardless of which one is used, but I would think it is not appropriate for USB-HDD it would seem to be a waste of capacity on the HDD. I wouldn't want to be destroying the partition table on my USB-HDD every time I dd'ed the new daily image.

Does there need to be a better definition as to what these images are meant to be used for?

I am booting my daily images with the method promoted by Jerry and it works well on HDD, Haven't tried it yet with these new images on a Flash Drive.

In this thread I've tried USB memory sticks to do the hybrid thing.  No luck yet.  When all else fails read the book which I should do more thoroughly I guess.  

I also have a USB hard drive which I have Ocelot installed on, in theory if install screws up it won't screw up the main hard drive (this is Alpha, I'm backed up).

Now I usually boot the daily .iso from a folder on the hard drive on three test systems which has been working for me (oops, Firefox just crashed & submitted a report to Mozilla. This is the 17 June Ocelot build).

If the developers have a sanctioned method such as dd to the USB stick, I'll try it but for my usual testing it's faster just to zsync the .iso and boot it direct right where it is, no dd or install required.  Persistent helps.

Jerry

---

### Post by VinDSL on 2011-06-18
I just tried the "zsync thing".  That's cute!  :D

I don't *think* it saved me any time, over downloading a regular ISO (I'm on a high-speed connection), but...

It might serve a useful purpose in the future.  CRON comes to mind.

It's definitely a "lazy boy's" tool (just like CRON) and I'm pretty lazy, so...  ;)

---

### Post by nm_geo on 2011-06-18
> **VinDSL said:**
> I just tried the "zsync thing".  That's cute!  :D

I don't *think* it saved me any time, over downloading a regular ISO (I'm on a high-speed connection), but...

It might serve a useful purpose in the future.  CRON comes to mind.

It's definitely a "lazy boy's" tool (just like CRON) and I'm pretty lazy, so...  ;)
If you do the current daily builds it will save you time. 

Say only 20% of the new daily is different from the old current you 

have saved.  Then only the 20% that is different will be added.  It is 

certainly used by Lazy-Boys LOL I be One

---

### Post by VinDSL on 2011-06-18
> **fjgaude said:**
> Will keep looking for what goes wrong as it tries to boot.
I'm sure you've done all this, but here are couple of quick thoughts...

It took a few stabs, to get the CD/USB image to work for me.  Basically:

[LIST]
[*]I reformatted my (new) USB flash drive using fat32 msdos, via GParted. The OEM fat32 formatting was giving me errors at boot.
[*]Then, I deleted the partition using GParted, essentially giving me a raw drive, so called.
[/LIST]

Since then, I haven't had a single problem writing. reading, or booting from my flash drive.

Secondly, I have successfully booted this CD/USB flash drive on several machines (different manufacturers, different BIOS) during the past 2 days, and I haven't had a failure yet.

But...

In every case, I've had to do a cold boot, to get the flash drive to boot, and the machine to work correctly, i.e. properly recognize the keyboard, correct screen res, network access...

By "cold boot" I mean:

[LIST]
[*]Completely shut the computer off.
[*]Plug in the flash drive.
[*]Turn the computer on.
[*]Immediately go into the BIOS and choose USB Flash ROM (or whatever) as the boot device.
[/LIST]

Different machines handle the selection of boot drives in different ways.  There is no standardized way of doing this.

If you don't get into BIOS quickly enough, you'll have to start the cold boot process all over again, e.g. don't just hit the reset button or alt-ctrl-del.  Turn the computer off and try again.

As an aside, today's Daily Build (17-June) is the first one that's worked on this particular machine, without OS errors (Unity 2D crashing, blah, blah, blah), so this discussion may become a moot point for me, very quickly.  Today may be the day that I wipe my 11.10 pre-Alpha partition and start anew.

Still, it's going to be uber-handy, carrying the latest version of Ubuntu on my keychain - knowing I can boot it anytime, anywhere, on any machine (as long as the sys admin hasn't defeated the USB ports and/or password protected the BIOS).  ;)

---

### Post by VinDSL on 2011-06-18
> **nm_geo said:**
> [Zsync] is certainly used by Lazy-Boys LOL I be One
Heh!  Don't get me wrong.  Zsynch is going to be great!  I can see that already.

I didn't realize (until last night) that you could switch back n' forth between distros by simply changing the filename.  :)


SOURCE:  [https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage) (Official ZsyncCDImage Help)
> 
zsync is a wonderful piece of software that downloads only the parts of a file that are changed, so as to avoid downloading a full copy every time.

A nice thing about the way the Ubuntu CDs are constructed is that it is quite easy to keep an up to date local install CD using zsync. Since the daily CDs generally change quite little, it can be processed quite quickly.

**[COLOR="Red"]zsync also perform a checksum comparison making it possible to change the flavour of the ISO [B][COLOR="Blue"](e.g. you have an ISO of Ubuntu and you want to change it on Kubuntu. Simply copy/paste the right line for Kubuntu and it will download just the parts that differs from the two versions)[/COLOR]**.[/COLOR][/B]



You could easily run a different distro every day, using zsync & DD...  :D

---

### Post by Starks on 2011-06-18
i like how everyone thinks zsync is this great new thing

it's been around for the past few years for ubuntu

---

### Post by nm_geo on 2011-06-18
> **VinDSL said:**
> Heh!  Don't get me wrong.  Zsynch is going to be great!  I can see that already.

I didn't realize (until last night) that you could switch back n' forth between distros by simply changing the filename.  :)


SOURCE:  [https://help.ubuntu.com/community/ZsyncCdImage](https://help.ubuntu.com/community/ZsyncCdImage) (Official ZsyncCDImage Help)



You could easily run a different distro every day, using zsync & DD...  :D

  See I never even thought of that last point Vin.. That is cool..

---

### Post by jerrylamos on 2011-06-18
> **VinDSL said:**
> 
...
As an aside, today's Daily Build (17-June) is the first one that's worked on this particular machine, without OS errors (Unity 2D crashing, blah, blah, blah), so this discussion may become a moot point for me, very quickly.  Today may be the day that I wipe my 11.10 pre-Alpha partition and start anew.
....
I've successfully done 17 June installs on a desktop and a netbook.  Both can run Unity 3D but I'm running Unity 2D.  Wireless even worked on the netbook.  

I didn't time the installs but they seemed relatively quick except for the infernal language downloads.  I'm hundreds of miles from any foreign country and have no correspondence with another country except Australia.  

Presuming you're backed up on all critical data, go for it!  Crashes still occur with good recovery.

Jerry

---

### Post by cariboo on 2011-06-19
> **jerrylamos said:**
> I've successfully done 17 June installs on a desktop and a netbook.  Both can run Unity 3D but I'm running Unity 2D.  Wireless even worked on the netbook.  

I didn't time the installs but they seemed relatively quick except for the infernal language downloads.  I'm hundreds of miles from any foreign country and have no correspondence with another country except Australia.  

Presuming you're backed up on all critical data, go for it!  Crashes still occur with good recovery.

Jerry

I just do installs on my netbook without a network cable attached, Broadcom wireless doesn't work on my netbook without installing the proprietary drivers, so it bypasses all the language files until a network connection is established. They will be downloaded and installed when I finish up the installation, while also doing something else.

---

### Post by fjgaude on 2011-06-19
VinDSL, I did exactly what you said to do with the 17th daily and it didn't work. I did it all again with the 19th x64 and it worked. I'm entering this post from Firefox from the dd'ed 4G flash drive.

So, I have no idea what makes the difference, but I can see how far along this present Alpha is. No bugs, yet!

Thanks for all the detailed help, from all of you.

---

### Post by jerrylamos on 2011-06-19
Finally....got the dd thing to work and this IBM Thinkpad T40 actually booted off the USB stick.

Now the USB ports are fairly flaky for whatever reason, likely T40 bios, and this T40 won't boot from some USB sticks, and this T40 won't boot from my two USB hard drives, and it doesn't do Unity 3D, but Unity 2D is fine thanks on this 1280x1024 external monitor.

The dd went and went.  I fell asleep.  Then the boot was hardly any faster.  zzzz.

But it did work and I'm entering this from 19 June daily build as booted from hybrid CD/USB image.

Now for the Alpha crashes....

Jerry

---

### Post by VinDSL on 2011-06-26
Added a HOWTO to the first post...

---

### Post by ZarathustraDK on 2011-06-26
Just chiming in...

The dd-woes some people experience sound similar to some of the USB-creator-problems I have, mainly partitioning/filesystem-related ones.

If I wanted to be 100% sure a USB would work with the iso, then I had to use gparted to first remove existing partitions/filesystems, then create a new fat32 partition. I had to do this because sometimes it borked even if the existing filesystem was fat32, which is strange IMO.

Makes one wonder why the USB-creator isn't rigged to simply bleach, scrub and cleanse by fire the device one wants to use as a live-usb before it asks for an iso.

I know, unrelated, just sayin' :)

---

### Post by fjgaude on 2011-06-26
Using the 24 June daily I installed the iso into VMware Player without issue, even the Tools came in automatically. Wow, the Alpha is getting there for sure.

I also was successful in using the iso grub install technique with the mouse and keyboard working after a system reboot.

I await for Alpha 2, and might install it onto a partition of the three drives in my main box, dropping the iso grub.

---

### Post by VinDSL on 2011-06-26
> **ZarathustraDK said:**
> If I wanted to be 100% sure a USB would work with the iso, then I had to use gparted to first remove existing partitions/filesystems, then create a new fat32 partition. I had to do this because sometimes it borked even if the existing filesystem was fat32, which is strange IMO.

Makes one wonder why the USB-creator isn't rigged to simply bleach, scrub and cleanse by fire the device one wants to use as a live-usb before it asks for an iso.

I know, unrelated, just sayin' :)
No!  NOT unrelated at all!  You are correct.

Until recently, I only had a couple of USB sticks, and they were filled with essentials, sooo...

When I decided to try this hybrid CD/USB idea, I bought a brand-new PNY 4GB stick ($8.00 USD).

Long story short:  I had to "bleach, scrub and cleanse it by fire" (via GParted) before it would CORRECTLY write the ISO.  Otherwise, I got a "No operating system" error at boot, using the OEM formatting.

IMO, using a RAW USB Flash Drive is paramount!

The only reason I didn't add this step to the HOWTO is because I didn't want to be responsible for eating someone's lunch, so to speak.

GParted can be a dangerous tool, in the wrong hands!

I've used GParted, so long, that it's second nature - like shaving or brushing my teeth, but noobs can do a LOT of damage with it, you know?!?!?

---

### Post by jerrylamos on 2011-06-27
> **VinDSL said:**
> 
I've used GParted, so long, that it's second nature - like shaving or brushing my teeth, but noobs can do a LOT of damage with it, you know?!?!?

I've had A LOT! of damage done by various "Ubuntu Ubiquity installs" both development and RC level.  Gparted is a lot clearer about what exists and what it is doing.  Ubiquity Install doesn't even show partition labels.

Having been burnt I use Gparted to rationally set up my partitions and then Ubuntu Install for just that and no more.

Jerry

---

### Post by sikander3786 on 2011-08-09
Didn't read the whole thread but guess I want to mention this too.

[http://ubuntu4beginners.blogspot.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html](http://ubuntu4beginners.blogspot.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html)

---

