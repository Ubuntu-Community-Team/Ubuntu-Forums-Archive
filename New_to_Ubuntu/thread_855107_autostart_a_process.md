---
title: "autostart a process?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by adredz on 2008-07-10
i don't whether or not what i am pertaining to is a process. i just want to autostart superkaramba widgets cos it's a bit annoying when you have to open superkaramba theme manager and run them each time we log in. is there a way?

---

### Post by rxtx on 2008-07-10
If using default gnome desktop:

System --> Preferences --> Sessions --> Startup Programs --> Add

:)

---

### Post by rxtx on 2008-07-10
Sorry! Assumed you were using gdm. Would help to read things huh?

Create a script to run the application and store it in ~/.kde/Autostart. Make sure it is executable. :)

---

### Post by adredz on 2008-07-10
no, im not exactly pertaining to an application but rather a component of an application which, in this case, is the superkaramba. example i want to autostart "system info" widget or component of superkaramba, how would i do it? i know how to autostart any application though..

---

### Post by txcrackers on 2008-07-10
1) Once you have superkaramba running with the appropriate widget, go to System Settings->Advanced->Session Manager. Select "Restore previous session". Save and exit.

2) Make sure you **only** have applications you want to run when you log in running.

3) Log out.

4) Log in and those apps that were running should start up.

---

### Post by adredz on 2008-07-10
> **txcrackers said:**
> 1)

2) Make sure you **only** have applications you want to run when you log in running.


Thanks!

---

