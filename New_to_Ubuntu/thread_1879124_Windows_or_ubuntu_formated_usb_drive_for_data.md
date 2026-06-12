---
title: "Windows or ubuntu formated usb drive for data"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-11-11
I've been running ubuntu 11.04 off of a 16 GB thumb drive and I've been wondering if it might make sense for me to keep the data on a separate thumb drive to make backups and upgrades easier.

I'm wondering if I might be better using a windows formated thumb drive (which ubuntu can read) or an ubuntu formated disk (which I don't believe windows can read). 

What are the pro's and con's of a windows or ubuntu formated usb drive?

Would the performance with ubuntu be better with an ubuntu formated drive or does it not really matter.   Generally not that much data, but will have a lot of email with Thunderbird, images for editing and some light video editing with currently openshot.

Considerations?

Thanks.

---

### Post by HermanAB on 2011-11-11
Use NTFS or VFAT for best cross platform support.

---

### Post by mysteriousdarren on 2011-11-11
Use NTFS because Windows and Ubuntu can read both. If you will always be using linux go ahead and format in ext4. I work in a environment with many Windows machines and find it helpful with the ability to read both. There really is no downside to NTFS other then needing to defrag it every once in a while.

---

### Post by Denver Dave on 2011-11-16
I'm having quite the time creating a writable NTFS drive and stirred up quite the discussion if that is the best format for a data drive.

I'm not trying to be radical here.  Wouldn't it be common for those running ubuntu from a flash drive to want a second and maybe additional USB drives for data?

