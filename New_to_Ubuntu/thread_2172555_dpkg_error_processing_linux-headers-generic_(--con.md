---
title: "dpkg: error processing linux-headers-generic (--configure):  dependency problems - le"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by ravc2 on 2013-09-05
cant download and install any software as I get below message 


installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 661613 files and directories currently installed.) 
Unpacking linux-headers-3.8.0-30 (from .../linux-headers-3.8.0-30_3.8.0-30.44_all.deb) ... 
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: invalid code lengths set' 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/linux-headers-3.8.0-30_3.8.0-30.44_all.deb (--unpack): 
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-headers-3.8.0-30_3.8.0-30.44_all.deb 
dpkg: dependency problems prevent configuration of linux-headers-3.8.0-30-generic: 
 linux-headers-3.8.0-30-generic depends on linux-headers-3.8.0-30; however: 
  Package linux-headers-3.8.0-30 is not installed. 
 
dpkg: error processing linux-headers-3.8.0-30-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-headers-generic: 
 linux-headers-generic depends on linux-headers-3.8.0-30-generic; however: 
  Package linux-headers-3.8.0-30-generic is not configured yet. 
 
dpkg: error processing linux-headers-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-headers-generic-pae: 
 linux-headers-generic-pae depends on linux-headers-generic (= 3.8.0.30.48); however: 
  Package linux-headers-generic is not configured yet. 
 
dpkg: error processing linux-headers-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-headers-generic (= 3.8.0.30.48); however: 
  Package linux-headers-generic is not configured yet. 
 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic-pae: 
 linux-generic-pae depends on linux-generic (= 3.8.0.30.48); however: 
  Package linux-generic is not configured yet. 
 
dpkg: error processing linux-generic-pae (--configure): 
 dependency problems - leaving unconfigured

---

### Post by bluefrog on 2013-09-05
looks like not enough disk space left to me.

try to free some space in /

can get rid of the .debs in /var/cache/apt/archives/ to begin with

---

### Post by Jonathan Precise on 2013-09-05
> **ravc2 said:**
> cant download and install any software as I get below message 


```
installArchives() failed: (Reading database ... 661613 files and directories currently installed.) 
Unpacking linux-headers-3.8.0-30 (from .../linux-headers-3.8.0-30_3.8.0-30.44_all.deb) ... 
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: invalid code lengths set' 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/linux-headers-3.8.0-30_3.8.0-30.44_all.deb (--unpack): 
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-headers-3.8.0-30_3.8.0-30.44_all.deb 
dpkg: dependency problems prevent configuration of linux-headers-3.8.0-30-generic: 
 linux-headers-3.8.0-30-generic depends on linux-headers-3.8.0-30; however: 
  Package linux-headers-3.8.0-30 is not installed. 
 
dpkg: error processing linux-headers-3.8.0-30-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-headers-generic: 
 linux-headers-generic depends on linux-headers-3.8.0-30-generic; however: 
  Package linux-headers-3.8.0-30-generic is not configured yet. 
 
dpkg: error processing linux-headers-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-headers-generic-pae: 
 linux-headers-generic-pae depends on linux-headers-generic (= 3.8.0.30.48); however: 
  Package linux-headers-generic is not configured yet. 
 
dpkg: error processing linux-headers-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-headers-generic (= 3.8.0.30.48); however: 
  Package linux-headers-generic is not configured yet. 
 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic-pae: 
 linux-generic-pae depends on linux-generic (= 3.8.0.30.48); however: 
  Package linux-generic is not configured yet. 
 
dpkg: error processing linux-generic-pae (--configure): 
 dependency problems - leaving unconfigured
```

Try: ```
sudo apt-get -f install linux-headers-3.8.0-30
sudo apt-get --silent update
sudo dpkg --configure -a
```

That should fix it.

---

### Post by ibjsb4 on 2013-09-05
And I am thinking a system cleaning may help if that didn't work.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

```
sudo apt-get clean
sudo apt-get autoremove
sudo rm -r /var/lib/apt/lists/*
sudo mkdir -p /var/lib/apt/list/partial
sudo apt-get update
```

---

