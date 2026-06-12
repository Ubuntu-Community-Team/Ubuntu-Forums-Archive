---
title: "Extract Here right click, not on .zip"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-10-08
The Extract Here option is not on my .zip files, and neither is the file-roller icon. I can double-click them to open with file-roller, but it doesn't get the icon or right click extract. It works fine with .rar and .tar.gz. Help please?

---

### Post by Joeb454 on 2008-10-08
Try installing [unzip]("apt://unzip") (that link should install it). It may appear after that :)

---

### Post by linkmaster03 on 2008-10-08
I had that installed. I reinstalled it, restarted GNOME. Nothing.

---

### Post by linkmaster03 on 2008-10-11
Anyone? :(

---

### Post by mc4man on 2008-10-11
You didn't say what ver. of ubuntu your running but the 'extract here' option should be available on .zip files.
maybe try doing a complete removal of file-roller and then an install.

You could use synaptic or run ```
sudo aptitude purge fileroller
```

Otherwise while it shouldn't be needed maybe try setting an association between archive manager and .zip. So right click on a .zip and choose 'open with' and pick archive manager from the list. ( really don't see why it would help, will give you a 'application/zip=file-roller.desktop' mimeapp  association.

---

### Post by linkmaster03 on 2008-10-12
Sorry, I'm running Ubuntu Hardy (8.04.1).

I tried purging file-roller, reinstalling, then restarting GNOME. No luck.

---

### Post by linkmaster03 on 2008-10-16
Bump. :(

---