See discussion about FAT vs NTFS and creating writable NTFS drives:
[http://ubuntuforums.org/showthread.php?p=11462733#post11462733](http://ubuntuforums.org/showthread.php?p=11462733#post11462733)

***** the issue for read-only is the 11.10 USB boot vs 11.04 USB boot - 11.10 DVD book can save to NTFS - see link immediately above *****

---

### Post by JayKay3OOO on 2011-11-16
I used a windows extension to read from ext4, but write was sketchy.

I'd keep the date on a second drive when it's a USB, HDD or SSD drive as you never know when any drive may go :popcorn:

That or you use some service like dropbox to backup important stuff to the cloud in the event of total system failure.

---

### Post by Denver Dave on 2011-11-17
I thought I'd resolve the question of whether to format my 16 GB USB data thumb drive by looking at my two MyBook USB drives and see what they did:

MyBook 1 TB - older - FAT 32
MyBook 2 TB - newer - NTFS

Split decision ?

---

### Post by Mark Phelps on 2011-11-17
NTFS has been out for a long time ... so I never quite understood why USB stick sellers STILL continued to use FAT32 formatting on their products.  When the sizes were xxxMB, I could see them using that.  But when they routinely exceeded xxGB, it made no sense to continue to use FAT32 formatting, especial with the 4GB file size limitation in that filesystem.

Whenever I buy a USB stick, I check the format.  If it's not already NTFS, I reformat it to NTFS.

---

### Post by Cyclane on 2011-11-17
What a big discussion for something so simple.

Ok first of all you don't need fat. I could say all kind of different things about fat but for a data partition fat is the worst fs to choose.

ext4: great fs but writing to this type of fs from windows will give you problems.

NTFS: this is the fs used by windows natively. In the past Linux had problems writing to NTFS but its very reliable now. Some might still say its unreliable but i've never actually seen anyone experiencing problems so I believe they're clinging to facts of the past.

So basically I advise you to choose between NTFS or ext4. ext4 if you only plan to use it on Linux and NTFS if you plan to use the fs on both windows and Linux.

now if you want to know how to do this let us know.

---

### Post by Denver Dave on 2011-11-17
If my 11.10 ubuntu USB Boot drive could write to an NTFS data disk, I would have never thought twice.

See discussion about FAT vs NTFS and creating writable NTFS drives:
[http://ubuntuforums.org/showthread.p...3#post11462733](http://ubuntuforums.org/showthread.p...3#post11462733)

Theory at the moment is that there is an NTFS configuration driver missing from the 11.10 USB, but on the DVD

= = = = =
.... wait - at least for me, the writable NTFS drive has been solved
[http://ubuntuforums.org/showthread.php?p=11466302#post11466302](http://ubuntuforums.org/showthread.php?p=11466302#post11466302)

So now I'm back, now that I have an option, wondering FAT or NTFS

---

### Post by Cyclane on 2011-11-17
> **Denver Dave said:**
> So now I'm back, now that I have an option, wondering FAT or NTFS

This question has been answered multiple times in this thread.

---

### Post by collisionystm on 2011-11-17
If you want to do USB, why not just get a usb hard drive?? 
You can get one the size of a motorola Razr phone that is powered off the usb port and holds atleast 500gb of data. Size problem solved.

---

### Post by Denver Dave on 2011-11-17
> This question has been answered multiple times in this thread.

On this thread the consensus seems to be to use NTFS

However, on another thread, maybe not the consensus, but there has been discussion and reasons for favoring FAT 32
[http://ubuntuforums.org/showthread.php?t=1881701](http://ubuntuforums.org/showthread.php?t=1881701)

Quotes from the other thread:
> Using any journaled filesystem (i.e. ext3 or NTFS) on a USB flash drive is a bad idea because the constant journal writes will greatly shorten the drive life.

I would stick with FAT32 or ext2.

> I see zero reason to use NTFS on Flash media. Even Microsoft doesn't do this... they developed exFAT as a FAT32 replacement. I don't think we have a exFAT driver in Linux yet, however.

For me, probably not a big deal either way, should be able to easily copy all data from one drive to another.   I'll pay attention to other's experience.

---

### Post by Cyclane on 2011-11-19
But if you can live with the limitations of fat, use that. The biggest drawback of fat is the limitation on file size and the amount of files it can hold. A full DVD ISO is enough to reach this limit. If you're not concerned about that it's probably the best FS for you.

Indeed NTFS performs more writes because of journaling what will wear down any kind of flash memory faster. I do believe you can disable journaling on NTFS but this will have a few drawbacks.

Ohhh and exfat is Microsoft proprietary, so I don't advise waiting for support from the open-source community, it could take a while ;)

---

### Post by beew on 2011-11-19
> **Cyclane said:**
> Windows is released on a DVD, so fat/ntfs doesn't come into play. Though when you make a bootable USB for windows 7 it is advised your format the drive according to NTFS standards. Also you are able to disable journaling on a filesystem, though off course this has some draw backs too (that's why it isn't the default standard).


AFAIK bootable Windows 7 usb is only for upgrading an existing Vista machine on which there is no CD ROm. It has to be created using MS's own tool installed on the same machine, and you are supposed to be able to use it only on this same machine, once. So it is a very restrictive scenario anyway.

---

### Post by Denver Dave on 2011-11-20
Someplace I I think I read that fragmentation is not a problem with ubuntu.  Is this universal with ubuntu or does the type of disk format effect the fragmentation?  Or I incorrect on the fragmentation issue for data drives.

I have a couple of TB USB hard drives and may go to them eventually, but for now, it is neat being able to carry the boot USB stick and my data stick in my shirt pocket (where did I set that drive?)

---

### Post by Cyclane on 2011-11-20
> **beew said:**
> AFAIK bootable Windows 7 usb is only for upgrading an existing Vista machine on which there is no CD ROm. It has to be created using MS's own tool installed on the same machine, and you are supposed to be able to use it only on this same machine, once. So it is a very restrictive scenario anyway.

Uhmmm no...,just a plain simple no. You can create a bootable windows 7 USB from the files on the CD without any Microsoft tools, and it will be usable on any PC for any number of times.. It's even the only way to install windows on a netbook since they don't have a cdrom reader.

---

### Post by beew on 2011-11-20
> **Cyclane said:**
> Uhmmm no...,just a plain simple no. You can create a bootable windows 7 USB from the files on the CD without any Microsoft tools, and it will be usable on any PC for any number of times.. It's even the only way to install windows on a netbook since they don't have a cdrom reader.

Have you done it without MS's tool?

Even if it is bootable can you actually run Windows 7 off it? I think it is just for installation.

---

