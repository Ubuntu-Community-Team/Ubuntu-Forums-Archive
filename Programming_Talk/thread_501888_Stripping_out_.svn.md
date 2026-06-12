---
title: "Stripping out .svn"
date: 2007-07-15
forum: Programming Talk
---

### Post by viniosity on 2007-07-15
I've been using subversion for quite a while, but my last experience has me wanting to try a different version control system (Mercurial).  My current code has all this .svn hidden files and directories about which I'd like to strip away clean.  Is there some way to do that?  How does one get rid of all traces of subversion from code you've checked out?

---

### Post by chris_nava on 2007-07-15
svn export PATH1 PATH2

This will give you a copy without .svn folders

[http://svnbook.red-bean.com/en/1.0/re10.html](http://svnbook.red-bean.com/en/1.0/re10.html)

---

### Post by viniosity on 2007-07-15
Ah!  Thanks!

---

