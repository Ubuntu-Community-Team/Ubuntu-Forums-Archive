---
title: "freeglut3"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by Penfold1971 on 2014-09-16
I'm running Folding@home version 7.4.4 on a machine with Ubuntu 14.4.1 installed. I downloaded fahviewer_7.4.4 along with the corresponding versions of fahclient and fahcontrol.

The folding is going fine but the viewer doesn't work. When I tried to install the viewer, after a successful download, I got this message :

> Unpacking fahviewer (7.4.4) over (7.3.6) …
dpkg: fahviewer: dependency problems, but configuring anyway as you requested:
fahviewer depends on freeglut3; however:
Package freeglut3 is not installed.

What is freeglut3?

How would I download it using a Terminal command?

---

### Post by Impavidus on 2014-09-16
glut=OpenGL Utility Toolkit. It's a library with higher level functions to use with the OpenGL graphics library. freeglut3 is an open source release of version 3. To install, use```
sudo apt-get install freeglut3
```

---

### Post by Penfold1971 on 2014-09-16
Thanks for that, but I've now changed my mind. I checked for updates, as I do regularly, and got the following :
> $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree 
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
fahviewer : Depends: freeglut3 but it is not installed
Recommends: fahcontrol (= 7.4.4) but 7.4.4-1 is installed
E: Unmet dependencies. Try using -f.

At this point I would simply like to uninstall fahviewer. I mainly monitor both Folding@home and the Ubuntu installation remotely from my Intel iMac.

How do I uninstall fahviewer?

---

### Post by Impavidus on 2014-09-16
Ah, dpkg already installed fahviewer, which leads to a dependency problem as freeglut3 hasn't been installed yet. Now you can either uninstall fahviewer using```
sudo dpkg -r fahviewer
```or have apt-get fix the dependency problem (by installing freeglut3) using```
sudo apt-get -f install
```This is all normal behaviour for the package manager, nothing scary going on.

---

### Post by Penfold1971 on 2014-09-16
Ok, thanks once again. I removed fahviewer as per the command you posted.

I only downloaded fahviewer for completeness, but really quite unnecessarily. After upgrades like Ubuntu, from 12.04 to 14.04, and the Folding@home software, from 7.3.6 to 7.4.4, I remove the monitor, keyboard and mouse and let the machine run headless, monitoring remotely.

All is now well. Thanks again.

---

