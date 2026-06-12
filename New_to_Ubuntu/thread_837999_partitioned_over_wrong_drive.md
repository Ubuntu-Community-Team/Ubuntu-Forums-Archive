---
title: "partitioned over wrong drive"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by KCormier on 2008-06-23
Howdy all.  I did something really stupid.  I had a drive with all my data on it and messing with ubuntu 8.04 late one night I clicked partition automatically one night and low and behold, I just realized I lost ALL my data, no backups.  It was an xfs partition toward the end of the drive.  Any recommendations on how I may be able to recover some if not all of it?  It's the pictures I want back more than anything!

-Kevin

---

### Post by cariboo on 2008-06-23
You might want to give testdisk, It is available here:

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Jim

---

### Post by fatality_uk on 2008-06-23
That's an option, possibly. Assuming that nothing has written over those sectors, there is a slight chance you can get back a little.

---

### Post by forestpixie on 2008-06-23
Stop using the hardrive and access it from the livecd - you should be able to install it from the repo amd see if you can get at the data from there.

---

### Post by bumanie on 2008-06-23
Testdisk or photorec are your two best hopes of retrieving the data. Depsite photorec's name, it does recover files other than photos.

---

### Post by KCormier on 2008-06-23
Howdy all.  Got everything back using testdisk.  I lost one partition but thank god it was the one I didn't need!  Thanks all!  I got an external backup solution now...  I think I'm going to use ntfs unfortunately for windows compatibility but I'm not sure.  Any recommendations for file systems for an external drive?

-Kevin

---

### Post by zephyrcat on 2008-06-23
Glad you got your data back!

Here are the main options for external drives:
NTFS - Works with Windows and Ubuntu (through ntfs-3g), but not OS X
EXT3 - Works with Linux
HFS+ (or whatever the native Mac filesystem is) - Works with Mac OS X
FAT32 - Works with basically all OSs, but there is a file size limit of 4GB

So if you don't have any files bigger than 4GB and don't expect to in the future, FAT32 is probably best. If you do have files larger than 4GB, and you need compatibility with Windows, you should probably use NTFS.

---

