---
title: "What is the linux equivalent of vss"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by ant2ne on 2011-12-21
[Volume Shadow Copies]("http://en.wikipedia.org/wiki/Shadow_Copy") aka previous versions is a pretty awesome feature in Windows file servers. But my file server runs linux with samba shares. How would I implement such a feature?

---

### Post by wildmanne39 on 2011-12-21
Hi, here is one link for it and you can see more just google the name and ubuntu and you will have plenty to read.
[http://www.wlug.org.nz/SambaShadowCopyHowto](http://www.wlug.org.nz/SambaShadowCopyHowto)
Thanks

---

### Post by ant2ne on 2011-12-21
that requires lvm. I was hoping there was a way to implement it without formatting. Apparently not.

---

### Post by anewguy on 2011-12-21
I didn't follow the link wildmanne39 provided, so perhaps it already covers this.  What you are talking about appears to me to just be simple raid - volume shadows.  Now perhaps that does require a format, but I thought that was purely a software implementation unless you go with actual hardware raid.  You may want to check out software raid for ubuntu.

EDIT:  Just re-read while checking threads I posted on.  Noticed your mention of Samba shares.  Don't know if my suggestion of raid even applies then.


Dave ;)

---

