---
title: "TRIM, do i need to enable for all partitions?"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2014-02-23
HI, I just recently installed ubuntu on my ultrabook and learned about this TRIM thing thats needs to be enabled, I found these instructions on how to enable a scheduled trim:

[http://askubuntu.com/questions/18903/how-to-enable-trim](http://askubuntu.com/questions/18903/how-to-enable-trim)

my question is when you enable trim using this method is that it enabled for the whole SSD or do you need to somehow do it for each partition manually? 
besides the windows partitions I have the main Ubuntu partition and also one more partition which is a shared partition between windows and Ubuntu. (there is no swap partition)

Thanks in advanced.

---

### Post by erind on 2014-02-23
> **LinuxVirgin2000 said:**
> [...]

my question is when you enable trim using this method is that it enabled for the whole SSD or do you need to somehow do it for each partition manually? 
besides the windows partitions I have the main Ubuntu partition and also one more partition which is a shared partition between windows and Ubuntu. (there is no swap partition) [...]

These are a few things I've gathered from experience when trimming a *SSD* using **fstrim** command:

- Run **fstrim** for each partition individually,
- the partitions must be mounted,
- there is no need to trim the swap partition (if you had one) - that's already being done automatically by the system. From: [https://en.wikipedia.org/wiki/Ssd#Swap_partitions](https://en.wikipedia.org/wiki/Ssd#Swap_partitions)
> 
Swap partitions

    Linux swap partitions are by default performing TRIM operations when the underlying block device supports TRIM, with the possibility to turn them off, or to select between one-time or continuous TRIM operations.

Just make sure that all (windows or not) partitions have mount points and are* mounted* when you run the **fstrim** command on each of them. Then you can simply edit the cron script (the for loop) given in your link to fit your situation. In my case I have a simple script (in weekly cron) that does the SSD trimming efficiently.

---

### Post by Bucky Ball on 2014-02-24
You can also add 'noatime' as an option for each partition in /etc/fstab. You should do this anyway.

---

### Post by erind on 2014-02-24
Yes, forgot to add 'noatime'. Now that I'm looking at my fstab I see I left it there after removing 'discard'.

---

