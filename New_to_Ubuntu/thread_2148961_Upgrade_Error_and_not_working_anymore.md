---
title: "Upgrade Error and not working anymore"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by uzapuca on 2013-05-27
Hi guys,
While upgrading to 13 systemr it seems i accidentaly overwrites some files and now i cannot upgrade anymore. I tried to do it by Terminal and is not working either. Here is the code i get

Check new Ubuntu version
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 111, in <module>
    useProposed=options.proposed_release)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 90, in __init__
    self.flavor_name = get_ubuntu_flavor_name()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 447, in get_ubuntu_flavor_name
    pkg = get_ubuntu_flavor_package(cache=cache)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 437, in get_ubuntu_flavor_package
    cache = apt.Cache()
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 105, in __init__
    self.open(progress)
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 151, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:El paquete dassault-systemes-draftsight:i386 need to be reinstalled but the file cannot be found

How can i clean the System or Cache and start all over nice with Ubuntu without having the Upgrade Problem all the time?

Best,

---

### Post by fantab on 2013-05-27
How about doing a fresh and clean install from ubuntu DVD/USB? If you have any data to rescue then you can use Live Ubuntu to do so.

Upgrades can be messy for various reasons.

---

### Post by ibjsb4 on 2013-05-27
> **fantab said:**
> How about doing a fresh and clean install from ubuntu DVD/USB? If you have any data to rescue then you can use Live Ubuntu to do so.

Upgrades can be messy for various reasons.

Very good idea, but if you want to try to save you current install ..

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

Good luck

---

### Post by uzapuca on 2013-05-28
Hi guys,
thanks for the very interesting info! I will try to save what i have before a new clean install, because of the time consuming process the back up takes.

I will let you know how it went ;)

Best,

---

### Post by uzapuca on 2013-05-28
It seems i was able to do some upgrade. Unfortunately, the Upgrade APP via software is not working anymore. Too bad. I thought i was able to fix it with those command in Terminal.

---

