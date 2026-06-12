---
title: "adding new hard drive/controller"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by AnimalMagic on 2008-11-09
Ubuntu 7.10:

I've added a Sata controller and an unformated drive, but nothing new shows in df or gparted. Should I be doing something extra to detect the new disk? Shouldn't gparted at least show the unformated disk?

---

### Post by Peter09 on 2008-11-09
You can try two commands really

```
df -l
```

This should show you raw drive

or

```
lshw -C storage
```

shows you a list of detected hardware

if you cannot see the drive there then it may not be configured correctly or you BIOS may need to be set up.

---

### Post by AnimalMagic on 2008-11-09
Thanks for that. Wasn't sure of the commands, but I did have it right :-).

Neither of those show the Sata controller, even though the bios shows a message at startup indicating it's there... Presumably Ubuntu should detect the new controller at startup?

---

### Post by Peter09 on 2008-11-09
Yes,
be aware that some BIOS's will not display your SATA controller correctly. I think some provide options to show it as an ide drive (cannot remember details here). It is worth looking in your BIOS setting for this.

---

### Post by AnimalMagic on 2008-11-09
Thanks again.

It appears I have a duff PCI slot. I swapped the controller over and now it is happy and I can see the disk OK.

Regards

---

