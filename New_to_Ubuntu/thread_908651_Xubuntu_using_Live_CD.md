---
title: "Xubuntu using Live CD?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by 3DGE on 2008-09-02
Is it possible to install Xubuntu from the Ubuntu Live CD I made without having to install Ubuntu?

Also will Xubuntu be able to run all the applications that Ubuntu could, I deleted Ubuntu from my partitioned drive because I found it to be too slow and "laggy". So I am hoping Xubuntu will be faster

My Specs Are
Intel Celeron(R) CPU
1.70GHz, 512MB of RAM

Thanks In Advanced

---

### Post by ayenack on 2008-09-02
Not that I know of.

Xubuntu should run all the programs that Ubuntu will run. What might happen is that when you install certain programs Xubuntu may install Gnome or other dependencies such as KDE dependencies which may in turn slow the system down a little but I don't think it'll be noticeable.

I'd say download [Xubuntu LiveCD]("http://www.xubuntu.org/") and see how it runs in the live mode then decide.

I'm surprised that it's laggy on your setup should run fine I would have thought.

---

### Post by Paqman on 2008-09-02
> **3DGE said:**
> Is it possible to install Xubuntu from the Ubuntu Live CD I made without having to install Ubuntu?


No, but turning Ubuntu into Xubuntu is as easy as running two commands:
```

sudo apt-get install xubuntu-desktop

```
Log out > Session > XFCE > set as default
Then run:

```

sudo apt-get remove alacarte bluez-gnome brltty brltty-x11 bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gedit gedit-common gimp-gnomevfs gimp-python gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gtkhtml3.14 gvfs gvfs-backends gvfs-fuse hwtest hwtest-gtk launchpad-integration libalut0 libao2 libarchive1 libart2.0-cil libcdio-cdda0 libcdio-paranoia0 libcompizconfig0 libcurl3 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libglade2.0-cil libglew1.5 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpgme11 libgpod-common libgpod3 libgtk2.0-cil libgtkhtml3.14-19 libgtkhtml3.16-cil libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0 libgweather-common libgweather1 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp7 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libopenal0a libopenobex1 libpam-gnome-keyring libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpth20 libpulsecore5 librarian0 libsamplerate0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libsmbclient libsoup2.4-1 libsqlite0 libtracker-gtk0 libvorbisfile3 libwpg-0.1-1 libwps-0.1-1 libx11-xcb1 libxml2-utils mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share o3read obex-data-server openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-gmenu python-gtksourceview2 python-uno rdesktop rhythmbox rss-glx scim-bridge-agent scim-bridge-client-gtk seahorse sound-juicer sqlite sqlite3 ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc xulrunner-1.9-gnome-support yelp 

```

---

### Post by brentoboy on 2008-09-02
If you just want to avoid downloading the entire cd, try getting the mini cd [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

it is only like 9 mb.
when you install it, choose the cli option (this will only install a command line system.  After installing, issue this command:

sudo apt-get install xubuntu-desktop

that will get all the stuff installed by the xubuntu cd.

in the end though it will have to download all the packages it installs, so it might take a while.
----
the alternative is not as clean, but might be preferable.  open up synaptic, and add xubuntu-desktop.   reboot into xubuntu/xfce.  then, open up synaptic again, and remove all the stuff in the gnome section.  it wont be a "clean" xubuntu, but it will be a decent alternative to fresh installation.

----
or, use bittorrent to download the xubuntu iso.

--
so many options, so little bandwidth.

---

### Post by 3DGE on 2008-09-02
Well it only becomes laggy when I multi-talk because I am usually installing the updates and I am doing work on the other window but after I installed all the updates it started to become slow and laggy. So my question now is do I have to install the updates for Ubuntu?

---

### Post by oilchangeguy on 2008-09-02
> **3DGE said:**
> Well it only becomes laggy when I multi-talk because I am usually installing the updates and I am doing work on the other window but after I installed all the updates it started to become slow and laggy. So my question now is do I have to install the updates for Ubuntu?

no, but you leave yourself open to security issues, and outdated software. 
also you don't say what version of ubuntu you're using. but you'd do yourself and your computer a favor if you'd install more ram.

---

### Post by kansasnoob on 2008-09-02
Look at this section:

> Playing Around
Enable Desktop Effects
KDE/Gnome Comparison
Install Gnome
Install KDE
Install XFCE
Install IceWM
Install XPDE
Pure Gnome
Pure KDE
Pure XFCE
A faster KDE
Replacing Nautilus 

of this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

It's best to use "aptitude" to change desktop environments rather than "apt-get".

---

### Post by Glw8z on 2008-09-03
I've installed Xubuntu on a machine w/ identical specs as yours, and it runs like charm. If you don't need all the bulk of Ubuntu or wish to pick and choose what to install, why not slim down a bit?

---

