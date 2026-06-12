---
title: "mounting external hd`s"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by greg m on 2008-09-04
hello  i can not mount my 300 gig 5 1/4" hd i can mount a 2.5" hd.does anyone know why? usb sticks are no problem. what i seen in the forum is for people that dual boot.i keep all my hd`s, when i get rid of a computer. i would like to put my info from them on a external hd but it will not mount. why will the 2.5 mount but not the 5 1/4?

thank you greg m

---

### Post by drs305 on 2008-09-04
You should be able to mount this drive. With it plugged in, run and post the results of:
```

sudo blkid
sudo fdisk -l

```

Do you have an entry in fstab for this drive? If so, post the results of:
```
cat /etc/fstab
```

If you want to try to put it into fstab on your own please refer to the SDM link in my signature line.

---

