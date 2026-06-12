---
title: "Java Executable?"
date: 2006-06-03
forum: Programming Talk
---

### Post by JNowka on 2006-06-03
Is there anyway to make a java program an executable for mass production instead of a .class file that has to be run using the syntax "java filename.class".

---

### Post by kunnk on 2006-06-03
Easiest way is to create shell script and it may call "java filename.class" and may have also some other initializations. Lot of java programs are using it, for example azureus bittorrent client contains shell script named azureus, and you can execute azureus by calling this shell script.

---

### Post by meng on 2006-06-03
I thought the syntax was "java <filename>" without the .class extension.

---

### Post by yaaarrrgg on 2006-06-03
the best route is probably to make an "executable" jar... meaning, create a MANIFEST.MF file, with the Main-Class attribute set to your main class. Put this in the folder META-INF..

[http://java.sun.com/j2se/1.3/docs/guide/jar/jar.html](http://java.sun.com/j2se/1.3/docs/guide/jar/jar.html)

---

### Post by ynef on 2006-06-04
Seconding yaaarrrgg's suggesting for a JAR file, since that is the standard way of distributing Java programs. Most file managers are configured to start Java when a JAR file is double-clicked.

---

### Post by kunnk on 2006-06-04
I dont have such success with file managers, my experience shows that almost no linux file manager supports by defaulft executable jar files. It works in windows, true, but not in linux. One should use shell script or run manually java -jar some.jar

---

### Post by ynef on 2006-06-04
[QUOTE=kunnk]I dont have such success with file managers, my experience shows that almost no linux file manager supports by defaulft executable jar files. It works in windows, true, but not in linux. One should use shell script or run manually java -jar some.jar[/QUOTE]
Well, I'll be damned. Guess that not even Nautilus did it by default -- must have been a setting I made a while ago and couldn't remember it now.

---

### Post by yaaarrrgg on 2006-06-04
I swear "executable" jars used to work (maybe on Redhat 9?), last time I tried them ... :)

In Nautilus, for this to work, now seems you have to either:

    Right click and select "open with Java 1.x"

or:

    Right click -> Properties -> Opens With -> Java 1.x

Really though... the jars ought to launch just by double-clicking.  Is this a bug in the file managers?  Or maybe a security "feature"?

---

