---
title: "SD Card Mounting Error"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by Ripp_Steakface on 2014-05-18
Error mounting /dev/sdb1 at /media/ripp/EOS_DIGITAL: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/ripp/EOS_DIGITAL"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'
.

So this is the error I get when I try mounting a SanDisk Ultra SDXC Class 10 64GB card on my Asus EeePC 900HA, shot with a Canon Rebel T2i. It says it has an unknown filesystem, so I'm not sure it's something I can get Xubuntu to read or of it's simply too large or fast of a card for this old netbook to read. It's fine if it can't be read but it would definitely be nice to be able to browse the photos.

---

### Post by sandyd on 2014-05-18
You will need to install the exfat drivers

```

sudo apt-get install exfat-utils exfat-fuse
```

---

### Post by Ripp_Steakface on 2014-05-18
> **sandyd said:**
> You will need to install the exfat drivers

```

sudo apt-get install exfat-utils exfat-fuse
```

It worked beautifully and I didn't even need to restart! Thank you so much!

---

### Post by n.e.t.gallatin on 2014-06-09
> **Ripp_Steakface said:**
> It worked beautifully and I didn't even need to restart! Thank you so much!
+1 Thank you

---

