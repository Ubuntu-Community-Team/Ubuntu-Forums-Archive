---
title: "Shared Network Drive"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by prenger745 on 2008-07-08
I currently have a shared network drive named "Public" on my Ubuntu box. Any computer on my network can access it.  However, when someone puts a file there and I try to edit it or change it on the Ubuntu box it says owner:unknown.  Is there anyway to have any file that is put in the Public folder to become owner:me?


Thanks,
Dan

---

### Post by superprash2003 on 2008-07-08
you could change the permissions of the file.. one way to do this is go to the terminal and type sudo nautilus .. then browse to where the file is ( in the window that pops up) and right click click on properties then go to permissions and set it to allow yourusername to write and delete

---

### Post by prenger745 on 2008-07-08
Yea I know how to do that.  I would rather the process be automated so that any file that is put in the PUBLIC folder automatically becomes "owned" by my Ubuntu login (not root).

---

