---
title: "Cannot detect scanner on detected HP printer"
date: 2022-08-12
forum: New to Ubuntu
---

### Post by euphorbialand on 2022-08-12
My Ubuntu 14.04 easily detected AllinOne HP 4520 printer automatically. The driver it automatically selected is hpcups 3.24.3 But it does not see the scanner. I tried everything possible that I found on the web.
 
1. I used localhost:831 that also detected a printer but not a scanner. The driver I selected manually is hpcups 3.14.3. Maybe I should use different driver but I don't know which one. 
2. I used Xsane which does not detect the scanner. In its control file there is "net" command. It searches the net and does not find anything. 
3. I used hplip with the IP address of a printer. It does not detect even a printer not to mention printer with a scanner.  
I have only basic knowledge of Ubuntu so I run out of ideas. 
I would appreciate any suggestions. Thanks in advance.

---

### Post by Autodave on 2022-08-12
Ubuntu 14.04????  That is 8 years old now.  You really need to d-l 20.04 or even 22.04 and start again.  14.04 is way too old and I doubt that anyone here will be able to assist you.

---

### Post by euphorbialand on 2022-08-12
I am planning to install on my Lenovo Yoga 13 with i7 processor ubuntu 20.04. I like to have LTS with it. 

I am currently testing all needed functions on 14.04 to be sure that I don't have any surprises after wiping out Windows from the computer. If you think that the problem will be fixed in new version of ubuntu I hope I will be OK. The scanner is the only problem I have. Everything else works great regardless of the ubuntu version. 

Thanks for your response.

---

### Post by Autodave on 2022-08-13
Well, I believe that that printer is newer than 14.04, so I would doubt that the drivers that are needed would be in 14.04.

I cannot say for certain that it will work in 20.04/22.04, but I can tell you that I have NEVER had an issue with getting an HP printer to work in any Linux distribution.  I have 9 different machines running Linux and they all work with the 9 different printers hooked up to them.

---

### Post by aljames2 on 2022-08-13
> **euphorbialand said:**
> I am currently testing all needed functions on 14.04 to be sure that I don't have any surprises after wiping out Windows from the computer. If you think that the problem will be fixed in new version of ubuntu I hope I will be OK. The scanner is the only problem I have. Everything else works great regardless of the ubuntu version. 

+1 what Autodave says

On the being “OK” part, having reliable, recovery tested backups of your data will take care of that.

---

### Post by euphorbialand on 2022-08-13
I backed up all my data, but to be honest I am not sure how to restore Windows after I start ubuntu installation. I don't want two systems. I want just ubunu. I have currently windows 8.1 that will expire by the end of the year. I don't want to buy new Windows, new office and whatever Microsoft has to offer for big bucks. I just hope that I will be succesful with installing Ubuntu. I did not have any problems on my 32 bits computer with ubuntu 14.04.

---

### Post by Autodave on 2022-08-13
32 bit could be a problem......and I hope that someone corrects me if I am wrong here, but I believe that Lubuntu may be your only option.  And 20.04 might be also be your only option.

---

### Post by euphorbialand on 2022-08-13
While creating installation disk I got some problems. I downloaded ISO file of 22.04 version of Ubuntu and proceeded to create installation disk on 32GB flash drive. I used BalenaEtcher. It worked for a while, performed verification and then said "flash failed". I repeated the process and it again told me "flash failed". I looked at the flash drive. It is empty, write protected and impossible to format. I used all kinds of tricks to remove write protection like using diskpart but it does not see this flash drive. Chkdsk tells me that it is not available for RAW drives. I used Recuva to recover whatever was on the disk but it does not recognize file system type. Ubuntu computer does not see this flash drive.I was afraid to use registry to remove write protection because I wouldn't really know what I were doing.

What the heck this BalenaEtcher did to this flash drive, I would like to know.

Looks like I need to throw away this flash drive and never use BalenaEtcher again.  Total loss of the flash drive and still no installation drive. I remember that I used "Startup Disk Creator" before. I hope I can use "Startup Disk Creator" from 14.04 version to create bootable flash drive for 22.04 version.

