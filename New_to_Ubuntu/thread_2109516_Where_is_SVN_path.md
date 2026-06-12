---
title: "Where is SVN path ?"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by nsingh on 2013-01-27
I installed subversion (SVN or Subversion is a version control software) on ubuntu. I went to Software Manager, searched for "Subversion", clicked install and it got installed.

My question is where is the subversion path set ? In other words when I go to terminal and type >svn help   it does show me help options of SVN but I did not set path of SVN myself; I just installed SVN and path got set by itsef.
I tried >echo $PATH  but couldn't see svn path there, then where is path to SVN set ?

---

### Post by steeldriver on 2013-01-27
Hello and welcome

AFAIK svn does not need to alter the PATH variable - its components are installed in standard system directories. You can see where the program binaries are located using the 'which' command e.g.

```
$ which svn
/usr/bin/svn
$
$ which svnadmin
/usr/bin/svnadmin

```

---

