---
title: "OLE2 Compound Document Storeage file..."
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Mike Krall on 2008-09-21
I have a file I'm trying to figure how to get open and haven't been able to do it. Would someone point me, please?

Name: VerticalForge.dft
Type: OLE2 Compound Document Storeage

Mike

---

### Post by vikramaditya on 2008-09-21
Doesn't look good :(

> File Type:  Solid Edge Draft Document 
Category:  Data Files 
Common? No 
File Description: CAD draft document created by Solid Edge 3D CAD manufacturing software 
Program(s) that open dft files:  Windows  UGS Solid Edge

---

### Post by Mike Krall on 2008-09-21
I got here

Unable to open Document
Unhandled MIME type: 'application/x-ole-storage'

from [URL="http://www.8daysaweek.co.uk/forums/viewtopic.php?p=2071&sid=c05ffa1b200

Don't know if I've gained any, or not...

Mike

---

### Post by vikramaditya on 2008-09-21
Here's [good news]("http://worldcadaccess.typepad.com/blog/2006/09/ugs_2d_solidedg.html") for accessing the .dft file.  The bad news is the FREE app will only install in winxp and you apparently have to run it from ie.

---

### Post by Mike Krall on 2008-09-21
That is good news and bad news... I guess I'm surprized CAD hasn't made it to Linux World. I've got a letter off to the send to see if there is a resolution from his end... thanks for the effor, 'vikramaditya'

Mike

---

### Post by Pa Blum on 2010-03-04
Geez!  Without my consent or even my knowledge, some of my Gnumeric spreadsheet files have been converted, or at least re-typed, as OLE2 compound files, so I have lost access to them.  What's going on here?  When is it happening?  Why is it happening?  I have NO trace of MS Windows on my system, so what's doing this to me?  This is valuable data becoming inaccessible!

(Incidentally, I've looked in the Ubuntu Software Center for anything that might serve to open these files, but nothing is offered.  If you think I sound panicky -- you're right.)

Thanks for any help,
Pete

---

### Post by earthdan on 2012-05-01
These may do the work.
1) [GNOME Structured File Library]("http://www.gnome.org/projects/libgsf/") &#8211; Can read Microsoft structured storage files.

2) [http://www.dimin.net/software/pole/](http://www.dimin.net/software/pole/)
3) [Pure Java implementation of the OLE 2 Compound Document format.]("http://poi.apache.org/poifs/index.html")

4) [OpenMCDF]("http://sourceforge.net/projects/openmcdf/") is a 100% .net / C# component that allows developers to manipulate Microsoft Compound Document File Format for OLE structured storage. It supports read/write operations on streams and storages and traversal of structures tree.(You may use mono runtime to run this, but i haven't try this on linux)

These software/library has **ability to read/write  OLE Structured Storage/ OLE 2 Compound Document format**

---

### Post by oldos2er on 2012-05-01
Closed. Please don't bump old threads.

---

