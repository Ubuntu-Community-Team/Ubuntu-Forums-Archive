---
title: "Is there a GNOME desktop Lite version of Ubuntu?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by orwellus on 2008-09-16
Okay, this might be a goofy question, but stick with me.

I was wondering if there is basically a skeleton version of Ubuntu.

What I mean by this, a version of Ubuntu that has the GNOME desktop (which I like) and has all the basic hardware stuff installed (sound, internet ready, synaptic package manager, printer set up). But, it does NOT have any applications installed. So no open office, no GIMP, no games, no firefox, etc. 

I hope that makes sense.

I have tried to install the barebones Ubuntu, but unfortuately I couldn't get that to work. Plus no GNOME desktop and no basic hardware stuff installed. 

So any help would be appreciated.

---

### Post by linux6994 on 2008-09-16
Best bet would be to load the server version [http://astromirror.uchicago.edu/ubuntu-releases/](http://astromirror.uchicago.edu/ubuntu-releases/) which is barebones, then load ubuntu-desktop via sudo apt-get.

---

### Post by scragar on 2008-09-16
no, that won't work, ubuntu-desktop is the meta package for the whole ubuntu system, that would be the same as installing the full ubuntu release from the start.

---

### Post by Elfy on 2008-09-16
Not too sure what you mean by barebones or where you got it, so if it was this ... you could use the minimal cd - then download what you want to use.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Alternatively remove the things you don't need from a standard install.

---

### Post by Vivaldi Gloria on 2008-09-16
About different versions of cli ubuntu see CLI in my sig. Once you install a base cli system you can install a light DE on it like openbox. If you really want a light gnome desktop then you should selectively install the packages you want from the dependencies of ubuntu-desktop. To begin with install

xorg
gdm
nautilus
gnome-core
gnome-system-tools
gnome-app-install

and their dependencies. Not sure what else you need. Here is the list of all dependencies of ununtu-desktop:

```
~$ apt-cache showpkg ubuntu-desktop
...
Dependencies: 
1.102 - acpi (0 (null)) acpi-support (0 (null)) acpid (0 (null)) alacarte (0 (null)) alsa-base (0 (null)) alsa-utils (0 (null)) anacron (0 (null)) apmd (0 (null)) avahi-daemon (0 (null)) bc (0 (null)) ca-certificates (0 (null)) consolekit (0 (null)) cupsys (0 (null)) cupsys-bsd (0 (null)) cupsys-client (0 (null)) cupsys-driver-gutenprint (0 (null)) dc (0 (null)) dcraw (0 (null)) desktop-file-utils (0 (null)) doc-base (0 (null)) eog (0 (null)) evince (0 (null)) fast-user-switch-applet (0 (null)) file-roller (0 (null)) foomatic-db (0 (null)) foomatic-db-engine (0 (null)) foomatic-filters (0 (null)) gcalctool (0 (null)) gconf-editor (0 (null)) gdebi (0 (null)) gdm (0 (null)) gedit (0 (null)) genisoimage (0 (null)) ghostscript-x (0 (null)) gimp-python (0 (null)) gnome-about (0 (null)) gnome-app-install (0 (null)) gnome-applets (0 (null)) gnome-control-center (0 (null)) gnome-icon-theme (0 (null)) gnome-media (0 (null)) gnome-menus (0 (null)) gnome-netstatus-applet (0 (null)) gnome-nettool (0 (null)) gnome-panel (0 (null)) gnome-pilot-conduits (0 (null)) gnome-power-manager (0 (null)) gnome-session (0 (null)) gnome-spell (0 (null)) gnome-system-monitor (0 (null)) gnome-system-tools (0 (null)) gnome-terminal (0 (null)) gnome-themes (0 (null)) gnome-utils (0 (null)) gnome-volume-manager (0 (null)) gstreamer0.10-alsa (0 (null)) gstreamer0.10-plugins-base-apps (0 (null)) gstreamer0.10-pulseaudio (0 (null)) gtk2-engines (0 (null)) gtk2-engines-pixbuf (0 (null)) gucharmap (0 (null)) hal (0 (null)) hotkey-setup (0 (null)) hwtest-gtk (0 (null)) language-selector (0 (null)) launchpad-integration (0 (null)) lftp (0 (null)) libgl1-mesa-glx (0 (null)) libglut3 (0 (null)) libgnome2-perl (0 (null)) libgnomevfs2-bin (0 (null)) libgnomevfs2-extra (0 (null)) libpt-1.10.10-plugins-v4l (0 (null)) libpt-1.10.10-plugins-v4l2 (0 (null)) libsasl2-modules (0 (null)) libxp6 (0 (null)) metacity (0 (null)) nautilus (0 (null)) nautilus-cd-burner (0 (null)) nautilus-sendto (0 (null)) notification-daemon (0 (null)) openprinting-ppds (0 (null)) pnm2ppa (0 (null)) powermanagement-interface (0 (null)) pulseaudio (0 (null)) pulseaudio-esound-compat (0 (null)) readahead (0 (null)) rss-glx (0 (null)) screen (0 (null)) screensaver-default-images (0 (null)) scrollkeeper (0 (null)) seahorse (0 (null)) smbclient (0 (null)) software-properties-gtk (0 (null)) ssh-askpass-gnome (0 (null)) synaptic (0 (null)) system-config-printer-gnome (0 (null)) tangerine-icon-theme (0 (null)) tsclient (0 (null)) ttf-bitstream-vera (0 (null)) ttf-dejavu-core (0 (null)) ttf-freefont (0 (null)) ubuntu-artwork (0 (null)) ubuntu-sounds (0 (null)) unzip (0 (null)) update-manager (0 (null)) update-notifier (0 (null)) usplash (0 (null)) usplash-theme-ubuntu (0 (null)) x-ttcidfont-conf (0 (null)) xdg-user-dirs (0 (null)) xdg-user-dirs-gtk (0 (null)) xkb-data (0 (null)) xorg (0 (null)) xscreensaver-data (0 (null)) xscreensaver-gl (0 (null)) xterm (0 (null)) yelp (0 (null)) zenity (0 (null)) zip (0 (null)) app-install-data-commercial (0 (null)) apport-gtk (0 (null)) avahi-autoipd (0 (null)) bluez-cups (0 (null)) bluez-gnome (0 (null)) bluez-utils (0 (null)) bogofilter (0 (null)) brasero (0 (null)) brltty (0 (null)) brltty-x11 (0 (null)) bug-buddy (0 (null)) cdparanoia (0 (null)) compiz (0 (null)) contact-lookup-applet (0 (null)) cups-pdf (0 (null)) deskbar-applet (0 (null)) displayconfig-gtk (0 (null)) diveintopython (0 (null)) dvd+rw-tools (0 (null)) ekiga (0 (null)) espeak (0 (null)) evolution (0 (null)) evolution-exchange (0 (null)) evolution-plugins (0 (null)) evolution-webcal (0 (null)) example-content (0 (null)) f-spot (0 (null)) firefox (0 (null)) firefox-gnome-support (0 (null)) foo2zjs (0 (null)) foomatic-db-hpijs (0 (null)) fortune-mod (0 (null)) gcc (0 (null)) gimp (0 (null)) gimp-gnomevfs (0 (null)) gnome-accessibility-themes (0 (null)) gnome-games (0 (null)) gnome-mag (0 (null)) gnome-orca (0 (null)) gnome-screensaver (0 (null)) gnome-user-guide (0 (null)) gvfs-fuse (0 (null)) hal-cups-utils (0 (null)) hplip (0 (null)) im-switch (0 (null)) jockey-gtk (0 (null)) landscape-client (0 (null)) laptop-detect (0 (null)) libdeskbar-tracker (0 (null)) libgl1-mesa-dri (0 (null)) libnss-mdns (0 (null)) libpam-gnome-keyring (0 (null)) linux-headers-generic (0 (null)) make (0 (null)) min12xxw (0 (null)) mousetweaks (0 (null)) nautilus-share (0 (null)) network-manager-gnome (0 (null)) onboard (0 (null)) openoffice.org-calc (0 (null)) openoffice.org-gnome (0 (null)) openoffice.org-impress (0 (null)) openoffice.org-writer (0 (null)) pidgin (0 (null)) pidgin-otr (0 (null)) powernowd (0 (null)) pulseaudio-module-gconf (0 (null)) pulseaudio-module-hal (0 (null)) pulseaudio-module-x11 (0 (null)) pxljr (0 (null)) rhythmbox (0 (null)) scim (0 (null)) scim-bridge-agent (0 (null)) scim-bridge-client-gtk (0 (null)) scim-gtk2-immodule (0 (null)) sound-juicer (0 (null)) splix (0 (null)) tomboy (0 (null)) totem (0 (null)) totem-mozilla (0 (null)) tracker (0 (null)) tracker-search-tool (0 (null)) transmission-gtk (0 (null)) ttf-arabeyes (0 (null)) ttf-arphic-uming (0 (null)) ttf-indic-fonts-core (0 (null)) ttf-kochi-gothic (0 (null)) ttf-kochi-mincho (0 (null)) ttf-lao (0 (null)) ttf-malayalam-fonts (0 (null)) ttf-thai-tlwg (0 (null)) ttf-unfonts-core (0 (null)) ubufox (0 (null)) ubuntu-docs (0 (null)) vinagre (0 (null)) vino (0 (null)) wodim (0 (null)) wvdial (0 (null)) xcursor-themes (0 (null)) xdg-utils (0 (null)) xsane (0 (null)) 

```

---

### Post by Elfy on 2008-09-16
> About different versions of cli ubuntu see CLI in my sig.That's a nice page to bookmark, so I did :)

---

### Post by Vivaldi Gloria on 2008-09-16
> **forestpixie said:**
> That's a nice page to bookmark, so I did :)

Ha ha. Thanks. Cheers.

---

