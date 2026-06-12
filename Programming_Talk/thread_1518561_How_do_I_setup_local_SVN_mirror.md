---
title: "How do I setup local SVN mirror?"
date: 2010-06-26
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-06-26
I am working on a Java-based project in Eclipse that depends on another open-source project.  I like getting the latest updates so I checked out the dependent project using SVN and update it periodically.  Last night I encountered an issue with a recent checkout that broke my project and I had to revert to the previous release.  What I would like to do is have my local SVN server mirror the dependent project.  So how can I checkout the latest copy of the dependent project, ensure that everything compiles ok on my local machine, and if so commit that version of the dependent project into my local SVN?  I would imagine that there's some SVN application or interface that does exactly what I just described.

---

### Post by MadCow108 on 2010-06-26
you can use externals for this:
[http://svnbook.red-bean.com/en/1.0/ch07s03.html](http://svnbook.red-bean.com/en/1.0/ch07s03.html)

---

### Post by SNYP40A1 on 2010-08-07
I don't quite see how that will work for me.  The link you sent appears to allow a simple URL redirection for some folders of the SVN repository.  What I want to do is not simply point to or mirror (although that's why my subject title asked for...not quite accurate...) an external SVN, but instead buffer or selectively mirror it.  I basically want to first checkout the SVN onto my local SVN server and then periodically, merge updates from the remote SVN onto my local SVN.  The local SVN will never be able to commit updates to the remote SVN directly.

---

