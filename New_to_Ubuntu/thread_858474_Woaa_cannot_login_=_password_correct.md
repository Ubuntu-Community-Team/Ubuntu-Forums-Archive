---
title: "Woaa cannot login = password correct"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by uber1 on 2008-07-13
Ok I am very new and have installed ubuntu 8.04 onto a Asus dual core machine with 200Gb hdd, all went smoothly till I restarted and tried to login.

I entered the correct login and after a few seconds then a blank screen I was prompted yet again to login. There was no error to indicate the login info was wrong, this login process repeats etc.

Why do I have to use a password at all !!, for the life of me I dont get it. Why can we not just boot up and go ??.

Reg

---

### Post by annda on 2008-07-13
have you installed ubuntu in addition to windows? if so, it is possible that the linux partition is too small - the error often appears in that case.

to check that, can you boot into recovery mode and see what this command says about free disk space?

```
df -h
```

the first line of output is crucial.

---

### Post by markbuntu on 2008-07-13
Try logging in in gnome safe mode. 

Click on the little icon on the bottom left of the login screen and change session to gnome safe mode.

---

### Post by naturalfreak on 2008-08-14
I tried enabling the ATI driver and that fixed things.  In Failsafe mode, System > Administration > Hardware Drivers then select the ATI driver.

---

