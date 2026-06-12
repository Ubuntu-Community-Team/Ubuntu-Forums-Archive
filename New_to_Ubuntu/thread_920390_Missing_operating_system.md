---
title: "Missing operating system"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by CheesePlease on 2008-09-15
Hi, I have a feeling I have really screwed up. I attempted to install 8.04 on my Asus laptop dual booting with Windows Vista. Upon getting to step 4 out of 7 (the partition step) I messed around a little bit, mainly following steps outlined [here]("https://help.ubuntu.com/8.04/switching/dualboot-procedure.html"). I perhaps stupidly set the partition with Windows on it to /windows as I was unsure what else to do. After clicking continue and being led to the next screen with naming details I began having second thoughts as I was not sure what I was doing and I eventually exited the installer.

I hoped I hadn't screwed anything up too bad, but unfortunately when I turned my computer back on I am given the error message "Missing operating system". 

I'd be greatly appreciative of any information that could be given on getting Vista back. Thanks.

---

### Post by Lord DarkPat on 2008-09-15
Either your MBR is screwed up, or you made mistakes on the partition setup. Happens a lot to newbies, don't worry. I'm afraid you can't recover the Vista partition if you made a partitioning mistake, but if it's the MBR, then, it's your lucky day. Google Super GRUB Disc, download it, burn it, pop it into your drive, and see if it can restore your MBR. 
Good Luck!

---

### Post by bumanie on 2008-09-15
It sounds as though you have most likely got a corrupted partition table. Go [here]("http://www.cgsecurity.org/wiki/TestDisk") and download the live cd. If it is the partition table, testdisk should be able to recover it and re-write it. It can also recover whole partitions, if they have not been overwritten, so it is best that you only use the computer via a live cd of some description. Super grub disc is unlikely to help in this situation as you didn't get as far as installing ubuntu. Under certain circumstances, partitions can be rertrieved. There is a tutorial on the above site. Also there is an ubuntu program in the repositories that you should be able to get via th elive ubuntu cd called ntfsprogs. Part of ntfsprogs is a utility ntfsundelete that apparently is good at recovering accidentally deleted ntfs partitions - you could read up on ntfs undelete as well. Terminal code off the live cd to get ntfsprogs is sudo apt-get install ntfsprogs. Unfortunately, I have never tried ntfsundelete so can't give any specific help there. I have always used tesdisk with a good success rate.

---

### Post by volkswagner on 2008-09-15
+1 for testdisk, you can even install testdisk running on your current live CD.

---

### Post by fourthofjuly on 2008-09-15
> **CheesePlease said:**
> Hi, I have a feeling I have really screwed up. I attempted to install 8.04 on my Asus laptop dual booting with Windows Vista. Upon getting to step 4 out of 7 (the partition step) I messed around a little bit, mainly following steps outlined [here]("https://help.ubuntu.com/8.04/switching/dualboot-procedure.html"). I perhaps stupidly set the partition with Windows on it to /windows as I was unsure what else to do. After clicking continue and being led to the next screen with naming details I began having second thoughts as I was not sure what I was doing and I eventually exited the installer.

I hoped I hadn't screwed anything up too bad, but unfortunately when I turned my computer back on I am given the error message "Missing operating system". 

I'd be greatly appreciative of any information that could be given on getting Vista back. Thanks.
you only seem to have mounted vista so it doesn't look like you have lost it...

to check, boot from the live CD and see if it detects your Vista partition(s)...

cheers ! & please give Ubuntu a fair chance...

devang.

---

