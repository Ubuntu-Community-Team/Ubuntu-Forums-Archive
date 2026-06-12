---
title: "Ubuntu(new user)  - Support required for partitioning"
date: 2017-05-03
forum: New to Ubuntu
---

### Post by ag26 on 2017-05-03
Hi All, ):P

I have removed windows 10 & installed ubuntu 16.04 in my laptop (hp g6 pavillion 500GB) yesterday.

I need help in partitioning my hard disk.

My requirement is making two partitions. One for boot drive+applications (suggest what should be the ideal space for this - I am a general user-using gparted I have given size of 100 GB). The other for standard files (movies,music etc.- using gparted I have used balance 360 GB. Primary Drive type ext4 )There are 3 more partitions 3.5 GB swap. 3.5 GB additional files and 1 MB allocated space. I have disabled  LVM while installing.. 

Also while accessing thru disk app the file size is showing 485 GB but same file size in gparition is showing 460 GB. Can somebody explain.

Would appreciate your help.

---

### Post by oldrocker99 on 2017-05-03
Welcome to the forums!

The disk app shows the total number of **bytes**. The actual total is of **gigs**, which is 1024x1024X1024. I gig, not 1,000,000,000 bytes, is actually 1,073,741,824 bytes, which accounts for the lower number of actual gigs. Hard drive manufacturers use the same method of showing capacity, which confuses new users (as you were, no offense intended)

Partition your disk as / (root) (I use 32GB for root, you might want to make it, say, 48GB. 32 GB is plenty as far as I'm concerned), and mount the rest as /home, which will allow you to store whatever you want. It also makes reinstallation a lot easier, since you won 't have to restore your /home folder.

Let us know any time you have questions. We were all n00bs at one time.

---

### Post by ag26 on 2017-05-03
Thank you very much for your reply. 

I have reinstalled the os and created fresh partition of 50gig in /(root) and balance in /home and swap. For both partition selected logical volume & location of the new partition @"beginning of the space"

Hope it is alright!

---

### Post by oldrocker99 on 2017-05-03
> **ag26 said:**
> Thank you very much for your reply. 

I have reinstalled the os and created fresh partition of 50gig in /(root) and balance in /home and swap. For both partition selected logical volume & location of the new partition @"beginning of the space"

Hope it is alright!

It should be fine. BTW, the fewer gigabytes problem with hard drives is a mirror of RAM: the "8GB" RAM stick is larger than 8GB.

---

