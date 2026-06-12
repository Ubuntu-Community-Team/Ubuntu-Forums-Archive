---
title: "huh?????????"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-05
how come every time I try to put a file larger than 713 mb anywhere! it says there is not enough room, no matter how much I delete?

---

### Post by dRock1286 on 2008-09-05
What are you running?

---

### Post by k3lt01 on 2008-09-05
Why is it people can't use a descriptive title? huh?

---

### Post by Crafty Kisses on 2008-09-05
> **hyperhopper said:**
> how come every time I try to put a file larger than 713 mb anywhere! it says there is not enough room, no matter how much I delete?

System specs and HD size would be much appreciated.

---

### Post by iaculallad on 2008-09-05
You could try posting whatever displays when you issue the command below on your terminal:

```
df -h
```

---

### Post by hyperhopper on 2008-09-05
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.6G  2.7G  675M  81% /
varrun________________252M  104K  252M   1% /var/run

varlock_______________252M     0  252M   0% /var/lock

udev__________________252M   44K  252M   1% /dev

devshm________________252M   52K  252M   1% /dev/shm

lrm___________________252M   38M  214M  16% /lib/modules/2.6.24-19-generic/volatile

gvfs-fuse-daemon______3.6G  2.7G  675M  81% /home/me/.gvfs

/dev/sdb1_____________2.0G  778M  1.2G  40% /media/disk

---

### Post by hyperhopper on 2008-09-05
is it the fact Im running wubi?

---

### Post by Elfy on 2008-09-05
No it's probably to do with only having 675Mb left on your ubuntu installation

3.6G 2.7G [COLOR="Red"]675M[/COLOR] 81% /

---

### Post by hyperhopper on 2008-09-05
ahhhh---how do I add to it?

---

### Post by Elfy on 2008-09-05
[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

It's in your other thread as well :)

---

