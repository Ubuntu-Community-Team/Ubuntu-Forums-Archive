---
title: "Removing windows XP"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Julian Lewis on 2008-07-21
Hi,
I have a dual boot system, I would like to get rid of Windows XP and recover the space.
If I use gparted to turn the Windows NTFS partition into an ext3 partition, I can not access the partition for write. I deleted the partition completely, but then I can't boot at all. I tried reinstalling grub from the Live Ubuntu CD, but to make that work I had to put windows back again, and that worked... I nearly lost my Ubuntu installation, and that would have been a real problem. However I still have windows, and I cant seem to find a way to get rid of it.

So I guess I should do something like ...
1) Backup Ubuntu... obviously 
2) Do something to grub ?
3) Wipe out the Windows partition somehow ?
4) Do something to the MBR/Grub boot loader ?
5) Boot my Ubuntu only system
6) Mount the new empty first partition

I will run Windows under vmware or vbox on the rare occasions I need it. I need to turn the first partition into an Ubuntu partition, while still keeping my Ubuntu system on the second partition, and I will boot from the second partition.

Advice would be much appreciated ... The posts I find here are mostly the other way round IE going from dual boot to windows only, which is rather easy and straight forward using fixmbr.

Thanks

---

### Post by tuxxy on 2008-07-21
Run the LIVE CD, now run gparted and you should be able to remove the partition

---

### Post by sharks on 2008-07-21
First put ur Ubuntu live cd . boot it. then use gparted. format the partittion (windows and ubuntu). change it into ext3.  merge both partitions. then install ubuntu.


or wait for others advice.

---

### Post by vanadium on 2008-07-21
I understand that you are back to square 1, i.e., you can load both operating systems.

I think the reason you could not start Ubuntu anymore is because a partition was deleted. Grub looks for the "second" partition. After deleting your Win partition, your Ubuntu partition had become the "first" partition.

To get rid of Windows, just reformat the existing partition. 

> If I use gparted to turn the Windows NTFS partition into an ext3 partition, I can not access the partition for write.

The reason for this is that your ntfs partition was probably mounted. Before reformatting, you can unmount a partition from within gparted by right-clicking the partition and selecting "unmount". After that, you can reformat the partition to ext3.

In order to use the partition, you will need to mount it during startup by including it in /etc/fstab. If you want, we can help you with that, provided you post here (after you formatted your Windows partition to ext3) the output of the commands 

```

sudo fdisk -l
mount
cat /etc/fstab

```

---

### Post by Julian Lewis on 2008-07-21
> **tuxxy said:**
> Run the LIVE CD, now run gparted and you should be able to remove the partition

But how will I be able to reconfigure grub to boot only from partition 2 ?

---

### Post by Julian Lewis on 2008-07-21
> **sharks said:**
> First put ur Ubuntu live cd . boot it. then use gparted. format the partittion (windows and ubuntu). change it into ext3.  merge both partitions. then install ubuntu.


or wait for others advice.

That would delete my existing Ubuntu system that I have spent a lot of time setting up. I can't afford to delete my existing system, there is months of work in it.

---

### Post by Potatoj316 on 2008-07-21
All you have to do is use gparted from the live CD to delete the windows partition and expand the linux partition to fill the space.  Then find a tutorial (there are so many in the forum and web) that tells you how to install grub from that live CD (it takes less than 2 minutes)

---

