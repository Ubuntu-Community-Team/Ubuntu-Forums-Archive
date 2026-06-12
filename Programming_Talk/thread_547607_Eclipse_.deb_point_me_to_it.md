---
title: "Eclipse .deb point me to it"
date: 2007-09-10
forum: Programming Talk
---

### Post by cevil203 on 2007-09-10
im lookin for eclipse java programming tool for ubuntu linux. i would greatly appreciate a .deb file. cuz i cant figure out the .tar.gz files.

---

### Post by pmasiar on 2007-09-10
use synaptic

---

### Post by Tomosaur on 2007-09-10
> **cevil203 said:**
> im lookin for eclipse java programming tool for ubuntu linux. i would greatly appreciate a .deb file. cuz i cant figure out the .tar.gz files.


Isn't Eclipse in the repositories?
```

sudo apt-get install eclipse

```

The default Eclipse setup when installed this way uses the GCJ Java compiler. I prefer Sun's compiler, but you'll have to set that up manually.

---

### Post by [h2o] on 2007-09-10
Yep, install eclipse through APT, and then any of the sun-java packages. Then change /etc/eclipse/java_home to use the sun-java runtime instead of gcj. That's how I have it setup right now, and it works really nice.

---

### Post by CptPicard on 2007-09-10
On the other hand, I always prefer having the latest eclipse straight from the source... the tgz's aren't that hard. All you do is sudo -s -H yourself a root shell, cd to /opt, move the eclipse-sdk-....tar.gz there, then tar zxf eclipse-sdk...tar.gz to extract the package, remove the original archive file and start using (/opt/eclipse/eclipse). Removal is as easy as just removing the directory from /opt.

---

### Post by aitorcalero on 2007-09-11
Even easier is to download eclipse and extract it in home directory

---

