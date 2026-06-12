---
title: "Nautilus (Files) and the Unity launcher when external partition is mounted."
date: 2013-05-21
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-05-21
Hi,

Not sure if this is a bug or a "feature" as nowadays gnome seems to come up with weird "features" in each new release. 

Anyway, here is my problem in Raring. Open nautilus, navigate to mount a partition in an external harddrive, then minimize Nautilus to the unity bar. Now if I click the "Files" icon (with the little right triangle beside indicating that it is in use) , it opens a new instance of Nautilus instead of restoring the one that has been minimized. This only happens when the minimized instance is for an external partition, if  I open directories in the installations' own file system then it doesn't happen, in that case when click on the icon it restores the minimized instance as expected.

I am on Raring, I am interested to know if there is any work around, and/or if a bug has been filed. 

Thanks.

---

### Post by mc4man on 2013-05-21
Don't know if there is a bug report but it seems to be a behavior/bug of the unity launcher, not nautilus.
(if I use another dock like plank then a min. naut window of another partition is always returned on left click.

---

### Post by monkeybrain2012 on 2013-05-21
No sure if it is Unity though. The problem doesn't arise with the patched version of Nautilus3.4 from SoluOS 

[http://www.webupd8.org/2012/08/install-solusos-patched-nautilus-in-ubuntu-1204.html](http://www.webupd8.org/2012/08/install-solusos-patched-nautilus-in-ubuntu-1204.html)

I will file a bug tomorrow, probably against both Nautilus and Unity.

---

### Post by sup on 2013-06-03
It is this bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1170647](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1170647)

---

