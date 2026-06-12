---
title: "dsl error cant find knopix file system"
date: 2007-07-21
forum: Other OS Talk
---

### Post by jacob01 on 2007-07-21
i burnt a live cd of dsl and booted up to the cd and went into a limited kernal and said that it could not find knopix file system

---

### Post by init1 on 2007-07-24
```

sudo apt-get install qemu
qemu -cdrom thecdimage.iso

```
And then
```

qemu -cdrom /dev/cdrom

```
Tell me what happens.

---

### Post by jacob01 on 2007-07-25
i think i figured it out

on older kernals or distros it tries to load the file system and looks for the cd drive through the ide cable but since i have an sata cd drive it can not find and load the file system after it boots so it puts you into a verry limited shell

i found a site that talks a bout it happening with laptops that use 

[http://www.linuxquestions.org/questions/showthread.php?t=447438](http://www.linuxquestions.org/questions/showthread.php?t=447438)

it loads up the menu but then tries to detect the knopix file system but it cannot find it through the default location

---

