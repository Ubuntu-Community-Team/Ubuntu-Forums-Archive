---
title: "New evolution-data-server breaks gnome-shell and gnome-panel"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-12
There is a new version of evolution-data-server in Oneiric repos now.
But if you have gnome-shell or gnome-panel installed, you cannot upgrade evolution-data-server yet.

The reason is that gnome-shell and gnome-panel depend on libedataserverui-3.0-0,
but new libedataserverui-3.0-1 will uninstall it (through its dependency on evolution-data-server-common.

---

### Post by Quackers on 2011-07-12
Yes, those updates for evolution wouldn't run due to dependencies earlier.
Sounds like I should be grateful :-)
Thanks Harry33

---

### Post by Harry33 on 2011-07-12
> **Quackers said:**
> Yes, those updates for evolution wouldn't run due to dependencies earlier.
Sounds like I should be grateful :-)
Thanks Harry33

That is the way it is now.
You may, however, install from evolution-data-server group (3.1.3.1-0ubuntu1) these packages:
- libcamel-1.2-28 (leaving also libcamel-1.2-26 installed)
- libebook1.2-11
- libecal1.2-9
- libedataserver1.2-14

---

### Post by Quackers on 2011-07-12
Ok thanks. I'll have a mooch around :wink:

---

### Post by dino99 on 2011-07-12
the problem is that libedataserverui-3.0-1 cant be installed

---

### Post by dino99 on 2011-07-12
looking at ricotz/testing: gnome-shell is waiting to be built, so dependencies might be updated

---

### Post by Harry33 on 2011-07-12
> **dino99 said:**
> looking at ricotz/testing: gnome-shell is waiting to be built, so dependencies might be updated

Yes they might.
Still, gnome-panel (3.0.2-0ubuntu5) ought to be updated too.

---

### Post by Harry33 on 2011-07-12
The new gnome-shell build in Ricotz testing PPA dependencies:

```
Depends: gir1.2-atk-1.0 (>= 1.32), gir1.2-clutter-1.0 (>= 1.4), gir1.2-freedesktop (>= 0.10.6), gir1.2-gdkpixbuf-2.0, gir1.2-glib-2.0 (>= 0.9), gir1.2-gtk-3.0, gir1.2-json-1.0, gir1.2-mutter-3.0, gir1.2-pango-1.0, gir1.2-soup-2.4, gir1.2-telepathyglib-0.12, gir1.2-telepathylogger-0.2, gjs (>= 0.7.11), gnome-bluetooth (>= 3.0.0), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.6.0), libcanberra0 (>= 0.2), libclutter-1.0-0 (>= 1.6.0), libcroco3 (>= 0.6.2), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libecal1.2-9 (>= 3.1.3.1), libedataserver1.2-14 (>= 3.1.3.1), libedataserverui-3.0-1 (>= 3.1.3.1), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgirepository-1.0-1 (>= 0.9.2), libgjs0b (>= 0.7.11), libglib2.0-0 (>= 2.28.0), libgnome-desktop-3-2 (>= 2.91.5), libgnome-menu2 (>= 2.27.92), libgstreamer0.10-0 (>= 0.10.20), libgtk-3-0 (>= 3.0.0), libical0 (>= 0.30), libmozjs185-1.0 (>= 1.8.5~hg20110306r6), libmutter0 (>= 3.0.0), libpango1.0-0 (>= 1.14.0), libpolkit-agent-1-0 (>= 0.99), libpolkit-gobject-1-0 (>= 0.94), libpulse-mainloop-glib0, libpulse0 (>= 0.9.23), libstartup-notification0 (>= 0.11), libtelepathy-glib0 (>= 0.15.0), libtelepathy-logger2 (>= 0.2.0), libx11-6, libxfixes3 (>= 1:5.0), libxml2 (>= 2.7.4), dconf-gsettings-backend | gsettings-backend, gconf2 (>= 2.28.1-2), libdconf0 | gsettings-backend, gnome-settings-daemon (>= 2.91.5.1), gsettings-desktop-schemas (>= 0.1.7), gnome-icon-theme-symbolic (>= 2.91), gir1.2-gconf-2.0, gir1.2-gkbd-3.0, gir1.2-gnomebluetooth-1.0, gir1.2-networkmanager-1.0, gir1.2-polkit-1.0, gir1.2-upowerglib-1.0, python, pkg-config, mesa-utils
```

