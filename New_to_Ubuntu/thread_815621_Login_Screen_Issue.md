---
title: "Login Screen Issue"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by aheicher on 2008-06-01
Wow, I seem to be chuck full of noobish questions today.
Well anyway, I am attempting to install a login screen that can be found [here](http://gnome-look.org/content/show.php/FBI_Terminal?content=82380&PHPSESSID=9570300dfce2fea6441c48d4f2f8c9c3).  I follow the normal procedure, System->Administration->Login Window, drag the tar file to the Local Screen, and select it as the default.  Everything appears fine, until I logout to test the screen.  I never get to the screen, all I get is a human color screen with the white circle (loading) by itself.  It hangs here, and the only way I can login again is to press Ctrl+Alt+F1 and type ```
$ sudo rm /tmp/.X0-lock
``` and start the XServer.  If anyone has had any experience with this screen or this specific problem, I would appreciate it.  
Thanks
-Sintax

EDIT: I DID NOT delete the tar file from the original location, if anyone is wondering.  Also I'm using 8.04

---

### Post by Xiong Chiamiov on 2008-06-01
Are you having problems booting into the desktop to change your login back to normal, or do you just want to get this working?

---

### Post by aheicher on 2008-06-01
I just want to get it working, I can get to the desktop fine

---

### Post by tigersrock on 2008-06-01
i had the same problem with the same file, don't use it

---

