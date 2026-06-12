---
title: "Dependency is not satisfiable problem"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-29
Attempting to install 
gnome-network-admin_2.28.1-0ubuntu2_amd64.deb
with Gnome Package Installer
Error: Dependency is not satisfiable: libiw29 (>= 28+29pre7)
Can someone please explain how to solve this?

---

### Post by skatinjj on 2012-03-29
A dependency is another piece of software a program needs to run.

In your case,gnome-network-admin_2.28.1-0ubuntu2_amd64.deb requires you to install libiw29 (>= 28+29pre7).

You should be able to this by opening the terminal and typing:

```
sudo apt-get install libiw29
```

Alternately you can open synaptic from System > Administration and search for libiw29.

---

### Post by Bumpalot on 2012-03-29
thanks!

---

