---
title: "Batch rename folders"
date: 2007-02-11
forum: Programming Talk
---

### Post by Tilex on 2007-02-11
I've been trying to rename 1000+ folders to template_XXXX where the XXXX is a number.  I want to rename all the folders, but don't want the subfolders to be changed, only the parents.  Can anyone help me for achieving this?  Thanks!

---

### Post by lloyd mcclendon on 2007-02-11
num=1; for dir in `find -maxdepth 1 -type d` ; do mv $dir template_$num ; num=$((num + 1)) ; done

you may want to read the man page for find, it's a pretty powerful command.  

-type d tells it to find only directories
-maxdepth 1 says don't recurse into sub dirs
the for loop goes through every line that the find command spits out, moves the line (stored as $dir) to template_$num.  num starts at 1 and is incremented each time.

---

### Post by gradedcheese on 2007-02-11
Not 100% relevant, but here's something similar that I made which plugs into Nautilus: [http://andrey.thedotcommune.com/rename.html](http://andrey.thedotcommune.com/rename.html) (my bash scripting isn't too good, so I used Python)

---

### Post by Tilex on 2007-02-11
Thanks for the help guys, I'm gonna check that out!

---

