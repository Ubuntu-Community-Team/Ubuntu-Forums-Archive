---
title: "KDevelop - install stupid error"
date: 2005-11-21
forum: Packaging and Compiling Programs
---

### Post by ja_b on 2005-11-21
I am completely new to linux.
I was installing KDevelop (running configure script), and I reclieved ```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
```
And I used the:
```
sudo apt-get install build-essential"
``` gizmo ;) 

I use Kubuntu (but since they're are - according to what Kubuntu site says - almost the same, i felt free to ask here)

---

### Post by JohnnyMast on 2005-12-06
Build essentials have nothing to do with this, try 

apt-get install libx11-dev - X11 client-side library (development headers)

That will do

---

