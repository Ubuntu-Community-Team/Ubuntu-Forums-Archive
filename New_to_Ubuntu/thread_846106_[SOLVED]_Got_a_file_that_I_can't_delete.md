---
title: "[SOLVED] Got a file that I can't delete"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Sand &amp; Mercury on 2008-07-01
I have a folder called 'qemu' sitting in my trash, that gives me an error saying 'Directory not empty' when I try to get rid of it.

Doing 'sudo nautilus' and then trying makes nautilus hang when I try to access the trash, too. :confused:

---

### Post by bobbob1016 on 2008-07-01
Open a terminal
cd .Trash (or wherever the trash is, not sure in Hardy .local I think)
pwd (MAKE SURE IT SAYS YOU ARE IN YOUR TRASH FOLDER AND ONLY IN YOUR TRASH FOLDER)

sudo chmod -R 777 * (This changes the permissions on everything in the folder so anyone can read/write them)

---

### Post by Sand &amp; Mercury on 2008-07-01
Worked like a charm. Thanks mate!

---

