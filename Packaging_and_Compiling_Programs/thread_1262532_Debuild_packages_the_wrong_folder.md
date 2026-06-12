---
title: "Debuild packages the wrong folder?"
date: 2009-09-10
forum: Packaging and Compiling Programs
---

### Post by korin43 on 2009-09-10
So I've been trying to make a package of Pidgin-facebookchat-1.61 for Jaunty. Everything seemed to work fine, but the .deb file was completely empty except for some generic documentation. I looked at the pidgin-facebookchat in the repository and it had:
```
	$(MAKE) DESTDIR=$(CURDIR)/debian/pidgin-facebookchat install
```
While I had:
```
	$(MAKE) DESTDIR=$(CURDIR)/debian/tmp install
```

I was under the impression that debuild was supposed to build the deb file from debian/tmp. I'm just trying to figure out what's going on..

(the package works now, I just want to know why the "official" folder is being ignored)

---

### Post by Brandon Williams on 2009-09-10
When I create the debian directory contents with dh_make -e and then used debuild to generate the deb file, it does what you see in the repository, using debian/<package-name> as the root of the tree for the contents of the package.

---

