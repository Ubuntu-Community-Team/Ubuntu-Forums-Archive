---
title: "External Drive Unuseable"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-10-29
My old laptop just died while I was in the middle of installing Ubunutu (not related by the way, its time had just come). Anyway, I took the hard drive out and stuck it in an enclosure to get myself an 80 Gb drive. My problem is, when I plug it into my desktop, it sees the external okay, and shows me the folders from the Ubuntu install I was attempting, but it won't let me do anything with them, telling me I don't have permissions. Can anyone advise please?

---

### Post by vanadium on 2008-10-29
Clarify. Your post is confusing. If this is only about permissions, then you need to adjust the permissions. You need to be administrator (root) to change permissions. From what I understand, I cannot be more specific.

---

### Post by sdowney717 on 2008-10-29
from terminal type 
sudo nautilus

and it will give you root priveleges to the files.
you can also then perhaps adjust the properties on the folders on the drive.

When I have done this they dont take until after a reboot.

---

### Post by Nepherte on 2008-10-29
For graphical applications you better use gksudo:
```
gksudo nautilus
```

---

