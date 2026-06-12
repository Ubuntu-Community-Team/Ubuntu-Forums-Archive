---
title: "Hard drive clone"
date: 2021-02-12
forum: New to Ubuntu
---

### Post by sdantonio on 2021-02-12
Hi

I finally have my first Ubuntu box set up petty much the way I want it and running my TV and entertainment system.  Can the hard drive be cloned, and if so, can that clone be put into another computer (different manufacturer, different chip set, etc.).  I'm looking to set up another box for the upstairs TV.  I know windows would throw a hissy fit if the clone was mounted into another computer with a completely different chip set.

If this can be done can you recommend some good cloning software?

Thanks 
Steven

---

### Post by TheFu on 2021-02-13
Yes, you can clone it - bit for bit.  Just be certain to never place the same 2 drives back into the same computer.  There will be a conflict with the UUIDs which is likely to mount different partitions than you actually want.

In general, the proprietary GPU drivers or other specialized HW drivers would be the only concerns. Best to disable those before making the clone, unless you have exactly the same GPU in both systems.

You will need to change the hostname and any static IP settings too. There are plenty of guides to do that.

good cloning software? .... there are 10+ of them.  dd is built into every Unix on the planet.  ddrescue is a little nicer.  gddrescue, fsarchiver, clonezilla, partimage, .... all can do it.  I'd use dd or ddrescue.

Oh - and when you are cloning, the source drive cannot be running.  Boot into a Try Ubuntu / Live Desktop environment, install whatever cloning tool you like, then make the clone.  I can't say this clearly enough.  Be 100% certain you get the order of the parameters correct when using any of these tools.  With them, you can either 
a) clone the drive A --> B, getting exactly what you want
or
b) clone the drive B --> A, wiping everything off A with little chance to recover any data.

If you don't fully understand the difference between drive devices and partition devices - STOP!  Go learn.  Understand. Do this first.  It is very, very, very, common for people to get these things wrong and wipe their drive(s).

When cloning HDDs, the target must be at least the same size as the source. If you need to go smaller, it becomes a little more complex.  fsachiver works on the partition level, not the whole drive level, so it can restore to a smaller partition, if the actual amount of data will fit.

After you do the clone, it would be really smart to force some new UUIDs to be created for every partition, then update the fstab file to use those new UUIDs for that disk. Don't touch the fstab for the original disk.  None of this is hard, assuming you have the understand for the terms and what goes where.

Ok ... so let's show an example. Boot into a _Try Ubuntu_ flash drive environment. Login. Open a terminal.

```
# install ddrescue
sudo apt install ddrescue
```
Installed programs in these *Try Ubuntu* environments are for that boot only. If you reboot and need to do it again, you'll need to reinstall.
The manpage for ddrescue says:
```
SYNOPSIS
       ddrescue [options] infile outfile [mapfile] 
```
so the source (infile) is first and the target (outfile) is 2nd.  You may have heard that on Unix systems, everything is a file. We are going to take advantage of that.  Let's change our directory to the place where HDD and partition device files are and look at the available devices:
```
cd /dev/
ls sd*
```
You should see at least 3 devices
[LIST=1]
[*]The Try Ubuntu Flash drive
[*]The source drive
[*]The target drive
[/LIST]

When I run 
```
$ ls sd*
sda  sda1  sdb  sdb1  sdb2  sdb5
```
So there are 2 drives connected.  
[LIST]
[*]sda
[*]sdb
[/LIST]

**sda1** is the first partition on the drive, sda.
**sdb1** is the first partition on the drive, sd**b**.
**sdb2** is the 2nd partition on the drive, sd**b**.
sdb5 is the first, Logical Partition on the drive, sdb.  If you don't understand this and need to, then read the wikipedia article. Logical Partitions are a hack due to the IBM/Microsoft hacks to get around the MSDOS 4 partition limit.  Today, we have GPT partition tables which don't need these hacks.  Alas ... the Ubuntu installer at the time this system was installed decided the drive couldn't be GPT and forced the MSDOS partition table onto it.

Anyway ... these "devices" are just files full of bits.  We can clone them.  Or we can clone an entire partition. It is up to us.
Now, on my system, sdb is where the OS is, but that is fairly odd.  Also, the order of the device files (sda or sdb) can change from reboot to reboot, so **always** check which drive is which after each reboot.  This is why Linux uses UUIDs to mount storage and not partition device files anymore.
Let's assume 
* sda is the source (YOU need to be 100% positive about this!)
* sdb is the target  (YOU need to be 100% positive about this!)
* sdc is the Try Ubuntu Flash drive  (YOU need to be 100% positive about this!)
Then this command:
```
sudo ddrescue /dev/sda    /dev/sdb  /tmp/log
```
will clone everything on sda to sdb.  The *--force* option may be required. Place it just after the ddrescue command.  It gets the partition table, all partitions, and will take a few hours - to a few days depending on the size of the whole drive.  It doesn't know anything about data. It doesn't care.  It is just copying bytes from A --> B. Nothing else.  If you get the device wrong on your system, it will be a very, very, very, bad day.  EVERYTHING on sdb will be wiped/replaced. No need to format, create partitions in advance. Those won't matter.

