---
title: "The following packages have unmet dependencies? (krita)"
date: 2015-10-03
forum: New to Ubuntu
---

### Post by sofia7 on 2015-10-03
Hey everyone! Earlier today I installed KDE on my HP Chromebook using Crouton. 
I spend most of my day drawing on the computer, and I have a desktop running Windows 8 on which I use Paint Tool SAI, but I am interested in running a painting program from my laptop. I found out about Krita today and was very excited. It seems to be a great program! In fact, I chose KDE just to have access to Krita, ajajaja ...
I followed these instructions: [https://krita.org/download/krita-desktop/](https://krita.org/download/krita-desktop/)
This is copied straight from the terminal:
```
sudo apt-get install krita
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. 
The following information may help resolve the situation:

The following packages have unmet dependencies:
krita : Depends : krita-data (>=1:24.0.0Ubuntu2.1) but it is not going to be installed. 
E: Unable to correct problems, you have held broken packages
```
I've got absolutely nothing installed apart from the Synaptic package manager, the KDE desktop, and something called ubuntu-desktop which I needed to get access to most of the basic Ubuntu apps. [http://www.everydaylinuxuser.com/2015/02/how-to-install-ubuntu-on-hp-chromebook.html](http://www.everydaylinuxuser.com/2015/02/how-to-install-ubuntu-on-hp-chromebook.html) <- I used this guide, if you're curious, but I installed KDE and not Unity. I don't know if that was a big mistake, this is my first time doing any of this. 

I've tried apt-get clean, apt-get auto clean, apt-get update, apt-get upgrade, apt-get install -f .... all the basic fixes, and the error message will not change.
I've also tried the following: apt-get install krita-data, then apt-get install update, then apt-get install krita, but the terminal still tells me I have an unmet dependency! And Synaptic manager tells me krita-data was installed correctly. I really just have no idea what's going on, heh.

---

### Post by dino99 on 2015-10-04
Generally speaking, avoid mixing several flavours of the same distro (in your case, ubuntu+kubuntu) as they can use different releases where libs/dependencies can conflict (which is the case here)

---

### Post by grahammechanical on 2015-10-04
I use Ubuntu+Unity. I do not have any other desktop user interface installed. The Ubuntu Software Centre will install krita for me. I have not installed it but I am confident that Software Centre will install all the dependencies needed. In fact Software Centre will also install Calligra the suite of applications the krita is part of. Perhaps if Caligra was installed first then the dependency problem would go away. I do not think that I need to install KDE Desktop Environment to install and use a KDE application. 

Regards.

---

### Post by ian-weisser on 2015-10-04
> **sofia7 said:**
> I followed these instructions: [https://krita.org/download/krita-desktop/](https://krita.org/download/krita-desktop/)
[...]
krita : Depends : krita-data (>=**1:24.0.0Ubuntu2.1**) but it is not going to be installed. 

Looks a lot like a version conflict...or perhaps a typo. The current version of krita-data in Ubuntu is 1:2.9.7 in 15.10.

Did you add the PPAs listed in those instructions?
If you did add those PPAs, delete them and install krita from the plain old Ubuntu repositories. The Ubuntu packages are built to prevent version conflicts. The PPA packages are not.

What release of Ubuntu are you running?

---

### Post by mc4man on 2015-10-04
Maybe it's related to crouton, maybe something else.
Please post - 
```
apt-cache policy krita krita-data krita-2.9
```
Also your main sources.list 
```
cat /etc/apt/sources.list
```

---

