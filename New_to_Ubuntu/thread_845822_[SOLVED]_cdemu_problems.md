---
title: "[SOLVED] cdemu problems"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-07-01
I recently got the newest stable (1.1) of cdemu from launchpad. Since installing it I have already restarted but I cannot find how to start the program. Bash can't find cdemu or gcdemu (the GUI).
here's what I added to sources.list to download cdemu deb [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) hardy main

---

### Post by tosoth on 2008-07-13
You have to right click any gnome panel, choose "Add to panel" and find gcdemu on the list.

Then you have to start daemon:
```
$sudo cdemud -d
```

I don't know how to start daemon upon system boot.

---

### Post by hyper_ch on 2008-07-13
what do you need that for?

---

### Post by tosoth on 2008-07-13
If you ask me, I need it to mount some cd images with windows programs or i.e. images with DVD movies.

---

### Post by hyper_ch on 2008-07-13
```

mount -o loop -t iso9660 file.iso /media/iso

```

???

---

### Post by tosoth on 2008-07-13
Unfortunately some programs have to "think" they're being installed from CD. Mounting image as directory won't work.

And maybe one more thing... cdemu is really easy and comfortable to use.

---

### Post by fontenot_1031 on 2008-07-13
> **tosoth said:**
> You have to right click any gnome panel, choose "Add to panel" and find gcdemu on the list.

Then you have to start daemon:
```
$sudo cdemud -d
```

I don't know how to start daemon upon system boot.

Woo that got it going. Thank you sir.

---

