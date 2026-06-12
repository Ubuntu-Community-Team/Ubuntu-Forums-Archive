---
title: "Partition Size, using dd and options afterwords"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2014-03-21
I have a new Western Digital model [WDBH2D0010HNC-NRSN]("http://ubuntuforums.org/showthread.php?t=2203910") hard disk drive. That's a 1 terabyte drive. My current, in use, desktop drive is 400gig.

```
mark@Lexington:~$ sudo fdisk -l
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2       765798398   781422591     7812097    5  Extended
/dev/sda3        39063552   765796351   363366400   83  Linux
/dev/sda5       765798400   781422591     7812096   82  Linux swap / Solaris
```


I want to use the command line command "dd" to transfer ALL of what is on the 400 gig to the 1 terabyte drive.

One - is this the correct use of dd for my purpose? And please note, no sudo argument

dd if=/dev/sda of /dev/sdb

where **sda** is the 400gig drive with folders, files, objects and **sdb** is the new, essentially empty, drive.

Two - what formatting is necessary for ext4? Rounded to cylinders should NOT be checked using GParted? Or by using dd I don't have to format to ext4 first? 

Three - the transfer must be done in LiveCD (or LiveUSB) session? Or can the /sda be mounted and the /sdb be unmounted?

After the transfer is completed should I resize the / and /home and 'swap'? I'm mostly considering enlarging the / as it is about 20 gig. I am thinking to make it 40 gig. Maybe that's overkill. Opinions?

I have backed up all of /home, that the default Ubuntu backup software, named: Backup, can do. Whenever it does a backup, Backup puts a message on-screen about not backing up a few items. I believe this is harmless, as it cannot backup the directory or file .gvfs and the like. Here is today's message: 

```
/home/mark/.speech-dispatcher/log/ibmtts.log
/home/mark/.speech-dispatcher/pid/speech-dispatcher.pid
```

Thank you for your time and all ideas considered.

---

### Post by mansonfan78 on 2014-03-21
As far as partition sizes are concerned 20 gb is more than enough for / (I only have a 15 gb partition for it), swap should be the same size (or slightly larger) as your ram (more than that would just be wasting space), /home can be as big as you want.  I would use Gparted to make the new drives partitions and then just use Clonezilla to copy the drive (just select partition to partition copy and select all the partitions - if you tell it to just copy the whole drive it might resize the partitions to a size you don't want).

---

### Post by Mark_in_Hollywood on 2014-03-21
I had a look at the Clonezilla site as well as the Clonezilla Forum. Oddly, I cannot find documents showing how to make this work for my specific setup. I'm sure it would. I just don't see what to do.

I'm still in the hunt.

---

### Post by mansonfan78 on 2014-03-21
It's not complicated, once Clonezilla is running it's pretty self-explanatory.  I'd say it's much easier to figure out than command line dd.

---

### Post by Mark_in_Hollywood on 2014-03-21
Can you tell me if Clonezilla creates or re-creates the existing partitions? Do I have to create / and /home and swap or does CZ do it automatically?

---

### Post by mansonfan78 on 2014-03-21
If you choose to copy the entire drive it will create the partitions automatically and size them proportionately, meaning if the new drive is twice the size of the old drive than the new partitions will be twice the size of the old ones.  If you want them to be different sizes you'll have to resize them with Gparted later.

---

### Post by sammiev on 2014-03-21
> **Mark_in_Hollywood said:**
> Can you tell me if Clonezilla creates or re-creates the existing partitions? Do I have to create / and /home and swap or does CZ do it automatically?

Clonezilla will put it back as it was on the HDD you saved it from. I use Clonezilla often and learn new things every time I use it.

---

### Post by Mark_in_Hollywood on 2014-04-02
Clonezilla has confused me a lot. While it did clone the target and I can boot into it, it made a mess of things. I followed the instructions exactly. 

When I was asked if I want to clone the boot sector, I said yes.

When I was asked the question about default install I said yes.

My source drive, 400gig, had 3 partitions:

/ (sda1)

/home (sda5)

swap (swap - only 8 gig anyway)

nothing else.

The new drive, after being mauled by Clonezilla has:

sda1 is /

sda3 is /home

sda2 is extended

sda5 is linux-swap

unallocated

for a better description, please see the attached screenshot.[ATTACH=CONFIG]251662[/ATTACH]

I read at, this forum: [Clean 13.10 install, cannot upgrade to 14.04]("http://ubuntuforums.org/showthread.php?t=2203910")

that the problem of:

Partition 2 does not start on physical sector boundary.

can be fixed with software: fixparts, a package not in the USoftwareCent. Nor will apt-get install find it, either.

Can someone please help?

---

### Post by oldfred on 2014-04-02
One thing I do not know about Clonezilla is whether when you clone to a new drive does it create new UUIDs, or do you now have duplicate UUIDs on each drive. Or you need to change old drives UUID to make sure it really boots correct partition.

       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by Mark_in_Hollywood on 2014-04-02
> **oldfred said:**
> One thing I do not know about Clonezilla is whether when you clone to a new drive does it create new UUIDs, or do you now have duplicate UUIDs on each drive. Or you need to change old drives UUID to make sure it really boots correct partition.

       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

please pardon me: whattttt????

Results of CL:

mark@Lexington:~$ sudo blkid -c /dev/null -o list
[sudo] password for mark: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              536a864f-d91c-4e3d-b6f6-108a783d5e46
/dev/sda3  ext4             /home          1455a163-528e-42ec-8b29-ca7076fc00c7
/dev/sda5  swap             <swap>         a37873a0-d70f-495f-92ea-fffb41041cf4

The "booting" isn't the problem. Clonezilla messed up the partitioning. I have an "unallocated" (that's not a partition) of 500 gig, that CZ left unallocated. I'm trying to fix the partitions with the app: fixparts.
What should I do?

