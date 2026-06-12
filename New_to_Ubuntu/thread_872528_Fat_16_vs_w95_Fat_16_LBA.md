---
title: "Fat 16 vs w95 Fat 16 LBA?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-07-28
I did a search on the differences and was unsuccessful. My primary concern is if there is any compatibility issues between OS X, XP and Linux. 

But I but I would also like to know what the difference is. I formatted one drive for Ubuntu that read as formatted as Fat 16 yet when I popped in my untouched-by-linux USB it read W95 USB (LBA). 

Thanks!

---

### Post by candtalan on 2008-07-28
> **Lateforgym said:**
> I did a search on the differences and was unsuccessful

LBA is logical block addressing and it is likely that any hard drive of 8GB or above will be LBA capable. I believe that it will be hard to find one (of any size) which will not be. LBA uses a special look up table to access the hard drive, and is the way things work now. Your computer must be LBA capable too of course (BIOS), but most PCs still around, will be ok. There might be a bios setting though.

> My primary concern is if there is any compatibility issues between OS X, XP and Linux. 


I do not know about osx. I do not know of any compatibility issues with linux, and would not expect any. I have used some very old kit with linux, with no problems at all.

> 
But I but I would also like to know what the difference is.

LBA will be what is used nowadays. It might even be hard to get machines which will turn it off.

> 
 I formatted one drive for Ubuntu that read as formatted as Fat 16 yet when I popped in my untouched-by-linux USB it read W95 USB (LBA). 
Thanks!

USB sticks are usually FAT for simplicity and will probably be LBA whether they ask or not, or even tell you, I believe. Also for usb external hard drives.

BTW why did you 'format one drive for Ubuntu'? (as fat 16)?

If you are thinking of installing ubuntu somewhere, then keep in mind that it will make its own format and file system, a non windows type, all it needs is a hard drive (to take over completely) or an unformatted empty partition to install into. You do not usually need to do any formatting first.

Linux usually uses a file system called EXT3 which is superior to windows NTFS.

---

