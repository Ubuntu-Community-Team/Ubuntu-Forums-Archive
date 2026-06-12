---
title: "[SOLVED] root user"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by johnnyhostile on 2008-08-12
I am trying to get thinkfinger running and when I try to modify the /etc/pam.d/common-auth file it tells me I dont have permission and that the owner is root..

I am the only user on this machine and I don't really know where to look to get either root access or at least have permissions enabled for my user.

Thanks!

:guitar:

---

### Post by dje on 2008-08-12
open a terminal (applications >> accessories >> terminal) and type:
```
gksu gedit /etc/pam.d/common-auth
```
**Be careful when using root as you can do ANYTHING to your system!**

dje

---

### Post by Elfy on 2008-08-12
I assume you are trying to edit it with gedit, if so use

```
gksudo gedit /file/to/edit
```

Use sudo for non gui apps, gksudo for gui apps. Generally when something wants to be run as root, use either of those 2. When you enter sudo in the terminal it won't appear to be there - it is.

> at least have permissions enabled for my user.It's different than windows - you only temporarily gain root rights to accomplish task here using either of those.

---

### Post by SunnyRabbiera on 2008-08-12
You need to access the protected directory by going into a terminal and typing in sudo and then the command you need like nautilus.
In Ubuntu the root account is disabled, protecting the user from the issues found with a root account, it is what devides ubuntu from both windows and most other linux distros.

---

### Post by johnnyhostile on 2008-08-12
worked! may thanks! :)

---

### Post by SunnyRabbiera on 2008-08-12
Indeed, I know suff like this can be annoying to the new user but trust me its for the better.
The main cause of all the issues in windows is that it allows people to use root access by default, by doing so it puts the user at risk.
Sure it makes windows "easy" but it also makes it insecure, windows has sacrificed security for ease of use.

---

### Post by mlentink on 2008-08-12
If it did, then please mark your thread as [SOLVED], so other won't come back unnecessarily, or learn how to solve their own problem.

---

