---
title: "Howto: install xmoto-0.1.12 (newest)"
date: 2006-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Fredde on 2006-05-15
Follow all those steps, and you'll have xmoto-0.1.12 running.
```
sudo apt-get install dpkg-dev fakeroot debhelper build-essential libjpeg62-dev libpng12-dev zlib1g-dev libsdl1.2debian liblua50-dev liblualib50-dev libode0-dev libsdl-mixer1.2-dev
```
```
wget http://heanet.dl.sourceforge.net/sourceforge/xmoto/xmoto-0.1.12-src.tar.gz
```
```
gunzip < xmoto-0.1.12-src.tar.gz | tar xvf -
```
```
cd xmoto-0.1.12
```
```
./configure
```
```
make
```
```
sudo make install
```

---

### Post by InsomniacAgent on 2008-06-19
Will this run on hardy heron?

---

### Post by ShirishAg75 on 2008-06-21
InsomiacAgent, 
 You don't need to do that anymore. xmoto is now in universe. So what you need to do is simply :-

1. Go to Administration > Synaptic Package Manager
2. Give your admin password
3. Click on Reload 
4 After Reload is complete do any updates, if required or given.  
5. Look/search for xmoto 
6. when it finds xmoto click in the rectangular box 
7. Click apply. 
8. When Synaptic downloads and installs for you let it do its work
9. After its installed and everything close Synaptic Network Manager. 
10. Go to Applications > Games Find xmoto therein 
11. Start playing ;)

---

