---
title: "Compiling trouble"
date: 2006-07-09
forum: Programming Talk
---

### Post by misterE0 on 2006-07-09
Hello all, i'm having a little trouble.  Trying to get back into programming after a several year hiatus.  Anyway, i've just been using g++ and gedit, but want to check out glade.  I installed it and it will build progs, but they won't compile with the autogen.sh script.  I figure I must be missing some dependancy, but don't know what.  Anyone have any clue?  Thanks.

---

### Post by misterE0 on 2006-07-09
sorry for not including any errors in the orig post...
i'm getting "No package 'gtkmm-2.0' found"

---

### Post by Max Luebbe on 2006-07-10
You probably never installed libgtkmm (C++ wrappers for gtk)

Open up synaptic and install libgtkmm-2.4-dev

---

### Post by misterE0 on 2006-07-11
hrm...it is installed, and i reinstalled it just for grins, same problem.  any other ideas?

---

### Post by misterE0 on 2006-07-11
It also mentions something about changing the PKG_CONFIG_PATH environment variable, which i have changed to:

PKG_CONFIG_PATH=/usr/lib/gtkmm-2.4

still, no results :(

---

### Post by asimon on 2006-07-11
> **misterE0 said:**
> 
i'm getting "No package 'gtkmm-2.0' found"
The current version is 2.4 but if you want/need 2.0 then it should be available as "libgtkmm2.0-dev".

---

