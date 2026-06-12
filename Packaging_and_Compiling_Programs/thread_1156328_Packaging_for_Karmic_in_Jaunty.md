---
title: "Packaging for Karmic in Jaunty"
date: 2009-05-11
forum: Packaging and Compiling Programs
---

### Post by CHaoSlayeR on 2009-05-11
Hi there,

I'm currently packaging some SBLIM WBEM providers for Jaunty (could also backport it for Hardy). But the main problem is as that are completely new packages my goal is to get them into the universe repos for the upcoming Karmic Koala.

But as I don't have a Karmic Koala installation yet here is my question:

Is it possible to package for Karmic when actually running Jaunty?

As I already use **pbuilder** and its **pdebuild** I thought it would be possible to do that. Without success. Or is it safe to just add a link in /usr/share/debootstrap/scripts/ for karmic?

Thanx,

C]-[aoZ

---

### Post by Vorian on 2009-05-12
> **CHaoSlayeR said:**
> Hi there,

I'm currently packaging some SBLIM WBEM providers for Jaunty (could also backport it for Hardy). But the main problem is as that are completely new packages my goal is to get them into the universe repos for the upcoming Karmic Koala.

But as I don't have a Karmic Koala installation yet here is my question:

Is it possible to package for Karmic when actually running Jaunty?

As I already use **pbuilder** and its **pdebuild** I thought it would be possible to do that. Without success. Or is it safe to just add a link in /usr/share/debootstrap/scripts/ for karmic?

Thanx,

C]-[aoZ

yes, you can use a karmic pbuilder in inrepid (or earlier if you'd like)

You need to enable backports and upgrade your debootstrap so you can get the karmic script.  Once you do that, simply do "sudo DIST=karmic pbuilder create" and you are all set.

Unless you fix your pbuilderrc to do otherwise, you will need to use "sudo DIST=karmic pbuilder build *dsc" to have pbuilder do that.

Here is more information on multi distro pbuilder management.    [https://wiki.ubuntu.com/StephenStalcup/PbuilderFoo](https://wiki.ubuntu.com/StephenStalcup/PbuilderFoo)

---

### Post by CHaoSlayeR on 2009-05-22
Thanx

This saves me a lot of time plus a partition.

---

