---
title: "get ride of flash-plugin installer 'fake Error&quot;"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by shevin on 2012-01-15
when I installed the new ubuntu , I had some difficulty to install the flash plugin ,(because I use 64bit) I solved that flash plugin and it works now ,
but still whenever I install anything , I still have a FAKE ERROR in apt-get

I tried to use apt-get fix thing it wont help , how can I get ride of this ugly error message ?
 
> Errors were encountered while processing:
 flashplugin-installer
Setting up flashplugin-installer (11.1.102.55ubuntu0.11.10.1) ...
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1


---

### Post by Fernhill Linux Project on 2012-01-15
'ubuntu restricted extras' contains flash player and many other media codecs, and can be installed from ubuntu software centre or a terminal using 
'sudo apt-get install ubuntu-restricted-extras'

---

### Post by shevin on 2012-01-15
> **Fernhill Linux Project said:**
> 'ubuntu restricted extras' contains flash player and many other media codecs, and can be installed from ubuntu software centre or a terminal using 
'sudo apt-get install ubuntu-restricted-extras'

sorry you didnt get my meaning, 
I have installed flash, it works fine,

but for some reason this fake error in the apt-get keeps showing whenver I install any OTHER application .

other applications install fine too, but at the end apt-get returns an error about flash , I want that error to be gone , it is ugly

---

### Post by shevin on 2012-01-15
I fixed it using this 

apt-get how to fix very broken packages

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

