---
title: "LVM enlarge disk volume"
date: 2021-06-16
forum: New to Ubuntu
---

### Post by tzung on 2021-06-16
Hi 
I suffer some problems and want to discuss with you.
I need to use LVM to enlarge disk volume.
When I operate LVM, I don't understand how to alter the volume of xvdb to xvda (xvda become 150 GB).
I need to expand the volume of xvda.
Could anyone please help me?
Thanks.

---

### Post by TheFu on 2021-06-16
expand the same VG onto 2 different disks, then use **lvextend -r** to increase the size of the LV.  It will automatically pull from where ever free space is available inside the VG.

BTW, this is dangerous. If 1 of physical storage devices fails, you'll lose all the data inside the VG. It will become unavailable.

Alternatively, you can use pvmove to relocate the PV (which includes the VG and LVs) to a larger storage device. Then use **pvresize**, **vgextend** and **lvextend -r** to access more of the available storage. Just be certain to make the partition used for the PV larger on the new disk before starting the pvmove.  I think these commands can be run while the system keeps working. Zero downtime.

Please post information using text-only, wrapped in code-tags like I'll do below. The information needed is:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo pvs
sudo vgs
sudo lvs
# and perhaps
sudo fdisk -l
```

---

### Post by rsteinmetz70112 on 2021-06-16
Is this LVM set to use RAID?

---

### Post by tzung on 2021-06-17
Hi
Thanks for your reply.

---

### Post by ActionParsnip on 2021-06-17
LVM is boxes in boxes. You have the group of disks that makes a pool. If you want to extend an LVM you need to add a new disk to the pool to grow it. Once you have space you can assign out then you can extend the disks that are on it that are provisioned to the OS. 
Once you have extended the disk then you can extend the partition in the OS so that it is then usable.
This explains it well 
[https://www.cyberciti.biz/faq/howto-add-disk-to-lvm-volume-on-linux-to-increase-size-of-pool/](https://www.cyberciti.biz/faq/howto-add-disk-to-lvm-volume-on-linux-to-increase-size-of-pool/)

---

### Post by TheFu on 2021-06-17
> **ActionParsnip said:**
> LVM is boxes in boxes. You have the group of disks that makes a pool. If you want to extend an LVM you need to add a new disk to the pool to grow it. Once you have space you can assign out then you can extend the disks that are on it that are provisioned to the OS. 
Once you have extended the disk then you can extend the partition in the OS so that it is then usable.
This explains it well 
[https://www.cyberciti.biz/faq/howto-add-disk-to-lvm-volume-on-linux-to-increase-size-of-pool/](https://www.cyberciti.biz/faq/howto-add-disk-to-lvm-volume-on-linux-to-increase-size-of-pool/)

This could be confusing to someone who had LVM added at install and didn't specifically want it.
LVM = PVs, VGs, LVs so while technically, adding a new disk may be required, we don't actually know that yet.  Proper use of LVM means only allocating the storage needed for a few months to each LV.

There are no partitions in LVM.  LVM sits inside partitions.

It is difficult to easily describe possible LVM setups because the system is extremely flexible. There are a few common patterns for using LVM on single disks, multiple disks, multiple disks with different RAID levels, and for moving where physical data is stored between different disks. LVM has tools for each of these. All very flexible, but flexibility brings complexity.

The link to [https://www.cyberciti.biz](https://www.cyberciti.biz) from ActionParsnip is one of the LVM guides I've used, but it really shows only 1 use. There are 50 other patterns for LVM.  Something that example shows, which I completely disagree about is they use the whole disks as a PV.  Never do that.  Always have partitions and always create a PV using a partition device, never the whole disk.  This rule applies to RAID as well. Every disk should have a partition table as a guide to what is located on that disk. Without one, we just have unorganized stuff and many tools won't know what is there.  It won't be bad from an LVM-use perspective, but if something bad happens 4 months later, do you think you'll remember how 1 disk is organized?  Is it RAID or LVM or something else?  With a partition table, preferably GPT, you'll be able to ask the disk (parted, gparted, fdisk, ....) and be told "LVM Member". No guessing required. In my home, there are over 30 HDDs/SSDs. I'm not counting virtual machine vHDDs.  I cannot possibly remember what each disk has on it. At work, it is much worse.  

For almost all my VMs, the host presents an LV as a block device to the guest VM. Here's the LV view from a VM host:
```
$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  libvirt-lv     hadar-vg -wi-ao---- 175.00g                                  
  lv-001         hadar-vg -wi-a-----  10.00g                                  
  lv-2104-srv    hadar-vg -wi-a-----  11.00g                                  
  lv-blog44-1804 hadar-vg -wi-ao----  16.20g                                  
  lv-regulus     hadar-vg -wi-ao----  30.00g                                  
  lv-regulus-2   hadar-vg -wi-ao----  10.00g                                  
  lv-spam3       hadar-vg -wi-ao----  10.00g                                  
  lv-tp-lxd      hadar-vg twi-a-tz--  32.23g             0.00   10.06         
  lv-vpn09-1804  hadar-vg -wi-a-----   7.50g                                  
  lv-xen41-1804  hadar-vg -wi-ao----  12.50g                                  
  lv-zcs45-1804  hadar-vg -wi-ao----  25.00g                                  
  lxd-lv         hadar-vg -wi-ao----  60.00g                                      
  root           hadar-vg -wi-ao----  32.33g                                  
  swap_1         hadar-vg -wi-ao----   4.25g                                  
  lv-backups     vg-hadar -wi-ao---- 465.72g
```
There is free space in the VG for a number of reasons. If needed, I could probably get 100G of storage back quickly from the SSD (hadar-vg).
Flexibility.

---

