---
title: "[SOLVED] Opera"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-07-21
Yesterday all was fine, now today, without any changes, I get (see screenshot) and the file browser window behind opera ??  I have tried to reinstall package, but error still remains.  When I look in Add Remove, Opera is not listed, same with synaptic.  How do I totally uninstall Opera so I can do a fresh install ??
[ATTACH]78454[/ATTACH]

---

### Post by tuxxy on 2008-07-21
Opera will be in synaptic, search for opera

In the terminal you could remove it by

```
sudo apt-get remove opera*
```

---

### Post by gandaran on 2008-07-21
> **gettinoriginal said:**
> Yesterday all was fine, now today, without any changes, I get (see screenshot) and the file browser window behind opera ??  I have tried to reinstall package, but error still remains.  When I look in Add Remove, Opera is not listed, same with synaptic.  How do I totally uninstall Opera so I can do a fresh install ??
[ATTACH]78454[/ATTACH]

if you don't find it in synaptic, how did you install it ? what type of package?

---

### Post by gettinoriginal on 2008-07-21
It was in synaptic when I installed it, but after the error message, search of synaptic showed nothing.  I did uninstall it with sudo, then it was back in synaptic, but now I get this ](*,)

[ATTACH]78456[/ATTACH]

---

### Post by tuxxy on 2008-07-21
Open terminal

```
killall opera
```

try now

---