---

### Post by oldfred on 2014-04-02
You then have disconnected old drive, so there can be no issue?
You only show sda.

---

### Post by monkeybrain20122 on 2014-04-02
I don't use clonzilla, I use fsarchiver to clone partitions instead of the whole drive. But the way to change uuids should still work if needed (pending outputs for blkid to see whether clonzilla creates new uuid, your problem may lie else where) Here is how I change uuids

[http://ubuntuforums.org/showthread.php?t=2214474&p=12974306#post12974306](http://ubuntuforums.org/showthread.php?t=2214474&p=12974306#post12974306)

---

### Post by mansonfan78 on 2014-04-02
In my experience Clonezilla doesn't create new uuids, it copies the old ones (this is to make sure fstab entries aren't affected).  It will copy partitions by device name, not location - meaning sda3 in the image will be written to sda3 on the disk, even if sda3 is in a different location (or if the order has changed in the partition table).  As long as the system boots and everything works it doesn't really matter if the partitions have moved or are out of numerical order.  As far as the unallocated space is concerned you can always use gparted to resize the existing partitions or create new ones.

---

### Post by Mark_in_Hollywood on 2014-04-02
Not so fast, folks:

mark@Lexington:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00084ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2       765798398   781422591     7812097    5  Extended
[COLOR="#FF0000"]Partition 2 does not start on physical sector boundary.[/COLOR]
/dev/sda3        39063552   765796351   363366400   83  Linux
/dev/sda5       765798400   781422591     7812096   82  Linux swap / Solaris

---

### Post by oldfred on 2014-04-02
You have a new 4K drive, but you do not write into the extended partition just the logical partitions inside the extended partition. The partitions you write into must be divisible by 8.
So it does not matter that sda2 is not on boundry.

If just installing Ubuntu and not dual booting with Windows you can use gpt partitioning. Then you do not have extended and logical partitions.

       Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

   First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[URL="http://ubuntuforums.org/showthread.php?t=1635018"]http://ubuntuforums.org/showthread.php?t=1635018

[/URL]
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

[URL="http://ubuntuforums.org/showthread.php?t=1635018"]
[/URL]

---

### Post by Mark_in_Hollywood on 2014-04-03
OldFred -

I have opened the links you provided. (Color me confused).

I have gone as far as attempting to determine if the motherboard I have supports UEFI (EFI, too) and haven't a clue as to whether it will or will not work in EFI/UEFI manner.

I'm a computer "end user". Not a computer wizard. I say this as reading the GPT pages, of which there are 16 links (and links on some of those 16 pages) and I'm getting more confused feeling just reading the GPT home page about the direction I want to go in.

