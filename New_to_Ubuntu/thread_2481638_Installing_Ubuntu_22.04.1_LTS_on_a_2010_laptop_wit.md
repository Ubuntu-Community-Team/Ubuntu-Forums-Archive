---
title: "Installing Ubuntu 22.04.1 LTS on a 2010 laptop without GPT support"
date: 2022-12-05
forum: New to Ubuntu
---

### Post by yorublaireau on 2022-12-05
Hi,

I have an old laptop lying around and I decided to format it and install Linux on it, so I could use it as a home server. As I'm pretty new to linux in a non-professional situation, I decided to go for Ubuntu because it is popular so that help is easily accessible.
If only I knew what I was getting into...

This laptop is pretty old, it's a Dell XPS L502X from 2010-11. It came with Windows 7 and I was pretty happy with it. I played around with it, installed Ubuntu & GRUB back in 2012, and it worked fine for a time. I left the laptop in storage for a few years, so it's not seen any recent use.

So when it came to install Ubuntu now, I installed the Ubuntu ISO on a USB key with Rufus and loaded it up on the laptop. I picked to format disk & install automatically. Once that was done, I removed the USB key and booted, and got the error `Operating System Not Found`. That's when the problem started.

Basically, I've tried many things
- [boot repair disk]("https://sourceforge.net/p/boot-repair-cd/home/Home/")
- ubuntu live usb with GPT partition scheme (usb doesn't boot)
- ubuntu live usb with MBR partition scheme (can install but ubuntu doesn't boot)
- ubuntu live usb with "Fix for old bios" option from Rufus (can install but ubuntu doesn't boot)
- ubuntu mate live usb, trying a different distro (can install but ubuntu doesn't boot)
- letting the live usb format the disk (can install but ubuntu doesn't boot)
- formatting the disk manually with msdos partition table following [this guide]("https://linuxbsdos.com/2015/10/30/gpt-and-mbr-manual-disk-partitioning-guide-for-ubuntu-15-10/") (can install but ubuntu doesn't boot)
- reinstalling grub manually

And what I've gathered is the following (but happy to be proven wrong):
- My laptop is old and doesn't seem to support EFI / GPT partition scheme
- boot repair disk is convinced I need to use GPT partition scheme, and is therefore unhelpful (the `MBR options` tab is greyed out)
- I think I need to set particular flags on the partitions but I can't figure out what they are?
- Sometimes I manage to get my system in a state that means I can't boot from the Ubuntu Live USB, but I can from the boot repair disk usb. Only way I found to fix this it to reinstall windows 10 via their install USB, and then I can boot from the Ubuntu Live USB - It's probably not relevant but I thought I'd mention it just in case
 - When using the GPT partition scheme, nothing seem to boot on my laptop (


Last actions I've taken:
- Install windows and let it handle all of the partitioning (that's my "clean slate" reset)
- Use boot repair disk to export the following logs: [https://paste.ubuntu.com/p/6c5Rmf37zN/](https://paste.ubuntu.com/p/6c5Rmf37zN/) (not what I want but it's a working setup on this hardware)
- Use Ubuntu live usb to install Ubuntu with "Erase Disk and install Ubuntu" option
- Use boot repair disk to export the following logs: [https://paste.ubuntu.com/p/6gmjGhwq7m/](https://paste.ubuntu.com/p/6gmjGhwq7m/)
 - Last thing boot repair disk tells me to do: To disable BIOS-compatibility in the UEFI (I don't have this)


I've spend a couple dozen hours on this problem, so I'm now turning to the ubuntu forums for some expert help. I'm not interested in dual-boot with windows, I only used Windows install because I ran out of ideas to fix my system.

Here's a few pictures of my BIOS to show all of the settings available:

And here's a picture of an occasional thing I get when booting the laptop - it flashes really quickly. I don't know if it's relevant but I thought I'd include it just in case.

As a note: I've checked out a few other threads on this forum but I couldn't find any actual information on how to resolve my specific issue

---

### Post by grahammechanical on 2022-12-05
> My laptop is old and doesn't seem to support EFI / GPT partition scheme

I do not think that statement is true. I have installed Ubuntu on a hard disk with GPT partitioning and with a motherboard that had BIOS and not UEFI. In fact I used to have a machine with one version of Ubuntu running on a hard disk with MBR partitioning and another version of Ubuntu running on a drive with GPT partitioning. 

You do not show us the Boot menu of the Motherboard settings utility. I suspect that is where you will find options to load an OS in either UEFI mode or BIOS/Legacy/CSM mode.

Also, your INTEL i5 CPU is much more powerful than my Intel dual core CPU. Please supply any system messages that you get when "Ubuntu does not boot."

Regards

---

### Post by yorublaireau on 2022-12-05
Thanks for your help.

I have sent everything in the BIOS through my screenshots, there is absolutely no options about UEFI, Legacy, Secure boot or CSM.
Added to that, it seems that no live usb I created with Rufus with the "GPT Partition Scheme" will boot on my laptop, it just doesn't get recognised in the boot order list.
These 2 things are why I believe this laptop doesn't support EFI/GPT.
Also looking at [this link]("https://www.dell.com/community/Laptops-General-Read-Only/XPS-15-L502X-Any-future-update-supporting-UEFI-is-possible/td-p/4577175") and [this link]("https://www.dell.com/community/Laptops-General-Read-Only/XPS-L502X-Latest-BIOS/td-p/3988885"), it seems that everyone has the same problem.

When I say "Ubuntu does not boot" I mean the same as my original error: I just get a black screen with "Operating System Not Found" on it.

---

### Post by #&amp;thj^% on 2022-12-05
Right now as I've been running a development version On Ubuntu for a a couple of weeks, and I find a root_linux_zfs, is a very buggy set-up. ATM
I've now lost 2 test beds with a similar setup IE: "ZFS Root" with just a blinking cursor, where my Display Manager or Login screen would normally show.
I'm working very hard to triage this matter, but sadly I've not found a work-around or fix just yet.
BTW You show you have a efi boot, @
```
 # /boot/efi was on /dev/sda2 during installation
UUID=E068-B756  /boot/efi       vfat    umask=0077      0       1
```

---

### Post by tea for one on 2022-12-05
Try this:-
Boot into a live session in legacy mode.
Open Gparted and create a msdos partition table.
Then make _one_ Ext4 partition.
Open the installer and install to your previously created partition.
(i.e. do not let the installer "Erase Disk and Install")
If you see a message/warning about ESP missing, ignore it and continue the installation.

It may work, it may not................?

Finally, given the age of your PC, perhaps Lubuntu or Xubuntu may be worth a shot.
(Lubuntu uses a different installer)

---

### Post by yorublaireau on 2022-12-05
> **1fallen said:**
> 
BTW You show you have a efi boot, @
```
 # /boot/efi was on /dev/sda2 during installation
UUID=E068-B756  /boot/efi       vfat    umask=0077      0       1
```
My understanding is that it was created by the Ubuntu installer. I can't boot from it (OS not found error) so I don't consider that to be meaningful? Unless I'm misreading the BootInfo dump.

I'm starting to suspect that the Ubuntu installer only supports GPT partition scheme, which would prevent it from installing on my system.

---

### Post by yorublaireau on 2022-12-05
> **tea for one said:**
> Try this:-
Boot into a live session in legacy mode.
Open Gparted and create a msdos partition table.
Then make _one_ Ext4 partition.
Open the installer and install to your previously created partition.
(i.e. do not let the installer "Erase Disk and Install")
If you see a message/warning about ESP missing, ignore it and continue the installation.

It may work, it may not................?
I've tried this but I don't get the option. Here's what I created in gparted and the install menu:

And if I try to pick "Something else" and create a single partition there, I get the following error:

> **tea for one said:**
> 
Finally, given the age of your PC, perhaps Lubuntu or Xubuntu may be worth a shot.
(Lubuntu uses a different installer)
I'll look into those!

---

### Post by TheFu on 2022-12-05
If rufus doesn't work, try a different tool. Etcher is one.*I use 'cp' myself, but it can be dangerous if you don't know Linux device names.  mkusb is another.  Any program that can accurately move bits from A ---> B without molesting those bits can be used. On Unix-like systems, there must be 10+ built-in, commonly used tools that will do the job.

Often, too much Windows background is a hindrance for getting any Linux to work. Things that are mandated by MSFT aren't usually mandated under Linux.  I too have installed legacy boot (not-UEFI) onto GPT disks since around 2011-ish.  The mandate that GPT must use UEFI booting is only for MSFT.  Since around 2015, using GPT for all partitioning has been my rule, regardless of legacy or UEFI booting.  

MSFT said that all 64-bit OSes had to use UEFI booting. That's a MSFT-only thing, I can promise you.

GPT doesn't care about the BIOS at all. GPT support has been in all Linux systems since, perhaps, 2008, maybe earlier.

If a specific flash drive doesn't work to boot, try another flash device.  I wish there was a specific flash drive that always works, but that isn't reality.  I've had high end, branded flash drives work and fail in different computers over the last 15+ yrs. I've also had no-name flash drives work and fail during that time.  Every computer model seems to be different. Each can have a different USB controller, different firmware, and hence, different boot compatibility.  USB2 tends to boot easier than USB3.  On laptops, sometimes the left  or right or rear USB ports have different controllers - try them each.

If the system has limited BIOS screens, then it might be an enterprise variant model which has hardcoded some very important BIOS settings that need to be tweaked for any non-MSFT OS to be installed.  Without those tweaks, it ain't gonna happen.  I've never seen this on Dell laptops, but I have on HP and Acer and some of MSFT's Surface tablets running with locked down boot controls.  I'd guess it is only 10% likely you have this in a Dell.  There are a few people here with Dell repair certifications. They'd know more, if they see this thread.  The title won't likely grab the attention - no "Dell {model}" in it. 

I'd also suggest trying a different flavor and version of Linux.  I'd try Xubuntu 20.04 and see if that doesn't work.  That will get you support until Apr-June 2023, which should be enough time to learn more about your hardware and perhaps do a 22.04 upgrade after becoming more familiar with Linux.

Life can be tough when only 5% of the end-users run an OS as compared to the other 85% using that "other" OS.  Of course, we want you to be successful running Linux on your hardware.  I have a Dell 1558 Core i5-2xxx from around 2010. It booted an Ubuntu flavor for a few years, long ago, but got Windows on it and hasn't been booted since, perhaps Feb.  I consider it an emergency Windows system ... if I need to use a specific all-in-one device here.

Sorry, I'm short on installation ideas.  I used to host Linux InstallFests at a local university each semester, but they built up internal expertise and didn't need outside help anymore about 5 yrs ago.  That was an excellent way to see all sorts of different computers each semester trying to get Linux working. Of about 50 systems, 1-2 would be difficult to install.  Plus, having 10 grey-beard experts in the room really would speed up help and solutions.  Only once did we fail to get Linux installed and that system was bleeding, bleeding, edge - released a few weeks before the installfest.  There were no drivers for the new disk controller it included or the NICs or the hot GPU ... it was ugly.  OTOH, he was able to run a "Live Boot" Try Ubuntu environment off a flash drive, but the graphics was low-end and there wasn't any sound possible.  Bleeding edge stuff at that time. Clearly, you don't have that issue.

---

### Post by tea for one on 2022-12-05
I don't think that you are using Gparted and the installer correctly.
Gparted > Device > Create Partition Table > Select msdos.

After you have created one partition, select that partition as root (i.e.system)
You haven't defined the partition as root, hence the message in your screenshot.

---

### Post by #&amp;thj^% on 2022-12-05
> **tea for one said:**
> I don't think that you are using Gparted and the installer correctly.
Gparted > Device Create Partition Table > Select msdos.

After you have created one partition, select that partition as root (i.e.system)
You haven't defined the partition as root, hence the message in your last screenshot.
+1
You have a good handle on this. ;)

---

### Post by tea for one on 2022-12-05
> **1fallen said:**
> +1
You have a good handle on this. ;)
Thank you - your support is appreciated.

---

### Post by yorublaireau on 2022-12-05
> **tea for one said:**
> I don't think that you are using Gparted and the installer correctly.
Gparted > Device > Create Partition Table > Select msdos.

After you have created one partition, select that partition as root (i.e.system)
You haven't defined the partition as root, hence the message in your screenshot.


Sorry, handling partitions manually isn't my cup of tea. I understand creating the Partition table with type msdos, but then I'm not sure how to "select that partition as root".

---

### Post by tea for one on 2022-12-05
Right click partition > Change Mountpoint > Select symbol for root / (forward slash)
Scroll down to Method 3 in this link [https://www.itechguides.com/no-root-file-system-is-defined/](https://www.itechguides.com/no-root-file-system-is-defined/)

Also, please install bootloader to sda not sda1.

---

### Post by TheFu on 2022-12-05
I figured this was as good a place as any to spell out device names in Linux Storage:
A few Linux Storage Devices
```
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda5
```
"sd" - says which type of device is might be.  "sd" is used for SATA, eSATA, and SCSI.  Can be "hd" for old IDE or "md" for SW-RAID, and there are others.

"a", as in "sda" means it is the first SATA/eSATA/SCSI device found at this boot.  "sda" is the device for the entire HDD.   The name can change if there are multiple devices connected and they are discovered in different order for all sorts of reasons.  sdb, sdc, sdd, sde, sdf, ..... sdz ... would be additional drives.  Whole drives is where we want the partition table to be written. Never data.

"1", as in sda**1** ... means it is the first, primary partition created. Numeric order doesn't mean the order of layout on the disk. It is possible to place a partition anywhere on the drive. It is purely the order created.  Partitions are where we place file systems like ext4, xfs, fat32, exFAT, zfs, btrfs, or non-file system volumes like encryption containers or LVM2 physical volumes.

"2", as in sda**2** ... means it is the 2nd primary partition created.

"3", as in sda**3** ... means it is the 3rd primary partition created.

"5", as in sda**5** ... can be either a primary partition, if the partition table is a GPT/GUID Partition Table  OR ... more likely, the first "Logical Partition"  if the partition table is the older MSDOS/MBR type of partition table.

Again, partitions are were file systems are formatted and data, OSes, etc, must have a file system to store data.

So, never create a file system on "sda", always use a partition, which ends with a number.

Drive device names "a", "b", "c", are luck/chance and can change from boot to boot. This is why when we mount file systems in the /etc/fstab that we use UUIDs or LABELs, not device names.  If the device name can change, that would be foolish, right?

To see the mapping between the current boot device names and the UUID, the 'blkid' command exists.

Those are the main rules of drives and partitions and apply to simple partitions. Be aware that there are volume management tools which are governed by some of these rules, but not all of them.  Volumes managed by ZFS, BTRFS, and LVM2 need to be handled differently, but they are placed into paritions. It is just that they have added flexibility and complexity to do some other amazing things that are beyond this thread.

If you see /dev/sdc2, what does that tell you?  It tells me that the 3rd disk found at boot (or after boot if hotswap connections are allowed) and the 2nd partition exists.  I don't know which file system, if any, is on it.

If you have NVMe SSD drives, you'll see they don't use "sd" drivers. But there is still the "whole drive" device and each partition gets a number at the end, just like for "sd" devices. A few examples:
```
  /dev/nvme0n1
  /dev/nvme0n1p1
  /dev/nvme0n1p2
```
Which is the whole drive and which are the partition devices?

BTW, the order the partitions are created doesn't matter for which file system must go there. The main choice about that is faster access to data, which I haven't worried about in over a decade.  I don't recall which is faster, inner or outer data. At this point, Don't know that it matters.  On SATA-SSD and NVMe SSDs, there isn't any inner or outer spinning, so it doesn't matter.

Remember always that almost everything on Unix-like OSes are files.  That includes the partition, the whole disk, most devices have files for the OS to interact through.  It is a simple, but elegant solution for many things.  Understanding the idea that to access devices or to get information from those devices, we just need to read or write to a specific device file.  So, the mouse, keyboard, monitor, GPU, microphone, speakers ... those are all "files" in a simplistic way.  Actually, for the audio stuff, we deal with the audio card and it handles where the audio gets output, but the idea that everything is a file still helps with understanding.  There's 1 thing that isn't a file.  That is processes.  So, everything that isn't a process **is** a file.  With that low-level knowledge, you can understand Unix-like systems much better and make them bend to your will.

It also shows why learning, understanding and using file permissions are so important.  File permissions apply to devices too!

Anyway, hope this helps someone.

---

### Post by yorublaireau on 2022-12-06
> **tea for one said:**
> Right click partition > Change Mountpoint > Select symbol for root / (forward slash)
Scroll down to Method 3 in this link [https://www.itechguides.com/no-root-file-system-is-defined/](https://www.itechguides.com/no-root-file-system-is-defined/)

Also, please install bootloader to sda not sda1.

I've done that and it didn't boot - I just got a black screen with a cursor. However I tried running Boot Repair Disk, and it reinstalled Grub. After that, I could boot on the installed Ubuntu!

Now I'm trying to reinstall it properly with the right partitions but at least I got something working, which can be my base for future experiments.

I'm gonna try a few other things but hopefully I can sort myself out from here on out. Thanks for your help &#10024;

> **TheFu said:**
> Anyway, hope this helps someone.

Yeah thanks that was really useful.

---

### Post by tea for one on 2022-12-06
> **yorublaireau said:**
> I've done that and it didn't boot - I just got a black screen with a cursor. However I tried running Boot Repair Disk, and it reinstalled Grub. After that, I could boot on the installed Ubuntu!
That's good news.
In order to help other forum members/searchers, it is a nice gesture to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by yorublaireau on 2022-12-06
> **tea for one said:**
> That's good news.
In order to help other forum members/searchers, it is a nice gesture to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Will do! I just have some more questions:

To create my partitions manually, I was following this guide: [https://linuxbsdos.com/2015/10/30/gpt-and-mbr-manual-disk-partitioning-guide-for-ubuntu-15-10/](https://linuxbsdos.com/2015/10/30/gpt-and-mbr-manual-disk-partitioning-guide-for-ubuntu-15-10/) with the MBR instructions
And more specifically, trying to recreate this: 
[IMG]http://linuxbsdos.com/wp-content/uploads/2015/10/manual-partition-ubuntu-8-700x389.png[/IMG]

After your suggestion and installing on a single partition, I tried a few combination of the above.

It looks like it worked when I removed the `swap` partition, but I don't understand why it would cause my entire system to fail to boot. Do you have any idea why?

Thanks again for your help!

---

### Post by tea for one on 2022-12-06
I suspect that the separate boot partition was not configured perfectly.
Also, it is an unnecessary complication to boot one OS.
Separate boot partitions are nowadays used for encrypted systems.
Swap partitions have now been replaced by swapfiles in recent Ubuntu systems.

As you are experimenting with your Dell XPS L502X (from 2010-11), I think it would be better to start a new thread for future questions.

---

### Post by TheFu on 2022-12-06
> **yorublaireau said:**
>  
And more specifically, trying to recreate this: 
[IMG]http://linuxbsdos.com/wp-content/uploads/2015/10/manual-partition-ubuntu-8-700x389.png[/IMG]

After your suggestion and installing on a single partition, I tried a few combination of the above.

It looks like it worked when I removed the `swap` partition, but I don't understand why it would cause my entire system to fail to boot. Do you have any idea why?
 
In 2022, please don't use MBR, use GPT.  There are many reasons and you'll likely run into issues later by using MBR when it adds complexity that is trivially avoided by using GPT instead.  
sda5 - sda99 in the MBR world are all Logical Partitions and every logical partition must exist inside an "Extended Primary Partition".  When changing sizes of partitions later (nobody will get their partition sizes and locations correct), the extended partition can't be modified as long as there are any Logical partitions inside it.  It is a pain.  With GPT, all partitions are primary. None are contained.  There is effectively no limit on the number of primary partitions under GPT.  It also has ZERO impact on booting or other aspects of running the system, besides being easier to modify later.  To make expansion easier later, it would be smart to leave some empty space between (to the right) the partitions to they can be enlarged without moving data.  Shifting data left is extremely intensive and risky. If there is empty, unused, space to the right of a partition, increasing the size will let you take a few seconds in gparted and a reboot to address the issue as a quick fix. You'll know to go clean up some junk or to order more storage - depends on your needs/wants/budget.

Have you looked current partition suggestions in these forums?
Is there a reason you don't just let the defaults be used from the installer?  Then you'd see the minimal setup. BTW, each installer for each release is a little different and does slightly different things for partitioning.  I'm a little picky and setup my partitions to make backups easiest.  For me, storage layout is about
performance, flexibility, backups, restores, and security.  

A layout only:
[Https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](Https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)

A layout with reasons why:
[Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

Here's an install I did from a few months ago:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root--00                   ext4   35G   11G   23G  32% /
/dev/nvme0n1p2                              ext4  574M  272M  260M  52% /boot
/dev/nvme0n1p1                              vfat   50M  5.2M   45M  11% /boot/efi
/dev/mapper/vg00-home                       ext4   26G  9.9G   15G  41% /home
/dev/mapper/vg00-var                        ext4   35G   26G  7.0G  79% /var
```
Think of the lines with /dev/mapper/ as separate partitions. They are LVM2-logical volumes and extremely flexible in ways that regular partitions cannot touch.  My /var/ area is larger than most people would need because some toy virtual machines and linux containers end up in that area.  If you don't use those things, 10G would be overkill ... or it should be.  Also, I have a 4.1G swap LV that doesn't show up in that list of mounts.  

I've simplified the stuff above down to just the OS "partitions".  The computer has over 40TB of storage connected, but most of that is data and backups. They don't matter for booting.

The 50M for the efi fat32 partition is needed here.  Because I use LVM2 for storage volume management, I need /boot to be separate.  I'd like for /boot to be ext2, not ext4, but the 20.04 installer didn't like that choice for some, unknown, reason.

Anyway, you're disk layout should be for your needs and you should expect to guess wrong. We all do. Everyone.

Can't remember if I said this, but don't feel like you need to allocate all the storage inside the drive, especially if it is an SSD.  For SSDs, leaving 20% unused should drastically improve the lifespan of the drive.  Having all partitions use all the space available also means less flexibility for your incorrect choices.  Leave some space to the right of each partition as a buffer to allow expansion and a warning when it is full that gives you some time to get more storage or to clean up some junk.

20G for the OS (/) isn't enough these days. You'll likely need 35G there.

250MB for /boot  isn't enough either. You'll run into patching failures because that really needs to be large enough to hold 6 full kernels and support images. The newer you are at Linux, the more likely you'll need more space - make it 700MB as the minimal size. Even then, you'll need to purge old kernels monthly. And when you switch to the HWE kernels, you'll have to manually remove the non-HWE kernels to prevent filling /boot/ and ending up in a terrible situation where patching the system isn't possible.

Swap for a desktop, should be 4.1G in size. There are reasons. Go and read the swap thread for why.

---

### Post by yorublaireau on 2022-12-06
> **tea for one said:**
> I suspect that the separate boot partition was not configured perfectly.
Also, it is an unnecessary complication to boot one OS.
Separate boot partitions are nowadays used for encrypted systems.
Swap partitions have now been replaced by swapfiles in recent Ubuntu systems.

As you are experimenting with your Dell XPS L502X (from 2010-11), I think it would be better to start a new thread for future questions.
Will do if I encounter more issues.

> **TheFu said:**
> In 2022, please don't use MBR, use GPT. 
That's what you keep telling me, but as I explained at the start, my laptop doesn't seem to be supporting GPT. I've tried letting the installer create the partitions, I've tried manually creating the partitions with a GPT partition scheme, I've tried changing the partition scheme on the Live USB that Rufus creates. Nothing worked. Every time I get "Operating System Not Found".

Unless someone can prove to me that my laptop supports GPT without 20h of trial and errors, I'm gonna keep using MBR, as it's working.
(I don't mean to sounds rude, I'm just tired of this and want a working laptop &#129315;)

> **TheFu said:**
> Can't remember if I said this, but don't feel like you need to allocate all the storage inside the drive, especially if it is an SSD. For SSDs, leaving 20% unused should drastically improve the lifespan of the drive. Having all partitions use all the space available also means less flexibility for your incorrect choices. Leave some space to the right of each partition as a buffer to allow expansion and a warning when it is full that gives you some time to get more storage or to clean up some junk. 
Yeah I had the same idea for my latest installs, and that's much easier to create extra stuff if I need!

Thanks for your help and explanations, they are much appreciated!

---

### Post by oldfred on 2022-12-06
Only place for MBR(msdos) is if installing Windows in BIOS mode on old system. And newer Windows does not really work well with old systems.
Ubuntu also now is a heavier system. I use Kubuntu which is more mid-weight but even worked on my 2006 laptop. Functional but not speedy. Most older systems need a lighter weight flavor.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I have used gpt since 2010 on all new drives including larger flash drives. Then my system was BIOS only. 
While UEFI is normally used with gpt partitioning, Linux can use gpt with BIOS.
But if booting in BIOS mode with gpt, you do need one additional partition, bios_grub.
Create a tiny 1 or 2MB unformatted partition with bios_grub flag (if using gparted). 

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

---

