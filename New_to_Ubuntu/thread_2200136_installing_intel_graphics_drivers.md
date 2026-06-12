---
title: "installing intel graphics drivers"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by HappyAsHellas on 2014-01-17
How do I install graphics drivers? When I check in system details it says graphics driver unknown.

---

### Post by deadflowr on 2014-01-17
It's a weird behavior, but don't worry, the intel graphics drivers are built into the system.
If you want to see what the drivers are, install the package mesa-utils.
Either through the software center, or run
```
sudo apt-get install mesa-utils
```
in a terminal.
(Sidenote, the terminal will ask for a password, but the password field will not show the input of the keystrokes, type it as best you remember it)

---

### Post by sandyd on 2014-01-17
> **George_McEwan said:**
> How do I install graphics drivers? When I check in system details it says graphics driver unknown.

also
if you are using Ubuntu 13.10, and intend to continue upgrading as new releases become avaliable, check out the  Intel Graphics driver installer ([http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html)) for the latest drivers direct from intel

---

