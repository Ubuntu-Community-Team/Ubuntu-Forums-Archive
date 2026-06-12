---
title: "command touch"
date: 2015-07-07
forum: New to Ubuntu
---

### Post by houmingc on 2015-07-07
When i get a project files from my friend, i could not compile it in ubuntu.
I was told to type touch * under the project files.
And miraculously, the build is a success.


Can someone enlighten me why this is so?

---

### Post by dino99 on 2015-07-07
[http://www.computerhope.com/unix/utouch.htm](http://www.computerhope.com/unix/utouch.htm)

---

### Post by buzzingrobot on 2015-07-07
The "make" program relies on a "makefile" file that specifies which files need to be compiled to support the building of other components.  Make uses the modification date/time of files. I.e., if an object file is older than the source file it was built from, make will assume that source file has been updated and will recompile it. 

The "touch *" reset all the files in that directory to the same date and time.

---

### Post by Keith_Helms on 2015-07-07
Is the problem that you could not compile it, or just that the compile didn't do anything?  Were the resulting object files already present in the project that you downloaded?  If so, make looked at the timestamps of the source and object files, decided the object files were up to date, and thought there were no new changes to the source code that needed to be built.

Running touch changed the timestamps on the source files so that they now look newer than the object files and make's "up to date" check determines that they need to be recompiled.

---

### Post by houmingc on 2015-07-10
Thanks for the explanation.
Is my virtual understanding below correct?

                               TIME
object file             |============       (newer)
source file           |=======                   (older)

After touch

object file             |=========                  (older)
source file           |=============         (newer)

or
each file to current system time

object file             |=============   (same)
source file           |=============   (same)

---

