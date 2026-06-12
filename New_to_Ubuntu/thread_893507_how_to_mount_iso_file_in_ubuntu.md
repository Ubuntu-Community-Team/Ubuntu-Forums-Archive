---
title: "how to mount iso file in ubuntu"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by enri2 on 2008-08-18
easy plz

---

### Post by sisco311 on 2008-08-18
```
sudo mount *path/to/the/file.iso path/to/the/mount/point *-o loop
```

---

### Post by Majorix on 2008-08-18
> **sisco311 said:**
> ```
sudo mount *path/to/the/file.iso path/to/the/mount/point *-o loop
```

Make sure the mount point exists first.

Also add "-t iso9660" somewhere, because as far as I know you need a filesystem type with the mount command.

---

### Post by waspbr on 2008-08-18
no gui for this?

---

### Post by Majorix on 2008-08-18
There is the gmountiso in the repos, but I don't have good memories of it. If you are tired of writing the command you can make an alias out of it or something.

---

### Post by kreutzman on 2008-08-18
gmountiso has a GUI.

---

### Post by enri2 on 2008-08-18
thanks

---

### Post by kirsis on 2008-08-18
I suggest installing CDemu ([http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/) <- they have deb packages there, iirc). I find it very unobtrusive, easy to use and it supports mounting bin/nrg/other formats too (which you can't otherwise mount without converting)

---

