---
title: "Secure User Folder"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Whatrymes on 2008-07-14
Hey:

I created an administrator account at installation and created a "User" account for general purposes. I noticed in the general account that I can access the folders of my administrator account(/Home/"administrator account"/). Can I secure this folder somehow so that other users can not access it.

Thank you,
Ed

---

### Post by mriedel on 2008-07-14
You could do that, but I think you should reconsider your setup in general. The administrator account on ubuntu (and linux in general) is root (whose home is /root, not /home/root). There's no need to set one up, except you want a user account that's not allowed to sudo (see man sudo).

---

### Post by sayakb on 2008-07-14
Log into you administrator account and open /home folder. Right click on the administrator folder and click the permissions tab and **uncheck** read/write permissions for Group and Others.

---

### Post by Whatrymes on 2008-07-14
Thank you "LinuxIsInnovation" worked like a charm.

Ed

---

