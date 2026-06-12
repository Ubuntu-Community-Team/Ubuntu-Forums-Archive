---
title: "Flash Disaster"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by neon100 on 2008-05-24
I've tried all methods of installing flash player.
But i cannot get flash working in my browser. I really feel dejected. 
Please dont refer to any other tutorial. Just explain some miracle here.
I've used the following command 

sudo apt-get install flashplugin-nonfree

but it gives messages that its already installed.

SOS !

---

### Post by lswest on 2008-05-24
```
sudo apt-get remove --purge flashplugin-nonfree gnash mozilla-plugin-gnash
```

then run ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install flashplugin-nonfree
```

See if that helps.

---

### Post by bubba_169 on 2008-05-24
What browser are you using?

---

