---
title: "GParted scrapped my SD Card, searching a repair utility."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by LeDechaine on 2008-07-08
Having bought an all new 8GB CF (Yeah Compact Flash, not SD, correction.) Card that I had to format and partition in ext2, I decided to put trust a shiny little GUI daemon called GParted. When I finally finished partitioning my CF Card, after many crashes and segfaults, long story short, my card became a 32mb card according to GParted, and fdisk, and nautilus, and after trying to repair the stupidity of GParted which propagated through my 8GB CF Card with the good old fdisk.. my 8GB CF Card won't even mount, Ubuntu believing that my 8GB Card is more than 2000GB and giving me I/O errors after.

So i'm now searching for a program which is able to repair a disk scrapped by some worthless stupid ignorant wannabe-coders who thought it would be good to publish a trainwreck daemon that could scrap an entire drive in two simple GUI commands.

Thanks in advance.
And thanks in advance, too, for not arguing about my arrogance, since a free daemon just cost me 60$, or else, at least, 4 hours of my too tiny spare time.

---

### Post by st33med on 2008-07-08
Ummm...Why did you have to format your card? You did not have to do that, since Ubuntu usually detects whatever the format the card is using, usually FAT32...

---

### Post by LeDechaine on 2008-07-08
I wanted ext2. And the card was not for an Ubuntu machine.

---

### Post by sdennie on 2008-07-08
1) As st33med said, it's best to leave removable media in something like FAT32 because if you plug it into another machine, the permissions will not be right for something like ext2.

2) FAT support has been available in linux for as long as I can remember regardless of whether or not you are using Ubuntu.

3) Maybe the problem is with the SD card or, equally likely, your card reader.  Is your card reader actually capable of reading SDHC cards?  If you were getting segfaults and crashes while trying to partition the card, that sounds like something is fundamentally broken.

4) Calling people, "worthless stupid ignorant wannabe-coders who thought it would be good to publish a trainwreck daemon that could scrap an entire drive in two simple GUI commands" is not a good way to get help.  It's probably more insulting still to said programmers that you called gparted a daemon.

---

### Post by sloggerkhan on 2008-07-08
flash memory has been very temperamental for formatting in my experience, possibly because sector and cluster sizes are hardwired?
In any case I think there are some basic differences with flash memory that somehow cause problems when it's treated like a hard disk.

[http://tldp.org/HOWTO/html_single/Flash-Memory-HOWTO/](http://tldp.org/HOWTO/html_single/Flash-Memory-HOWTO/)
is old but might help.

---

### Post by dmizer on 2008-07-08
i can think of many reasons to format a usb disk to ext2, not the least of which is the 2gig file size limit for fat32.

well, i'm not sure if your card is toast or not, but i thought you might like to know why this happened.  so, for future reference:

when formating a usb drive, you must disable the hal daemon with the following command:
```
sudo killall hald
```
if this is not done, the hal daemon will mount the drive when qparted accesses it for formatting, which means that the drive cannot be formatted.  this is a vicious cycle and can break things if you try to continue the format.

once the format has completed, restart the hardware layer with this command:
```
sudo /etc/init.d/dbus restart
```

this is a good practice to use any time you use gparted (or any other partitioning program) to partition any drive.

---

### Post by dmizer on 2008-07-08
> **vor said:**
> 1) As st33med said, it's best to leave removable media in something like FAT32 because if you plug it into another machine, the permissions will not be right for something like ext2.

this is partially true.  to avoid this problem, all you have to do is create a world rwx folder (sudo chmod 777 /mount/point/folder) on the drive and store everything in there.

---

### Post by LeDechaine on 2008-07-09
> **vor said:**
> 1) As st33med said, it's best to leave removable media in something like FAT32 because if you plug it into another machine, the permissions will not be right for something like ext2.

2) FAT support has been available in linux for as long as I can remember regardless of whether or not you are using Ubuntu.

3) Maybe the problem is with the SD card or, equally likely, your card reader.  Is your card reader actually capable of reading SDHC cards?  If you were getting segfaults and crashes while trying to partition the card, that sounds like something is fundamentally broken.

