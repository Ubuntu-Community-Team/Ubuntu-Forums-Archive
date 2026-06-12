---
title: "CVS to SVN adapter interface"
date: 2007-01-30
forum: Programming Talk
---

### Post by lloyd mcclendon on 2007-01-30
hi

I think i may have a good idea here, I'm wondering if such a thing exists.  We have a subversion repository here that has been in use for a long time.  We also have a few applications that have built in CVS support but no SVN.

So I could either a) setup another seperate CVS repository (ok but meh)   b) hack the programs to support svn (no way)  c) find something that fakes a CVS interface and translates all the commands to svn.


program that wants cvs -->  fake cvs thing -> translate to svn --> svn repository

does such an adapter exist?  is it possible?  so far i've found cvstosvn.tigris.org, but that's only for converting an old cvs repo to an svn one.  i don't really know a whole lot about CVS other than it's old and doesn't handle directories but we need to have version control for these apps

TIA

---

