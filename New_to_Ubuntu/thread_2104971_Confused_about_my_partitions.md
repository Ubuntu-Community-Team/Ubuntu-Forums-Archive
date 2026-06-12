---
title: "Confused about my partitions"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by oxf on 2013-01-14
Please could someone explain this for me. 

When I installed 12.04 on another laptop it had a completely empty hard drive. I created a primary partition of 60GB as EXT4 at the start of the disk. I also created a swap partition of 1GB

I was just looking at the disk partition with Gparted before creating a new partion for a dual boot. This is what have:

/dev/sda1  60GB    EXT4
/dev/sda2  456MB Extended
/dev/sda3  1GB    Swap

What is sda2 Extended?  i didn't create it. Can it be deleted?

Sorry if this seems a silly question but I don't understand this!

Caitlin

---

### Post by Impavidus on 2013-01-14
An extended partition is a partition that can contain logical partitions. They have been invented to circumvent the limitation of 4 primary partitions per disk. In this case the extended partitions doesn't contain anything and is very small, so you can savely delete it. However, if you want to dual boot, you'll need several partitions. Having an extended partition with several logical partitions inside may be necessary and is certainly more flexible. It also sound like you've unallocated space left on your disk, or is it really just 62 GB?

---

### Post by oxf on 2013-01-14
> **Impavidus said:**
> An extended partition is a partition that can contain logical partitions. They have been invented to circumvent the limitation of 4 primary partitions per disk. In this case the extended partitions doesn't contain anything and is very small, so you can savely delete it. However, if you want to dual boot, you'll need several partitions. Having an extended partition with several logical partitions inside may be necessary and is certainly more flexible. It also sound like you've unallocated space left on your disk, or is it really just 62 GB?

Thanks.. I understand now. I didn't create it so maybe I hit the wrong key or something.

Oh yes I have lots of space left in fact most of the HD is unformatted at the moment!

---

### Post by oldfred on 2013-01-14
Usually swap goes into the extended just to create the extended and not use all 4 primaries.

Best to create a new extended (you only can have one extended partition and it counts as one of the 4 primaries). Then in the extended you can have as many logicals as you want. Linux works just fine from logical, it is Windows that only boots from primary partitions.

---

### Post by oxf on 2013-01-14
@ oldfred..
OK thanks I understand now. I doubt partitions will be  an issue for me.
1. Ubuntu
 2. Other Linux Distro
3. Swap
4.  .... free for whatever!

---

