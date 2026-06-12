---
title: "[SOLVED] Installing on a HD partition, booting from USB pen drive problems"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by ElCapitanAmerica on 2008-11-29
Basically, I have a small install of Ubuntu on a partition of my laptop (which has WinXP) and I want to boot from a USB "pen drive".

So I did a manual install of 8.10, installed the OS on the partition (that seemed to work) and in the "advanced" option for the GRUB installation I asked it to install it on my external USB pen drive.

Anyways, when I boot, all I get is my screen being filled up with repeated GRUB GRUB GRUB GRUB messages, as if caught in an infinite loop.

I've looked around on google, and get some people saying this is a problem with the GRUB stages, but I'm not getting how to fix this. Anybody have any ideas?

---

### Post by paultag on 2008-11-29
This is a curious issue.

Perhaps boot into 8.10 and try out the new utility to make a pen drive ISO Image?

Cheers,
Tag

---

### Post by ElCapitanAmerica on 2008-11-29
I can try that, but won't that just go ahead and install the OS to my thumb drive (which is not what I want). Maybe I should just look at the options for that util ...

---

### Post by ElCapitanAmerica on 2008-11-29
Well I checked on that option, and is says "USB startup", but it looks like it installs a full OS to the drive which is not what I want.

Anyways, I reinstalled and this time tried with another USB pen drive I have and get the same error "GRUB GRUB GRUB GRUB ...". Just did this to see if there was anything weird with the USB device.

Note that I can boot from these usb devices, as I have a full Ubuntu install in one of them and it boots fine. I just don't want to use it because it's very slow, and rather just use a little bit of spare space I have on my laptop drive. Without of course messing too much with it, which is why I want grub on the device.

This is similar to me installing Linux (a looooong time ago) and booting from a floppy drive, still, not sure why this isn't working.

---

### Post by caljohnsmith on 2008-11-30
How about opening a terminal (Applications > Accessories > Terminal), and please post the following:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like. 

Also, getting that repeating "GRUB" error on start up is often due to having your drive misconfigured in BIOS; first let's start with the above information, but you also may want to check what drive-related options are available in your BIOS, such as "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Let me know what BIOS options you have if it's not too much trouble. We can work from there if you want.

---

### Post by ElCapitanAmerica on 2008-11-30
Thanks for the reply, here are the results.

fdisk -lu returns;

-------------
[B]
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75487548

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52436159    26218048+   7  HPFS/NTFS
/dev/sda2        52436160   195366464    71465152+   f  W95 Ext'd (LBA)
/dev/sda5        52436223    62926604     5245191    7  HPFS/NTFS
/dev/sda6        62926668    73160009     5116671    7  HPFS/NTFS
/dev/sda7        83907558   104888384    10490413+   7  HPFS/NTFS
/dev/sda8       104888448   195366464    45239008+   7  HPFS/NTFS
/dev/sda9        73160073    83907494     5373711   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1014 MB, 1014497280 bytes
65 heads, 24 sectors/track, 1270 cylinders, total 1981440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          88     1981439      990676    6  FAT16[/B]

-------------------

/dev/sda is my laptop HD
/dev/sdb is my pen drive, 
/dev/sda9 is the partition with Ubuntu on my drive. The rest is Windows (with 2 encrypted partitions).

Next commands;
sudo xxd -l 2 -p /dev/sda
**faeb**

sudo xxd -l 2 -p /dev/sdb
**eb48**

sbd returns eb48 so for that one we get;
sudo xxd -s 1049 -l 2 -p /dev/sdb
**0880**

I'm going to look into the BIOS options next, however, I did google some postings about a similar problem and the drive auto detect BIOS options, however, I couldn't findd that option at all in the BIOS menu (but will look again).

Thanks for the help!

---

