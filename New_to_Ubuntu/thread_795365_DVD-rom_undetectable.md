---
title: "DVD-rom undetectable"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-05-15
Put in my 8 GB flash drive. And tried to transfer files from my external DVD-Rom to the flash drive. But during transfer something went wrong and the files where unreadable. The trying to do the operation once more showed no files on the disc. I tried several discs and they all came out as empty. Can't unmount the device either. So pulled it out and put it back in. But no luck. Tried to mount it manually with:

```
sudo mount /media/cdrom0
```

which return: mount: special device /dev/scd0 does not exist

Which obviously is the wrong command.....or..I'm really not sure. Any takers?? 

Running Ubuntu 8.04 Hardy Heron (64), Gnome 2.22.1, Mem. 3.0 GB, AMD Athlon 64 3000+

External Sony 8x DVD-Rom

*SOLVED*

Rebooted the machine. The only thing that happened where that the external dvd-rom disappeared completely. Unplugged it and plugged it in again. Nothing happened. Turned it off and then on. Ejected the dvd disc. Shoved the disc back in est voila!! Success!!  :)

---

