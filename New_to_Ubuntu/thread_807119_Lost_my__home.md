---
title: "Lost my  /home"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by natman on 2008-05-25
I am after reinstalling kubuntu and i wanted to keep my old home partition ( was separate )
So only asked to format the old "/" as ext3 and leave the rest alone, When i boot up i still can access my old "home" but i want to merge it back so thats its the current home ( which is new and blank )
I am willing to reinstall kubuntu again its still fresh

---

### Post by sisco311 on 2008-05-25
> **natman said:**
> I am after reinstalling kubuntu and i wanted to keep my old home partition ( was separate )
So only asked to format the old "/" as ext3 and leave the rest alone, When i boot up i still can access my old "home" but i want to merge it back so thats its the current home ( which is new and blank )
I am willing to reinstall kubuntu again its still fresh

open a terminal:

Applications -> Accessories -> Terminal

and post the output of this commands:

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by natman on 2008-05-25
Im sorry , for some resaon i cannot get my restricted nvidia driver working ! ( tried envy and stuff screen is stuck at 640 480 , using a different machine to do this )
Could you give me instructions on how to properly intstall my kubuntu, my partition list is as follows

sda1 ntfs
sda2 ext3 /
sda3 swap
sda4 ext3 /home

I want to wipe the sda2 and put a new kubuntu on it but have it use the old home in sda4.

---

### Post by nvteighen on 2008-05-25
Reinstall using manual partitioning.

There you'll be able to set sda4 as /home (without formatting it), and mark sda2 as / (and format it).

Of course, always backup your data first!

---