### Post by caljohnsmith on 2008-11-30
The results of those commands show that Grub for some reason didn't get installed to the MBR (Master Boot Record) of you USB pen drive correctly. How about posting the output of:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Next do:
```
sudo dd if=/dev/sda count=62 | gzip -c > ~/Desktop/sda.MBR.gz
```
That will create a really small "sda.MBR.gz" file on your desktop; please attach that file to your next post so I can check it (click the paper click icon in the Ubuntu message box in your browser to attach the file). After that, go ahead and reboot, and let me know what happens when you boot the pen drive. :)

---

### Post by ElCapitanAmerica on 2008-11-30
The results btw are from booting from a Live CD of course (since I can't boot from my pen drive, nor get to my partition).

For the first grub command you sent, is that going to print results from the LiveCD, HD or pen drive (again taking into count that I'm booting LiveCD).

On the second command, I'm assuming you're trying to see an image for the MBR, you want the one for the hard drive or the one for the pen drive (which is sdb instead of sda)?

---

### Post by ElCapitanAmerica on 2008-11-30
Well I guess hd1 is my pen drive? Anyways here is the result of the grub command;

grub> setup (hd1)
Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists... no

Error 15: File not found

---

### Post by caljohnsmith on 2008-11-30
OK, I think I was misunderstanding what you are trying to do. Let me see if I have it right now: you installed Ubuntu to your HDD, but instead of installing Grub to the MBR of your HDD, you wanted to install Grub to the MBR of your pen drive so that you would boot Ubuntu by simply booting your pen drive? And when the pen drive is not plugged in, you want to simply boot straight into Windows on your HDD? Is that maybe what you are looking for? 

If that's what you want to do, then try this:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,8)
grub> setup (hd0)
grub> quit
```
Also, are you currently able to boot straight into Windows OK? Because the MBR for your Windows drive returned a different result with the xxd command than the Windows MBRs I've encountered. So if I could ask you a small favor, would you mind if I look at your sda Windows MBR? That's what that "dd" command does in my previous post, so if it's not too much trouble to post that file, it would help me out so I can figure out why your Windows MBR returned a different result than what I expected. :)

---

### Post by meierfra. on 2008-11-30
> sudo xxd -l 2 -p /dev/sda
faeb

caljohnsmith:

This means "Lilo" is installed in the MBR of sda.

---

### Post by ElCapitanAmerica on 2008-11-30
I've got safeboot booting up on the HD, is that it?

Hey thanks the grub commands you sent worked! So I'm taking it for future reference, if I want to try this setup again, I have to do this manually? 

You are correct, what I want is to boot from a USB pen drive into an unencrypted partition on my laptop's harddrive. Initially, in the last stage of the Ubuntu install ( I did the manual option for the partitioning ) I pointed it to install GRUB into my USB drive but I guess that doesn't work.

Anyways, thanks a lot! If I understand those commands correctly, did that just setup the right order for the devices? And what's the '8' for in the root command?

Thanks!

BTW - Somebody else edits the thread title to solved right? I don't see the option for me to do so myself.

---

### Post by caljohnsmith on 2008-11-30
> **ElCapitanAmerica said:**
> I've got safeboot booting up on the HD, is that it?

Hey thanks the grub commands you sent worked! So I'm taking it for future reference, if I want to try this setup again, I have to do this manually? 

Unfornately, yes, you have to do it manually since the Ubuntu installer can't handle special cases yet like what you wanted to do. 
> **ElCapitanAmerica said:**
> 
Anyways, thanks a lot! If I understand those commands correctly, did that just setup the right order for the devices? And what's the '8' for in the root command?

Thanks!
Yes, the trick is just using the "device" commands to set up the correct order of the drives so that when you boot the USB pen drive, it will correctly point to your internal drive for Grub's boot files. And the "8" in the root command is your Linux partition, sda9, because Grub's numbering starts with 0 and not 1. Anyway, I'm really glad it worked, cheers and have fun with your OSes. :)

EDIT: If you go to the top of the thread and click on the "thread tools" link, it gives you the option to mark the thread as "solved".

---

