---
title: "Ubuntu, Lubuntu and partitions"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by jowze on 2013-01-02
Hello hello !

So I have an old computer, I have a disc with Ubuntu 12.04 on it. Fine. 
I make a pure Ubuntu install. It works, but it's slow and laggy and just a general pain.

So I thought of putting Lubuntu onto it. 
I have a couple questions :

-If I install Ubuntu, and put Lubuntu, will the Ubuntu install that remains still slow the machine down ? Or running Lubuntu will be faster and smoother regardless ?

-Once Lubuntu is installed, can I [sudo apt-get remove] Ubuntu and run just on Lubuntu without causing problems ?

That's it for now, 
Thanks !
Jo

---

### Post by Megaptera on 2013-01-02
You could install Lubuntu & let it wipe Ubuntu completely - though backup your important docs, pics etc to external media first.

---

### Post by snowpine on 2013-01-02
You can "convert" your existing Ubuntu to "pure" Lubuntu following these directions:

[http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

---

### Post by grahammechanical on 2013-01-02
All the flavours of Ubuntu use the same installer. Just put in the Lubuntu live DVD and tick to use the entire disk and Lubuntu will install over Ubuntu, removing/deleting Ubuntu completely. You will find that the install process is the same except for the branding.

This I suggest is the simplest method.

Regards.

---

### Post by jowze on 2013-01-02
Megaptera - How would I do this ? Can you wipe Ubuntu completely by installing Lubuntu from the terminal in Ubuntu ? Or do you need to make another Boot CD ? I don't have any files to backup on this PC so it doesn't really matter.

Snowpine - the directions you sent, it says 'These removal commands were created based on what Ubuntu, Kubuntu, etc. packages were added to a default Lubuntu installation' in my case, Lubuntu will be added to Ubuntu and not the contrary. Will this manipulation work anyway ?

---

### Post by jowze on 2013-01-02
Graham - Yes i keep this option in mind, just I have no boot CD of Lubuntu and nothing to create one at the moment, if this was the only option, I would resort to it, if there was an alternative, I'd be happy to use it :)

---

### Post by jowze on 2013-01-02
so I found a blank dvd and did a Boot CD of lubuntu 32 bits version. 

I start the PC, boot from CD, select the basic partition that worked with Ubuntu before, installation starts and asks me for the usual Country, computer name and passwords etc. Install starts and then..........

Blank screen and sandclock. No more install progression bar, nothing... 

What could be the cause of this ? Would anyone know a workaround ?

---

### Post by docshawnc on 2013-01-02
An answer to your original question - if you install lubuntu along side of ubuntu and use grub to chose the system that runs, you should not notice a slowdown.

---

### Post by COMECON on 2013-01-02
You can install **Lubuntu** without reinstalling anything. Just run this on Ubuntu:
```
 $ sudo apt-get install lubuntu-desktop
```Then log out, and click on the little Ubuntu logo next to your username, and select Lubuntu there.
Then you can remove Unity:
```
 $ sudo apt-get remove account-plugin-aim  account-plugin-facebook account-plugin-flickr account-plugin-google  account-plugin-icons account-plugin-identica account-plugin-jabber  account-plugin-salut account-plugin-twitter account-plugin-windows-live  account-plugin-yahoo acpi-support acpid activity-log-manager-common  activity-log-manager-control-center adium-theme-ubuntu aisleriot apg  app-install-data-partner appmenu-gtk appmenu-gtk3 appmenu-qt  apt-xapian-index apturl apturl-common avahi-autoipd avahi-daemon  bamfdaemon baobab binutils bluez-alsa bluez-cups bluez-gstreamer  branding-ubuntu brasero brasero-cdrkit brasero-common brltty checkbox  checkbox-qt compiz compiz-core compiz-gnome compiz-plugins-default  cryptsetup-bin cups-bsd dc dconf-tools deja-dup doc-base duplicity  dvd+rw-tools empathy empathy-common eog espeak-data  evolution-data-server evolution-data-server-common example-content  firefox firefox-globalmenu firefox-gnome-support folks-common  fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao  fonts-lklug-sinhala fonts-opensymbol fonts-sil-abyssinica  fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg  fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari  fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa  fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist  fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-engine  freerdp-x11 gcalctool gcc gcc-4.7 gedit gedit-common geoclue  geoclue-ubuntu-geoip gir1.2-accounts-1.0 gir1.2-appindicator3-0.1  gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0  gir1.2-gdata-0.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0  gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0 gir1.2-gst-plugins-base-0.10  gir1.2-gstreamer-0.10 gir1.2-gtksource-3.0 gir1.2-gudev-1.0  gir1.2-indicate-0.7 gir1.2-javascriptcoregtk-3.0  gir1.2-messagingmenu-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-signon-1.0  gir1.2-soup-2.4 gir1.2-syncmenu-0.1 gir1.2-totem-1.0  gir1.2-totem-plparser-1.0 gir1.2-ubuntuoneui-3.0 gir1.2-unity-5.0  gir1.2-webkit-3.0 gnome-accessibility-themes gnome-bluetooth  gnome-contacts gnome-control-center gnome-control-center-data  gnome-control-center-signon gnome-desktop3-data gnome-font-viewer  gnome-games-data gnome-mahjongg gnome-media gnome-menus  gnome-online-accounts gnome-orca gnome-power-manager gnome-screensaver  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log  gnome-system-monitor gnome-terminal gnome-terminal-data  gnome-user-guide gnome-user-share gnomine growisofs gstreamer0.10-alsa  gstreamer0.10-gconf gstreamer0.10-plugins-base-apps  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x  gtk2-engines-murrine guile-1.8-libs gvfs-bin gwibber gwibber-service  gwibber-service-facebook gwibber-service-identica  gwibber-service-twitter hplip hplip-data hwdata ibus-gtk3 ibus-pinyin  ibus-pinyin-db-android ibus-pinyin-db-open-phrase ibus-table  indicator-appmenu indicator-datetime indicator-messages indicator-power  indicator-printers indicator-session indicator-sound intel-gpu-tools  kerneloops-daemon landscape-client-ui-install laptop-detect  libaccount-plugin-1.0-0 libaccounts-glib0 libaccounts-qt1 libart-2.0-2  libasound2-plugins libatk-adaptor libatk-adaptor-data libavahi-core7  libavahi-gobject0 libbamf3-0 libboost-date-time1.49.0  libbrasero-media3-1 libbrlapi0.5 libc-dev-bin libc6-dev libcamel-1.2-40  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libclutter-1.0-0  libclutter-1.0-common libclutter-gst-1.0-0 libclutter-gtk-1.0-0  libcmis-0.2-2 libcogl-common libcogl-pango0 libcogl9 libcompizconfig0  libcrypt-passwdmd5-perl libcryptsetup4 libcurl3-nss libdaemon0  libdbusmenu-qt2 libdecoration0 libdee-1.0-4 libdmapsharing-3.0-2  libdotconf1.0 libebackend-1.2-5 libebook-1.2-14 libecal-1.2-15  libedata-book-1.2-15 libedata-cal-1.2-18 libedataserver-1.2-17  libespeak1 libexempi3 libexiv2-12 libexttextcat-1.0-0 libexttextcat-data  libfile-copy-recursive-perl libfolks-eds25 libfolks-telepathy25  libfolks25 libfreerdp-plugins-standard libfreerdp1 libgail-common  libgail18 libgdata-common libgdata13 libgeoclue0 libgexiv2-1 libglew1.8  libglewmx1.8 libgmime-2.6-0 libgnome-control-center1  libgnome-desktop-3-4 libgnome-media-profiles-3.0-0 libgnome-menu-3-0  libgnome-menu2 libgnomekbd-common libgnomekbd8 libgoa-1.0-0  libgoa-1.0-common libgomp1 libgtkmm-3.0-1 libgtksourceview-3.0-0  libgtksourceview-3.0-common libgtkspell-3-0 libgweather-3-1  libgweather-common libgwibber-gtk3 libgwibber3 libhpmud0 libhyphen0  libical0 libido3-0.1-0 libindicate5 libitm1 libjavascriptcoregtk-3.0-0  libjs-jquery liblcms1 liblouis-data liblouis2 liblua5.1-0 liblvm2app2.2  libmessaging-menu0 libmetacity-private0a libmission-control-plugins0  libmng1 libmusicbrainz5-0 libmx-1.0-2 libmx-bin libmx-common  libmysqlclient18 libmythes-1.2-0 libnotify-bin libnss-mdns libnux-3.0-0  libnux-3.0-common liboauth0 libopencc1 libpackagekit-glib2-14  libpam-freerdp libpam-gnome-keyring libpeas-1.0-0 libpeas-common  libprotobuf7 libprotoc7 libproxy1-plugin-gsettings  libproxy1-plugin-networkmanager libpulsedsp libpython3.2 libqjson0  libqt4-dbus libqt4-declarative libqt4-designer libqt4-help  libqt4-network libqt4-script libqt4-scripttools libqt4-sql  libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml  libqt4-xmlpatterns libqtassistantclient4 libqtcore4 libqtgui4  libqtwebkit4 libquadmath0 libquvi-scripts libquvi7 libraw5  libreoffice-base-core libreoffice-calc libreoffice-common  libreoffice-core libreoffice-draw libreoffice-emailmerge  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us  libreoffice-impress libreoffice-math libreoffice-ogltrans  libreoffice-pdfimport libreoffice-presentation-minimizer  libreoffice-presenter-console libreoffice-style-human  libreoffice-style-tango libreoffice-writer librest-0.7-0  librhythmbox-core6 librsync1 libsane-hpaio libsensors4 libsgutils2-2  libsignon-extension1 libsignon-glib1 libsignon-plugins-common1  libsignon-qt1 libsnmp-base libsnmp15 libsonic0 libspeechd2 libspeexdsp1  libssh-4 libstlport4.6ldbl libsync-menu1 libsyncdaemon-1.0-1  libtelepathy-farstream2 libtelepathy-logger2 libtimezonemap1  libtotem-plparser17 libtotem0 libubuntuoneui-3.0-1 libufe-xidgetter0  libunity-core-6.0-5 libunity-misc4 libunity-protocol-private0  libunity-webapps0 libunity9 libuuid-perl libvncserver0 libwacom-common  libwacom2 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwmf0.2-7-gtk  libyaml-tiny-perl libyelp0 libzeitgeist-1.0-1 light-themes  lightdm-remote-session-freerdp lightdm-remote-session-uccsconfigure  linux-headers-generic-pae linux-libc-dev make manpages-dev  mcp-account-manager-uoa media-player-info metacity-common mousetweaks  mscompress mtools mysql-common nautilus nautilus-sendto  nautilus-sendto-empathy nautilus-share network-manager-pptp  network-manager-pptp-gnome notify-osd notify-osd-icons nux-tools  obexd-client onboard oneconf overlay-scrollbar overlay-scrollbar-gtk2  overlay-scrollbar-gtk3 pcmciautils pinyin-database pkg-config  plymouth-theme-ubuntu-logo policykit-desktop-privileges pptp-linux  printer-driver-c2esp printer-driver-foo2zjs printer-driver-hpcups  printer-driver-min12xxw printer-driver-postscript-hp  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi  printer-driver-splix protobuf-compiler pulseaudio  pulseaudio-module-bluetooth pulseaudio-module-gconf  pulseaudio-module-x11 pulseaudio-utils python-apport python-configglue  python-debtagshw python-dirspec python-gconf python-gi-cairo  python-gnupginterface python-gst0.10 python-httplib2 python-imaging  python-lxml python-mako python-markupsafe python-oauth python-openssl  python-pam python-pexpect python-piston-mini-client  python-problem-report python-protobuf python-pyinotify python-qt4  python-qt4-dbus python-renderpm python-reportlab python-reportlab-accel  python-serial python-simplejson python-sip python-twisted-bin  python-twisted-core python-twisted-names python-twisted-web  python-ubuntu-sso-client python-ubuntuone-client  python-ubuntuone-control-panel python-ubuntuone-storageprotocol  python-uno python-xapian python-zeitgeist python-zope.interface  python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-crypto  python3-gi-cairo python3-httplib2 python3-louis python3-lxml  python3-oauthlib python3-pyatspi2 python3-pycurl python3-speechd  python3-virtkey qdbus qt-at-spi radeontool remmina remmina-common  remmina-plugin-rdp remmina-plugin-vnc remote-login-service rhythmbox  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins  rhythmbox-ubuntuone rtkit samba-common samba-common-bin sane-utils  seahorse session-migration sessioninstaller sgml-base shotwell  signon-keyring-extension signon-plugin-oauth2 signon-plugin-password  signon-ui signond sni-qt software-center  software-center-aptdaemon-plugins sound-theme-freedesktop  speech-dispatcher ssh-askpass-gnome syslinux syslinux-common  syslinux-legacy telepathy-gabble telepathy-haze telepathy-idle  telepathy-indicator telepathy-logger telepathy-mission-control-5  telepathy-salut thin-client-config-agent thunderbird  thunderbird-globalmenu thunderbird-gnome-support toshset totem  totem-common totem-mozilla totem-plugins ttf-indic-fonts-core  ttf-punjabi-fonts ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono  ubuntu-settings ubuntu-sounds ubuntu-sso-client ubuntu-sso-client-qt  ubuntu-system-service ubuntu-wallpapers ubuntu-wallpapers-quantal  ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel  ubuntuone-control-panel-qt ubuntuone-couch udisks unity unity-asset-pool  unity-common unity-greeter unity-lens-applications unity-lens-files  unity-lens-gwibber unity-lens-music unity-lens-photos  unity-lens-shopping unity-lens-video unity-scope-gdocs  unity-scope-musicstores unity-scope-video-remote unity-services  unity-webapps-common unity-webapps-service uno-libs3 update-inetd ure  usb-creator-common usb-creator-gtk vino wodim xcursor-themes xdiagnose  xfonts-mathml xul-ext-ubufox xul-ext-unity xul-ext-websites-integration  yelp yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity  zenity-common && sudo apt-get install lubuntu-desktop  ubuntu-minimal && sudo /usr/lib/lightdm/lightdm-set-defaults -g  lightdm-gtk-greeter
```(Font: [Psychocats]("http://psychocats.net/ubuntu/purelubuntu"))

Catbuntu

---

### Post by nothingspecial on 2013-01-02
You can even run the Ubuntu you have now with LXDE which is the desktop environment Lubuntu uses and choose it when you log in.

This means you will not get all the apps that come with Lubuntu.......

.......but


...... you also will not get all the nice pretty stuff the Lubuntu teams have done to LXDE.

---

### Post by COMECON on 2013-01-02
> **nothingspecial said:**
> You can even run the Ubuntu you have now with LXDE which is the desktop environment Lubuntu uses and choose it when you log in.

This means you will not get all the apps that come with Lubuntu.......

.......but


...... you also will not get all the nice pretty stuff the Lubuntu teams have done to LXDE.

IIRC, lubuntu-desktop has all the modifications done to Lubuntu. For a "pure" LXDE experience, I think that the package is **lxde-core**, or some of the others **lxde-***.

Catbuntu

---

### Post by snowpine on 2013-01-03
> **jowze said:**
> Snowpine - the directions you sent, it says 'These removal commands were created based on what Ubuntu, Kubuntu, etc. packages were added to a default Lubuntu installation' in my case, Lubuntu will be added to Ubuntu and not the contrary. Will this manipulation work anyway ?

The directions will remove Ubuntu desktop and install Lubuntu desktop. There is no reason/need to completely reinstall to get Lubuntu desktop on your existing Ubuntu. You can even (if you choose) have both desktops installed and switch between them based on your mood that day. :)

---

