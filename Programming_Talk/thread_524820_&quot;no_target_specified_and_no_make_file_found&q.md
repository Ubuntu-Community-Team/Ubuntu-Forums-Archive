---
title: "&quot;no target specified and no make file found&quot;"
date: 2007-08-13
forum: Programming Talk
---

### Post by Taleman on 2007-08-13
i'm trying to use Anjuta but anytime a try to compile a Gnome 2.0 or Gnomemm 2.0 project (even a simple hello world project) i get a "no target specified and no make file found" error anytime I try to build it. However a generic terminal project  execute just fine. Any suggestions?

---

### Post by cybrid on 2007-08-14
If it's not a managed make project, you must write your own makefile in order to compile a project. If it's a managed make one, then you should select a target ie: debug, release...

---

