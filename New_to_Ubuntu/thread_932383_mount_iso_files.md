---
title: "mount iso files"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by gkraju on 2008-09-28
hi how to mount iso files in ubuntu 8.04 thanks in advance

---

### Post by howefield on 2008-09-28
One way is to install a package called gmountiso

From terminal type

```
sudo apt-get install gmountiso
```

Or install via Synaptic Package Manager.

---

### Post by unutbu on 2008-09-28
Open a terminal and type
```
sudo mount -o loop -t iso9660 filename.iso /mountpoint
```

---

### Post by gmconie on 2009-01-24
[http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2](http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2)

This tutorial is good.

---

