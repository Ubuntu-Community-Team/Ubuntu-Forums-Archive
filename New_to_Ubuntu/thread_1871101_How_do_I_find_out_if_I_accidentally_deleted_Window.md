---
title: "How do I find out if I accidentally deleted Windows when I installed Ubuntu?"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by timcd100 on 2011-10-28
I'm an absolute beginner who just downloaded Ubuntu 11.10 a week ago. I wanted to run both OS's side by side and be able to switch between them. I downloaded it from the "alternative downloads" section of ubuntu here: [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) 

During the installation the only question it asked me that seemed to pertain to running both Windows and Ubuntu seemed to be saying that I could make a decision later and that clicking yes or no wouldn't be doing anything permanent so I just clicked what seemed like the default.

Now I'm running Ubuntu and I have no idea how to switch back and forth between Windows and Ubuntu or if I accidentally deleted Windows during the partitioning maybe. How do I tell?

I'm using an HP laptop, AMD E-350 1.7 GHz.

EDIT: I attached a screenshot of the disk utility.

---

### Post by gandaran on 2011-10-28
looks like you formatted the entire disk to linux ext4 format so there's no windows ntfs partitions.
> During the installation the only question it asked me that seemed to pertain to running both Windows and Ubuntu seemed to be saying that I could make a decision later and that clicking yes or no wouldn't be doing anything permanent so I just clicked what seemed like the default.
the decision has to be made before starting the installing process.

---

### Post by 2F4U on 2011-10-28
From your screenshot I would agree that you dedicated the whole drive to Ubuntu and deleted Windows. If you want Windows back you need to do a fresh installation.

---

### Post by oldfred on 2011-10-28
Did you make the recovery DVD's and a Windows repair CD before installing Ubuntu? It looks like you overwrote the recovery partition also.

HP - Recover Windows Vista Operating System Using HP Recovery
[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00809678&lc=en&product=18703](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00809678&lc=en&product=18703)
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00810334&lang=en&cc=us&contentType=SupportFAQ&prodSeriesId=4078809&prodTypeId=321957](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00810334&lang=en&cc=us&contentType=SupportFAQ&prodSeriesId=4078809&prodTypeId=321957)

---

### Post by timcd100 on 2011-10-28
The reason I was cavalier is that this is a new lap top and I didn't have anything important on it. If there's no recovery partition it looks from the HP site that I'll need to order a re-installation CD. The only thing I'll lose is some firefox bookmarks.

---

### Post by oldfred on 2011-10-28
Did Ubuntu import the bookmarks?  You can save the Firefox profile for your next install.

---

