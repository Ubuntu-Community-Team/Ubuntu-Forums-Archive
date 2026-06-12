---
title: "clueless as to how to use virtual Disk drives on linux"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Meow27 on 2008-05-30
hello again,

        not too long ago i remember looking at a post about a guy trying to install alcohol 120%, he wanted to use virtual disk drives so he didn't have to always use a real one.

he was told that he could make virtual drives on Linux without extra software(something like that) but i have no idea where the topic went (dunno what to search) and clearly don't know how to do this in Linux

anyone have the patience to teach me (or find an existing thread that answers my Q)

thanks in advance

---

### Post by Unix_Slayer on 2008-05-30
Try K3b. Granted, it is a KDE application, but it works...

---

### Post by quelx on 2008-05-30
[https://help.ubuntu.com/community/Mount#head-105a8515167c59d006614f5398c80b57883db36d](https://help.ubuntu.com/community/Mount#head-105a8515167c59d006614f5398c80b57883db36d)

For example in a terminal window
```
sudo mount -o loop myimagefile.iso /mnt
```

You will find the contents of the iso @ /mnt/

EDIT: to create an image file you can use

```
dd if=/dev/cdrom of=~/Desktop/myimagefile.iso
```

---

### Post by Unix_Slayer on 2008-05-30
[http://ubuntuforums.org/showthread.php?t=60423&highlight=alcohol+120%25]("http://ubuntuforums.org/showthread.php?t=60423&highlight=alcohol+120%25")

---

