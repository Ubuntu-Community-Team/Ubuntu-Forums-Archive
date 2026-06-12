---
title: "hal91"
date: 2007-08-02
forum: Other OS Talk
---

### Post by fistfullofroses on 2007-08-02
Seeing as HAL91 is no longer actively maintained, does anyone know how to go about updating it? [http://chris.silmor.de/hal91/](http://chris.silmor.de/hal91/)

I would love to have an updated version of HAL91 for rescue tasks, but I would also like to remove some packages and add others. I am also interested in adding kernel modules for new network adapters. Any help would be appreciated.

---

### Post by init1 on 2007-08-03
> **fistfullofroses said:**
> Seeing as HAL91 is no longer actively maintained, does anyone know how to go about updating it? [http://chris.silmor.de/hal91/](http://chris.silmor.de/hal91/)

I would love to have an updated version of HAL91 for rescue tasks, but I would also like to remove some packages and add others. I am also interested in adding kernel modules for new network adapters. Any help would be appreciated.

I was thinking of the exact same thing, actually. I wanted to add [robotfindskitten]("http://robotfindskitten.org/") to it. 
The version of Hal91 that is available now is different from the version I copied to a floppy awhile back. I like the old version because it has pico. In fact, I learned many things about Linux CLI from of Hal91 and other floppy distros. 
If you want to add things, the first step is to mount it. 
```

mount -o loop hal91.img somedir

```
I don't know what to do next. I do some research.

---

### Post by init1 on 2007-08-03
Try [Orange Linux]("http://orangelin.sourceforge.net/"). It is not compressed, so making changes is easy.

---

