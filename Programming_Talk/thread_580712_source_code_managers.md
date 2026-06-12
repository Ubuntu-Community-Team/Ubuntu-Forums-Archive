---
title: "source code managers"
date: 2007-10-19
forum: Programming Talk
---

### Post by jpkotta on 2007-10-19
At work we're deciding upon a source code management system.  We really don't care what we use, just as long as it has low overhead.  Our software dept. consists 3 people, and we generally just decide what parts of a project to work on and integrate them after they're finished.  In other words, this would mainly be to manage our individual changes, not merge each other's work.  I've come to the conclusion that anything centralized like SVN is probably a waste of time, so that narrows it down to distributed systems.  I've never really used an SCM, other than to sync to repos.  

I use Monotone to sync OpenEmbedded, and I was not very impressed, but then again I didn't really dive in to it.  I played with Git, and it was very powerful but sort of clunky (also it pissed me off to no end when I needed to build it from source and couldn't get checkinstall to work right).  I then tried Mercurial; it was like Git but easy to use, so that's the one I'm going with.  The head software guy said he'll check it out soon, and it will probably be the one we all go with.

Does anyone have any comments about their favorite SCM, especially the ones I mentioned?

---

### Post by dwhitney67 on 2007-10-19
If you are looking for something that is simple, then RCS or CVS would fit the bill.  Most folks though would recommend subversion.  My employer uses CVS.  It makes no difference to me.

---

### Post by pmasiar on 2007-10-19
Subversion is new CVS: Couple years ago folks decided that CVS is convoluted beyond saving, and not worth fixing. SVN is CVS done right, by the same folks.

Take look at the Trac. It is server which integrates SVN, bug tracker, ViewSVN (so you can see diff in browser, in colors), and wiki for docs. Wiki and bug trackers has markup to bugs and changesets, everything neatly integrated.

[http://trac.edgewall.org/](http://trac.edgewall.org/)

The version in Ubuntu repos had recently security bug unfixed, our sysadmin recommends to use sources, guys run business supporting Trac and ar very good.

SVN lets you to use GUI SVN clients, like pysvn workbench, pretty neat too.

---

