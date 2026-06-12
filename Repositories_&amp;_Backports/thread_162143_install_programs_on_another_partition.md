---
title: "install programs on another partition"
date: 2006-04-18
forum: Repositories &amp; Backports
---

### Post by medya on 2006-04-18
I have two hard drives one is 4 GB the other is 40GB

I have installed Ubuntu on the 4 GB hard drive , right now 3.8 GB of my ubuntu partition been used,
is there any way to tell Ubuntu to install programs (like Media Players , or Amule or ... other thing that I order to install ) on my second hard dirve ?

+ my second hard drive (40 GB one) has two partitions one is NTFS and the other is FAT 16

---

### Post by fdoving on 2006-04-18
The short and easy answer is no.

The long answer is:

You can make a 'partition file' on one of the windows partitions. Since writing to NTFS is dangerous I suggest putting the file on the FAT partition.

Example: 

This is just to show you that it can be done, and how it's done. I do not recommend doing this unless you know what you're doing.


Say you want 2G extra space
Make the 2G file:
First cd to the folder where you want the extra space. In your case, somewhere on the FAT partition.
```

dd if=/dev/zero of=linuxspace.img bs=1024 count=2048000

```
This will take some time, it's filling a 2GB file (linuxspace.img) with zeros.
(You can calculate your own size with sizeinMB*1024, count=result)

Now create the filesystem in the file:
```

mke2fs linuxspace.img

```

Now you have a 2GB image file with a ext2 linux filesystem in it.
I assume you already have mounted your windows partition. And that it's auto mounted at boot time.

Edit /etc/fstab and add something like this to make it automount at boot:
```

/windowspartition/linuxspace.img  /space  ext2  loop,defaults 0 0

```

Now, mount /space.

Again, I do not recommend doing this if you're not sure what you are doing.
As an example moving /usr to a new device can break your system very much.

- Frode

---

### Post by medya on 2006-04-21
thanks , will the space be added to my whole Linux partition ? 

so my 4 GB linux partion would become 6 GB? with this mehod?
or it would be like a new partition.

---

### Post by fdoving on 2006-04-21
Like a new partition.

- Frode

---

### Post by medya on 2006-04-21
would linux automaticly use this partition , when the first one is full?

for example let say I have 20 mb free space on linux partition, and I want to install a  50 Mb Deb Package , will it install it on the new partition ?

if not , then whats the point of that, I can use the free space of the FAT drive by myself too

---

### Post by fdoving on 2006-04-21
No, it will not automatically be used. You'll have to mount it as /usr and move all /usr files over to the new partition to use it like you want. The point is that you can use a part of the FAT partition as a linux filesystem and have a ext2/3 partition image on it.


- Frode

---

### Post by medya on 2006-04-21
sorry for asking too much questions... 

whats the point of having linuxfilesystems on a partition ? I have mounted my FAT partition and it is working fine , I listen to my music theres ...

I guess , you mean that the linux files wont be runned in a FAT partition ...did I get it right?

another question , what is betetter ext2 or ext3 ?

---

### Post by medya on 2006-04-21
& another question  : what are those directories at linux's root for ...

for example what is USR for , what is OPT for , what ...blah blah for.

&anothe question : how I can mount that IMG file as a USR ?
should it be like this 
/windowspartition/linuxspace.img  /usr  ext2  loop,defaults 0 0

---

