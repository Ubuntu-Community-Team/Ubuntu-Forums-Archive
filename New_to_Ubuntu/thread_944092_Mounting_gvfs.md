---
title: "Mounting gvfs"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by alpdo on 2008-10-11
How do i mount gvfs??? using the terminal....
can i mount it to other mount points...???

---

### Post by mejy on 2008-10-11
The standard way to make a GVFS mount is to use the "Connect to Server" entry on the places menu.  These can be made permanent by checking "Add Bookmark".  Mounts are then accessible via the terminal in ~/.gvfs/.  I'm not aware of any way to mount to other mount points, but you should be able to create a symbolic link.

---

