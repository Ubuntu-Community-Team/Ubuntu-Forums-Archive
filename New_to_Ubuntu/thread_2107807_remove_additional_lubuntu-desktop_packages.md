---
title: "remove additional lubuntu-desktop packages"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by jaramarana on 2013-01-22
I installed lubuntu-desktop from my unity desktop (12.10), but I'd like to undo it. When it installed, it was over 300mb. I can only remove a few kilobytes via sudo apt-get remove and autoremove. How can I expunge the remaining unnecessary programs that installed with lubuntu, and the other desktops that came with it like gnome/openbox?

I realise I asked a similar question after installing gnome, but this seems to be a different issue. I'll stop mucking about after this, promise...

---

### Post by Cheesemill on 2013-01-22
```
 sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman catfish chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg elementary-icon-theme fonts-lyx galculator gdebi gdebi-core gecko-mediaplayer giblib1 gnome-desktop-data gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview gtk2-engines-pixbuf guvcview hardinfo indicator-application-gtk2 leafpad libaacs0 libabiword-2.9 libass4 libaudclient2 libaudcore1 libavcodec53 libavformat53 libavutil51 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9 libenca0 libept1.4.12 libexo-1-0 libexo-common libexo-helpers libfaad2 libfluidsynth1 libfm-data libfm-gtk-bin libfm-gtk-data libfm-gtk3 libfm3 libgdome2-0 libgdome2-cpp-smart0c2a libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common libgsm1 libgtkmathview0c2a libgtkspell0 libguess1 libid3tag0 libimlib2 libindicate-gtk3 libjpeg-progs libjpeg-turbo-progs liblink-grammar4 libloudmouth1-0 libmenu-cache1 libmms0 libmodplug1 libmowgli2 libmp3lame0 libmpg123-0 libmusicbrainz3-6 libnet-dbus-perl libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0 libpisock9 libpostproc52 librarian0 libresid-builder0c2a libschroedinger-1.0-0 libsdl1.2debian libsidplay2 libswscale2 libtidy-0.99-0 libtie-ixhash-perl libts-0.0-0 libuniconf4.6 libva1 libvdpau1 libvpx1 libvte-common libvte9 libwebcam0 libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util6 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxvidcore4 lightdm-gtk-greeter link-grammar-dictionaries-en lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-12-10 lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lubuntu-lxpanel-icons lubuntu-software-center lxappearance lxappearance-obconf lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-data lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint ntp obconf openbox openbox-themes pcmanfm pidgin pidgin-data pidgin-libnotify pidgin-microblog plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-pysqlite2 python-support python-xklavier rarian-compat scrot sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic system-tools-backends transmission tsconf uvcdynctrl uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts xfce4-notifyd xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad xscreensaver xscreensaver-data && sudo apt-get install ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter 
```

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

### Post by jaramarana on 2013-01-22
Thank you very much - if the space to be freed is larger than what was taken up with the install, should I go through the list and remove items that look like ones I already use? For example, will the command to remove 'pidgin' touch the instance of pidgin that I already had?

apologies for my ignorance.

EDIT: just realised I installed pidgin rather than it being a default program. sorry.

---

### Post by Cheesemill on 2013-01-22
Yes.

The above command will remove all of the applications that are standard in Lubuntu but not in a normal Ubuntu installation. If you use Pidgin then remove it from the list.

---

### Post by jaramarana on 2013-01-22
it also apparently removed a load of unlisted applications, some of which i had installed, some of which are standard in ubuntu?

e.g. transmission (standard for me); gtg (i installed it)

i'll reinstall these now. why did that happen?

---

