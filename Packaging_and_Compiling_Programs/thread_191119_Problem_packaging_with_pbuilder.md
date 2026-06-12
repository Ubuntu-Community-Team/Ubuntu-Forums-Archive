---
title: "Problem packaging with pbuilder"
date: 2006-06-07
forum: Packaging and Compiling Programs
---

### Post by RAOF on 2006-06-07
Hi all.

I've been building gnash packages from CVS using dpkg-buildpackage, and they're working quite well.  However, I'd like to use pbuilder in order to make sure that other people can build the packages, and that they don't have spurious dependencies.

Now, I think I've got pbuilder set up fine.  I've been able to build some packages with it, but not gnash.  Gnash seems to be having trouble linking in the pbuilder environment.  Does anyone have any ideas here?  How might I be able to fix this?  I've attached the pbuilder buildlog (as a zip file, as it's rather large).

Thanks.

---

### Post by mlind on 2006-06-30
It looks like a bug in Gnash
[http://www.mail-archive.com/gnash@gnu.org/msg00454.html](http://www.mail-archive.com/gnash@gnu.org/msg00454.html)

I guess you must get it from cvs or just get Debian source package.

---

