---
title: "install custom partitions.."
date: 2008-10-02
forum: New to Ubuntu
---

### Post by KS1987 on 2008-10-02
I want to install Ubuntu on 10 GB space. Can anyone suggest the recommended partitions? I've tried before "use the max available free space" and it ended up with me using a recovery disc for my Windows, so this time I'll try to play safe. Thank you in advance!

---

### Post by Paqman on 2008-10-02
That's a pretty tight install. I'd go for a single root partition (a separate home would probably waste space). The size of your swap depends on how much RAM you have and whether you need to be able to hibernate.

---

### Post by Patb on 2008-10-03
I second what Paqman says. It would help to know more about your system. How much RAM do you have? Do you want to be able to hibernate? Do you have storage space on the Windows partition where you might wish to save documents and files (ie dual access from Windows or Ubuntu)? 

Cheers, Pat

---

### Post by hyper_ch on 2008-10-03
on 10 GB

(1) set swap equal to your ram (at max. 1 GB)
(2) make no seperate boot partition - if you don't intend to do a fully encrypted install
(3) make no seperate /home partition but put everything in root "/"

that's what I'd do.

---

### Post by KS1987 on 2008-10-03
Hi everyone, first of all, thank you for your input. Here below are my spec's:
```
IBM Z61m | Intel® CoreTM Duo Processor T2500 - 2.0 GHz | 
3 GB DDR-RAM | ATI MOBILITY RADEON X1400 M54 / 
PCI Express x16 / 128MB GDDR1 | 100 GB HDD
```
I need 70 GB for my Windows partition, that is work related and I can't compromise on that part. I can however on the shared space between the operating systems. I heard about it before, but I didn't think about this possibility.

How does it work exactly? I've heard about making a seperate FAT 32 partition, linking the Vista folders to that partition. But how do I access them from Linux?

What I understood from the posts above, I should make two partitions. A root (which I can select when I use the custom method, no?) and a swap? Is that all, or is more needed? Thank you for your continuing input !!!

---

### Post by hyper_ch on 2008-10-03
with 3 gb ram you won't even need require a swap partition... so if you only dedicate 10gb to linux then I'd put everything in root "/".

Linux can read/write to ntfs... Windows can read/write to ext2/3 - Fat32 isn't required anymore.

---

### Post by KS1987 on 2008-10-04
It worked, thank you.

---

### Post by Paqman on 2008-10-04
> **hyper_ch said:**
> Windows can read/write to ext2/3

Quick point: you'll need to install [Ext2 IFS](http://www.fs-driver.org/) in Windows if you want to make this happen.

---

