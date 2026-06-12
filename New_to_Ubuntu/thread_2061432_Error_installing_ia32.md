---
title: "Error installing ia32"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by afixane on 2012-09-22
Hi :D

I wanna install ia32libs, but i got this error from synaptic
```
E: /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_i386.deb: './usr/share/doc/libjack-jackd2-0/buildinfo.gz' is different from the same file on the system


```

Running Lubuntu 12.04 amd64

---

### Post by daslinkard on 2012-09-23
> **afixane said:**
> Hi :D

I wanna install ia32libs, but i got this error from synaptic
```
E: /var/cache/apt/archives/libjack-jackd2-0_1.9.8~dfsg.2-1precise1_i386.deb: './usr/share/doc/libjack-jackd2-0/buildinfo.gz' is different from the same file on the system


```Running Lubuntu 12.04 amd64

You can try this first....
**To install 32-bit libraries on a 64-bit linux system**

  Install:```
  $ apt-get install ia32-libs   
```To install 32-bit libraries for development  Install: ```
  $ apt-get install lib32gcc1 libc6-i386 lib32z1 lib32stdc++6 
```  ```
$ apt-get install lib32asound2 lib32ncurses5 lib32gomp1 lib32z1-dev lib32bz2-dev   
``````
$ apt-get install g++-multilib
```   You may need this too, or it may be a virtual package already provided: 
  ```
$ apt-get install ia32-libs-gtk
```   You may need a symlink, which g++-multilib may set up for you automatically:```

  $ ln -s /usr/lib32/libstdc++.so.6 /usr/lib32/libstdc++.so
``` 


Here is the [link]("http://sixarm.com/about/ubuntu-apt-get-install-ia32-for-32-bit-on-64-bit.html")

---

