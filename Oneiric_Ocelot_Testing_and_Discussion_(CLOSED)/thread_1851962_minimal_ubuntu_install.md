---
title: "minimal ubuntu install"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by SpinningAround on 2011-09-29
How do you install ubuntu without gnome and all the applications? My thought is to install lxde and from there install those applications I need (libreoffice, chromium, thunderbird ... ). I would guess that I don't need lubuntu since it would have the same base system as any other ubuntu dist. I tried alternative cd but ended up with a regular install, something I missed?

[http://releases.ubuntu.com/oneiric/ubuntu-11.10-beta2-alternate-i386.iso](http://releases.ubuntu.com/oneiric/ubuntu-11.10-beta2-alternate-i386.iso)

---

### Post by lucazade on 2011-09-29
[http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/mini.iso)

this image is only 22mb and it will install only ubuntu-minimal and ubuntu-standard metapackages. 
(x/l/k)ubuntu-desktop metapackage instead will be not installed and you will get a minimal installation without any gui.
from there you can install xorg, the DE you like and all the apps you need.

note: this is the wiki page but it is not updated for oneiric yet:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by speedwlk on 2011-09-29
If you need a minimal installation, please try out the following:

At the start of the installation (while using the alternate cd), press the F4 key and choose "Install a Command-line System". Next start the installation.

See [https://help.ubuntu.com/community/Installation/LowMemorySystems#Install_an_Ubuntu_command-line_system](https://help.ubuntu.com/community/Installation/LowMemorySystems#Install_an_Ubuntu_command-line_system)
for more info.

---

### Post by Blasphemist on 2011-09-29
Not knowing what you goal is, I will make this known to you. Bodhi Linux is based on Ubuntu 10.04 but Bodhi 1.2 uses the 3.0.0 kernel and E17 for its desktop. It is very lightweight. It installs very few apps but then makes it very easy to install what you describe and much more. You can install individual apps or groups of apps. [http://bodhilinux.com/](http://bodhilinux.com/)

---

### Post by Frozen Forest on 2011-09-29
Tried the minimal install with the command-line but ended up with a blank/black screen, guess some xorg libraries is required, will install a regular beta 2 will work and instead uninstall things i don't want

---

### Post by paul_in_london on 2011-09-29
Try booting into recovery mode and then:

```
aptitude install --without-recommends xorg xserver-xorg-core \
xserver-input-all xserver-utils x11-xserver-utils \
xorg-input-all xserver-xorg-input-all lightdm lightdm-gtk-greeter \
gnome-session gnome-panel gnome-terminal gnome-themes \
gnome-themes-selected gnome-themes-ubuntu ubuntu-artwork \
light-themes gnome-session-fallback
```

```
aptitude install --without-recommends synaptic \
flashplugin-downloader app-install-data gnome-applets gnome-panel-bonobo \
gvfs-backends indicator-applet-appmenu indicator-applet-complete \
indicator-application libasound-plugins libgtk2-perl libpam-ck-connector \
notification-daemon notify-osd nvidia-settings pulseaudio python-gconf \
software-properties-gtk python-software-properties gnome-keyring \
indicator-appmenu indicator-me indicator-messages indicator-session \
indicator-sound notify-osd-icons pulseaudio-esound-compat \
pulseaudio-module-x11 appmenu-gtk indicator-applet-session \
libpam-gnome-keyring python-indicate
```

---

### Post by speedwlk on 2011-09-29
> **Frozen Forest said:**
> Tried the minimal install with the command-line but ended up with a blank/black screen, guess some xorg libraries is required, will install a regular beta 2 will work and instead uninstall things i don't want

I also had the blank/black screen. I shifted to tty1 with Ctrl+Alt+F1 and then logged on to install xorg and other required packages.

---

### Post by lucazade on 2011-09-29
> **speedwlk said:**
> I also had the blank/black screen. I shifted to tty1 with Ctrl+Alt+F1 and then logged on to install xorg and other required packages.

yep, it is due to 'vt.handoff=7' as grub params.

---

### Post by speedwlk on 2011-09-29
> **lucazade said:**
> yep, it is due to 'vt.handoff=7' as grub params.

Thanks lucazade.
I did not know about this.

---

### Post by speedwlk on 2011-09-29
Found two related posts:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

and here:

[http://ubuntuforums.org/showthread.php?t=1768725](http://ubuntuforums.org/showthread.php?t=1768725)

---

