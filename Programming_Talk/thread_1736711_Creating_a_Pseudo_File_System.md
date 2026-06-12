---
title: "Creating a Pseudo File System"
date: 2011-04-22
forum: Programming Talk
---

### Post by kelltrick on 2011-04-22
I'm new to how the pseudo file system works, I apologize in advance if this is a dumb question. 

Is there a way I can expose a pseudo file (similar to /proc/stat) that will run a program and get the file contents from the output of that program? More over, can I create my own stat file that will allow other programs to access its information without having to have another program constantly dumping information to a disk? The updates need to be ever few hundred ms, so I'd like to avoid disk IO.

---

### Post by MadCow108 on 2011-04-22
probably fuse is what your looking for:
[http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)

---

### Post by kelltrick on 2011-04-22
Cool, Thanks!

---

