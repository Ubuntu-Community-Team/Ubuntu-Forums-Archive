---
title: "E: Unable to locate package tree"
date: 2019-01-27
forum: New to Ubuntu
---

### Post by bumpping.rabbit on 2019-01-27
I'm new to linux. I have this problem (as titled) when I try to use 'tree' command. I tried to fixed it but got the following. Any ideas?


bumppingrabbit@ubuntu:~/Desktop$ sudo add-apt-repository universe
'universe' distribution component is already enabled for all sources.


bumppingrabbit@ubuntu:~/Desktop$ sudo apt-get install tree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tree


bumppingrabbit@ubuntu:~/Desktop$ sudo apt install tree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tree


bumppingrabbit@ubuntu:~/Desktop$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

---

### Post by howefield on 2019-01-27
Ubuntu 17.04 has reached end of life, best to start again with a currently supported release, preferably version 18.04 for maximum support period.

The repositories for 17.04 have been archived hence the package manager will not find the "tree" package where it expects it to be.

---

