---
title: "XUbuntu software center"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by piscvau on 2015-01-30
Hello,
I am new to xubuntu (14.04 LTS version). I have problems with the software center. I installed 2 software outside of the software center, the first one is the Oracle virtual Box and the second one is XnView MP.
My problem is that when I go to the software center I do not see these softwares, neither in the installed software neither when I click on all softwares. 
As a consequence I cannot uninstall these softwares. I suspect I have to do this through command line but I would like to know if there is another solution through the user interface of the software center.
Could someone please help me?
I thank you in advance.
Piscvau

---

### Post by newb85 on 2015-01-30
How did you go about installing them, if not from the software center?

---

### Post by Impavidus on 2015-01-30
The software centre is one of the tools to the package manager. It only knows about packages installed from .deb files. If you installed your software differently, there is no standard procedure to uninstall.

---

### Post by slickymaster on 2015-01-30
Hi piscvau, welcome to the forums.
> **Impavidus said:**
> The software centre is one of the tools to the package manager. It only knows about packages installed from .deb files. If you installed your software differently, there is no standard procedure to uninstall.
This ^^^

You can confirm if it's installed, or not, running at a terminal window the following command```
apt-cache policy virtualbox
```If you want to remove it from your system, in a terminal window run:```
sudo apt-get purge virtualbox
```

---

### Post by ajgreeny on 2015-01-30
I would also suggest that you install **synaptic** which is a great deal more flexible and useful than the software-center for package management.

For the best way to install VBox you should have added the VBox repository and security key, info at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)  (scroll down to Debian-based Linux distributions) and you will get the chance to update VBox as new versions appear, and VBox will also appear in synaptic (not sure if it also appears in software-center as I never use it)

---

### Post by piscvau on 2015-01-30
Well tahnk you every one. It is clear now.

---

