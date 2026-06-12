---
title: "RAID1 Parititons prior to installation"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by jwxie on 2011-09-21
I just created RAID-1 from BIOS, and right now disk0 and disk1 are mapped. 

I want to run Windows 7 and Ubuntu on the same computer using this setup. The problem I am facing is how to make partitions.

I like the idea of partition before installation. I boot into Gparted, and at this stage with RAID-1 in place, I am appalled to see dev/device-mapper/raid01, dev/sda, and dev/sdb shown in the drop down menu. 

The question is, which one do I select to proceed making partitions? I don't want to end up making partition, but RAID1 not in effect (even when it's set to RAID-1).

Can someone please help me on this?

Thanks!

---

### Post by dwasifar on 2011-09-21
/dev/device-mapper/raid01 is what you want.

/dev/sda and /dev/sdb are the component drives of your array.  dev/device-mapper/raid01 is the completed array.

---

### Post by Jagoly on 2011-09-21
just remember that grub cannot reside on a fake raid. If you raid was done by the bios, then grub will fail if there.

A fake raid is not a true hardware raid. a fake raid is just a software (using you're cpu's power) raid done in the bios.

If you weren't dual booting, then you would use a linux software raid. Unfortunately windows does not support these. I use one of these in my microserver.

So you need to remember to leave a small (< 100mb) non-raid partition for grub and /boot.

---

### Post by jwxie on 2011-09-21
**dwasifar**,
Thanks for the answer. I will check it out tonight. 

> **Jagoly said:**
> just remember that grub cannot reside on a fake raid. If you raid was done by the bios, then grub will fail if there.

A fake raid is not a true hardware raid. a fake raid is just a software (using you're cpu's power) raid done in the bios.

If you weren't dual booting, then you would use a linux software raid. Unfortunately windows does not support these. I use one of these in my microserver.

So you need to remember to leave a small (< 100mb) non-raid partition for grub and /boot.

Hi Jagoly, thanks. Now raid is set, how do I make that small non-raid partition, and is it done at the same time I create partitions using GParted? When it comes to Ubuntu installation (Win 7 first), do I need to create a boot partition for Ubuntu? 

My ideal setup:
```

500GB (in order)
  - 120GB Windows 7 (primary)
  - 120GB Ubunut (extended)
     -- unallocated 120GB
  - 120GB Personal (primiary, NTFS)
  - 120GB Programming (primary, NTFS)

```


Thanks.

---

### Post by Jagoly on 2011-09-21
Well, I'm pretty sure that a bios raid creates what appear to be physical disks, right?

So you would raid 1 the almost the entire disk, but leave 50mb on each disk. In a operating system (Linux or windows should recognise three unpartitioned disks. 50mb, 50mb and just under 500gb.

Now, use gparted to partition the big disk, exactly like you wrote. Then use gparted to add an ext4 partition to either of the small disks. Just leave the other 50mb blank.

Also I would not recommend directly using an ntfs partition created by gparted for windows. Let windows create it's own partition.

---

### Post by jwxie on 2011-09-21
> **Jagoly said:**
> Well, I'm pretty sure that a bios raid creates what appear to be physical disks, right?

So you would raid 1 the almost the entire disk, but leave 50mb on each disk. In a operating system (Linux or windows should recognise three unpartitioned disks. 50mb, 50mb and just under 500gb.

Now, use gparted to partition the big disk, exactly like you wrote. Then use gparted to add an ext4 partition to either of the small disks. Just leave the other 50mb blank.

Also I would not recommend directly using an ntfs partition created by gparted for windows. Let windows create it's own partition.


According to dwasifar's response, he said I should perform partition on dev/device-mapper/raid1  over  dev/sda and dev/sdb.

Now you are suggesting that:
```
(1) raid map the two disks from bios
(2) boot into gparted
       - for sda and sdb, create 50mb partitions and make them bootable
       - then if i want to create partitions for windows, ubuntu, etc, perform the partitions on Mapper
```

Is that what you are saying?
Because when I create the RAID-1 from BIOS, it will prompt "All the data will be loss after creating RAID-1, Y/N". So I assume that if we were to
```
    1. there is no raid-1
    2. partition 50mb for each disk
    3. now boot into bios and create raid-1
```
has no effect whatsoever?

Thanks!

---

### Post by Jagoly on 2011-09-22
Hmm...
I cant actually remember how fake raid handles leftover space. What I suggested was, starting with two completely blank hard drives, and for simplicities sake, I'll assume that they are bothe exactly 500,000mb.
From the bios, create a hardware raid1 volume on the disks of 499,950mb. Then from gparted partition one of the remaining 50mb sections for grub.

However, now that I think of it, that may not be an option. Fake raid is different to other true software raids.

Perhaps, if this is for a desktop system, buying another hard drive (or even SSD if you have the money) for the operating systems would be a good idea? Also remembering that software raid1 can often drastically harm performance when used for an OS. Then put important data on the raid1 partition.

---

### Post by jwxie on 2011-09-22
Hi. Thanks.
Yeah. The thing is I dont know what I can do with that spare 500GB now.

I don't really need RAID-1, but the two disks have been with me for a long time. 

What should I do, instead?
Thanks for all the help, however!

---

### Post by Jagoly on 2011-09-22
Well, if they are old(ish) hard drives, then perhaps RAID 1 is not a good idea?

If you have the money, than an SSD plus raid1 of the drives you have would be good.

If not, Why not just have the drives separate? Have the OS's on one, and excess data on the other?

---