---

### Post by Impavidus on 2022-08-14
> **euphorbialand said:**
> I backed up all my data, but to be honest I am not sure how to restore Windows after I start ubuntu installation. I don't want two systems. I want just ubunu. I have currently windows 8.1 that will expire by the end of the year. I don't want to buy new Windows, new office and whatever Microsoft has to offer for big bucks. I just hope that I will be succesful with installing Ubuntu. I did not have any problems on my 32 bits computer with ubuntu 14.04.You can restore Windows later if you've got a complete backup, including all the boot stuff, so that means a disk image. Some people just remove the hard drive and plug in a fresh one for Ubuntu. When they want to restore Windows, they put the original harddrive back. Otherwise, you can reinstall Windows if you've got an installation disk. But if you only want Ubuntu, why bother. I've just Linux only for 15 years or so.

I assume that this 32 bit computer is a different one, right? Because i7 processors are 64 bit. Ubuntu no longer supports 32 bit on new releases; the last supported 32 bit release is 18.04 (technically, Lubuntu only, and that had only 3 years of support).

> **euphorbialand said:**
> While creating installation disk I got some problems. I downloaded ISO file of 22.04 version of Ubuntu and proceeded to create installation disk on 32GB flash drive. I used BalenaEtcher. It worked for a while, performed verification and then said "flash failed". I repeated the process and it again told me "flash failed". I looked at the flash drive. It is empty, write protected and impossible to format. I used all kinds of tricks to remove write protection like using diskpart but it does not see this flash drive. Chkdsk tells me that it is not available for RAW drives. I used Recuva to recover whatever was on the disk but it does not recognize file system type. Ubuntu computer does not see this flash drive.I was afraid to use registry to remove write protection because I wouldn't really know what I were doing.

What the heck this BalenaEtcher did to this flash drive, I would like to know.

Looks like I need to throw away this flash drive and never use BalenaEtcher again.  Total loss of the flash drive and still no installation drive. I remember that I used "Startup Disk Creator" before. I hope I can use "Startup Disk Creator" from 14.04 version to create bootable flash drive for 22.04 version.
Some tools may get confused as the usb drive has no valid partition table. Wiping the first megabyte may help. I don't think that BalenaEtcher has destroyed your usb drive, but it may have been bad already. Every Ubuntu release has all the tools you need to create a life disk. You can even use a simple file copy tool to copy the .iso file to the usb device (normally /dev/sdb or something like that, but you have to check, or you may overwrite some other drive). As in, copy it to the device itself, not to its mountpoint. Don't even mount it.

---

### Post by ajgreeny on 2022-08-14
You can try using gparted to create a new partition table on that USB disk.

I very much doubt that the disk is damaged. I suspect it has an ISO9660 filesystem like a CD meaning it is not writable, just like a normal CD.
Give it a new partition table (msdos) and then create a new fat32 partition and you'll probably find all is good again.

---

### Post by mIk3_08 on 2022-08-14
> **euphorbialand said:**
> My Ubuntu 14.04  This Linux Ubuntu 14.04 already end of life last 2015. Just want to remind you that its already end of support but maybe others still have a solution to your issue just stay cool. Regards and cheers.

---

### Post by euphorbialand on 2022-08-14
I cannot do anything with this flash drive because it has write protection that I cannot remove. Believe me, I tried. It was formated before I started with BalenaEtcher so it was fine. I found on the web that many people complained about the problem that BalenaEtcher destroyed their flash devices. BalenaEtcher must be aware of it because on their web site there is an instruction how to recover the devices. Mine has write protection. This is my personal opinion, but I don't understand why Ubuntu.com promotes this application. At best it has not been tested suficiently. There are other Windows applications like Unetbootin, Rufus or Universal USB Installer. I will get another flash drive and use UUI. Hopefully it will work.
Thanks for all your responses.

---

### Post by Impavidus on 2022-08-14
There's a difference between a read-only usb drive and a read-only filesystem.

Some usb drives have a write protect switch. If you put that switch to read-only, the circuits required for writing to the drive are physically disabled and the entire drive is read-only. I haven't encountered such a usb drive in over a decade.

