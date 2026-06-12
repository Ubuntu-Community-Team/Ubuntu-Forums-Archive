---
title: "Unzip problems"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Drezard on 2008-04-24
Im following this tutorial:

[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html)

and it says to run:

unzip -a 

on an .EXE, which fails. any ideas on how i could do this?

Daniel

---

### Post by spiderbatdad on 2008-04-24
try running the command cabextract on the file.
Also ndis-gtk can be useful for installing drivers with ndiswrapper. Ndis-gtk is in synaptic package manager.

---

### Post by Drezard on 2008-04-24
Nope Cabextract didn't do do anything... other ideas?

---

### Post by spiderbatdad on 2008-04-24
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by Joeb454 on 2008-04-24
You probably need to install the program *unzip* Open up synaptic and search for it, or in a terminal type ```
sudo aptitude update
sudo aptitude install unzip
```

---

### Post by spiderbatdad on 2008-04-24
> **Drezard said:**
> Nope Cabextract didn't do do anything... other ideas?

Check out the post above for installing ndiswrapper and bcm driver...however, cabextract didn't do anything? Did you get an error message? Are you in the right directory, ie, Desktop if the file is on your desktop?```
cd Desktop
cabextract file.exe
```

---

### Post by Joeb454 on 2008-04-24
My mistake. I didn't read the original post properly :(

Have you tried running ```
ndiswrapper file.exe
``` I'm no 100% sure if this works, I've only used nspluginwrapper, which could be a little different

---

