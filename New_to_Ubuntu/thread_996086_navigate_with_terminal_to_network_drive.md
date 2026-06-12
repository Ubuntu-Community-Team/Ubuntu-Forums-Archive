---
title: "navigate with terminal to network drive"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-28
I have 2 network drives attached to my network which i use to keep backups.
the address for one of them is
```
smb://lan-disk1/store1/
```

how do navigate to the directory store1 in a terminal?

---

### Post by a0u on 2008-11-28
Refer to: [http://ubuntuforums.org/showthread.php?t=875332](http://ubuntuforums.org/showthread.php?t=875332)

---

### Post by llamakc on 2008-11-28
You may use `smbclient` or `smbmount`.

[http://ubuntuforums.org/showpost.php?p=1637029&postcount=1](http://ubuntuforums.org/showpost.php?p=1637029&postcount=1) Goes into detail on how to do it.

---

### Post by sdennie on 2008-11-28
If they are already mounted via nautilus, you can also probably find them in ~/.gvfs

---

### Post by corkscrew on 2008-11-28
ah i wondered where .gvfs came from, i've been experimenting with grsync to do my backups to these networked drives and could'nt figure out where that came from. I guess it was as you say because i'd already browsed to the drive in nautilus

---

### Post by mopurizwarriors on 2012-09-21
> **sdennie said:**
> If they are already mounted via nautilus, you can also probably find them in ~/.gvfs

-------------------------------------------------------
It worked perfectly for me, thanks for the suggestion

---

### Post by nothingspecial on 2012-09-21
Old Thread.

Closed.

---

