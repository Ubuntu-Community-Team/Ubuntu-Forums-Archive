---
title: "I think GParted wiped out my FAT, any way to recover?"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by pakopako on 2011-12-07
The MBR seems OK, but I think my file allocation table is gone and I am still a state of panic. For reference, this block quote will detail what has led up to my question.

> To start off, I am using a Toshiba M200 laptop with only one USB port available and a non-powered hub. It has a 32GB SSD drive divided up into smaller partitions.

The main partition at the start of the drive is 14 GB NTFS with Windows XP SP3, the remaining 18GB was put into an extended partition with two logical partitions (10GB and 7.5 GB) inside (both NTFS). After the extended partition was about 6 megabytes of empty space.

I installed WUBI Ubuntu (5GB) on the smallest logical partition and tried moving it to my USB drive [according to this site]("http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/"). Technically it worked. If I used the USB drive on a machine that supported USB drive boots it would boot into the Ubuntu WUBI. Unfortunately my laptop, as I found out recently and have [some corroboration]("http://ashleyangell.com/2011/06/how-to-boot-toshiba-portege-m200-off-sd-memory-card/").

I could still bootleg a USB WUBI install from my laptop... but there would have to be an ubuntu folder with root.disk et al somewhere on my HDD. I found out if I moved the ubuntu folder from my 7.5 GB partition to my 10 GB partition, I would have a totally empty 7.5GB partition to do [bcbc's WUBI-to-full port]("http://ubuntuforums.org/showthread.php?t=1519354").

So I installed GParted and saw how my drives were laid out. I saw the 14GB NTFS partition, the extended partition with the two logical partitions inside, and 6MB of space at the end. I decided to maximize the extended partition to include the extra space, merged that empty space with my 7.5GB partition, and turn it into a 7 GB ext4 with a 256MB swap partition. The end result looked like 14GB + extended (10GB + 7GB + 256MB)Unfortunately I cannot access my HDD anymore. Upon boot, I am offered the OS choices menu; if I choose Windows, I get sent to the Safe Mode Choices menu. Any choice causes a reboot, but I choose "Safe Mode", for a second, I see a blue-screen pop up asking among other things *"Check to make sure any new hardware or software is properly installed"*. The good news is, if my USBuntu drive is attached, it can still log into that somehow.

Ubuntu 11.04's disk utility sees that the HDD is... messed up. The HDD still begins with a 14GB NTFS partition, but then has a 1.1 TB extended partition (including 10GB NTFS, 7.3GB unknown/empty, and 1.0 TB free) followed by a free space... of 18446743 TB (-1,049,456,572,928 bytes)

GParted still sees the HDD as 29.84GB of unallocated space. The information option gives me a  (!) warning that I can't have a partition outside the disk. I can't mount/unmount .... wait. I was using Disk Utility and said something about a daemon issue so I couldn't mount my 14 or 10 GB partitions, but now I can. I can see what's inside, but I'm hesitant to reboot.

Is there any way to salvage this situation without formatting the entire drive? (I do have a two-year-old drive image I'd rather not drag out.) I am thrilled I can still boot into Ubuntu with what seems like full functionality I do have a DVD drive I can attach to the M200 that supports disc-booting (with lots of blank DVDs but no CDRs), but when I tried using a WinXP Recovery Disk... it just hangs (probably can't find the FAT XP is on). The GParted recover CD was about as useful as Ubuntu's GParted; it had an option to search for a File-allocation table to recover (instead of just creating a new one), but couldn't find any.

Thanks for reading about my problems. Appreciate any input. And apologies if for not knowing how this topic should be categorized as.

---

### Post by oldfred on 2011-12-07
Both Windows & Testdisk have been know to write a bad partition table that has the end beyond the end of the drive. Then nothing works as most booting has to read partition table.

Post this and do a backup of the partition table just incase.

sudo fdisk -lu

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Sometimes you can just use the sfdisk or fdisk to rewrite partition table and it is smart enough to know the last entry cannot be beyond the end of the drive.

Often this tool is easier to use.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by pakopako on 2011-12-08
High fives and hugs all around. Thank you for getting my partitions working again!
:popcorn: (I'd send a card, but mine are either [horrible]("http://theoatmeal.com/horrible") or [just]("http://www.someecards.com/usercards/viewcard/MjAxMS1lMTMxMGU4NmZhMGQ5YjJj") [inappropirate]("http://www.someecards.com/usercards/viewcard/MjAxMS03Yjk3OTE0MWQzOThhNzA0").)

A small curiosity did pop up: WinXP DiskPart has no problems reading the drives, but an old copy of PQ Magic 5.0 (I still have Win9x habits) says there is some sort of LBA and C/H/S mismatch (LBA is about 27.6 * 10^6 while CHS is 16.4 * 10^6). GParted and Disk Utility in Ubuntu have no problems; should I be at all concerned what this now-very-outdated software says?

I guess that's the last question before I mark this thread SOLVED (thanks again OldFred; I seriously did not notice Thread Tools would do that if it were not for your sig).

Here's what happened after I tried [FixParts](http://ubuntuforums.org/showthread.php?t=1705325) in case some unlucky soul runs into a similar problem:
> Huh. GParted sees an extra 255 MB of unallocated space after my extended partition for some reason.

I ran "sudo fdisk -lu" and found that sda2 (W95 Ext'd) ends at sector 62,064,639 while the last sector of the disk is 62,586,880 -- gparted isn't allowing me to grow or shrink it, even though it can calibrate the new start/end sectors. The error: "Unable to satisfy all constraints on the partition."

What the... FixParts fixed it (just by recalculating the CHS values), sort of. I can shrink the Ext'd (since it now had empty space where a 2nd logical partition used to be), but can't grow it. I could still use GParted to create Linux partitions (0x83), but they would be unusable (and finalized as Unknown from whatever I wanted them to be). So I created an SDA3 (failed ext4) and SDA4 (failed swap) sections **and left 1 MB at the end of the drive the hell alone** just in case the drive needed space to keep a backup partition table.

Stymied for a bit because Disk Utility couldn't do anything (*error creating partition; daemon is being inhibited ubuntu*) and GParted was still* "unable to satisfy all constraints on the partition"*. Windows offered little comfort; DiskPart and Fdisk could see spaces, but I was too afraid to muck around with non-NTFS partitions. PQ Magic was still citing an LBA/CHS mismatch and crashing because it couldn't assign letters or labels to the partitions.

I went back to FixParts to see if it could access the drive. I managed to change the larger unknown partition label from Linux to NTFS, so that was something. I then went to WinXP and amazingly I saw a drive letter mounted! I couldn't check it, but Windows considered it a RAW volume. A quick "format /fs:NTFS" worked and I could access it. Amazing!

I booted back to Ubuntu and managed to find the last unknown sector had merged with the unallocated space, but GParted was now easily able to carve a swap space out of it. Ubuntu's Disk Utility could as well access the new NTFS partition and reformat into an ext4 (though I still needed to use GParted to turn the label into 0x83 from 0x07 because DiskUtil was hanging when I asked it to do that).

This was all a very long and strange trip, but everything looks OK for my try to migrate this WUBI install to an actual partition using [bcbc's guide]("http://ubuntuforums.org/showthread.php?t=1519354") (I hope it creates a working GRUB2 loader like LVPM promises.. mainly because my curent bootleg WUBI workaround involves ignoring two annoying "no such device/no such disk" errors after selecting to boot into Ubuntu.)

---

### Post by oldfred on 2011-12-08
Modern drives have not used CHS values since they became larger than 8GB. That was when BIOS converted to LBA. 

Even fdisk and some other Linux tools report CHS values and testdisk still uses them(?). I think any error on CHS vs. LBA is due to some sort of rounding issue unless of course all the tools cannot mount a partition/drive. But then I would think it really is LBA & CHS have problems.

---

### Post by pakopako on 2011-12-09
> **oldfred said:**
> Modern drives have not used CHS values since they became larger than 8GB. That was when BIOS converted to LBA. 

Even fdisk and some other Linux tools report CHS values and testdisk still uses them(?). I think any error on CHS vs. LBA is due to some sort of rounding issue unless of course all the tools cannot mount a partition/drive. But then I would think it really is LBA & CHS have problems.
Hm. Well, it is only that one program that has any problems, so most likely it is because the program itself is so old that it does not match up with drives beyond 8GB.

**This thread... IS SOLVED.**

---

