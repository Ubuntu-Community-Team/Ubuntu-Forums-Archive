---
title: "[SOLVED] Cannot open Opera 9.27 after removing 9.50b"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by benevolent on 2008-06-03
Hello there, I have installed Opera 9.50b2 (**sudo dpkg -i opera**) but i decided to move back to the stable version, so i unistalled it (**sudo apt-get remove opera**)..


But I cannot open Opera.. This is what i get from the console!


```
dimitris@ubuntu:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
```


thx..

---

### Post by Aearenda on 2008-06-03
Have you tried reinstalling 9.27?

---

### Post by benevolent on 2008-06-03
Yes... I also remove opera from synaptic and sudo apt-get install it again.. And i have the same error...

how can I completeley remove Opera, and its dependencies???

---

### Post by Aearenda on 2008-06-03
EDIT: Please ignore the bit about JRE below. I've just logged on to a machine with Opera installed - the JRE messages are normal and don't prevent opera from running.

Ignore this: *The two libraries it complains about are part of the Java Runtime Environment (JRE) so I suggest you first try to reinstall sun-java6-plugin (or an earlier version if that's what you use). You can do this from system->administration->Synaptic by right-clicking and choosing 'Mark for reinstallation', then click on the 'Apply' button.*

I would delete the .opera folder from your home directory as the next step. 

If that makes no difference, then to completely remove opera, do this:
```
sudo apt-get purge opera
sudo apt-get autoremove
```
Autoremove gets rid of packages that were installed automatically to satisfy dependencies, and which are no longer required because the package they were installed for has been removed.

---

### Post by benevolent on 2008-06-04
thank you very much! :-)

---

