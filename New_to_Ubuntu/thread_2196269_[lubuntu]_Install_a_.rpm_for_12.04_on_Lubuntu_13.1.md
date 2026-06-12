---
title: "[lubuntu] Install a .rpm for 12.04 on Lubuntu 13.10 works ?"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by exortifier on 2013-12-28
Hi,

I'm very new to Linux so I'm still a bit confused about what I can or can't do.
I'd like to use one software which is for Ubuntu 12.04 LTS and I'd like to know whether I can install it or not on Lubuntu 13.10.

The file is a .rpm and I'm a bit confused because from what I understood .rpm are not intended to be installed on Ubuntu. But it's indicated as the "Ubuntu version" of the software. 

Thanks for reading.

---

### Post by hoopia on 2013-12-28
You should be able to install it, but first you'll need to Alien to convert it (or you can install directly via Alien). Check this out:

[http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/)

---

### Post by exortifier on 2013-12-28
Thanks for your answer, I finally succeeded but alien didn't work. 

I found a .deb version then about 4-5 dependencies were misssing, I had to download all of them from packages.ubuntu.fr and install them with GDebi. After that I had to modify a path into a file to make the whole things works, because when I was sourcing this file, before using the software, one path was not correct into the sourced file. But anyway I'm happy it eventually works.

Now I wonder, if later I want to remove everything is there an easy way to do it or do I have to write down all the name of the packages I installed with GDebi ?

---

### Post by hoopia on 2013-12-28
Glad you found a working DEB. Uninstalling is fairly simple with **dpkg**, and if you have unused dependencies you can run something like **apt-get autoremove** to get rid of them afterwards.

---

### Post by exortifier on 2013-12-29
Thanks !

---

