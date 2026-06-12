---
title: "flash player"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by mrrod on 2008-06-27
I've downloaded flash player so i can view the vids on youtube but i have no idea how to install it,can anyone enlighten me ?

---

### Post by wormser on 2008-06-27
Install it via the repositories.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by avtolle on 2008-06-27
I'd try the following: from Synaptic, check if gnash (a FOSS flash "replacement") is installed; mark it (gnash, the mozilla plugin for gnash, and gnash common) for total removal, hit apply. Then, install flash-plugin-nonfree from Synaptic, and see if that gets you where you want to be.

---

### Post by aysiu on 2008-06-27
The standard method is to visit a site with Flash and follow the *Install Missing Plugins* drop-down message.

More details here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

