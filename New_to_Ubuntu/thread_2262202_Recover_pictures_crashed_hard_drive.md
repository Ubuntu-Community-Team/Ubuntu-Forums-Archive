---
title: "Recover pictures crashed hard drive"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by nixpaints on 2015-01-23
Hello,
i am running windows 7 on a vaio laptop. Hard drive started making noise (sounds like skipping -doesn't stop) and got the error "operating system not found". The drive is recognized in BIOS. I booted up with ubuntu 14.04 from a flash drive in an attempt to copy and paste much needed pictures/videos. The hard drive is not being seen under devices. Where do I go from here? Any help is much appreciated 
Thanks

---

### Post by oldfred on 2015-01-23
You can try testdisk or photorec. But I think system has to at least see drive, but not necessarily partitions.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS

[/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]
[/URL]

---

### Post by nixpaints on 2015-01-23
What is a better recovery option for pictures/videos on a crashed drive, testdisk or ddrescue?

---

### Post by oldfred on 2015-01-23
ddrescue is just to image drive to another drive, so you can work on copy. If data vital that may be better. It does not get you any files.
Deep search in testdisk may show files. 
Photorec takes a long time, but is just a drive scan tools looking for anything that looks like a file. It does not recover full file names.

---

### Post by the3dman on 2015-01-23
PhotoRec listed above by oldfred is fantastic. Here is a link that lists all the file types recoverable by PhotoRec: [http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec) I personally have always used a live disc or usb with PhotoRec; however as noted by oldfred it does not recover full file names. It assigns new sequential names to the files it recovers.

---

### Post by Mark Phelps on 2015-01-24
Sorry, but if it actually is a "crashed" drive (i.e., suffered a head crash) there is NO software that will recover data from it, as it would need to be repaired first -- and that takes a "clean room" enviroment and typical costs start at $1000 USD.

---

### Post by philinux on 2015-01-24
> **Mark Phelps said:**
> Sorry, but if it actually is a "crashed" drive (i.e., suffered a head crash) there is NO software that will recover data from it, as it would need to be repaired first -- and that takes a "clean room" enviroment and typical costs start at $1000 USD.

I have to agree with Mark. Especially if ubuntu not even seeing the drive.

Testdisk and photorec have to be able to read the device. You could try the drive in another machine or caddy as a last resort.

---

