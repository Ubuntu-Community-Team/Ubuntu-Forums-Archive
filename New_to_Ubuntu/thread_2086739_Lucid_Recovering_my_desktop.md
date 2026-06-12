---
title: "Lucid: Recovering my desktop"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by Nebelhom on 2012-11-21
I did something rather silly...

All I wanted to do was install python2.7 (which I did successfully) and remove the default python2.6 from my lucid installation. When I tried to remove Python2.6 using synaptic package manager, it suddenly started to remove everything. gnome-applet, my dropbox installation (at least that's what it said; even friggin aisleriot). In my panic, I made a force quit of synaptic (yes, I know, not too clever, but I'm stuck with that decision now :( ) On reboot, I wasn't even able to boot into the GUI and I have no idea what has been removed and what hasn't.

I honestly must have stopped thinking for a minute when I did this sequence, but I can't change it now.

Is there an operationally simple way to recover this from one of the command line terminals?

Any help is really appreciated. Thanks a lot.

---

### Post by bryncoles on 2012-11-21
Now, I might be wrong here, but can you try typing 

```
sudo apt-get install xubuntu-desktop
```

That should pull everything back in for you.  Give it a try anyway, and post any output you get!

(also, if you have a live CD maybe now is a good time to boot from that and make backups of your data...?)

***edit***

Changed code to xubuntu-desktop for you...

---

### Post by oldfred on 2012-11-21
+1 on    	bryncoles suggestions.

Some of the older versions, once python was uninstalled you could not even get on the Internet. The only way to repair was to chroot into install and run the fixes from the chroot.

Do you have terminal and Internet working?

---

### Post by Nebelhom on 2012-11-21
Hi, Thanks for your quick answer.

I tried what you said, but I am getting a long list of:

```

W: Failed to fetch <Archive>
```

Errors. Judging by the list, this looks to be every archive there is.

I couldn't find a way to fix this, so far... Any ideas?

-----------------------------------
**edit**

Actually, forget that. I'm not having a good day. I used wireless previsouly and just assumed it would carry on working now. obviously that's not gonna work. Cable connection could fetched the archives.

---

### Post by Nebelhom on 2012-11-21
@oldfred: Terminal is working. internet is unconfirmed, but I am reasonably sure. I reinstalled python alright (at least it said it)

I can't copy the exact words, but it said something along the lines of "Was already installed, 1 file updated...

Hope that helps.

Thanks guys!

---

### Post by Nebelhom on 2012-11-21
@bryncoles: I wish, I'd seen that edit a bit earlier. I already went for ubuntu-desktop :( 

What's the difference? Will I have to clean up more afterwards?

Thanks for this really quick help!

---

### Post by bryncoles on 2012-11-21
You can confirm the net is working by typing

```
ping -c 5 www.google.com
```

and looking for output along the lines of:

```
5 packets transmitted, 5 received, 0% packet loss, time 1000ms
```

That tells you you can reach the server.  

Now...  You say it fails to fetch the archives...?  Lucid is still supported, so the archives should be there...

---

### Post by bryncoles on 2012-11-21
It's not a big difference.  ubuntu-desktop is the Gnome version, Xubuntu is the Xfce version.  It's quite easy to swap between them though, you would just run the following command from the [Psychocats website](http://www.psychocats.net/ubuntu/purexfcelucid)

```
sudo apt-get remove adium-theme-ubuntu alacarte app-install-data-partner binfmt-support binutils bluez-gstreamer branding-ubuntu brltty brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktopcouch empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot gbrainy gcc gcc-4.4 gconf-defaults-service gconf-editor gdm-guest-session gedit gedit-common gnome-about gnome-applets gnome-applets-data gnome-bluetooth gnome-control-center gnome-disk-utility gnome-media gnome-media-common gnome-nettool gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-session gnome-session-canberra gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-share gnome-utils gstreamer0.10-gnonlin gstreamer0.10-plugins-base-apps gstreamer0.10-tools gvfs-fuse gwibber gwibber-service humanity-icon-theme ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-me indicator-messages indicator-session indicator-sound libanthy0 libart2.0-cil libc-dev-bin libc6-dev libcamel1.2-14 libcanberra-pulse libcompizconfig0 libcouchdb-glib-1.0-2 libcryptui0 libdecoration0 libdesktopcouch-glib-1.0-2 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libgail-gnome-module libgconf2.0-cil libgd2-xpm libgdata-google1.2-1 libgdata1.2-1 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1 libglitz1 libgmime2.4-cil libgnome-keyring1.0-cil libgnome-media0 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.24-cil libgnomepanel2.24-cil libgoocanvas-common libgoocanvas3 libgpgme11 libgpod-common libgpod4 libgraphite3 libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common libgweather-common libgweather1 libhyphen0 libibus1 libical0 libido-0.1-0 liblaunchpad-integration1.0-cil liblpint-bonobo0 libm17n-0 libmetacity-private0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libmtp8 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls libnunit2.4-cil libotf0 libpisock9 libpisync1 libprotobuf5 libprotoc5 libpst4 libpth20 libraptor1 librasqal2 librdf0 libsctp1 libsdl1.2debian-pulseaudio libsqlite0 libstlport4.6ldbl libtelepathy-farsight0 libubuntuone-1.0-1 libupower-glib1 libwmf0.2-7-gtk light-themes linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-headers-generic linux-libc-dev lksctp-tools m17n-contrib m17n-db manpages-dev media-player-info metacity metacity-common mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share obexd-client openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-math openoffice.org-style-galaxy openoffice.org-style-human openoffice.org-writer pitivi pkg-config plymouth-theme-ubuntu-logo protobuf-compiler pulseaudio-module-bluetooth pulseaudio-module-gconf python-avahi python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight python-fstab python-gnomekeyring python-gtksourceview2 python-gtkspell python-ibus python-indicate python-mako python-openssl python-pam python-papyon python-protobuf python-pycurl python-pygoocanvas python-pyinotify python-serial python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone python-ubuntuone-client python-ubuntuone-storageprotocol python-uno python-wnck rdesktop rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store screen-resolution-extra seahorse ssh-askpass-gnome telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome uno-libs3 upower ure vino whois xdg-user-dirs-gtk xfonts-mathml && sudo apt-get install xubuntu-desktop
```

That ends with 'sudo apt-get install xubuntu-desktop', so you'll be fine!  (assuming the archives hit...)

---

### Post by Nebelhom on 2012-11-21
ok, update:

Despite my apparent lack of mental faculties during this rather lovely night and with your help, I was able to recover my desktop using

```
sudo apt-get install ubuntu-desktop
```

Some things are still gone (Dropbox installation), but I'm not complaining. Far from it. What is the best way to clean up after myself now. As in remove duplicate files or the like.

I better ask, in case I accidentally format the hard drive...

@bryncoles: Thanks so much for your assistence. Is there some sort of reputation thing (like in StackOverflow), I can vote for on your behalf. I haven't been on the forums in awhile.

---

### Post by bryncoles on 2012-11-21
There used to be a 'thanks button' for helpful posts, but apparently it was too much of a strain on the server, so now simply knowing I have helped in my reward!

The best way to clean up is the epic command I posted from the psychocats page (see my above post).  It's a cut-and-paster, as I wouldn't wnat to be the one typing it out!  Then you can start reinstalling all your things like dropbox.  If you're lucky, you'll still have the config files for them!

Glad I could help you!

---

