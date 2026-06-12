---
title: "Accessing new logical drive."
date: 2012-07-22
forum: New to Ubuntu
---

### Post by pcal on 2012-07-22
Hi folks.

I've just used gparted to resize some partitions on my dual boot laptop (12.04 and xp). Soaked up some wasted space on the end of the xp partition to boost space on "/". Because I didn't want to risk moving the start sector of "/", I ended up with an unused 20gig just in front of the root partition that I decided to use as a manually mountable storage partition.

Formatted it ext4, rebooted the system and found it in the file system no problem at all.

The issue arises when I mount the partition. It seems I have no permissions at all to access it beyond mounting and unmounting. I don't intend for the partition to automount - happy to manually mount it when required - assumed I would have full permissions when I did so.

How do I go about making it so I do?

Thanks in anticipation

pcal

---

### Post by coffeecat on 2012-07-22
You simply need to chown the filesystem to your ownership You do this by mounting the partition and chowning the mountpoint, which has the effect of chowning the filesystem, not the mountpoint.

Mount the partition from nautilus and check what the mountpoint is with ctrl-L - it will appear in the location bar. I'll demonstrate the code with /media/mountpoint, but change this as necessary. Now open a terminal, and:

```
sudo chown yourusername: /media/mountpoint
```

Substitute your account name for "yourusername" and don't forget the trailing colon which will assign your default group. If you haven't saved any files yet to that partition, you don't need the -R recursive option. If you want others to have read-write access, then also do:

```
sudo chmod 777 /media/mountpoint
```

---

### Post by matt_symes on 2012-07-22
Hi

How are you trying you mount ? 

Are you trying to mount it through the terminal or using Nautilus ?

EDIT: Ninja'ed :)

As an addendum to coffeecat's explanation, give the partition a label and it's mount point will be that label.

Kind regards

---

### Post by pcal on 2012-07-22
Cheers Coffecat - worked like a charm.

Matt_symes, I'm mounting via Nautilus - but don't see any option to assign a label to the mount... Just shows up as "19GB Filesystem".

Is that a terminal only option?

---

### Post by coffeecat on 2012-07-22
> **pcal said:**
> Cheers Coffecat - worked like a charm.

Matt_symes, I'm mounting via Nautilus - but don't see any option to assign a label to the mount... Just shows up as "19GB Filesystem".

Is that a terminal only option?

You can assign a partition label with Disk Utility or Gparted. Disk Utility would be easiest as it's already installed. You don't have to use the terminal but if you do you use e2label if you know the partition device number.

---

### Post by pcal on 2012-07-25
> **coffeecat said:**
> You can assign a partition label with Disk Utility or Gparted...

All very simple when you know how.

Thanks guys - appreciated.

Pcal

---

