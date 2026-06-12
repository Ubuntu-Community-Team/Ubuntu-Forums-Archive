---
title: "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"
date: 2022-07-06
forum: New to Ubuntu
---

### Post by edith-nuaa on 2022-07-06
Hi everyone,
I was trying to install freeglut3-dev, but i got this info when i followed instructions online. Is there any method to solve this problem? I already tried to use "--fix-missing" and "sudo apt-get update" before installation but they are not helping.

```
edith@Edith:~$ sudo apt-get install freeglut3-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  freeglut3 libegl-dev libegl-mesa0 libegl1 libgbm1 libgl-dev libgl1-mesa-dev libgles-dev libgles1 libgles2
  libglu1-mesa libglu1-mesa-dev libglvnd-dev libglx-dev libopengl-dev libopengl0 libwayland-server0
The following NEW packages will be installed:
  freeglut3 freeglut3-dev libegl-dev libegl-mesa0 libegl1 libgbm1 libgl-dev libgl1-mesa-dev libgles-dev
  libgles1 libgles2 libglu1-mesa libglu1-mesa-dev libglvnd-dev libglx-dev libopengl-dev libopengl0
  libwayland-server0
0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 198 kB/1016 kB of archives.
After this operation, 6162 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Err:1 http://archive.ubuntu.com/ubuntu focal/universe amd64 freeglut3 amd64 2.8.1-3
  Connection failed [IP: 185.125.190.36 80]
Err:2 http://archive.ubuntu.com/ubuntu focal/universe amd64 freeglut3-dev amd64 2.8.1-3
  Connection failed [IP: 185.125.190.39 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/f/freeglut/freeglut3_2.8.1-3_amd64.deb  Connection failed [IP: 185.125.190.36 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/f/freeglut/freeglut3-dev_2.8.1-3_amd64.deb  Connection failed [IP: 185.125.190.39 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
```

---

### Post by TheFu on 2022-07-08
If you can't get to 185.125.190.39, then you'll want to wait and try again later, or look for a different repo, perhaps one in your country?
```
$ ping 185.125.190.39 
```
is working from here.

---

