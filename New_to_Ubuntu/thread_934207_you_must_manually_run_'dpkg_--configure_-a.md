---
title: "you must manually run 'dpkg --configure -a"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-09-30
I have been trying to install java in order to run tix guitar and i keep getting this error.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
With this, I now cannot update anything? 
HOw can i fix this?

---

### Post by Idefix82 on 2008-09-30
Just type
```
sudo dpkg --configure -a
```
and try again.

---

### Post by nilsolaris on 2008-09-30
Thank you for the reply. I am not getting:
Unable to get an exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

?

---

### Post by nothingspecial on 2008-09-30
Have you got synaptic package manager, Add Remove or Software Sources open. If so close them.

---

### Post by SunnyRabbiera on 2008-09-30
also it might help if you restarted as sometimes the app managers hang.

---

