---
title: "[SOLVED] Help me PLZ!!!!!!!!!"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by mag1strate on 2008-11-26
I've been trying to download updates for my computer (Intrepid), but I keep on getting this error!:(

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by theozzlives on 2008-11-26
You have apt or synaptic running, if you don't type
```
sudo dpkg -a --configure
``` into a terminal box

---

### Post by ibuclaw on 2008-11-26
```
sudo lsof /var/cache/apt/archives/lock
```
That will tell you what process is using apt at the current time.

If you have reason to believe that it shouldn't be running, then kill the app with 
```
sudo killall **APPNAME**
```
or
```
sudo kill -9 **PID**
```
Where APPNAME is the name of the app running, and PID is the pid number.

Then run
```
sudo rm /var/cache/apt/archives/lock
```
And try again.

Regards
Iain

---

### Post by mag1strate on 2008-11-26
Thanks guys that worked but, when I begin to download the updates it tells me to insert a cd!?!?!:( 

Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)

---

### Post by Joeb454 on 2008-11-26
Click System &#8594; Administration &#8594; Software Sources

Then untick the CD as a software source. That should solve it, though you may need to run ```
sudo apt-get update
``` from a terminal before trying to install/update again

---

### Post by mag1strate on 2008-11-26
Thank You guys very much! I really appreciate what you have done!!:)

---

