---
title: "Updating"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Mitchlb on 2008-10-23
Like to update from gutsy gibbon. Its all screwed up. I press update and the thing loads to the end and disappears.

---

### Post by tuxxy on 2008-10-23
It may save time if you did a fresh install of Hardy but make sure your /home is on a seperate partition to save your files/settings.

---

### Post by Mitchlb on 2008-10-23
I don't understand what your talking about.

---

### Post by Mitchlb on 2008-10-23
How can I install it without using synaptic?

[http://ubuntuforums.org/showthread.php?p=6022323#post6022323](http://ubuntuforums.org/showthread.php?p=6022323#post6022323)

---

### Post by tuxxy on 2008-10-23
> **Mitchlb said:**
> How can I install it without using synaptic?

[http://ubuntuforums.org/showthread.php?p=6022323#post6022323](http://ubuntuforums.org/showthread.php?p=6022323#post6022323)

Download the Ubuntu Hardy ISO and install it as normal, if you want to move your /home to a new partition first try this guide 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by zvacet on 2008-10-23
If you want to install Xubuntu desktop and you don´t want to use Gnome type in terminal

```
sudo apt-get remove alacarte bluez-gnome brltty brltty-x11 bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gedit gedit-common gimp-gnomevfs gimp-python gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gtkhtml3.14 gvfs gvfs-backends gvfs-fuse hwtest hwtest-gtk launchpad-integration libalut0 libao2 libarchive1 libart2.0-cil libcdio-cdda0 libcdio-paranoia0 libcompizconfig0 libcurl3 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libglade2.0-cil libglew1.5 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpgme11 libgpod-common libgpod3 libgtk2.0-cil libgtkhtml3.14-19 libgtkhtml3.16-cil libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0 libgweather-common libgweather1 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp7 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libopenal0a libopenobex1 libpam-gnome-keyring libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpth20 libpulsecore5 librarian0 libsamplerate0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libsmbclient libsoup2.4-1 libsqlite0 libtracker-gtk0 libvorbisfile3 libwpg-0.1-1 libwps-0.1-1 libx11-xcb1 libxml2-utils mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share o3read obex-data-server openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-gmenu python-gtksourceview2 python-uno rdesktop rhythmbox rss-glx scim-bridge-agent scim-bridge-client-gtk seahorse sound-juicer sqlite sqlite3 ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc xulrunner-1.9-gnome-support yelp && sudo apt-get install xubuntu-desktop
```

Of course this is valid only if your hardy work properly.If you still have problems with Hardy after upgrade boot in recovery mode and type

```
dpkg --configure -a
apt-get -f install
```

If that doesn´t halp and you want to have Xubuntu download it from [here.]("http://www.xubuntu.org/get")

---

### Post by Mitchlb on 2008-10-24
Tuxy, I downloaded the iso, but i can't run .exe files because i don't have wine installed, synaptic package manager is no longer under administrator.

---

### Post by Mitchlb on 2008-10-24
Its recognizing the cd and booting from it.... but it froze 3 times in a row.

---

### Post by Mitchlb on 2008-10-24
Give me some boot comands or something i can use to make it stop freezing.

---

