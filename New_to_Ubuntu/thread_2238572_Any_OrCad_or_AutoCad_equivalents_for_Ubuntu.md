---
title: "Any OrCad or AutoCad equivalents for Ubuntu?"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by robert237 on 2014-08-08
I am new to Ubuntu. For work I use OrCad and AutoCAD. Are there any equivalents available for Ubuntu either free or for at cost?

---

### Post by Vladlenin5000 on 2014-08-08
I'm completely out of my field of study, of my element in a nutshell, but I'll offer the free and open source QCAD (just for starters): [http://www.qcad.org/en/](http://www.qcad.org/en/)

---

### Post by ajgreeny on 2014-08-08
And **librecad**, but I am also out of my depth with any of the cad applications.

---

### Post by texaswriter on 2014-08-08
> **robert237 said:**
> I am new to Ubuntu. For work I use OrCad and AutoCAD. Are there any equivalents available for Ubuntu either free or for at cost?

DraftSight is freeware by Dassault Systems, makers of Solidworks. Available for Linux, Mac, and Windows. I use it on Ubuntu 14.04 [Unity] and Windows 7.

[http://www.3ds.com/products-services/draftsight/overview/](http://www.3ds.com/products-services/draftsight/overview/)


Free version allows you to open, edit, and save .dwg (and other formats). There is a professional version for Windows.

---

### Post by robert237 on 2014-08-12
All very good suggestions. Thank you Vlad, aj, and tex!!!
These will take care of the AutoCAD (for mechanical and line drawings) part.
The OrCad (for electrical schematic and Printed circuit board layout) will be a little harder to find.

---

### Post by texaswriter on 2014-08-12
> **robert237 said:**
> 
The OrCad (for electrical schematic and Printed circuit board layout) will be a little harder to find.

Two pieces of software for this:
Xcircuit and PCB
[https://en.wikipedia.org/wiki/Xcircuit](https://en.wikipedia.org/wiki/Xcircuit)
[https://en.wikipedia.org/wiki/PCB_%28software%29](https://en.wikipedia.org/wiki/PCB_%28software%29)

---

### Post by coldraven on 2014-08-13
Bricscad, although I have never tried it.
[https://www.bricsys.com/en_INTL/](https://www.bricsys.com/en_INTL/)

---

### Post by Rob Sayer on 2014-08-13
Depends on what you mean by 'equivalent'.  You can find programs that have the same functions more or less.  But if Autocad uses any proprietary formats you may have problems publishing something you've done in another program in autocad.  This is why Gimp is only a Photoshop substitute if you're a hobbyist.

---

### Post by Mike_Walsh on 2014-08-13
Hi, robert237.

For electrical circuit CAD work, have a look at QElectrotech, and also Cirkuit. I came across them a couple of months ago when I was searching for LibreCAD. (LibreCAD, too, is quite acceptable for hobbyist work, although it's a bit limited in what it will allow you to do.)

I don't know whether they would suit your needs, but they are both available in the Software Centre.

Also, have a look at OpenSCAD.

See what you think. I won't make firm recommendations, since I only use LibreCAD as an amateur.


Regards,

Mike.

BTW, Rob IS right. You may well find that you have equivalent functions, but specific formats may not necessarily work quite the way you expect them to, so.....be prepared to do some installing/uninstalling until you find one that DOES do what you require!

---

### Post by texaswriter on 2014-08-13
> **Rob Sayer said:**
> Depends on what you mean by 'equivalent'.  You can find programs that have the same functions more or less.  But if Autocad uses any proprietary formats you may have problems publishing something you've done in another program in autocad.  This is why Gimp is only a Photoshop substitute if you're a hobbyist.

Overall, you make a good point, but your conclusion is a bit ambiguous. Although off-topic, Photoshop isn't necessarily a better program because it has a highly proprietary format. I'm not going to go any further than that since it isn't relevant to the OP. 

 Same thing with Autocad, not necessarily a better program because it has a highly proprietary format. There was a library that had very good compatibility with saving to/from Autocad, but Autodesk went after them with extreme prejudice. Since then, there is legal precedent that would prevent Autodesk from going after somebody for maintaining interoperability. That said, there are plenty of *paid* versions that are equal or superior to Autocad. 

DraftSight (freeware) is really good (~ Autocad LT), and it works on Windows, Mac, and Linux. There is a professional version (~ Autocad), but it is Windows only. Also, it opens Autocad formats and writes to them fine.
Bricscad (proprietary/paid version) is also really good (~ Autocad), and it works on Windows and Linux. Same here, interoperability. 

LibreCad doesn't open up .dwg files, but does other formats (.dwf).

---

### Post by cwmoser on 2014-08-13
Autocad 14 runs well on Ubuntu:

$  wine  ./acad.exe

---

