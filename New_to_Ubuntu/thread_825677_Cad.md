---
title: "Cad"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by luke_1981 on 2008-06-11
I want to install ubuntu in my computer, i need to use autoCAD, so i want to know if there is an alternative software to autoCAD that allow me to modify and save dwg files...

---

### Post by dondos on 2008-06-11
DWG is a proprietary, binary, non-free, undocumented file format, controlled by a single software company. My advice is to avoid storing your drawings in this particular format. DXF is a much better alternative, as it is plain-text, well-documented, and a very widely used file format.

Open Design Alliance ([www.opendwg.org](www.opendwg.org)) maintains an alternative library for DWG read/write. See their site if it suits your needs.

Sorry for not answering your question. A few years ago I used QCAD for GNU/Linux, but not anymore. So I am still searching for a good AutoCAD alternative too...

Did I mention to avoid DWG? :-)

---

### Post by LowSky on 2008-06-11
You can try to install autoCAD with Wine, it might work...?

Or try QCAD, there is also sagCAD (only 2D), and Varkon. All 3 in Synaptic

---

### Post by aeiah on 2008-06-11
cad packages that are compatible with autocad are based off the intellicad framework. software that uses intellicad are fully compatible with autocad .dwg files. the bad news is, they're almost all windows based and none are free or open source. there's one that supports linux by packaging their software with a custom wine wrapper but from when i last looked, this were only compatible with older versions of autocad .dwg (2005 i believe), so you'll have problems using these in some instances. if you dont mind that, then look here:
[http://www.bricsys.com](http://www.bricsys.com)

it seems they stopped the linux version at v6 but i dont know if they plan to bring it in line with the windows version (v8.) at a later date. either way, its a commercial product.

---

### Post by atomkarinca on 2008-06-11
AutoCAD 2000 works without problems on Wine but I recommend using a native application. QCad is very good. I don't like SagCAD and others are not there yet.

As for dwg files, you can save your projects as dxf under AutoCAD or use [dwg2dxf]("https://sourceforge.net/project/showfiles.php?group_id=30996&package_id=40588") to convert your files.

---

### Post by mtcycler on 2008-09-03
I was a Autodesk AutoCAD operator, I don't claim to know it very well, but I have used it a little. When I switched to Ubuntu I tried to find an alternitive, the best by far that I found is Bricscad by Bricsys, based off of intelicad.  The linux version works with autocad 2004 and before, but not after, too bad. It has nearly all the same commands AutoCAD has and has the command line and saves NATIVELY to the DWG format.
The url is [www.bricsys.com](www.bricsys.com)
This is not a free software, but it is lot cheaper than AutoCAD, it costs around $250.
It comes in a .tar.gz or .rpm.

---

