---
title: "changing from xubuntu to lubuntu"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by coolsulabh on 2013-01-09
i have xubuntu 12.10 installed on my pc and i want to change it to lubuntu .i used the command apt-get install lubuntu-desktop -y && apt-get remove xubuntu-desktop -y.it installed some appplications but rest is same as xubuntu.i want to completely remove xubuntu.

---

### Post by llamabr on 2013-01-09
What do you mean the rest is the same?  What do you want to change?

---

### Post by vasa1 on 2013-01-09
Backup your data and just do a clean install of whatever you want over the existing one.

---

### Post by Elfy on 2013-01-10
> **llamabr said:**
> What do you mean the rest is the same?  What do you want to change?

This - it's entirely possible that Xubuntu and Lubuntu use some of the same apps. 

Regardless of that - a bit more detail will allow people to actually help you without a long list of questions beforehand.


> **coolsulabh said:**
> ...i used the command apt-get install lubuntu-desktop -y && apt-get remove xubuntu-desktop -y...

Edit - actually to remove xubuntu you need to do more than remove xubuntu-desktop,

the command to go from xubuntu to lubuntu would be more like 
```

sudo apt-get remove abiword-plugin-grammar abiword-plugin-mathview acpi-support acpid alacarte app-install-data-partner apt-xapian-index avahi-autoipd avahi-daemon binutils bison bluez-alsa bluez-cups brltty brltty-x11 cups-bsd dc doc-base docbook-xml espeak espeak-data exo-utils firefox firefox-globalmenu firefox-gnome-support flex fonts-droid fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-lklug-sinhala fonts-lyx fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-engine gcalctool gcc gcc-4.7 gigolo gir1.2-appindicator3-0.1 gir1.2-atspi-2.0 gir1.2-gmenu-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-soup-2.4 gir1.2-webkit-3.0 gmusicbrowser gnome-accessibility-themes gnome-games-data gnome-sudoku gnome-user-guide gnomine gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gthumb gthumb-data gtk2-engines-murrine gvfs-bin hplip hplip-data ibus-gtk ibus-pinyin ibus-pinyin-db-android ibus-pinyin-db-open-phrase ibus-table indicator-sound indicator-sound-gtk2 kerneloops-daemon laptop-detect libart-2.0-2 libasound2-plugins libavahi-core7 libbison-dev libbrlapi0.5 libc-dev-bin libc6-dev libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra0 libdaemon0 libdigest-crc-perl libdotconf1.0 libespeak1 libexiv2-12 libfile-copy-recursive-perl libfl-dev libgarcon-1-0 libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libgeoclue0 libgnome-menu-3-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgomp1 libgstreamer-perl libgtk2-notify-perl libgtk2-trayicon-perl libgtkmathview0c2a libgtkmm-3.0-1 libhpmud0 libical0 libido-0.1-0 libido3-0.1-0 libintl-perl libitm1 libjavascriptcoregtk-3.0-0 libkeybinder0 liblcms1 liblink-grammar4 liblua5.1-0 libnotify-bin libnss-mdns libopencc1 libotr2 libpam-gnome-keyring libpulsedsp libquadmath0 librarian0 libsane-hpaio libsensors4 libsexy2 libsnmp-base libsnmp15 libsonic0 libspeechd2 libspeexdsp1 libtagc0 libthunarx-2-0 libtumbler-1-0 libunique-1.0-0 libuuid-perl libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxfce4ui-utils libxfcegui4-4 libyaml-tiny-perl libyelp0 link-grammar-dictionaries-en linux-libc-dev m4 make manpages-dev mscompress network-manager-pptp network-manager-pptp-gnome onboard oneconf orage parole pastebinit pavucontrol pcmciautils pidgin-otr pinyin-database pkg-config plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text policykit-desktop-privileges pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-hpcups printer-driver-min12xxw printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix pulseaudio pulseaudio-module-x11 pulseaudio-utils python-configobj python-debtagshw python-dirspec python-gi-cairo python-gst0.10 python-httplib2 python-imaging python-lxml python-oauth python-openssl python-pam python-pexpect python-piston-mini-client python-renderpm python-reportlab python-reportlab-accel python-serial python-twisted-bin python-twisted-core python-twisted-web python-ubuntu-sso-client python-xapian python-zope.interface python3-cairo python3-gi-cairo python3-virtkey radeontool rarian-compat ristretto rtkit sane-utils screensaver-default-images scrollkeeper sessioninstaller sgml-base sgml-data shimmer-themes software-center software-center-aptdaemon-plugins sound-theme-freedesktop speech-dispatcher tcl8.5 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman thunderbird thunderbird-globalmenu toshset ttf-droid ttf-indic-fonts-core ttf-punjabi-fonts tumbler tumbler-common ubuntu-sso-client update-inetd xbrlapi xchat xchat-common xcursor-themes xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfwm4 xml-core xscreensaver-gl xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-icon-theme xubuntu-wallpapers xul-ext-ubufox yelp yelp-xsl zenity zenity-common && sudo apt-get install lubuntu-desktop
```

Check out aysiu's website - [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

xubuntu-desktop is a meta package - [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by black veils on 2013-01-14
maybe you just need to know how to switch, installing isnt the whole process.

at the login screen, you will have a session changer, click it and change to lubuntu, it will remember your setting.

---

