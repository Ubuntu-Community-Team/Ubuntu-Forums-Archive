---
title: "How to remove/downgrade packages from disabled repos"
date: 2009-08-04
forum: Repositories &amp; Backports
---

### Post by Dinth on 2009-08-04
Hi.
Today ive added external ppa repository in Synaptic, unfortunately, after upgrade, some of my applications broke. Ive disabled this repo in Synaptic, but updated packages still exists in my system. Is there any way to synchronize (with downgrading) packages in my system with enabled repositories? 
Manualy reinstalling packages will not work for my, because ive upgraded many of them.

---

### Post by 3togo on 2009-08-05
No easy method as far as I know. I would like to share my method though I know many many people will not agree at what I am doing. Also, wired connection is recommended.
1) sudo gedit /etc/apt/sources.list
replace every karmic to jaunty
2) ctrl-alt-F1
3) sudo apt-get remove x11-common
4) sudo apt-get update
5) sudo apt-get install ubuntu-desktop

---

