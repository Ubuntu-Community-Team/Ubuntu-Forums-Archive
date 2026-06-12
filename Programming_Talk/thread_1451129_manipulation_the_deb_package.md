---
title: "manipulation the deb package"
date: 2010-04-10
forum: Programming Talk
---

### Post by 1991sudarshan on 2010-04-10
i want to know to manipulate the .deb package! i am using the kanjisaver as application instead as a screensaver i want to add navigation keys so that i cant change the displayed kanji rather waiting for the kanji to change by itself!!

---

### Post by nvteighen on 2010-04-10
The best way to do that is to download the **package's** source tarball (i.e. not the upstream source tarball, but the one you get by using apt-get source), make your modfications and then rebuild the .deb. This is because direct manipulation of the .deb (which essentially is a .tar.gz) may render it useless.

Look at the .deb packaging sticky for more information.

---

