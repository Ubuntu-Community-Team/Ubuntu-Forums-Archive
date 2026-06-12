---
title: "Badly partitioned drive"
date: 2021-07-02
forum: New to Ubuntu
---

### Post by jampants on 2021-07-02
I've accidentally created a partition scheme based off outdated information on the wiki and am now dealing with under utilized and full partitions, would there be any way to fix this besides fully resetting my computer

---

### Post by deadflowr on 2021-07-03
What wiki?
And does the partitioning look like?

Without knowing what the partition scheme looks like it's impossible for anyone to give a proper assessment of whether or not it can be fixed.
Depending on how it's laid out it can either be easy and relatively safe or very hard and with a high potential for serious risk.


Also, it might good to know if it's a Desktop system or a Server system.

---

### Post by Impavidus on 2021-07-03
It can be fixed without a complete reinstall, but, depending on the current partitioning and your wishes, a reinstall may be the easiest way to fix this. Can you enlighten us?

---

### Post by TheFu on 2021-07-03
The only answer is "it depends." We need some data. Run these commands and post the results.
```
sudo fdisk -l
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Very important to use 'code tags' when posting commands, especially those since they generate columns. [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

The fdisk output will be full of loop devices. Please, please, please, remove those. They have nothing to do with actual storage used at the level we need to work.
If any of the commands say "lvm member", then we also need these commands run:
```
sudo pvs
sudo vgs
sudo lvs
```
If LVM is used, we can very likely correct all sorts of things.  LVM brings great flexibility to storage management.  ZFS would too, but that will require a ZFS expert to help.

---

