---
title: "[SOLVED] How to start a program automatically when starting the comp?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-05-12
Bs'd

Is is possible to set up a program in such a way that it starts automatically every time I start the computer?

---

### Post by lswest on 2008-05-12
if you want to start a GUI app when you log in, you can add it to sessions under system-->preferences-->session, or to run a script at boot, copy it to /etc/init.d/ chmod it to 755, and run ```
sudo update-rc.d <scriptname> defaults
```

---

### Post by drs305 on 2008-05-12
An easy gui method: System, Preferences, Sessions, Startup Programs, Add

---

### Post by Carnivorum on 2008-05-12
Bs'd

I followed method 2, the easy gui method, added Kalarm, restarted my comp, and YES!  It works!

Thanks everybody for your help.

---

