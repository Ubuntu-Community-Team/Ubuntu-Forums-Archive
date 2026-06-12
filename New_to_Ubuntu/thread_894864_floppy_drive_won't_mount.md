---
title: "floppy drive won't mount"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Matt26 on 2008-08-19
i cannot use my floppy drive in ubuntu 8.04.. whenever i put a floppy disk in the drive and attempt to open in i get the error message:

[B]Unable to mount location
No media in the drive[/B]

i am using a good floppy disk that has data on it (i have used it recently) and i have tried other floppy drives with the same result so i don't think it is a media or hardware issue.. plus the floppy drive will respond during the post process to check for any floppy boot disks..

anyone have any ideas what the issue might be here?

thanks.

---

### Post by ajgreeny on 2008-08-19
You have to actually mount the floppy first.  Try using the Disk Mounter in your panel.  It should allow you to mount a floppy easily, provided there is a good disk in the drive.  Or you can simply try ```
mount /media/floppy0
```Make sure you have the line

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

in your** /etc/fstab** file first, as I have in mine, put there automatically by the install procedure.

---

### Post by Matt26 on 2008-08-24
> **ajgreeny said:**
> You have to actually mount the floppy first.  Try using the Disk Mounter in your panel.  It should allow you to mount a floppy easily, provided there is a good disk in the drive.  Or you can simply try ```
mount /media/floppy0
```Make sure you have the line

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

in your** /etc/fstab** file first, as I have in mine, put there automatically by the install procedure.

i tried the terminal command that you suggested but i receive this error message:

**mount: /dev/fd0 is not a valid block device**

any ideas?

---

### Post by alienexplorers on 2008-08-24
In your media folder do you have a folder for floppy0.  If not make one and try the command again.

---

### Post by Matt26 on 2008-08-24
> **alienexplorers said:**
> In your media folder do you have a folder for floppy0.  If not make one and try the command again.

yes i already have a folder named floppy0 in the media directory..

is it possible that this may indicate a bad floppy drive?

---

### Post by alienexplorers on 2008-08-25
Could be or else if the floppies were made on a different machine the head may not align properly and you will get the error your getting.

---

### Post by Matt26 on 2008-08-25
> **alienexplorers said:**
> Could be or else if the floppies were made on a different machine the head may not align properly and you will get the error your getting.

i tried the floppy drive under windows xp with a few different floppy disks and it worked fine, so i guess this is specific to ubuntu..

the floppy disks that i have tried under ubuntu (same ones i tried under windows xp) were made under an old xp installation, but shouldn't ubuntu be able to read them anyways?

---

### Post by Matt26 on 2008-08-25
> **ajgreeny said:**
> You have to actually mount the floppy first.  Try using the Disk Mounter in your panel.  It should allow you to mount a floppy easily, provided there is a good disk in the drive.  Or you can simply try ```
mount /media/floppy0
```Make sure you have the line

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

in your** /etc/fstab** file first, as I have in mine, put there automatically by the install procedure.

i checked by fstab file and this line is already there:

[B]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
[/B]

should this work as is or would i need to modify this entry according to what you have suggested in order to get it to work?

---

