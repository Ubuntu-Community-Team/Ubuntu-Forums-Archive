---
title: "Waste - Waste Apparently a System for Trash Elimination"
date: 2006-10-01
forum: Programming Talk
---

### Post by Note360 on 2006-10-01
Any way I just finished putting together my trash can application called waste. It is a simple application that moves files to trash, deletes them, and allows you to view them.

[CENTER]waste - Waste Apparently a System for Trash Elimination[/CENTER]

Features:
[LIST]
[*]Globs for moving and deleting trash
[*]Uses .Trash to store trash
[*]Allows you to view trash
[*]Will eventually be platform independant, but currently it is not. It relies on a Unix based system.
[/LIST]

How To:
Installation
```
$ tar -xf waste-.1-BETA.tar.gz
$ cd waste-.1-BETA
$ sudo python setup.py install
```

Move files/directories to trash 
```
waste filename
```

View Trash directory
```
waste -v
```

Delete whole trash
```
waste -e
```

Version
```
waste --version
```

Help
```
waste --help
```


Trash deletion and viewing is done from within python. However, the moving of files is done using mv. I am in the process of moving it over to python.

---

### Post by Note360 on 2006-10-01
I just fixed something. I got globbing on file deletion working so now you can delete with file names and globs. (eg. waste -e * is now the same as waste -e . Lets sya you wanted to delete file foo inside directory bar you would type waste -e bar/foo . Now lets say you wanted to delete everything in directory bar you would type waste -e bar/* )

---

