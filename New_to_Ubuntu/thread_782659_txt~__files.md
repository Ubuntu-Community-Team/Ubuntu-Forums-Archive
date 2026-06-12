---
title: "txt~  files"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Poga on 2008-05-05
I have a question regarding hidden files that appear after using gedit.

     I've noticed that when I use gedit to edit a text file (such as "example.txt") and then save my changes, a hidden file is created with the name of "example.txt~", in addition to the original text file.  I didn't even notice it until opening up the folder containing them in Windows XP, where the txt~ files were, of course, no longer hidden.

     I'm wondering why these files are created, and what their purpose is.  I switch back and forth between Ubuntu and XP frequently, and don't like dealing with the added clutter (and hard drive space--though it's obviously minor) as a result.  I also like having 'clean' folders, and don't like a lot of needless files dangling around.  It's a major hassle to have to constantly keep track of them all and then go back and delete them in Windows (and it would be a similar hassle to unhide and delete them all in Ubuntu).

     Any comments or suggestions?

---

### Post by Trail on 2008-05-05
These are backup files. (generally a suffix of ~ denotes a backup).

There is a menu option somewhere to disable creating backup upon saving somewhere (though I use KDE and don't have gedit to see exactly where)

---

### Post by tacutu on 2008-05-05
what he said.
to disable, go to edit->preferences->editor->Create a backup copy

---

### Post by Poga on 2008-05-05
Thanks.  That's certainly a helpful start.

If anyone could elaborate on either of those points, I'd really appreciate it.

---

### Post by Joeb454 on 2008-05-05
if you want to delete them in your current directory (from a terminal) I always run ```
rm -f *.*~
```

Which would delete any file, with any file extension that has a ~ on the end :) I mainly use it on my server to reduce the amount of redundant files apache has :p

---

### Post by Trail on 2008-05-05
By the way, you can see hidden files and folders (such backups included) by pressing Ctrl-H in nautilus, if you want to delete them manually.

---

### Post by SlappyPappy on 2008-05-05
Very cool to know! I had no idea this thing was making all these backup files. What a mess   :confused:

---

