---
title: "switching to Xubuntu"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by Autodave on 2012-05-20
I currently have Ubuntu 12.04 running on my lowly Asus 900 netbook.  It runs fine, albeit a little slowly.  I would like to change to Xubuntu to free up some ram and pick up some speed.  Is it possible to do this without wiping and starting over?

---

### Post by Lisiano on 2012-05-20
Sure, just [press here to install Xubuntu](apt://xubuntu-desktop)
After it finishes installing, log out and look at the little cog near your username, click it and select Xubuntu. Log in as usual.

---

### Post by Autodave on 2012-05-20
> **Lisiano said:**
> Sure, just [press here to install Xubuntu]("apt://xubuntu-desktop")
After it finishes installing, log out and look at the little cog near your username, click it and select Xubuntu. Log in as usual.

OK...easy enough so far.  Now, can I or should I remove the unity desktop to save space on my tiny 20 gig SSD?  How do you remove it?

---

### Post by Autodave on 2012-05-20
> **Lisiano said:**
> Sure, just [press here to install Xubuntu]("apt://xubuntu-desktop")
After it finishes installing, log out and look at the little cog near your username, click it and select Xubuntu. Log in as usual.

I use auto login: do I have to change that?

---

### Post by Lisiano on 2012-05-20
You don't need to remove it if you want to keep it. Linux is quite small even if you have both Ubuntu and Xubuntu, since they share the same core, the extra space won't be that much different.

If you do want to remove Ubuntu. After logging into Xubuntu, open a terminal (Ctrl+Alt+T) and copy-paste the following.
```
sudo apt-get remove activity-log-manager-common activity-log-manager-control-center adium-theme-ubuntu apg appmenu-gtk appmenu-gtk3 appmenu-qt apturl apturl-common bamfdaemon baobab bluez-gstreamer branding-ubuntu brasero brasero-cdrkit brasero-common checkbox checkbox-qt cmap-adobe-japan2 compiz compiz-core compiz-gnome compiz-plugins-default compiz-plugins-main-default compizconfig-backend-gconf deja-dup duplicity dvd+rw-tools empathy empathy-common eog evolution-data-server evolution-data-server-common example-content folks-common gedit gedit-common geoclue geoclue-ubuntu-geoip ginn gir1.2-gnomebluetooth-1.0 gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 gir1.2-gtksource-3.0 gir1.2-indicate-0.7 gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-ubuntuoneui-3.0 gnome-bluetooth gnome-control-center gnome-control-center-data gnome-desktop3-data gnome-disk-utility gnome-font-viewer gnome-icon-theme-symbolic gnome-media gnome-menus gnome-nettool gnome-online-accounts gnome-orca gnome-power-manager gnome-screensaver gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-user-share growisofs gstreamer0.10-gconf gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter hwdata indicator-appmenu indicator-datetime indicator-power indicator-printers indicator-session intel-gpu-tools landscape-client-ui-install libatk-adaptor libatk-adaptor-schemas libaudio2 libavahi-gobject0 libavahi-ui-gtk3-0 libbamf0 libbamf3-0 libboost-serialization1.46.1 libbrasero-media3-1 libcamel-1.2-29 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcmis-0.2-0 libcompizconfig0 libcurl3 libcurl3-nss libdbusmenu-qt2 libdconf-dbus-1-0 libdconf-qt0 libdecoration0 libdiscid0 libdmapsharing-3.0-2 libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10 libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver-1.2-15 libedataserverui-3.0-1 libexempi3 libexttextcat-data libexttextcat0 libfolks-eds25 libfolks-telepathy25 libfolks25 libfreerdp-plugins-standard libfreerdp1 libgail-common libgdata-common libgdata13 libgdu-gtk0 libgexiv2-1 libglew1.6 libglewmx1.6 libgmime-2.6-0 libgnome-control-center1 libgnome-desktop-3-2 libgnome-media-profiles-3.0-0 libgnome2-common libgnomekbd-common libgnomekbd7 libgoa-1.0-0 libgoa-1.0-common libgpgme11 libgpod-common libgpod4 libgtksourceview-3.0-0 libgtksourceview-3.0-common libgtkspell-3-0 libgweather-3-0 libgweather-common libgwibber-gtk2 libgwibber2 libhyphen0 libidl-common libidl0 libjson-glib-1.0-0 liblircclient0 liblouis-data liblouis2 libmetacity-private0 libmission-control-plugins0 libmtp-common libmtp-runtime libmtp9 libmusicbrainz3-6 libmysqlclient18 libmythes-1.2-0 libneon27-gnutls libnux-2.0-0 libnux-2.0-common liboauth0 liborbit2 liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 libpackagekit-glib2-14 libpeas-1.0-0 libpeas-common libprotobuf7 libprotoc7 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpth20 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1 libqtgui4 libquvi-scripts libquvi7 libraw5 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-style-human libreoffice-style-tango libreoffice-writer librest-0.7-0 librhythmbox-core5 librsync1 libsdl1.2debian libssh-4 libstlport4.6ldbl libsyncdaemon-1.0-1 libtelepathy-farstream2 libtelepathy-logger2 libtimezonemap1 libtotem-plparser17 libtotem0 libubuntuoneui-3.0-1 libunique-3.0-0 libunity-2d-private0 libunity-core-5.0-5 libunity-misc4 libvncserver0 libwacom-common libwacom2 libwmf0.2-7-gtk libzeitgeist-1.0-1 light-themes linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic-pae linux-headers-generic-pae media-player-info metacity metacity-common mousetweaks mysql-common nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share notify-osd notify-osd-icons nux-tools obexd-client overlay-scrollbar plymouth-theme-ubuntu-logo protobuf-compiler pulseaudio-module-bluetooth pulseaudio-module-gconf python-aptdaemon.pkcompat python-brlapi python-configglue python-dateutil python-dirspec python-egenix-mxdatetime python-egenix-mxtools python-libproxy python-louis python-mako python-markupsafe python-packagekit python-protobuf python-pyatspi2 python-pyinotify python-speechd python-twisted-names python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno python-zeitgeist qdbus qt-at-spi remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone seahorse shotwell sni-qt ssh-askpass-gnome telepathy-gabble telepathy-haze telepathy-idle telepathy-indicator telepathy-logger telepathy-mission-control-5 telepathy-salut thunderbird-gnome-support totem totem-common totem-mozilla totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntu-wallpapers-precise ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-couch ubuntuone-installer unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-asset-pool unity-common unity-greeter unity-lens-applications unity-lens-files unity-lens-music unity-lens-video unity-scope-musicstores unity-scope-video-remote unity-services uno-libs3 ure vino whois whoopsie wodim xdiagnose xfonts-mathml zeitgeist zeitgeist-core zeitgeist-datahub && sudo apt-get install xubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter

```
It will ask for your password, while you type it, it won't be visible, just keep typing it and press Enter when you are done typing. Then press Enter again to confirm you want to delete Ubuntu.


EDIT: Yes, disable auto-login, log out of Ubuntu, log into Xubuntu, then re-enable it.

EDIT2: There is an edit button in the lower-righthand side of your post, use it if you want to edit your post instead of posting multiple times.

EDIT3: Don't open multiple threads on the same question in different forums, if you accidentally opened it in the wrong forum, please click the "Report abuse" button and ask a moderator to move your thread.

Also, the Asus Support is for questions related to Asus computers and laptops, not for vendor-independent questions like this.

---

### Post by Autodave on 2012-05-20
> **Lisiano said:**
> You don't need to remove it if you want to keep it. Linux is quite small even if you have both Ubuntu and Xubuntu, since they share the same core, the extra space won't be that much different.

EDIT: Yes, disable auto-login, log out of Ubuntu, log into Xubuntu, then re-enable it.

EDIT2: There is an edit button in the lower-righthand side of your post, use it if you want to edit your post instead of posting multiple times.

EDIT3: Don't open multiple threads on the same question in different forums, if you accidentally opened it in the wrong forum, please click the "Report abuse" button and ask a moderator to move your thread.

Also, the Asus Support is for questions related to Asus computers and laptops, not for vendor-independent questions like this.


Thanks!  Sorry for the double post: never knew how to get a post moved before!  And, I thought that it being an ASUS machine that I am talking about, that would be a better place to post it.

---

