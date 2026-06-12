---
title: "Read Only File System"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by rromero143 on 2013-04-07
My internal hard drive is damaged and needs to be replaced. But first i need to put some files on a external hard drive. My problem is that whenever I plug in the hard drive my computer tells me "Error creating directory `/media/*computername*': Read-only file system". How do I change my file system back to read and write? Please help!

---

### Post by sandyd on 2013-04-07
> **rromero143 said:**
> My internal hard drive is damaged and needs to be replaced. But first i need to put some files on a external hard drive. My problem is that whenever I plug in the hard drive my computer tells me "Error creating directory `/media/*computername*': Read-only file system". How do I change my file system back to read and write? Please help!

You will have to boot up in a linux livecd to copy the files.
When the filesystem is damaged, the system mounts the drive as read-only, so Ubuntu cannot create a mount point for the external drive.

---

### Post by SeijiSensei on 2013-04-07
Have you run fsck against the drive yet?  Try booting up in safe mode, then running these commands 

```

cd /
mount -o remount,rw /
touch /forcefsck
shutdown -r now

```

This will remove the read-only lock on the root filesystem then create a semaphore that tells the system to force a filesystem check at reboot.

---

### Post by rromero143 on 2013-04-07
> **sandyd said:**
> You will have to boot up in a linux livecd to copy the files.
When the filesystem is damaged, the system mounts the drive as read-only, so Ubuntu cannot create a mount point for the external drive.

Thanks i do not have a live cd with me at the moment but i will try this when i do

---

### Post by rromero143 on 2013-04-07
> **sandyd said:**
> You will have to boot up in a linux livecd to copy the files.
When the filesystem is damaged, the system mounts the drive as read-only, so Ubuntu cannot create a mount point for the external drive.
when booted from a livecd how do i find the files on my computer because i don't see it in the home directory

---

### Post by rromero143 on 2013-04-07
Never mind I found it

---

