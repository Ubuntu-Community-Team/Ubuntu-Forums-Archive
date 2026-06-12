---
title: "Packge I would like reviewed"
date: 2008-02-15
forum: Packaging and Compiling Programs
---

### Post by volksman on 2008-02-15
I was wondering if someone could take a peek at a package I created for Geany 0.13 and let me know if I followed the correct procedure to package it.

This is a package from scratch type package and not an upgrade to the existing (hence minimal changelog).  However that will be my next step if I got this one right.

Please any feedback is appreciated.  I would love to be able to help more in this area...

Thanks!

Due to attachment limits I have put the file here: [http://nomad.ca/wp-content/uploads/2008/02/geany_013-1gutsy1_i386.deb](http://nomad.ca/wp-content/uploads/2008/02/geany_013-1gutsy1_i386.deb)

---

### Post by volksman on 2008-02-16
Anyone?

---

### Post by Vorian on 2008-02-16
> I: geany: arch-dep-package-has-big-usr-share 4024kB 72%
I: geany: hyphen-used-as-minus-sign usr/share/man/man1/geany.1.gz:17
W: geany: extra-license-file usr/share/doc/geany/COPYING.gz
W: geany: extra-license-file usr/share/doc/geany/ScintillaLicense.txt
W: geany: package-contains-empty-directory usr/sbin/
W: geany: readme-debian-contains-debmake-template
W: geany: description-contains-homepage

Do you have the complete source package anywhere?

---

### Post by volksman on 2008-02-16
Nice!  What program dumps that?

Yeah I have the source....Why do you ask?

---

### Post by Vorian on 2008-02-16
That was just a quick [lintian]("http://lintian.debian.org/") scan.  From the looks of the scan, you only need just a couple of fixes in your debain directory (you could probably remove the dirs, readme.debian, docs files, and fix up the copyright file a little bit.)

If you would like a full review, you can upload your package to [REVU]("http://revu.tauware.de/index.py"), where a MOTU can give you a proper critique.

actually, it seems geany is in Hardy.  You can compare your package with the one in the Hardy Universe 
[http://packages.ubuntu.com/hardy/devel/geany](http://packages.ubuntu.com/hardy/devel/geany)

---

### Post by volksman on 2008-02-17
Thanks a bunch Vorian!  Very helpful.  I'll review and submit to the proper channels... :)

---

### Post by SoulSmasher on 2008-03-21
the compiled c files' output is just empty, when i execute, output is nothing.. is that a bug from geany, or from your package?

---

