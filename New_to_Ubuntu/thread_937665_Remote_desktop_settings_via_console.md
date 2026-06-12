---
title: "Remote desktop settings via console"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-04
Is it possible to set the remote desktop settings via the console? ie Enabling desktop sharing. If so how?

---

### Post by kylet450 on 2008-10-04
vinagre

Do that in terminal

---

### Post by Kinetic_lord on 2008-10-04
Why? you can do that from System>>Prefereces...

---

### Post by Konstabel on 2008-10-04
I only have ssh access to my ubuntu system and is trying to set up a graphical remote login with out any success. That is why I would like the console commands.

Just for clarity, what is the difference between the console and terminal?

---

### Post by derekshaw on 2009-10-27
> **Konstabel said:**
> Is it possible to set the remote desktop settings via the console? ie Enabling desktop sharing. If so how?

not quite what you are looking for, but may be helpful to others.  Needs X Window Client and Server on target and the host you are working on.

see [http://ubuntuforums.org/showthread.php?t=1301409](http://ubuntuforums.org/showthread.php?t=1301409)

essentially
   ssh userID@targethost -X
   vino-preferences

---

