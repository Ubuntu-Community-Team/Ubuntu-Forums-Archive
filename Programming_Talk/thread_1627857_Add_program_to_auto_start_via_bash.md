---
title: "Add program to auto start via bash"
date: 2010-11-21
forum: Programming Talk
---

### Post by kyleabaker on 2010-11-21
Does anyone know how I can add a program such as google gadgets (ggl-gtk) to the list of Startup Applications via a bash install script or command line? I know this can be done via the Startup Applications gui, but I need to automate this process.

Thanks in advanced!

---

### Post by kyleabaker on 2010-11-22
I've found a few tips and created a bash file, copied it to /etc/init.d/ and then created a symbolic link.

Now how do I update the system to notice it? update-rc.d? I can't seem to get the format correct. Tips?

EDIT:
Nm, I think I've got it now.

---

