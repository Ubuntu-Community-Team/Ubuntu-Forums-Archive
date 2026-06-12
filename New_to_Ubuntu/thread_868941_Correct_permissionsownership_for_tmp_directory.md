---
title: "Correct permissions/ownership for /tmp directory?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by TheDriZZle on 2008-07-24
My /tmp directory got completely messed up. I read that the best way to fix the permissions and ownership with chmod and chown is:

```
chmod 1777 /tmp
chown root.root /tmp
```

Is this right?

---

### Post by caljohnsmith on 2008-07-24
That should work just fine, except you need to put a "sudo" in front of both of those commands.

---

### Post by cartosys on 2010-04-15
That worked for me.  My error message at login screen was:  

"There is a problem with the configuration server"  

usr/lib/libgconf2-4/gconf-sanity-check-2

exited with status 256

---

### Post by HunterThomson on 2011-12-22
Yes, also, the command is with a colon not a pirod.

sudo chmod 1777 /tmp
sudo chown **root:root** /tmp

---

### Post by oldos2er on 2011-12-23
Closed, necromancy.

---

