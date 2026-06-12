---
title: "software sources does not work anymore"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by iamnobody on 2008-11-03
I upgraded from 8.04 to 8.10, and now I can't open Software Sources.  The first time I try to use it (each time I boot up), I am prompted for my password.  I enter it and then nothing shows up.  I try clicking Software Sources again, and nothing happens.

---

### Post by taurus on 2008-11-03
What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by iamnobody on 2008-11-04
they both seem to work.  sudo apt-get update hits a bunch of repositories. the final messages are

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Fetched 8962B in 2s (3054B/s)
Reading package lists... Done

sudo apt-get upgrade also seems to work, printing

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

