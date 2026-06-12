---
title: "update"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by cosine352 on 2008-07-03
Hi All,
I have one question. Every time when we do update Ubuntu it downloads some packages. Does it download them temporarily or is it filling my hard drive?

Thanks in advance.

---

### Post by Can+~ on 2008-07-03
Of course it uses hard disk.

Most of them are security fixes, so they end up replacing a lot of old files with similar sizes.

---

### Post by woedend on 2008-07-03
It downloads them to a cache directory, then installs them.  So yes, the actual files are downloaded.  use the clean feature of apt-get to remove them.

---

### Post by iaculallad on 2008-07-03
The exact cache location for the downloaded package is in:

> /var/cache/apt/archives/

And to clean this folder from previous package update/installation, open your terminal and execute:

```
sudo apt-get clean
```

---

