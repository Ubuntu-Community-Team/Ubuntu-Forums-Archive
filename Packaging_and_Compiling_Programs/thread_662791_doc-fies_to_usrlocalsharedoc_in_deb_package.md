---
title: "doc-fies to /usr/local/share/doc/ in deb package?"
date: 2008-01-09
forum: Packaging and Compiling Programs
---

### Post by Forlong on 2008-01-09
I managed to build my first deb-package today using dh_make and dpkg-buildpackage.
I chose to copy all files to /ur/local/ rather than /usr/ - which turned out fine in the final deb but the doc-files like *copyright* point to /usr/share/doc/

In which file of the *debian* folder do I have to specify I want those files in /usr/local/share/doc/?

---

### Post by dholbach on 2008-01-10
Why do you want to install stuff to /usr/local/? Debian/Ubuntu packages never put stuff there: [http://www.debian.org/doc/manuals/maint-guide/ch-modify.en.html](http://www.debian.org/doc/manuals/maint-guide/ch-modify.en.html)

---

### Post by Forlong on 2008-01-10
Because I had a source package available before that copied the files for the sake of clarity to /usr/local/

So I thought if people forget to 'make uninstall' that one and just install the "new" deb, it's best to keep the interference to a minimum.

And I used to have packages before, that did the same (Screenlets for example) - but thanks for the clarification, I will follow that in later packages.

---

