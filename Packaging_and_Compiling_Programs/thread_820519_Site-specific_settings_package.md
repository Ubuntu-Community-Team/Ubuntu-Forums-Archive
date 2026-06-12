---
title: "Site-specific settings package"
date: 2008-06-06
forum: Packaging and Compiling Programs
---

### Post by pocketchange on 2008-06-06
I'm making site-specific modifications to a site-specific re-mastered version of Ubuntu.  I'm adding NIS support and need to append the "+" entry to the passwd, shadow, and group files.  I also need to do some changes to nsswitch.conf.  I also have to modify the /etc/apt/sources.list.  I wondered what the best way to modify these.  Do I modify the package each of these came with (i.e. modify the yp.conf in the nis package and then re-pack it)?  Or is it best for me to have one package that contains all my config files and deploy that (effectively overwriting the yp.conf, nsswitch.conf, etc from other packages)?  The idea of maintaining one site-specific.deb is much more appealing than re-packing (and maintaining) versions of nis, apt, etc.

I've read through the Debian admin guide and the maintenance guide and can't find any guidance on how this is supposed to work.

---

