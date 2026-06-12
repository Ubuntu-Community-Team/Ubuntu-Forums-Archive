---
title: "[SOLVED] files from cdrom to terminal"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by steve allen on 2008-05-13
How do I get files from cdrom into terminal

The cdrom is netgear windows drivers need to move .inf and.sys files to terminal so that I can use ndiswrapper to load.

Have tried loading with wine but terminal says that /home/s/.wine/drive_C/ does not exist

help

regards

steve

---

### Post by pedro_orange on 2008-05-13
Remember; case sensitive.

home/username/.wine/drive_c

If this does not exist run:

```
winecfg
```

in terminal.

---

### Post by BDNiner on 2008-05-13
CD ROM are usually mounted in /media/cdrom. if you cd to that directory you should be able to browse the cd.

---

### Post by Monicker on 2008-05-13
Normally your cdrom should get automatically mounted.

Try these commands:
```

ls /media/cdrom
ls /media/cdrom0
```


If either of those show the files you want then just
```

cp /media/cdrom0/file /home/username
```

afaik, wine is not a requirement for using ndiswrapper.

---

### Post by steve allen on 2008-05-13
Thanks to all I will have another go and let you know.

---

