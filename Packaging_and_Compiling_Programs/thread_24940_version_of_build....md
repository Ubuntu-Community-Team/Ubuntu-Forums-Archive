---
title: "version of build..."
date: 2005-04-08
forum: Packaging and Compiling Programs
---

### Post by Bloody on 2005-04-08
How to establish the version of assembly??
ex.  mc_4.6.0-**1**_i386.deb

And I for example wish to put number 2 or in general something to write, how it to make??

PS: Can to whom it is interesting, I have collected mc with complete support utf8 ?  :-)

---

### Post by az on 2005-04-08
[http://www.debian.org/doc/manuals/maint-guide/ch-update.en.html#s-newrevision](http://www.debian.org/doc/manuals/maint-guide/ch-update.en.html#s-newrevision)

[http://www.debian.org/doc/manuals/maint-guide/index.ru.html](http://www.debian.org/doc/manuals/maint-guide/index.ru.html)


Did you use debhelper?


Also, the backports people may wat that...

---

### Post by Bloody on 2005-04-08
Thanks, has appeared all simply, was to change it in changelog file enough. Fairly - never would guess there to look.

---

### Post by az on 2005-04-08
Yes, using debhelper.  Otherwise (by hand) you need to add it to ther version in the control file.

---