Can you point me to a tutorial on fixing my problem? It needn't be perfect or total, only something that doesn't require me to spend 4 weeks reading up first? I need a starting point. I'm willing to learn, I'm unwilling to become a boot level computer expert, just to fix a problem caused by otherware (clonezilla). By the bye: I did donate a little $ to the author of the [GPT fdisk Tutorial]("http://www.rodsbooks.com/gdisk/") it sounds like a wonderful app for those who understand it. Sadly, for me, I'm pretty much a GParted user. And GParted doesn't require much technical knowledge, IMO.

MansonFan78 -

Would using the command line: dd have been better for me? I don't understand why clonezilla decided to do what it did. My bad. I came to believe clonezilla was the 'way to go'. And now I have no way to figure a repair/solution.

In another other event such as this one, I would have backed up my /home. (and I have a copy of /home on an external usb drive).  And having such a backup, would have ditched the clonezilla results and re-installed ubuntu and restored the backup. And if that is the simplest way to restore/repair my problem, I'll consider it. Can you opine about this?

So are you both saying that reading through the myriad of pages involving GPT is the only current solution for me?

In the meantime, thank you both for your help.

---

### Post by mansonfan78 on 2014-04-03
If you had used dd the end result might have been better, but if you don't know what you're doing, then getting there would have been more difficult.  Although, at this point it appears to have been difficult anyway.  I don't know why clonezilla did what it did, I've never experienced any problems with it myself.
If you already have a backup of /home it probably would be easiest to just reinstall and let the installer automatically create the partitions.  When installing, when asked to create a user just use the exact same username, password, and computer name you had before (you don't need to worry about the computer name unless you changed what was automatically entered the first time you installed).  After it's installed and you're ready to restore your backup you should reboot into the livecd and do the copying from there so there aren't any conflicts with an active user.

---

### Post by oldfred on 2014-04-03
You do not have a problem. Just a suggestion for the future.

I just suggest gpt as the new somewhat better partitioning system for Ubuntu whether BIOS or UEFI.
I have been using gpt since 10.10 on my BIOS system and all new drives and even larger flash drives are now gpt partitioned. 

MBR(msdos) has been around for 35 years and does not even support new drives over 2TB as that was not even thought of with a PC 35 years ago.

---

### Post by monkeybrain20122 on 2014-04-03
Whenever the option is available I will use mbr instead of gpt at this point. Much simpler to work with and more flexible in terms of cloning, migrating etc. gpt may have some advantages, but most people I know don't have n TB hard drives and I can make as many logical partitions as I like, I don't need a gazillion primary partitions. As least for my use case (I am sure for many others too) I see no advantage of gpt whatsoever, only a drastic loss in flexibility.

---

### Post by monkeybrain20122 on 2014-04-03
> **Mark_in_Hollywood said:**
> 
Would using the command line: dd have been better for me? I don't understand why clonezilla decided to do what it did. My bad. I came to believe clonezilla was the 'way to go'. And now I have no way to figure a repair/solution.
.

If you have mbr (instead of gpt) fsarchiver is the best tool hands down. It is flexible, fast and easy to use. 

It is much much better than clonzilla IMO. Clonezilla requires the target partition to be as large or larger than the original, that makes it inflexible as a migration tool. Sure you can resize the original partition before cloning, but this is not desirable because why should I need to modify my original layout in order to make a copy? And how many times do I have to resize my partitions if I want to do several migrations to smaller and smaller drives (without knowing beforehand what the smallest target drive would turn out to be)?  Moreover resizing is a long and sometimes risky operation with gparted, and one way to use fsarchiver is to completely avoid that even if the purpose is to modify the original drive's layout: clone, delete/repartition/reformat , restore, much faster and risk free comparing to resize.

dd can be dangerous, and you have to redo it for each migration (and it takes long), it doesn't allow you to make multiple restores from a single image.

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

All you need are two commands: savefs and restfs. Check out the options. You may need to change uuids, see my previous posts.

---

### Post by Mark_in_Hollywood on 2014-04-04
With some help in another post I started, I have managed to repair the glut of partitions made by clonezilla. 

The next problem resolved was the ownership created by using GParted on an external eSATA drive. 

After that, I had to modify the /etc/fstab, using the eSATA drive's GUID. I should probably tweak the fstab line about the eSATA, but I am closing this thread for now.

As I write this, Ubuntu's default application (app or applet) named Backup is running and making a backup of my /home.

Thank you to everyone who contributed.

---

