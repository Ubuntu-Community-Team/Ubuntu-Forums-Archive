---
title: "adding a 2nd hard drive"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by seanjuan on 2008-10-31
i am using Ubuntu Server 8.04 with the gnome environment and need to add a additional hard drive. How can I accomplish this?

---

### Post by Sarmacid on 2008-10-31
Do you mean mounting the disk? or resizing partitions? Or something else?:confused:

---

### Post by kpkeerthi on 2008-10-31
Connect the drive and find out if Ubuntu did recognize it. It should be listed when you run this command:
```
sudo fdisk -l
```

If it is not already formated, you may use [gparted live cd]("http://gparted.sourceforge.net/livecd.php") to partition it. Ubuntu Live CD has it already. You may use it as well.

To mount the new partitions, you need to edit your /etc/fstab per the instructions [here]("https://help.ubuntu.com/community/Fstab") in the WIKI.

---

### Post by Elfy on 2008-10-31
add it to fstab - then mount it

get the drive UUID label with ```
sudo blkid
```

Make a directory for it to mount in

```
sudo mkdir /mnt/foldername
```

Backup and edit fstab

```
sudo cp /etc/fstab /etc/fstab.3110
sudo nano /etc/fstab
```

Assuming that drive is ext3 add this - replace 'number'with the UUID - no quotes and foldername with name you give the folder

> UUID='number' /mnt/foldername ext3 defaults 0 2

Change permissions/ownership with chmod and chown.

This thread will show the detail for all filetypes and chmod/chown

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

