---
title: "make vs ant"
date: 2005-03-24
forum: Programming Talk
---

### Post by und3rdog on 2005-03-24
Background: Doing a respectably large program for an OO class based in Java, Working as part of a 3 member team.

Question: Given only one of us has any background on building with ant, which would be better?

---

### Post by defkewl on 2005-03-25
Isn't ant only for Java? and make for Perl and C/C++ ?

---

### Post by cow_racer on 2005-03-25
Ant is the way to go.  It is easier to write.  But a little slower.  And it also does dependency check.  Make only uses time stamp to determine which files to compile.  A file changed may affect other classes in some other unchanged files, but because Make only use time stamp, these effected files are not recompiled.  I heard Jikes can create dependency for Make to use, but so far I never got that to work.  Jikes simply crash on me.

---

### Post by vague- on 2005-03-29
[QUOTE=defkewl]Isn't ant only for Java? and make for Perl and C/C++ ?[/QUOTE]

No, Ant can have many targets, including building language other than Java.  Perl might be a special case due to the MakeMaker magic and such.  It is not that you could not use Ant to build a Perl project, it just would not slot in with the default system.

Personally, I would use Ant.  The format is fairly easy to learn, it will be supported (if via plug-ins) in most IDEs and Java-aware programmer's text editors and most targets are cross-platform (assuming that your Java application probably is, also).

---

