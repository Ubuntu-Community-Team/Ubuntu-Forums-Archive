---
title: "FIrst Class Client Issues"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by deadyeti on 2008-07-26
I am using Ubuntu 8.04 and recently installed the first class client.  The client tries to load from GUI and then disappears, and in the terminal I get this message when I run $fcc;

kirk@kirk-laptop:~$ fcc
fcc: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

Any ideas would be splendid.


[COLOR=Red]On a second note, does anyone know how to set a folder to use as a D drive in Wine?  I dont want to run out of room in my home folder.[/COLOR] Got it working :P

Thanks!

---

### Post by Tim Sharitt on 2008-07-26
In a terminal
```
sudo apt-get install libqt3-mt
```

---

### Post by deadyeti on 2008-07-26
kirk@kirk-laptop:~$ sudo apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt3-mt is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kirk@kirk-laptop:~$

---

