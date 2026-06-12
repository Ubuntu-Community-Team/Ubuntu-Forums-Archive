---
title: "What framework does Conky use?"
date: 2009-09-25
forum: Programming Talk
---

### Post by abeisgreat on 2009-09-25
I have a few ideas for software that would be integrated into the desktop like conky can be. So my question is, what framework or libraries is the conky UI based on, or for that matter what are some other good frameworks that will allow for that flawless integration into the background?

Thanks!
Abe Haskins

---

### Post by phrostbyte on 2009-09-25
Here is a trick:

I did this

```
apt-cache show conky
```

this is the output

```

Package: conky
Priority: optional
Section: universe/utils
Installed-Size: 560
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Kapil Hari Paranjape <kapil@debian.org>
Architecture: amd64
Version: 1.6.1-0ubuntu4
Depends: libc6 (>= 2.8), libcurl3-gnutls (>= 7.16.2-1), libglib2.0-0 (>= 2.12.0), libiw29 (>= 28+29pre7), libx11-6, libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxft2 (>> 2.1.1), libxml2 (>= 2.6.27)
Suggests: mpd
Filename: pool/universe/c/conky/conky_1.6.1-0ubuntu4_amd64.deb
Size: 196130
MD5sum: e4f82a5a5c8ad478d88d12b0915a1e8c
SHA1: 64163d3f911cf43c7797dbbe7ede8d1999e4bb7b
SHA256: cda413d196e24a3cc2b7c715c269c6d5c632d97e839ddb6d80ad574f00134c24
Description: highly configurable system monitor for X based on torsmo
 Conky is a system monitor for X originally based on the torsmo code.
 Since its original conception, Conky has changed a fair bit from its
 predecessor. Conky can display just about anything, either on your
 root desktop or in its own window. Conky has many built-in objects,
 as well as the ability to execute programs and scripts, then display
 the output from stdout.
Homepage: http://conky.sf.net
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

Notice "depends" list.

Now you can recursively use that same command to see what kind of libraries conky uses.

From what I saw, they are not using GTK+ or Qt, but rather Xlibs directly.

---

