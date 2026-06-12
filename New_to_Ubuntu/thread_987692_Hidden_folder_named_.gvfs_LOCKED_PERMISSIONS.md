---
title: "Hidden folder named .gvfs LOCKED PERMISSIONS"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-19
Hi Gang

In running a mirror I'm finding a failure on a hidden file named .gvfs

When trying to change the permissions, it jumps back to previously established permissions, RIGHT IN FRONT OF MY EYES!

The folder is EMPTY, so it's no big deal it don't copy, EXCEPT it causes a log entry 4 times a day saying it failed and they add up quite quick.  

More annoying than bugs on a windshield in summer!

I've tried root commands to change it and they change right back.
Must be a pretty important EMPTY file to have it do that!

I wonder if there is a way to write a script for Rsync that ignores certain troublesome files such as this?????

If ROOT doesn't have permission to change permissions, and user doesn't have permission to change permissions, WHO DOES?????

TTUL
Gary

---

### Post by taurus on 2008-11-19
If you look at the permissions of that directory, you would see it set as

```
dr-x------  2 taurus taurus     0 2008-11-13 22:16 .gvfs
```
So, nobody can write to it, not even the owner.  Besides, the directory is empty anyway.

By the way, root doesn't mean that you can write or delete whatever you want on the system.  It all depends on the permissions too.

---

### Post by Kellemora on 2008-11-20
Hi taurus

OK, I see, it's some super important file the gods have decided need to be their and completely out of the computer owners control.  I can deal with that until it's used for Spyware!

But for NOW, what can I do to keep it from messing up backups, mirrors, log-files and the like?????

And are there any other god controlled folders hidden on my computer I should know about?

TTUL
Gary

---

