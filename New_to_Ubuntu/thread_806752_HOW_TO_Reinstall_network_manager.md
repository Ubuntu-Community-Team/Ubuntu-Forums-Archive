---
title: "HOW TO? Reinstall network manager"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by rivercitybuntu on 2008-05-25
I'm running Heron 8.04. It installed fine and recognized my wireless adapter on installation - which had been a problem with earlier versions.

Since I was having trouble restoring connections after suspend, I tried using WICD. It replaces Network Manager.

WICD didn't authenticate to my network, so I uninstalled it. But now, I don't have any Network Manager and no way to make a wireless connection at all.

Can someone tell me how to do a NM reinstall in Ubuntu Hardy?

Thanks,

---

### Post by muted1987 on 2008-05-25
have you tried searching in synaptic package manager???

or even cmd line sudo apt-get Network Manager to see if the package exists

if it does

sudo apt-get install Network Manager

---

### Post by mbaker824 on 2008-05-25
> **rivercitybuntu said:**
> Can someone tell me how to do a NM reinstall in Ubuntu Hardy?

```
sudo apt-get install network-manager network-manager-gnome
```

---

### Post by rivercitybuntu on 2008-05-26
thanks, mbaker.

That's just what I was looking for. :)

---

