---
title: "Can't Unmount Iso"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Iteria on 2008-07-18
I used gmount-iso to mount a ISO. It was an iso to game. I had to switch disks, so I tried to unmount the image using Gmount-Iso, but it would. When I cancelled the install and tried to unmount it again using Gmount-Iso and I failed. I tried to unmount it using the Nautilus "unmount volume" option and it gave me an error about the fstab.

I'm using Hardy. Does anyone know why this is happening and how I can fix it?

---

### Post by JagDragon on 2008-07-19
Try to do a forced unmount in a terminal.
```
sudo umount -f /path/to/mount
```

---

### Post by dexter.deepak on 2008-07-19
before trying the forced unmount stated above...first see if the drive is busy, if it is , try killing the process :
```
pkill <the name of your game>
```
or you can also try
```
ps aux
```
and see the pid of the used process, the simply do
```
kill <pid>
```
now i hope you can do a safe unmount !!

---

### Post by Iteria on 2008-07-20
I was able to forcefully unmount the image, but... I just feel like I shouldn't have to. I checked to see if the drive was busy and it wasn't. It's just weird and annoying. 

Maybe it's just Gmount-Iso? Does anyone know of another iso mounting utility?

---

