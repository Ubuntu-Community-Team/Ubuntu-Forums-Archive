---
title: "[Java] Mass poll files"
date: 2010-06-13
forum: Programming Talk
---

### Post by SpinningAround on 2010-06-13
I would like to mass poll files to check if they have change, been deleted or if new have been created. The files are quite many above 300 and the are placed into subfolders.Question is what is the best method to do this.

---

### Post by DanielWaterworth on 2010-06-13
It's best not to poll at all as it consumes cpu-time. On Linux you can use [inotify]("http://en.wikipedia.org/wiki/Inotify").

---

### Post by SpinningAround on 2010-06-14
> **DanielWaterworth said:**
> It's best not to poll at all as it consumes cpu-time. On Linux you can use [inotify]("http://en.wikipedia.org/wiki/Inotify").

It's not really what I'm looking for, I don't want to constantly monitor files for change. What I would like to do is when the program execute is to get the change date of the files. The time between running the program can be weeks or even months.

---

### Post by DanielWaterworth on 2010-06-14
That's not really polling then [=. The function you want is stat and it's relations.

---

### Post by PaulM1985 on 2010-06-14
Your program could use a log file to see when it was last run.  It could then take a directory which the user provides and create a Java "File" object, see here:
[http://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html](http://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html)

Using this object you should be able to find out if it is a file or directory.  For directorys you can use the function listFiles to get sub files and use the lastModified function to check when it was last modified.  Compare this value to see if it is newer than the value of the last run in you programs log file.

This will give you all the information you need on last modified. Not sure how you could do the difference in if it had been created.  Maybe you could have some info on the file structure in your log file too.  Describing which paths exist and so on, then check if the path of you "File" object is in your log file.

Hope these ideas are of some help.

Paul

---

