---
title: "best format for pdf storage?"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by s1wood on 2013-02-27
I'm getting a 16GB SD card to double the storage space on my lubuntu netbook, it will just be used for storing my downloaded pdfs and occasional small image files. What is the best format to use for it? 
I'm looking for reliability as a priority, I won't be doing anything with it except reading and re-arranging files,it doesn't have to be used with Windows. 

Susan

---

### Post by Jonny87 on 2013-02-27
I'll admit I don't have much experience formatting sd cards for extra storage, so there may be some unknown issue that I'm unaware of.

If you know that you a sure it will never be used on a Windows system then a linux format (ext4) would do just fine. There are permission issues for somethings on ntfs.

---

### Post by Paqman on 2013-02-27
In your case it doesn't really matter what format you use. Cards generally come formatted as FAT32, which would work fine as long as you weren't storing any file larger than 4GB.

You can reformat into a Linux format if you like, but I suspect you'd get slightly less usable space on a more modern filesystem. The 4GB file limit is the only real problem with FAT32 on an SD card.

---

### Post by slickymaster on 2013-02-27
Even though FAT32 has the advantage of being recognized in many other systems and the data structures are simpler which might mean less writes on the SD card and less code being executed (unverified) and the are more tools available to recover information when it gets errors, I would go for ext4.

Ext4 is faster than FAT32, it supports owner/group concept and permissions and has support for hard/soft links, which is typically useful to avoid redundant copies of files.

---

### Post by schragge on 2013-02-27
@**Paqman**
+1. The short answer is that you probably shouldn't reformat your SD card because it is [optimized for FAT32](http://lwn.net/Articles/428584) that it comes preformatted with. There are [some recent efforts](http://lwn.net/Articles/518988) to make a flash-friendly filesystem for Linux, but it's still very much a work in progress.

---

### Post by s1wood on 2013-02-27
Thanks,
I'll leave it alone then.

Susan

---

### Post by x33a on 2013-02-27
In case you are feeling a bit adventurous, there's the new F2FS file system, which is especially oriented towards flash devices.

It's included in the 3.8 kernel.

Take a look here

[http://www.phoronix.com/scan.php?page=article&item=linux_f2fs_sdhc&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_f2fs_sdhc&num=1)

---

### Post by audiomick on 2013-02-27
> **x33a said:**
> In case you are feeling a bit adventurous, there's the new F2FS file system, which is especially oriented towards flash devices.


I think that is what this link deals with.

> **schragge said:**
> There are [some recent efforts](http://lwn.net/Articles/518988) to make a flash-friendly filesystem for Linux, but it's still very much a work in progress.

---

### Post by x33a on 2013-02-27
Sorry I missed it. It wasn't elaborate enough :P

Moreover, it has been included in the 3.8 kernel, which is a great news.

---

### Post by audiomick on 2013-02-27
> **x33a said:**
> 

Moreover, it has been included in the 3.8 kernel, which is a great news.

Yes, indeed.

---

