---
title: "Python run multiple files together"
date: 2009-10-10
forum: Programming Talk
---

### Post by nipunreddevil on 2009-10-10
I need to run multiple programs which read from the same text file and each produces its own output.What shall be the best approach in terms of memory usage.
Also how can i run multiple python scripts together simultaneously.

---

### Post by smartbei on 2009-10-10
Unless this is a really big text file (say, more than a couple hundred megs at the least), I wouldn't bother with running them simultaneously or not reading the file multiple times.

Instead, just run them sequentially.

If you want to run python scripts simultaneously, you can just start them in the shell with an '&' at the end of the line - which starts a process in the background. If in this way you start several, they will all run in the background until finished.

I can't think of a good way to have the python scripts all access a single resource loaded to memory (the huge file). What you can do however, (if you can edit the scripts) is edit them so that they read the file in chunks. This way, memory usage stays low.

---

### Post by nipunreddevil on 2009-10-10
How would it be to make a shell script/python script which makes other python scripts run.I have little experience of shell scripting though

---

