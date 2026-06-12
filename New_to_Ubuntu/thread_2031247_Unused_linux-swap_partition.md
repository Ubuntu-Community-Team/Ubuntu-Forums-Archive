---
title: "Unused linux-swap partition"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by Epith on 2012-07-21
Hello,

I'm working on an HP Pavilion dv9000, and I attempted to install Xubuntu when I first received it.  Xubuntu wouldn't work, so I opted for Puppy Linux, but got sick of it *very* quickly.

So, I installed Xubuntu off of the live usb (rather than my failed live cd attempt) and just finished re-partitioning the hard drive to get rid of puppy and create a full Xubuntu partition.  The thing is, /dev/sda5 (see picture below), the Puppy Linux linux-swap partition, remains.

I'd like to delete the partition so I don't ever get confused bewteen the Xubuntu swap and Puppy swap.  Is it safe to delete the Puppy linux-swap partition since it's not in use?

---

### Post by GreatDanton on 2012-07-21
Why do you have two swap partitions? You can have only one. I have one swap for multiple distros. If you are not using this current partition then it is safe do delete it, but first you have to unmount it. 

Edit: yes it's safe to delete puppy partition.

---

### Post by drs305 on 2012-07-21
You can delete this swap partition. Just make sure it isn't referenced in your /etc/fstab file.

---

### Post by Epith on 2012-07-21
No mention in fstab, so goodbye /dev/sda5! :D

Looks like I'll have to go into the live usb to delete the swap, it's telling me I have to unmount any partition having a number higher than 5, of which both my Xubuntu partition and linux-swap partition that I'm keeping are.

Thanks to both of you!

---

### Post by GreatDanton on 2012-07-21
Haha, good luck with deleting unused swap partition.

---

### Post by ajgreeny on 2012-07-21
Even using a live CD or USB you will need to right click on the unwanted swap partition and choose "swapoff" before you can delete it as live Linux systems are so clever they manage to find and use any swap partitions on the machine.

---

### Post by Elfy on 2012-07-23
> **GreatDanton said:**
> Why do you have two swap partitions? You can have only one. 

This is not true - if you have more than one swap - they will be used if the system knows about it.

```
cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/sda8                               partition	2302972	132	-1
/dev/sdc1                               partition	2440188	0	-2
```

---

