---
title: "Partial Upgrade"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by poordamnedfool on 2008-11-18
Went to run the upgrade the other day and could only get a partial upgrade, I am running Ubuntu 64, I only have the basic package installed and swiftweasel/swiftdove, rainlendar2, mediabuntu, and build-essential.  Here is a copy of "sudo apt-get upgrade"

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bluez-cups bluez-utils evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins f-spot gdm
  gimp gimp-data gnome-control-center gnome-panel gnome-power-manager
  gnome-screensaver gnome-settings-daemon gstreamer0.10-plugins-good
  gtk2-engines-pixbuf gvfs gvfs-backends libebook1.2-9 libedata-book1.2-2
  libedataserverui1.2-8 libgimp2.0 libgnome-window-settings1 libgtk2.0-0
  libgtk2.0-bin libpisock9 libpt-1.10.10-plugins-v4l2 libtotem-plparser12
  libxi6 linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic network-manager-gnome obex-data-server
  rhythmbox seahorse-plugins totem totem-gstreamer totem-mozilla totem-plugins
  ubuntu-desktop xinput xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-intel
  xserver-xorg-video-openchrome
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.

```

---

### Post by phidia on 2008-11-18
Did you issue > sudo apt-get update before you did "upgrade"?
If not try that now.

---

### Post by handydan918 on 2008-11-18
If you are trying to go from 8.04 to 8.10, you might also want to try ```
sudo apt-get dist-upgrade
```

---

### Post by poordamnedfool on 2008-11-18
Thanks that worked, I thought because I have 8.10b that I didnt have to do the dist upgrade...

thanks again

---

