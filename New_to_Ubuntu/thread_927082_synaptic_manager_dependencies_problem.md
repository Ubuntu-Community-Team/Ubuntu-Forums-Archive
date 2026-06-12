---
title: "synaptic manager dependencies problem"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by ibit-matt on 2008-09-22
Hi there I am trying to install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr but get dependencies error

awn-core-applets-bzr:
 Depends: libawn0-bzr but it is not going to be installed
 Depends: libgnome-desktop-2-7 (>=1:2.23.90) but it is not installable
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu4 is to be installed
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1 is to be installed
  Depends: libpopt0 (>=1.14) but 1.10-3build1 is to be installed
  Depends: libvte9 (>=1:0.17.1) but 1:0.16.13-1ubuntu1 is to be installed
 Depends: libxcb-render-util0  but it is not installable
  Depends: libxi6 (>=2:1.1.3-1ubuntu1) but 2:1.1.3-1 is to be installed


Can someone help me please

---

### Post by Yannick Le Saint kyncani on 2008-09-22
> **ibit-matt said:**
> Hi there I am trying to install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr but get dependencies error

You could install avant-window-navigator instead of the -bzr version, it should install fine (hardy here).

---

### Post by BryanMarley on 2008-09-22
the last time i installed avant my whole Desktop manager was f'ed up hahahah.
Never gonna try that again.

---

### Post by rustutzman on 2008-09-22
Start adding the requested libs through synaptic. Just search for them. Synaptic should have id'd the dependencies.

Russ

edit: the bzr version has more active developement

---

### Post by ibit-matt on 2008-09-22
I have installed it now but I dont have any of the core applets to add to the bar.

Also how do I get the bar to start on boot I went to System > Preferences > Sessions clicked Add and added the following

Name: AWN
Command avant-window-navigator


And it does not work?

---

### Post by rustutzman on 2008-09-22
To auto start it go to "System"/"Preferences"/"Sessions" and add it there. 

The lack of applets and such is why I switched to the bzr version. Much better supported. I uninstalled the regular version and installed the bzr version and haven't had a problem.

Check out:[http://wiki.awn-project.org/Awn_Extras:Installation](http://wiki.awn-project.org/Awn_Extras:Installation)
Scroll down to the section Reacocard's PPA. HTH

Russ

---

