---
title: "Looking for Advice Regarding Proper Mounting of a Hard Drive Disk Partition"
date: 2020-07-03
forum: New to Ubuntu
---

### Post by michael-bielesky on 2020-07-03
Hi,

I split a 4 TB HDD into two 2 TB partitions (GPT table). I formatted one partition as an ext4 file system and I want to dedicate it to work done on Ubuntu. The 2nd partition might be used later for work done on Windows. I thought this will be safer than having one FAT32 formatted partition shared  by both operating systems. 

It makes sense to me to use PARTUUID a not UUID since the former is partition specific. I assume I will need to append the /dev/fstab file with:


PARTUUID=XXXX      /mydirectory       ext4      defaults,errors=remount-ro     0     2

And then use: mount -a

Before I do this I wanted to know if my thinking is correct. I guess I can also use the label name that I created for that specific partition. If I use UUID will I mount both partitions to the same point? Looking forward to your comments/suggestions!

Cheers,
Mike

---

### Post by TheFu on 2020-07-03
uuid is filesystem specific which is what you want.  We mount file systems, not partitions.  

Don't use FAT32 for any storage larger than 32GB.  For SSD or spinning HDDs to be shared physically by unplugging and moving to Windows, use NTFS.

What is GDP?  Perhaps you mean GPT?  When posting, it really helps to be 100% accurate or not say anything.

---

### Post by michael-bielesky on 2020-07-03
TheFu, sorry and thanks for noticing the typo. I edited my post. When I looked at the UUIDs using command <sudo blkid> I saw that only one of the partitions was assigned a UUID number. I was confused about this, but now it makes sense based on what you said and because the other partition is not formatted and therefore lacked a filesystem.

Cheers,
--Mike

---

### Post by ActionParsnip on 2020-07-04
The fstab entry looks fine to me. Using the UUID means it will always mount that partition where you say. Back in the day you'd use /dev/sdb1 (you can today if you want) but these could change

---

### Post by Morbius1 on 2020-07-04
The only advantage I can think of for a PARTUUID ( rather than a UUID ) is that since it is a partition table reference and not a filesystem reference should the partition be reformatted the UUID will change but the PARTUUID will remain unchanged.

---

### Post by TheFu on 2020-07-04
There are many possible options for how to decouple an fstab mount from the device names (sda, sdb, sdc, ...) that seldom, but may, change.

> **TheFu said:**
> uuid is filesystem specific which is what you want.  We mount file systems, not partitions.

I've never seen PARTUUID used anywhere. Mounts, references, anywhere.  In home systems, UUID is typically used unless LVM or ZFS are used.  But you can use any links that point to a device or mapped device (DM-*) under /dev/disk/by-* ... 

You can ignore the stuff below, unless you are interested in using a volume manager:

When I use LVM, I prefer to use the /dev/{VG}/{LV} mapping files. They clearly provide LVM information and are short. The device mapper sets those up automatically after any encrypted containers are properly opened. For example:
```
/dev/hadar-vg/root        /     ext4    noatime,errors=remount-ro 0  1
```
So, the VG is "hadar-vg" and the LV is "root."  If I do an ls in that directory, I'll see a other LVs:
```
$ ls -Fl /dev/hadar-vg/
total 0
lrwxrwxrwx 1 root root 7 Jul  4 01:35 libvirt-lv -> ../dm-2
lrwxrwxrwx 1 root root 7 Jul  4 01:35 lv-blog44-1604 -> ../dm-5
lrwxrwxrwx 1 root root 7 Jul  4 01:35 lv-lubuntu11-1604 -> ../dm-6
lrwxrwxrwx 1 root root 8 Jul  4 01:35 lv-opnsense -> ../dm-11
lrwxrwxrwx 1 root root 8 Jul  4 01:35 lv-regulus -> ../dm-10
lrwxrwxrwx 1 root root 8 Jul  4 01:35 lv-regulus-2 -> ../dm-12
lrwxrwxrwx 1 root root 7 Jul  4 01:35 lv-spam3 -> ../dm-8
lrwxrwxrwx 1 root root 8 Jun 27 17:36 lv-tp-lxd -> ../dm-16
lrwxrwxrwx 1 root root 7 Jul  4 01:35 lv-vpn09-1604 -> ../dm-3
lrwxrwxrwx 1 root root 7 Jul  4 01:35 lv-xen41-1604 -> ../dm-4
lrwxrwxrwx 1 root root 7 Jul  4 01:35 lv-zcs45-1604 -> ../dm-7
lrwxrwxrwx 1 root root 7 Jul  4 01:35 lxd-lv -> ../dm-9
lrwxrwxrwx 1 root root 7 Jul  4 01:35 **root** -> ../dm-0
lrwxrwxrwx 1 root root 7 Jul  4 01:35 **swap_1** -> ../dm-1

```
But the "root" and "swap_1" are the expected LVs for a system using LVM for storage management.

I use the LABEL= mount for portable USB storage so it gets mounted in predictable locations. Controlling the LABEL is easier and humans don't exactly think in UUIDs.

---

### Post by Morbius1 on 2020-07-04
Speaking of labels: Although it is rare to actually see one PARTLABEL can also be used to identify a partition. And like PARTUUID it has the same characteristic. Since it is a partition table reference to a partition reformatting the partition does not remove the PARTLABEL.

Just like using a PARTUUID in fstab however the only use case I can think of that this would be useful is if you routinely reformat partitions .... just because you like to mix things up a bit every now and then/

---

### Post by michael-bielesky on 2020-07-04
Thank you all for your comments. I've learned a lot here!

Cheers,
--Mike

---

