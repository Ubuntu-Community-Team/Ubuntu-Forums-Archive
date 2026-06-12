---
title: "OpenOffice crashes reproducible"
date: 2005-02-26
forum: Repositories &amp; Backports
---

### Post by Sebastian Richter on 2005-02-26
Hi,

I have installed Hoary Array 5 from a cdimage, because I thought it would fix my openoffice, however :). 

But now, I have to see, that the very same bug occurs in a fresh Hoary install. I use OpenOffice 1.1.3. Maybe this is important for you:

seri@orion:~$ apt-cache show openoffice.org
Package: openoffice.org
Priority: optional
Section: editors
Installed-Size: 28792
Maintainer: Debian OpenOffice Team <debian-openoffice@lists.debian.org>
Architecture: all
Version: 1.1.3-2.3ubuntu8

The bug is that, whenever I mark multiple cells and try to move them, OO crashes with a unrecoverable error. Sometimes, my spreadsheets is recovered automaticaly after a new start of OO. I tried OO 1.1.4 from the OO homepage. This version works very well.

I now want to ask, if somebody has the same problems, so a more detailed bug report can be made. I can't imagine, where the problem could be, I mean, if it's something with my hardware or whatever :).

Thank you very much in advance,

Sebastian

---

### Post by Sebastian Richter on 2005-02-26
Uh, forgot to say that it's all about the OpenOffice.org Spreadsheet program.

---

### Post by wolovids on 2005-02-26
This might be the [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=4407) you are experiencing...

---

### Post by Sebastian Richter on 2005-02-26
Hi,

thank you very much. So, well, then I just add my report, too.

Bye,

Sebastian

---

