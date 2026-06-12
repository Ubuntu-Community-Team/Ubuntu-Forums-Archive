---
title: "SVN Questions (with Sourceforge SVN Servers)"
date: 2006-05-18
forum: Programming Talk
---

### Post by bieber on 2006-05-18
Hello.  I know this probably sounds like a terribly stupid question, but I'm a new user and developer at Sourceforge, and a friend and I recently started a project, and are attempting to use SVN to manage code, something neither of us had done previously.  So, I created a local repository, uploaded it and had it imported to the project repository.  I've found that I can check the project out without trouble, but if I try to commit, it doesn't work.  The terminal session I used looks something like this, to check out the code:
```

bieber@bieber:~/projects/particlesim$ svn checkout https://robertbieber@svn.sourceforge.net:/svnroot/particlesim/trunk ./
A    test
A    test2
A    makefile
A    particlesim.cpp
Checked out revision 1.
bieber@bieber:~/projects/particlesim$ svn diff
Index: particlesim.cpp
===================================================================
--- particlesim.cpp     (revision 1)
+++ particlesim.cpp     (working copy)
@@ -1,3 +1,5 @@
+//SVN
+
 /*
     Copyright 2006, Robert Bieber, Joel Levin

```
Now, when I tried to commit, I got this:
```

bieber@bieber:~/projects/particlesim$ svn commit -m "Test of SVN" --username robertbieber
Authentication realm: <https://svn.sourceforge.net:443> SourceForge Subversion area
Password for 'robertbieber':
svn: Commit failed (details follow):
svn: MKACTIVITY of '/svnroot/particlesim/!svn/act/9f831bf3-1814-0410-8c8d-84dc5fdb3434': 403 Forbidden (https://svn.sourceforge.net)

```
Now, I know I must be doing something stupidly obviously wrong.  Would you, perchance, happen to know what it is?

---

### Post by maphew on 2006-06-15
just figured this one out myself! You need to login to the sourceforge admin page for your project and enable yourself as an SVN developer. For some reason the default SF setup is for the project creater to be [yes] for cvs access but [no] for subversion.

---

