---
title: "I can't mount cdrom..."
date: 2008-12-02
forum: New to Ubuntu
---

### Post by darek_jestem on 2008-12-02
When i try to mount cdrom:
```
dariusz@dariusz:~$ sudo mount /dev/cdrom /japierdole

```
I have tha output:
```
mount: block device /dev/hda is write-protected, mounting read-only
mount: you must specify the filesystem type

```
I have to specify file system, what does it means?
Thank you for your answers;)

---

### Post by taurus on 2008-12-02
Try something like

```
sudo mount -t iso9660 /dev/cdrom /japierdole
```

---

