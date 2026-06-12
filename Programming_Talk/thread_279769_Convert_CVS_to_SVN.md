---
title: "Convert CVS to SVN"
date: 2006-10-18
forum: Programming Talk
---

### Post by yippy on 2006-10-18
I'm migrating to SVN from CVS, but I have a CVS repository that's been in use for a few years and I'd like to carry the history over if possible.

I tried the cvs2svn tool, but it moves the CVS repository over to a single SVN repository, and treats all the modules as directories within a single project.  That would be fine, except that it treats branches as tags as if they are for the whole repository.  If I had a module called "System1" and a tag called "6_18_06", now the entire repository has a tag by that name, not just System1.  I'd like to have a /tags and /branches for each project, but cvs2svn creates a root-level /tags, /branches and /trunk, and puts all my projects into /trunk.

Does anyone know a better way?  I thought what I was trying to do is typical, but I've never used Subversion before so I could be mistaken.  Can I convert a module at a time into individual repositories instead?

---

