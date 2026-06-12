---
title: "Installing HOMM 3 on Kubuntu 6.06 with Wine"
date: 2006-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by phase on 2006-06-10
You need:
1. CD with HOMM 3
2. Wine, msttcorefonts
3. KUbuntu 6.06 + NVidia/ATI drivers

How to install Wine:
**sudo gedit /etc/apt/sources.list**

_insert these lines on the end of the file_

## WineHQ APT Repository
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

**save the file**

sudo apt-get update
sudo apt-get install wine 
sudo apt-get install msttcorefonts

[B]run winecfg to configure Wine for you software

then installing HOMM3, after install write at terminal: wine 'your path/HEROES3.EXE'

---

