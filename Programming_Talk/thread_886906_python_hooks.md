---
title: "python hooks?"
date: 2008-08-11
forum: Programming Talk
---

### Post by meanburrito920 on 2008-08-11
I've been looking around for a python library that supports application hooks and havent found anything. Basically what I was trying to do is to run a python program and then allow another python program to grab data or objects out of that program while it is still running. I could always have it pickle into a file and then have the other program read it, but that wouldn't be live and would add some overhead. Does anyone have any suggestons?

---

### Post by pmasiar on 2008-08-11
You want to share memory between processes? Why? What do you want to accomplish?

---

### Post by meanburrito920 on 2008-08-11
I was going to attempt making a 'gene-pool' simulation in python. the other program would just allow me to get status updates and save static stats of what was occuring for later use. Besides that, I just wanted to know if it's even possible in Python.

---

### Post by NathanB on 2008-08-11
Not unique to python, but take a look here:

[http://tldp.org/LDP/lpg/node65.html](http://tldp.org/LDP/lpg/node65.html)

Nathan.

---

### Post by tinny on 2008-08-11
I think this is what you want.

[http://pyro.sourceforge.net/](http://pyro.sourceforge.net/)

Looks to me like this is Python's equivalent to Java RMI?

---

### Post by NathanB on 2008-08-11
That's a good find, tinny...   your "APPLAUSE" icon applies!  :)

Nathan.

---

### Post by tinny on 2008-08-11
> **NathanB said:**
> That's a good find, tinny...   your "APPLAUSE" icon applies!  :)

Nathan.

Haha a complete Google search fluke really. Google => "Python RMI"

Ive only ever written "Hello World" in Python :)

---

### Post by imdano on 2008-08-11
[D-Bus](http://freedesktop.org/wiki/Software/dbus) would work here as well.

---

