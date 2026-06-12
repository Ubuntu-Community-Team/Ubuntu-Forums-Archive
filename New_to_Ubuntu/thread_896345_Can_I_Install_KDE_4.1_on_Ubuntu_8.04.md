---
title: "Can I Install KDE 4.1 on Ubuntu 8.04?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Harmony_Of_Distortion on 2008-08-21
Hello! I have installed ubuntu 8.04 on my laptop and I want to know if I can convert the ubuntu to kubuntu by istalling the KDE 4.1 on my ubuntu version.

---

### Post by DemonBob on 2008-08-21
Yup, sudo apt-get install kubuntu-desktop

Or search for it through synaptic package manager.

---

### Post by anewguy on 2008-08-21
This is true, but you will need to at least once at login select options and change session to KDE.  If you don't answer yes to the prompt about making it the default you will go back to Gnome when you log in next.  I use both myself.

---

### Post by Harmony_Of_Distortion on 2008-08-21
> **DemonBob said:**
> Yup, sudo apt-get install kubuntu-desktop

Or search for it through synaptic package manager.

THAAAAAAAAAAAAANKS MEN I'l try it!:lolflag::guitar:

---

### Post by draclear on 2008-08-21
You need to edit the /etc/apt/sources.list file
[INDENT]sudo gedit /etc/apt/sources.list[/INDENT]
For Kubuntu Users use the following command
[INDENT]sudo kate /etc/apt/sources.list[/INDENT]
add the following line
*deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main*
save and exit the file
Update the source list using the following command
[INDENT]sudo apt-get update[/INDENT]
For Ubuntu 8.04 users use the following command to install
[INDENT]sudo apt-get install kubuntu-kde4-desktop[/INDENT]
For Kubuntu 8.04 users use the following command to install
[INDENT]sudo apt-get dist-upgrade[/INDENT]
Note you may need to install kdebase-runtime-data-common in order to get Application directory icons under the Kickoff menu.

---

