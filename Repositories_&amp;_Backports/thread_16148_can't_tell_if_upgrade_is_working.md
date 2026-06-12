---
title: "can't tell if upgrade is working"
date: 2005-02-19
forum: Repositories &amp; Backports
---

### Post by G.I.Josh on 2005-02-19
I typed in: sudo apt-get update && sudo apt-get upgrade, and I got the following feedback:

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Reading Package Lists... Done
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Does that last line meen it didn't upgrade anything?  It's my first time running it, so I know there should be updates.  Thanks

---

### Post by mendicant on 2005-02-20
You'd only get upgrades if you used security updates, too:

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted universe

in your apt/sources.list file.

Also, you should probably use aptitude instead of apt-get.  Similar command line interface, much better behavior (automatic dependency tracking among others).  Aptitude also has a curses gui if you need it.

---

### Post by kassetra on 2005-02-20
You could also try Synaptic, which is installed into ubuntu by default:
 Computer->System Configuration->Synaptic Package Manager
 
 It might be easier to actually see what's going on with your packages.  :)

---

