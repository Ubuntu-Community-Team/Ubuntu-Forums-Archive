---
title: "Rhythmbox with patch."
date: 2012-06-01
forum: Packaging and Compiling Programs
---

### Post by melrokz on 2012-06-01
Hi all,

I've applied a patch to Rhythmbox and compiled it. Upon installing, it was the vanilla Rhythmbox, but the patch fixed my issue. 

1. I'd like to add the folder 'debian' in rhythmbox_2.96-0ubuntu4.debian.tar.gz for making ubuntu customizations to rhythmbox. How do I go about it?

2. I'd also like to package this into a .deb for easy install in my arch i386 systems.

Please advise.
Thanks in advance.

---

### Post by MadCow108 on 2012-06-02
the rhythmbox package is a 3.0 (quilt) package
so just do:

```
apt-get source rhythmbox
cd rhythmbox-...
export QUILT_PATCHES="debian/patches"
quilt import /path/to/your/patch
#apply the patch for testing
quilt push

```

and build it as usual (debuild -us -uc)

---

