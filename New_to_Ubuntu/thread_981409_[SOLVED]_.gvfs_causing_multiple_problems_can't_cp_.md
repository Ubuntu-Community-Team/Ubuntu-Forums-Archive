---
title: "[SOLVED] .gvfs causing multiple problems can't cp can't rsync"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-13
I have a hidden directory:

.gvfs

it is empty.

When I try to

cp -ar /home /external-hard-drive

I get errors about the directory. 

When I try rsync I get errors. 

And when I first installed this drive (external usb 2.0) and tried to use it after copying /home to it, I got errors due to the .gvfs.

Can I delete it? How do I fix this?

---

### Post by talsemgeest on 2008-11-13
gvfs stands for Gnome Virtual File System, and it controls all file operations, pretty much everything using the files system. I can see why it can't be copied, due to the fact that it is the thing doing the copying. You should usually exclude it from copy commands and any syncs.

Just make sure you don't try to delete it, it is safer simply to ignore it.

---

### Post by psusi on 2008-11-14
Add -x to cp to tell it not to travel into different filesystems while recursing subdirectories.

---

