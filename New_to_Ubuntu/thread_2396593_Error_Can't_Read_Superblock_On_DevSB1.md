---
title: "Error: Can't Read Superblock On Dev/SB1"
date: 2018-07-18
forum: New to Ubuntu
---

### Post by wpwend42 on 2018-07-18
Just got a System76 laptop last week running Ubuntu 18.04 with a 2TB SSD as an extra drive I am using as "cold storage" for files. This morning when I went to add something to it, the drive would not mount. The error I am receiving is...

Can't read superblock on dev/sb1

How do I fix this? Searching online is giving me results from many years ago and I want to make sure I using the most up to date solution. Thanks!

---

### Post by Autodave on 2018-07-18
Did the 2TB disk come with the machine or did you already have it?  That error* usually* means that either the disk has not been partitioned yet or the disk has called it quits.

---

### Post by wpwend42 on 2018-07-18
> **Autodave said:**
> Did the 2TB disk come with the machine or did you already have it?  That error* usually* means that either the disk has not been partitioned yet or the disk has called it quits.

It came with it...I fixed it using this set of terminal commands: [https://askubuntu.com/questions/1057266/error-cant-read-superblock-on-dev-sb1](https://askubuntu.com/questions/1057266/error-cant-read-superblock-on-dev-sb1)

Seems to be working fine now.

---

