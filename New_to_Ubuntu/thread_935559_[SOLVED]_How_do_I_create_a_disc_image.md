---
title: "[SOLVED] How do I create a disc image?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-10-01
I want to make some disc images of cds I have. Specifically I want to make some images of my psx games so I can try them on my iPhone. Is there a program to make images on Ubuntu? I would like to make compressed disc images too. So all in all I would like to know how to make .ISO, .IMG, .BIN, .Z, .ZNX formats.

---

### Post by bangmalley on 2008-10-02
you can use Brasero (pre-installed) to create .ISO
1. Make Data Project
2. Drag files to brasero
3. go Project->Burn, and select Image File, click on Properties for more option

---

### Post by davidryder on 2008-10-02
Try this:

```
sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024 
```

Where file.iso is the name of the image you wish to create. 

```
man dd
``` if you want to read more about what **dd** does.

---

### Post by slughappy1 on 2008-10-02
So there is no way to make a compressed image?

---

### Post by Racecar56 on 2008-10-02
Only thing I can think of closest to that is a iso in a tar or similar. :/

---

