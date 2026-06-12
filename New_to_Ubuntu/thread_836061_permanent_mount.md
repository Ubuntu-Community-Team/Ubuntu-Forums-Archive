---
title: "permanent mount"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by _TED_ on 2008-06-21
Hello there!

I just created a new partition on my hard drive, but I can't mount it permanently. Every time I reboot, it needs to be mounted again. How can I solve this problem?

---

### Post by akiratheoni on 2008-06-21
Go to Applications -> Accessories -> Terminal and post the output of the following command:

```
sudo cat /etc/fstab
```

I'm not quite confident in my ability to continue so I'll leave it there but it's a good starting point so someone else can help you :P

---

### Post by forestpixie on 2008-06-21
It depends on what file system you have used as to how to make the necessary changes, can you do

```
sudo fdisk -l
sudo blkid
```

Post all outputs here please

@akiratheoni - you don't need sudo with that command :)

---

### Post by _TED_ on 2008-06-21
the file system is ext2 (I picked a diferent file system, but I formated it with mkfs...)

blkid:
/dev/sda3: UUID="06869d29-cf4d-45bf-9ce0-c579591dcda2" TYPE="ext2"

---

### Post by forestpixie on 2008-06-21
I assume that the syntax is the same for ext2 as ext3 but can't be sure

Make a directory for it, change 'name' to suit you for directory name and change fstab to match.

```
sudo mkdir /media/name
```

Backup and edit fstab

```
sudo cp /etc/fstab /etc/fstab.2106
gksudo gedit /etc/fstab
```

Add lines to end of fstab

> #/dev/sda3
UUID=06869d29-cf4d-45bf-9ce0-c579591dcda2 /media/name ext2 defaults 0 2

save and close file
Run these to mount and check whether it has mounted

```
sudo mount -a
mount
```

---

### Post by _TED_ on 2008-06-21
thanks a lot! It worked :):)

---

