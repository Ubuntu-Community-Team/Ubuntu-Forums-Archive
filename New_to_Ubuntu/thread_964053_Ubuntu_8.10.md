---
title: "Ubuntu 8.10"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-10-30
Ok, well I'm installing the live disk now. Everything is working better than ever. My wireless has always been fast and worked just fine on my laptop (just as good is windows which my laptop was made for) but now I must admit. The wireless connects and runs much much faster. It's actually beating my windows side which again I would like to remind you this computer was made to run. So I am very impressed with that. My only question is I can't find advanced desktop settings any more in this version? Please help me with that.

---

### Post by jbrown96 on 2008-10-30
You need to install it ```
sudo apt-get install ccsm
```

---

### Post by RadiationHazard on 2008-10-30
```
jordan@jordan-laptop:~$ sudo apt-get install ccsm
[sudo] password for jordan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm
jordan@jordan-laptop:~$ 

```

---

### Post by eolson on 2008-10-30
Cheat!   Use add/remove do a search and ccsm.  It's there.

---

### Post by jbrown96 on 2008-10-30
My bad. The name has changed ```
sudo apt-get install compizconfig-settings-manager

```

---

