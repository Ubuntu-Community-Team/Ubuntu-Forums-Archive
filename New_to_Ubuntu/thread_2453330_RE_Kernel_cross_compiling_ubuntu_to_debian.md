---
title: "RE: Kernel cross compiling ubuntu to debian"
date: 2020-11-08
forum: New to Ubuntu
---

### Post by kj4qwt on 2020-11-08
Hello team,

Is there any known good way to cross compile the ubuntu kernel with the debian kernel.

What I mean by this is, how does one take a PPA kernel package designed for ubuntu and install it in debian.

Here is a link example if this helps: [https://github.com/b-rad-NDi/Ubuntu-media-tree-kernel-builder](https://github.com/b-rad-NDi/Ubuntu-media-tree-kernel-builder)

Any suggestions would be greatly appreciated.

-Robert

---

### Post by wildmanne39 on 2020-11-08
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by garvinrick4 on 2020-11-08
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
Pick your kerne think 5.9 latest stable
##Choose generic modules, Headers and image and the all.deb 
4 of them download and save each one. (Low latency for the light build)
##Make sure only 4 .deb files in one location be it Downloads, Desktop ect..
Open a Terminal:
> cd Downloads
> ls
##check to make sure only .deb files or move them to say Desktop to install;
> sudo dpkg -i *.deb
> sudo shutdown -r now
##Installed and booting from new kernel.

---

