---
title: "Is it possible to extract/build en (gentoo) ebuild"
date: 2006-09-11
forum: Programming Talk
---

### Post by djvishnu on 2006-09-11
I've got a patched versian of bioapi-1.2.2 ([here]("http://sejo.be/tmp/bioapi-1.2.2.tar.bz2")), but it is made by a gentoo dev and only in an ebuild format.

Is it possible for me to "extract" the right files and compile them? or is it easier to install the gentoo programs requierd to automate it.

Have anyone done this before? Any theories on where to start?

Thank you

---

### Post by nereid on 2006-09-11
An ebuild is a simple text file (nothing else than a bash script). You just need the source file and compile the source by hand (Portage, the Gentoo package manager, uses ebuild files to automate the compilation of the source files).

---

