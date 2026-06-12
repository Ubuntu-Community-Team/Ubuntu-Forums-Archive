---
title: "Many moduled python app into Single File for distribution"
date: 2009-04-05
forum: Programming Talk
---

### Post by stimpack on 2009-04-05
Thinking along the lines of a .jar file but for python apps. Something that takes an app with many modules and turns it into a single file.

I am looking to retain cross-platformness and so an executable compile is not what I have in mind.

The closest I can find is zipimport, that narrows it down to 2 files, the loader and a zip.

Does anyone know a nice way of achieving a single file, similar to .jar files?

---

### Post by imdano on 2009-04-05
[Eggs](http://peak.telecommunity.com/DevCenter/PythonEggs) are the closest thing to jars that Python has (at least that I know of).

---

