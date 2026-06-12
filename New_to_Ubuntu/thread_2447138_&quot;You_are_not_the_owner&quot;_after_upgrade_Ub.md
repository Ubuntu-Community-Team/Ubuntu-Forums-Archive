---
title: "&quot;You are not the owner&quot; after upgrade Ubuntu 18.04 BIOS to 20.04 UEFI"
date: 2020-07-13
forum: New to Ubuntu
---

### Post by alexvucenovic on 2020-07-13
I wanted to convert a Ubuntu 18.04 BIOS to Ubuntu 20.04 UEFI. To do this in (what I thought was) the most efficient approach, I physically removed the secondary storage SSD and used the option to "wipe and install" Ubuntu 20.04. This process worked with one exception:

After physically reinstalling and mounting the secondary storage SSD, I am able to read it but do not have write privileges. I have subsequently tried to change ownership as root user to no avail:

```
sudo -s
chown -R username /storage
```

Looking for recommendations to restore access to this secondary storage drive without having to back it up, re-format it, and then transfer all of my content back.

Thank you

---

### Post by tea for one on 2020-07-13
Here is a guide.

[https://www.computerhope.com/unix/uchown.htm](https://www.computerhope.com/unix/uchown.htm)

There are some examples towards the end of the webpage.

I reckon you may need something like this:-

```
sudo chown -R  username:usergroup /storage

```

---

### Post by ActionParsnip on 2020-07-13
How are you mounting the storage please? If it is an entry in /etc/fstab can you please give the output of:
```

grep storage /etc/fstab

```
Thanks

---

### Post by Morbius1 on 2020-07-13
And if it is not in fstab how is this partition formatted:
```
sudo blkid -c /dev/null
```

---

### Post by alexvucenovic on 2020-07-21
```
grep storage /etc/fstab
```

returns

```
/dev/disk/by-uuid/B971-95FF /storage auto x-gvfs-show 0 0
```

and

```
sudo blkid -c /dev/null
```

returns

```
/dev/sdb1: UUID="B971-95FF" TYPE="vfat" PARTUUID="d248a510-01"
```

---

### Post by Morbius1 on 2020-07-21
Someone needs to make a concerted effort to remove Disks from the repository.
> /dev/disk/by-uuid/B971-95FF /storage auto x-gvfs-show 0 0


** Unmount the partition:
```
sudo umount /storage
```
** Edit /etc/fstab and change the line above to:
> /dev/disk/by-uuid/B971-95FF /storage auto [COLOR=#ff0000]**uid=1000,**[/COLOR]x-gvfs-show 0 0
I'm assuming your uid=1000. To make sure run this command to find out your real uid and change the above:
```
id
```
** Save fstab

** Remount with this:
```
sudo mount -a
```

---

### Post by TheFu on 2020-07-21
Non-Linux file systems like FAT32, exFAT, and NTFS don't support chown or chmod.  Those are Windows file systems.

All permissions for those file systems are set through the mount options.  That is a key understanding.

If this storage has a Linux file system, then chown, chmod, will work.  
Linux file systems include: ext2/3/4, zfs, jfs, btrfs, xfs, f2fs and about 50 others for specialized needs. In general, using ext4 is the best, default, for Ubuntu systems.

After a file system is mounted, the easy way to see the file system is 
**df -Th**  or   a plain **mount** though the output from mount is very _busy_.
Another option is **lsblk -e 7 -o name,size,type,fstype,mountpoint**

I use aliases for those commands so there isn't any need to remember them or type all that in.

---

