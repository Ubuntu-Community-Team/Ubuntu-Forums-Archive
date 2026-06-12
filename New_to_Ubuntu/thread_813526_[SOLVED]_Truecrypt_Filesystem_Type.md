---
title: "[SOLVED] Truecrypt Filesystem Type"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Michaelg14 on 2008-05-30
I just created an encrypted partition. When I tried to mount it I got an error message saying I had to specify the filesystem type.  How do I do that?  I am using version 5 on Hardy and would like to use the GUI of Truecrypt but there doesn't seem to be any way to tell it the filesystem type.

Thanks.

---

### Post by saj0577 on 2008-05-30
How did you create the encrypted partition?

Saj

---

### Post by Michaelg14 on 2008-05-30
I created an ext3 partition with gparted then created the encrypted partition with truecrypt as a FAT volume, all it would allow.

---

### Post by saj0577 on 2008-05-30
Okay.

I really need to head off to bed if no one else finds a solution I will continue helping in the morning.

Saj

---

### Post by saj0577 on 2008-05-30
Just try to provide as much relevant information as possible to help us help you.:)

Saj

---

### Post by Michaelg14 on 2008-05-30
Thanks for your assistance.  For further information I am using kernel 2.6.24-17 and Trucrypt version 5.1a

---

### Post by Michaelg14 on 2008-05-31
I got my volume mounted with a command line of $ truecrypt /dev/sda3 --filesystem=vfat

and it worked fine, I guess I will use it.  The problem is with Truecrypt so I will pursue it with them.

Thanks for your interest.

---

