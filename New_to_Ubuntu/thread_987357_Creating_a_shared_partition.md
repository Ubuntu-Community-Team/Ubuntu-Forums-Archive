---
title: "Creating a shared partition"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Sacrifice on 2008-11-19
I want to create a shared partition for Ubuntu and Windows. How would I create one?

---

### Post by MasterSander on 2008-11-19
Do you mean create two partitions? Just use the partition manager in the installer or download the Gparted live cd or do it in windows with diskpart.

---

### Post by Sacrifice on 2008-11-19
No. I have Ubuntu installed and connected to a separate partition. I want a shared partition for both Ubuntu and Window files.

---

### Post by MasterSander on 2008-11-19
Then use the gnome partition editor  or diskpart or gparted and create a new ntfs partition, or an ext3 partition, but then you'll need ext3 support in windows. [http://www.fs-driver.org/](http://www.fs-driver.org/)  --> This lets windows read ext partitions. Be sure to edit /etc/fstab after partitioning to mount the partition everytime you boot

---

### Post by taurus on 2008-11-19
Do you mean you want to shrink one of the partitions, making room for an additional partition to share data between Ubuntu & windows?

---

### Post by Sacrifice on 2008-11-19
Yes, Taurus. Nice post count. ^^

---

### Post by taurus on 2008-11-19
Well, it depends on how many primary partitions do you have right now.  Remember, you can only have 4 primary partitions and if you need more than 4, you need to make one of those 4 as an extended partition and then create logical partitions under that extended partition.  

So, what is the layout of your harddrive?

```
sudo fdisk -l
```

---

