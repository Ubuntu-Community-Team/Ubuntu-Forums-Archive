---
title: "is it possible to install pure xubuntu from mint..."
date: 2008-06-08
forum: New to Ubuntu
---

### Post by windfer on 2008-06-08
or strip mint of its mintyness so that I have pure ubuntu.

---

### Post by Paqman on 2008-06-08
Yep, to remove all trace of Gnome and install XFCE instead, stick this into a terminal:
```

sudo apt-get remove alacarte bluez-gnome brltty brltty-x11 bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw deskbar-applet diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet firefox-3.0-gnome-support firefox-gnome-support gconf-editor gedit gedit-common gimp-gnomevfs gimp-python gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-settings-daemon gnome-spell gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gtkhtml3.14 gvfs gvfs-backends gvfs-fuse hwtest hwtest-gtk launchpad-integration libalut0 libao2 libarchive1 libart2.0-cil libcdio-cdda0 libcdio-paranoia0 libcompizconfig0 libcurl3 libdecoration0 libdeskbar-tracker libdirectfb-1.0-0 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.1.5-cil libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1 libglade2.0-cil libglew1.5 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpgme11 libgpod-common libgpod3 libgtk2.0-cil libgtkhtml3.14-19 libgtkhtml3.16-cil libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0 libgweather-common libgweather1 libicu38 liblpint-bonobo0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmtp7 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libopal-2.2 libopenal0a libopenobex1 libpam-gnome-keyring libpisock9 libpisync1 libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpth20 libpulsecore5 librarian0 libsamplerate0 libsdl1.2debian libsdl1.2debian-alsa libsgutils1 libsmbclient libsoup2.4-1 libsqlite0 libtracker-gtk0 libvorbisfile3 libwpg-0.1-1 libwps-0.1-1 libx11-xcb1 libxml2-utils mesa-utils metacity mono-common mono-gac mono-jit mono-runtime mousetweaks nautilus nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share o3read obex-data-server openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-style-human openoffice.org-writer pkg-config pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 python-gmenu python-gtksourceview2 python-uno rdesktop rhythmbox rss-glx scim-bridge-agent scim-bridge-client-gtk seahorse sound-juicer sqlite sqlite3 ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc xulrunner-1.9-gnome-support yelp && sudo apt-get install xubuntu-desktop

```

---

### Post by lazyart on 2008-06-08
If your /home is a separate partition you can install ubuntu and keep your stuff intact.  I actually went the other-- installed Mint on my once ubuntu laptop.

Is there something you dislike about Mint?

Anyhow, if you can backup your /home to other media, then wipe out your install, drop ubuntu in and copy your stuff back.

---

### Post by starcannon on 2008-06-08
When you installed Mint did you put /home on its own partition?

If so you can just install Ubuntu as normal, just don't format the /home partition.

If not... more difficult, I would say its still going to be easier than *un-minting* your current install though.

If you can, using either an external hdd, or popping a spare if you have one around hdd into your case, backup your /home directory:

```
cp -r /home /media/the_new_hdd
```

if this is not an option, then if there is enough empty space on your hdd you could run the [gparted livecd]("http://gparted.sourceforge.net/livecd.php") and make a new space for /home, then move your /home directory to it and go from there.

Either way its going to be tedious, go slow so you don't lose anything important (backing things up to another hard drive is the safest way).

Then do a clean install using but not formatting the /home you created with the gparted livecd, or flattening everything if you backed up /home to another hdd.

If I'm making this all sound upside down feel free to skype me *starcannon99022* I'd be happy to help you out that way as well.

---

### Post by windfer on 2008-06-08
> **lazyart said:**
> 
Is there something you dislike about Mint?


No I am actually quite satisfied with mint. But it runs too slow on my laptop and xubuntu is leaner so i figure it will run faster. I don't use any of the mint tools so all the benifits and extra stuff are pretty much wasted on me.

---

### Post by Paqman on 2008-06-08
Just to reiterate: you do not need to reinstall to go from Ubuntu to Xubuntu. The only difference is the desktop environment, which can just be (un)installed like any other set of packages.

---

### Post by starcannon on 2008-06-08
+1 to Paqman's post, but I think the OP was also wanting to go from Linux Mint to Xubuntu, I'd just backup /home unless its already on its own partition and install Xubuntu from scratch, but as always theres a number of ways to skin the cat, and if Paqmans post #2 is all you really want to do (switch to Xfce) then it is by far the easiest, and you should probably consider it first.

I will advise that at some point you may want to consider setting up a /home partition, it makes deciding to try out other flavors of linux, and other desktop managers, so much easier to do and to undo.

---

### Post by SunnyRabbiera on 2008-06-08
you vcan just put XFCE in as opposed to gnome, you dont need the xubuntu packages.

---

### Post by Paqman on 2008-06-08
> **starcannon said:**
> I think the OP was also wanting to go from Linux Mint to Xubuntu

Well, Mint is just Ubuntu with a new theme and some extra packages.
```

sudo apt-get remove mintassistant mintassistant-gnome mintassistant-kde mintdesktop mintinstall mintmenu mintupdate mintupdate-gnome mintupdate-kde mintupload mintwifi usplash-theme-mint 

```

Should take care of all the Mint-specific stuff.

---

### Post by SunnyRabbiera on 2008-06-08
> **Paqman said:**
> Well, Mint is just Ubuntu with a new theme and some extra packages.
```

sudo apt-get remove mintassistant mintassistant-gnome mintassistant-kde mintdesktop mintinstall mintmenu mintupdate mintupdate-gnome mintupdate-kde mintupload mintwifi usplash-theme-mint 

```

Should take care of all the Mint-specific stuff.

actually Mint has a lot of good tools in it, especially mintupdate that seems to do a better job then ubuntu's updater.

---

### Post by Paqman on 2008-06-09
> **SunnyRabbiera said:**
> actually Mint has a lot of good tools in it, especially mintupdate that seems to do a better job then ubuntu's updater.

Well, if he's got the Mint repo, he can always stick them back on if he misses them :)

---

