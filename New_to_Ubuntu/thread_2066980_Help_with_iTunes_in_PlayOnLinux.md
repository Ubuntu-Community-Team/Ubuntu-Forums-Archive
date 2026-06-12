---
title: "Help with iTunes in PlayOnLinux"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by JSF16 on 2012-10-05
Alrighty, got a new iPod touch and I want to set it up with iTunes which -thanks to PlayOnLinux- I can. Or, I should be able to. I've followed the tutorials, have latest version of PlayOnLinux, and installed iTunes 7. However, when all is said and done, when I try and run iTunes 7, a window pops up which says 'the file iTunes library.itl cannot be read because it was created by a newer version of iTunes.' Now previously I had installed the latest version of iTunes with Wine, and I thought that might be the 'newer version of iTunes' so I uninstalled it with Wine. But the problem persists. Any help for a poor new Ubuntu user?

---

### Post by josephmills on 2012-10-05
If you are on 12.04 I made ppa for playonlinux that I upkeep and itunes 10 works 

[https://launchpad.net/~josephjamesmills/+archive/beta](https://launchpad.net/~josephjamesmills/+archive/beta)

could you please open you terminal and enter in 
```
apt-cache policy playonlinux
```

Then paste that back here.

---

### Post by Krist Blomme on 2012-12-23
Joseph
seems this post didn' continue , however I have the same problem , so I copy the requested info 


krist@XIIApostoli:~$ apt-cache policy playonlinux
playonlinux:
  Installed: 4.1.8
  Candidate: 4.1.8
  Version table:
 *** 4.1.8 0
        500 [http://deb.playonlinux.com/](http://deb.playonlinux.com/) precise/main amd64 Packages
        100 /var/lib/dpkg/status
     4.0.14-1 0
        500 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise/multiverse amd64 Packages
krist@XIIApostoli:~$ 


tnx

---

