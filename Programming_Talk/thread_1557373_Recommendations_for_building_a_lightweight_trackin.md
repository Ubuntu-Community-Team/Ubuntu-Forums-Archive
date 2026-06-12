---
title: "Recommendations for building a lightweight tracking system for patient records ?"
date: 2010-08-20
forum: Programming Talk
---

### Post by JackD on 2010-08-20
I'm looking to build a fairly lightweight tracking system. I think a RDBMS is the right choice, but it only needs to be a desktop app, and I'm really having a hard time finding something like Microsoft Access (I'm actually considering Lotus Notes, which works fine on Ubuntu, but the development is in Windows only). 

Kexi doesn't look that active or well developed to my eyes, but I could be wrong.

I'm not convinced that the Python Quickly/CouchDB is the right fit (awfully new, and I'll need to output boring reports and such).

The app is track medications for about 100+ HIV infected kids, but I'm really concerned that I'm going to build something that no one else can support. It needs to be on Ubuntu for cost and security.

Any tips would be appreciated.

---

### Post by memilanuk on 2010-08-20
It sounds like what you want is a (relatively) simple desktop CRUD (Create, Read, Update, Delete) application - which is not too hard to set up in Dabo... take a look @ [www.dabodev.com](www.dabodev.com)

I'm pretty green at this stuff myself, but the points that might interest you:  free, cross-platform, can use full-blown 'server' DBs like MySQL or 'server-less' ones like SQLite, uses Python & wxPython, covers up some of the 'ugliness' of accessing the database (in theory should be able to access either a local SQLite db file or a MySQL server with very few changes - assuming the table structures are the same of course).  It is supposed to have hooks to ReportLab for creating PDF output, which may also be of interest to you...

They have a pretty good start on the documentation... you want to read the Pycon 2010 Atlanta tutorial (newest), not the 'Step-By-Step' one, as it's been deprecated and will eventually be removed.

---

### Post by juancarlospaco on 2010-08-20
Yes is good idea!, 
but FYI there are already existing open source patient records tracking systems,
also if you need a custom custom one, go and do it :)

Python is the fastest to write, and quickly helps a lot.

---

