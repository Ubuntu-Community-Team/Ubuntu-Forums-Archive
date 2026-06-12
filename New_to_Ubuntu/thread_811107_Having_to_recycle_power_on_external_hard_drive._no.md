---
title: "Having to recycle power on external hard drive. normal or not?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by linuxinireland on 2008-05-28
Ok, I have an external hard drive, a western digital 500 GB.  Anyways, is there anyway to avoid having to recycle the power on it, if i switch the logged in user over.  I noticed I couldnt access it, but when i recycled the power, it worked fine.  Is there a simpler way to do this?

---

### Post by tamoneya on 2008-05-28
are you unmounting the drive before hand?  How is it formatted? NTFS? FAT32? ext3?

---

### Post by linuxinireland on 2008-05-28
i think its ntfs file system, but why would i unmount it, if i never mounted it? please tell me cause i thought i needed to mount it, but it just worked on its own.  All i did was plug in the usb.

---

### Post by linuxinireland on 2008-05-28
No one else knows huh?

---

### Post by tamoneya on 2008-05-28
i was under the impression that you:
mounted
used files
switched user
attempted to use
couldnt use
power cycled
mounted
used files

Is that correct because in the case the NTFS partition probably doesnt like being improperly unmounted and therefore wont mount again until you power cycle.

---

### Post by linuxinireland on 2008-05-28
ok, what exactly is the proper procedure of mounting and unmounting?

---

### Post by tamoneya on 2008-05-28
when you want to use a drive it needs to be mounted.  Sometimes it is done automatically.  This is how you do it manually.```
sudo mount -t ntfs /dev/sdb1 /place/to/mount
```Then you go to /place/to/mount and you will see your files.  When you shutdown or restart a computer it is automatically unmounted.  If partitions dont get unmounted properly they can get angry (and corrupted).  To do this manually you can do:```
sudo umount /dev/sdb1
```

---

### Post by linuxinireland on 2008-05-28
in your reply it clearly states, and i guess I'll quote " If partitions dont get unmounted properly they can get angry (and corrupted). To do this manually you can do: "
now correct me if im wrong, but the word partition is referring to a hard drive, with different "parts" a split drive if you will, but my drive is only one spcae, it is not partitioned, and also, you say i need to mount it by going to the terminal and typing stuff, but why would i do that, if a simple double click is all i need?. So, if i switch user accounts, my options are 
A: Go to the terminal and type " sudo umount /dev/sdb1 " OR
B: Reset the power on my External hard drive

I guess I'll stick with B

What im reall asking is, cant i mount the drive to any, all, or specific users, and swithc from account to account, without resetting the power.  isnt there a terminal command for that?

---

### Post by tamoneya on 2008-05-29
you have to have partitions on your harddrive.  In your case you just have one large partition.

---

