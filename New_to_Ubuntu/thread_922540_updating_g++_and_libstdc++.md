---
title: "updating g++ and libstdc++"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by herbert tamayo on 2008-09-17
Hi, I have network restrictions to connect to several ubuntu repos, so, every time I need to update some packages i have to do it manually, so I have the next questions:

1. I have the packages g++-4.3(ver 4.3.2-1) and libstdc++6-4.3-dev (ver 4.3.2-1) if i try to install first g++ (using dpkg -i) I get the message that it has dependences with libstdc++6, then, if I try to install first libstdc++ i get the same message that it has dependences with g++. My question is: how can I install those packages? which one first? is there any "force" option?

2. Currently I have the 2.6.17 kernel, if I want to upgrade to 2.6.26 for example, which option is better: a) download the deb package? b) download the tar.gz. from kernel.org?
When the new kernel is installed, would be some modules disabled?(for example XGL Accel)

Regards

---

### Post by acidsolution on 2008-09-17
well installing g++ and libstdc. I guess you can download the packages  . Download the .deb packages and than copy the packages to 
```

/var/cache/apt/archives/

```
and than now try to run  
```

sudo apt-get install g++  

```

apt-get first tries to find in /var/cache/apt/archives/ directory if not found than seek for internet. 

I guess this will help you to install g++.
for kernel 
download the latest stable release for ubuntu you are using ..
so .deb is preferable for me :)

---

