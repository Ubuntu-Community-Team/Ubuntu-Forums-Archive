---
title: "kdevelop installation trouble"
date: 2007-09-30
forum: Programming Talk
---

### Post by Seismosaur on 2007-09-30
I was trying to install kdevelop data .deb package with gdebi, but it kept telling me i needed to be root to install the package, and wouldn't let me install it. I do not have internet on my linux-comp. so i can paste the terminal in here. I also tried using apt-get install, but that just told me it couldn't find the package, please help! :(

---

### Post by dolgion1 on 2007-11-02
Hi, 
now, im a newbie myself, but i think i can help here.
there are 2 ways to install a package on ubuntu:
1. by Synaptic Package Manager (which is the easier way) 
2. by terminal 

to install the .deb package go to the folder containing the package file and type "sudo apt-get install <packagefile.deb>"
then type your root-password and it should install automatically.
of course, you need to know the root-password :)

---

### Post by carlosjuero on 2007-11-03
> **Seismosaur said:**
> I was trying to install kdevelop data .deb package with gdebi, but it kept telling me i needed to be root to install the package, and wouldn't let me install it. I do not have internet on my linux-comp. so i can paste the terminal in here. I also tried using apt-get install, but that just told me it couldn't find the package, please help! :(
Have you tried running gdebi as sudo? i.e. ```
sudo gdebi <package name>
```

---

