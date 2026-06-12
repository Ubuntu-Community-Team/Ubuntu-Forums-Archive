---
title: "Convert a .nrg in a .img"
date: 2009-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by WitchCraft on 2009-03-18
If you want to convert a .nrg file to a .iso file you can use either:
```

dd if=image.nrg of=image.iso bs=100k skip=3

```

or use the nrg2iso tool to create this. nrg2iso is a program that extracts ISO9660 data from Nero &#8220;.nrg&#8221; CD-ROM ([http://www.debianadmin.com/howto-convert-a-nrg-nero-file-to-a-iso-file-in-debian.html](http://www.debianadmin.com/howto-convert-a-nrg-nero-file-to-a-iso-file-in-debian.html))


**Install nrg2iso in Debian**
 ```


apt-get install nrg2iso

```


**Usage**
 ```


nrg2iso [nrg-file] [iso-file]

```


**Example**
 ```


nrg2iso image.nrg image.iso

```

---

### Post by Psyphre on 2009-04-13
awesome thank  you very much for sharing that. I managed to convert an nrg file to iso.

Thanks again.

---

