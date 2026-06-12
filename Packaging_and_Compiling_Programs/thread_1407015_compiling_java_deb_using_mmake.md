---
title: "compiling java deb using mmake"
date: 2010-02-14
forum: Packaging and Compiling Programs
---

### Post by sandyd on 2010-02-14
Im currently attempting to use mmake to make a deb for a java program.
Im really close, but im missing one thing. 

The application was developed using Netbeans.
There are several java files, so I have to set the main class using the manifest file.
however, where in the whole wide world am I supposed to put it?

p.s. this is what im trying to make a deb out of.
[http://ubuntuforums.org/showthread.php?p=8805030#post8805030](http://ubuntuforums.org/showthread.php?p=8805030#post8805030)

---

### Post by SevenMachines on 2010-02-16
hi, have to admit i dont really know much about java packaging. however, theres a section about this [in debian here]("http://wiki.debian.org/Java/Packaging"), you might want to look in particular at the 'jh_manifest' section and see if thats the kind of thing your after

---

