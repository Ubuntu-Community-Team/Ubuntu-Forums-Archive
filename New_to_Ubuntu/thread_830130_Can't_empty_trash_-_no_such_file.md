---
title: "Can't empty trash - no such file"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by helino on 2008-06-15
Hi, when I try to empty my trash, I get:

Error removing file: No such file or directory

The file I want to remove was once on a mounted sambashare, but I've removed from the computer that shared it, so it doesn't exist anymore.

Can anyone help me with this?

---

### Post by jamewill on 2008-06-15
try this

cd ~/.local/share/Trash/files

ls (to see the files you want to remove)

if you want remove them all do the following

sudo rm -r *

ONLY DO THIS if you are in the correct directory as indicated above
IF YOU DO NOT TAKE THIS ADVICE YOU COULD REMOVE WIPE DATA THAT WANT TO KEEP AND DAMAGE YOUR ENTIRE INSTALL

if you are in the correct directory then no problem

pwd (to check your current directory)

jw

---

### Post by helino on 2008-06-16
Hi jamewill, thanks for your answer. Unfortunately, I've already tried to empty the trash CLI style, the problem is that there are no files in ~/.local/share/Trash/files.

Since there are no files, I can't remove any files, and I can't "empty" the trash. The trash still looks like it's full in Nautilus, which is annyoing. 

Anyway, thanks for taking the time to reply

---

### Post by alienexplorers on 2008-06-16
Do yo have the following directory:
> ~/.gnome/gnome-vfs/.trash_entry_cache
do an ls -la and post the results here.  If you are missing that file build it and reboot.

---

### Post by helino on 2008-06-18
Just for the record, I didn't have a .gnome folder (I deleted it when I needed to remove all the gnome settings). I was about to install xubuntu anyway, because I wanted something lighter, so I ended up doing that.

---

