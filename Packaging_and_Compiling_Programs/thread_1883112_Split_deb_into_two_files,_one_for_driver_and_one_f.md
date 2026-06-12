---
title: "Split deb into two files, one for driver and one for apps?"
date: 2011-11-18
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-11-18
Building a .deb from source. The source tarball includes both the driver for a device and several applications that use the device. I've been using checkinstall to automagically create a .deb that contains both the driver and app. What is the optimal method for separating the driver and the applications into two separate .debs?

---

### Post by Bachstelze on 2011-11-18
The first step is to drop checkinstall and learn how to build proper packages

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

It can be overwhelming at first, until you have learned how all the parts work together. Don't hesitate to ask if you're stuck somewhere. ;) Also if you don't plan to have your package included in the official repos, you don't have to scrupulously follow all the formal rules about syntax; debian/copyright and whatnot.

---

### Post by djsephiroth on 2011-11-18
ooc, what makes checkinstall a Bad Thing?

The debs would only be used internally. Neither would do much other than drop some files in place and possibly run a single command post-install.

---

### Post by MG&amp;TL on 2011-11-18
Considering the huge amount of configuration involved in building a debian package, it's likely that a 'magic' app will make generalisations that should not be there. If it works, no reason why you can't use internally.

---

### Post by Bachstelze on 2011-11-18
> **djsephiroth said:**
> ooc, what makes checkinstall a Bad Thing?

Well, for one thing it can't do split packages (that I know of). ;) It's not a Bad Thing *per se*: if it works for you, great, just use it. But it doesn't work for everything.

---

### Post by djsephiroth on 2011-11-18
Thanks; those are both good answers.

---

