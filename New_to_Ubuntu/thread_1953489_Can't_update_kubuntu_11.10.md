---
title: "Can't update kubuntu 11.10"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by Norman Thom on 2012-04-06
I am trying out Kubuntu 11.10 for the first time
It appears to boot OK and I get a notice saying there are 384 updates to install
When I try to install them I get an error message saying that some other program is using the package manager and that I should close all other programs down before I can update - no other programs are open

I then tried to install Firefox and an error message told me that the package may be broken.

Are there any steps I can take to resolve this

---

### Post by NikTh on 2012-04-06
hi Norman , 
Open a terminal and try these commands 
```
sudo apt-get -f install 
sudo apt-get update
sudo apt-get dist-upgrade
``` 
Copy them from here and run them one at time. 
Thanks.

---

### Post by Norman Thom on 2012-04-06
Efxaristo NikTH

Your suggestion worked but unfortunately now I have another problem
when I restarted my system it would not load the KDE destop or at least that icon would not show

I guess I should just try to reinstall

Norm

---

### Post by NikTh on 2012-04-07
> **Norman Thom said:**
> Efxaristo NikTH

Your suggestion worked but unfortunately now I have another problem
when I restarted my system it would not load the KDE destop or at least that icon would not show

I guess I should just try to reinstall

Norm

Parakalo Norman. 
Try to reinstall KDE desktop if you want or maybe kdm (display manager for kde) or try to reconfigure kdm(if you still have it). 

To reinstall KDE ```
sudo apt-get install --reinstall kubuntu-desktop
```for kdm ```
sudo apt-get install --reinstall kdm
```for reconfiguration ```
sudo dpkg-reconfigure kdm
```maybe its also helpful to reconfigure all packages. This will take some time 
```
sudo dpkg --configure -a
```

---

