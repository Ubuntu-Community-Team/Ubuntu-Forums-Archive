---
title: "Best DVD ISO Creator"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by AnimalMagic on 2008-07-02
So what is the recommended software for copying a DVD to ISO?

---

### Post by scragar on 2008-07-02
depends on what you want, the dd command will work for copying the DVD to an iso from the command line, while k9copy is great kde ap that works well. Ubuntu has the whole [right click -> copy dosk; to file] option. acidrip and dvd::rip are other programs that copy DVDs, although I have never used either of them.

---

### Post by Ryadt on 2008-07-02
k9copy works great for me..

---

### Post by WRDN on 2008-07-02
In Ubuntu, you can make an iso from the disk by right clicking on it, selecting "Copy Disk" and choosing "File Image" from the 'Copy to Disk' drop-down.
You can also use the command:

```
dd if=/dev/cdrom0 of=isofile.iso
```

In this case /dev/cdrom0 refers your CD/DVD drive.

---

### Post by AnimalMagic on 2008-07-02
> **WRDN said:**
> In Ubuntu, you can make an iso from the disk by right clicking on it, selecting "Copy Disk" and choosing "File Image" from the 'Copy to Disk' drop-down.
You can also use the command:

```
dd if=/dev/cdrom0 of=isofile.iso
```

In this case /dev/cdrom0 refers your CD/DVD drive.

Thanks for that. I had missed the right click option and assumed I needed a separate application. doh!

Regards

---

### Post by clive littlewood on 2008-07-02
I have found Brasero to work just fine and it is in synaptic.

Clive

---

### Post by Biggy on 2008-07-02
[ISO Master]("http://www.getdeb.net/download/2873/0")

---

### Post by BullButcher on 2010-02-07
Also try this one [http://old.getdeb.net/category.php?id=12](http://old.getdeb.net/category.php?id=12)

---

