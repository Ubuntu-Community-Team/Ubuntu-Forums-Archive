---
title: "Trying to make amd64 Ubuntu packages"
date: 2005-11-07
forum: Packaging and Compiling Programs
---

### Post by wantilles on 2005-11-07
I am using the following How-To as a reference point:

**Debian New Maintainers' Guide**

[http://www.debian.org/doc/manuals/maint-guide/index.en.html](http://www.debian.org/doc/manuals/maint-guide/index.en.html)

and the following as a guide:

**How to make Debian standard packages from scratch**

[http://tamir.nooms.de/wiki/doku.php?id=guides:howto_make_debian_standards_packages_from_scratch](http://tamir.nooms.de/wiki/doku.php?id=guides:howto_make_debian_standards_packages_from_scratch)

I am starting with a fairly simple package that does not exist, either in Debian or Ubuntu - the x264 video encoding library with today's snapshot tarball.

I have attached two tarballs. The first contains my working debianized source directory just before I issue:

```
dpkg-buildpackage -rfakeroot
```

The second tarball contains the output files (deb packages) of the above command.

As you can see, while the library if flawlessly built with its full directory structure (fully adhering to Debian standards) under the **/debian/tmp/** directory, none of the files of this directory structure are included in the final packages.

I cannot figure out what is going wrong.

Any help would be greatly appreciated.

---

### Post by wantilles on 2005-11-08
Anyone?

---

