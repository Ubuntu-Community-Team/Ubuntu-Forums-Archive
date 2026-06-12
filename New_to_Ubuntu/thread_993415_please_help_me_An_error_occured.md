---
title: "please help me An error occured"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by dmx2007 on 2008-11-25
i cant do any thing without sawing this :

E: Type ‘See’ is not known on line 4 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

---

### Post by taurus on 2008-11-25
There is something wrong with line 4 in your /etc/apt/sources.list.  Therefore, open a terminal and edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of line 4 to comment it out.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

