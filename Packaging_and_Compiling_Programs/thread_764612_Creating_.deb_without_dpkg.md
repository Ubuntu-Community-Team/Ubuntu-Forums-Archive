---
title: "Creating .deb without dpkg"
date: 2008-04-24
forum: Packaging and Compiling Programs
---

### Post by Mlehliw on 2008-04-24
I want to be able to create a debian package without having to use dpkg-deb --build or what have you. I can manually create the control and data tarballs and the debian-binary file easily and archive it with "ar" and use that as my debian package. I can install it with dpkg -i but if I use gdebi, it complains that my package is corrupted. I even tried un-archiving opera's deb file and re-archiving it and I got the same corruption error. Is it possible to create debian packages this way or will I have to resort to using debian's tools.

By the way my inspiration came from this site:
[http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/]("http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/")

Edit: the actual website I wanted to refer to
[http://synthesize.us/HOWTO_make_a_deb_archive_without_dpkg]("http://synthesize.us/HOWTO_make_a_deb_archive_without_dpkg")

---

### Post by soxs on 2008-04-24
```
./configure
sudo make depend && make
sudo checkinstall --fstrans=no
```

this will make a "dirty" package of almost *any* sourcecode.

---

### Post by RainCT on 2008-04-24
Quoting from the website you mention:

> But most important, I want to emphasize again that for Debian maintainers, packages are source packages, not binary packages. They never interact directly with the internals binary packages. In fact only 'dpkg-deb' and 'dpkg' developers need to know what they are. In fact it is not recommended to do so.

---

### Post by Mlehliw on 2008-04-24
Sorry I had the wrong website in my clipboard, this is the website I intended to reference.

[http://synthesize.us/HOWTO_make_a_deb_archive_without_dpkg]("http://synthesize.us/HOWTO_make_a_deb_archive_without_dpkg")

---

### Post by Mlehliw on 2008-04-24
> **soxs said:**
> ```
./configure
sudo make depend && make
sudo checkinstall --fstrans=no
```

this will make a "dirty" package of almost *any* sourcecode.
I am hoping to avoid using any "non standard" packages. The procedure in the website I listed uses standard gnu utils.

---

