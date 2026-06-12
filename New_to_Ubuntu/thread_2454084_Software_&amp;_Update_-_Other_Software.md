---
title: "Software &amp; Update - Other Software"
date: 2020-11-22
forum: New to Ubuntu
---

### Post by sofianito on 2020-11-22
Hi there,

I upgraded from Ubuntu 18.04 Bionic Beaver to Focal Fossa.

Shall I delete everything except:

Canonical Partners

[http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable)

Any help appreciated.
Thanks

---

### Post by sofianito on 2020-11-22
Help?

---

### Post by Impavidus on 2020-11-23
Deleting those sources will reduce clutter, but will also make it harder to add them back to your system. If you're sure you'll never need those sources again, you can delete them.

Have you still software from those sources installed? I see most are for bionic, but if a version for focal is available, you should change it to focal and enable the source again. Or delete the software that came from it.

---

### Post by CelticWarrior on 2020-11-23
This ^^^

In this situations I always whether or not the third-party repos (PPAs) already support the the new upgraded release. That being the case I re-enable them and edit out the "disabled on upgrade to...". I also remove all those remaining official repos for the old release just to have a clean house (they're not enabled so they do nothing but for cleanness sake I remove them all).

Most can be edited simply by changing the distribution field, in this case, from "bionic" to "focal". Others added by scripts or not following the typical Ubuntu PPA organization may need to be removed and re-added for the proper release. Examples are the repository for Mega.nz and your Dell repositories. Others like the Google Chrome one need no change.

---

