---
title: "Select and install software fails"
date: 2011-06-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by linuxman94 on 2011-06-20
I'm using the 64bit alternate iso and dd to make a bootable usb disk and for the past few daily builds, the installer always fails on 'Select and Install software'. Also, using the alpha on usb disk causes a boot fail.  Any idea what is going on?

---

### Post by coffeecat on 2011-06-21
I can confirm I was also getting a failure at the select and install software stage with recent alternate dailies, but this was when trying to install directly from a mounted ISO into a VirtualBox virtual machine.

---

### Post by paul_in_london on 2011-06-21
You could always do a minimal install from one of the daily boot-only **mini.iso** images and go from there. 64 bit ones here:

```
http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/
```

Last tried the 32 bit one the other day to check that the partioning bug was fixed (which it was). Presumably 64 bit is also ok now.

This was the bug:

```
https://bugs.launchpad.net/ubuntu/+source/parted/+bug/797054
```

---

### Post by linuxman94 on 2011-06-21
Ah good idea. Trying now..

---

### Post by floydsp on 2011-06-21
I tried the mini install and it hung at the ubuntu screen
and would never load
I tried the not free video drivers and borked my system

floydsp

---

### Post by linuxman94 on 2011-06-21
AH it works now.  FInally into testing. 

@floydsp

I think you posted in the wrong section.. This is the oneiric testing forum.

---

### Post by paul_in_london on 2011-06-21
These were the initial packages I added to a base install on another PC (this was a little while back when it was still Natty):

```
xorg xserver-xorg-core gdm gnome-session gnome-panel gnome-terminal \
gnome-themes gnome-themes-selected gnome-themes-ubuntu ubuntu-artwork \
light-themes nvidia-current synaptic flashplugin-nonfree app-install-data \
gnome-applets gnome-panel-bonobo  gvfs-backends indicator-applet-appmenu \
indicator-applet-complete indicator-application libasound2-plugins \
libgtk2-perl libpam-ck-connector notification-daemon notify-osd \
nvidia-settings pulseaudio python-gconf software-properties-gtk \
python-software-properties gnome-keyring indicator-appmenu indicator-me \
indicator-messages indicator-session indicator-sound notify-osd-icons \
pulseaudio-esound-compat pulseaudio-module-x11 appmenu-gtk \
indicator-applet-session libpam-gnome-keyring python-indicate firefox \
gedit htop evince
```

Then I gradually worked out what else I needed or had forgotten before I added gnome-shell etc! ;)

---

### Post by floydsp on 2011-06-21
> **linuxman94 said:**
> AH it works now.  FInally into testing. 

@floydsp

I think you posted in the wrong section.. This is the oneiric testing forum.

Thats what I am testing also oneiric, both flavors Ubuntu and Kubuntu:P

floydsp

---