So there is libedataserverui-3.0-1 (>= 3.1.3.1)

Installing this version of gnome-shell will uninstall
gnome-panel (3.0.2-0ubuntu5) and gnome-session-fallback (3.1.3-0ubuntu2)
until gnome-panel has been rebuilt.

---

### Post by dino99 on 2011-07-13
yeah, still waiting for some packages upgrade

---

### Post by Quackers on 2011-07-13
Yep, I've got about 12 packages awaiting others at the moment.

---

### Post by Harry33 on 2011-07-13
I marked this thread as solved, because now I can install gnome-shell and gnome-panel that are build against the new evolution-data-server (3.1.3.1-0ubuntu2).
Of course gnome-shell must be installed from ricotz PPA, because Oneiric's build failed.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.2-1svn2build1](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.2-1svn2build1)

Gnome-panel from Oneiric repos is here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu6](https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu6)

---

### Post by paul_in_london on 2011-07-13
> **Harry33 said:**
> I marked this thread as solved, because now I can install gnome-shell and gnome-panel that are build against the new evolution-data-server (3.1.3.1-0ubuntu2).
Of course gnome-shell must be installed from ricotz PPA, because Oneiric's build failed.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.2-1svn2build1](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.2-1svn2build1)

Gnome-panel from Oneiric repos is here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu6](https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu6)

+1:

```
paul@oneiric:~$ sudo aptitude safe-upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  libedataserverui-3.0-1{a} 
The following packages will be REMOVED:
  libcamel-1.2-26{u} libedataserverui-3.0-0{u} 
The following packages will be upgraded:
  evolution-data-server-common gir1.2-panelapplet-4.0 gnome-panel 
  gnome-panel-data gnome-shell libpanel-applet-4-0 
The following packages are RECOMMENDED but will NOT be installed:
  alacarte evolution-data-server 
6 packages upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 1,864 kB of archives. After unpacking 1,421 kB will be freed.
Do you want to continue? [Y/n/?] Y
```

---

### Post by Quackers on 2011-07-13
Most of mine are waiting for libedataserverui or something - including gnome-shell. Gnome-panel got removed by one package just run :-(

Edit  aptitude safe-upgrade found the necessary packages when synaptic didn't

---

### Post by dino99 on 2011-07-13
same here because gnome-shell "Failed to build" status

---

### Post by Quackers on 2011-07-13
After safe-upgrade the first reboot loaded everything but at the end gdm used up 100% cpu (like it used to occasionally).
Second reboot loaded a desktop with no panel at all.
After a REISUB, third time lucky, everything loaded normally :-)
I did get a "Sorry, Metacity closed unexpectedly" message then a "Sorry, zeitgeist daemon had a problem" but everything is working.

---

### Post by dino99 on 2011-07-13
yeah wonder what zeitgeist really brings :( (much noise for nothing)

---

### Post by Quackers on 2011-07-13
It seems so. It's been a regular(ish) problem notice here :-)  along with Gnome Settings Daemon.

---

### Post by paul_in_london on 2011-07-13
> **Quackers said:**
> After safe-upgrade the first reboot loaded everything but at the end gdm used up 100% cpu (like it used to occasionally).
Second reboot loaded a desktop with no panel at all.
After a REISUB, third time lucky, everything loaded normally :-)
I did get a "Sorry, Metacity closed unexpectedly" message then a "Sorry, zeitgeist daemon had a problem" but everything is working.

@Quackers: fine here in a VM, with a single reboot, after those updates (although at the moment I still have to start **gnome-shell** manually, but that's a separate issue). This is with **lightdm** though.

Funnily enough a **lightdm** update on my **Arch** install caused a ridiculous increase in CPU load, so I switched back to **gdm** and the load went back to normal!

---

### Post by Quackers on 2011-07-13
I've shied away from lightdm after a couple of teething problems. Maybe I'll try it again :-)

---

### Post by paul_in_london on 2011-07-13
> **Quackers said:**
> I've shied away from lightdm after a couple of teething problems. Maybe I'll try it again :-)

It was updated yesterday in Oneiric actually and is working fine for me atm.

---

### Post by Harry33 on 2011-07-13
> **dino99 said:**
> same here because gnome-shell "Failed to build" status

The gnome-shell in ricotzs testing PPA is built against libedataserverui-3.0-1 and it works well.

---

