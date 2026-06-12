---
title: "[SOLVED] gksu and gksudo"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by t0p on 2008-07-16
What is the difference between **gksu** and **gksudo**?  They both seem to do the same thing, far as I can tell!  Are there situations where the one is indicated rather than the other?

---

### Post by Barrucadu on 2008-07-16
gksu uses su as the authentication method, whereas gksudo uses sudo.

---

### Post by pedro_orange on 2008-07-16
They're just GTK front ends to su and sudo, used for graphical apps.

---

### Post by t0p on 2008-07-16
> **Barrucadu said:**
> gksu uses su as the authentication method, whereas gksudo uses sudo.

Sorry, I don't understand that.  In ubuntu, you can't by default use su - because user doesn't set a root password, using su results in an authentication error.  Right? So how can gksu use su?

---

### Post by sisco311 on 2008-07-16
> ls -al  /usr/bin/gksu*
-rwxr-xr-x 1 root root 28944 2008-05-08 12:16 /usr/bin/gksu
lrwxrwxrwx 1 root root     4 2008-07-16 13:42 /usr/bin/gksudo -> gksu
As you can see gksudo is a symbolic link to gksu.
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

---

### Post by t0p on 2008-07-16
> **sisco311 said:**
> As you can see gksudo is a symbolic link to gksu.
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

*Ahhh!!!* So gksudo and gksu don't just act the same... they *are* th same!!

**Thanks**

---

### Post by sisco311 on 2008-07-16
> **pedro_orange said:**
> They're just GTK front ends to su and sudo, used for graphical apps.

gksu and gksudo is a graphical front-end to sudo.
kdesu is a grapchical front-end to su
kdesudo is a graphical front-end to sudo, has replaced kdesu in Kubuntu, starting with Gusty Gibbon.

---

