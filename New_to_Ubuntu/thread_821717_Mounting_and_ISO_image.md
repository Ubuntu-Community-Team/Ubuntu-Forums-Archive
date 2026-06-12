---
title: "Mounting and ISO image?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by socngill on 2008-06-07
Trying to mount an ISO image I have but am not having any luck.  Tried using Gmount but I get an error message

An error occured
 not found

Not overly helpful!!  Is there anything else I could use instead, or does anybody know how to get this to work?

Thanks.

---

### Post by abn91c on 2008-06-07
did you burn to cd?

---

### Post by avtolle on 2008-06-07
Where is the image, e.g., on the Desktop? If it is then you will need to```
cd Desktop
``` then run the mount command.

---

### Post by thepipirate on 2008-06-07
> **socngill said:**
> Trying to mount an ISO image I have but am not having any luck.  Tried using Gmount but I get an error message

An error occured
 not found

Not overly helpful!!  Is there anything else I could use instead, or does anybody know how to get this to work?

Thanks.

What happens when you try mounting from the command line, i.e.,
```

mount -o loop yourimage.iso /mnt/yourmountpoint
```

?

---

### Post by ChompTheMan on 2008-06-07
You can mount ISO images with this command:

```
sudo mount -t iso9660 filename.iso /media/cdrom0 -o loop
```

This will mount the ISO image where your cdrom usually mounts, but you can mount it anyplace.  I created a folder in /media called *mount* for mounting ISO images.

To unmount:

```
sudo umount
```

---

### Post by saratchandra on 2008-06-07
I use [AcetoneISO]("http://getdeb.net/app/AcetoneISO") to mount and unmount images. It has gui to mount and create iso images. Not sure if its there in synaptic since I downloaded it from getdeb.net

---

### Post by socngill on 2008-06-07
> **saratchandra said:**
> I use [AcetoneISO]("http://getdeb.net/app/AcetoneISO") to mount and unmount images. It has gui to mount and create iso images. Not sure if its there in synaptic since I downloaded it from getdeb.net

Brilliant!  That is working.  Thanks very much.

Also a big thank you to everybody else who answered so quickly.  Regrettably I am still finding my feet when it comes to the Terminal.  I always seem to point it in the wrong direction :lolflag:

---

