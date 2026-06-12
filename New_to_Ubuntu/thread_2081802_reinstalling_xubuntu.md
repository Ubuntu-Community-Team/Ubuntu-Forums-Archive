---
title: "reinstalling xubuntu"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-11-07
need some help. got some errors with xubuntu-too much playing around. when i tried this got this error

THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo apt-get reinstall xubuntu-desktop
[sudo] password for ray: 
E: Invalid operation reinstall
ray@ray-GC660AA-ABA-SR5123WM:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xubuntu-desktop : Depends: thunar but it is not going to be installed
                   Depends: thunar-volman but it is not going to be installed
                   Depends: xfce4-panel but it is not going to be installed
                   Depends: xfdesktop4 but it is not going to be installed
                   Recommends: orage but it is not going to be installed
                   Recommends: thunar-archive-plugin but it is not going to be installed
                   Recommends: thunar-media-tags-plugin but it is not going to be installed
                   Recommends: xfce4-cpugraph-plugin but it is not going to be installed
                   Recommends: xfce4-dict but it is not going to be installed
                   Recommends: xfce4-indicator-plugin but it is not going to be installed
                   Recommends: xfce4-mailwatch-plugin but it is not going to be installed
                   Recommends: xfce4-netload-plugin but it is not going to be installed
                   Recommends: xfce4-notes-plugin but it is not going to be installed
                   Recommends: xfce4-places-plugin but it is not going to be installed
                   Recommends: xfce4-quicklauncher-plugin but it is not going to be installed
                   Recommends: xfce4-systemload-plugin but it is not going to be installed
                   Recommends: xfce4-terminal but it is not going to be installed
                   Recommends: xfce4-verve-plugin but it is not going to be installed
                   Recommends: xfce4-weather-plugin but it is not going to be installed
                   Recommends: xfce4-xkb-plugin but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ray@ray-GC660AA-ABA-SR5123WM:~$ 

however when i opened the spm to correct it showed i had no broken packages.

looking for command to reinstall xubuntu. maybe force remove and then reinstall or whatever. not worried about data loss have xfce,classic,mate and cinnamon installed so i am covered.

---

### Post by newb85 on 2012-11-07
Sounds to me like you really only want to reinstall XFCE.

```
sudo apt-get purge xfce4
sudo apt-get autoremove
sudo apt-get install xfce
```

I doubt that will eliminate the problem of dependencies refusing to install, though.  That problem might be caused by sources you added in order to install Cinnamon and Mate.  Perhaps you could provide more information about that...

---

### Post by rburkartjo on 2012-11-08
note output

ray@ray-GC660AA-ABA-SR5123WM:~$ sudo apt-get install xfce4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xfce4 : Depends: xfce4-panel (>= 4.10.0) but it is not going to be installed
         Depends: xfdesktop4 (>= 4.10.0) but it is not going to be installed
         Depends: thunar (>= 1.4.0) but it is not going to be installed
         Depends: xfce4-mixer (>= 4.8.0) but it is not going to be installed
         Depends: orage (>= 4.8.0) but it is not going to be installed
         Recommends: thunar-volman (>= 0.8.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ray@ray-GC660AA-ABA-SR5123WM:~$

---

### Post by Peripheral Visionary on 2012-11-08
My goodness, what a bunch of confusion!

There is no such command in Linux as "reinstall."  Only "install."  I'm a graphical user, so for most of my installation / removal / reinstallation stuff I use Synaptic Package Manager.

The package you want to reinstall may be "xubuntu-desktop" rather than "Xfce."  Try using Synaptic to locate that metapackage, select Mark for Reinstallation, and go with that.

---

### Post by rburkartjo on 2012-11-08
per tks but if i open the spm it shows that i dont have the xubuntu-desktop installed and if i try to install it get the dependencies error. really weird since i have both a xfce and xubuntu session on the log in menu and both work. just weird

---

### Post by rburkartjo on 2012-11-08
and new mate and cin sources havent been the problem. just somehow mess up by installing xfce4.10 and .12 dev ppas which i have since purged

---

### Post by newb85 on 2012-11-08
> **Peripheral Visionary said:**
> My goodness, what a bunch of confusion!

There is no such command in Linux as "reinstall."  Only "install."  I'm a graphical user, so for most of my installation / removal / reinstallation stuff I use Synaptic Package Manager.

The package you want to reinstall may be "xubuntu-desktop" rather than "Xfce."  Try using Synaptic to locate that metapackage, select Mark for Reinstallation, and go with that.

xubuntu-desktop is a metapackage.  Its only purpose is as a dependency placeholder.  Uninstalling or reinstalling it won't do anything.

Have you tried directly installing the packages it says "won't be installed" to see if it kicks any helpful error messages?

---

### Post by rburkartjo on 2012-11-08
new it is like i am in a non-ending loop if i try to install any sub package i get an error of an unresolved dependency happens with about everything i try. must be an easy way to fix if not just will live with until 13.04 come out.

---

### Post by rburkartjo on 2012-11-08
there has to be a way of completely removing xfce and xubuntu including all preferences. then i could log back into a unity or classic session and install xfce and xubuntu.

---

### Post by mike555 on 2012-11-08
[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by rburkartjo on 2012-11-08
mike tks for the link. i thought i had that one bookmarked but couldnt fine.

---

