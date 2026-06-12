---
title: "Simple Flash 10.0.32 install under any ubuntu"
date: 2009-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by leaferz on 2009-09-11
For some reason the apt method never seemed to work for me so here's a 5 step method that has worked every time.

```
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.21_all.deb
sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb
```

or just convert it to a script to run it all together. 

```

#!/bin/sh

wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu1_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.21_all.deb
sudo dpkg -i gsfont*.deb
sudo dpkg -i flash*.deb
```

Enjoy :)

---

### Post by wieman01 on 2009-09-11
Nice, I'll try it out later myself.

**_EDIT:_**
I just gave it a shot. Youtube works perfectly. Thank you!

---

