---
title: "help with down load updates"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by blake7 on 2008-08-08
i keep trying to down load up dates but it keeps saying

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i try this it then says


a@a-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
a@a-laptop:~$ 

what does this mean  help

---

### Post by silkstone on 2008-08-08
You need to run the command as sudo...

sudo dpkg --configure -a

You will be asked for your password. When you enter it, nothing will appear on the screen, but that's OK - just type it in and press Enter.

EDIT/ Do you have the CD Option enabled in Update Manager? If so, it will try to read from the install CD which probably isn't there! You need to uncheck the CD option in System > Administration > Software Sources.

---

### Post by Het Irv on 2008-08-08
Just run 
```
sudo dpkg --configure -a
```

it will ask for your password and then you can run the command with superuser privilege.

EDIT:  DOH! Beat to it, but I can still make this post useful!

The command sudo elevates the current user to root privileges for a short amount of time (usually 5 min).  When you are root, you have full control of your computer, and could do anything you want, including screwing it up.  When you are root its not going to second guess what you are doing, so its a good idea not to run as root, except when you have to.

---

### Post by atihimself on 2008-08-08
> **blake7 said:**
> i keep trying to down load up dates but it keeps saying

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i try this it then says


a@a-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
a@a-laptop:~$ 

what does this mean  help

Do [COLOR="Blue"]sudo dpkg [/COLOR]and so on:)

---

### Post by GreenN00b on 2008-08-08
This thread is about the same issue:
[http://ubuntuforums.org/showthread.php?t=883008](http://ubuntuforums.org/showthread.php?t=883008)

---

### Post by blake7 on 2008-08-11
thank you everone for your help 

may the force be with you 

ps why is ubuntu not more user friendly??

---

