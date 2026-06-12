---
title: "Problem With synaptic package manager"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by j-d3r on 2008-09-19
i am just a beginner in linux. and this is my first post as i am having a problem in synaptic package manager and the error it showing is:-

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please help me out>>>
i have done the updates...
and installed many softwares, but when when i was installing dock for linux my laptop hanged and so i restarted..
and after that i am suffering the problem>>>
please help

---

### Post by iaculallad on 2008-09-19
You need to add the 'sudo' before the command to give you a bit of privilege to maintain your system: Now on your terminal:

```
sudo dpkg --configure -a
```

---

### Post by waspbr on 2008-09-19
don't worry every now and then, something like that may happen, it is not serious. 

just open yourself a terminal window  (Applications>accessories>terminal) and paste the following as the message suggested

```
sudo dpkg --configure -a
```

enter ur admin password and it should be fine

then just for funzies do

```
sudo apt-get update
sudo apt-get upgrade
```

---

