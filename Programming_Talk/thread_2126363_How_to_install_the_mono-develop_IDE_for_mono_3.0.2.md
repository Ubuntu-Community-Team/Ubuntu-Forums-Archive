---
title: "How to install the mono-develop IDE for mono 3.0.2 on Ubuntu 12.04.2 LTS 64?"
date: 2013-03-16
forum: Programming Talk
---

### Post by fnuxfl on 2013-03-16
Hi all,

I've downloaded (from the mono-project.com web site) and installed mono 3.0.2 for a specific purpose in /usr/lib on my Ubuntu 12.04.2 LTS 64 bit system using these commands:

```
wget -O Downloads/mono-3.0.2.tar.bz2 http://origin-download.mono-project.com/sources/mono/mono-3.0.2.tar.bz2 
tar -C Downloads -xjf Downloads/mono-3.0.2.tar.bz2
cd Downloads/mono-3.0.2
sudo ./configure --prefix=/usr
sudo make
sudo make install
```

Now, I'd like to install the mono-develop IDE, but I'm scared to use apt-get or synaptic since the Ubuntu standard installation install an old version of mono and furthermore doesn't install the shared libraries into /usr/lib.

Any help to install this IDE (or another one supporting mono 3.0.2) will be very appreciated. 

TIA.

---

