---
title: "Accessing root"
date: 2007-04-29
forum: Programming Talk
---

### Post by TeamMicron on 2007-04-29
My terminal will not allow my to access root.  I typed su root and then entered the correct passworkd.  
error: setgid: operation not permitted.  Does anyone know what I am doing incorrectly?  thanks.
 TeamMicron

---

### Post by bashologist on 2007-04-29
If you absolutely have to be root then type the following.
```
sudo su
```
Root can be a dangerous thing so be careful! It's almost always better to use sudo instead.

---

### Post by Tomosaur on 2007-04-30
If you're only trying to gain root priveleges to edit a file, for example, then you should be usind 'sudo', like this:
```

sudo nano /etc/X11/xorg.conf

```

Logging in as root is not reccommended, but as always, the choice is yours. It makes sense to me, anyway, to only give myself root privs for the shortest time possible.

---

