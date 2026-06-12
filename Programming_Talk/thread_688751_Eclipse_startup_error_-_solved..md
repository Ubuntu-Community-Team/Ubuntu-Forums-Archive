---
title: "Eclipse startup error - solved."
date: 2008-02-05
forum: Programming Talk
---

### Post by JLuc_yvr on 2008-02-05
Just wanted to share the solution for a nasty Eclipse error that I had today.

env:  Eclipse 3.2, with Pydev, on Ubuntu 7.10, using the java 6 jvm.

Eclipse would fail at startup and advise me to look my workspace/.medata/.log file.

org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element

This was in relation to one of my source files which was on the file system allright.  I tried to move my source file elsewhere but that didn't help.

There was an IBM solution talking about deleting workbench.xml.  That didn't help either.

Looking around some more I found a solution at [http://forum.ubuntu-fr.org/viewtopic.php?id=183842](http://forum.ubuntu-fr.org/viewtopic.php?id=183842)

which advises to delete the .metadata directory.

I deleted both

/root/workspace/.metadata
/home/<user>/workspace/.metadata

and the problem went away.  So did my pydev projects though.

I had to reconfigure pydev first.  Then I created projects with the same names as previously and I unchecked the 'create default src directory' checkbox each time.  

I got all my projects back, including the SVN info.  But I did lose any extra configuration at the project and PyDev level.

---

