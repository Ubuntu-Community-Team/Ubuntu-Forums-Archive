---
title: "Python - copying files without &quot;modifying&quot;"
date: 2011-07-21
forum: Programming Talk
---

### Post by heinz1231 on 2011-07-21
My question is very simple, but I can't find a reasonable solution.

For my purposes, I need to be able to use some Python function or module or something, *anything*, to be able to copy a file from one location to another without changing the "last modified" statistic attached to the file in the properties.

Copying files normally (using the usual point-and-click methods in Ubuntu 11.04) does not change the "last modified" time on a file.  However, curiously enough, using the 'cp' command to perform the same action via the terminal does change the "last modified" time, as does the shutil module (keep in mind I am referring to the mod time of the newly created file)

I'm just confused as to how and why the mod time of the new file is changing when I copy certain ways, and staying the same as the original when I copy other ways.

Basically, I am looking for some code I can use to copy files in Python and keep the new file's mod time identical to its original file. Also, I sort of need a cross-platform solution. Any help is appreciated!

---

### Post by sectshun8 on 2011-07-21
cp -p

---

### Post by heinz1231 on 2011-07-21
Yup.  I totally just read an article about 'cp -p' and shutil.copy2() about 5 minutes after posting.  Huh, I guess I didn't research hard enough before asking.  Python Docs ftw.  Thanks, appreciate it :)

---

