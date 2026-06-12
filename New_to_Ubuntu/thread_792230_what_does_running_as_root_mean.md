---
title: "what does running as root mean?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by svenofix on 2008-05-12
So ya, what does running as root mean? I'm still confused on that. Is it
sudo? :confused:

---

### Post by JoshuaRL on 2008-05-12
> **svenofix said:**
> So ya, what does running as root mean? I'm still confused on that. Is it
sudo? :confused:

Running as root entails logging in as root instead of as a sudo user.  It's the same as an "administrator" account in Windows.  It lets you do absolutely anything, and anyone that compromises your system too.  That's why it's so dangerous and isn't discussed how to do it here.

Use sudo, its safe and easy once you know how.  If something says you need to run it as root, use sudo.

---

### Post by Monicker on 2008-05-12
> **JoshuaRL said:**
> Running as root entails logging in as root instead of as a sudo user.  It's the same as an "administrator" account in Windows.  It lets you do absolutely anything, and anyone that compromises your system too.  That's why it's so dangerous and isn't discussed how to do it here.

Use sudo, its safe and easy once you know how.  If something says you need to run it as root, use sudo.

You can still screw up your system using sudo.  :P

---

### Post by licensedorchid on 2008-05-12
Root is the "superuser". Root can do anything to anything. Ubuntu makes it hard to *be* root, but you can still do dumb things with sudo.
Sudo, by the way, runs commands as root, just without su'ing to root.
Basically, logging in as root is discouraged, unless you know what you are doing!

---

### Post by SunnyRabbiera on 2008-05-12
sudo is sort of root, though not completely.
In the unix system you are faced with what is known as a multiuser environment, and the root user is the administrator of the system.
In ubuntu the root account is disabled by default, so sudo is used instead, sudo allows root access to a certain extent.
To understand how root works is to understand how unix works, as ubuntu is based on linux and linux is a unix like system.

---

### Post by svenofix on 2008-05-12
Thank you so much everyone!! :KS

---

### Post by JoshuaRL on 2008-05-12
> **Monicker said:**
> You can still screw up your system using sudo.  :P

Aw, now you're just picking on me because I was trying to be concise.

:lolflag:

---