4) Calling people, "worthless stupid ignorant wannabe-coders who thought it would be good to publish a trainwreck daemon that could scrap an entire drive in two simple GUI commands" is not a good way to get help.  It's probably more insulting still to said programmers that you called gparted a daemon.
1) I don't want a linux operating system running in a fat32 partition.
2) I know.
3) It's actually a CF Card. I wrote this too fast before going to bed. And I think the only thing that is actually fundamentally broken.. is GParted. Everything seemed fine with the card until I used this program.
4) It's a good way to get help through people who feel the same. For the rest, I'm not crazy enough to get help from these wannabe-coders, unless I want to scrap another drive.

---

### Post by dmizer on 2008-07-09
> **LeDechaine said:**
> And I think the only thing that is actually fundamentally broken.. is GParted. Everything seemed fine with the card until I used this program.
there is nothing fundamentally, or even partly broken with gparted.  i use it quite frequently to reformat usb flash memory drives and CF cards.

---

### Post by LeDechaine on 2008-07-09
> **sloggerkhan said:**
> flash memory has been very temperamental for formatting in my experience, possibly because sector and cluster sizes are hardwired?
In any case I think there are some basic differences with flash memory that somehow cause problems when it's treated like a hard disk.

[http://tldp.org/HOWTO/html_single/Flash-Memory-HOWTO/](http://tldp.org/HOWTO/html_single/Flash-Memory-HOWTO/)
is old but might help.
Thanks, but it's no help for me. =/

After trying *many* things (debugfs, etc).. I can see that 90% of the time i get the "**Attempt to read block from filesystem resulted in short read**" error.

The problem is that, yeah, the filesystems are scrapped. The drive doesn't even mount. It's /dev/sdb, but almost everything I can get from this is some "**Attempt to read block from filesystem resulted in short read**" errors. No /dev/sdb1, because the partition(s) can't be mounted.

Let's say, «I need a program to repair a drive. Not a partition.» Maybe if I use "dd" to write zeros everywhere in /dev/sdb... don't know.

Again, thanks in advance.

---

### Post by LeDechaine on 2008-07-09
Have fun, more weirdness:

> Jul  9 20:38:53 ubuntu kernel: [ 5090.151116] sd 2:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Jul  9 20:38:53 ubuntu kernel: [ 5090.151886] sd 2:0:0:0: [sdb] READ CAPACITY(16) failed
Jul  9 20:38:53 ubuntu kernel: [ 5090.151898] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Jul  9 20:38:53 ubuntu kernel: [ 5090.151908] sd 2:0:0:0: [sdb] Use 0xffffffff as device size
Jul  9 20:38:53 ubuntu kernel: [ 5090.151918] sd 2:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
Jul  9 20:38:53 ubuntu kernel: [ 5090.163111] sd 2:0:0:0: [sdb] Write Protect is off
Jul  9 20:38:53 ubuntu kernel: [ 5090.232053] sd 2:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Jul  9 20:38:53 ubuntu kernel: [ 5090.232713] sd 2:0:0:0: [sdb] READ CAPACITY(16) failed
Jul  9 20:38:53 ubuntu kernel: [ 5090.232723] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Jul  9 20:38:53 ubuntu kernel: [ 5090.232733] sd 2:0:0:0: [sdb] Use 0xffffffff as device size
Jul  9 20:38:53 ubuntu kernel: [ 5090.232744] sd 2:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
Jul  9 20:38:53 ubuntu kernel: [ 5090.243044] sd 2:0:0:0: [sdb] Write Protect is off
Jul  9 20:38:53 ubuntu kernel: [ 5090.243076]  sdb:end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:53 ubuntu kernel: [ 5090.281050] printk: 6 messages suppressed.
Jul  9 20:38:53 ubuntu kernel: [ 5090.321001] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:53 ubuntu kernel: [ 5090.360966] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:53 ubuntu kernel: [ 5090.400954] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:53 ubuntu kernel: [ 5090.440910] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:53 ubuntu kernel: [ 5090.480907] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.521847] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.560804] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.600799] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.601191] Dev sdb: unable to read RDB block 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.640777] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.680724] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.720696] end_request: I/O error, dev sdb, sector 24
Jul  9 20:38:54 ubuntu kernel: [ 5090.760668] end_request: I/O error, dev sdb, sector 24
Jul  9 20:38:54 ubuntu kernel: [ 5090.800632] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.840601] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5090.840818]  unable to read partition table
Jul  9 20:38:54 ubuntu kernel: [ 5090.960507] end_request: I/O error, dev sdb, sector 4294967168
Jul  9 20:38:54 ubuntu kernel: [ 5091.000480] end_request: I/O error, dev sdb, sector 4294967168
Jul  9 20:38:54 ubuntu kernel: [ 5091.040456] end_request: I/O error, dev sdb, sector 4294967280
Jul  9 20:38:54 ubuntu kernel: [ 5091.080417] end_request: I/O error, dev sdb, sector 4294967280
Jul  9 20:38:54 ubuntu kernel: [ 5091.120396] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5091.160356] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5091.200344] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:54 ubuntu kernel: [ 5091.240304] end_request: I/O error, dev sdb, sector 4294967288
Jul  9 20:38:55 ubuntu kernel: [ 5091.281293] end_request: I/O error, dev sdb, sector 4294967288
Jul  9 20:38:55 ubuntu kernel: [ 5091.610043] end_request: I/O error, dev sdb, sector 4294967288
Jul  9 20:38:55 ubuntu kernel: [ 5091.649994] end_request: I/O error, dev sdb, sector 4294967288
Jul  9 20:38:55 ubuntu kernel: [ 5091.689957] end_request: I/O error, dev sdb, sector 4294967288
Jul  9 20:38:55 ubuntu kernel: [ 5091.730927] end_request: I/O error, dev sdb, sector 4294967288
Jul  9 20:38:55 ubuntu kernel: [ 5091.770904] end_request: I/O error, dev sdb, sector 4294967232
Jul  9 20:38:55 ubuntu kernel: [ 5091.809866] end_request: I/O error, dev sdb, sector 4294967280
Jul  9 20:38:55 ubuntu kernel: [ 5091.849833] end_request: I/O error, dev sdb, sector 4294967288
Jul  9 20:38:55 ubuntu kernel: [ 5091.889813] end_request: I/O error, dev sdb, sector 4294967288
Jul  9 20:38:55 ubuntu kernel: [ 5091.930783] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5091.970745] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5092.009712] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5092.049679] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5092.089673] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5092.139611] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5092.179582] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5092.219564] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5092.260539] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:55 ubuntu kernel: [ 5092.299519] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.339924] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.659239] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.699191] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.739157] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.779127] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.819091] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.859065] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.899030] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.939002] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5092.978972] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5093.018943] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5093.058913] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5093.098870] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5093.138870] end_request: I/O error, dev sdb, sector 0
Jul  9 20:38:56 ubuntu kernel: [ 5093.178822] end_request: I/O error, dev sdb, sector 0

