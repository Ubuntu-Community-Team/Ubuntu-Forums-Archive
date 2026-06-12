---
title: "Looking For Version Number For Libraries"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by mreos on 2013-03-11
Here are two minimum requirements and I can't figure out where to look:

libc-2.12.2 or later
 libstdc++.6.0.13 or later

Can someone point me in the right direction? Which folder do I go to look for these files? Once there, do I simply right click and then properties?

Ubuntu 12.10

---

### Post by Nr90 on 2013-03-11
The command:dpkg-query -l 'libc*'
Should give you installed packages matching libc.
You can do the same for libstdc++
An alternative is:
dpkg -l | grep "libc"

---

### Post by Bashing-om on 2013-03-11
mreos; Hi !

There are many ways to see what is installed on one's system. In your situation I can not think of an easieror more convenient  way than using "synaptic" to search for the packages/files."synaptic" will give you full disclosure on what is installed and what is available to install (if you have used the package manager for all installations of software). Be advised "synaptic" is no longer installed by default, you may have to install "synaptic".
[INDENT=3]
hth

[/INDENT]

---

### Post by mreos on 2013-03-12
Thanks Nr90 and Bashing-om !!

---

