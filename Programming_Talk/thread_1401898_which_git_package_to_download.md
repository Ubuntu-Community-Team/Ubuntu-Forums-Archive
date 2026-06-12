---
title: "which git package to download?"
date: 2010-02-08
forum: Programming Talk
---

### Post by badperson on 2010-02-08
I'm setting up a server this week, and I want to use git for version control. There are a whole bunch of packages in the repositories...git-svn, git-cvs, gitg...for a server hosting a code repository (available only to me on my home wireless network) which package is best? 
thanks, 
bp

---

### Post by jfparis on 2010-02-14
They all have different purposes

If you want to use git for keeping control of you files you need git-core (and dependencies).

git-svn and git-cvs are for interacting with svn and cvs trees (so you don't need it)

you might want to have a look at:
* gitk: a GUI to browse git trees. It looks ugly (thanks to TK but it works)
* gitweb: if you want to have you revisions browsable on the web (internally or publicly)

---