When you write the .iso file to the usb drive, it may (depending on the settings of the tool you use, but it's always the case for simple cloning) create an iso9660 filesystem. Such a filesystem is read-only by design. Once created with a bunch of files in place, no new files can be added. That makes your filesystem read-only. The instructions to recover the drive, as given on BalenaEtcher's website, are to get rid of this read-only filesystem and get an ordinary filesystem back &#8211; usually FAT32, exFAT or NTFS &#8211; simply by formatting the drive again. This has nothing to do with a read-only drive. BalenaEtcher and all other tools you can use to make live disks can put a read-only filesystem on the drive, but won't make the drive itself read-only. The people complaining that BalenaEtcher destroyed their usb drives don't know the difference between read-only drives and read-only filesystems.

Maybe you can just format the drive, maybe there's a switch on the side that made it read-only and was accidentally moved (not very likely), maybe the drive is broken. Of course, it's possible that it broke by chance just as you created the live disk. After all, it's a large write. Some formatting tools get confused when there's something unexpected on the drive. In that case, wipe the first megabyte. Then most tools won't be confused any more.

Ubuntu 14.04 is dead. It's no longer safe to use for most applications. However, you can still use it to create a live disk of a more recent Ubuntu release. If you can't create an Ubuntu live disk with Windows tools, use Ubuntu 14.04. Just don't use it to browse the web.

Following commands can be dangerous. I cannot guarantee that your usb drive will be known as /dev/sdb; if it's known by another name, change the commands accordingly or you'll wipe the wrong drive. Also, substitute the path to your ubuntu live disk .iso file. Any typo in one of these commands can wipe the wrong drive and destroy all your files, so be careful.

To wipe the first megabyte of your usb drive:```
sudo dd if=/dev/zero of=/dev/sdb bs=4096 count=256
```That should remove any confusion for the partitioning tools.

To clone the live disk image to your usb drive:```
sudo dd if=/path/to/ubuntu-live-disk.iso of=/dev/sdb bs=4096
```That should create a bootable live usb. The filesystem on the usb will be read-only, but you can still format it later to a read-write filesystem.

If dd complains that it cannot write to the usb drive, the problem is in the hardware and no software trick can fix it. Either there's a physical write-protect switch or the drive is really broken (and probably was (almost) broken already).

After running either of those commands, make sure everything was actually written to the drive and no longer sitting in some buffer:```
sync
```

---

### Post by euphorbialand on 2022-08-14
Thank you impavidus for giving me so much information. 

It might be the case that the flash drive is broken because windows refuses to format it saying that it is write protected. There is no switch to turn off write protection. As for ubuntu computer with 14.04 version it does not even see this flash drive. I tested the system with other flash drives. They are visible by ubuntu system.

 I ordered several 16 GB flash drives from Amazon. I was surprised that they are so cheap. I haven't purchased it for few years.

Regarding your advise to use 14.04 version to create bootable flash drive using "Startup Disk Creator" I read on the web, maybe the person was wrong, that "Startup Disk creator" can only be used if already existing ubuntu system has the same version as the bootup flash drive it is creating. Some people complained about errors while installing the system created by older version of "Startup Disk Creator". Especially from 32 bits to 64 bits. But I will try it to see whether they are have a point. 

As for creating live bootable drive that is read only created by BalenaEtcher.  I looked at the one with 14.04 version. It is maybe read only but the contents is visible by any computer. The one created by BalenaEtcher does not show any contents under Windows and is not visible on ubuntu computer. How could I boot from this drive if the computer would not even see it. 

 I am planning to create several versions of bootable flash drives using different tools like Windows applications Unetbootin, Rufus, and UUI (Universal USB Installer) and also by "Startup Disk Creator" since flash drives are so inexpensive. I am sure one of them will work. I will keep away from BalenaEtcher though.

---

### Post by Impavidus on 2022-08-15
I think I once used Startup Disk Creator on Ubuntu 12.04 (32 bit) to create a live disk for Ubuntu 13.10 (I think 64 bit), but 12.04 was still supported when 13.10 was released, so that's different from using 14.04 to create one for 22.04. If you can't use Startup Disk Creator, you can always clone from the command line. I posted the command in my previous post.

Last time I bought a usb drive must have been about 9 years ago, a 16GB drive for about €10, one of the smallest models they had available. I'm surprised they still sell 16GB drives.

BTW, have you made sure the .iso file is OK? File corruption sometimes happens. If the file is damaged, your live usb won't work and strange errors could happen.
[https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview)

---

### Post by euphorbialand on 2022-08-15
Hi Impavidus. 
I do everything on Windows 8.1 for the moment. I haven't installed ubuntu yet. So I cannot apply terminal commands that you suggested. 

But I followed your advise to verify whether ISO file is corrupted, and downloaded WinMD5 to verify checksum and also used certutil from command line of Windows. I don't know how to compare checksup with original checksum. I could not fine anything on ubuntu.com. Something like hash number. I don't know how it works.

But I downloaded three times the same copy of ISO file. The first copy has checksum different from two others. I suppose that since the second and the third are the same the first one might have been corrupted. I was hoping that BalenaEtcher would have positive verification on the second copy of ISO file but it failed again. I need to wait for pen drives from Amazon to try other applications. 

Is there other way to verify whether ISO file is corrupted using Windows?

Thank you so much for your assistance.

---

### Post by Impavidus on 2022-08-17
Go to [http://releases.ubuntu.com/](http://releases.ubuntu.com/), find the 22.04.1 .iso and look for the SHA256SUMS file. It lists the SHA256 checksums:```
c396e956a9f52c418397867d1ea5c0cf1a99a49dcf648b086d2fb762330cc88d *ubuntu-22.04.1-desktop-amd64.iso
10f19c5b2b8d6db711582e0e27f5116296c34fe4b313ba45f9b201a5007056cb *ubuntu-22.04.1-live-server-amd64.iso
```
It appears that the old md5 checksums are gone now. They're no longer considered cryptographically secure, but are still useful to check for accidental file corruption.

If you download the .iso by torrent, this check is performed automatically during download. File corruption is most likely to happen during download.

---

### Post by mIk3_08 on 2022-08-17
> **euphorbialand said:**
> My Ubuntu 14.04 easily detected AllinOne  HP 4520 printer automatically. The driver it automatically selected is  hpcups 3.24.3 But it does not see the scanner. I tried everything  possible that I found on the web.
1. I used localhost:831 that also detected a printer but not a scanner.  The driver I selected manually is hpcups 3.14.3. Maybe I should use  different driver but I don't know which one. 

In my case  I've have my brother printer installed via wifi and I have downloaded  from the brother's website and installed all the drivers I need for my  Brother printer/scanner and configure out the .cfg from the root scanner  folder and run the command:
```
brsaneconfig4 -a name=PrinterBrand model=PrinterModel XXX-X500X ip=192.168.1.101 
``` 
But the results gives "Permission denied"
so I run the following command
```
sudo chmod a+rwx targetpath/brsaneconfig4.cfg
``` 
so the next time I run the first command it was then successful. 
And my printer scanner works perfectly with xsane image scanning program and simple scanned Regards and cheers.

---

### Post by euphorbialand on 2022-08-19
Hi Impavidus,

I finally figured out that there are different formats of checksum. I downloaded MD5_and_SHA_Checksum_Utility and verified that SHA256 is correct. Now I think I am getting somewhere. I created 4 different installation flash drives: UUI, RUFUS, UNETBOOTIN and one from startup utility on my old ubuntu 14.04. I hope one will work. I need to do lots of housekeeping to preserve my data and I am ready for installation. I learned a lot in the process.  

Microsoft is so funny. Periodically it displays message on my 8.1 computer that they will terminate support by the end of the year and gives me advise what to do about it. Advise is unambiguous. "Buy new computer with Windows 11" followed by the link where I could find new computers to purchase. No comments.  

Once more thank you very much for your advise. I hope I will manage with installation. Otherwise I will be back with farther questions.

---

