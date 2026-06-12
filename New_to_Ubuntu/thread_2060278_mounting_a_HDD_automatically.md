---
title: "mounting a HDD automatically"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by Spark_s on 2012-09-19
So I have been trying to mount a HDD on boot, for my MythTV box.  I hooked the HDD, use gparted and partitioned it as an ext3.  I then added to the /etc/fstab as
```
UUID="bf258e0b-cc25-4fb8-8d59-0ae8308abee5 /media/storage       ext3    defaults,errors=remount-ro      0       1
```

But when I do reboot I get the following:
```
The disk drive for /media/storage is not ready yet or present
```

I can mount it manually, but it won't perform it at boot. suggestions?

---

### Post by whatthefunk on 2012-09-19
> **Spark_s said:**
> ```
UUID=**"**bf258e0b-cc25-4fb8-8d59-0ae8308abee5 /media/storage       ext3    defaults,errors=remount-ro      0       1
```


No expert here, but I dont think that the quotation mark before the UUID number belongs there....

---

### Post by Spark_s on 2012-09-19
WOW...now I feel like an idiot, thanks for pointing that out.

---

