---
title: "Building frontend apps for OpenOffice Base odb files"
date: 2008-12-08
forum: Programming Talk
---

### Post by halfguard on 2008-12-08
*edit - originally I was looking to use OpenOffice odb files, but from what I've been reading I don't think that will be possible*

Sorry if this has been asked before. I searched, but didn't find anything. I'm looking for a language to write a simple graphical frontend for a local database. I'd be happy to use MySQL, SQLite, flat XML files, whatever is the easiest to learn. Any tutorials or books recommended?

I don't need a full blown IDE or anything. I'm fine with using a text editor to code. I'm just not sure what language / API is best for database access in Linux.

I'm an old MS Access / MS SQL programmer who spends most of his workday writing in either VBA or VB.NET, but recently switched to Ubuntu at home. I'm not necessarily looking to write commercial-level apps with a local database on the backend; just simple databases / frontends to play with around the house in my spare time.

Thanks in advance.

Jason

---

### Post by Zugzwang on 2008-12-09
OpenOffice odb files are actually zip archives containing a HSQLDB database and some additional information. If you have an OpenOffice odb file with all the necessary tables, etc., then you can just extract the zip file, use the HSQLDB library to add/remove some data from the tables and zip the stuff again (however you have to rename some files from the zip file in order to get this working correctly).

---

### Post by mike_g on 2008-12-09
I think SQLite would be a good choice for a lightweight desktop app. If you are not worried about the queries in your ODB or Access database you could always dump the sql and import it to SQLite. I have done it in the past and from what I remember it was not very difficult.

There are SQLite wrappers for lots of languages. If you want an easy language to work with Python might be a good choice. PyGtk is an easy to use gui toolkit and you can design your interface graphically with Glade. I made a simple DB app using SQLite+Pygtk not too long ago. If you like you can have a look at the source [here](http://grundez.net/subsites/classman/index.html).

---

