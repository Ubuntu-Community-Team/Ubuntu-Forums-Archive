---
title: "xfce4 weird"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-12-10
I added xubuntu desktop to my classic 11.10 and am getting very weird desktop effects. The panels seem to carry over but they are just pictures of the classic desktop panels so can't be deleted or tweaked at all is there a way to have both classic and xfce4 without affecting each other- they are on the same / partition I just added the xfce4 and xunbuntu desktops from synaptic

---

### Post by techvish81 on 2011-12-10
xubuntu desktop works flawlessly with unity and undercover gnome but with gnome shell and fallback it sometimes messes everything.
i dont know whether it will solve your problem or not but good to try..

remove xubuntu desktop and install/reinstall xfce4 only not xubuntu desktop.

and if you have removed unity and all the related stuff, reinstall it , you mave have removed some required components.

---

### Post by cmcanulty on 2011-12-10
That didn't work and now if I try to remove xfce it says broken dependencies but no pkgs show as broken.I logged out and in and now removed all the xfce and now I try to reinstall just the xfce4 desktop and it complains of missing dependencies. I just want to try xfce4 without screwing up ubuntu of xfce4

---

### Post by lolpenguin on 2011-12-10
Select the Xubuntu session from your Display Manager. I installed all of ubuntu-desktop, kubuntu-desktop, lubuntu-desktop, xubuntu-desktop on one machine and it works perfectly.

---

### Post by cmcanulty on 2011-12-11
Where is display manager?  I select it from login screen and get these problems

---

### Post by mike555 on 2011-12-11
Better to backup and do clean install of xubuntu ..... also turn off "treat recommends as depends" in package manager, that way it won't download so much unneeded stuff .....

---

### Post by cmcanulty on 2011-12-11
Hey thanks I never even noticed the preferences in synaptic until I started searching for turning off recommends. I don't want to do a clean install as I want to keep my classic as an option while I learn xfce

---

### Post by lolpenguin on 2011-12-12
> **cmcanulty said:**
> Where is display manager?  I select it from login screen and get these problems

Your display manager is the login screen. If you want to just try it, then install Xubuntu directly onto a virtual machine.

---

