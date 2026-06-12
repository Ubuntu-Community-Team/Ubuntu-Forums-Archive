---
title: "can't format ntfs with qtparted"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by _zax_ on 2008-05-24
I'm trying to format the partition that has the winxp os [ntfs] and qtparted prompts

No Implementation: Support for opening ntfs file systems is not implemented yet.
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
No Implementation: Support for opening ntfs file systems is not implemented yet.

 Any other application or idea?

---

### Post by Sarah L on 2008-05-24
Gparted might be able to overcome this obstacle; I've had success in editing NTFS partitions with it. It comes with most Linux installation discs and exists as a LiveCD of its own. You can also install it from the repositories.

If you're still having trouble, there's a package that might be able to handle this for you: ```
 sudo apt-get install ntfsprogs 
```

---

### Post by logos34 on 2008-05-24
sudo apt-get install ntfsprogs

sudo mkntfs /dev/sda1

(replace sda1 with actual partition)

EDIT: I see SarahL has already posted, but I don't think ntfsresize will help--you want to format/erase the partition.  So mkntfs should work--I believe it will do a full-format by default unless you specify otherwise

---

### Post by _zax_ on 2008-05-24
> **logos34 said:**
> sudo apt-get install ntfsprogs

sudo mkntfs /dev/sda1

(replace sda1 with actual partition)

EDIT: I see SarahL has already posted, but I don't think ntfsresize will help--you want to format/erase the partition.  So mkntfs should work--I believe it will do a full-format by default unless you specify otherwise

2questions:
1.What i have to do so the sda1 [that now is ntfs] be formated ext3?

2.I saw with the gparted that sda1 has the flag 'boot', i have to make sda2 [that has the ubuntu] the flag 'boot'?

---

### Post by Sarah L on 2008-05-24
mkntfs creates an NTFS partition. I don't believe that this is what the original poster wanted.

To create an ext3 partition, you should use mkfs.ext3 - see [the manual page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?mkfs.ext3+8") for usage details.

---

### Post by logos34 on 2008-05-24
> **Sarah L said:**
> mkntfs creates an NTFS partition. I don't believe that this is what the original poster wanted.

mkntfs will format/overwrite an existing physical partition.  I assumed zax wanted to (re)format ntfs, since no other fs type was indicated. But I now see zax wants ext3

---

### Post by _zax_ on 2008-05-24
i've done it. now i have an ext3 partition, but because the owner is 'root' i cant use it. how can i change the permissions?

---

### Post by logos34 on 2008-05-24
> **_zax_ said:**
> i've done it. now i have an ext3 partition, but because the owner is 'root' i cant use it. how can i change the permissions?

sudo chown -R username:username /mountpoint/sda1

sudo chmod -R 755 /mountpoint/sda1

(substitute your actual mount point for '/mountpoint/sda1')

---