"sd" devices are for SCSI or SCSI-emulated storage.  That is all SATA, eSATA, and most USB devices.  However, NVMe drives have different names and conventions. The naming for NVMe drives is different and more complex. If you don't 100% positively know the whole drive vs the partition names, STOP.  It will not be a good day if you get those wrong.

There is 1 other thing.  Sector sizes.  If the source and target storage devices don't have the same sector sized (that's a physical thing), then terrible performance can happen.  There are 2 different sector sizes, generally based on the total size of the storage device.  Smaller drives use 512b sectors and large drives use 4K sectors.  1 sector is the smallest amount of storage that a 1 byte file will use.  So, if we have 1 byte in a file on a 512b/sector disk, then 512b will be used.  But on a 4K/sector disk, that same 1 byte will use 4K of storage.  This is one of the reasons that using huge HDDs for the OS, which has thousands of tiny files, is to be avoided.

Hope this is all clear enough and good luck.

---

### Post by oldfred on 2021-02-13
The other option is to do a new install & restore from your backup.
Your backup should be complete, so you can easily restore your entire system when your hard drive fails or other major issue.
Then you also know your backup is complete as you still have your install to go back & find anything missing.

Typical desktop needs /home (user settings), your data if not in /home, maybe some settings in /etc, but those could be unique to your one system, and a list of installed apps. If a server, you probably will have folders in / (root) that have settings for server apps. Those also have to then be part of your backup. 

I do not backup Ubuntu as it is easily reinstalled.

---

### Post by sdantonio on 2021-02-13
Wow, Thank you both.  It looks like it will end up being easier than I thought.

---

### Post by TheFu on 2021-02-13
I'm usually the one suggesting that people use their normal recovery process. When will you have a better opportunity and not be freaking out about data loss?  

I don't do imaged based backups and basically do what oldfred suggested above. I keep between 90 days - 180 days of daily, versioned, backups for each system. Storage needed is 10-30% more than the first mirror copy. Bargain! Takes 2-8 minutes for each new version to complete. Fast, efficient, easy to restore.

Image backups aren't efficient at all, they are slow, and require inconvenient downtime.  There must be 200 threads here about doing backups and 50 treads about restoring them.

---

### Post by C.S.Cameron on 2021-02-13
**User's Desktop Ubuntu to Bootable USB, BIOS or UEFI**

TheFu has posted some excellent advice above, Here is a method to create an image of your Ubuntu system that can be flashed to either Legacy or UEFI computers.

**This is another mkusb hacking project**

- Create a Live USB drive using USB tool of your choice. Mkusb works.

- Create a Persistent USB drive using mkusb with defaults. USB drive should be at least as large as your Ubuntu root partition.

- Boot the computer using a Live USB.

- Plug in Persistent USB target drive.

- Open GParted and delete all partitions except sdx2 and sdx3 on the target drive.

- Right click and copy the root partition from the internal drive, 

- Right click the unallocated space on the target drive and select "Paste".

- If there is a /home partition copy it as well. Do not include any boot or EFI partitions.

- Overwrite /dev/**sdx3**/boot/grub/grub.cfg with /dev/**sdxy**/boot/grub/grub.cfg.

Where sdx3 is your target drive EFI partition and sdxy is your internal drive root partition.

- Use Gnome-Disks to make an image of the target USB, truncate and compress the image to save space as required.

- You can use mkusb, Disks, Etcher or dd to flash the image to a new drive in Ubuntu or use Rufus or Etcher in Windows.

---

### Post by rsteinmetz70112 on 2021-02-15
Just a little clarification. A comment above showed installing a package called "ddrescue". There isn't a package called "ddrescue" in the standard Ubuntu repositories. The package is called "gddrescue" but the executable is called "ddrescue".
```
$sudo apt install gddrescue
$sudo ddrescue /dev/sda    /dev/sdb  /root/sda.log
```
It is also possible to create an image of the drive using ddrescue and then use the image to clone a drive.
```
$sudo ddrescue /dev/sda /root/sda.img /root/recovery.log
$sudo ddrescue -f /root/sda.img /dev/sdb /root/restore.log
```

---

