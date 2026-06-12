---
title: "package install from CD-ROM is there a way ..."
date: 2005-01-04
forum: Repositories &amp; Backports
---

### Post by flade on 2005-01-04
First of all this distro is what I was waiting for. 

Now I want to install aditiona packages (apache, mysql, ssh, etc....) I use APT and Synaptic. Both works fine to use from if you are connected to internet.

But what if you don't have internet connection. Is there a way to install packages from CD ?

Help?!



Happy, healthy and that all whishes come true in 2005.  =D>  =D> 


bye,

Fladé

---

### Post by zeroK on 2005-01-04
[QUOTE=flade]First of all this distro is what I was waiting for. 

Now I want to install aditiona packages (apache, mysql, ssh, etc....) I use APT and Synaptic. Both works fine to use from if you are connected to internet.

But what if you don't have internet connection. Is there a way to install packages from CD ?

Help?!



Happy, healthy and that all whishes come true in 2005.  =D>  =D> 


bye,

Fladé[/QUOTE]
 You could perhaps download packages (including their dependencies) and then place them in /var/cache/apt/archives :-)

---

### Post by az on 2005-01-04
Apache, mysql, php4 and ssh all included on the cd.

They are not installed by default.

---

### Post by flade on 2005-01-04
Tnx for help.

I tried apt-get -d install [package name] and it put it to /var/cache/apt/archives .

Next time I'll try man before posting (i feel so ...)



-------------
++   Fladé

---

### Post by tiiim on 2005-01-05
[QUOTE=flade]Tnx for help.

I tried apt-get -d install [package name] and it put it to /var/cache/apt/archives .

Next time I'll try man before posting (i feel so ...)



-------------
++   Fladé[/QUOTE]
 in future you can also add cds to ur source list... Ubuntu cd is there by default but say if you ever get a Hoary cd or whatever you can add it on the list of sources.

---

