---
title: "recovery softeare for external device."
date: 2013-04-16
forum: New to Ubuntu
---

### Post by ironman187 on 2013-04-16
Hey all, I made the mistake of doing a factory reset on my wife's new Samsung galaxy s3 android phone running 4.1.1. And deleting all her photos and videos of the kids. With earlier versions of android the phone's internal memory would show up on your pc as an SD card. With this version however, the internal memory only shows up as a media device. Since android is Linux based I'm under the impresson that I should be able to recover the pictures using Linux software. Does anybody have any suggestions? keep in mind that while I have dabbled in Linux, I still only know enough to break it.LOL. the phone is rooted BTW.

---

### Post by sydbat on 2013-04-16
Factory reset = no chance at recovery. Sorry.

I had to do a factory reset on my Android tablet and it completely erased everything. Fortunately, I made backups first.

---

### Post by ironman187 on 2013-04-16
Well, that's not entirely true. On an older android who's internal memory mounts as a disc, the data can be recovered with a recovery software provided that nothing has been written over those sectors. What I am trying to do is find a software that can search the internal memory on the Galaxy s3 but since android 4.1.1 does not mount the internal memory as a disk, that is proving to be difficult. Btw, my understanding is that the internal memory is not partitioned and is ext4. This means that most programs won't see it. The phone also won't connect to Linux. So, since android is Linux based, I figire there must be a workaround.

---

### Post by Mark Phelps on 2013-04-16
With all due respect folks, the OP has an S3 -- so telling them what used to work on older devices is useless. AFAIK, and I've looked since I too have an S3, there is NO Linux SW that will allow you to do data recovery of the phone's Internal file system.  There have been instances of recovering data from external SD cards, but that required inserting the SD card in a Windows PC and running Windows data recovery apps -- and as I have done that, as well, I can tell you that data recovery is spotty, at best.

With ICS, and now JB, Android USB Mass Storage is history  -- you get MTP or PTP.  There have been lots of posts on these forums about folks trying workarounds to the no-USB-MS problem -- and I've not seen any successes.

---

### Post by ironman187 on 2013-04-16
> **Mark Phelps said:**
> With all due respect folks, the OP has an S3 -- so telling them what used to work on older devices is useless. AFAIK, and I've looked since I too have an S3, there is NO Linux SW that will allow you to do data recovery of the phone's Internal file system.  There have been instances of recovering data from external SD cards, but that required inserting the SD card in a Windows PC and running Windows data recovery apps -- and as I have done that, as well, I can tell you that data recovery is spotty, at best.

With ICS, and now JB, Android USB Mass Storage is history  -- you get MTP or PTP.  There have been lots of posts on these forums about folks trying workarounds to the no-USB-MS problem -- and I've not seen any successes.

I've found a few promising links pertaining to connecting the S3 to Linux. I also took the SD card out of my wife's old phone (now serving as a wifi homephone) which was formatted several times. This is where all the pictures were originally before I moved them over to her S3, and since it was formatted at least three times during the rom swap I wasn;t sure if anything would be recoverable. As we speak I have recuvia recovering deleted files off of it. This looks promising, but I am continuing to research the ability to mount the S3 in Linux which should in theory allow one to perform a data recovery on it. These are the links I have found so far. 

[http://oliverkuster.wordpress.com/2012/07/13/galaxy-s3-access-files-in-linux/](http://oliverkuster.wordpress.com/2012/07/13/galaxy-s3-access-files-in-linux/)

[http://blog.kamens.us/2012/07/18/using-the-samsung-galaxy-s-iii-with-linux/](http://blog.kamens.us/2012/07/18/using-the-samsung-galaxy-s-iii-with-linux/)


[http://gunavara.blogspot.com/2012/11/samsung-galaxy-s3-vs-ubuntu-1204.html](http://gunavara.blogspot.com/2012/11/samsung-galaxy-s3-vs-ubuntu-1204.html)

---

