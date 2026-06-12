---
title: "editing pdf's in open office"
date: 2007-07-12
forum: Programming Talk
---

### Post by joshkrajnak on 2007-07-12
I was wondering if it's possible to edit pdf's in OpenOffice. Preferably with the similar style of Adobe's where you can add pages, and so forth. If there is not, how about an open source pdf editor? I need to make an application or a macro in the case of OpenOffice that will give similar functionality as Adobe Acrobat. I know this is somewhat out there, but I'm trying.

---

### Post by gpilkay on 2007-07-12
If you don't mind installing from a deb file (download, then double-click, like a Windows EXE), this isn't perfect but seems to work ok for me:

[http://www.getdeb.net/app.php?name=PDF+Editor](http://www.getdeb.net/app.php?name=PDF+Editor)

There's a lot of interest in portign this for Gutsey, and honestly, I hope they do.

However, I would advise you to print the PDF *to* a PDF (with CUPS-PDF or similar) because a lot of PDF files have odd codes that seem to mess up editing attempts.  Printed PDF files don't seem to have as many troubles.  Regardless, I'd make an unaltered backup copy before doing anything in case it won't open after editing.

---

### Post by aysiu on 2007-07-12
[https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)

---

