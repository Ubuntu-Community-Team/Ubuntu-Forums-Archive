---
title: "how do i make a .img of a directory and mount it?"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-10-31
I can find how to make an iso(.iso) of a directory but the directory I want to image (.img) is my /home at 133.7 GB so that I can reinstall Ubuntu. Home is not on a separate partition so I can not use clonezilla

---

### Post by philinux on 2011-10-31
> **lance bermudez said:**
> I can find how to make an iso(.iso) of a directory but the directory I want to image (.img) is my /home at 133.7 GB so that I can reinstall Ubuntu. Home is not on a separate partition so I can not use clonezilla

If you just back up home to an external hard drive that should be enough. The new installer in 11.10 can preserve home even when not on its own partition. 

I always backup anyway even though my home is on its own partition :)

---

### Post by WasMeHere on 2011-10-31
Hi lance,

I think you can make a normal backup copy of your directory, or for example a tarball (compressed tarfile), because there are no secret files or files that must be in special positions in your home directory.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by lance bermudez on 2011-10-31
was told it was something

dd if=/dev/zero of=home.img bs=1&#653; count=1&#658;6908.8

but &#618; can not mount it with out a file system. So how do &#618; make an ext&#658; file system in the home.img?

---

### Post by WasMeHere on 2011-10-31
> **lance bermudez said:**
> was told it was something

dd if=/dev/zero of=home.img bs=1&#653; count=1&#658;6908.8

but &#618; can not mount it with out a file system. So how do &#618; make an ext&#658; file system in the home.img?

Don't worry about that command and making a file system inside the img file. There are tools, that can take care of your backup directly, and that will be much safer to use.

If you want a complete and easy to restore backup, you can make an image of your whole hard drive with Clonezilla. I do almost that once a month. Actually I make a Clonezilla image of the system partitions, while I make a syncronized directory copy with Unison of my multimedia partition.

---

### Post by matt_symes on 2011-10-31
Hi

> **lance bermudez said:**
> was told it was something

dd if=/dev/zero of=home.img bs=1&#653; count=1&#658;6908.8

but &#618; can not mount it with out a file system. So how do &#618; make an ext&#658; file system in the home.img?

To format it you could mount it as a loop device and format it that way but i am not sure why you want to do this.

BTW: Be very carful with the dd and mke2fs commands ;)

Kind regards

---

### Post by hailtothethief on 2011-10-31
> **lance bermudez said:**
> my /home at 133.7 GB

I guess no one else noticed this, but nice file size ;)

Anyway, [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) has a lot of good options, of which I personally choose to use tarballs (as was suggested by Olle Wiklund)

Good luck.

---

