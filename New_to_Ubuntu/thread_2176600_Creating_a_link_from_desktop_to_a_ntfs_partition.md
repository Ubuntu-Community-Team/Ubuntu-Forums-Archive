---
title: "Creating a link from desktop to a ntfs partition"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by dshgna on 2013-09-25
Hi!

As I am dual booting Windows 8 and Ubuntu 13.04, I would like to share some files between them. So I created a NTFS partition for such documents. 

I created a shortcut from my Desktop to a folder I use regularly. After rebooting, I get the error 

```
This link cannot be used because its target “/media/dshgna/2E24B20A007E4351/Chill” doesn't exist.
```

I think it is because the NTFS partition gets mounted under different names. What can I do to remedy this situation? I read aout editting the fstab file but I am confused so any pointers are greatly appreciated.

Thanks :)

---

### Post by Bucky Ball on 2013-09-25
What have you got in the fstab for it now, if that's how you're trying to mount it: at boot?

Give more detail. You say it is named differently in each OS? Further explanation, please. ;)

One clue you do give: You should be mounting it using the UUID, not it's location. Run:

```
sudo blkid
```

... and find the UUID for the partition. Then, in fstab, you want something like:

```
#Entry for /dev/**sd** **:
UUID=**1231231231233**   /mnt/**mountpoint **      ntfs    defaults,locale=en_AU.UTF-8     0       0
```

... where:

/dev/sd** should match the partition you want to mount (it is a comment only and this is for clarity: you can write anything there);
UUID=**1231231231233** = replace this number with the UUID of the partition, and;
 /mnt/**mountpoint ** should match the mount point you have created for it.

It looks like you have the UUID in the middle of everything here:

```
/media/dshgna/**2E24B20A007E4351**/Chill
```

Presuming I'm correct, you're looking for something like this in fstab:

```
UUID=**2E24B20A007E4351**   /media/dshgna/Chill      ntfs    defaults,locale=en_AU.UTF-8     0       0
```

Doing it this way the name of the partition doesn't matter (the partition is not actually named anyway and shouldn't matter regardless as the name you see for it is actually whatever you've named the mountpoint, in this case 'Chill'). You need to have ntfs-3g installed in Ubuntu to use NTFS.

---

### Post by Mark Phelps on 2013-09-25
Windows 8, unlike its predecessors, automatically hibernates when you shut it down -- unless you go to the trouble to disable fast startup.  When hibernated, the NTFS partitions remain mounted in Win8 and you will be denied access to them.

---

### Post by dshgna on 2013-09-25
Hi

ntfs-3g was in my ubuntu installation by default. I added the NTFS partition to my fstab. Here is the entry.

```
UUID=2E24B20A007E4351    /mnt/shared    ntfs    defaults    0    0
```

But the problem still persists. Namely I have a link on my desktop to a file in this ntfs partition. But I still get the same error I mentioned in the previous post.

---

