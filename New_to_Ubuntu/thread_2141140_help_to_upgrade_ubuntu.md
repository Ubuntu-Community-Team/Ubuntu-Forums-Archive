---
title: "help to upgrade ubuntu"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by vlgngl on 2013-05-01
I am using ubuntu 12.10 quantal and I want to upgrade last version of ubuntu, I need your helps.. ?

---

### Post by ibjsb4 on 2013-05-01
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo do-release-upgrade
```

---

### Post by vlgngl on 2013-05-01
thanks for your contribution but the error in below was occured. I dont know what i should do 



Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,206 kB]                                                  
Fetched 1,206 kB in 0s (0 B/s)                                                 
authenticate 'raring.tar.gz' against 'raring.tar.gz.gpg' 
extracting 'raring.tar.gz'

Reading cache


A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

Traceback (most recent call last): 

File "/tmp/ubuntu-release-upgrader-uzchwd/raring", line 10, in 
<module> 
sys.exit(main()) 

File 
"/tmp/ubuntu-release-upgrader-uzchwd/DistUpgrade/DistUpgradeMain.py", 
line 237, in main 
save_system_state(logdir) 

File 
"/tmp/ubuntu-release-upgrader-uzchwd/DistUpgrade/DistUpgradeMain.py", 
line 130, in save_system_state 
scrub_sources=True) 

File "/tmp/ubuntu-release-upgrader-uzchwd/DistUpgrade/apt_clone.py", 
line 147, in save_state 
self._write_state_installed_pkgs(sourcedir, tar) 

File "/tmp/ubuntu-release-upgrader-uzchwd/DistUpgrade/apt_clone.py", 
line 177, in _write_state_installed_pkgs 
cache = self._cache_cls(rootdir=sourcedir) 

File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in 
__init__ 
self.open(progress) 

File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in 
open 
self._list.read_main_list() 

SystemError: E:Malformed line 56 in source list /etc/apt/sources.list 
(dist parse)

---

### Post by ibjsb4 on 2013-05-01
Please post the output of:

```
cat -n /etc/apt/sources.list
```

---

