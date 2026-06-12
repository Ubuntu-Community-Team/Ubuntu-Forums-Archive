---
title: "HOWTO: Install Nvidia Beta Drivers from Nvidia Website"
date: 2006-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by buckethead27 on 2006-09-25
Forgive me if I am wrong, but I keep getting asked how to install the nvidia beta drivers from their website, and as far as I can see, everyone is using sudo apt-get install nvidia-glx, which won't get you beta. If you want beta, follow this post!


Download your drivers from [www.nvidia.com](www.nvidia.com).

Jump into a consle and type in:
```
sudo apt-get upgrade
sudo apt-get install build-essential
```

Press ctrl+alt+F1 to switch out of gnome.

To kill X:
```
sudo /etc/init.d/gdm stop
```
To install drivers:
```
sudo sh /(nvidiadrivers)
```
To restart X:
```
sudo /etc/init.d/gdm start
```

That's it! You might want to restart, but it is not needed.

---

### Post by Fr@nKy on 2006-10-04
I doesn't work! It say it needs to get something to my Kernel and that will try to find it on NVIDIA server and than it doesn't fin it so it tries to compile then it fails.

I'm using Dapper BTW

---

### Post by Fr@nKy on 2006-10-04
It says that I need to kernel source tree btw ;) What can I do?

---

### Post by Fr@nKy on 2006-10-04
BTW if I manage to install this drivers how do I get AIGLX on Dapper??

---

### Post by phoenix49 on 2006-10-05
Install linux-headers and you will be able to easily install drivers. Also remove nvidia-glx with --purge, and you should also disable linux-restricted drivers from /etc/linux-restricted/.. Disable driver "nv".
More info is on nvidia forums :)

---

