---
title: "trouble updating on ubuntu 7.10"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by octopusfinley on 2008-11-21
I recently got some updates on package manager and was able to install all of them except three, hpijs, hplip, and hplip-data
I tried installing with apt-get upgrade through the terminal after clearing the cache and apt-get update but I still can't install them. I get a 302 error and it says there's a size mismatch. Any ideas?
finley

---

### Post by LowSky on 2008-11-22
i would download from the web directly if you really need hplip
[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

its a very simple install, here the instructions
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by nhasian on 2008-11-22
you could try:

```
sudo apt-get --fix-broken upgrade hpijs hplip hplip-data
```

or

```
sudo apt-get --force-yes upgrade hpijs hplip hplip-data
```

---

### Post by kansasnoob on 2008-11-22
> **octopusfinley said:**
> I recently got some updates on package manager and was able to install all of them except three, hpijs, hplip, and hplip-data
I tried installing with apt-get upgrade through the terminal after clearing the cache and apt-get update but I still can't install them. I get a 302 error and it says there's a size mismatch. Any ideas?
finley

It would be really helpful to see the full error output!

I'm curious about partition free space.

---

### Post by octopusfinley on 2008-11-22
I'm not even sure what these are supposed to do, I'm more worried that they're not installing. Is this something that I should even be caring about? It seems like it's something for printing but I don't own a printer (although I've noticed that I can't seem to hook up to other people's printers)
I've tried both force yes and the previous command, but neither seem to have worked.
Here's everything after my input (sorry, I'm not quite sure where the error output starts):


finley@squid:~$ sudo apt-get --force-yes upgrade hpjis hplip hplip-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  hpijs hplip hplip-data
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7522kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main hplip-data 2.7.7.dfsg.1-0ubuntu5.1 [6898kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main hplip 2.7.7.dfsg.1-0ubuntu5.1 [290kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main hpijs 2.7.7+2.7.7.dfsg.1-0ubuntu5.1 [334kB]
Fetched 7523kB in 1m18s (96.1kB/s)                                              
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)  Size mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)  Size mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
finley@squid:~$

---