This.. is actually what happens when I plug in my CF Card. This ends there, at least. :P

---

### Post by dmizer on 2008-07-09
have you considered that the cf card may have been toast to begin with?  if it's a new card, just take it back and exchange it for a new one.

you said that you had crashes and seg faults while attempting to format this drive, so that suggests to me that either there's something broken in your install, or there was a problem with the hardware.

---

### Post by LeDechaine on 2008-07-09
Yeah this is actually a brand new card.. The first thing I dit was plugging it there and using GParted to *try* to partition it. Then.. that.

And the crashes/segfaults always happened when I tried to unmount the card via GParted.  *click* *crash* *restart GParted = Card is unmounted.*

---

### Post by dmizer on 2008-07-09
> **LeDechaine said:**
> Yeah this is actually a brand new card.. The first thing I dit was plugging it there and using GParted to *try* to partition it. Then.. that.

And the crashes/segfaults always happened when I tried to unmount the card via GParted.  *click* *crash* *restart GParted = Card is unmounted.*

seriously, save yourself the frustration and just exchange the card for a new one.  the card may have been damaged in your attempt to format it, the card may have been damaged before you purchased it, the card may be recoverable or not, but you'll save yourself a lot of time and headache if you just return it as defective and exchange it for a new card.

then, when you attempt to format the new card, please see my [previous post](http://ubuntuforums.org/showpost.php?p=5348234&postcount=6) regarding the hal daemon.

---

### Post by LeDechaine on 2008-07-13
Yeah i'll exchange it and read this carefully, thanks. :p

---

