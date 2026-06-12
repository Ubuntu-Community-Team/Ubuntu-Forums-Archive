---
title: "gksudo nautilus problem"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by paulemony on 2012-09-28
Ubuntu 12.04

I have a number of directories on desktop which I want to delete. Each icon has the dreaded padlock, **Permissions** shows owner as root but **Folder Access** has **Create and delete files** greyed out. When I invoke **gksudo nautilus** & navigate to desktop the icons are no longer there. Where did they go, & how to get them back in order to get rid of them permanently?

---

### Post by tienlbhoc on 2012-09-28
gksudo nautilus can del any file or folder, you need go to nautilus (without gksu), ctrl+ L and copy link folder, and paste to gksudo nautilus, home in nautilus (gksu) is different with nautilus normal

---

### Post by paulemony on 2012-09-28
OK found it, use path **Home/file system/home/username/desktop** *not* just **Home/Desktop**. Of course!

---

