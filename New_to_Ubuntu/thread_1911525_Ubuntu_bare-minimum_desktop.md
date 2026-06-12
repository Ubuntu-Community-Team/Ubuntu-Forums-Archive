---
title: "Ubuntu bare-minimum desktop"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by chindichor on 2012-01-19
I need to build a dev VM of Ubuntu that takes as less resource as possible (disk space, memory). I have downloaded latest Ubuntu 11.10, I found that it's bloated with software, utilities and language-packs that we will never use.

I just wanted plain Ubuntu with GUI without software like Gimp, Office, and the likes. The idea is to keep image as slim as possible. Can someone suggest an option other than installing regular Ubuntu and then uninstalling software and language packs?

thanks in advance

---

### Post by mcduck on 2012-01-19
Download the [Minimal Install CD]("https://help.ubuntu.com/community/Installation/MinimalCD"), and then add the desktop environment, programs, tools and services you actually want.

My Openbox setup installed this way uses less than 40MB of RAM on desktop (even with some eyecandy like transparency and drop shadows) Can't say much about disc space since I've already installed programs and stuff, but it's of course equally minimal to the memory usage...

(of course dong it this ways requires you to be at least fairly comfortable with command line, and of course also to know what programs and things you need on your computer...)

---

### Post by paul_in_london on 2012-01-21
Download the **mini.iso** from here (or the corresponding 386 directory):

[http://archive.ubuntu.com/ubuntu/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/)

and install in a VM using that.

Once you've got your bare-bones system installed, build it up from there with something like:

```
sudo aptitude install --without-recommends xorg xserver-xorg-core \
xserver-input-all xserver-utils x11-xserver-utils \
xorg-input-all xserver-xorg-input-all lightdm lightdm-gtk-greeter \
gnome-session gnome-panel gnome-terminal gnome-themes \
gnome-themes-selected gnome-themes-ubuntu ubuntu-artwork \
light-themes
```

```
sudo aptitude install --without-recommends synaptic \
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

### Post by Paqman on 2012-01-21
Paul-in-London's suggestions look pretty good, but if you want to pick and choose you packages try the script in my sig. Pick one of the lightweight desktop environment packages and install just the apps you want.

---

### Post by snowpine on 2012-01-21
To play devil's advocate :) there is no actual tangible benefit to removing language packs etc. unless you are running low on hard drive space.

Nevertheless minimal installs are a lot of fun (and perfect for your VM project), so here's a good how-to with screenshots: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by sean abbott on 2012-05-18
mcduck...can you give a quick list of packages you installed?

---

### Post by 29732 on 2012-05-18
> **paul_in_london said:**
> Download the **mini.iso** from here (or the corresponding 386 directory):

[http://archive.ubuntu.com/ubuntu/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/oneiric/main/installer-amd64/current/images/netboot/)

and install in a VM using that.

Once you've got your bare-bones system installed, build it up from there with something like:

```
sudo aptitude install --without-recommends xorg xserver-xorg-core \
xserver-input-all xserver-utils x11-xserver-utils \
xorg-input-all xserver-xorg-input-all lightdm lightdm-gtk-greeter \
gnome-session gnome-panel gnome-terminal gnome-themes \
gnome-themes-selected gnome-themes-ubuntu ubuntu-artwork \
light-themes
```

```
sudo aptitude install --without-recommends synaptic \
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
Didn't aptitude get replaced with apt-get?

---

### Post by Cheesemill on 2012-05-18
> **29732 said:**
> Didn't aptitude get replaced with apt-get?

Not replaced, you used to get apt-get and aptitude but you no longer get aptitude by default on a desktop installation.

You do have it installed on a server installation though, I'm not sure about the Mini CD.

It's always the first package I install on a new system though.

---

