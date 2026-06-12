---
title: "Help deleting a user."
date: 2012-06-27
forum: New to Ubuntu
---

### Post by kruger53 on 2012-06-27
Ubunutu 12.4

I've been stuffing around trying to install postgres and somehow I've added a user 'postgres' that doesn't show up in the GUI 'User Accounts' list. It won't let me add another by this name and when I use the deluser command I get;

mark@mark-desktop:~$ sudo userdel -r postgres
userdel: user postgres is currently logged in


I've rebooted and tried various things but I can't seem to get this user logged out so I can remove it and start again.

Any help appreciated.

---

### Post by lisati on 2012-06-27
Do you have a copy of postgres running?

---

### Post by kruger53 on 2012-06-27
Ummm. Not sure. I installed it via the software center and then removed it. How can I tell?

---

### Post by kruger53 on 2012-06-27
thanks to lisati I've solved my problem.

---

