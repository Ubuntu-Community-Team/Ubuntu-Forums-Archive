---
title: "Cannot open system settings"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by j88n on 2014-01-07
NEW to Ubuntu, so bear with me here!

I cannot open system settings by pressing the power cog. If I  click on it, it'll just hang and won't open. So I tried to open it through the terminal by typing
 
> gnome-control-center

as suggested in another post. When doing that I get the error: 

> Bus error (core dumped)

I think I have multiple errors are at play here. The second problem I get is that I can't remove/upgrade/install things without getting this recurring error:

> E: Sub-process /usr/bin/dpkg exited unexpectedly

Any ideas where to start to fix this problem would be greatly appreciated. Thanks!

---

### Post by Bashing-om on 2014-01-07
j88n; Hi ! Welcome to the forum .

This might be tough to isolate. Lets make a start by cleaning up the system:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean

```

Next, see what the package manager thinks of the system as a whole:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```
In the event that the package manager reports any errors, stop and post the entire session so we see the context to aid the analysis.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-07
> sudo apt-get autoclean

```
sean@Sean-Monster:~$ sudo apt-get autoclean[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```


> sudo apt-get autoremove

```
sean@Sean-Monster:~$ sudo apt-get autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fonts-droid gir1.2-ubuntuoneui-3.0 gnome-exe-thumbnailer icoutils
  libcapi20-3 libencode-locale-perl libfile-listing-perl libfont-afm-perl
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libio-socket-inet6-perl libio-socket-ssl-perl
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl
  libmpg123-0 libnet-http-perl libnet-ssleay-perl libosmesa6 libpam-winbind
  libsocket6-perl libubuntuoneui-3.0-1 liburi-perl libwww-perl
  libwww-robotrules-perl thunderbird-globalmenu ttf-droid ttf-umefont
  ttf-unfonts-core winbind wine-gecko1.4 wine-gecko2.24 wine-mono4.5.2
  winetricks
0 upgraded, 0 newly installed, 42 to remove and 1601 not upgraded.
After this operation, 122 MB disk space will be freed.
Do you want to continue [Y/n]? y
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

I couldn't actually finish the steps because I got an error when doing autoremove... should I go through the other commands, or try to address this first??

---

### Post by Bashing-om on 2014-01-08
j88n; Well,

Proper thing is as you have done, stop, and deal with this "/usr/bin/dpkg exited unexpectedly".
It is late here my time, will cogitate on this and get back at ya in my AM.

I have not encountered this before.

I look forward  ->
[INDENT][INDENT]to a learning experience
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-01-08
j88n; My good morning !

Let's do some light probing and see if we can determine why "dpkg" is not in a happy state.
```

sudo apt-get update
sudo apt-get upgrade

```
Get us a hint of where to look.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-08
Sounds like a plan! Thanks for helping

> sudo apt-update
```


Get:1 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security Release.gpg [933 B]

Get:2 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security Release [49.6 kB]       
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal Release.gpg                         
   
Get:3 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates Release.gpg [933 B]
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports Release.gpg        
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal Release                         
Get:4 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates Release [49.6 kB]         
   
Get:5 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/universe amd64 Packages
[65.4 kB]
Get:6 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/main amd64 Packages [189
kB]
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports Release                   
   
Get:7 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/multiverse amd64
Packages [1,489 B]
Get:8 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/restricted amd64
Packages [3,469 B]
Get:9 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/main TranslationIndex
[73 B]
Get:10 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/multiverse
TranslationIndex [71 B]
Get:11 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/restricted
TranslationIndex [72 B]
Get:12 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/universe
TranslationIndex [73 B]
Get:13 [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/main Translation-en
[94.8 kB]
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/main Sources                        
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/universe Sources                    
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/restricted Sources                  
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/multiverse Sources                  
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/main amd64 Packages                 
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/universe amd64 Packages             
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/restricted amd64 Packages           
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/multiverse amd64 Packages           
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/main TranslationIndex               
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/multiverse TranslationIndex         
   
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/multiverse Translation-en 
   
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/restricted Translation-en 
   
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") quantal-security/universe Translation-en   
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/restricted TranslationIndex         
   
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/universe TranslationIndex           
   
Get:14 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/universe amd64 Packages
[210 kB]
Hit [http://ubuntu.mirror.cambrium.nl]("http://ubuntu.mirror.cambrium.nl/") precise Release.gpg                  
   
Get:15 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/main amd64 Packages [320
kB] 
Hit [http://ubuntu.mirror.cambrium.nl]("http://ubuntu.mirror.cambrium.nl/") precise Release                      
   
Hit [http://ubuntu.mirror.cambrium.nl]("http://ubuntu.mirror.cambrium.nl/") precise/main amd64 Packages          
   
Hit [http://ubuntu.mirror.cambrium.nl]("http://ubuntu.mirror.cambrium.nl/") precise/universe amd64 Packages
Hit [http://ubuntu.mirror.cambrium.nl]("http://ubuntu.mirror.cambrium.nl/") precise/main TranslationIndex
Hit [http://ubuntu.mirror.cambrium.nl]("http://ubuntu.mirror.cambrium.nl/") precise/universe TranslationIndex
Hit [http://ubuntu.mirror.cambrium.nl]("http://ubuntu.mirror.cambrium.nl/") precise/main Translation-en
Hit [http://ubuntu.mirror.cambrium.nl]("http://ubuntu.mirror.cambrium.nl/") precise/universe Translation-en
Get:16 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/multiverse amd64 Packages
[12.1 kB]
Get:17 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/restricted amd64 Packages 
[4,804 B]
Get:18 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/main TranslationIndex [74
B]
Get:19 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/multiverse
TranslationIndex [72 B]
Get:20 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/restricted
TranslationIndex [72 B]
Get:21 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/universe TranslationIndex
[74 B]
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/main amd64 Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/multiverse amd64 Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/restricted amd64 Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/main TranslationIndex
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/multiverse
TranslationIndex
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/restricted
TranslationIndex
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/main Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/multiverse Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/restricted Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal/universe Translation-en
Get:22 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/main Translation-en [156
kB]
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/restricted Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-updates/universe Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/main Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/restricted Translation-en
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") quantal-backports/universe Translation-en
Fetched 1,159 kB in 3s (384 kB/s)                      
Reading package lists... Done[FONT=arial][/FONT]
```[FONT=arial][/FONT]
> sudo apt-get upgrade[FONT=arial][/FONT]


```
 
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  apport apport-gtk apt-utils aptdaemon apturl apturl-common bamfdaemon baobab
  bluez brltty checkbox checkbox-qt colord command-not-found compiz
  compiz-core compiz-gnome compiz-plugins-default cpp cpp-4.6 cups-filters
  dbus dconf-gsettings-backend dconf-service debhelper default-jre-headless
  dpkg-dev empathy empathy-common eog evince evince-common
  evolution-data-server evolution-data-server-common
  foomatic-db-compressed-ppds g++ g++-4.6 gcc gcc-4.6 gcc-4.6-base gdal-bin
  gettext gettext-base ghc ghc-prof ghostscript ghostscript-x
  gir1.2-gdkpixbuf-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-unity-5.0
  gnome-bluetooth gnome-control-center gnome-control-center-data
  gnome-desktop3-data gnome-disk-utility gnome-font-viewer gnome-games-data
  gnome-keyring gnome-nettool gnome-online-accounts gnome-orca
  gnome-screensaver gnome-session gnome-session-bin gnome-session-common
  gnome-settings-daemon gnome-sudoku gnome-system-log gnome-user-share gnomine
  grass grub-common grub-ieee1275-bin grub-pc grub-pc-bin grub2-common
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gvfs gvfs-backends
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs gwibber
  gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter imagemagick indicator-appmenu indicator-datetime
  indicator-messages indicator-session irqbalance language-selector-common
  language-selector-gnome libatk-adaptor libbamf0 libbamf3-0 libblas3gf
  libcommons-dbcp-java libcompizconfig0 libcupsfilters1 libdconf-dbus-1-0
  libdecoration0 libdpkg-perl libexttextcat-data libfolks-eds25 libgail-3-0
  libgcc1 libgcj-bc libgck-1-0 libgcr-3-1 libgdata13 libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-common libgdk-pixbuf2.0-dev libgeos-c1 libgettextpo0
  libgexiv2-1 libgfortran3 libghc-base-unicode-symbols-dev
  libghc-base-unicode-symbols-prof libghc-bindings-dsl-dev libghc-cairo-dev
  libghc-cairo-prof libghc-cereal-dev libghc-cereal-prof libghc-conduit-dev
  libghc-conduit-prof libghc-configfile-dev libghc-configfile-prof
  libghc-crypto-api-dev libghc-crypto-api-prof libghc-data-default-dev
  libghc-data-default-prof libghc-digest-dev libghc-digest-prof
  libghc-dlist-dev libghc-dlist-prof libghc-dpkg-dev libghc-dpkg-prof
  libghc-entropy-dev libghc-entropy-prof libghc-event-list-dev
  libghc-event-list-prof libghc-explicit-exception-dev
  libghc-explicit-exception-prof libghc-glib-dev libghc-glib-prof
  libghc-hashable-dev libghc-hashable-prof libghc-haskell-src-dev
  libghc-haskell-src-prof libghc-hipmunk-dev libghc-hipmunk-prof
  libghc-hsemail-dev libghc-hsemail-prof libghc-hslogger-dev
  libghc-hslogger-prof libghc-hunit-dev libghc-hunit-prof
  libghc-lambdabot-utils-dev libghc-lambdabot-utils-prof libghc-largeword-dev
  libghc-largeword-prof libghc-lifted-base-dev libghc-lifted-base-prof
  libghc-logict-dev libghc-logict-prof libghc-midi-dev libghc-midi-prof
  libghc-missingh-dev libghc-missingh-prof libghc-monad-control-dev
  libghc-monad-control-prof libghc-monad-loops-dev libghc-monad-loops-prof
  libghc-monoid-transformer-dev libghc-monoid-transformer-prof libghc-mtl-dev
  libghc-mtl-prof libghc-network-dev libghc-network-prof
  libghc-non-negative-dev libghc-non-negative-prof libghc-numtype-dev
  libghc-numtype-prof libghc-parallel-dev libghc-parallel-prof
  libghc-parsec3-dev libghc-parsec3-prof libghc-polyparse-dev
  libghc-polyparse-prof libghc-pool-conduit-dev libghc-pool-conduit-prof
  libghc-primitive-dev libghc-primitive-prof libghc-puremd5-dev
  libghc-puremd5-prof libghc-quickcheck2-dev libghc-quickcheck2-prof
  libghc-random-dev libghc-random-prof libghc-ranges-dev libghc-ranges-prof
  libghc-regex-base-dev libghc-regex-base-prof libghc-regex-compat-dev
  libghc-regex-compat-prof libghc-regex-pcre-dev libghc-regex-pcre-prof
  libghc-regex-posix-dev libghc-regex-posix-prof libghc-regex-tdfa-dev
  libghc-regex-tdfa-prof libghc-resource-pool-dev libghc-resource-pool-prof
  libghc-semigroups-dev libghc-semigroups-prof libghc-socks-dev
  libghc-socks-prof libghc-split-dev libghc-split-prof libghc-statevar-dev
  libghc-statevar-prof libghc-stm-dev libghc-stm-prof libghc-svgcairo-dev
  libghc-svgcairo-prof libghc-syb-dev libghc-syb-prof libghc-tagged-dev
  libghc-tagged-prof libghc-tagsoup-dev libghc-tagsoup-prof libghc-text-dev
  libghc-text-prof libghc-transformers-base-dev libghc-transformers-base-prof
  libghc-transformers-dev libghc-transformers-prof libghc-unixutils-dev
  libghc-unixutils-prof libghc-utf8-string-dev libghc-utf8-string-prof
  libghc-utility-ht-dev libghc-utility-ht-prof libghc-vector-dev
  libghc-vector-prof libghc-zip-archive-dev libghc-zip-archive-prof
  libghc-zlib-dev libghc-zlib-prof libgnome-control-center1 libgoa-1.0-0
  libgoa-1.0-common libgomp1 libgpod-common libgpod4 libgs9 libgs9-common
  libgstreamer-plugins-bad0.10-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtkmm-3.0-1 libhsqldb-java liblapack3gf libnetpbm10 libogre-1.7.4
  libogre-1.7.4-dbg libpackagekit-glib2-14 libpam-winbind libpeas-1.0-0
  libplymouth2 libpoppler-glib8 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml
  libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtgui4 libquadmath0 libraptor2-0
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-us
  libreoffice-impress libreoffice-math libreoffice-style-tango
  libreoffice-writer libsane libsane-common libspandsp2 libspatialite3
  libstdc++6 libstdc++6-4.6-dev libtiff4 libtotem0 libunity9 libwbclient0
  libwxgtk2.8-0 lsb-release mahjongg metacity nautilus nautilus-data
  nautilus-sendto nautilus-sendto-empathy netpbm network-manager-gnome
  nvidia-common onboard openprinting-ppds overlay-scrollbar plymouth
  plymouth-label poppler-data poppler-utils printer-driver-c2esp
  printer-driver-foo2zjs printer-driver-postscript-hp printer-driver-ptouch
  printer-driver-pxljr printer-driver-splix procps python-apt python-aptdaemon
  python-aptdaemon.gtk3widgets python-debian python-packagekit
  python-ubuntu-sso-client python-ubuntuone-control-panel python-uno qdbus
  rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  samba-common seahorse shotwell smbclient software-center
  software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk synaptic telepathy-indicator thunderbird
  thunderbird-gnome-support thunderbird-locale-en totem totem-common
  totem-mozilla totem-plugins transmission-common transmission-gtk
  ttf-freefont ubuntu-minimal ubuntu-sso-client ubuntu-sso-client-qt
  ubuntu-wallpapers ubuntuone-control-panel ubuntuone-control-panel-qt ufw
  unattended-upgrades unity unity-common unity-greeter unity-lens-applications
  unity-lens-files unity-lens-music unity-lens-video unity-scope-musicstores
  unity-scope-video-remote unity-services update-manager update-manager-core
  update-notifier update-notifier-common upower usbmuxd whoopsie winbind
  xdiagnose xorg xpdf xz-utils
The following packages will be upgraded:
  accountsservice acl acpi-support acpid activity-log-manager-common
  activity-log-manager-control-center adduser adium-theme-ubuntu aisleriot
  alsa-base alsa-utils anacron antlr apg app-install-data
  app-install-data-partner apparmor appmenu-gtk appmenu-gtk3 appmenu-qt
  apport-symptoms apt apt-transport-https apt-xapian-index aptdaemon-data
  aspell aspell-en at at-spi2-core autoconf autotools-dev avahi-autoipd
  avahi-daemon avahi-utils base-files base-passwd bash bash-completion bc
  bind9-host binfmt-support binutils bluez-alsa bluez-cups bluez-gstreamer
  brasero brasero-cdrkit brasero-common bsdmainutils bsdutils build-essential
  busybox-initramfs busybox-static bzip2 ca-certificates ca-certificates-java
  cabextract camlp4 chromium-browser chromium-browser-l10n
  chromium-codecs-ffmpeg command-not-found-data compiz-plugins-main-default
  compizconfig-backend-gconf console-setup consolekit coreutils cpio cron
  cryptsetup-bin cups cups-bsd cups-client cups-common cups-ppdc curl dash
  dbus-x11 dc debconf debconf-i18n debianutils deja-dup desktop-file-utils
  dh-apparmor dictionaries-common diffutils dmidecode dmsetup dnsmasq-base
  dnsutils doc-base dosfstools dpkg duplicity dvd+rw-tools e2fslibs e2fsprogs
  ed eject enchant espeak espeak-data fakeroot file file-roller findutils
  firefox firefox-gnome-support firefox-locale-en flashplugin-installer
  folks-common fontconfig fontconfig-config fonts-droid fonts-horai-umefont
  fonts-kacst fonts-kacst-one fonts-liberation fonts-nanum fonts-opensymbol
  fonts-thai-tlwg fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma
  fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee
  fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush
  fonts-tlwg-waree fonts-unfonts-core foomatic-db-engine foomatic-filters
  freeglut3 ftp fuse gcalctool gcj-4.6-base gcj-4.6-jre-lib gconf-service
  gconf-service-backend gconf2 gconf2-common gdb gedit gedit-common
  genisoimage geoclue geoclue-ubuntu-geoip geoip-database ghostscript-cups
  ginn gir1.2-appindicator3-0.1 gir1.2-atk-1.0 gir1.2-atspi-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk-0.4 gir1.2-dee-1.0
  gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-gmenu-3.0 gir1.2-gnomekeyring-1.0
  gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 gir1.2-gtk-2.0
  gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-indicate-0.7
  gir1.2-javascriptcoregtk-3.0 gir1.2-launchpad-integration-3.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-rsvg-2.0 gir1.2-soup-2.4
  gir1.2-totem-plparser-1.0 gir1.2-ubuntuoneui-3.0 gir1.2-vte-2.90
  gir1.2-webkit-3.0 gir1.2-wnck-3.0 gksu glib-networking
  glib-networking-common glib-networking-services gnome-accessibility-themes
  gnome-icon-theme gnome-icon-theme-symbolic gnome-media gnome-menus
  gnome-power-manager gnome-screenshot gnome-session-canberra
  gnome-system-monitor gnome-terminal gnome-terminal-data gnome-user-guide
  gnupg gpgv grep groff-base growisofs gsettings-desktop-schemas
  gstreamer0.10-alsa gstreamer0.10-ffmpeg gstreamer0.10-gconf
  gstreamer0.10-nice gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines
  gtk2-engines-murrine gtk3-engines-unico gucharmap guile-1.8-libs gzip hdparm
  hostname hplip hplip-data html2text humanity-icon-theme hwdata hyphen-en-us
  ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-pinyin-db-android ibus-table
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-netx-common
  icoutils ifupdown im-switch imagemagick-common indicator-application
  indicator-power indicator-printers indicator-sound info initramfs-tools
  initramfs-tools-bin initscripts inputattach insserv install-info
  intel-gpu-tools iproute iptables iputils-arping iputils-ping
  iputils-tracepath isc-dhcp-client isc-dhcp-common iso-codes ivy java-common
  jockey-common jockey-gtk junit4 kbd kerneloops-daemon keyboard-configuration
  klibc-utils krb5-locales landscape-client-ui-install language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  launchpad-integration ledit less libaa1 libaccountsservice0 libacl1
  libalgorithm-diff-xs-perl libantlr-java libapache-pom-java libappindicator1
  libappindicator3-1 libapt-pkg4.12 libarchive12 libart-2.0-2 libasm3-java
  libasn1-8-heimdal libasound2 libasound2-plugins libaspell15 libasyncns0
  libatasmart4 libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0
  libatk1.0-data libatk1.0-dev libatkmm-1.6-1 libatspi2.0-0 libattr1 libaudio2
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7
  libavahi-glib1 libavahi-gobject0 libavahi-ui-gtk3-0 libavc1394-0
  libavcodec53 libavformat53 libavutil51 libbind9-80 libbiojava1.7-java
  libblkid1 libbluetooth3 libbrasero-media3-1 libbrlapi0.5 libbsd-dev libbsd0
  libbsf-java libburn4 libbytecode-java libbz2-1.0 libc-bin libc-dev-bin libc6
  libc6-dev libcaca0 libcairo-gobject2 libcairo-perl
  libcairo-script-interpreter2 libcairo2 libcairo2-dev libcairomm-1.0-1
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcap-ng0 libcap2
  libcap2-bin libcdaudio1 libcdio-cdda1 libcdio-paranoia1 libcdio13
  libcdparanoia0 libcdt4 libck-connector0 libcolord1 libcomerr2
  libcommons-cli-java libcommons-collections-java libcommons-collections3-java
  libcommons-lang-java libcommons-logging-java libcommons-parent-java
  libcommons-pool-java libcroco3 libcryptsetup4 libcups2 libcupscgi1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls
  libcurl3-nss libdaemon0 libdap11 libdapclient3 libdatrie1 libdb5.1
  libdbus-1-3 libdbus-glib-1-2 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdbusmenu-qt2 libdc1394-22 libdee-1.0-4
  libdevmapper-event1.02.1 libdevmapper1.02.1 libdirac-encoder0
  libdirectfb-1.2-9 libdiscid0 libdjvulibre-text libdjvulibre21
  libdmapsharing-3.0-2 libdns81 libdotconf1.0 libdrm-intel1 libdrm-nouveau1a
  libdrm-nouveau2 libdrm-radeon1 libdrm2 libdv4 libdvdnav4 libdvdread4
  libedit2 libelf1 libenca0 libenchant1c2a libencode-locale-perl libept1.4.12
  libespeak1 libevent-2.0-5 libexempi3 libexif12 libexpat1 libexpat1-dev
  libfaad2 libfarstream-0.1-0 libffi-dev libffi6 libfftw3-3
  libfile-listing-perl libfile-mimeinfo-perl libfindlib-ocaml
  libfindlib-ocaml-dev libflac8 libflite1 libfolks-telepathy25 libfolks25
  libfontconfig1 libfontconfig1-dev libfontenc1 libframe6
  libfreerdp-plugins-standard libfreerdp1 libfreetype6 libfreetype6-dev
  libfreexl1 libfribidi0 libfs6 libftdi1 libfuse2 libgail-common libgail18
  libgcj-common libgcj12 libgconf-2-4 libgconf2-4 libgcr-3-common libgcrypt11
  libgd2-xpm libgdata-common libgdbm3 libgee2 libgeis1 libgeoclue0 libgeoip1
  libgif4 libgirepository-1.0-1 libgksu2-0 libglib-perl libglib2.0-0
  libglib2.0-bin libglib2.0-data libglib2.0-dev libglibmm-2.4-1c2a
  libglu1-mesa libgmime-2.6-0 libgmp-dev libgmp10 libgmpxx4ldbl
  libgnome-keyring-common libgnome-keyring0 libgnome-media-profiles-3.0-0
  libgnome-menu-3-0 libgnome-menu2 libgnome2-common libgnomekbd-common
  libgnutls26 libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-l10n
  libgphoto2-port0 libgpm2 libgrail5 libgraph4 libgrip0 libgsm1
  libgssapi-krb5-2 libgssapi3-heimdal libgssdp-1.0-3
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtk2.0-dev libgtksourceview-3.0-0
  libgtksourceview-3.0-common libgtkspell-3-0 libgtop2-7 libgtop2-common
  libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4
  libgutenprint2 libgvc5 libgweather-common libhamcrest-java
  libhcrypto4-heimdal libhdf4-0-alt libheimbase1-heimdal libheimntlm0-heimdal
  libhpmud0 libhtml-form-perl libhtml-parser-perl libhtml-tree-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhunspell-1.3-0
  libhx509-5-heimdal libhyphen0 libibus-1.0-0 libical0 libice-dev libice6
  libicu48 libidn11 libido3-0.1-0 libiec61883-0 libieee1284-3 libijs-0.35
  libilmbase6 libindicate-gtk3 libindicate5 libindicator3-7 libindicator7
  libio-socket-ssl-perl libirrlicht1.7a libirrlicht1.7a-dbg libisc83
  libisccc80 libisccfg82 libisofs6 libiw30 libjack-jackd2-0 libjasper1
  libjavascriptcoregtk-3.0-0 libjbig2dec0 libjline-java libjpeg-turbo8
  libjs-jquery libjson-glib-1.0-0 libjson0 libjte1 libk5crypto3 libkeyutils1
  libklibc libkrb5-26-heimdal libkrb5-3 libkrb5support0
  liblaunchpad-integration-3.0-1 liblaunchpad-integration-common liblcms1
  libldap-2.4-2 liblightdm-gobject-1-0 liblircclient0 liblocale-gettext-perl
  liblockfile-bin liblockfile1 liblouis-data liblouis2 liblqr-1-0 libltdl7
  liblua5.1-0 liblvm2app2.2 liblwp-mediatypes-perl liblwp-protocol-https-perl
  liblwres80 liblzma5 libmagic1 libmailtools-perl libmeanwhile1 libmhash2
  libmikmod2 libminiupnpc8 libmission-control-plugins0 libmms0 libmng1
  libmodplug1 libmount1 libmp3lame0 libmpc2 libmpeg2-4 libmpfr4 libmpg123-0
  libmtdev1 libmtp-common libmtp-runtime libmtp9 libmysqlclient18
  libmythes-1.2-0 libnautilus-extension1a libncurses5 libncurses5-dev
  libncursesw5 libneon27-gnutls libnet-http-perl libnet-ssleay-perl
  libnetfilter-conntrack3 libnettle4 libnewt0.52 libnfnetlink0 libnice10
  libnih-dbus1 libnih1 libnl-3-200 libnl-genl-3-200 libnl-route-3-200
  libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2
  libnotify-bin libnotify4 libnspr4 libnspr4-0d libnss-mdns libnss3 libnss3-1d
  liboauth0 libodbc1 libofa0 libogg0 libopenal-data libopenal1 libopencc1
  libopencore-amrnb0 libopencore-amrwb0 libopenexr6 libopenjpeg2 libopenobex1
  liborc-0.4-0 libosmesa6 libp11-kit0 libpam-cap libpam-ck-connector
  libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime
  libpam0g libpango-perl libpango1.0-0 libpango1.0-dev libpangomm-1.4-1
  libpaper-utils libpaper1 libparted0debian1 libpathplan4 libpcap0.8 libpci3
  libpciaccess0 libpcre3 libpcre3-dev libpcrecpp0 libpcsclite1 libpeas-common
  libperl5.14 libpipeline1 libpixman-1-0 libpixman-1-dev libplist1 libpng12-0
  libpng12-dev libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0
  libpopt0 libportaudio2 libpostproc52 libpq5 libproj0 libprotobuf7 libprotoc7
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpth20 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin
  libpurple0 libpython2.7 libqtassistantclient4 libqtwebkit4 libquvi-scripts
  libquvi7 librarian0 librasqal3 libraw1394-11 libraw5 librdf0 libreadline6
  libregexp-java libreoffice-emailmerge libreoffice-style-human librest-0.7-0
  libroken18-heimdal librsvg2-2 librsvg2-bin librsvg2-common librsvg2-dev
  librsync1 librtmp0 libsamplerate0 libsane-hpaio libsasl2-2 libsasl2-modules
  libschroedinger-1.0-0 libsdl-mixer1.2 libsdl1.2debian libselinux1
  libsensors4 libservlet2.5-java libsgutils2-2 libshout3 libsigc++-2.0-0c2a
  libslang2 libslp1 libslv2-9 libsm-dev libsm6 libsmbclient libsndfile1
  libsnmp-base libsnmp15 libsocket6-perl libsonic0 libsoundtouch0
  libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeechd2 libspeex1
  libspeexdsp1 libsqlite3-0 libss2 libssh-4 libssl1.0.0
  libstartup-notification0 libswscale2 libsyncdaemon-1.0-1 libsysfs2 libt1-5
  libtag1-vanilla libtag1c2a libtalloc2 libtasn1-3 libtdb1
  libtelepathy-farstream2 libtelepathy-glib0 libtelepathy-logger2
  libtext-charwidth-perl libtext-iconv-perl libthai-data libthai0 libtheora0
  libtimezonemap1 libtinfo-dev libtinfo5 libtotem-plparser17 libts-0.0-0
  libubuntuoneui-3.0-1 libudev0 libunique-3.0-0 libunistring0
  libunity-2d-private0 libunity-misc4 libupower-glib1 liburi-perl libusb-0.1-4
  libusb-1.0-0 libutempter0 libuuid-perl libuuid1 libv4l-0 libv4lconvert0
  libva1 libvisual-0.4-0 libvisual-0.4-plugins libvncserver0 libvo-aacenc0
  libvo-amrwbenc0 libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1
  libvte-2.90-9 libvte-2.90-common libvte-common libvte9 libwacom-common
  libwacom2 libwavpack1 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwildmidi-config libwildmidi1 libwind0-heimdal libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck-3-common libwnck-common libwnck22 libwpd-0.9-9
  libwpg-0.2-2 libwps-0.2-2 libwrap0 libwww-perl libwxbase2.8-0 libx11-6
  libx11-data libx11-dev libx11-doc libx11-xcb1 libx86-1 libxapian22
  libxau-dev libxau6 libxaw7 libxcb-dri2-0 libxcb-glx0 libxcb-render0
  libxcb-render0-dev libxcb-shape0 libxcb-shm0 libxcb-shm0-dev libxcb-util0
  libxcb1 libxcb1-dev libxcomposite-dev libxcomposite1 libxcursor-dev
  libxcursor1 libxdamage-dev libxdamage1 libxdmcp-dev libxdmcp6 libxerces-c28
  libxerces2-java libxext-dev libxext6 libxfixes-dev libxfixes3 libxfont1
  libxft-dev libxft2 libxi-dev libxi6 libxinerama-dev libxinerama1 libxkbfile1
  libxklavier16 libxml-commons-external-java libxml-commons-resolver1.1-java
  libxml2 libxml2-utils libxmu6 libxmuu1 libxp6 libxpm4 libxpp3-java
  libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxslt1.1
  libxss1 libxstream-java libxt6 libxtst6 libxv1 libxvidcore4 libxvmc1
  libxxf86dga1 libxxf86vm1 libyaml-tiny-perl libyelp0 libzbar0 libzephyr4
  libzvbi-common libzvbi0 light-themes lightdm linux-firmware linux-libc-dev
  linux-sound-base lirc lockfile-progs login logrotate lsb-base lshw lsof
  ltrace m4 make makedev man-db manpages manpages-dev media-player-info
  memtest86+ metacity-common mime-support mlocate
  mobile-broadband-provider-info modemmanager module-init-tools mount mountall
  mousetweaks mscompress mtools mtr-tiny multiarch-support mysql-common nano
  nautilus-share ncurses-base ncurses-bin net-tools netbase netcat-openbsd
  network-manager network-manager-pptp network-manager-pptp-gnome notify-osd
  ntfs-3g ntpdate nux-tools obex-data-server obexd-client ocaml-base-nox
  ocaml-findlib ocaml-interp ocaml-nox odbcinst odbcinst1debian2 oneconf
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssh-client
  openssl os-prober oss-compat parted passwd patch pciutils pcmciautils perl
  perl-base perl-modules pkg-config plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text pm-utils policykit-1 policykit-1-gnome
  policykit-desktop-privileges powermgmt-base ppp pptp-linux
  printer-driver-gutenprint printer-driver-hpcups printer-driver-hpijs
  printer-driver-min12xxw printer-driver-pnm2ppa proj-bin proj-data
  protobuf-compiler psmisc pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python
  python-appindicator python-apport python-apt-common python-cairo
  python-crypto python-cups python-cupshelpers python-dateutil python-dbus
  python-dbus-dev python-debtagshw python-defer python-dirspec
  python-egenix-mxdatetime python-egenix-mxtools python-gconf python-gdbm
  python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gst0.10 python-gtk2 python-httplib2 python-ibus
  python-imaging python-keyring python-launchpadlib python-lazr.restfulclient
  python-libproxy python-libxml2 python-mako python-markupsafe python-minimal
  python-notify python-numpy python-opengl python-openssl python-pam
  python-pexpect python-piston-mini-client python-pkg-resources
  python-problem-report python-protobuf python-pyatspi2 python-pycurl
  python-pyinotify python-qt4 python-qt4-dbus python-renderpm python-reportlab
  python-reportlab-accel python-serial python-simplejson python-sip
  python-smbc python-software-properties python-support python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web
  python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey
  python-wxgtk2.8 python-wxversion python-xapian python-xdg python-xkit
  python-zeitgeist python-zope.interface python2.7 python2.7-minimal qt-at-spi
  radeontool rarian-compat readline-common remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc resolvconf rfkill rsync rsyslog rtkit
  samba-common-bin sane-utils sed sensible-utils sessioninstaller setserial
  sgml-base sgml-data shared-mime-info simple-scan sni-qt speech-dispatcher
  ssh-askpass-gnome ssl-cert strace sudo syslinux syslinux-common
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev sysv-rc sysvinit-utils tcl8.5 tcpd tcpdump
  telepathy-gabble telepathy-haze telepathy-idle telepathy-logger
  telepathy-mission-control-5 telepathy-salut telnet thunderbird-globalmenu
  thunderbird-locale-en-us time tk8.5 toshset tsconf ttf-droid
  ttf-ubuntu-font-family ttf-umefont ttf-unfonts-core tzdata tzdata-java
  ubuntu-artwork ubuntu-docs ubuntu-keyring ubuntu-mono ubuntu-standard
  ubuntu-system-service ubuntu-wallpapers-precise ubuntuone-client
  ubuntuone-client-gnome ubuntuone-couch ucf udev udisks unity-2d
  unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
  unity-asset-pool unixodbc uno-libs3 unrar unzip update-inetd upstart ure
  ureadahead usb-creator-common usb-creator-gtk usb-modeswitch
  usb-modeswitch-data usbutils util-linux uuid-runtime vdr vim-common vim-tiny
  vino wget whiptail whois wireless-tools wodim wpasupplicant x11-apps
  x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils
  x11-xserver-utils x11proto-core-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-xext-dev xauth xdg-user-dirs xdg-user-dirs-gtk
  xfonts-mathml xfonts-utils xinit xinput xkb-data xml-core xserver-common
  xterm xtrans-dev xul-ext-ubufox yelp yelp-xsl zeitgeist zeitgeist-core
  zeitgeist-datahub zenity zenity-common zip zlib1g zlib1g-dev
1215 upgraded, 0 newly installed, 0 to remove and 415 not upgraded.
Need to get 0 B/553 MB of archives.
After this operation, 17.3 MB disk space will be freed.
Do you want to continue [Y/n]? 
y

...........


ubuntu4 [7,784 B]
Get:966 http://archive.ubuntu.com/ubuntu/ quantal/main libcap2-bin amd64 1:2.22-1ubuntu4 [17.8 kB]
Get:967 http://archive.ubuntu.com/ubuntu/ quantal/universe libcdaudio1 amd64 0.99.12p2-12 [42.0 kB]
Get:968 http://archive.ubuntu.com/ubuntu/ quantal/main libcdio13 amd64 0.83-4 [64.5 kB]
Get:969 http://archive.ubuntu.com/ubuntu/ quantal/main libcdio-cdda1 amd64 0.83-4 [17.8 kB]
Get:970 http://archive.ubuntu.com/ubuntu/ quantal/main libcdio-paranoia1 amd64 0.83-4 [17.6 kB]
Get:971 http://archive.ubuntu.com/ubuntu/ quantal/main libcdt4 amd64 2.26.3-12ubuntu1 [24.0 kB]
Get:972 http://archive.ubuntu.com/ubuntu/ quantal/main libcommons-lang-java all 2.6-3ubuntu2 [270 kB]
Get:973 http://archive.ubuntu.com/ubuntu/ quantal/main libcommons-cli-java all 1.2-3ubuntu1 [39.0 kB]
Get:974 http://archive.ubuntu.com/ubuntu/ quantal/main libcommons-collections3-java all 3.2.1-5build1 [603 kB]
Get:975 http://archive.ubuntu.com/ubuntu/ quantal/main libcommons-parent-java all 22-2build1 [6,968 B]
Get:976 http://archive.ubuntu.com/ubuntu/ quantal/main libcommons-logging-java all 1.1.1-9ubuntu1 [116 kB]
Get:977 http://archive.ubuntu.com/ubuntu/ quantal/main libdmapsharing-3.0-2 amd64 2.9.15-1 [79.2 kB]
Get:978 http://archive.ubuntu.com/ubuntu/ quantal/main libdotconf1.0 amd64 1.0.13-3build1 [13.5 kB]
Get:979 http://archive.ubuntu.com/ubuntu/ quantal/main libenca0 amd64 1.13-4build1 [68.8 kB]
Get:980 http://archive.ubuntu.com/ubuntu/ quantal/main libept1.4.12 amd64 1.0.9 [135 kB]
Get:981 http://archive.ubuntu.com/ubuntu/ quantal/main libfile-mimeinfo-perl all 0.16-1 [47.9 kB]
Get:982 http://archive.ubuntu.com/ubuntu/ quantal/main libfindlib-ocaml-dev amd64 1.3.1-1 [138 kB]
Get:983 http://archive.ubuntu.com/ubuntu/ quantal/main libfindlib-ocaml amd64 1.3.1-1 [104 kB]
Get:984 http://archive.ubuntu.com/ubuntu/ quantal/main libfolks25 amd64 0.7.4.1-0ubuntu1 [176 kB]
Get:985 http://archive.ubuntu.com/ubuntu/ quantal/main libfolks-telepathy25 amd64 0.7.4.1-0ubuntu1 [79.7 kB]
Get:986 http://archive.ubuntu.com/ubuntu/ quantal/main libfreerdp1 amd64 1.0.1-1ubuntu7 [254 kB]
Get:987 http://archive.ubuntu.com/ubuntu/ quantal/main libfreerdp-plugins-standard amd64 1.0.1-1ubuntu7 [77.3 kB]
Get:988 http://archive.ubuntu.com/ubuntu/ quantal/main libgcr-3-common all 3.6.0-0ubuntu1 [7,684 B]
Get:989 http://archive.ubuntu.com/ubuntu/ quantal/main libgdata-common all 0.13.2-0ubuntu1 [17.4 kB]
Get:990 http://archive.ubuntu.com/ubuntu/ quantal/main libglib-perl amd64 3:1.261-1 [379 kB]
Get:991 http://archive.ubuntu.com/ubuntu/ quantal/main libgnome-menu2 amd64 3.0.1-0ubuntu8 [52.5 kB]
Get:992 http://archive.ubuntu.com/ubuntu/ quantal/main libgnome2-common all 2.32.1-2ubuntu3 [36.7 kB]
Get:993 http://archive.ubuntu.com/ubuntu/ quantal/main libgnomekbd-common all 3.6.0-0ubuntu1 [8,484 B]
Get:994 http://archive.ubuntu.com/ubuntu/ quantal/main libgraph4 amd64 2.26.3-12ubuntu1 [36.5 kB]
Get:995 http://archive.ubuntu.com/ubuntu/ quantal/main libgrip0 amd64 0.3.5-0ubuntu1 [16.1 kB]
Get:996 http://archive.ubuntu.com/ubuntu/ quantal/main libpango-perl amd64 1.223-0ubuntu1 [222 kB]
Get:997 http://archive.ubuntu.com/ubuntu/ quantal/main libgtk2-perl amd64 2:1.244-1ubuntu1 [935 kB]
Get:998 http://archive.ubuntu.com/ubuntu/ quantal/main libgtk2.0-bin amd64 2.24.13-0ubuntu2 [10.3 kB]
Get:999 http://archive.ubuntu.com/ubuntu/ quantal/main libgtkspell-3-0 amd64 3.0.0~hg20110814-1build1 [14.5 kB]
Get:1000 http://archive.ubuntu.com/ubuntu/ quantal/main libpathplan4 amd64 2.26.3-12ubuntu1 [29.1 kB]
Get:1001 http://archive.ubuntu.com/ubuntu/ quantal/main libgvc5 amd64 2.26.3-12ubuntu1 [520 kB]
Get:1002 http://archive.ubuntu.com/ubuntu/ quantal/main libhyphen0 amd64 2.8.3-2 [21.0 kB]
Get:1003 http://archive.ubuntu.com/ubuntu/ quantal/main libical0 amd64 0.48-2 [208 kB]
Get:1004 http://archive.ubuntu.com/ubuntu/ quantal/main libijs-0.35 amd64 0.35-8build1 [16.8 kB]
Get:1005 http://archive.ubuntu.com/ubuntu/ quantal/main libilmbase6 amd64 1.0.1-4 [118 kB]
Get:1006 http://archive.ubuntu.com/ubuntu/ quantal/main libindicate-gtk3 amd64 12.10.1-0ubuntu1 [5,476 B]
Get:1007 http://archive.ubuntu.com/ubuntu/ quantal/main libjbig2dec0 amd64 0.11-1ubuntu2 [41.3 kB]
Get:1008 http://archive.ubuntu.com/ubuntu/ quantal/main libjline-java all 1.0-2 [69.4 kB]
Get:1009 http://archive.ubuntu.com/ubuntu/ quantal/main libjs-jquery all 1.7.2+debian-1ubuntu1 [115 kB]
Get:1010 http://archive.ubuntu.com/ubuntu/ quantal/main x11-xkb-utils amd64 7.7~1 [197 kB]
Get:1011 http://archive.ubuntu.com/ubuntu/ quantal/main libxklavier16 amd64 5.2.1-1ubuntu2 [50.0 kB]
Get:1012 http://archive.ubuntu.com/ubuntu/ quantal/main liblightdm-gobject-1-0 amd64 1.4.0-0ubuntu2 [32.7 kB]
Get:1013 http://archive.ubuntu.com/ubuntu/ quantal/main libmailtools-perl all 2.09-1 [83.9 kB]
Get:1014 http://archive.ubuntu.com/ubuntu/ quantal/main libmeanwhile1 amd64 1.0.2-4ubuntu2 [89.7 kB]
Get:1015 http://archive.ubuntu.com/ubuntu/ quantal/main libmhash2 amd64 0.9.9.9-1.1 [101 kB]
Get:1016 http://archive.ubuntu.com/ubuntu/ quantal/main libminiupnpc8 amd64 1.6-3ubuntu2 [23.3 kB]
Get:1017 http://archive.ubuntu.com/ubuntu/ quantal/main telepathy-mission-control-5 amd64 1:5.13.1-0ubuntu3 [186 kB]
Get:1018 http://archive.ubuntu.com/ubuntu/ quantal/main libmission-control-plugins0 amd64 1:5.13.1-0ubuntu3 [19.3 kB]
Get:1019 http://archive.ubuntu.com/ubuntu/ quantal/universe libmodplug1 amd64 1:0.8.8.4-3 [169 kB]
Get:1020 http://archive.ubuntu.com/ubuntu/ quantal/main libmythes-1.2-0 amd64 2:1.2.2-1build1 [9,032 B]
Get:1021 http://archive.ubuntu.com/ubuntu/ quantal/main libneon27-gnutls amd64 0.29.6-3 [76.4 kB]
Get:1022 http://archive.ubuntu.com/ubuntu/ quantal/main libnm-glib-vpn1 amd64 0.9.6.0-0ubuntu7 [16.0 kB]
Get:1023 http://archive.ubuntu.com/ubuntu/ quantal/main libnm-gtk-common all 0.9.6.2-0ubuntu6 [5,768 B]
Get:1024 http://archive.ubuntu.com/ubuntu/ quantal/main policykit-1-gnome amd64 0.105-1ubuntu4 [27.8 kB]
Get:1025 http://archive.ubuntu.com/ubuntu/ quantal/main libnm-gtk0 amd64 0.9.6.2-0ubuntu6 [67.2 kB]
Get:1026 http://archive.ubuntu.com/ubuntu/ quantal/main libnotify-bin amd64 0.7.5-1build1 [7,324 B]
Get:1027 http://archive.ubuntu.com/ubuntu/ quantal/main libnss-mdns amd64 0.10-3.2build1 [26.0 kB]
Get:1028 http://archive.ubuntu.com/ubuntu/ quantal/universe libofa0 amd64 0.9.3-5 [56.2 kB]
Get:1029 http://archive.ubuntu.com/ubuntu/ quantal/main libopenexr6 amd64 1.6.1-6 [227 kB]
Get:1030 http://archive.ubuntu.com/ubuntu/ quantal/main libopenobex1 amd64 1.5-2build2 [22.2 kB]
Get:1031 http://archive.ubuntu.com/ubuntu/ quantal-updates/main libpam-ck-connector amd64 0.4.5-3ubuntu0.1 [8,266 B]
Get:1032 http://archive.ubuntu.com/ubuntu/ quantal/main libpaper-utils amd64 1.1.24+nmu2 [9,116 B]
Get:1033 http://archive.ubuntu.com/ubuntu/ quantal/main libplist1 amd64 1.8-2 [25.9 kB]
Get:1034 http://archive.ubuntu.com/ubuntu/ quantal-updates/main libpq5 amd64 9.1.11-0ubuntu0.12.10 [75.0 kB]
Get:1035 http://archive.ubuntu.com/ubuntu/ quantal/main libzephyr4 amd64 3.0.2-2 [31.6 kB]
Get:1036 http://archive.ubuntu.com/ubuntu/ quantal/main librasqal3 amd64 0.9.29-1 [201 kB]
Get:1037 http://archive.ubuntu.com/ubuntu/ quantal/main librdf0 amd64 1.0.15-1 [111 kB]
Get:1038 http://archive.ubuntu.com/ubuntu/ quantal/main libregexp-java all 1.5-3build1 [35.1 kB]
Get:1039 http://archive.ubuntu.com/ubuntu/ quantal-updates/main libreoffice-emailmerge all 1:3.6.2~rc2-0ubuntu4 [31.7 kB]
Get:1040 http://archive.ubuntu.com/ubuntu/ quantal-updates/main libreoffice-style-human all 1:3.6.2~rc2-0ubuntu4 [2,022 kB]
Get:1041 http://archive.ubuntu.com/ubuntu/ quantal/main librsvg2-bin amd64 2.36.3-0ubuntu1 [19.0 kB]
Get:1042 http://archive.ubuntu.com/ubuntu/ quantal/main libsgutils2-2 amd64 1.33-1build1 [61.5 kB]
Get:1043 http://archive.ubuntu.com/ubuntu/ quantal/main libslp1 amd64 1.2.1-9 [45.1 kB]
Get:1044 http://archive.ubuntu.com/ubuntu/ quantal/universe libslv2-9 amd64 0.6.6+dfsg1-2 [26.8 kB]
Get:1045 http://archive.ubuntu.com/ubuntu/ quantal/main libsocket6-perl amd64 0.23-1build3 [22.8 kB]
Get:1046 http://archive.ubuntu.com/ubuntu/ quantal/main libt1-5 amd64 5.1.2-3.5 [158 kB]
Get:1047 http://archive.ubuntu.com/ubuntu/ quantal/main libtimezonemap1 amd64 0.3.2build1 [531 kB]
Get:1048 http://archive.ubuntu.com/ubuntu/ quantal/main libunique-3.0-0 amd64 3.0.2-1build1 [26.4 kB]
Get:1049 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe unity-2d-spread all 6.12.0-0ubuntu0.2 [9,296 B]
Get:1050 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe unity-2d-panel all 6.12.0-0ubuntu0.2 [9,296 B]
Get:1051 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe unity-2d-shell all 6.12.0-0ubuntu0.2 [9,298 B]
Get:1052 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe libunity-2d-private0 all 6.12.0-0ubuntu0.2 [9,308 B]
Get:1053 http://archive.ubuntu.com/ubuntu/ quantal/main libunity-misc4 amd64 4.0.4-0ubuntu3 [26.7 kB]
Get:1054 http://archive.ubuntu.com/ubuntu/ quantal/main libutempter0 amd64 1.1.5-4build1 [8,366 B]
Get:1055 http://archive.ubuntu.com/ubuntu/ quantal/main libvisual-0.4-plugins amd64 0.4.0.dfsg.1-7build1 [131 kB]
Get:1056 http://archive.ubuntu.com/ubuntu/ quantal/main libvte-common all 1:0.28.2-5ubuntu1 [22.8 kB]
Get:1057 http://archive.ubuntu.com/ubuntu/ quantal/main libvte9 amd64 1:0.28.2-5ubuntu1 [374 kB]
Get:1058 http://archive.ubuntu.com/ubuntu/ quantal/main libwnck-common all 1:2.30.7-0ubuntu2 [16.6 kB]
Get:1059 http://archive.ubuntu.com/ubuntu/ quantal/main libwnck22 amd64 1:2.30.7-0ubuntu2 [119 kB]
Get:1060 http://archive.ubuntu.com/ubuntu/ quantal/main libwpd-0.9-9 amd64 0.9.4-3 [306 kB]
Get:1061 http://archive.ubuntu.com/ubuntu/ quantal/main libwpg-0.2-2 amd64 0.2.1-1build1 [72.4 kB]
Get:1062 http://archive.ubuntu.com/ubuntu/ quantal/main libwps-0.2-2 amd64 0.2.7-1 [183 kB]
Get:1063 http://archive.ubuntu.com/ubuntu/ quantal/main libxml-commons-resolver1.1-java all 1.2-7build1 [91.6 kB]
Get:1064 http://archive.ubuntu.com/ubuntu/ quantal/main libxml-commons-external-java all 1.4.01-2build1 [245 kB]
Get:1065 http://archive.ubuntu.com/ubuntu/ quantal/main libxerces2-java all 2.11.0-6 [1,363 kB]
Get:1066 http://archive.ubuntu.com/ubuntu/ quantal/main libxpp3-java all 1.1.4c-2build1 [364 kB]
Get:1067 http://archive.ubuntu.com/ubuntu/ quantal/universe libxstream-java all 1.4.2-1 [555 kB]
Get:1068 http://archive.ubuntu.com/ubuntu/ quantal/universe libzbar0 amd64 0.10+doc-7build3 [93.2 kB]
Get:1069 http://archive.ubuntu.com/ubuntu/ quantal/main ubuntu-mono all 0.0.49 [8,392 kB]
Get:1070 http://archive.ubuntu.com/ubuntu/ quantal/main light-themes all 0.1.93 [293 kB]
Get:1071 http://archive.ubuntu.com/ubuntu/ quantal/main manpages-dev all 3.40-0.1ubuntu3 [1,710 kB]
Get:1072 http://archive.ubuntu.com/ubuntu/ quantal/main media-player-info all 17-1 [36.7 kB]
Get:1073 http://archive.ubuntu.com/ubuntu/ quantal/main sgml-base all 1.26+nmu3ubuntu1 [11.5 kB]
Get:1074 http://archive.ubuntu.com/ubuntu/ quantal/main metacity-common all 1:2.34.8-0ubuntu4 [108 kB]
Get:1075 http://archive.ubuntu.com/ubuntu/ quantal/main modemmanager amd64 0.6.0.0.really-0ubuntu1 [383 kB]
Get:1076 http://archive.ubuntu.com/ubuntu/ quantal/main mousetweaks amd64 3.6.0-0ubuntu2 [42.7 kB]
Get:1077 http://archive.ubuntu.com/ubuntu/ quantal/main mtools amd64 4.0.17-1 [194 kB]
Get:1078 http://archive.ubuntu.com/ubuntu/ quantal/main nautilus-share amd64 0.7.3-1ubuntu3 [23.2 kB]
Get:1079 http://archive.ubuntu.com/ubuntu/ quantal/main network-manager-pptp-gnome amd64 0.9.6.0-0ubuntu1 [28.1 kB]
Get:1080 http://archive.ubuntu.com/ubuntu/ quantal/main pptp-linux amd64 1.7.2-7 [49.0 kB]
Get:1081 http://archive.ubuntu.com/ubuntu/ quantal/main network-manager-pptp amd64 0.9.6.0-0ubuntu1 [22.5 kB]
Get:1082 http://archive.ubuntu.com/ubuntu/ quantal-updates/main nux-tools amd64 3.10.0-0ubuntu1 [11.1 kB]
Get:1083 http://archive.ubuntu.com/ubuntu/ quantal/main obex-data-server amd64 0.4.6-0ubuntu2 [83.8 kB]
Get:1084 http://archive.ubuntu.com/ubuntu/ quantal/main obexd-client amd64 0.46-1ubuntu2 [74.4 kB]
Get:1085 http://archive.ubuntu.com/ubuntu/ quantal/main ocaml-findlib amd64 1.3.1-1 [263 kB]
Get:1086 http://archive.ubuntu.com/ubuntu/ quantal/main os-prober amd64 1.56ubuntu1 [18.9 kB]
Get:1087 http://archive.ubuntu.com/ubuntu/ quantal/main patch amd64 2.6.1-3ubuntu1 [79.9 kB]
Get:1088 http://archive.ubuntu.com/ubuntu/ quantal/main plymouth-theme-ubuntu-logo amd64 0.8.4-0ubuntu3 [19.4 kB]
Get:1089 http://archive.ubuntu.com/ubuntu/ quantal/main policykit-desktop-privileges all 0.12 [3,450 B]
Get:1090 http://archive.ubuntu.com/ubuntu/ quantal/main printer-driver-gutenprint amd64 5.2.9-1ubuntu1 [385 kB]
Get:1091 http://archive.ubuntu.com/ubuntu/ quantal/main printer-driver-min12xxw amd64 0.0.9-6ubuntu2 [47.7 kB]
Get:1092 http://archive.ubuntu.com/ubuntu/ quantal/main printer-driver-pnm2ppa amd64 1.13+nondbs-0ubuntu2 [210 kB]
Get:1093 http://archive.ubuntu.com/ubuntu/ quantal-updates/main pulseaudio-module-gconf amd64 1:2.1-0ubuntu4.1 [14.0 kB]
Get:1094 http://archive.ubuntu.com/ubuntu/ quantal-updates/main pulseaudio-module-x11 amd64 1:2.1-0ubuntu4.1 [19.2 kB]
Get:1095 http://archive.ubuntu.com/ubuntu/ quantal/main python-crypto amd64 2.6-2 [366 kB]
Get:1096 http://archive.ubuntu.com/ubuntu/ quantal/main python-cups amd64 1.9.62-0ubuntu1 [63.2 kB]
Get:1097 http://archive.ubuntu.com/ubuntu/ quantal/main python-cupshelpers all 1.3.11+20120807-0ubuntu10 [36.1 kB]
Get:1098 http://archive.ubuntu.com/ubuntu/ quantal/main python-dateutil all 1.5+dfsg-0.1 [54.4 kB]
Get:1099 http://archive.ubuntu.com/ubuntu/ quantal/main python-debtagshw all 1.10.2 [12.8 kB]
Get:1100 http://archive.ubuntu.com/ubuntu/ quantal/main python-egenix-mxtools amd64 3.2.1-1.1 [89.1 kB]
Get:1101 http://archive.ubuntu.com/ubuntu/ quantal/main python-egenix-mxdatetime amd64 3.2.1-1.1 [78.6 kB]
Get:1102 http://archive.ubuntu.com/ubuntu/ quantal/main python-gconf amd64 2.28.1+dfsg-1build1 [28.3 kB]
Get:1103 http://archive.ubuntu.com/ubuntu/ quantal/main python-gdbm amd64 2.7.3-1ubuntu2 [13.6 kB]
Get:1104 http://archive.ubuntu.com/ubuntu/ quantal/main python-gnomekeyring amd64 2.32.0+dfsg-2ubuntu1 [26.8 kB]
Get:1105 http://archive.ubuntu.com/ubuntu/ quantal/main python-gst0.10 amd64 0.10.22-3ubuntu1 [295 kB]
Get:1106 http://archive.ubuntu.com/ubuntu/ quantal/main python-simplejson amd64 2.6.1-1 [76.9 kB]
Get:1107 http://archive.ubuntu.com/ubuntu/ quantal-updates/main python-lazr.restfulclient all 0.12.0-2ubuntu0.1 [54.5 kB]
Get:1108 http://archive.ubuntu.com/ubuntu/ quantal/main python-launchpadlib all 1.9.12-2 [50.4 kB]
Get:1109 http://archive.ubuntu.com/ubuntu/ quantal/universe python-libproxy all 0.4.7-0ubuntu6 [4,188 B]
Get:1110 http://archive.ubuntu.com/ubuntu/ quantal/main python-markupsafe amd64 0.15-1build1 [13.7 kB]
Get:1111 http://archive.ubuntu.com/ubuntu/ quantal/main python-mako all 0.7.1-1 [57.7 kB]
Get:1112 http://archive.ubuntu.com/ubuntu/ quantal/main python-numpy amd64 1:1.6.2-1ubuntu1 [1,861 kB]
Get:1113 http://archive.ubuntu.com/ubuntu/ quantal/universe python-opengl all 3.0.1-1 [510 kB]
Get:1114 http://archive.ubuntu.com/ubuntu/ quantal/main python-pam amd64 0.4.2-13ubuntu2 [11.9 kB]
Get:1115 http://archive.ubuntu.com/ubuntu/ quantal/universe python-pyatspi2 all 2.6.0+dfsg-0ubuntu1 [37.1 kB]
Get:1116 http://archive.ubuntu.com/ubuntu/ quantal/main python-sip amd64 4.13.3-2 [75.3 kB]
Get:1117 http://archive.ubuntu.com/ubuntu/ quantal/main python-qt4 amd64 4.9.3-4 [3,093 kB]
Get:1118 http://archive.ubuntu.com/ubuntu/ quantal/main python-qt4-dbus amd64 4.9.3-4 [15.9 kB]
Get:1119 http://archive.ubuntu.com/ubuntu/ quantal/main python-renderpm amd64 2.5-1.1build2 [37.6 kB]
Get:1120 http://archive.ubuntu.com/ubuntu/ quantal/main python-reportlab-accel amd64 2.5-1.1build2 [35.9 kB]
Get:1121 http://archive.ubuntu.com/ubuntu/ quantal/main python-serial all 2.5-3 [73.3 kB]
Get:1122 http://archive.ubuntu.com/ubuntu/ quantal/main python-smbc amd64 1.0.13-0ubuntu2 [17.1 kB]
Get:1123 http://archive.ubuntu.com/ubuntu/ quantal/universe python-support all 1.0.15 [26.7 kB]
Get:1124 http://archive.ubuntu.com/ubuntu/ quantal/universe python-virtkey amd64 0.61.0-0ubuntu1 [16.0 kB]
Get:1125 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe python-wxversion all 2.8.12.1-11ubuntu3.1 [17.5 kB]
Get:1126 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe python-wxgtk2.8 amd64 2.8.12.1-11ubuntu3.1 [5,555 kB]
Get:1127 http://archive.ubuntu.com/ubuntu/ quantal/main radeontool amd64 1.6.2-1.1build1 [75.2 kB]
Get:1128 http://archive.ubuntu.com/ubuntu/ quantal/main librarian0 amd64 0.8.1-5build1 [57.9 kB]
Get:1129 http://archive.ubuntu.com/ubuntu/ quantal/main xml-core all 0.13+nmu1 [23.0 kB]
Get:1130 http://archive.ubuntu.com/ubuntu/ quantal/main rarian-compat amd64 0.8.1-5build1 [102 kB]
Get:1131 http://archive.ubuntu.com/ubuntu/ quantal/main remmina-plugin-rdp amd64 1.0.0-1ubuntu8 [32.1 kB]
Get:1132 http://archive.ubuntu.com/ubuntu/ quantal/main remmina-plugin-vnc amd64 1.0.0-1ubuntu8 [20.7 kB]
Get:1133 http://archive.ubuntu.com/ubuntu/ quantal/main remmina amd64 1.0.0-1ubuntu8 [132 kB]
Get:1134 http://archive.ubuntu.com/ubuntu/ quantal/main remmina-common all 1.0.0-1ubuntu8 [47.0 kB]
Get:1135 http://archive.ubuntu.com/ubuntu/ quantal/main rfkill amd64 0.4-1ubuntu3 [9,054 B]
Get:1136 http://archive.ubuntu.com/ubuntu/ quantal/main sane-utils amd64 1.0.23-0ubuntu1 [188 kB]
Get:1137 http://archive.ubuntu.com/ubuntu/ quantal/main sgml-data all 2.0.8 [276 kB]
Get:1138 http://archive.ubuntu.com/ubuntu/ quantal/main simple-scan amd64 3.6.0-0ubuntu1 [119 kB]
Get:1139 http://archive.ubuntu.com/ubuntu/ quantal/main sni-qt amd64 0.2.6-0ubuntu1 [56.1 kB]
Get:1140 http://archive.ubuntu.com/ubuntu/ quantal/main ssh-askpass-gnome amd64 1:6.0p1-3ubuntu1 [16.1 kB]
Get:1141 http://archive.ubuntu.com/ubuntu/ quantal/main syslinux-common all 2:4.05+dfsg-6 [905 kB]
Get:1142 http://archive.ubuntu.com/ubuntu/ quantal/main syslinux amd64 2:4.05+dfsg-6 [55.6 kB]
Get:1143 http://archive.ubuntu.com/ubuntu/ quantal/main system-config-printer-common all 1.3.11+20120807-0ubuntu10 [39.9 kB]
Get:1144 http://archive.ubuntu.com/ubuntu/ quantal/main system-config-printer-gnome all 1.3.11+20120807-0ubuntu10 [178 kB]
Get:1145 http://archive.ubuntu.com/ubuntu/ quantal/main system-config-printer-udev amd64 1.3.11+20120807-0ubuntu10 [21.8 kB]
Get:1146 http://archive.ubuntu.com/ubuntu/ quantal/main tcl8.5 amd64 8.5.11-2ubuntu1 [1,098 kB]
Get:1147 http://archive.ubuntu.com/ubuntu/ quantal/main tcpd amd64 7.6.q-23 [27.7 kB]
Get:1148 http://archive.ubuntu.com/ubuntu/ quantal/main telepathy-haze amd64 0.6.0-1 [78.8 kB]
Get:1149 http://archive.ubuntu.com/ubuntu/ quantal/main telepathy-salut amd64 0.8.0-2 [422 kB]
Get:1150 http://archive.ubuntu.com/ubuntu/ quantal/main tk8.5 amd64 8.5.11-2 [1,009 kB]
Get:1151 http://archive.ubuntu.com/ubuntu/ quantal/main toshset amd64 1.76-4 [64.4 kB]
Get:1152 http://archive.ubuntu.com/ubuntu/ quantal/universe ttf-droid all 20111207+git-1ubuntu1 [1,732 B]
Get:1153 http://archive.ubuntu.com/ubuntu/ quantal/main ttf-ubuntu-font-family all 0.80-0ubuntu5 [1,994 kB]
Get:1154 http://archive.ubuntu.com/ubuntu/ quantal/universe ttf-unfonts-core all 1.0.3.is.1.0.2-080608-5ubuntu2 [1,290 B]
Get:1155 http://archive.ubuntu.com/ubuntu/ quantal-updates/main adium-theme-ubuntu all 0.3.3-0ubuntu0.1 [47.2 kB]
Get:1156 http://archive.ubuntu.com/ubuntu/ quantal/main ubuntu-artwork all 58 [13.4 kB]
Get:1157 http://archive.ubuntu.com/ubuntu/ quantal/main ubuntu-docs all 12.10.3 [1,434 kB]
Get:1158 http://archive.ubuntu.com/ubuntu/ quantal/universe ubuntu-wallpapers-precise all 0.35.2 [2,504 kB]
Get:1159 http://archive.ubuntu.com/ubuntu/ quantal/main udisks amd64 1.0.4-6 [241 kB]
Get:1160 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe unity-2d all 6.12.0-0ubuntu0.2 [9,276 B]
Get:1161 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe unity-2d-common all 6.12.0-0ubuntu0.2 [9,294 B]
Get:1162 http://archive.ubuntu.com/ubuntu/ quantal/main unity-asset-pool all 0.8.24-0ubuntu2 [66.0 kB]
Get:1163 http://archive.ubuntu.com/ubuntu/ quantal/main unixodbc amd64 2.2.14p2-5ubuntu4 [23.1 kB]
Get:1164 http://archive.ubuntu.com/ubuntu/ quantal-updates/main ure amd64 3.6.2~rc2-0ubuntu4 [2,573 kB]
Get:1165 http://archive.ubuntu.com/ubuntu/ quantal-updates/main uno-libs3 amd64 3.6.2~rc2-0ubuntu4 [643 kB]
Get:1166 http://archive.ubuntu.com/ubuntu/ quantal/multiverse unrar amd64 1:4.1.4-1 [108 kB]
Get:1167 http://archive.ubuntu.com/ubuntu/ quantal/main whois amd64 5.0.19 [28.2 kB]
Get:1168 http://archive.ubuntu.com/ubuntu/ quantal/main wireless-tools amd64 30~pre9-8ubuntu1 [118 kB]
Get:1169 http://archive.ubuntu.com/ubuntu/ quantal-updates/main x11-apps amd64 7.7~2ubuntu1.1 [762 kB]
Get:1170 http://archive.ubuntu.com/ubuntu/ quantal/main x11-session-utils amd64 7.6+2build1 [77.9 kB]
Get:1171 http://archive.ubuntu.com/ubuntu/ quantal/main x11-xfs-utils amd64 7.7~1 [27.0 kB]
Get:1172 http://archive.ubuntu.com/ubuntu/ quantal/main xdg-user-dirs amd64 0.14-0ubuntu4 [65.9 kB]
Get:1173 http://archive.ubuntu.com/ubuntu/ quantal/main xdg-user-dirs-gtk amd64 0.9-1ubuntu1 [11.4 kB]
Get:1174 http://archive.ubuntu.com/ubuntu/ quantal/main xfonts-utils amd64 1:7.7~1 [97.6 kB]
Get:1175 http://archive.ubuntu.com/ubuntu/ quantal/main xinit amd64 1.3.2-1 [18.8 kB]
Get:1176 http://archive.ubuntu.com/ubuntu/ quantal/main xinput amd64 1.6.0-1 [28.0 kB]
Get:1177 http://archive.ubuntu.com/ubuntu/ quantal-updates/main xserver-common all 2:1.13.0-0ubuntu6.5 [31.8 kB]
Get:1178 http://archive.ubuntu.com/ubuntu/ quantal/main xterm amd64 278-1ubuntu2 [584 kB]
Get:1179 http://archive.ubuntu.com/ubuntu/ quantal/main zenity amd64 3.4.0-2 [64.8 kB]
Get:1180 http://archive.ubuntu.com/ubuntu/ quantal/main zenity-common all 3.4.0-2 [222 kB]
Get:1181 http://archive.ubuntu.com/ubuntu/ quantal-updates/main aptdaemon-data all 0.45+bzr861-0ubuntu9.1.2 [162 kB]
Get:1182 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe compiz-plugins-main-default all 1:0.9.8.6-0ubuntu1 [3,486 B]
Get:1183 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe compizconfig-backend-gconf all 1:0.9.8.6-0ubuntu1 [9,448 B]
Get:1184 http://archive.ubuntu.com/ubuntu/ quantal-updates/main dh-apparmor all 2.8.0-0ubuntu5.1 [9,698 B]
Get:1185 http://archive.ubuntu.com/ubuntu/ quantal/universe ginn amd64 0.2.6-0ubuntu1 [17.2 kB]
Get:1186 http://archive.ubuntu.com/ubuntu/ quantal/main indicator-printers amd64 0.1.6-0ubuntu3 [29.8 kB]
Get:1187 http://archive.ubuntu.com/ubuntu/ quantal/main indicator-sound amd64 12.10.1-0ubuntu1 [108 kB]
Get:1188 http://archive.ubuntu.com/ubuntu/ quantal/main inputattach amd64 1:1.4.3-1 [20.1 kB]
Get:1189 http://archive.ubuntu.com/ubuntu/ quantal/main libcanberra-gtk3-module amd64 0.29-0ubuntu2 [11.0 kB]
Get:1190 http://archive.ubuntu.com/ubuntu/ quantal/main libgweather-common all 3.6.0-0ubuntu1 [586 kB]
Get:1191 http://archive.ubuntu.com/ubuntu/ quantal/universe libhdf4-0-alt amd64 4.2r4-13 [302 kB]
Get:1192 http://archive.ubuntu.com/ubuntu/ quantal/main liblircclient0 amd64 0.9.0-0ubuntu3 [16.2 kB]
Get:1193 http://archive.ubuntu.com/ubuntu/ quantal/main libpeas-common all 1.4.0-2ubuntu3 [13.8 kB]
Get:1194 http://archive.ubuntu.com/ubuntu/ quantal/universe proj-data amd64 4.7.0-2 [2,918 kB]
Get:1195 http://archive.ubuntu.com/ubuntu/ quantal/universe libproj0 amd64 4.7.0-2 [118 kB]
Get:1196 http://archive.ubuntu.com/ubuntu/ quantal/main protobuf-compiler amd64 2.4.1-3ubuntu1 [21.5 kB]
Get:1197 http://archive.ubuntu.com/ubuntu/ quantal/main libprotoc7 amd64 2.4.1-3ubuntu1 [264 kB]
Get:1198 http://archive.ubuntu.com/ubuntu/ quantal/universe libxerces-c28 amd64 2.8.0+deb1-3 [1,317 kB]
Get:1199 http://archive.ubuntu.com/ubuntu/ quantal/main setserial amd64 2.17-47 [40.8 kB]
Get:1200 http://archive.ubuntu.com/ubuntu/ quantal/universe lirc amd64 0.9.0-0ubuntu3 [623 kB]
Get:1201 http://archive.ubuntu.com/ubuntu/ quantal/main mobile-broadband-provider-info all 20120708-1 [45.4 kB]
Get:1202 http://archive.ubuntu.com/ubuntu/ quantal/main mscompress amd64 0.3-3.1build1 [9,342 B]
Get:1203 http://archive.ubuntu.com/ubuntu/ quantal/main python-piston-mini-client all 0.7.2+bzr57-0ubuntu2 [17.8 kB]
Get:1204 http://archive.ubuntu.com/ubuntu/ quantal/main oneconf all 0.2.9.1 [33.2 kB]
Get:1205 http://archive.ubuntu.com/ubuntu/ quantal/universe oss-compat amd64 2ubuntu1 [4,676 B]
Get:1206 http://archive.ubuntu.com/ubuntu/ quantal/universe proj-bin amd64 4.7.0-2 [40.6 kB]
Get:1207 http://archive.ubuntu.com/ubuntu/ quantal-updates/main pulseaudio-module-bluetooth amd64 1:2.1-0ubuntu4.1 [84.8 kB]
Get:1208 http://archive.ubuntu.com/ubuntu/ quantal/main python-defer all 1.0.6-2 [11.6 kB]
Get:1209 http://archive.ubuntu.com/ubuntu/ quantal/main python-dirspec all 4.0.0-0ubuntu1 [7,122 B]
Get:1210 http://archive.ubuntu.com/ubuntu/ quantal-updates/main sessioninstaller all 0.20+bzr131-0ubuntu2.1 [29.8 kB]
Get:1211 http://archive.ubuntu.com/ubuntu/ quantal/main speech-dispatcher amd64 0.7.1-6.1ubuntu2 [471 kB]
Get:1212 http://archive.ubuntu.com/ubuntu/ quantal/main ubuntuone-couch all 0.3.0-0ubuntu5 [7,718 B]
Get:1213 http://archive.ubuntu.com/ubuntu/ quantal/universe vdr amd64 1.7.28-1 [922 kB]
Get:1214 http://archive.ubuntu.com/ubuntu/ quantal/main xfonts-mathml all 6ubuntu1 [42.5 kB]
Fetched 553 MB in 4min 54s (1,873 kB/s)                                        
Extracting templates from packages: 100%
Preconfiguring packages ...
Bus error (core dumped)
keyboard-configuration failed to preconfigure, with exit status 135
Bus error (core dumped)
cups failed to preconfigure, with exit status 135
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
setserial failed to preconfigure, with exit status 135
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

---

### Post by Bashing-om on 2014-01-08
j88nl Well, That does not bode well.

Still trying to see the problem as the package manager sees it. We are looking for indications of what is corrupt.
What returns from:
```

sudo dpkg --configure -a

```

[INDENT][INDENT]look'n for a bit of direction here
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-08
It doesn't actually return anything. No error either. 

It prompts for a password and then finishes without spitting anything back.

---

### Post by Bashing-om on 2014-01-08
j88n; Yuk !

I hate shooting in the dark, The condition we are looking at is generally a bad control file for "some" installed package(s). The problem is which one(s).

While I stew on this some more, what returns from:
```

sudo dpkg -C

```

Gotta be a way - and -
[INDENT][INDENT]we will find it
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-08
Still no output... is there a log file I should look in?

---

### Post by Bashing-om on 2014-01-08
j88n;

A good thought, but I know of no log that would pertain to this situation.
Still in a quandry as to how to proceed. Consider some more on what to do, what to do.

[INDENT][INDENT]there are those times I just do not know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-01-08
j88n;

Still trying to isolate the cause.

Because of this advisement:
> 
The following packages have been kept back:

Try this and see what happens:
```

sudo apt-get dist-upgrade

```

still poke'n to see what prods

---

### Post by j88n on 2014-01-08
This is the first part... Is there a way to increase the buffer size of the terminal window? The beginning part gets cut off

```

sean@Sean-Monster:~$ sudo apt-get dist-upgrade
[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  cmap-adobe-japan2 gs-cjk-resource indicator-status-provider-mc5
  libatk-adaptor-schemas libebook-1.2-12 libedata-book-1.2-11
  libedataserverui-3.0-1 libevince3-3 libexttextcat0 libgdal1-1.7.0-grass
  libgnome-desktop-3-2 libgwibber-gtk2 libgwibber2
  libindicator-messages-status-provider1 libmetacity-private0
  liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 libunity-core-5.0-5
  python-aptdaemon.pkcompat ubuntu-sso-client-gtk ubuntuone-control-panel-qt
  xz-lzma
The following NEW packages will be installed:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-icons account-plugin-identica
  account-plugin-jabber account-plugin-salut account-plugin-twitter
  account-plugin-windows-live account-plugin-yahoo cpp-4.7 cracklib-runtime
  dconf-tools diffstat finger fonts-freefont-ttf freerdp-x11 g++-4.7 gcc-4.7
  gcc-4.7-base gcj-4.7-base gcj-4.7-jre-lib gcr gir1.2-accounts-1.0
  gir1.2-gdata-0.0 gir1.2-goa-1.0 gir1.2-messagingmenu-1.0 gir1.2-signon-1.0
  gir1.2-syncmenu-0.1 gnome-contacts gnome-control-center-signon
  gnome-mahjongg grass-doc hardening-includes hpijs icedtea-7-jre-jamvm
  libaccount-plugin-1.0-0 libaccounts-glib0 libaccounts-qt1 libapt-inst1.5
  libapt-pkg-perl libarchive-zip-perl libarmadillo3 libasprintf0c2
  libatk-adaptor-data libatk-bridge2.0-0 libblas3 libboost-date-time1.49.0
  libboost-thread1.49.0 libcamel-1.2-40 libclass-accessor-perl libclone-perl
  libclutter-1.0-0 libclutter-1.0-common libclutter-gst-1.0-0
  libclutter-gtk-1.0-0 libcmis-0.2-2 libcogl-common libcogl-pango0 libcogl9
  libcrack2 libdconf1 libdigest-hmac-perl libebackend-1.2-5 libebook-1.2-14
  libecal-1.2-15 libedata-book-1.2-15 libedata-cal-1.2-18
  libedataserver-1.2-17 libemail-valid-perl libevdocument3-4 libevview3-3
  libexiv2-12 libexttextcat-1.0-0 libfile-fcntllock-perl libfontembed1
  libgcj13 libgeos-3.3.3 libgeronimo-jta-1.1-spec-java libghc-resourcet-dev
  libghc-resourcet-prof libghc-void-dev libghc-void-prof libglew1.8
  libglewmx1.8 libgnome-bluetooth11 libgnome-desktop-3-4 libgnomekbd8 libgusb2
  libgweather-3-1 libgwibber-gtk3 libgwibber3 libgxps2 libimobiledevice3
  libio-pty-perl libio-string-perl libipc-run-perl libitm1 libjbig0 libkms1
  libkpathsea6 liblapack3 liblinear-tools liblinear1 libmagickcore5
  libmagickcore5-extra libmagickwand5 libmessaging-menu0 libmetacity-private0a
  libmusicbrainz5-0 libmx-1.0-2 libmx-bin libmx-common libnatpmp1
  libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libnss-winbind
  libnuma1 libnux-3.0-0 libnux-3.0-common libopus0 libp11-kit-gnome-keyring
  libpam-freerdp libparse-debianchangelog-perl libpoppler28 libprocps0
  libpwquality1 libpython3.2 libqjson0 libqpdf8 libreoffice-pdfimport
  librhythmbox-core6 libsecret-1-0 libsecret-common libservlet3.0-java
  libsignon-extension1 libsignon-glib1 libsignon-plugins-common1 libsignon-qt1
  libstdc++6-4.7-dev libsub-name-perl libsync-menu1 libtiff5 libudisks2-0
  libunity-core-6.0-5 libunity-protocol-private0 libunity-webapps0 libusbmuxd2
  libwhoopsie0 libx264-123 libyajl2 lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure lintian mcp-account-manager-uoa nmap
  openjdk-7-jre-headless openjdk-7-jre-lib overlay-scrollbar-gtk2
  overlay-scrollbar-gtk3 packagekit-backend-aptcc patchutils python-lxml
  python-six python3 python3-apport python3-apt python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi
  python3-cairo python3-crypto python3-dbus python3-defer python3-distupgrade
  python3-gdbm python3-gi python3-gi-cairo python3-httplib2 python3-louis
  python3-lxml python3-minimal python3-oauthlib python3-pkg-resources
  python3-problem-report python3-pyatspi2 python3-pycurl
  python3-software-properties python3-update-manager python3-virtkey
  python3-xkit python3.2 python3.2-minimal qpdf remote-login-service
  session-migration signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signond thin-client-config-agent
  ubuntu-drivers-common ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-wallpapers-quantal udisks2
  unity-lens-gwibber unity-lens-photos unity-lens-shopping unity-scope-gdocs
  unity-webapps-service
The following packages have been kept back:
  gdal-bin gnome-orca grass xorg
The following packages will be upgraded:
  accountsservice acl acpi-support acpid activity-log-manager-common
  activity-log-manager-control-center adduser adium-theme-ubuntu aisleriot
  alsa-base alsa-utils anacron antlr apg app-install-data
  app-install-data-partner apparmor appmenu-gtk appmenu-gtk3 appmenu-qt apport
  apport-gtk apport-symptoms apt apt-transport-https apt-utils
  apt-xapian-index aptdaemon aptdaemon-data apturl apturl-common aspell
  aspell-en at at-spi2-core autoconf autotools-dev avahi-autoipd avahi-daemon
  avahi-utils bamfdaemon baobab base-files base-passwd bash bash-completion bc
  bind9-host binfmt-support binutils bluez bluez-alsa bluez-cups
  bluez-gstreamer brasero brasero-cdrkit brasero-common brltty bsdmainutils
  bsdutils build-essential busybox-initramfs busybox-static bzip2
  ca-certificates ca-certificates-java cabextract camlp4 checkbox checkbox-qt
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg colord
  command-not-found command-not-found-data compiz compiz-core compiz-gnome
  compiz-plugins-default compiz-plugins-main-default
  compizconfig-backend-gconf console-setup consolekit coreutils cpio cpp
  cpp-4.6 cron cryptsetup-bin cups cups-bsd cups-client cups-common
  cups-filters cups-ppdc curl dash dbus dbus-x11 dc dconf-gsettings-backend
  dconf-service debconf debconf-i18n debhelper debianutils
  default-jre-headless deja-dup desktop-file-utils dh-apparmor
  dictionaries-common diffutils dmidecode dmsetup dnsmasq-base dnsutils
  doc-base dosfstools dpkg dpkg-dev duplicity dvd+rw-tools e2fslibs e2fsprogs
  ed eject empathy empathy-common enchant eog espeak espeak-data evince
  evince-common evolution-data-server evolution-data-server-common fakeroot
  file file-roller findutils firefox firefox-gnome-support firefox-locale-en
  flashplugin-installer folks-common fontconfig fontconfig-config fonts-droid
  fonts-horai-umefont fonts-kacst fonts-kacst-one fonts-liberation fonts-nanum
  fonts-opensymbol fonts-thai-tlwg fonts-tlwg-garuda fonts-tlwg-kinnari
  fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa
  fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo
  fonts-tlwg-umpush fonts-tlwg-waree fonts-unfonts-core
  foomatic-db-compressed-ppds foomatic-db-engine foomatic-filters freeglut3
  ftp fuse g++ g++-4.6 gcalctool gcc gcc-4.6 gcc-4.6-base gcj-4.6-base
  gcj-4.6-jre-lib gconf-service gconf-service-backend gconf2 gconf2-common gdb
  gedit gedit-common genisoimage geoclue geoclue-ubuntu-geoip geoip-database
  gettext gettext-base ghc ghc-prof ghostscript ghostscript-cups ghostscript-x
  ginn gir1.2-appindicator3-0.1 gir1.2-atk-1.0 gir1.2-atspi-2.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk-0.4 gir1.2-dee-1.0
  gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gmenu-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gnomekeyring-1.0
  gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 gir1.2-gtk-2.0
  gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-indicate-0.7
  gir1.2-javascriptcoregtk-3.0 gir1.2-launchpad-integration-3.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-rb-3.0
  gir1.2-rsvg-2.0 gir1.2-soup-2.4 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0
  gir1.2-ubuntuoneui-3.0 gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0
  gir1.2-wnck-3.0 gksu glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-bluetooth
  gnome-control-center gnome-control-center-data gnome-desktop3-data
  gnome-disk-utility gnome-font-viewer gnome-games-data gnome-icon-theme
  gnome-icon-theme-symbolic gnome-keyring gnome-media gnome-menus
  gnome-nettool gnome-online-accounts gnome-power-manager gnome-screensaver
  gnome-screenshot gnome-session gnome-session-bin gnome-session-canberra
  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log
  gnome-system-monitor gnome-terminal gnome-terminal-data gnome-user-guide
  gnome-user-share gnomine gnupg gpgv grep groff-base growisofs grub-common
  grub-ieee1275-bin grub-pc grub-pc-bin grub2-common gsettings-desktop-schemas
  gstreamer0.10-alsa gstreamer0.10-ffmpeg gstreamer0.10-gconf
  gstreamer0.10-nice gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk3-engines-unico
  gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  gzip hdparm hostname hplip hplip-data html2text humanity-icon-theme hwdata
  hyphen-en-us ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-pinyin-db-android
  ibus-table icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx
  icedtea-netx-common icoutils ifupdown im-switch imagemagick
  imagemagick-common indicator-application indicator-appmenu
  indicator-datetime indicator-messages indicator-power indicator-printers
  indicator-session indicator-sound info initramfs-tools initramfs-tools-bin
  initscripts inputattach insserv install-info intel-gpu-tools iproute
  iptables iputils-arping iputils-ping iputils-tracepath irqbalance
  isc-dhcp-client isc-dhcp-common iso-codes ivy java-common jockey-common
  jockey-gtk junit4 kbd kerneloops-daemon keyboard-configuration klibc-utils
  krb5-locales landscape-client-ui-install language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector-common language-selector-gnome launchpad-integration ledit
  less libaa1 libaccountsservice0 libacl1 libalgorithm-diff-xs-perl
  libantlr-java libapache-pom-java libappindicator1 libappindicator3-1
  libapt-pkg4.12 libarchive12 libart-2.0-2 libasm3-java libasn1-8-heimdal
  libasound2 libasound2-plugins libaspell15 libasyncns0 libatasmart4
  libatk-adaptor libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0
  libatk1.0-data libatk1.0-dev libatkmm-1.6-1 libatspi2.0-0 libattr1 libaudio2
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core7
  libavahi-glib1 libavahi-gobject0 libavahi-ui-gtk3-0 libavc1394-0
  libavcodec53 libavformat53 libavutil51 libbamf0 libbamf3-0 libbind9-80
  libbiojava1.7-java libblas3gf libblkid1 libbluetooth3 libbrasero-media3-1
  libbrlapi0.5 libbsd-dev libbsd0 libbsf-java libburn4 libbytecode-java
  libbz2-1.0 libc-bin libc-dev-bin libc6 libc6-dev libcaca0 libcairo-gobject2
  libcairo-perl libcairo-script-interpreter2 libcairo2 libcairo2-dev
  libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcap-ng0 libcap2
  libcap2-bin libcdaudio1 libcdio-cdda1 libcdio-paranoia1 libcdio13
  libcdparanoia0 libcdt4 libck-connector0 libcolord1 libcomerr2
  libcommons-cli-java libcommons-collections-java libcommons-collections3-java
  libcommons-dbcp-java libcommons-lang-java libcommons-logging-java
  libcommons-parent-java libcommons-pool-java libcompizconfig0 libcroco3
  libcryptsetup4 libcups2 libcupscgi1 libcupsfilters1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libcurl3-nss libdaemon0
  libdap11 libdapclient3 libdatrie1 libdb5.1 libdbus-1-3 libdbus-glib-1-2
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdbusmenu-qt2
  libdc1394-22 libdconf-dbus-1-0 libdecoration0 libdee-1.0-4
  libdevmapper-event1.02.1 libdevmapper1.02.1 libdirac-encoder0
  libdirectfb-1.2-9 libdiscid0 libdjvulibre-text libdjvulibre21
  libdmapsharing-3.0-2 libdns81 libdotconf1.0 libdpkg-perl libdrm-intel1
  libdrm-nouveau1a libdrm-nouveau2 libdrm-radeon1 libdrm2 libdv4 libdvdnav4
  libdvdread4 libedit2 libelf1 libenca0 libenchant1c2a libencode-locale-perl
  libept1.4.12 libespeak1 libevent-2.0-5 libexempi3 libexif12 libexpat1
  libexpat1-dev libexttextcat-data libfaad2 libfarstream-0.1-0 libffi-dev
  libffi6 libfftw3-3 libfile-listing-perl libfile-mimeinfo-perl
  libfindlib-ocaml libfindlib-ocaml-dev libflac8 libflite1 libfolks-eds25
  libfolks-telepathy25 libfolks25 libfontconfig1 libfontconfig1-dev
  libfontenc1 libframe6 libfreerdp-plugins-standard libfreerdp1 libfreetype6
  libfreetype6-dev libfreexl1 libfribidi0 libfs6 libftdi1 libfuse2 libgail-3-0
  libgail-common libgail18 libgcc1 libgcj-bc libgcj-common libgcj12 libgck-1-0
  libgconf-2-4 libgconf2-4 libgcr-3-1 libgcr-3-common libgcrypt11 libgd2-xpm
  libgdata-common libgdata13 libgdbm3 libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-common libgdk-pixbuf2.0-dev libgee2 libgeis1 libgeoclue0
  libgeoip1 libgeos-c1 libgettextpo0 libgexiv2-1 libgfortran3
  libghc-base-unicode-symbols-dev libghc-base-unicode-symbols-prof
  libghc-bindings-dsl-dev libghc-cairo-dev libghc-cairo-prof libghc-cereal-dev
  libghc-cereal-prof libghc-conduit-dev libghc-conduit-prof
  libghc-configfile-dev libghc-configfile-prof libghc-crypto-api-dev
  libghc-crypto-api-prof libghc-data-default-dev libghc-data-default-prof
  libghc-digest-dev libghc-digest-prof libghc-dlist-dev libghc-dlist-prof
  libghc-dpkg-dev libghc-dpkg-prof libghc-entropy-dev libghc-entropy-prof
  libghc-event-list-dev libghc-event-list-prof libghc-explicit-exception-dev
  libghc-explicit-exception-prof libghc-glib-dev libghc-glib-prof
  libghc-hashable-dev libghc-hashable-prof libghc-haskell-src-dev
  libghc-haskell-src-prof libghc-hipmunk-dev libghc-hipmunk-prof
  libghc-hsemail-dev libghc-hsemail-prof libghc-hslogger-dev
  libghc-hslogger-prof libghc-hunit-dev libghc-hunit-prof
  libghc-lambdabot-utils-dev libghc-lambdabot-utils-prof libghc-largeword-dev
  libghc-largeword-prof libghc-lifted-base-dev libghc-lifted-base-prof
  libghc-logict-dev libghc-logict-prof libghc-midi-dev libghc-midi-prof
  libghc-missingh-dev libghc-missingh-prof libghc-monad-control-dev
  libghc-monad-control-prof libghc-monad-loops-dev libghc-monad-loops-prof
  libghc-monoid-transformer-dev libghc-monoid-transformer-prof libghc-mtl-dev
  libghc-mtl-prof libghc-network-dev libghc-network-prof
  libghc-non-negative-dev libghc-non-negative-prof libghc-numtype-dev
  libghc-numtype-prof libghc-parallel-dev libghc-parallel-prof
  libghc-parsec3-dev libghc-parsec3-prof libghc-polyparse-dev
  libghc-polyparse-prof libghc-pool-conduit-dev libghc-pool-conduit-prof
  libghc-primitive-dev libghc-primitive-prof libghc-puremd5-dev
  libghc-puremd5-prof libghc-quickcheck2-dev libghc-quickcheck2-prof
  libghc-random-dev libghc-random-prof libghc-ranges-dev libghc-ranges-prof
  libghc-regex-base-dev libghc-regex-base-prof libghc-regex-compat-dev
  libghc-regex-compat-prof libghc-regex-pcre-dev libghc-regex-pcre-prof
  libghc-regex-posix-dev libghc-regex-posix-prof libghc-regex-tdfa-dev
  libghc-regex-tdfa-prof libghc-resource-pool-dev libghc-resource-pool-prof
  libghc-semigroups-dev libghc-semigroups-prof libghc-socks-dev
  libghc-socks-prof libghc-split-dev libghc-split-prof libghc-statevar-dev
  libghc-statevar-prof libghc-stm-dev libghc-stm-prof libghc-svgcairo-dev
  libghc-svgcairo-prof libghc-syb-dev libghc-syb-prof libghc-tagged-dev
  libghc-tagged-prof libghc-tagsoup-dev libghc-tagsoup-prof libghc-text-dev
  libghc-text-prof libghc-transformers-base-dev libghc-transformers-base-prof
  libghc-transformers-dev libghc-transformers-prof libghc-unixutils-dev
  libghc-unixutils-prof libghc-utf8-string-dev libghc-utf8-string-prof
  libghc-utility-ht-dev libghc-utility-ht-prof libghc-vector-dev
  libghc-vector-prof libghc-zip-archive-dev libghc-zip-archive-prof
  libghc-zlib-dev libghc-zlib-prof libgif4 libgirepository-1.0-1 libgksu2-0
  libglib-perl libglib2.0-0 libglib2.0-bin libglib2.0-data libglib2.0-dev
  libglibmm-2.4-1c2a libglu1-mesa libgmime-2.6-0 libgmp-dev libgmp10
  libgmpxx4ldbl libgnome-control-center1 libgnome-keyring-common
  libgnome-keyring0 libgnome-media-profiles-3.0-0 libgnome-menu-3-0
  libgnome-menu2 libgnome2-common libgnomekbd-common libgnutls26 libgoa-1.0-0
  libgoa-1.0-common libgomp1 libgpg-error0 libgpgme11 libgphoto2-2
  libgphoto2-l10n libgphoto2-port0 libgpm2 libgpod-common libgpod4 libgrail5
  libgraph4 libgrip0 libgs9 libgs9-common libgsm1 libgssapi-krb5-2
  libgssapi3-heimdal libgssdp-1.0-3 libgstreamer-plugins-bad0.10-0
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtk2.0-dev libgtkmm-3.0-1 libgtksourceview-3.0-0
  libgtksourceview-3.0-common libgtkspell-3-0 libgtop2-7 libgtop2-common
  libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-igd-1.0-4
  libgutenprint2 libgvc5 libgweather-common libhamcrest-java
  libhcrypto4-heimdal libhdf4-0-alt libheimbase1-heimdal libheimntlm0-heimdal
  libhpmud0 libhsqldb-java libhtml-form-perl libhtml-parser-perl
  libhtml-tree-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhunspell-1.3-0 libhx509-5-heimdal libhyphen0 libibus-1.0-0 libical0
  libice-dev libice6 libicu48 libidn11 libido3-0.1-0 libiec61883-0
  libieee1284-3 libijs-0.35 libilmbase6 libindicate-gtk3 libindicate5
  libindicator3-7 libindicator7 libio-socket-ssl-perl libirrlicht1.7a
  libirrlicht1.7a-dbg libisc83 libisccc80 libisccfg82 libisofs6 libiw30
  libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig2dec0
  libjline-java libjpeg-turbo8 libjs-jquery libjson-glib-1.0-0 libjson0
  libjte1 libk5crypto3 libkeyutils1 libklibc libkrb5-26-heimdal libkrb5-3
  libkrb5support0 liblapack3gf liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common liblcms1 libldap-2.4-2
  liblightdm-gobject-1-0 liblircclient0 liblocale-gettext-perl liblockfile-bin
  liblockfile1 liblouis-data liblouis2 liblqr-1-0 libltdl7 liblua5.1-0
  liblvm2app2.2 liblwp-mediatypes-perl liblwp-protocol-https-perl liblwres80
  liblzma5 libmagic1 libmailtools-perl libmeanwhile1 libmhash2 libmikmod2
  libminiupnpc8 libmission-control-plugins0 libmms0 libmng1 libmodplug1
  libmount1 libmp3lame0 libmpc2 libmpeg2-4 libmpfr4 libmpg123-0 libmtdev1
  libmtp-common libmtp-runtime libmtp9 libmysqlclient18 libmythes-1.2-0
  libnautilus-extension1a libncurses5 libncurses5-dev libncursesw5
  libneon27-gnutls libnet-http-perl libnet-ssleay-perl libnetfilter-conntrack3
  libnetpbm10 libnettle4 libnewt0.52 libnfnetlink0 libnice10 libnih-dbus1
  libnih1 libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1
  libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4
  libnspr4 libnspr4-0d libnss-mdns libnss3 libnss3-1d liboauth0 libodbc1
  libofa0 libogg0 libogre-1.7.4 libogre-1.7.4-dbg libopenal-data libopenal1
  libopencc1 libopencore-amrnb0 libopencore-amrwb0 libopenexr6 libopenjpeg2
  libopenobex1 liborc-0.4-0 libosmesa6 libp11-kit0 libpackagekit-glib2-14
  libpam-cap libpam-ck-connector libpam-gnome-keyring libpam-modules
  libpam-modules-bin libpam-runtime libpam-winbind libpam0g libpango-perl
  libpango1.0-0 libpango1.0-dev libpangomm-1.4-1 libpaper-utils libpaper1
  libparted0debian1 libpathplan4 libpcap0.8 libpci3 libpciaccess0 libpcre3
  libpcre3-dev libpcrecpp0 libpcsclite1 libpeas-1.0-0 libpeas-common
  libperl5.14 libpipeline1 libpixman-1-0 libpixman-1-dev libplist1
  libplymouth2 libpng12-0 libpng12-dev libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpoppler-glib8 libpopt0
  libportaudio2 libpostproc52 libpq5 libproj0 libprotobuf7 libprotoc7
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpth20 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin
  libpurple0 libpython2.7 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml
  libqt4-xmlpatterns libqtassistantclient4 libqtbamf1 libqtcore4 libqtgui4
  libqtwebkit4 libquadmath0 libquvi-scripts libquvi7 libraptor2-0 librarian0
  librasqal3 libraw1394-11 libraw5 librdf0 libreadline6 libregexp-java
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-style-tango libreoffice-writer
  librest-0.7-0 libroken18-heimdal librsvg2-2 librsvg2-bin librsvg2-common
  librsvg2-dev librsync1 librtmp0 libsamplerate0 libsane libsane-common
  libsane-hpaio libsasl2-2 libsasl2-modules libschroedinger-1.0-0
  libsdl-mixer1.2 libsdl1.2debian libselinux1 libsensors4 libservlet2.5-java
  libsgutils2-2 libshout3 libsigc++-2.0-0c2a libslang2 libslp1 libslv2-9
  libsm-dev libsm6 libsmbclient libsndfile1 libsnmp-base libsnmp15
  libsocket6-perl libsonic0 libsoundtouch0 libsoup-gnome2.4-1 libsoup2.4-1
  libspandsp2 libspatialite3 libspectre1 libspeechd2 libspeex1 libspeexdsp1
  libsqlite3-0 libss2 libssh-4 libssl1.0.0 libstartup-notification0 libstdc++6
  libstdc++6-4.6-dev libswscale2 libsyncdaemon-1.0-1 libsysfs2 libt1-5
  libtag1-vanilla libtag1c2a libtalloc2 libtasn1-3 libtdb1
  libtelepathy-farstream2 libtelepathy-glib0 libtelepathy-logger2
  libtext-charwidth-perl libtext-iconv-perl libthai-data libthai0 libtheora0
  libtiff4 libtimezonemap1 libtinfo-dev libtinfo5 libtotem-plparser17
  libtotem0 libts-0.0-0 libubuntuoneui-3.0-1 libudev0 libunique-3.0-0
  libunistring0 libunity-2d-private0 libunity-misc4 libunity9 libupower-glib1
  liburi-perl libusb-0.1-4 libusb-1.0-0 libutempter0 libuuid-perl libuuid1
  libv4l-0 libv4lconvert0 libva1 libvisual-0.4-0 libvisual-0.4-plugins
  libvncserver0 libvo-aacenc0 libvo-amrwbenc0 libvorbis0a libvorbisenc2
  libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common libvte-common
  libvte9 libwacom-common libwacom2 libwavpack1 libwbclient0
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwildmidi-config libwildmidi1
  libwind0-heimdal libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common
  libwnck-common libwnck22 libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0
  libwww-perl libwxbase2.8-0 libwxgtk2.8-0 libx11-6 libx11-data libx11-dev
  libx11-doc libx11-xcb1 libx86-1 libxapian22 libxau-dev libxau6 libxaw7
  libxcb-dri2-0 libxcb-glx0 libxcb-render0 libxcb-render0-dev libxcb-shape0
  libxcb-shm0 libxcb-shm0-dev libxcb-util0 libxcb1 libxcb1-dev
  libxcomposite-dev libxcomposite1 libxcursor-dev libxcursor1 libxdamage-dev
  libxdamage1 libxdmcp-dev libxdmcp6 libxerces-c28 libxerces2-java libxext-dev
  libxext6 libxfixes-dev libxfixes3 libxfont1 libxft-dev libxft2 libxi-dev
  libxi6 libxinerama-dev libxinerama1 libxkbfile1 libxklavier16
  libxml-commons-external-java libxml-commons-resolver1.1-java libxml2
  libxml2-utils libxmu6 libxmuu1 libxp6 libxpm4 libxpp3-java libxrandr-dev
  libxrandr2 libxrender-dev libxrender1 libxres1 libxslt1.1 libxss1
  libxstream-java libxt6 libxtst6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1
  libxxf86vm1 libyaml-tiny-perl libyelp0 libzbar0 libzephyr4 libzvbi-common
  libzvbi0 light-themes lightdm linux-firmware linux-libc-dev linux-sound-base
  lirc lockfile-progs login logrotate lsb-base lsb-release lshw lsof ltrace m4
  mahjongg make makedev man-db manpages manpages-dev media-player-info
  memtest86+ metacity metacity-common mime-support mlocate
  mobile-broadband-provider-info modemmanager module-init-tools mount mountall
  mousetweaks mscompress mtools mtr-tiny multiarch-support mysql-common nano
  nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy
  nautilus-share ncurses-base ncurses-bin net-tools netbase netcat-openbsd
  netpbm network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome notify-osd ntfs-3g ntpdate nux-tools
  nvidia-common obex-data-server obexd-client ocaml-base-nox ocaml-findlib
  ocaml-interp ocaml-nox odbcinst odbcinst1debian2 onboard oneconf
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openprinting-ppds
  openssh-client openssl os-prober oss-compat overlay-scrollbar parted passwd
  patch pciutils pcmciautils perl perl-base perl-modules pkg-config plymouth
  plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
  pm-utils policykit-1 policykit-1-gnome policykit-desktop-privileges
  poppler-data poppler-utils powermgmt-base ppp pptp-linux
  printer-driver-c2esp printer-driver-foo2zjs printer-driver-gutenprint
  printer-driver-hpcups printer-driver-hpijs printer-driver-min12xxw
  printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch
  printer-driver-pxljr printer-driver-splix procps proj-bin proj-data
  protobuf-compiler psmisc pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python
  python-appindicator python-apport python-apt python-apt-common
  python-aptdaemon python-aptdaemon.gtk3widgets python-cairo python-crypto
  python-cups python-cupshelpers python-dateutil python-dbus python-dbus-dev
  python-debian python-debtagshw python-defer python-dirspec
  python-egenix-mxdatetime python-egenix-mxtools python-gconf python-gdbm
  python-gi python-gi-cairo python-gnomekeyring python-gobject
  python-gobject-2 python-gst0.10 python-gtk2 python-httplib2 python-ibus
  python-imaging python-keyring python-launchpadlib python-lazr.restfulclient
  python-libproxy python-libxml2 python-mako python-markupsafe python-minimal
  python-notify python-numpy python-opengl python-openssl python-packagekit
  python-pam python-pexpect python-piston-mini-client python-pkg-resources
  python-problem-report python-protobuf python-pyatspi2 python-pycurl
  python-pyinotify python-qt4 python-qt4-dbus python-renderpm python-reportlab
  python-reportlab-accel python-serial python-simplejson python-sip
  python-smbc python-software-properties python-support python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web
  python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno
  python-virtkey python-wxgtk2.8 python-wxversion python-xapian python-xdg
  python-xkit python-zeitgeist python-zope.interface python2.7
  python2.7-minimal qdbus qt-at-spi radeontool rarian-compat readline-common
  remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc resolvconf
  rfkill rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rsync rsyslog rtkit
  samba-common samba-common-bin sane-utils seahorse sed sensible-utils
  sessioninstaller setserial sgml-base sgml-data shared-mime-info shotwell
  simple-scan smbclient sni-qt software-center
  software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk speech-dispatcher ssh-askpass-gnome ssl-cert strace
  sudo synaptic syslinux syslinux-common system-config-printer-common
  system-config-printer-gnome system-config-printer-udev sysv-rc
  sysvinit-utils tcl8.5 tcpd tcpdump telepathy-gabble telepathy-haze
  telepathy-idle telepathy-indicator telepathy-logger
  telepathy-mission-control-5 telepathy-salut telnet thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us time tk8.5 toshset totem totem-common totem-mozilla
  totem-plugins transmission-common transmission-gtk tsconf ttf-droid
  ttf-freefont ttf-ubuntu-font-family ttf-umefont ttf-unfonts-core tzdata
  tzdata-java ubuntu-artwork ubuntu-docs ubuntu-keyring ubuntu-minimal
  ubuntu-mono ubuntu-sso-client ubuntu-sso-client-qt ubuntu-standard
  ubuntu-system-service ubuntu-wallpapers ubuntu-wallpapers-precise
  ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel
  ubuntuone-couch ucf udev udisks ufw unattended-upgrades unity unity-2d
  unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
  unity-asset-pool unity-common unity-greeter unity-lens-applications
  unity-lens-files unity-lens-music unity-lens-video unity-scope-musicstores
  unity-scope-video-remote unity-services unixodbc uno-libs3 unrar unzip
  update-inetd update-manager update-manager-core update-notifier
  update-notifier-common upower upstart ure ureadahead usb-creator-common
  usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd usbutils
  util-linux uuid-runtime vdr vim-common vim-tiny vino wget whiptail whois
  whoopsie winbind wireless-tools wodim wpasupplicant x11-apps x11-common
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-xext-dev xauth xdg-user-dirs xdg-user-dirs-gtk xdiagnose
  xfonts-mathml xfonts-utils xinit xinput xkb-data xml-core xpdf
  xserver-common xterm xtrans-dev xul-ext-ubufox xz-utils yelp yelp-xsl
  zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zip zlib1g
  zlib1g-dev
1625 upgraded, 215 newly installed, 22 to remove and 4 not upgraded.
Need to get 577 MB/1,129 MB of archives.
After this operation, 328 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by j88n on 2014-01-08
Second Part (as much as I could grab)

```

Get:371 http://archive.ubuntu.com/ubuntu/ quantal/main g++-4.7 amd64 4.7.2-2ubuntu1 [7,966 kB]
Get:372 http://archive.ubuntu.com/ubuntu/ quantal/main g++ amd64 4:4.7.2-1ubuntu2 [1,448 B]
Get:373 http://archive.ubuntu.com/ubuntu/ quantal/main dpkg-dev all 1.16.7ubuntu6 [595 kB]
Get:374 http://archive.ubuntu.com/ubuntu/ quantal/main libdpkg-perl all 1.16.7ubuntu6 [188 kB]
Get:375 http://archive.ubuntu.com/ubuntu/ quantal/main python3-lxml amd64 2.3.5-1 [658 kB]
Get:376 http://archive.ubuntu.com/ubuntu/ quantal-updates/main checkbox amd64 0.14.10 [1,331 kB]
Get:377 http://archive.ubuntu.com/ubuntu/ quantal-updates/main checkbox-qt amd64 0.14.10 [75.5 kB]
Get:378 http://archive.ubuntu.com/ubuntu/ quantal/main cracklib-runtime amd64 2.8.19-1 [170 kB]
Get:379 http://archive.ubuntu.com/ubuntu/ quantal/main debhelper all 9.20120608ubuntu1 [623 kB]
Get:380 http://archive.ubuntu.com/ubuntu/ quantal/main diffstat amd64 1.55-3 [23.5 kB]
Get:381 http://archive.ubuntu.com/ubuntu/ quantal/universe finger amd64 0.17-15 [17.3 kB]
Get:382 http://archive.ubuntu.com/ubuntu/ quantal/main freerdp-x11 amd64 1.0.1-1ubuntu7 [49.1 kB]
Get:383 http://archive.ubuntu.com/ubuntu/ quantal/main gcj-4.7-jre-lib all 4.7.2-1ubuntu1 [10.5 MB]
Get:384 http://archive.ubuntu.com/ubuntu/ quantal/main gir1.2-gdata-0.0 amd64 0.13.2-0ubuntu1 [40.5 kB]
Get:385 http://archive.ubuntu.com/ubuntu/ quantal/main gir1.2-syncmenu-0.1 amd64 12.10.4-0ubuntu1 [2,746 B]
Get:386 http://archive.ubuntu.com/ubuntu/ quantal-updates/main totem-mozilla amd64 3.4.3-0ubuntu5 [139 kB]
Get:387 http://archive.ubuntu.com/ubuntu/ quantal-updates/main totem-plugins amd64 3.4.3-0ubuntu5 [164 kB]
Get:388 http://archive.ubuntu.com/ubuntu/ quantal-updates/main totem amd64 3.4.3-0ubuntu5 [220 kB]
Get:389 http://archive.ubuntu.com/ubuntu/ quantal-updates/main gir1.2-totem-1.0 amd64 3.4.3-0ubuntu5 [7,006 B]
Get:390 http://archive.ubuntu.com/ubuntu/ quantal-updates/main libtotem0 amd64 3.4.3-0ubuntu5 [217 kB]
Get:391 http://archive.ubuntu.com/ubuntu/ quantal-updates/main totem-common all 3.4.3-0ubuntu5 [232 kB]
Get:392 http://archive.ubuntu.com/ubuntu/ quantal/main gnome-contacts amd64 3.6.0-0ubuntu2 [274 kB]
Get:393 http://archive.ubuntu.com/ubuntu/ quantal/main gnome-control-center-signon amd64 0.0.18-0ubuntu1 [99.5 kB]
Get:394 http://archive.ubuntu.com/ubuntu/ quantal/main liblapack3gf all 3.4.1-6 [3,444 B]
Get:395 http://archive.ubuntu.com/ubuntu/ quantal/main libblas3gf all 1.2.20110419-5 [2,920 B]
Get:396 http://archive.ubuntu.com/ubuntu/ quantal/main libblas3 amd64 1.2.20110419-5 [287 kB]
Get:397 http://archive.ubuntu.com/ubuntu/ quantal/main liblinear1 amd64 1.8+dfsg-1ubuntu1 [33.4 kB]
Get:398 http://archive.ubuntu.com/ubuntu/ quantal/main nmap amd64 6.00-0.1 [4,344 kB]
Get:399 http://archive.ubuntu.com/ubuntu/ quantal/universe gnome-nettool amd64 3.2.0-1 [111 kB]
Get:400 http://archive.ubuntu.com/ubuntu/ quantal-updates/main gnome-system-log amd64 3.6.0-0ubuntu1.1 [112 kB]
Get:401 http://archive.ubuntu.com/ubuntu/ quantal/main gnome-user-share amd64 3.0.4-0ubuntu1 [95.7 kB]
Get:402 http://archive.ubuntu.com/ubuntu/ quantal/universe grass-doc all 6.4.2-2build1 [6,486 kB]
Get:403 http://archive.ubuntu.com/ubuntu/ quantal/main grub-pc amd64 2.00-7ubuntu11 [169 kB]
Get:404 http://archive.ubuntu.com/ubuntu/ quantal/main grub-pc-bin amd64 2.00-7ubuntu11 [800 kB]
Get:405 http://archive.ubuntu.com/ubuntu/ quantal/main grub2-common amd64 2.00-7ubuntu11 [116 kB]
Get:406 http://archive.ubuntu.com/ubuntu/ quantal/universe grub-ieee1275-bin amd64 2.00-7ubuntu11 [517 kB]
Get:407 http://archive.ubuntu.com/ubuntu/ quantal/main grub-common amd64 2.00-7ubuntu11 [1,280 kB]
Get:408 http://archive.ubuntu.com/ubuntu/ quantal/universe gstreamer0.10-plugins-ugly amd64 0.10.19-2 [358 kB]
Get:409 http://archive.ubuntu.com/ubuntu/ quantal-updates/main gwibber-service-facebook all 3.6.0-0ubuntu1.1 [6,144 B]
Get:410 http://archive.ubuntu.com/ubuntu/ quantal-updates/main gwibber-service-identica all 3.6.0-0ubuntu1.1 [6,660 B]
Get:411 http://archive.ubuntu.com/ubuntu/ quantal-updates/main gwibber-service-twitter all 3.6.0-0ubuntu1.1 [7,994 B]
Get:412 http://archive.ubuntu.com/ubuntu/ quantal-updates/main indicator-appmenu amd64 12.10.3-0ubuntu2.1 [65.8 kB]
Get:413 http://archive.ubuntu.com/ubuntu/ quantal/main indicator-session amd64 12.10.4-0ubuntu1 [120 kB]
Get:414 http://archive.ubuntu.com/ubuntu/ quantal/main libapt-pkg-perl amd64 0.1.26 [81.8 kB]
Get:415 http://archive.ubuntu.com/ubuntu/ quantal/main libarchive-zip-perl all 1.30-6 [90.3 kB]
Get:416 http://archive.ubuntu.com/ubuntu/ quantal/main liblapack3 amd64 3.4.1-6 [5,025 kB]
Get:417 http://archive.ubuntu.com/ubuntu/ quantal/universe libarmadillo3 amd64 1:3.2.3+dfsg-1 [16.9 kB]
Get:418 http://archive.ubuntu.com/ubuntu/ quantal/main libatk-adaptor amd64 2.6.0-0ubuntu1 [4,078 B]
Get:419 http://archive.ubuntu.com/ubuntu/ quantal/main libatk-adaptor-data amd64 2.6.0-0ubuntu1 [3,830 B]
Get:420 http://archive.ubuntu.com/ubuntu/ quantal/main libcommons-dbcp-java all 1.4-3ubuntu1 [149 kB]
Get:421 http://archive.ubuntu.com/ubuntu/ quantal/main libhsqldb-java all 1.8.0.10-13ubuntu1 [918 kB]
Get:422 http://archive.ubuntu.com/ubuntu/ quantal/main libsub-name-perl amd64 0.05-1build3 [9,768 B]
Get:423 http://archive.ubuntu.com/ubuntu/ quantal/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:424 http://archive.ubuntu.com/ubuntu/ quantal/main libclone-perl amd64 0.31-1build4 [11.3 kB]
Get:425 http://archive.ubuntu.com/ubuntu/ quantal/main libclutter-1.0-common all 1.12.0-0ubuntu1 [76.0 kB]
Get:426 http://archive.ubuntu.com/ubuntu/ quantal/main libcogl-common all 1.10.4-0ubuntu1 [188 kB]
Get:427 http://archive.ubuntu.com/ubuntu/ quantal/main libexiv2-12 amd64 0.23-1 [770 kB]
Get:428 http://archive.ubuntu.com/ubuntu/ quantal/main libfile-fcntllock-perl amd64 0.14-2 [15.8 kB]
Get:429 http://archive.ubuntu.com/ubuntu/ quantal/universe libgeos-3.3.3 amd64 3.3.3-1.1 [529 kB]
Get:430 http://archive.ubuntu.com/ubuntu/ quantal/universe libgeos-c1 amd64 3.3.3-1.1 [56.8 kB]
Get:431 http://archive.ubuntu.com/ubuntu/ quantal/main libgeronimo-jta-1.1-spec-java all 1.1.1-2ubuntu2 [12.2 kB]
Get:432 http://archive.ubuntu.com/ubuntu/ quantal/main libgexiv2-1 amd64 0.4.90-0ubuntu1 [50.3 kB]
Get:433 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-zip-archive-prof amd64 0.1.1.7-3build2 [122 kB]
Get:434 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-digest-prof amd64 0.0.1.0-1build2 [10.8 kB]
Get:435 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-zip-archive-dev amd64 0.1.1.7-3build2 [133 kB]
Get:436 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-digest-dev amd64 0.0.1.0-1build2 [15.5 kB]
Get:437 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-unixutils-prof amd64 1.50-1build1 [111 kB]
Get:438 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-puremd5-prof amd64 2.1.0.3-2build3 [80.1 kB]
Get:439 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-crypto-api-prof amd64 0.10.2-1build3 [1,528 kB]
Get:440 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-entropy-prof amd64 0.2.1-2build2 [6,230 B]
Get:441 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-unixutils-dev amd64 1.50-1build1 [121 kB]
Get:442 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-puremd5-dev amd64 2.1.0.3-2build3 [55.7 kB]
Get:443 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-crypto-api-dev amd64 0.10.2-1build3 [1,832 kB]
Get:444 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-entropy-dev amd64 0.2.1-2build2 [10.4 kB]
Get:445 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-largeword-prof amd64 1.0.1-2build3 [50.6 kB]
Get:446 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-largeword-dev amd64 1.0.1-2build3 [59.0 kB]
Get:447 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-tagged-prof amd64 0.4.2.1-1build2 [91.2 kB]
Get:448 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-tagged-dev amd64 0.4.2.1-1build2 [92.1 kB]
Get:449 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-lambdabot-utils-prof amd64 4.2.1-3build1 [277 kB]
Get:450 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-haskell-src-prof amd64 1.0.1.5-1build2 [1,033 kB]
Get:451 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-syb-prof amd64 0.3.6.1-1build2 [140 kB]
Get:452 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-lambdabot-utils-dev amd64 4.2.1-3build1 [308 kB]
Get:453 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-haskell-src-dev amd64 1.0.1.5-1build2 [1,044 kB]
Get:454 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-syb-dev amd64 0.3.6.1-1build2 [138 kB]
Get:455 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-polyparse-prof amd64 1.7-1build2 [642 kB]
Get:456 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-polyparse-dev amd64 1.7-1build2 [623 kB]
Get:457 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-pool-conduit-prof amd64 0.1.0.2-1build1 [10.9 kB]
Get:458 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-resource-pool-prof amd64 0.2.1.0-2build2 [33.2 kB]
Get:459 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hashable-prof amd64 1.1.2.3-1build3 [41.9 kB]
Get:460 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-pool-conduit-dev amd64 0.1.0.2-1build1 [14.5 kB]
Get:461 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-resource-pool-dev amd64 0.2.1.0-2build2 [41.4 kB]
Get:462 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hashable-dev amd64 1.1.2.3-1build3 [49.7 kB]
Get:463 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-conduit-prof amd64 0.4.2-2build2 [225 kB]
Get:464 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-lifted-base-prof amd64 0.1.1-1build2 [68.0 kB]
Get:465 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-monad-control-prof amd64 0.3.1.3-1build2 [63.7 kB]
Get:466 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-base-unicode-symbols-prof amd64 0.2.2.3-1build3 [17.9 kB]
Get:467 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-conduit-dev amd64 0.4.2-2build2 [219 kB]
Get:468 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-lifted-base-dev amd64 0.1.1-1build2 [61.0 kB]
Get:469 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-monad-control-dev amd64 0.3.1.3-1build2 [63.6 kB]
Get:470 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-base-unicode-symbols-dev amd64 0.2.2.3-1build3 [20.4 kB]
Get:471 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-midi-prof amd64 0.2.0.1-1build1 [1,136 kB]
Get:472 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-event-list-prof amd64 0.1.0.1-1build1 [540 kB]
Get:473 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-non-negative-prof amd64 0.1-2build2 [101 kB]
Get:474 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-utility-ht-prof amd64 0.0.5.1-3build2 [141 kB]
Get:475 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-midi-dev amd64 0.2.0.1-1build1 [1,158 kB]
Get:476 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-event-list-dev amd64 0.1.0.1-1build1 [478 kB]
Get:477 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-non-negative-dev amd64 0.1-2build2 [101 kB]
Get:478 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-utility-ht-dev amd64 0.0.5.1-3build2 [141 kB]
Get:479 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hipmunk-prof amd64 5.2.0.8-1build2 [331 kB]
Get:480 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-statevar-prof amd64 1.0.0.0-2build3 [8,566 B]
Get:481 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hipmunk-dev amd64 5.2.0.8-1build2 [372 kB]
Get:482 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-statevar-dev amd64 1.0.0.0-2build3 [12.2 kB]
Get:483 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-explicit-exception-prof amd64 0.1.7-1build2 [188 kB]
Get:484 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-explicit-exception-dev amd64 0.1.7-1build2 [179 kB]
Get:485 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-transformers-base-prof amd64 0.4.1-2build2 [32.7 kB]
Get:486 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-svgcairo-prof amd64 0.12.1-1build1 [19.9 kB]
Get:487 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-tdfa-prof amd64 1.1.8-2build2 [2,519 kB]
Get:488 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-configfile-prof amd64 1.0.6-4build1 [198 kB]
Get:489 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-missingh-prof amd64 1.1.0.3-6build2 [1,190 kB]
Get:490 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-compat-prof amd64 0.95.1-2build2 [18.2 kB]
Get:491 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-posix-prof amd64 0.95.1-2build2 [153 kB]
Get:492 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-pcre-prof amd64 0.94.2-2build2 [155 kB]
Get:493 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-base-prof amd64 0.93.2-2build3 [82.3 kB]
Get:494 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-tagsoup-prof amd64 0.12.6-1build2 [331 kB]
Get:495 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-socks-prof amd64 0.4.1-1build2 [227 kB]
Get:496 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hslogger-prof amd64 1.1.4+dfsg1-2build2 [135 kB]
Get:497 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-network-prof amd64 2.3.0.13-1build2 [628 kB]
Get:498 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hsemail-prof amd64 1.7.1-2build2 [905 kB]
Get:499 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-parsec3-prof amd64 3.1.2-1build2 [604 kB]
Get:500 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-logict-prof amd64 0.5.0.1-1build2 [89.3 kB]
Get:501 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-cairo-prof amd64 0.12.3-1build2 [543 kB]
Get:502 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-mtl-prof amd64 2.1.1-1build4 [139 kB]
Get:503 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-transformers-prof amd64 0.3.0.0-1build3 [478 kB]
Get:504 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-transformers-base-dev amd64 0.4.1-2build2 [34.1 kB]
Get:505 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-svgcairo-dev amd64 0.12.1-1build1 [28.4 kB]
Get:506 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-tdfa-dev amd64 1.1.8-2build2 [3,880 kB]
Get:507 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-configfile-dev amd64 1.0.6-4build1 [212 kB]
Get:508 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-missingh-dev amd64 1.1.0.3-6build2 [1,282 kB]
Get:509 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-compat-dev amd64 0.95.1-2build2 [24.3 kB]
Get:510 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-posix-dev amd64 0.95.1-2build2 [166 kB]
Get:511 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-pcre-dev amd64 0.94.2-2build2 [166 kB]
Get:512 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-regex-base-dev amd64 0.93.2-2build3 [87.8 kB]
Get:513 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-tagsoup-dev amd64 0.12.6-1build2 [351 kB]
Get:514 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-socks-dev amd64 0.4.1-1build2 [190 kB]
Get:515 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hslogger-dev amd64 1.1.4+dfsg1-2build2 [149 kB]
Get:516 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-network-dev amd64 2.3.0.13-1build2 [656 kB]
Get:517 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hsemail-dev amd64 1.7.1-2build2 [876 kB]
Get:518 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-parsec3-dev amd64 3.1.2-1build2 [590 kB]
Get:519 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-logict-dev amd64 0.5.0.1-1build2 [83.6 kB]
Get:520 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-cairo-dev amd64 0.12.3-1build2 [553 kB]
Get:521 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-mtl-dev amd64 2.1.1-1build4 [122 kB]
Get:522 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-transformers-dev amd64 0.3.0.0-1build3 [407 kB]
Get:523 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hunit-prof amd64 1.2.4.2-2build3 [84.2 kB]
Get:524 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-hunit-dev amd64 1.2.4.2-2build3 [89.4 kB]
Get:525 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-quickcheck2-prof amd64 2.4.2-1build2 [561 kB]
Get:526 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-random-prof amd64 1.0.1.1-1build2 [218 kB]
Get:527 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-quickcheck2-dev amd64 2.4.2-1build2 [544 kB]
Get:528 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-random-dev amd64 1.0.1.1-1build2 [239 kB]
Get:529 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-monoid-transformer-prof amd64 0.0.2-3build2 [17.1 kB]
Get:530 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-monoid-transformer-dev amd64 0.0.2-3build2 [18.7 kB]
Get:531 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-resourcet-dev amd64 0.3.2.1-1build1 [143 kB]
Get:532 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-semigroups-prof amd64 0.8.3.2-1build2 [290 kB]
Get:533 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-semigroups-dev amd64 0.8.3.2-1build2 [274 kB]
Get:534 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-void-dev amd64 0.5.5.1-2build2 [31.9 kB]
Get:535 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-resourcet-prof amd64 0.3.2.1-1build1 [157 kB]
Get:536 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-void-prof amd64 0.5.5.1-2build2 [26.8 kB]
Get:537 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-stm-prof amd64 2.3-1build2 [45.6 kB]
Get:538 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-stm-dev amd64 2.3-1build2 [51.7 kB]
Get:539 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-vector-prof amd64 0.9.1-2build2 [1,745 kB]
Get:540 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-primitive-prof amd64 0.4.1-1build2 [97.2 kB]
Get:541 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-vector-dev amd64 0.9.1-2build2 [1,688 kB]
Get:542 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-primitive-dev amd64 0.4.1-1build2 [103 kB]
Get:543 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-text-prof amd64 0.11.2.0-1build2 [1,808 kB]
Get:544 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-text-dev amd64 0.11.2.0-1build2 [2,005 kB]
Get:545 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-utf8-string-prof amd64 0.3.7-1build2 [126 kB]
Get:546 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-utf8-string-dev amd64 0.3.7-1build2 [141 kB]
Get:547 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-zlib-prof amd64 0.5.3.3-1build2 [72.5 kB]
Get:548 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-zlib-dev amd64 0.5.3.3-1build2 [86.0 kB]
Get:549 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-glib-prof amd64 0.12.2-1build2 [265 kB]
Get:550 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-glib-dev amd64 0.12.2-1build2 [285 kB]
Get:551 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-parallel-prof amd64 3.2.0.2-2build3 [53.4 kB]
Get:552 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-parallel-dev amd64 3.2.0.2-2build3 [61.1 kB]
Get:553 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-ranges-prof amd64 0.2.4-2build3 [21.0 kB]
Get:554 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-ranges-dev amd64 0.2.4-2build3 [26.0 kB]
Get:555 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-data-default-prof amd64 0.4.0-1build2 [12.9 kB]
Get:556 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-dlist-prof amd64 0.5-3build2 [18.8 kB]
Get:557 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-data-default-dev amd64 0.4.0-1build2 [17.0 kB]
Get:558 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-dlist-dev amd64 0.5-3build2 [19.9 kB]
Get:559 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-dpkg-prof amd64 0.0.3-1 [193 kB]
Get:560 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-dpkg-dev amd64 0.0.3-1 [199 kB]
Get:561 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-bindings-dsl-dev amd64 1.0.15-1build2 [11.9 kB]
Get:562 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-monad-loops-prof amd64 0.3.2.0-1build2 [57.1 kB]
Get:563 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-monad-loops-dev amd64 0.3.2.0-1build2 [55.1 kB]
Get:564 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-split-prof amd64 0.1.4.2-2build2 [49.9 kB]
Get:565 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-split-dev amd64 0.1.4.2-2build2 [58.5 kB]
Get:566 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-numtype-prof amd64 1.0-2build2 [55.2 kB]
Get:567 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-numtype-dev amd64 1.0-2build2 [59.3 kB]
Get:568 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-cereal-prof amd64 0.3.5.2-1build1 [507 kB]
Get:569 http://archive.ubuntu.com/ubuntu/ quantal/universe ghc-prof amd64 7.4.2-2ubuntu1 [44.2 MB]
Get:570 http://archive.ubuntu.com/ubuntu/ quantal/universe libghc-cereal-dev amd64 0.3.5.2-1build1 [284 kB]
Get:571 http://archive.ubuntu.com/ubuntu/ quantal/universe ghc amd64 7.4.2-2ubuntu1 [45.8 MB]
Get:572 http://archive.ubuntu.com/ubuntu/ quantal-updates/main libgpod-common amd64 0.8.2-6ubuntu1 [28.4 kB]
Get:573 http://archive.ubuntu.com/ubuntu/ quantal/main libio-pty-perl amd64 1:1.08-1build3 [35.8 kB]
Get:574 http://archive.ubuntu.com/ubuntu/ quantal/main libio-string-perl all 1.08-2 [12.0 kB]
Get:575 http://archive.ubuntu.com/ubuntu/ quantal/main libipc-run-perl all 0.91-1 [101 kB]
Get:576 http://archive.ubuntu.com/ubuntu/ quantal/main liblinear-tools amd64 1.8+dfsg-1ubuntu1 [18.7 kB]
Get:577 http://archive.ubuntu.com/ubuntu/ quantal/main libmx-bin amd64 1.4.6-1ubuntu2 [20.5 kB]
Get:578 http://archive.ubuntu.com/ubuntu/ quantal/main libnatpmp1 amd64 20110808-3ubuntu2 [8,460 B]
Get:579 http://archive.ubuntu.com/ubuntu/ quantal/main netpbm amd64 2:10.0-15ubuntu1 [1,338 kB]
Get:580 http://archive.ubuntu.com/ubuntu/ quantal/main libnetpbm10 amd64 2:10.0-15ubuntu1 [69.0 kB]
Get:581 http://archive.ubuntu.com/ubuntu/ quantal/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Get:582 http://archive.ubuntu.com/ubuntu/ quantal/universe libqtbamf1 amd64 0.2.4-0ubuntu2 [67.6 kB]
Get:583 http://archive.ubuntu.com/ubuntu/ quantal-updates/main libreoffice-help-en-us all 1:3.6.2~rc2-0ubuntu4 [8,963 kB]
Get:584 http://archive.ubuntu.com/ubuntu/ quantal/main hardening-includes all 2.2 [15.0 kB]
Get:585 http://archive.ubuntu.com/ubuntu/ quantal/main patchutils amd64 0.3.2-1.1build1 [91.1 kB]
Get:586 http://archive.ubuntu.com/ubuntu/ quantal-updates/main lintian all 2.5.10.2ubuntu2.1 [536 kB]
Get:587 http://archive.ubuntu.com/ubuntu/ quantal/main network-manager-gnome amd64 0.9.6.2-0ubuntu6 [418 kB]
Get:588 http://archive.ubuntu.com/ubuntu/ quantal/main python3-cairo amd64 1.10.0+dfsg-3~exp2 [37.5 kB]
Get:589 http://archive.ubuntu.com/ubuntu/ quantal-updates/main python3-gi-cairo amd64 3.4.0-1ubuntu0.1 [21.5 kB]
Get:590 http://archive.ubuntu.com/ubuntu/ quantal/main python3-virtkey amd64 0.61.0-0ubuntu1 [15.9 kB]
Get:591 http://archive.ubuntu.com/ubuntu/ quantal/main onboard amd64 0.98.0-0ubuntu2 [423 kB]
Get:592 http://archive.ubuntu.com/ubuntu/ quantal/main printer-driver-ptouch amd64 1.3-4ubuntu1 [29.8 kB]
Get:593 http://archive.ubuntu.com/ubuntu/ quantal/main printer-driver-pxljr amd64 1.3+repack0-2build1 [30.3 kB]
Get:594 http://archive.ubuntu.com/ubuntu/ quantal/main printer-driver-splix amd64 2.0.0+svn306-2ubuntu1 [43.9 kB]
Get:595 http://archive.ubuntu.com/ubuntu/ quantal/main python3-crypto amd64 2.6-2 [381 kB]
Get:596 http://archive.ubuntu.com/ubuntu/ quantal/main python3-oauthlib all 0.3.0-0ubuntu1 [45.6 kB]
Get:597 http://archive.ubuntu.com/ubuntu/ quantal/main python3-pyatspi2 all 2.6.0+dfsg-0ubuntu1 [36.5 kB]
Get:598 http://archive.ubuntu.com/ubuntu/ quantal/main python3-pycurl amd64 7.19.0-5ubuntu1 [48.9 kB]
Get:599 http://archive.ubuntu.com/ubuntu/ quantal/main qpdf amd64 3.0.2-1 [190 kB]
Get:600 http://archive.ubuntu.com/ubuntu/ quantal/main ubuntu-wallpapers-quantal all 0.35.2 [3,391 kB]
Get:601 http://archive.ubuntu.com/ubuntu/ quantal/main ubuntu-wallpapers all 0.35.2 [566 kB]
Get:602 http://archive.ubuntu.com/ubuntu/ quantal-updates/main unity-greeter amd64 12.10.4-0ubuntu5.1 [137 kB]
Get:603 http://archive.ubuntu.com/ubuntu/ quantal-updates/main unity-lens-applications amd64 6.10.0-0ubuntu1 [94.8 kB]
Get:604 http://archive.ubuntu.com/ubuntu/ quantal-updates/main unity-lens-gwibber amd64 3.6.0-0ubuntu1.1 [28.9 kB]
Get:605 http://archive.ubuntu.com/ubuntu/ quantal-updates/main unity-lens-photos all 0.9-0ubuntu1 [28.5 kB]
Get:606 http://archive.ubuntu.com/ubuntu/ quantal/main unity-lens-shopping amd64 6.8.0-0ubuntu1 [32.2 kB]
Get:607 http://archive.ubuntu.com/ubuntu/ quantal/main unity-scope-gdocs all 0.7-0ubuntu1 [10.7 kB]
Get:608 http://archive.ubuntu.com/ubuntu/ quantal/main unity-scope-musicstores amd64 6.8.1-0ubuntu1 [35.7 kB]
Get:609 http://archive.ubuntu.com/ubuntu/ quantal-updates/main unity-scope-video-remote all 0.3.10-0ubuntu1.1 [9,704 B]
Get:610 http://archive.ubuntu.com/ubuntu/ quantal-updates/main xdiagnose all 3.2.4 [100 kB]
Get:611 http://archive.ubuntu.com/ubuntu/ quantal/universe xpdf amd64 3.03-9ubuntu5 [189 kB]
Get:612 http://archive.ubuntu.com/ubuntu/ quantal/main libpam-freerdp amd64 1.0.1-0ubuntu1 [9,944 B]
Get:613 http://archive.ubuntu.com/ubuntu/ quantal-updates/main libreoffice-pdfimport amd64 1.0.6+LibO3.6.2~rc2-0ubuntu4 [489 kB]
Get:614 http://archive.ubuntu.com/ubuntu/ quantal/universe libspatialite3 amd64 3.1.0~rc2-1ubuntu1 [1,007 kB]
Get:615 http://archive.ubuntu.com/ubuntu/ quantal/main lightdm-remote-session-freerdp amd64 1.0-0ubuntu2 [7,254 B]
Get:616 http://archive.ubuntu.com/ubuntu/ quantal/main lightdm-remote-session-uccsconfigure amd64 1.1-0ubuntu2 [6,028 B]
Get:617 http://archive.ubuntu.com/ubuntu/ quantal/universe python-packagekit all 0.7.6-1 [23.1 kB]
Get:618 http://archive.ubuntu.com/ubuntu/ quantal/universe packagekit-backend-aptcc amd64 0.7.6-1 [118 kB]
Get:619 http://archive.ubuntu.com/ubuntu/ quantal/main ubuntuone-control-panel all 4.0.0-0ubuntu1 [1,966 B]
Get:620 http://archive.ubuntu.com/ubuntu/ quantal/main python-ubuntuone-control-panel all 4.0.0-0ubuntu1 [29.7 kB]
Get:621 http://archive.ubuntu.com/ubuntu/ quantal-updates/main python3-aptdaemon.pkcompat all 0.45+bzr861-0ubuntu9.1.2 [34.0 kB]
Get:622 http://archive.ubuntu.com/ubuntu/ quantal/main python3-brlapi amd64 4.4-5ubuntu3 [55.0 kB]
Get:623 http://archive.ubuntu.com/ubuntu/ quantal/main python3-louis amd64 2.4.1-1ubuntu1 [7,020 B]
Get:624 http://archive.ubuntu.com/ubuntu/ quantal-updates/main shotwell amd64 0.13.1-0ubuntu1 [2,304 kB]
Get:625 http://archive.ubuntu.com/ubuntu/ quantal/main thin-client-config-agent all 0.6 [5,828 B]
Fetched 577 MB in 5min 53s (1,633 kB/s) 

```

It's currently at 39% Extracting templates from packages

---

### Post by j88n on 2014-01-08
Here's the last bit after extracting the templates:

```

Extracting templates from packages: 100%
Preconfiguring packages ...
Bus error (core dumped)
keyboard-configuration failed to preconfigure, with exit status 135
Bus error (core dumped)
cups failed to preconfigure, with exit status 135
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
Bus error (core dumped)
setserial failed to preconfigure, with exit status 135
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

---

### Post by Bashing-om on 2014-01-08
j88n; Yuk !

Many many updates pending, many many held back and no idea yet what is holding them up !

Long shot:
```

sudo dpkg -l | grep -v ^ii

``` to see what the status is of any packages the package manager is tracking that are not fully installed.
Now if some knowledgeable one will come forth and advise on what "exit status 135" means in this context, will sure help a lot.

Now ya got me going !
[INDENT][INDENT]inquiring minds want to klnow
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-08
Sigh... No output for that command :( 

I've looked up that error too, but I don't see anything that'd fit for me..

---

### Post by j88n on 2014-01-08
This thread seems kind of similar to my issue, however, I'm not getting as much helpful output as they were

[http://ubuntuforums.org/showthread.php?t=2073770]("http://ubuntuforums.org/showthread.php?t=2073770&page=3")

---

### Post by Bashing-om on 2014-01-08
j88n;

Welp, I am burned out for this session, I will pick this up again in my AM. See what I can find out about "exit status 135".
As I am getting nowhere with my current approach, a change in tactics is in order.

[INDENT][INDENT]this is a thing !
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-08
Okay, see you tomorrow! Thanks for trying

---

### Post by Bashing-om on 2014-01-08
j88n;

We ain't whooped, No quit in my nature.

See ya then.

---

### Post by mc4man on 2014-01-09
I'd probably take a look at the status for the 3 mentioned packages  in /var/lib/dpkg/status directly & see if they were at - 
Status: install ok installed
(- setserial,  keyboard-configuration, cups
If not, then  see if making them such had any effect.. (best to** back up **that /var/lib/dpkg/status first
If already showing the above  then maybe deleting those 3 entries entirely.

Edit : if you have any doubts about doing the above then ask first. Also please backup that file before doing anything, no sense going from very bad to impossible..

Do you happen to have aptitude installed?

---

### Post by Bashing-om on 2014-01-09
@ mc4man; Thanks, outstanding observation as we are sure that some entries in "/var/lib/dpkg/status" are in an inconsistent state.

@j88n; Comply with mc4man's advisements and we will carry on.

[INDENT][INDENT]a little help
[INDENT][INDENT][INDENT]goes a long way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-09
Sorry for the late reply!  Thanks @mc4man for joining in to help. I opened /var/lib/status and searched for those three packages. The status is as follows: 

-setserial
```
 
Package: setserial
Status: install ok installed
Priority: extra
Section: comm
Installed-Size: 176
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2.17-46
Depends: libc6 (>= 2.7), debconf (>= 0.5) | debconf-2.0
Conffiles:
 /etc/init.d/setserial 8559d521dedd832b2be120f70cb1706a
 /etc/init.d/etc-setserial 93030e9123cb63db75b2179623c60cf8
 /etc/modutils/setserial cb23d25565eae64f12ef267efd3f42c3
Description: controls configuration of serial ports
 Set and/or report the configuration information associated with
 a serial port. This information includes what I/O port and which IRQ
 a particular serial port is using.
 .
 This version has a completely new approach to configuration, so if you
 have a setup other than the standard ttyS0 and 1, you will have to get
 your hands dirty.
 .
 By default, only COM1-4 are configured by the kernel, using IRQ 3 and 4.
 If you have other serial ports (such as an AST Fourport card), or
 if you have mapped the IRQs differently (perhaps COM3 and 4 to other
 IRQs to allow concurrent access with COM1 and 2) then you must have this
 package.
Original-Maintainer: Debian QA Group <packages@qa.debian.org>
```

keyboard-configuration
```
Package: keyboard-configuration
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 2172
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Architecture: all
Source: console-setup
Version: 1.70ubuntu5
Replaces: console-setup (<< 1.47), console-setup-mini (<< 1.47)
Depends: debconf (>= 1.5.34), upstart-job, liblocale-gettext-perl
Conflicts: console-setup (<< 1.47), console-setup-mini (<< 1.47)
Conffiles:
 /etc/init/console-setup.conf 7fe93d1fb1311225f741b61ebff20942
Description: system-wide keyboard preferences
 This package maintains the keyboard preferences in
 /etc/default/keyboard.  Other packages can use the information
 provided by this package in order to configure the keyboard on the
 console or in X Window.
Original-Maintainer: Debian Install System Team <debian-boot@lists.debian.org>
```

cups
```
Package: cups
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 4193
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.5.3-0ubuntu8
Replaces: cupsddk-drivers (<< 1.4.0), ghostscript-cups (<< 9.02~)
Provides: cupsddk-drivers
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.15), libcups2 (>= 1.5.0), libcupscgi1 (>= 1.4.2), libcupsimage2 (>= 1.4.0), libcupsmime1 (>= 1.5.0), libcupsppdc1 (>= 1.4.0), libdbus-1-3 (>= 1.0.2), libgcc1 (>= 1:4.1.1), libgnutls26 (>= 2.12.6.1-0), libgssapi-krb5-2 (>= 1.8+dfsg), libkrb5-3 (>= 1.6.dfsg.2), libldap-2.4-2 (>= 2.4.7), libpam0g (>= 0.99.7.1), libpaper1, libslp1, libstdc++6 (>= 4.1.1), libusb-1.0-0 (>= 2:1.0.9~rc3), debconf (>= 1.2.9) | debconf-2.0, upstart-job, poppler-utils (>= 0.12), procps, ghostscript (>= 9.02~), lsb-base (>= 3), cups-common (>= 1.5.3), cups-client (>= 1.5.3-0ubuntu8), ssl-cert (>= 1.0.11), adduser, bc, cups-ppdc, cups-filters
Pre-Depends: dpkg (>= 1.15.7.2)
Recommends: avahi-daemon, colord, foomatic-filters (>= 4.0), printer-driver-gutenprint, ghostscript-cups (>= 9.02~)
Suggests: cups-bsd, foomatic-db-compressed-ppds | foomatic-db, printer-driver-hpcups, hplip, cups-pdf, udev, smbclient
Breaks: cupsddk-drivers (<< 1.4.0), foomatic-filters (<< 4.0), ghostscript-cups (<< 9.02~)
Conffiles:
 /etc/apparmor.d/usr.sbin.cupsd 5cc210d5438fc12e5f0a4aa50ac9e3df
 /etc/ufw/applications.d/cups 29e98a6d850da251e180c3d68dec2bd3
 /etc/pam.d/cups ff2488324854f7b1e892bb0df062d5f0
 /etc/default/cups 2b436fbb1a32b82b6aba45a76a1d7e40
 /etc/cups/cups-files.conf 2d5c3341837e2dabeaa16cf90582fd6c
 /etc/cups/cupsd.conf bd2b7cffb7cc23734ccee179d2584419
 /etc/cups/snmp.conf 55baa060a50f48f9dbb99c6eb60dc04c
 /etc/cups/cupsd.conf.default 03cc7d46e085b96b9dea5f78cb80d116
 /etc/logrotate.d/cups 5bb41fa9900f0d1c565954405a2bd7c4
 /etc/init/cups.conf 43d2d4234cff969f03c48484e985deed
Description: Common UNIX Printing System(tm) - server
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the CUPS scheduler/daemon and related files.
Homepage: http://www.cups.org
Original-Maintainer: Debian CUPS Maintainers <pkg-cups-devel@lists.alioth.debian.org>

```

---

### Post by j88n on 2014-01-09
Since they look like they are all installed correct, I have run the command:

```
sudo cp status status.old
```
 
to make a copy and am removing those three entries to see what happens.

---

### Post by Bashing-om on 2014-01-09
j88n; Well,

High hopes, but, back to the drawing board.

---

### Post by j88n on 2014-01-09
I just ran "apt-get autoclean"

```
sean@Sean-Monster:/var/lib/dpkg$ sudo apt-get autocleanReading package lists... Done
Building dependency tree       
Reading state information... Done



```

then "apt-get autoremove" to see what spit out... any ideas?

```
sean@Sean-Monster:/var/lib/dpkg$ sudo apt-get autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 bluez-cups : Depends: cups but it is not installable
 console-setup : Depends: keyboard-configuration but it is not installable
 hplip : Depends: cups (>= 1.1.20) but it is not installable
 indicator-printers : Depends: cups (>= 1.5) but it is not installable
 lirc : Depends: setserial but it is not installable
 printer-driver-gutenprint : Depends: cups (>= 1.3.0) but it is not installable
 printer-driver-hpcups : Depends: cups but it is not installable
 xserver-xorg-core-lts-raring : Depends: keyboard-configuration but it is not installable
E: Unmet dependencies. Try using -f.



```

---

### Post by Bashing-om on 2014-01-10
j88n; Whohh !

What a web we weave for our self, yeah now we have something to work with.
> 
Get:371 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [color=red]quantal[/color]/main g++-4.7 amd64 4.7.2-2ubuntu1 [7,966 kB]
 xserver-xorg-core-lts-[color=red]raring[/color] : Depends: keyboard-configuration but it is not installable
cups:
Version: 1.5.3-0ubuntu8
hplip : Depends: cups (>= 1.1.20) but it is not installable
indicator-printers : Depends: cups (>= 1.5) but it is not installable


For starters, right off hand I would say we need to uninstall the hp printer driver(s), AND deal with some way to get "xserver-xorg-core-lts" downgraded back to the proper version for quantal.


It is late my time, and my thinking has become impaired, will pick this one up at a later time.

[INDENT][INDENT]good work !
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-10
Okay, good night!

Let me know how I can go about uninstalling the drivers and doing the downgrade.

---

### Post by mc4man on 2014-01-10
downgrading xserver-xorg-core shouldn't be that difficult but keep in mind - 

It depends on **xserver-common**, best to do 2 both at once (xserver-common is an all.deb, -core is arch specific
There are 2 meta packages, xorg & xorg-server, just make sure they don't conflict (shouldn't be an issue, worst case they can be removed
**Once you start do not log out, restart or shutdown until you've squared this up **or you not *may* be able to log in 

What you need can be found here, there 3 sources in quantal, release or updates probably best choices
[https://launchpad.net/ubuntu/+source/xorg-server](https://launchpad.net/ubuntu/+source/xorg-server)

Hopefully didn't pick up on any other 'core' packages from raring, may want to first check somehow..

@j88n - You should wait for thoughts/directions from bashing-om,

---

### Post by Bashing-om on 2014-01-10
@ mc4man; I do so appreciate the collaboration !

Here is my thoughts, I do enjoy a good challenge - getting cups squared away may be a real challenge - not to even mention the printer drivers.
Now with all that is to be done - quantal only has 3 months of life left, Do YOU want to go through this trouble and hassle for only such a short time ??
Particularly so as you have a working install 13.10 ! .. 
I am up for the effort, the call is yours.

If we are to proceed in the salvage operation we need to have some idea of what we are up against.
show us:
```

apt-cache policy bluez-cups
apt-cache policy console-setup
apt-cache policy keyboard-configuration
apt-cache policy hplip
apt-cache policy indicator-printers
apt-cache policy lirc
apt-cache policy setserial
apt-cache policy printer-driver-gutenprint
apt-cache policy printer-driver-hpcups
apt-cache policy cups

```
And more to come and these are biggies.
do:
```

apt-cache depends <package_name>

```
and as well the reverse depends; do:
```

apt-cache rdepends <package_name>

```
For each and every package listed above.

These will give us a good idea of what we might have to contend with . There is a lot of work to do.

In addition is downgrading  xserver-xorg-core, which I expect should be the 1st order of business . That may introduce more dependency issues.

[INDENT]all in a days work and 
[INDENT][INDENT][INDENT]this will be a learning experience
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-10
So I'm don't really understand the difference between quantal and other things. My main objective is to have ubuntu working where I can install and/or upgrade normally. I have 12.04.3 and would like to upgrade, but can't with these "bugs." I am just trying to avoid a complete fresh install and starting from scratch. I'd like to some-what some these problems.

Okay running the commands now.

---

### Post by j88n on 2014-01-10
Here's the first chunk:  

apt-cache policy bluez-cups
```
bluez-cups:
  Installed: 4.98-2ubuntu7
  Candidate: 4.101-0ubuntu6
  Version table:
     4.101-0ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
 *** 4.98-2ubuntu7 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```




apt-cache policy console-setup
```
console-setup:
  Installed: 1.70ubuntu5
  Candidate: 1.70ubuntu6
  Version table:
     1.70ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
 *** 1.70ubuntu5 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```




apt-cache policy keyboard-configuration
```
keyboard-configuration:
  Installed: (none)
  Candidate: 1.70ubuntu6
  Version table:
     1.70ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
     1.70ubuntu5 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages

```


apt-cache policy hplip
```
hplip:
  Installed: 3.12.2-1ubuntu3.3
  Candidate: 3.12.6-3ubuntu4.2
  Version table:
     3.12.6-3ubuntu4.2 0
        500 http://security.ubuntu.com/ubuntu/ quantal-security/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main amd64 Packages
     3.12.6-3ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
 *** 3.12.2-1ubuntu3.3 0
        100 /var/lib/dpkg/status
     3.12.2-1ubuntu3 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages
```


apt-cache policy indicator-printers
```
indicator-printers:
  Installed: 0.1.6-0ubuntu1
  Candidate: 0.1.6-0ubuntu3
  Version table:
     0.1.6-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
 *** 0.1.6-0ubuntu1 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```


apt-cache policy lirc
```
lirc:
  Installed: 0.9.0-0ubuntu1
  Candidate: 0.9.0-0ubuntu3
  Version table:
     0.9.0-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
 *** 0.9.0-0ubuntu1 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```


apt-cache policy setserial
```
  Installed: (none)
  Candidate: 2.17-47
  Version table:
     2.17-47 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
     2.17-46 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages

```


apt-cache policy printer-driver-gutenprint
```
printer-driver-gutenprint:
  Installed: 5.2.8~pre1-0ubuntu2.1
  Candidate: 5.2.9-1ubuntu1
  Version table:
     5.2.9-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
 *** 5.2.8~pre1-0ubuntu2.1 0
        100 /var/lib/dpkg/status
     5.2.8~pre1-0ubuntu2 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages
```


apt-cache policy printer-driver-hpcups
```
printer-driver-hpcups:
  Installed: 3.12.2-1ubuntu3.3
  Candidate: 3.12.6-3ubuntu4.2
  Version table:
     3.12.6-3ubuntu4.2 0
        500 http://security.ubuntu.com/ubuntu/ quantal-security/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main amd64 Packages
     3.12.6-3ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
 *** 3.12.2-1ubuntu3.3 0
        100 /var/lib/dpkg/status
     3.12.2-1ubuntu3 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages

```


apt-cache policy cups
```
cups:
  Installed: (none)
  Candidate: 1.6.1-0ubuntu11.4
  Version table:
     1.6.1-0ubuntu11.4 0
        500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main amd64 Packages
     1.6.1-0ubuntu11.3 0
        500 http://security.ubuntu.com/ubuntu/ quantal-security/main amd64 Packages
     1.6.1-0ubuntu11 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
     1.5.2-9ubuntu1 0
        500 http://ubuntu.mirror.cambrium.nl/ubuntu/ precise/main amd64 Packages

```

---

### Post by Bashing-om on 2014-01-10
j88n; You the man .

This:
> 
quantal/main g++-4.7 amd64 4.7.2-2ubuntu1 [7,966 kB]
Get:372 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main g++ amd64 4:4.7.2-1ubuntu2 [1,448 B]
Get:373 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main dpkg-dev all 1.16.7ubuntu6 [595 kB]
Get:374 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main libdpkg-perl all 1.16.7ubuntu6 [188 kB]
Get:375 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main python3-lxml amd64 2.3.5-1 [658 kB]
Get:376 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main checkbox amd64 0.14.10 [1,331 kB]
Get:377 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main checkbox-qt amd64 0.14.10 [75.5 kB]
Get:378 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main cracklib-runtime amd64 2.8.19-1 [170 kB]
Get:379 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main debhelper all 9.20120608ubuntu1 [623 kB]
Get:380 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main diffstat amd64 1.55-3 [23.5 kB]
Get:381 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe finger amd64 0.17-15 [17.3 kB]
Get:382 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main freerdp-x11 amd64 1.0.1-1ubuntu7 [49.1 kB]
Get:383 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main gcj-4.7-jre-lib all 4.7.2-1ubuntu1 [10.5 MB]
Get:384 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main gir1.2-gdata-0.0 amd64 0.13.2-0ubuntu1 [40.5 kB]
Get:385 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main gir1.2-syncmenu-0.1 amd64 12.10.4-0ubuntu1 [2,746 B]
Get:386 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main totem-mozilla amd64 3.4.3-0ubuntu5 [139 kB]
Get:387 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main totem-plugins amd64 3.4.3-0ubuntu5 [164 kB]
Get:388 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/main totem amd64 3.4.3-
<snip>

Says we are working on a quantal (12.10) install that will be End Of Life @ April of 2014. No longer enjoying support.
The current Long Term Support is indeed 12.04, and will maintain support 'till 2017.
In April 2014 the next LTS version 14.04 will also be released.
So let's KNOW what version you have:
```

uname -a
lsb_release -a

```

I do re-affirm, we will do as you dictate. If you want to expend the time and other resources to repair this nearing EOL install, that is what we will do.
But up front believe me, it is going to be an experience in learning !

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-10
bluez-cups


apt-cache depends <package_name>
```

bluez-cups
  Depends: libc6
  Depends: libdbus-1-3
  Depends: libglib2.0-0
  Depends: cups

```


apt-cache rdepends <package_name>
```

bluez-cups
Reverse Depends:
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-sugar-remix
  lubuntu-core
  kubuntu-active
  ichthux-desktop
  bluetooth
  ubuntu-desktop
  kubuntu-desktop
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-gnome-desktop
  lubuntu-core
  kubuntu-desktop
  bluetooth
  ubuntu-desktop

```




console-setup
apt-cache depends <package_name>
```

console-setup
  Depends: debconf
  Depends: xkb-data
  Depends: keyboard-configuration
  Depends: initramfs-tools
  Depends: kbd
  Depends: <upstart-job>
    upstart
  Suggests: lsb-base
  Suggests: locales
  Conflicts: <console-terminus>
  Conflicts: lsb
  Conflicts: lsb-base
  Conflicts: lsb-core
  Replaces: <console-terminus>
    console-setup

```


apt-cache rdepends <package_name>
```

console-setup
Reverse Depends:
  ubuntu-minimal
 |initramfs-tools-tcos
  console-setup-mini
  ubuntu-minimal
  ubiquity
  ltsp-client-core
  keyboard-configuration
  keyboard-configuration
  kbd
  ubiquity
 |initramfs-tools-tcos
 |console-tools
 |console-tools
  console-setup-mini
  ubuntu-minimal
  ubiquity
  system-config-kickstart
  ltsp-client-core
  keyboard-configuration
  keyboard-configuration
  kbd
  grub-common

```




keyboard-configuration
apt-cache depends <package_name>
```

keyboard-configuration
  Depends: debconf
  Depends: <upstart-job>
    upstart
  Depends: liblocale-gettext-perl
  Conflicts: console-setup
  Conflicts: console-setup-mini
  Replaces: console-setup
  Replaces: console-setup-mini

```


apt-cache rdepends <package_name>
```

Reverse Depends:
  xserver-xorg-core-lts-raring
  console-setup-mini
  xserver-xorg-core
  console-setup
  xserver-xorg-core
  xserver-xorg-core
  live-config
  console-setup-mini
  xserver-xorg-core
  console-setup

```


hplip
apt-cache depends <package_name>
```

hplip
  Depends: libc6
  Depends: libcups2
  Depends: libdbus-1-3
  Depends: libhpmud0
  Depends: libsane
  Depends: libsane-hpaio
  Depends: hplip-data
  Depends: printer-driver-hpcups
  Depends: python2.7
  Depends: python
  Depends: python
  Depends: python-dbus
  Depends: python-imaging
  Depends: python-pexpect
  Depends: python-reportlab
  Depends: coreutils
  Depends: lsb-base
  Depends: adduser
  Depends: cups
  Depends: policykit-1
  Depends: python-gobject-2
  Depends: wget
  Suggests: hplip-gui
  Suggests: hplip-doc
  Suggests: python-notify
  Suggests: <system-config-printer>
  Recommends: printer-driver-postscript-hp
  Recommends: sane-utils
  Recommends: avahi-daemon

```


apt-cache rdepends <package_name>
```

hplip
Reverse Depends:
  hplip-data
  printer-driver-postscript-hp
  printer-driver-postscript-hp
  printer-driver-postscript-hp
  libhpmud0
  libhpmud0
  printer-driver-hpcups
  printer-driver-hpijs
  libsane-hpaio
  libsane-hpaio
  libsane-hpaio
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-sugar-remix
  printer-driver-postscript-hp
  printer-driver-postscript-hp
  printer-driver-postscript-hp
  lubuntu-core
  kubuntu-active
  ichthux-desktop
  hplip-gui
  ubuntu-desktop
  printer-driver-hpijs
  printer-driver-hpcups
  libsane-hpaio
  libsane-hpaio
  libsane-hpaio
  libsane
  libhpmud0
  libhpmud0
  kubuntu-desktop
  hplip-doc
  hplip-dbg
 |hplip-dbg
  hplip-data
  foomatic-db-compressed-ppds
  foomatic-db
  cups
  cups
  printer-driver-postscript-hp
  printer-driver-postscript-hp
  printer-driver-postscript-hp
  printer-driver-hpijs
  printer-driver-hpcups
  libsane-hpaio
  libsane-hpaio
  libsane-hpaio
  libhpmud0
  libhpmud0
  hplip-doc
  hplip-dbg
 |hplip-dbg
  hplip-data
  cups
  hplip-gui
  hplip-gui
  hplip-gui
  zentyal-printers
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-gnome-desktop
  lubuntu-core
  kubuntu-desktop
  hplip-gui
  hplip-gui
  hplip-gui
  foomatic-db
  ubuntu-desktop
  printer-driver-postscript-hp
  printer-driver-postscript-hp
  printer-driver-postscript-hp
  printer-driver-hpijs
  printer-driver-hpcups
  libsane-hpaio
  libsane-hpaio
  libsane-hpaio
  libsane
  libhpmud0
  libhpmud0
  hplip-doc
  hplip-dbg
 |hplip-dbg
  hplip-data
  foomatic-db-compressed-ppds
  cups

```


 indicator-printers
apt-cache depends <package_name>
```

indicator-printers
  Depends: libc6
  Depends: libcairo2
  Depends: libcups2
  Depends: libdbusmenu-glib4
  Depends: libdbusmenu-gtk3-4
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk-3-0
  Depends: libindicator3-7
  Depends: libpango1.0-0
  Depends: cups
 |Recommends: indicator-applet
  Recommends: <indicator-renderer>
    awn-applet-indicator
    indicator-applet
    indicator-applet-appmenu
    indicator-applet-complete
    lxpanel-indicator-applet-plugin
    plasma-widgets-workspace
    ubiquity-frontend-gtk
    unity
    xfce4-indicator-plugin
  Recommends: system-config-printer-gnome

```


apt-cache rdepends <package_name>
```

indicator-printers
Reverse Depends:
  unity
  unity
  unity
  ubuntu-gnome-desktop
  unity

```


lirc
apt-cache depends <package_name>
```

lirc
  Depends: libasound2
  Depends: libc6
  Depends: libftdi1
  Depends: liblircclient0
  Depends: libportaudio2
  Depends: libusb-0.1-4
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Depends: lsb-base
  Depends: setserial
  Suggests: lirc-x
  Recommends: udev
  Conflicts: <lirc-modules-source>
  Conflicts: makedev
  Replaces: <lirc-modules-source>

```


apt-cache rdepends <package_name>
```

lirc
Reverse Depends:
  vdr
  mythbuntu-live-autostart
  lirc-x
  lirc-x
  freevo-lirc
  enna
  banshee-extension-lirc
  liblircclient0
  kremotecontrol
  kremotecontrol
  vdr
  mythbuntu-live-autostart
  mythbuntu-lirc-generator
  lirc-x
  lirc-x
  kremotecontrol
  inputlirc
  gnome-lirc-properties
  freevo-lirc
  enna
  banshee-extension-lirc
  liblircclient0

```


 setserial
apt-cache depends <package_name>
```

setserial
  Depends: libc6
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf

```


apt-cache rdepends <package_name>
```

setserial
Reverse Depends:
  bluez-pcmcia-support
  lirc
  irda-utils
  lirc
  gpstrans
  bluez-pcmcia-support
  irda-utils

```


printer-driver-gutenprint
apt-cache depends <package_name>
```

printer-driver-gutenprint
  Depends: libc6
  Depends: libcups2
  Depends: libcupsimage2
  Depends: libgutenprint2
  Depends: cups
  Depends: cups-client
  Depends: ghostscript-cups
  Suggests: gutenprint-doc
  Suggests: gutenprint-locales
  Conflicts: cups-driver-gutenprint
  Replaces: cups-driver-gutenprint

```


apt-cache rdepends <package_name>
```

printer-driver-gutenprint
Reverse Depends:
  ijsgutenprint-ppds
  gutenprint-doc
  foomatic-db-compressed-ppds
  foomatic-db
  cups-driver-gutenprint
  cups
  cups
  cups
  printer-driver-all-enforce
  printer-driver-all
  ijsgutenprint-ppds
  gutenprint-doc
  cups-driver-gutenprint
  cups

```


printer-driver-hpcups
apt-cache depends <package_name>
```

printer-driver-hpcups
  Depends: libc6
  Depends: libcups2
  Depends: libcupsimage2
  Depends: libdbus-1-3
  Depends: libgcc1
  Depends: libhpmud0
  Depends: libjpeg8
  Depends: libstdc++6
  Depends: ghostscript-cups
 |Depends: cups
  Depends: cupsddk
    cups-ppdc
  Depends: cups
  Suggests: hplip-doc
  Suggests: hplip
  Breaks: hplip-cups
  Replaces: hplip-cups

```


apt-cache rdepends <package_name>
```

printer-driver-hpcups
Reverse Depends:
  hplip
  hplip-cups
 |hplip-dbg
  hplip
  foomatic-db-compressed-ppds
  foomatic-db
  cups
  cups
 |hplip-dbg
  hplip
  cups
  hplip-cups
  printer-driver-all-enforce
  printer-driver-all
  hplip-cups
 |hplip-dbg
  hplip
  cups

```


cups
apt-cache depends <package_name>
```

cups
  Depends: libavahi-client3
  Depends: libavahi-common3
  Depends: libc6
  Depends: libcups2
  Depends: libcupscgi1
  Depends: libcupsimage2
  Depends: libcupsmime1
  Depends: libcupsppdc1
  Depends: libdbus-1-3
  Depends: libgcc1
  Depends: libgnutls26
  Depends: libgssapi-krb5-2
  Depends: libkrb5-3
  Depends: libpam0g
  Depends: libpaper1
  Depends: libstdc++6
  Depends: libusb-1.0-0
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Depends: <upstart-job>
    upstart
  Depends: poppler-utils
  Depends: procps
  Depends: ghostscript
  Depends: lsb-base
  Depends: cups-common
  Depends: cups-client
  Depends: ssl-cert
  Depends: adduser
  Depends: bc
  Depends: cups-ppdc
  Depends: cups-filters
  PreDepends: dpkg
  Suggests: cups-bsd
 |Suggests: foomatic-db-compressed-ppds
  Suggests: foomatic-db
    foomatic-db-compressed-ppds
  Suggests: printer-driver-hpcups
  Suggests: hplip
  Suggests: cups-pdf
  Suggests: udev
  Suggests: smbclient
  Recommends: avahi-daemon
  Recommends: colord
  Recommends: foomatic-filters
  Recommends: printer-driver-gutenprint
  Recommends: ghostscript-cups
  Breaks: <cupsddk-drivers>
  Breaks: foomatic-filters
  Breaks: ghostscript-cups
  Replaces: <cupsddk-drivers>
  Replaces: ghostscript-cups

```


apt-cache rdepends <package_name>
```

cups
Reverse Depends:
  hplip
  ghostscript-cups
  cups-bsd
  printer-driver-gutenprint
  printer-driver-postscript-hp
 |foomatic-filters
  cups-filters
  cups-filters
  libcups2
  libcupsmime1
  cups-client
  printer-driver-hpcups
 |printer-driver-hpcups
 |printer-driver-hpijs
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-sugar-remix
  printer-driver-postscript-hp
  printconf
  lubuntu-core
  libgnomecups1.0-1
  kubuntu-active
  ichthux-desktop
  geogebra
  cups-pdf
  ubuntu-desktop
 |printer-driver-splix
  printer-driver-min12xxw
 |printer-driver-hpijs
  printer-driver-hpcups
 |printer-driver-hpcups
  printer-driver-gutenprint
  printer-driver-foo2zjs
  printer-driver-foo2zjs
  printer-driver-c2esp
  openprinting-ppds
  openprinting-ppds
  libcupsmime1
  libcups2
  kubuntu-desktop
  indicator-printers
  hplip
  ghostscript-cups
 |foomatic-filters
  foomatic-db-engine
  foomatic-db-engine
  foomatic-db-compressed-ppds
  foomatic-db-compressed-ppds
  foomatic-db
  foomatic-db
  cups-filters
  cups-filters
  cups-dbg
  cups-client
  cups-bsd
  bluez-cups
  libcupsmime1
  libcups2
  cups-filters
  cups-filters
  cups-dbg
  cups-client
  cups-bsd
  printer-driver-postscript-hp
 |printer-driver-hpijs
  printer-driver-hpcups
 |printer-driver-hpcups
  libcupsmime1
  libcups2
  hplip
  cups-dbg
  cups-client
  cups-bsd
  zentyal-printers
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-gnome-desktop
  printer-driver-escpr
  printconf
  lubuntu-core
  libgnomeprint2.2-0
  libgnomecups1.0-1
  kubuntu-desktop
  geogebra
  foomatic-db
  foomatic-db
  cups-pdf
  ubuntu-desktop
 |printer-driver-splix
  printer-driver-sag-gdi
 |printer-driver-sag-gdi
  printer-driver-postscript-hp
  printer-driver-min12xxw
 |printer-driver-hpijs
  printer-driver-hpcups
 |printer-driver-hpcups
  printer-driver-gutenprint
  printer-driver-foo2zjs
  printer-driver-foo2zjs
  printer-driver-c2esp
  openprinting-ppds
  openprinting-ppds
  libcupsmime1
  libcups2
  indicator-printers
  hplip
  ghostscript-cups
 |foomatic-filters
  foomatic-db-engine
  foomatic-db-engine
  foomatic-db-compressed-ppds
  foomatic-db-compressed-ppds
  cups-filters
  cups-filters
  cups-dbg
  cups-client
  cups-bsd
  bluez-cups

```

---

### Post by j88n on 2014-01-10
uname -a
```

Linux Sean-Monster 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:25:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```



lsb_release -a
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

```

---

### Post by Bashing-om on 2014-01-10
j88n; Shheesshh,
This:
Confirms what you have been telling me all along:
> 
lsb_release -a
Code:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise


And I am totally in a quandry as to why your system is looking at the quantal repositories.
Someone may have to bail me out !
Show me what the source list is.
```

cat /etc/issue
cat /etc/apt/sources.list

```
Here I have been preparing really hard, and seems I am barking up the wrong tree . Still and yet, have got to get the correct files for the correct version of your operating system and get them installed !

And I still
[INDENT][INDENT]want to know
[/INDENT][/INDENT]

---

### Post by mc4man on 2014-01-10
Did you take a 12.04.3 install & switch your sources to 12.10 in hopes of doing an upgrade thru apt-get?
or
Did you take a 12.04.3 install & begin an upgrade process to 12.10  which failed to complete successfully.? (or completed partially.

===============================================================================================================

Quite honestly i'd consider copying out data of interest & installing ubuntu again, which one,  your choice. Note that an upgrade from 12.10 to 14.04 may have issues, so if starting over choose carefully..

(- if you have data you need to save & no means to do that  then take advantage of the free 5GB ubuntuone storage

---

### Post by mc4man on 2014-01-10
Something else you could look at - 
if you don't actually have any quantal packages installed (or any that matter), then consider setting sources back to precise, enabling -proposed, updating sources & see what a **simulated **upgrade or dist-upgrade shows

---

### Post by Bashing-om on 2014-01-10
+1

---

### Post by j88n on 2014-01-10
cat /etc/issue
```

Ubuntu 12.04.3 LTS \n \l

```

cat /etc/apt/sources.list
```

deb http://archive.ubuntu.com/ubuntu quantal main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ quantal-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu quantal-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu quantal-backports universe main multiverse restricted

```

I had the base install of 12.04 and tried to upgrade (in hopes) that an upgrade would solve some of these problems... which they obviously did not.

Can you elaborate on how I can do that?

---

### Post by Bashing-om on 2014-01-10
j88n; Oh Well,

Iffen ya want to try to fix that install, might I suggest ya generate a new sources list file and we will try mc4man's suggestion to simulate the update/upgrade and see what happens.

Let's copy the present source list file;
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak

```
and get that new source list file from:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
read the instruction carefully ! .. DO NOT allow it to enable 3rd party software.

Speaking of 3rd party s/w.. what have you got on your system now in that respect ? show us :
```

cat /etc/apt/sources.list.d/*.list

```

We can look and see what might happen .. and if in a worst case scenerio, revert back to what is now.

[INDENT]prudent to look before we jump
[/INDENT]

---

### Post by j88n on 2014-01-10
cat /etc/apt/sources.list.d/*.list


deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise main universe
# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main # disabled on upgrade to quantal
# deb [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable main # disabled on upgrade to quantal
# deb [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) quantal steam # disabled on upgrade to quantal
# deb-src [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) quantal steam # disabled on upgrade to quantal
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) quantal main # disabled on upgrade to quantal
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) quantal main # disabled on upgrade to quantal
# deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) quantal main # disabled on upgrade to quantal
# deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) quantal main # disabled on upgrade to quantal

---

### Post by Bashing-om on 2014-01-10
j88n; 'Nother thought !

If you would rather, I can reboot into my 12.04 install and provide you with the sources.list from my install (??)
Might be quicker and surer !

[INDENT]do'n all I can to help
[/INDENT]

---

### Post by j88n on 2014-01-10
That might help.. I tried to create the new sources.list , but am I supposed to do after that. The new sources.list I created is below:

```
################################################################################ OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb http://02.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://02.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 


###### Ubuntu Update Repos
deb http://02.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://02.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb http://02.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb http://02.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://02.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://02.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://02.archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse 
deb-src http://02.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 


###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by Bashing-om on 2014-01-10
j88n;

> 
cat /etc/apt/sources.list.d/*.list
deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise main universe

This line will be a duplicate in any new sources.list file. Comment out that line also.
=========
We cross posted, did you see my last about using my 12.04 sources.list file ?

From the looks of that .. appears we are suffering from a failed upgrade attempt !

Movin' at the speed
[INDENT][INDENT][INDENT]of a snail
[/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-10
Sorry, I think I'm a little lost at my next steps..There is a duplicate line in which file?

If you think your sources.list might help, I will gladly take it (just in case I re-generated the new one incorrectly)

---

### Post by Bashing-om on 2014-01-10
j88n;

Lemme back out of everything and reboot, will get that file to ya.
Then we can discuss that duplication of entries.

back in a bit

---

### Post by Bashing-om on 2014-01-10
j88n; OK !

Here is my sources.list file. It had slipped my mind I had changed my mirror. Are you located in the United States ? As my Mirror is in Texas.
```

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.utexas.edu/ubuntu/ precise main restricted
deb-src http://ftp.utexas.edu/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.utexas.edu/ubuntu/ precise-updates main restricted
deb-src http://ftp.utexas.edu/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.utexas.edu/ubuntu/ precise universe
deb-src http://ftp.utexas.edu/ubuntu/ precise universe
deb http://ftp.utexas.edu/ubuntu/ precise-updates universe
deb-src http://ftp.utexas.edu/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.utexas.edu/ubuntu/ precise multiverse
deb-src http://ftp.utexas.edu/ubuntu/ precise multiverse
deb http://ftp.utexas.edu/ubuntu/ precise-updates multiverse
deb-src http://ftp.utexas.edu/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://ftp.utexas.edu/ubuntu/ precise-security main restricted
deb-src http://ftp.utexas.edu/ubuntu/ precise-security main restricted
deb http://ftp.utexas.edu/ubuntu/ precise-security universe
deb-src http://ftp.utexas.edu/ubuntu/ precise-security universe
deb http://ftp.utexas.edu/ubuntu/ precise-security multiverse
deb-src http://ftp.utexas.edu/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main

```

Copy this file to someplace safe on your system and then copy it into place  "/etc/apt/sources.list" .

Now the duplication of entries<
this from your "cat /etc/apt/sources.list.d/*.list" output
> 
cat /etc/apt/sources.list.d/*.list
deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise main universe 

already present here:
"deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) precise [color=red]main[/color] restricted"
and
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) precise [color=red]universe[/color]

so comment out that line in the directory  /etc/apt/sources.li, in whatever file it is in - will have to look for it .


EDIT: Remember to make a backup of the current file prior to copying this file into place !
Hope I am making sense.

---

### Post by j88n on 2014-01-10
Yeah, I'm in the US, but on the East Coast. I think Texas should be fine.

So I copied your contents in my sources.list file

---

### Post by j88n on 2014-01-11
I'm still trying to figure out what I need to with the duplicate entries... not really sure.

I don't see any duplicate entries, so I'm not sure what to comment out and where.

---

### Post by Bashing-om on 2014-01-11
j88n; OK ;

here goes nothing !
```

sudo apt-get -s update
sudo apt-get -s upgrade

```
the '-s' is simulate, will tell us what it would do if this were for real (and it might be next time !).

So, run those 2 commands and lets see what the package manager looks like.

[INDENT][INDENT]fingers are crossed
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-11
sudo apt-get -s update
```

Hit http://ftp.utexas.edu precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ftp.utexas.edu precise-updates Release.gpg                          
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://ftp.utexas.edu precise-security Release.gpg               
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ubuntu.mirror.cambrium.nl precise Release.gpg                       
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ftp.utexas.edu precise Release                            
Hit http://ubuntu.mirror.cambrium.nl precise Release                           
Hit http://ftp.utexas.edu precise-updates Release                              
Hit http://ubuntu.mirror.cambrium.nl precise/main amd64 Packages               
Hit http://ftp.utexas.edu precise-security Release                             
Hit http://ubuntu.mirror.cambrium.nl precise/universe amd64 Packages           
Hit http://ubuntu.mirror.cambrium.nl precise/main TranslationIndex             
Hit http://ubuntu.mirror.cambrium.nl precise/universe TranslationIndex         
Hit http://ftp.utexas.edu precise/main Sources                                 
Hit http://ubuntu.mirror.cambrium.nl precise/main Translation-en               
Hit http://ubuntu.mirror.cambrium.nl precise/universe Translation-en           
Hit http://ftp.utexas.edu precise/restricted Sources                           
Hit http://ftp.utexas.edu precise/universe Sources                    
Ign http://archive.canonical.com precise/partner Translation-en_US    
Ign http://extras.ubuntu.com precise/main Translation-en_US           
Ign http://archive.canonical.com precise/partner Translation-en       
Ign http://extras.ubuntu.com precise/main Translation-en              
Hit http://ftp.utexas.edu precise/multiverse Sources
Hit http://ftp.utexas.edu precise/main amd64 Packages
Hit http://ftp.utexas.edu precise/restricted amd64 Packages
Hit http://ftp.utexas.edu precise/universe amd64 Packages
Hit http://ftp.utexas.edu precise/multiverse amd64 Packages
Hit http://ftp.utexas.edu precise/main TranslationIndex
Hit http://ftp.utexas.edu precise/multiverse TranslationIndex
Hit http://ftp.utexas.edu precise/restricted TranslationIndex
Hit http://ftp.utexas.edu precise/universe TranslationIndex
Get:1 http://ftp.utexas.edu precise-updates/main Sources [444 kB]
Hit http://ftp.utexas.edu precise-updates/restricted Sources           
Hit http://ftp.utexas.edu precise-updates/universe Sources
Hit http://ftp.utexas.edu precise-updates/multiverse Sources
Hit http://ftp.utexas.edu precise-updates/main amd64 Packages
Hit http://ftp.utexas.edu precise-updates/restricted amd64 Packages
Hit http://ftp.utexas.edu precise-updates/universe amd64 Packages
Hit http://ftp.utexas.edu precise-updates/multiverse amd64 Packages
Hit http://ftp.utexas.edu precise-updates/main TranslationIndex
Hit http://ftp.utexas.edu precise-updates/multiverse TranslationIndex
Hit http://ftp.utexas.edu precise-updates/restricted TranslationIndex
Hit http://ftp.utexas.edu precise-updates/universe TranslationIndex
Hit http://ftp.utexas.edu precise-security/main Sources
Hit http://ftp.utexas.edu precise-security/restricted Sources
Hit http://ftp.utexas.edu precise-security/universe Sources
Hit http://ftp.utexas.edu precise-security/multiverse Sources
Hit http://ftp.utexas.edu precise-security/main amd64 Packages
Hit http://ftp.utexas.edu precise-security/restricted amd64 Packages
Hit http://ftp.utexas.edu precise-security/universe amd64 Packages
Hit http://ftp.utexas.edu precise-security/multiverse amd64 Packages
Hit http://ftp.utexas.edu precise-security/main TranslationIndex
Hit http://ftp.utexas.edu precise-security/multiverse TranslationIndex
Hit http://ftp.utexas.edu precise-security/restricted TranslationIndex
Hit http://ftp.utexas.edu precise-security/universe TranslationIndex
Hit http://ftp.utexas.edu precise/main Translation-en                          
Hit http://ftp.utexas.edu precise/multiverse Translation-en                    
Hit http://ftp.utexas.edu precise/restricted Translation-en                    
Hit http://ftp.utexas.edu precise/universe Translation-en                      
Hit http://ftp.utexas.edu precise-updates/main Translation-en                  
Hit http://ftp.utexas.edu precise-updates/multiverse Translation-en            
Hit http://ftp.utexas.edu precise-updates/restricted Translation-en            
Hit http://ftp.utexas.edu precise-updates/universe Translation-en              
Hit http://ftp.utexas.edu precise-security/main Translation-en                 
Hit http://ftp.utexas.edu precise-security/multiverse Translation-en           
Hit http://ftp.utexas.edu precise-security/restricted Translation-en           
Hit http://ftp.utexas.edu precise-security/universe Translation-en             
Fetched 1 B in 8s (0 B/s)                                                      
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ftp.utexas.edu_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.

```


Should I even bother running apt-get upgrade?

---

### Post by Bashing-om on 2014-01-11
j88n;
Well, let me see if i can find it for you.
post back the output of:
```

ls -la /etc/apt/sources.list.d

```
and we will go through the suspect files in that directory and find that entry,

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by mc4man on 2014-01-11
You don't want to simulate an update, just the upgrade (it may ignore -s for update, may not

---

### Post by j88n on 2014-01-11
total 64
drwxr-xr-x 2 root root 4096 Jan 11 00:09 .
drwxr-xr-x 6 root root 4096 Jan 10 22:09 ..
-rw-r--r-- 1 root root   67 Jan 11 00:02 cambrium_precise.list
-rw-r--r-- 1 root root   68 Jan 11 00:01 cambrium_precise.list~
-rw-r--r-- 1 root root  187 Jan  6 00:27 google-talkplugin.list
-rw-r--r-- 1 root root  117 Jan  6 00:27 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root   59 Jan  6 00:17 google-talkplugin.list.save
-rw-r--r-- 1 root root  182 Jan  6 00:27 steam.list
-rw-r--r-- 1 root root  112 Jan  6 00:27 steam.list.distUpgrade
-rw-r--r-- 1 root root  112 Jan  6 00:17 steam.list.save
-rw-r--r-- 1 root root  204 Jan  6 00:27 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  134 Jan  6 00:27 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  134 Jan  6 00:17 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root  220 Jan  6 00:27 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root  150 Jan  6 00:27 ubuntu-x-swat-x-updates-precise.list.distUpgrade
-rw-r--r-- 1 root root  150 Jan  6 00:17 ubuntu-x-swat-x-updates-precise.list.save

---

### Post by Bashing-om on 2014-01-11
j88n; Hey

Take mc4man's advise and run the update once more with out the '-s' option. IThe warning I think is just that the miror does not contain that one file at this time, not to be worried about that one at this time.
```

sudo apt-get update

```

let er rip

---

### Post by j88n on 2014-01-11
sudo apt-get update
```
Hit http://archive.canonical.com precise Release.gpgHit http://ftp.utexas.edu precise Release.gpg                                  
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ftp.utexas.edu precise-updates Release.gpg                          
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ubuntu.mirror.cambrium.nl precise Release.gpg                       
Hit http://ftp.utexas.edu precise-security Release.gpg               
Hit http://ubuntu.mirror.cambrium.nl precise Release                           
Hit http://ftp.utexas.edu precise Release                                      
Hit http://ubuntu.mirror.cambrium.nl precise/main amd64 Packages               
Hit http://ftp.utexas.edu precise-updates Release                              
Hit http://ubuntu.mirror.cambrium.nl precise/universe amd64 Packages           
Hit http://ubuntu.mirror.cambrium.nl precise/main TranslationIndex             
Hit http://ubuntu.mirror.cambrium.nl precise/universe TranslationIndex         
Hit http://ftp.utexas.edu precise-security Release                             
Hit http://ubuntu.mirror.cambrium.nl precise/main Translation-en               
Hit http://ubuntu.mirror.cambrium.nl precise/universe Translation-en           
Hit http://ftp.utexas.edu precise/main Sources                                 
Ign http://extras.ubuntu.com precise/main Translation-en_US          
Hit http://ftp.utexas.edu precise/restricted Sources
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en       
Hit http://ftp.utexas.edu precise/universe Sources                    
Hit http://ftp.utexas.edu precise/multiverse Sources
Hit http://ftp.utexas.edu precise/main amd64 Packages
Hit http://ftp.utexas.edu precise/restricted amd64 Packages
Hit http://ftp.utexas.edu precise/universe amd64 Packages
Hit http://ftp.utexas.edu precise/multiverse amd64 Packages
Hit http://ftp.utexas.edu precise/main TranslationIndex
Hit http://ftp.utexas.edu precise/multiverse TranslationIndex
Hit http://ftp.utexas.edu precise/restricted TranslationIndex
Hit http://ftp.utexas.edu precise/universe TranslationIndex
Get:1 http://ftp.utexas.edu precise-updates/main Sources [444 kB]
Hit http://ftp.utexas.edu precise-updates/restricted Sources           
Hit http://ftp.utexas.edu precise-updates/universe Sources
Hit http://ftp.utexas.edu precise-updates/multiverse Sources
Hit http://ftp.utexas.edu precise-updates/main amd64 Packages
Hit http://ftp.utexas.edu precise-updates/restricted amd64 Packages
Hit http://ftp.utexas.edu precise-updates/universe amd64 Packages
Hit http://ftp.utexas.edu precise-updates/multiverse amd64 Packages
Hit http://ftp.utexas.edu precise-updates/main TranslationIndex
Hit http://ftp.utexas.edu precise-updates/multiverse TranslationIndex
Hit http://ftp.utexas.edu precise-updates/restricted TranslationIndex
Hit http://ftp.utexas.edu precise-updates/universe TranslationIndex
Hit http://ftp.utexas.edu precise-security/main Sources
Hit http://ftp.utexas.edu precise-security/restricted Sources
Hit http://ftp.utexas.edu precise-security/universe Sources
Hit http://ftp.utexas.edu precise-security/multiverse Sources
Hit http://ftp.utexas.edu precise-security/main amd64 Packages
Hit http://ftp.utexas.edu precise-security/restricted amd64 Packages
Hit http://ftp.utexas.edu precise-security/universe amd64 Packages
Hit http://ftp.utexas.edu precise-security/multiverse amd64 Packages
Hit http://ftp.utexas.edu precise-security/main TranslationIndex
Hit http://ftp.utexas.edu precise-security/multiverse TranslationIndex         
Hit http://ftp.utexas.edu precise-security/restricted TranslationIndex         
Hit http://ftp.utexas.edu precise-security/universe TranslationIndex           
Hit http://ftp.utexas.edu precise/main Translation-en                          
Hit http://ftp.utexas.edu precise/multiverse Translation-en                    
Hit http://ftp.utexas.edu precise/restricted Translation-en                    
Hit http://ftp.utexas.edu precise/universe Translation-en                      
Hit http://ftp.utexas.edu precise-updates/main Translation-en                  
Hit http://ftp.utexas.edu precise-updates/multiverse Translation-en            
Hit http://ftp.utexas.edu precise-updates/restricted Translation-en            
Hit http://ftp.utexas.edu precise-updates/universe Translation-en              
Hit http://ftp.utexas.edu precise-security/main Translation-en                 
Hit http://ftp.utexas.edu precise-security/multiverse Translation-en           
Hit http://ftp.utexas.edu precise-security/restricted Translation-en           
Hit http://ftp.utexas.edu precise-security/universe Translation-en             
Fetched 1 B in 8s (0 B/s)                                                      
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ftp.utexas.edu_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Bashing-om on 2014-01-11
ok, let's address that duplication.
lets see :
```

ls -la /etc/apt/sources.list.d

```
should not be too tough.

no step for a stepper

---

### Post by j88n on 2014-01-11
> **Bashing-om said:**
> ok, let's address that duplication.
lets see :
```

ls -la /etc/apt/sources.list.d

```
should not be too tough.

no step for a stepper

[email]sean@Sean-Monster:/etc/apt/sources.list[/email].d$ ls -la /etc/apt/sources.list.d
total 64
drwxr-xr-x 2 root root 4096 Jan 11 00:09 .
drwxr-xr-x 6 root root 4096 Jan 10 22:09 ..
-rw-r--r-- 1 root root   67 Jan 11 00:02 cambrium_precise.list
-rw-r--r-- 1 root root   68 Jan 11 00:01 cambrium_precise.list~
-rw-r--r-- 1 root root  187 Jan  6 00:27 google-talkplugin.list
-rw-r--r-- 1 root root  117 Jan  6 00:27 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root   59 Jan  6 00:17 google-talkplugin.list.save
-rw-r--r-- 1 root root  182 Jan  6 00:27 steam.list
-rw-r--r-- 1 root root  112 Jan  6 00:27 steam.list.distUpgrade
-rw-r--r-- 1 root root  112 Jan  6 00:17 steam.list.save
-rw-r--r-- 1 root root  204 Jan  6 00:27 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  134 Jan  6 00:27 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root  134 Jan  6 00:17 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root  220 Jan  6 00:27 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root  150 Jan  6 00:27 ubuntu-x-swat-x-updates-precise.list.distUpgrade
-rw-r--r-- 1 root root  150 Jan  6 00:17 ubuntu-x-swat-x-updates-precise.list.save

---

### Post by Bashing-om on 2014-01-11
Bet it's in:
```

cat /etc/apt/sources.list.d/cambrium_precise.list

```

Will know in a tic !

---

### Post by j88n on 2014-01-11
> **Bashing-om said:**
> Bet it's in:
```

cat /etc/apt/sources.list.d/cambrium_precise.list

```

Will know in a tic !

[email]sean@Sean-Monster:/etc/apt/sources.list[/email].d$ cat /etc/apt/sources.list.d/cambrium_precise.list
deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise main universe

---

### Post by Bashing-om on 2014-01-11
j88n; yepper !

text editor -> place a comment character (#)at the start of that line to comment that entry out.

and when that is done...
let's do this!

```

sudo apt-get -s upgrade

``` and get an idea of what havoc will be wrought !

[INDENT][INDENT]fingers double crossed
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-11
okay commenting out and running the command. I guess I was confused because I only saw that line once in the file, so I didn't know it was duplicated somewhere else.

---

### Post by j88n on 2014-01-11
```

sudo apt-get -s upgrade

``` 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 bluez-cups : Depends: cups but it is not installed
 console-setup : Depends: keyboard-configuration but it is not installed
 hplip : Depends: cups (>= 1.1.20) but it is not installed
 indicator-printers : Depends: cups (>= 1.5) but it is not installed
 lirc : Depends: setserial but it is not installed
 printer-driver-gutenprint : Depends: cups (>= 1.3.0) but it is not installed
 printer-driver-hpcups : Depends: cups but it is not installed
 xserver-xorg-core-lts-raring : Depends: keyboard-configuration but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by Bashing-om on 2014-01-11
yeah the main and universe terms were already in that main sources.list file.

---------------
> 
xserver-xorg-core-lts-raring : Depends: keyboard-configuration but it is not installed


Does not look as anything has changed, but we are now on a much firmer foundation.

Ok, I have been at this keyboard for a bunch of hours, and I am beyond tired, thinking processes not doing to well.

We can pick this up in my AM .. or if our guardian angel is still looking over our shoulder, and yall feel up to it.. see about rolling xserver-xorg and xserver-common into position.

Gots to take a long break

---

### Post by j88n on 2014-01-11
Lol, yeah I  hear ya! I have an early appointment tomorrow, so I'm calling it quits for tonight.

---

### Post by Bashing-om on 2014-01-11
j88n; More fun tomorrow !

see ya !

[INDENT][INDENT]later as in later
[/INDENT][/INDENT]

---

### Post by jjclonker on 2014-01-11
I don't know how close you are to fixing this problem, but if you have no important files on your computer reinstalling ubuntu may fix your problem.;)

I am new to ubuntu as well, and I had some problems with my system and reinstalling fixed them, but if Bashing-om is coming close to a solution I would just wait for more of his help.;)

---

### Post by Bashing-om on 2014-01-11
@ jjclonker, Thanks for the vote of confidence, We are working on it, (Re-)install is the means of last resort.

@j88n; Back to work here, I am working at setting up the next series of commands to obtain and install the xserver stuff. Soon as my ducks are all in one row, I will let ya know our next step in this ongoing saga.

[INDENT][INDENT]cheers to all and to all
[INDENT][INDENT]good morning !
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jjclonker on 2014-01-11
@Bashing-om and j88n, Good luck!

Just keep pushing forward and you will prevail.

---

### Post by Bashing-om on 2014-01-11
@ mc4man; I seem to have hit a snag, HELP ,looking at:
[http://packages.ubuntu.com/search?keywords=xserver-xorg-core&searchon=names&suite=precise-updates&section=all](http://packages.ubuntu.com/search?keywords=xserver-xorg-core&searchon=names&suite=precise-updates&section=all)
It shows this:
> 
Package xserver-xorg-core

precise-updates (x11): Xorg X server - core server 
2:1.11.4-0ubuntu10.14: amd64 i386 
also provided by: xserver-xorg-core-lts-quantal, xserver-xorg-core-lts-raring, xserver-xorg-core-lts-saucy

Now my point of concern -> "also provided by: xserver-xorg-core-lts-quantal, xserver-xorg-core-lts-raring, xserver-xorg-core-lts-saucy"; does this imply that there is no need at all to downgrade the xserver stuff in our present operation to version 2:1.11.4-0ubuntu10.14 ???

Are we better off to leave well enough alone ? Try and (re)configure what is presently installed ? I am reluctant to move forward until the situation with the xserver package(s) is resolved.

As my ignorance is showing.

---

### Post by mc4man on 2014-01-11
Each point release of precise comes with a new lts version of xserver, mesa & kernel.  
(12.04.2 = quantal, 12.04.3 = raring, 12.04.4 = saucy
They aren't seen as upgradeable, if you installed 12.04.3 then the saucy~lts packages are available but aren't upgrades from the raring~lts ones.

Better to deal with these 3 mentioned packages - 
cups & setserial don't matter, I'd remove  them & then figure out the problem with keyboard-configuration ( part of console-setup source) which you do appear to need

---

### Post by Bashing-om on 2014-01-11
@ mc4man; Thanks for the clarification;
Hardware Enablement Stack at work !

Your advise is sound, We will play it like it lies.

@ j88n; When you are ready to proceed,
Let's do the upgrade for real, and set the stage for those little things.
```

sudo apt-get update
sudo apt-get upgrade

```
I expect the better course as to housecleaning is to wait to do the clean and autoclean, ect routine  at a later time, when all the dust settles.

[INDENT][INDENT]let the sun shine in
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-13
Thanks everyone for the help and support!

@bashing-om, sorry I've been afk for a while, but I'm back and ready to hit the ground running.

sudo apt-get update
```
Hit http://archive.canonical.com precise Release.gpgGet:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://ftp.utexas.edu precise Release.gpg                                 
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise/partner amd64 Packages       
Get:2 http://ftp.utexas.edu precise-updates Release.gpg [198 B]
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Ign http://archive.canonical.com precise/partner TranslationIndex     
Ign http://extras.ubuntu.com precise/main TranslationIndex            
Get:3 http://ftp.utexas.edu precise-security Release.gpg [198 B]
Hit http://ftp.utexas.edu precise Release                                      
Get:4 http://ftp.utexas.edu precise-updates Release [49.6 kB]                  
Get:5 http://ftp.utexas.edu precise-security Release [49.6 kB]                 
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en_US                 
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://ftp.utexas.edu precise/main Sources                         
Hit http://ftp.utexas.edu precise/restricted Sources
Hit http://ftp.utexas.edu precise/universe Sources
Hit http://ftp.utexas.edu precise/multiverse Sources
Hit http://ftp.utexas.edu precise/main amd64 Packages
Hit http://ftp.utexas.edu precise/restricted amd64 Packages
Hit http://ftp.utexas.edu precise/universe amd64 Packages
Hit http://ftp.utexas.edu precise/multiverse amd64 Packages
Hit http://ftp.utexas.edu precise/main TranslationIndex
Hit http://ftp.utexas.edu precise/multiverse TranslationIndex
Hit http://ftp.utexas.edu precise/restricted TranslationIndex
Hit http://ftp.utexas.edu precise/universe TranslationIndex
Get:6 http://ftp.utexas.edu precise-updates/main Sources [445 kB]
Get:7 http://ftp.utexas.edu precise-updates/restricted Sources [7,039 B]
Get:8 http://ftp.utexas.edu precise-updates/universe Sources [101 kB]  
Get:9 http://ftp.utexas.edu precise-updates/multiverse Sources [8,468 B]
Get:10 http://ftp.utexas.edu precise-updates/main amd64 Packages [741 kB]
Get:11 http://ftp.utexas.edu precise-updates/restricted amd64 Packages [11.4 kB]
Get:12 http://ftp.utexas.edu precise-updates/universe amd64 Packages [227 kB]  
Get:13 http://ftp.utexas.edu precise-updates/multiverse amd64 Packages [14.2 kB]
Get:14 http://ftp.utexas.edu precise-updates/main TranslationIndex [3,564 B]   
Get:15 http://ftp.utexas.edu precise-updates/multiverse TranslationIndex [2,605 B]
Get:16 http://ftp.utexas.edu precise-updates/restricted TranslationIndex [2,461 B]
Get:17 http://ftp.utexas.edu precise-updates/universe TranslationIndex [2,850 B]
Get:18 http://ftp.utexas.edu precise-security/main Sources [95.7 kB]           
Get:19 http://ftp.utexas.edu precise-security/restricted Sources [2,494 B]     
Get:20 http://ftp.utexas.edu precise-security/universe Sources [29.9 kB]       
Get:21 http://ftp.utexas.edu precise-security/multiverse Sources [1,792 B]     
Get:22 http://ftp.utexas.edu precise-security/main amd64 Packages [355 kB]     
Get:23 http://ftp.utexas.edu precise-security/restricted amd64 Packages [4,627 B]
Get:24 http://ftp.utexas.edu precise-security/universe amd64 Packages [86.7 kB]
Get:25 http://ftp.utexas.edu precise-security/multiverse amd64 Packages [2,446 B]
Get:26 http://ftp.utexas.edu precise-security/main TranslationIndex [74 B]     
Get:27 http://ftp.utexas.edu precise-security/multiverse TranslationIndex [72 B]
Get:28 http://ftp.utexas.edu precise-security/restricted TranslationIndex [72 B]
Get:29 http://ftp.utexas.edu precise-security/universe TranslationIndex [73 B] 
Hit http://ftp.utexas.edu precise/main Translation-en                          
Hit http://ftp.utexas.edu precise/multiverse Translation-en                    
Hit http://ftp.utexas.edu precise/restricted Translation-en                    
Hit http://ftp.utexas.edu precise/universe Translation-en                      
Get:30 http://ftp.utexas.edu precise-updates/main Translation-en [332 kB]      
Hit http://ftp.utexas.edu precise-updates/multiverse Translation-en            
Hit http://ftp.utexas.edu precise-updates/restricted Translation-en            
Get:31 http://ftp.utexas.edu precise-updates/universe Translation-en [134 kB]  
Get:32 http://ftp.utexas.edu precise-security/main Translation-en [167 kB]     
Hit http://ftp.utexas.edu precise-security/multiverse Translation-en           
Hit http://ftp.utexas.edu precise-security/restricted Translation-en           
Hit http://ftp.utexas.edu precise-security/universe Translation-en             
Fetched 2,877 kB in 16s (177 kB/s)                                             
Reading package lists... Done

```

sudo apt-get upgrade
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 bluez-cups : Depends: cups but it is not installed
 console-setup : Depends: keyboard-configuration but it is not installed
 hplip : Depends: cups (>= 1.1.20) but it is not installed
 indicator-printers : Depends: cups (>= 1.5) but it is not installed
 lirc : Depends: setserial but it is not installed
 printer-driver-gutenprint : Depends: cups (>= 1.3.0) but it is not installed
 printer-driver-hpcups : Depends: cups but it is not installed
 xserver-xorg-core-lts-raring : Depends: keyboard-configuration but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by Bashing-om on 2014-01-14
j88n; Missed ya, kept an eye out for ya,

OK, Look'n good !
Try this and see what results :
```

sudo apt-get install keyboard-configuration

```
Depending on how this goes, we will look at "setserial" next.

[INDENT][INDENT]struggling merrily along
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-14
sean@Sean-Monster:~$ sudo apt-get install keyboard-configuration
[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bluez-cups : Depends: cups but it is not going to be installed
 hplip : Depends: cups (>= 1.1.20) but it is not going to be installed
 indicator-printers : Depends: cups (>= 1.5) but it is not going to be installed
 lirc : Depends: setserial but it is not going to be installed
 printer-driver-gutenprint : Depends: cups (>= 1.3.0) but it is not going to be installed
 printer-driver-hpcups : Depends: cups but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
sean@Sean-Monster:~$

---

### Post by Bashing-om on 2014-01-14
j88n; Yuk !

Not what I wanted to see !

OK - I don't think will have good result - but let's take the package manager's advise, seeing as how we are now up on precise repository.
```

sudo apt-get -f install

```
When that fails, try:
```

sudo apt-get -f install --fix-broken
dpkg-reconfigure -a

```

see where this points us to.

[INDENT][INDENT]when in doubt,
[INDENT][INDENT][INDENT]punt
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-14
sudo apt-get -f install

```
sean@Sean-Monster:~$ sudo apt-get -f install[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpam-winbind libnet-ssleay-perl ttf-umefont gnome-exe-thumbnailer
  gir1.2-ubuntuoneui-3.0 liburi-perl libhtml-parser-perl libhttp-daemon-perl
  libfont-afm-perl libhttp-negotiate-perl libfile-listing-perl
  libhtml-form-perl libcapi20-3 libhtml-tree-perl libencode-locale-perl
  libhttp-date-perl libmailtools-perl wine-gecko2.24
  liblwp-protocol-https-perl wine-gecko1.4 libhttp-cookies-perl winetricks
  libosmesa6 libhttp-message-perl libnet-http-perl icoutils wine-mono4.5.2
  libhtml-format-perl libubuntuoneui-3.0-1 libsocket6-perl ttf-unfonts-core
  libmpg123-0 thunderbird-globalmenu libhtml-tagset-perl libwww-perl winbind
  fonts-droid libio-socket-ssl-perl libwww-robotrules-perl
  liblwp-mediatypes-perl ttf-droid libio-socket-inet6-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cups keyboard-configuration setserial
Suggested packages:
  cups-pdf
The following NEW packages will be installed:
  cups keyboard-configuration setserial
0 upgraded, 3 newly installed, 0 to remove and 71 not upgraded.
Need to get 1,863 kB of archives.
After this operation, 6,698 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.utexas.edu/ubuntu/ precise-updates/main cups amd64 1.5.3-0ubuntu8 [1,299 kB]
Get:2 http://ftp.utexas.edu/ubuntu/ precise/main keyboard-configuration all 1.70ubuntu5 [523 kB]
Get:3 http://ftp.utexas.edu/ubuntu/ precise/main setserial amd64 2.17-46 [40.6 kB]
Fetched 1,863 kB in 3s (516 kB/s) 
Preconfiguring packages ...
Bus error (core dumped)
cups failed to preconfigure, with exit status 135
Bus error (core dumped)
keyboard-configuration failed to preconfigure, with exit status 135
Bus error (core dumped)
setserial failed to preconfigure, with exit status 135
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

sudo apt-get -f install --fix-broken
```
sean@Sean-Monster:~$ sudo apt-get -f install --fix-brokenReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpam-winbind libnet-ssleay-perl ttf-umefont gnome-exe-thumbnailer
  gir1.2-ubuntuoneui-3.0 liburi-perl libhtml-parser-perl libhttp-daemon-perl
  libfont-afm-perl libhttp-negotiate-perl libfile-listing-perl
  libhtml-form-perl libcapi20-3 libhtml-tree-perl libencode-locale-perl
  libhttp-date-perl libmailtools-perl wine-gecko2.24
  liblwp-protocol-https-perl wine-gecko1.4 libhttp-cookies-perl winetricks
  libosmesa6 libhttp-message-perl libnet-http-perl icoutils wine-mono4.5.2
  libhtml-format-perl libubuntuoneui-3.0-1 libsocket6-perl ttf-unfonts-core
  libmpg123-0 thunderbird-globalmenu libhtml-tagset-perl libwww-perl winbind
  fonts-droid libio-socket-ssl-perl libwww-robotrules-perl
  liblwp-mediatypes-perl ttf-droid libio-socket-inet6-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cups keyboard-configuration setserial
Suggested packages:
  cups-pdf
The following NEW packages will be installed:
  cups keyboard-configuration setserial
0 upgraded, 3 newly installed, 0 to remove and 71 not upgraded.
Need to get 0 B/1,863 kB of archives.
After this operation, 6,698 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Bus error (core dumped) 
cups failed to preconfigure, with exit status 135
Bus error (core dumped)
keyboard-configuration failed to preconfigure, with exit status 135
Bus error (core dumped)
setserial failed to preconfigure, with exit status 135
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

sudo dpkg-reconfigure -a

```
sean@Sean-Monster:~$ sudo dpkg-reconfigure -a/usr/sbin/dpkg-reconfigure: accountsservice is not installed

```

---

### Post by Bashing-om on 2014-01-14
j88n;

Well 2 steps forward and still in the same position. "keyboard-configuration failed to preconfigure, with exit status 135
Bus error (core dumped)"

It is back to the drawing board for me, and it is my witching hour. I am done for this session.

I have chores to get done tomorrow, so will be in my eve before I can get back to the keyboard.
Allow me to stew on this and I will get back at you.

[INDENT][INDENT]for sure,
[INDENT][INDENT][INDENT]it has my interest
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-01-14
j88n; Hey,

Have not done my homework yet, while I am looking;
What returns from:
```

apt-get purge cups
```
If the purge runs clean:
```

apt-get install cups

```

We fix all things,
[INDENT][INDENT]broken hearts takes a while 
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-14
Still no luck......

sudo apt-get purge cups
```
sean@Sean-Monster:~$ sudo apt-get purge cups[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cups is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bluez-cups : Depends: cups but it is not going to be installed
 console-setup : Depends: keyboard-configuration but it is not going to be installed
 hplip : Depends: cups (>= 1.1.20) but it is not going to be installed
 indicator-printers : Depends: cups (>= 1.5) but it is not going to be installed
 lirc : Depends: setserial but it is not going to be installed
 printer-driver-gutenprint : Depends: cups (>= 1.3.0) but it is not going to be installed
 printer-driver-hpcups : Depends: cups but it is not going to be installed
 xserver-xorg-core-lts-raring : Depends: keyboard-configuration but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2014-01-14
j88n; Curiouser and curiouser !

Why does the package manager insist that cups is not installed, when it is ?
Not to this time making much sense to me, and not making any headway either for "exit status 135".

More looking to see if we can find where the problem is, still using cups as our reference.
```

cat /var/lib/dpkg/status ##the stanza for cups is what, now ?
cat /var/lib/dpkg/info/cups.list
cat /var/lib/apt/extended_states ##the stanza for cups is what ?
cat /var/lib/dpkg/info/cups.prerm

```

See if we can not find some way to install cups, and move on . Failing this, will see about "find"ing the cups files !

[INDENT][INDENT]sometimes I wonder
 [/INDENT][/INDENT]

---

### Post by j88n on 2014-01-14
cat /var/lib/dpkg/status

The output got cut off...
```
Package: libcupsimage2Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 217
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: cups
Version: 1.5.3-0ubuntu8
Depends: libc6 (>= 2.14), libcups2 (>= 1.4.0), libjpeg8 (>= 8c), libpng12-0 (>= 1.2.13-4), libtiff4
Pre-Depends: multiarch-support
Description: Common UNIX Printing System(tm) - Raster image library
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the image libraries for handling the CUPS
 raster format.
Homepage: http://www.cups.org
Original-Maintainer: Debian CUPS Maintainers <pkg-cups-devel@lists.alioth.debian.org>


Package: libsyncdaemon-1.0-1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 173
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: ubuntuone-client
Version: 3.0.2-0ubuntu2
Replaces: ubuntuone-client (<< 1.3.0)
Depends: libc6 (>= 2.2.5), libdbus-glib-1-2 (>= 0.78), libglib2.0-0 (>= 2.24.0), ubuntuone-client (>= 3.0.2-0ubuntu2)
Suggests: ubuntuone-client-dbg
Breaks: ubuntuone-client (<< 1.3.0)
Description: Ubuntu One synchronization daemon library
 Ubuntu One is a suite of on-line services. This package provides the C
 library for the Ubuntu One file storage and sharing synchronization daemon.
Homepage: https://one.ubuntu.com
Original-Maintainer: Rick McBride <rick.mcbride@canonical.com>


Package: checkbox-qt
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 279
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: checkbox
Version: 0.13.10
Depends: checkbox (>= 0.13.10), libqtgui4, libqt4-dbus
Description: QT4 interface for checkbox
 This project provides an extensible interface for system testing. The
 results can then be sent to Launchpad.
 .
 This package provides a QT4 interface for answering tests.


Package: libgroovy1.7.2-java
Status: install ok installed
Priority: optional
Section: java
Installed-Size: 9752
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: groovy1.7.2
Version: 1.7.2-1
Depends: antlr, libasm3-java, libbsf-java, libcommons-cli-java (>= 1.0), libcommons-logging-java (>= 1.0.3), junit4, libmockobjects-java (>= 0.09), libregexp-java (>= 1.2), libservlet2.5-java, libjline-java, libxstream-java, ivy
Suggests: ant (>= 1.7.1)
Description: Agile dynamic language for the Java Virtual Machine
 Groovy is an agile dynamic language for the JVM combining lots of great
 features from languages like Python, Ruby and Smalltalk and making them
 available to the Java developers using a Java-like syntax.
 .
 Groovy is designed to help you get things done on the Java platform in a
 quicker, more concise and fun way - bringing the power of Python and Ruby
 inside the Java platform.
 .
 Groovy can be used as an alternative compiler to javac to generate
 standard Java bytecode to be used by any Java project or it can be used
 dynamically as an alternative language such as for scripting Java objects,
 templating or writing unit test cases.
 .
 The groovy API broke between 1.7.2 and 1.7.3 in a way that affects
 Eucalyptus. The latest version of the groovy 1.7 series is 1.7.10.
Original-Maintainer: Debian Java Maintainers <pkg-java-maintainers@lists.alioth.debian.org>
Homepage: http://groovy.codehaus.org/


Package: protobuf-compiler
Status: install ok installed
Priority: extra
Section: devel
Installed-Size: 101
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: protobuf
Version: 2.4.1-1ubuntu2
Depends: libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libprotoc7 (= 2.4.1-1ubuntu2), libstdc++6 (>= 4.1.1)
Description: compiler for protocol buffer definition files
 Protocol buffers are a flexible, efficient, automated mechanism for
 serializing structured data - similar to XML, but smaller, faster, and
 simpler. You define how you want your data to be structured once, then you can
 use special generated source code to easily write and read your structured
 data to and from a variety of data streams and using a variety of languages.
 You can even update your data structure without breaking deployed programs
 that are compiled against the "old" format.
 .
 Google uses Protocol Buffers for almost all of its internal RPC protocols and
 file formats.
 .
 This package contains the protocol buffer compiler that is used for
 translating from .proto files (containing the definitions) to the language
 binding for the supported languages.
Homepage: http://code.google.com/p/protobuf/
Original-Maintainer: Iustin Pop <iustin@debian.org>


Package: growisofs
Status: install ok installed
Priority: optional
Section: video
Installed-Size: 212
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: dvd+rw-tools
Version: 7.1-10
Replaces: dvd+rw-tools (<< 7.1-9)
Depends: libc6 (>= 2.4), libstdc++6 (>= 4.1.1)
Breaks: dvd+rw-tools (<< 7.1-9)
Description: DVD+-RW/R recorder
 growisofs is a general purpose DVD recording program that supports:
 .
  * random-access media (DVD+RW, DVD-RAM, plain files, hard disk partitions)
  * mastering multisession DVD media (DVD+R, DVD-R/-RW, and Blu-ray Disc)
  * first-/single-session recording of arbitrary pre-mastered image
    (formatted as UDF, ISO9660 or any other file system, if formatted at
    all) to all supported DVD media types.
 .
 growisofs is able to either write pre-created ISO images or create them
 on-the-fly (by calling genisoimage).
 .
 This package also contains dvd+rw-format, a utility to format a DVD+RW media.
Original-Maintainer: Optical Media Tools Team <pkg-opt-media-team@lists.alioth.debian.org>
Homepage: http://fy.chalmers.se/~appro/linux/DVD+RW/


Package: usbmuxd
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 126
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.0.7-2ubuntu0.1
Depends: libc6 (>= 2.14), libplist1 (>= 0.16), libusb-1.0-0 (>= 2:1.0.9~rc3), libusbmuxd1 (>= 1.0.0), adduser
Description: USB multiplexor daemon for iPhone and iPod Touch devices
 usbmuxd, the USB multiplexor daemon, is in charge of coordinating
 access to iPhone and iPod Touch services over USB. Synchronization and
 management applications for the iPhone and iPod Touch need this daemon
 to communicate with such devices concurrently.
 .
 This package includes udev rules to start the daemon when a supported
 device is plugged in, and stop it when all devices are removed.
Homepage: http://marcansoft.com/blog/iphonelinux/usbmuxd/
Original-Maintainer: gtkpod Maintainers <pkg-gtkpod-devel@lists.alioth.debian.org>


Package: libwrap0
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 148
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: tcp-wrappers
Version: 7.6.q-21
Replaces: tcpd (<< 7.6.q-20)
Depends: libc6 (>= 2.11)
Pre-Depends: multiarch-support
Recommends: tcpd
Breaks: tcpd (<< 7.6.q-20)
Description: Wietse Venema's TCP wrappers library
 Wietse Venema's network logger, also known as TCPD or LOG_TCP.
 .
 These programs log the client host name of incoming telnet,
 ftp, rsh, rlogin, finger etc. requests.
 .
 Security options are:
  - access control per host, domain and/or service;
  - detection of host name spoofing or host address spoofing;
  - booby traps to implement an early-warning system.
Original-Maintainer: Marco d'Itri <md@linux.it>


Package: libwrap0
Status: deinstall ok config-files
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 148
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: tcp-wrappers
Version: 7.6.q-21
Config-Version: 7.6.q-21
Replaces: tcpd (<< 7.6.q-20)
Depends: libc6 (>= 2.11)
Pre-Depends: multiarch-support
Recommends: tcpd
Breaks: tcpd (<< 7.6.q-20)
Description: Wietse Venema's TCP wrappers library
 Wietse Venema's network logger, also known as TCPD or LOG_TCP.
 .
 These programs log the client host name of incoming telnet,
 ftp, rsh, rlogin, finger etc. requests.
 .
 Security options are:
  - access control per host, domain and/or service;
  - detection of host name spoofing or host address spoofing;
  - booby traps to implement an early-warning system.
Original-Maintainer: Marco d'Itri <md@linux.it>


Package: libkrb5-3
Status: install ok installed
Multi-Arch: same
Priority: standard
Section: libs
Installed-Size: 959
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: krb5
Version: 1.10+dfsg~beta1-2ubuntu0.3
Replaces: libkrb53 (<< 1.6.dfsg.4~beta1-7)
Depends: libc6 (>= 2.14), libcomerr2 (>= 1.34), libk5crypto3 (>= 1.9+dfsg~beta1), libkeyutils1, libkrb5support0 (= 1.10+dfsg~beta1-2ubuntu0.3)
Pre-Depends: multiarch-support
Recommends: krb5-locales
Suggests: krb5-doc, krb5-user
Breaks: libkrb53 (<< 1.6.dfsg.4~beta1-9), libsmbclient (<= 2:3.6.1-2), sssd (<= 1.2.1-4.3)
Description: MIT Kerberos runtime libraries
 Kerberos is a system for authenticating users and services on a network.
 Kerberos is a trusted third-party service.  That means that there is a
 third party (the Kerberos server) that is trusted by all the entities on
 the network (users and services, usually called "principals").
 .
 This is the MIT reference implementation of Kerberos V5.
 .
 This package contains the runtime library for the main Kerberos v5 API
 used by applications and Kerberos clients.
Homepage: http://web.mit.edu/kerberos/
Original-Maintainer: Sam Hartman <hartmans@debian.org>


Package: libkrb5-3
Status: deinstall ok config-files
Multi-Arch: same
Priority: standard
Section: libs
Installed-Size: 957
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: krb5
Version: 1.10+dfsg~beta1-2ubuntu0.3
Config-Version: 1.10+dfsg~beta1-2ubuntu0.3
Replaces: libkrb53 (<< 1.6.dfsg.4~beta1-7)
Depends: libc6 (>= 2.9), libcomerr2 (>= 1.34), libk5crypto3 (>= 1.9+dfsg~beta1), libkeyutils1, libkrb5support0 (= 1.10+dfsg~beta1-2ubuntu0.3)
Pre-Depends: multiarch-support
Recommends: krb5-locales
Suggests: krb5-doc, krb5-user
Breaks: libkrb53 (<< 1.6.dfsg.4~beta1-9), libsmbclient (<= 2:3.6.1-2), sssd (<= 1.2.1-4.3)
Description: MIT Kerberos runtime libraries
 Kerberos is a system for authenticating users and services on a network.
 Kerberos is a trusted third-party service.  That means that there is a
 third party (the Kerberos server) that is trusted by all the entities on
 the network (users and services, usually called "principals").
 .
 This is the MIT reference implementation of Kerberos V5.
 .
 This package contains the runtime library for the main Kerberos v5 API
 used by applications and Kerberos clients.
Homepage: http://web.mit.edu/kerberos/
Original-Maintainer: Sam Hartman <hartmans@debian.org>


Package: lsof
Status: install ok installed
Priority: standard
Section: utils
Installed-Size: 452
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 4.81.dfsg.1-1build1
Replaces: lsof-2.0.35, lsof-2.0.36, lsof-2.0.38, lsof-2.2 (<< 4.73)
Depends: libc6 (>= 2.11)
Conflicts: suidmanager (<< 0.50)
Description: List open files
 Lsof is a Unix-specific diagnostic tool.  Its name stands
 for LiSt Open Files, and it does just that.  It lists
 information about any files that are open, by processes
 currently running on the system.
Original-Maintainer: Norbert Tretkowski <nobse@debian.org>


Package: pulseaudio-module-bluetooth
Status: install ok installed
Priority: extra
Section: sound
Installed-Size: 303
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: pulseaudio
Version: 1:1.1-0ubuntu15.4
Depends: libbluetooth3 (>= 4.91), libc6 (>= 2.15), libdbus-1-3 (>= 1.0.2), libpulse0 (>= 1:1.1-0ubuntu15.4), pulseaudio
Conflicts: pulseaudio (<< 0.9.14-2)
Description: Bluetooth module for PulseAudio sound server
 PulseAudio, previously known as Polypaudio, is a sound server for POSIX and
 WIN32 systems. It is a drop in replacement for the ESD sound server with
 much better latency, mixing/re-sampling quality and overall architecture.
 .
 This module enables PulseAudio to work with bluetooth devices, like headset
 or audio gateway.
 .
 The module is called module-bluetooth
Homepage: http://www.pulseaudio.org
Original-Maintainer: Pulseaudio maintenance team <pkg-pulseaudio-devel@lists.alioth.debian.org>


Package: libghc-crypto-api-prof
Status: install ok installed
Priority: extra
Section: haskell
Installed-Size: 8697
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: haskell-crypto-api
Version: 0.9-1
Provides: libghc-crypto-api-prof-0.9-abdf1
Depends: libghc-crypto-api-dev (= 0.9-1), libghc-array-prof-0.4.0.0-59d1c, libghc-base-prof-4.5.0.0-40b99, libghc-bytestring-prof-0.9.2.1-18f26, libghc-cereal-prof-0.3.5.1-c85af, libghc-entropy-prof-0.2.1-fb9e5, libghc-largeword-prof-1.0.1-1566c, libghc-tagged-prof-0.2.3.1-3ea34
Description: generic interface for cryptographic operations; profiling libraries
 This package provides a library for the Haskell programming language,
 compiled for profiling.
 See http://www.haskell.org/ for more information on Haskell.
 .
 A generic interface for cryptographic operations, platform independent
 quality RNG, property tests and known-answer tests (KATs) for common
 algorithms, and a basic benchmark infrastructure. Maintainers of hash
 and cipher implementations are encouraged to add instances for the
 classes defined in Crypto.Classes. Crypto users are similarly
 encouraged to use the interfaces defined in the Classes module. Any
 concepts or functions of general use to more than one cryptographic
 algorithm (ex: padding) is within scope of this package.
Original-Maintainer: Debian Haskell Group <pkg-haskell-maintainers@lists.alioth.debian.org>
Homepage: http://hackage.haskell.org/package/crypto-api


Package: liblockfile1
Status: install ok installed
Multi-Arch: same
Priority: standard
Section: libs
Installed-Size: 56
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: liblockfile
Version: 1.09-3ubuntu0.1
Depends: libc6 (>= 2.4), liblockfile-bin (>= 1.09-3ubuntu0.1)
Pre-Depends: multiarch-support
Description: NFS-safe locking library
 Liblockfile is a shared library with NFS-safe locking functions.
Original-Maintainer: Miquel van Smoorenburg <miquels@cistron.nl>


Package: libxau6
Status: install ok installed
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 54
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: libxau
Version: 1:1.0.6-4
Depends: libc6 (>= 2.4)
Pre-Depends: multiarch-support
Description: X11 authorisation library
 This package provides the main interface to the X11 authorisation handling,
 which controls authorisation for X connections, both client-side and
 server-side.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This module can be found at
 git://anongit.freedesktop.org/git/xorg/lib/libXau
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>


Package: libxau6
Status: deinstall ok config-files
Multi-Arch: same
Priority: optional
Section: libs
Installed-Size: 53
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libxau
Version: 1:1.0.6-4
Config-Version: 1:1.0.6-4
Depends: libc6 (>= 2.4)
Pre-Depends: multiarch-support
Description: X11 authorisation library
 This package provides the main interface to the X11 authorisation handling,
 which controls authorisation for X connections, both client-side and
 server-side.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This module can be found at
 git://anongit.freedesktop.org/git/xorg/lib/libXau
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>


Package: libghc-stm-dev
Status: install ok installed
Priority: extra
Section: haskell
Installed-Size: 307
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: haskell-stm
Version: 2.2.0.1-2
Provides: libghc-stm-dev-2.2.0.1-91af7
Depends: libghc-array-dev-0.4.0.0-59d1c, libghc-base-dev-4.5.0.0-40b99, libc6 (>= 2.15)
Suggests: libghc-stm-doc, libghc-stm-prof
Description: Haskell Software Transactional Memory library for GHC
 This package provides a library for the Haskell programming language.
 See http://www.haskell.org/ for more information on Haskell.
 .
 Provides a Haskell Software Transactional Memory (STM) library.
 STM is a modular composable concurrency abstraction.
Original-Maintainer: Debian Haskell Group <pkg-haskell-maintainers@lists.alioth.debian.org>
Homepage: http://hackage.haskell.org/package/stm


Package: gnome-power-manager
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 1580
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 3.4.0-0ubuntu1.1
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libglib2.0-0 (>= 2.31.18), libgtk-3-0 (>= 3.3.8), libpango1.0-0 (>= 1.18.0), libupower-glib1 (>= 0.9.1), dconf-gsettings-backend | gsettings-backend, notification-daemon, dbus-x11, consolekit, upower, gnome-settings-daemon (>= 3.2)
Suggests: policykit-1
Breaks: gnome-session (<< 2.28)
Description: power management tool for the GNOME desktop
 GNOME Power Manager is a session daemon for the GNOME desktop
 that takes care of system or desktop events related to power, and
 triggers actions accordingly. Its philosophy is to completely hide
 these complex tasks and only show some settings important to the user.
 .
 GNOME power manager displays and manages battery status, power plug
 events, display brightness, CPU, graphics card and hard disk drive
 power saving, and can trigger suspend-to-RAM, hibernate or shutdown
 events, all integrated to other components of the GNOME desktop.
Homepage: http://www.gnome.org/projects/gnome-power-manager/
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>


Package: libxcomposite-dev
Status: install ok installed
Priority: optional
Section: libdevel
Installed-Size: 84
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: libxcomposite
Version: 1:0.4.3-2build1
Depends: libxcomposite1 (= 1:0.4.3-2build1), libx11-dev, libxfixes-dev, x11proto-composite-dev (>= 1:0.4), x11proto-core-dev, libxext-dev
Description: X11 Composite extension library (development headers)
 libXcomposite provides an X Window System client interface to the Composite
 extension to the X protocol.
 .
 The Composite extension allows clients called compositing managers to control
 the final drawing of the screen.  Rendering is done into an off-screen buffer.
 .
 This package contains the development headers for the library found in
 libxcomposite1.  Non-developers likely have little use for this package.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This module can be found at
 git://anongit.freedesktop.org/git/xorg/lib/libXcomposite
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

```

cat /var/lib/dpkg/info/cups.list
...this output got cut off too
```
/usr/share/cups/templates/pl/subscription-added.tmpl/usr/share/cups/templates/pl/printer-jobs-header.tmpl
/usr/share/cups/templates/pl/samba-exported.tmpl
/usr/share/cups/templates/pl/printer-modified.tmpl
/usr/share/cups/templates/pl/restart.tmpl
/usr/share/cups/templates/pl/job-release.tmpl
/usr/share/cups/templates/pl/modify-class.tmpl
/usr/share/cups/templates/pl/edit-config.tmpl
/usr/share/cups/templates/pl/class-added.tmpl
/usr/share/cups/templates/pl/printer-default.tmpl
/usr/share/cups/templates/pl/printer-start.tmpl
/usr/share/cups/templates/pl/class-confirm.tmpl
/usr/share/cups/templates/pl/search.tmpl
/usr/share/cups/templates/pl/modify-printer.tmpl
/usr/share/cups/templates/pl/job-moved.tmpl
/usr/share/cups/templates/pl/samba-export.tmpl
/usr/share/cups/templates/pl/norestart.tmpl
/usr/share/cups/templates/pl/help-printable.tmpl
/usr/share/cups/templates/pl/printer-added.tmpl
/usr/share/cups/templates/pl/set-printer-options-trailer.tmpl
/usr/share/cups/templates/pl/printer-stop.tmpl
/usr/share/cups/templates/pl/choose-model.tmpl
/usr/share/cups/templates/pl/option-pickmany.tmpl
/usr/share/cups/templates/printer-accept.tmpl
/usr/share/cups/templates/classes.tmpl
/usr/share/cups/templates/option-boolean.tmpl
/usr/share/cups/templates/eu
/usr/share/cups/templates/eu/choose-make.tmpl
/usr/share/cups/templates/eu/pager.tmpl
/usr/share/cups/templates/eu/printer-confirm.tmpl
/usr/share/cups/templates/eu/jobs.tmpl
/usr/share/cups/templates/eu/job-cancel.tmpl
/usr/share/cups/templates/eu/classes-header.tmpl
/usr/share/cups/templates/eu/trailer.tmpl
/usr/share/cups/templates/eu/printer.tmpl
/usr/share/cups/templates/eu/set-printer-options-header.tmpl
/usr/share/cups/templates/eu/printers-header.tmpl
/usr/share/cups/templates/eu/class-jobs-header.tmpl
/usr/share/cups/templates/eu/printer-deleted.tmpl
/usr/share/cups/templates/eu/jobs-header.tmpl
/usr/share/cups/templates/eu/help-trailer.tmpl
/usr/share/cups/templates/eu/list-available-printers.tmpl
/usr/share/cups/templates/eu/add-printer.tmpl
/usr/share/cups/templates/eu/help-header.tmpl
/usr/share/cups/templates/eu/error-op.tmpl
/usr/share/cups/templates/eu/choose-serial.tmpl
/usr/share/cups/templates/eu/option-pickone.tmpl
/usr/share/cups/templates/eu/choose-uri.tmpl
/usr/share/cups/templates/eu/header.tmpl
/usr/share/cups/templates/eu/class-modified.tmpl
/usr/share/cups/templates/eu/job-restart.tmpl
/usr/share/cups/templates/eu/error.tmpl
/usr/share/cups/templates/eu/printer-reject.tmpl
/usr/share/cups/templates/eu/test-page.tmpl
/usr/share/cups/templates/eu/option-header.tmpl
/usr/share/cups/templates/eu/add-rss-subscription.tmpl
/usr/share/cups/templates/eu/add-class.tmpl
/usr/share/cups/templates/eu/choose-device.tmpl
/usr/share/cups/templates/eu/job-hold.tmpl
/usr/share/cups/templates/eu/option-conflict.tmpl
/usr/share/cups/templates/eu/class-deleted.tmpl
/usr/share/cups/templates/eu/printer-configured.tmpl
/usr/share/cups/templates/eu/option-trailer.tmpl
/usr/share/cups/templates/eu/printer-purge.tmpl
/usr/share/cups/templates/eu/command.tmpl
/usr/share/cups/templates/eu/job-move.tmpl
/usr/share/cups/templates/eu/printers.tmpl
/usr/share/cups/templates/eu/subscription-canceled.tmpl
/usr/share/cups/templates/eu/users.tmpl
/usr/share/cups/templates/eu/admin.tmpl
/usr/share/cups/templates/eu/class.tmpl
/usr/share/cups/templates/eu/printer-accept.tmpl
/usr/share/cups/templates/eu/classes.tmpl
/usr/share/cups/templates/eu/option-boolean.tmpl
/usr/share/cups/templates/eu/subscription-added.tmpl
/usr/share/cups/templates/eu/printer-jobs-header.tmpl
/usr/share/cups/templates/eu/samba-exported.tmpl
/usr/share/cups/templates/eu/printer-modified.tmpl
/usr/share/cups/templates/eu/restart.tmpl
/usr/share/cups/templates/eu/job-release.tmpl
/usr/share/cups/templates/eu/modify-class.tmpl
/usr/share/cups/templates/eu/edit-config.tmpl
/usr/share/cups/templates/eu/class-added.tmpl
/usr/share/cups/templates/eu/printer-default.tmpl
/usr/share/cups/templates/eu/printer-start.tmpl
/usr/share/cups/templates/eu/class-confirm.tmpl
/usr/share/cups/templates/eu/search.tmpl
/usr/share/cups/templates/eu/modify-printer.tmpl
/usr/share/cups/templates/eu/job-moved.tmpl
/usr/share/cups/templates/eu/samba-export.tmpl
/usr/share/cups/templates/eu/norestart.tmpl
/usr/share/cups/templates/eu/help-printable.tmpl
/usr/share/cups/templates/eu/printer-added.tmpl
/usr/share/cups/templates/eu/set-printer-options-trailer.tmpl
/usr/share/cups/templates/eu/printer-stop.tmpl
/usr/share/cups/templates/eu/choose-model.tmpl
/usr/share/cups/templates/eu/option-pickmany.tmpl
/usr/share/cups/templates/de
/usr/share/cups/templates/de/choose-make.tmpl
/usr/share/cups/templates/de/pager.tmpl
/usr/share/cups/templates/de/printer-confirm.tmpl
/usr/share/cups/templates/de/jobs.tmpl
/usr/share/cups/templates/de/job-cancel.tmpl
/usr/share/cups/templates/de/classes-header.tmpl
/usr/share/cups/templates/de/trailer.tmpl
/usr/share/cups/templates/de/printer.tmpl
/usr/share/cups/templates/de/set-printer-options-header.tmpl
/usr/share/cups/templates/de/printers-header.tmpl
/usr/share/cups/templates/de/class-jobs-header.tmpl
/usr/share/cups/templates/de/printer-deleted.tmpl
/usr/share/cups/templates/de/jobs-header.tmpl
/usr/share/cups/templates/de/help-trailer.tmpl
/usr/share/cups/templates/de/list-available-printers.tmpl
/usr/share/cups/templates/de/add-printer.tmpl
/usr/share/cups/templates/de/help-header.tmpl
/usr/share/cups/templates/de/error-op.tmpl
/usr/share/cups/templates/de/choose-serial.tmpl
/usr/share/cups/templates/de/option-pickone.tmpl
/usr/share/cups/templates/de/choose-uri.tmpl
/usr/share/cups/templates/de/header.tmpl
/usr/share/cups/templates/de/class-modified.tmpl
/usr/share/cups/templates/de/job-restart.tmpl
/usr/share/cups/templates/de/error.tmpl
/usr/share/cups/templates/de/printer-reject.tmpl
/usr/share/cups/templates/de/test-page.tmpl
/usr/share/cups/templates/de/option-header.tmpl
/usr/share/cups/templates/de/add-rss-subscription.tmpl
/usr/share/cups/templates/de/add-class.tmpl
/usr/share/cups/templates/de/choose-device.tmpl
/usr/share/cups/templates/de/job-hold.tmpl
/usr/share/cups/templates/de/option-conflict.tmpl
/usr/share/cups/templates/de/class-deleted.tmpl
/usr/share/cups/templates/de/printer-configured.tmpl
/usr/share/cups/templates/de/option-trailer.tmpl
/usr/share/cups/templates/de/printer-purge.tmpl
/usr/share/cups/templates/de/command.tmpl
/usr/share/cups/templates/de/job-move.tmpl
/usr/share/cups/templates/de/printers.tmpl
/usr/share/cups/templates/de/subscription-canceled.tmpl
/usr/share/cups/templates/de/users.tmpl
/usr/share/cups/templates/de/admin.tmpl
/usr/share/cups/templates/de/class.tmpl
/usr/share/cups/templates/de/printer-accept.tmpl
/usr/share/cups/templates/de/classes.tmpl
/usr/share/cups/templates/de/option-boolean.tmpl
/usr/share/cups/templates/de/subscription-added.tmpl
/usr/share/cups/templates/de/printer-jobs-header.tmpl
/usr/share/cups/templates/de/samba-exported.tmpl
/usr/share/cups/templates/de/printer-modified.tmpl
/usr/share/cups/templates/de/restart.tmpl
/usr/share/cups/templates/de/job-release.tmpl
/usr/share/cups/templates/de/modify-class.tmpl
/usr/share/cups/templates/de/edit-config.tmpl
/usr/share/cups/templates/de/class-added.tmpl
/usr/share/cups/templates/de/printer-default.tmpl
/usr/share/cups/templates/de/printer-start.tmpl
/usr/share/cups/templates/de/class-confirm.tmpl
/usr/share/cups/templates/de/search.tmpl
/usr/share/cups/templates/de/modify-printer.tmpl
/usr/share/cups/templates/de/job-moved.tmpl
/usr/share/cups/templates/de/samba-export.tmpl
/usr/share/cups/templates/de/norestart.tmpl
/usr/share/cups/templates/de/help-printable.tmpl
/usr/share/cups/templates/de/printer-added.tmpl
/usr/share/cups/templates/de/set-printer-options-trailer.tmpl
/usr/share/cups/templates/de/printer-stop.tmpl
/usr/share/cups/templates/de/choose-model.tmpl
/usr/share/cups/templates/de/option-pickmany.tmpl
/usr/share/cups/templates/subscription-added.tmpl
/usr/share/cups/templates/printer-jobs-header.tmpl
/usr/share/cups/templates/samba-exported.tmpl
/usr/share/cups/templates/printer-modified.tmpl
/usr/share/cups/templates/ru
/usr/share/cups/templates/ru/choose-make.tmpl
/usr/share/cups/templates/ru/pager.tmpl
/usr/share/cups/templates/ru/printer-confirm.tmpl
/usr/share/cups/templates/ru/jobs.tmpl
/usr/share/cups/templates/ru/job-cancel.tmpl
/usr/share/cups/templates/ru/classes-header.tmpl
/usr/share/cups/templates/ru/trailer.tmpl
/usr/share/cups/templates/ru/printer.tmpl
/usr/share/cups/templates/ru/set-printer-options-header.tmpl
/usr/share/cups/templates/ru/printers-header.tmpl
/usr/share/cups/templates/ru/class-jobs-header.tmpl
/usr/share/cups/templates/ru/printer-deleted.tmpl
/usr/share/cups/templates/ru/jobs-header.tmpl
/usr/share/cups/templates/ru/help-trailer.tmpl
/usr/share/cups/templates/ru/list-available-printers.tmpl
/usr/share/cups/templates/ru/add-printer.tmpl
/usr/share/cups/templates/ru/help-header.tmpl
/usr/share/cups/templates/ru/error-op.tmpl
/usr/share/cups/templates/ru/choose-serial.tmpl
/usr/share/cups/templates/ru/option-pickone.tmpl
/usr/share/cups/templates/ru/choose-uri.tmpl
/usr/share/cups/templates/ru/header.tmpl
/usr/share/cups/templates/ru/class-modified.tmpl
/usr/share/cups/templates/ru/job-restart.tmpl
/usr/share/cups/templates/ru/error.tmpl
/usr/share/cups/templates/ru/printer-reject.tmpl
/usr/share/cups/templates/ru/test-page.tmpl
/usr/share/cups/templates/ru/option-header.tmpl
/usr/share/cups/templates/ru/add-rss-subscription.tmpl
/usr/share/cups/templates/ru/add-class.tmpl
/usr/share/cups/templates/ru/choose-device.tmpl
/usr/share/cups/templates/ru/job-hold.tmpl
/usr/share/cups/templates/ru/option-conflict.tmpl
/usr/share/cups/templates/ru/class-deleted.tmpl
/usr/share/cups/templates/ru/printer-configured.tmpl
/usr/share/cups/templates/ru/option-trailer.tmpl
/usr/share/cups/templates/ru/printer-purge.tmpl
/usr/share/cups/templates/ru/command.tmpl
/usr/share/cups/templates/ru/job-move.tmpl
/usr/share/cups/templates/ru/printers.tmpl
/usr/share/cups/templates/ru/subscription-canceled.tmpl
/usr/share/cups/templates/ru/users.tmpl
/usr/share/cups/templates/ru/admin.tmpl
/usr/share/cups/templates/ru/class.tmpl
/usr/share/cups/templates/ru/printer-accept.tmpl
/usr/share/cups/templates/ru/classes.tmpl
/usr/share/cups/templates/ru/option-boolean.tmpl
/usr/share/cups/templates/ru/subscription-added.tmpl
/usr/share/cups/templates/ru/printer-jobs-header.tmpl
/usr/share/cups/templates/ru/samba-exported.tmpl
/usr/share/cups/templates/ru/printer-modified.tmpl
/usr/share/cups/templates/ru/restart.tmpl
/usr/share/cups/templates/ru/job-release.tmpl
/usr/share/cups/templates/ru/modify-class.tmpl
/usr/share/cups/templates/ru/edit-config.tmpl
/usr/share/cups/templates/ru/class-added.tmpl
/usr/share/cups/templates/ru/printer-default.tmpl
/usr/share/cups/templates/ru/printer-start.tmpl
/usr/share/cups/templates/ru/class-confirm.tmpl
/usr/share/cups/templates/ru/search.tmpl
/usr/share/cups/templates/ru/modify-printer.tmpl
/usr/share/cups/templates/ru/job-moved.tmpl
/usr/share/cups/templates/ru/samba-export.tmpl
/usr/share/cups/templates/ru/norestart.tmpl
/usr/share/cups/templates/ru/help-printable.tmpl
/usr/share/cups/templates/ru/printer-added.tmpl
/usr/share/cups/templates/ru/set-printer-options-trailer.tmpl
/usr/share/cups/templates/ru/printer-stop.tmpl
/usr/share/cups/templates/ru/choose-model.tmpl
/usr/share/cups/templates/ru/option-pickmany.tmpl
/usr/share/cups/templates/restart.tmpl
/usr/share/cups/templates/job-release.tmpl
/usr/share/cups/templates/modify-class.tmpl
/usr/share/cups/templates/edit-config.tmpl
/usr/share/cups/templates/class-added.tmpl
/usr/share/cups/templates/printer-default.tmpl
/usr/share/cups/templates/ja
/usr/share/cups/templates/ja/choose-make.tmpl
/usr/share/cups/templates/ja/pager.tmpl
/usr/share/cups/templates/ja/printer-confirm.tmpl
/usr/share/cups/templates/ja/jobs.tmpl
/usr/share/cups/templates/ja/job-cancel.tmpl
/usr/share/cups/templates/ja/classes-header.tmpl
/usr/share/cups/templates/ja/trailer.tmpl
/usr/share/cups/templates/ja/printer.tmpl
/usr/share/cups/templates/ja/set-printer-options-header.tmpl
/usr/share/cups/templates/ja/printers-header.tmpl
/usr/share/cups/templates/ja/class-jobs-header.tmpl
/usr/share/cups/templates/ja/printer-deleted.tmpl
/usr/share/cups/templates/ja/jobs-header.tmpl
/usr/share/cups/templates/ja/help-trailer.tmpl
/usr/share/cups/templates/ja/list-available-printers.tmpl
/usr/share/cups/templates/ja/add-printer.tmpl
/usr/share/cups/templates/ja/help-header.tmpl
/usr/share/cups/templates/ja/error-op.tmpl
/usr/share/cups/templates/ja/choose-serial.tmpl
/usr/share/cups/templates/ja/option-pickone.tmpl
/usr/share/cups/templates/ja/choose-uri.tmpl
/usr/share/cups/templates/ja/header.tmpl
/usr/share/cups/templates/ja/class-modified.tmpl
/usr/share/cups/templates/ja/job-restart.tmpl
/usr/share/cups/templates/ja/error.tmpl
/usr/share/cups/templates/ja/printer-reject.tmpl
/usr/share/cups/templates/ja/test-page.tmpl
/usr/share/cups/templates/ja/option-header.tmpl
/usr/share/cups/templates/ja/add-rss-subscription.tmpl
/usr/share/cups/templates/ja/add-class.tmpl
/usr/share/cups/templates/ja/choose-device.tmpl
/usr/share/cups/templates/ja/job-hold.tmpl
/usr/share/cups/templates/ja/option-conflict.tmpl
/usr/share/cups/templates/ja/class-deleted.tmpl
/usr/share/cups/templates/ja/printer-configured.tmpl
/usr/share/cups/templates/ja/option-trailer.tmpl
/usr/share/cups/templates/ja/printer-purge.tmpl
/usr/share/cups/templates/ja/command.tmpl
/usr/share/cups/templates/ja/job-move.tmpl
/usr/share/cups/templates/ja/printers.tmpl
/usr/share/cups/templates/ja/subscription-canceled.tmpl
/usr/share/cups/templates/ja/users.tmpl
/usr/share/cups/templates/ja/admin.tmpl
/usr/share/cups/templates/ja/class.tmpl
/usr/share/cups/templates/ja/printer-accept.tmpl
/usr/share/cups/templates/ja/classes.tmpl
/usr/share/cups/templates/ja/option-boolean.tmpl
/usr/share/cups/templates/ja/subscription-added.tmpl
/usr/share/cups/templates/ja/printer-jobs-header.tmpl
/usr/share/cups/templates/ja/samba-exported.tmpl
/usr/share/cups/templates/ja/printer-modified.tmpl
/usr/share/cups/templates/ja/restart.tmpl
/usr/share/cups/templates/ja/job-release.tmpl
/usr/share/cups/templates/ja/modify-class.tmpl
/usr/share/cups/templates/ja/edit-config.tmpl
/usr/share/cups/templates/ja/class-added.tmpl
/usr/share/cups/templates/ja/printer-default.tmpl
/usr/share/cups/templates/ja/printer-start.tmpl
/usr/share/cups/templates/ja/class-confirm.tmpl
/usr/share/cups/templates/ja/search.tmpl
/usr/share/cups/templates/ja/modify-printer.tmpl
/usr/share/cups/templates/ja/job-moved.tmpl
/usr/share/cups/templates/ja/samba-export.tmpl
/usr/share/cups/templates/ja/norestart.tmpl
/usr/share/cups/templates/ja/help-printable.tmpl
/usr/share/cups/templates/ja/printer-added.tmpl
/usr/share/cups/templates/ja/set-printer-options-trailer.tmpl
/usr/share/cups/templates/ja/printer-stop.tmpl
/usr/share/cups/templates/ja/choose-model.tmpl
/usr/share/cups/templates/ja/option-pickmany.tmpl
/usr/share/cups/templates/printer-start.tmpl
/usr/share/cups/templates/class-confirm.tmpl
/usr/share/cups/templates/search.tmpl
/usr/share/cups/templates/modify-printer.tmpl
/usr/share/cups/templates/job-moved.tmpl
/usr/share/cups/templates/samba-export.tmpl
/usr/share/cups/templates/norestart.tmpl
/usr/share/cups/templates/help-printable.tmpl
/usr/share/cups/templates/printer-added.tmpl
/usr/share/cups/templates/set-printer-options-trailer.tmpl
/usr/share/cups/templates/printer-stop.tmpl
/usr/share/cups/templates/choose-model.tmpl
/usr/share/cups/templates/option-pickmany.tmpl
/usr/share/cups/doc-root
/usr/share/cups/doc-root/index.html
/usr/share/cups/doc-root/cups.css
/usr/share/cups/doc-root/es
/usr/share/cups/doc-root/es/index.html
/usr/share/cups/doc-root/hu
/usr/share/cups/doc-root/hu/index.html
/usr/share/cups/doc-root/cups-printable.css
/usr/share/cups/doc-root/id
/usr/share/cups/doc-root/id/index.html
/usr/share/cups/doc-root/it
/usr/share/cups/doc-root/it/index.html
/usr/share/cups/doc-root/robots.txt
/usr/share/cups/doc-root/fr
/usr/share/cups/doc-root/fr/index.html
/usr/share/cups/doc-root/images
/usr/share/cups/doc-root/images/sample-image.png
/usr/share/cups/doc-root/images/right.gif
/usr/share/cups/doc-root/images/cups-raster-chain.png
/usr/share/cups/doc-root/images/cups.png
/usr/share/cups/doc-root/images/sel.gif
/usr/share/cups/doc-root/images/smiley.jpg
/usr/share/cups/doc-root/images/unsel.gif
/usr/share/cups/doc-root/images/generic.png
/usr/share/cups/doc-root/images/cups-postscript-chain.png
/usr/share/cups/doc-root/images/raster.png
/usr/share/cups/doc-root/images/wait.gif
/usr/share/cups/doc-root/images/cups-block-diagram.png
/usr/share/cups/doc-root/images/raster-organization.png
/usr/share/cups/doc-root/images/color-wheel.png
/usr/share/cups/doc-root/images/left.gif
/usr/share/cups/doc-root/images/cups-command-chain.png
/usr/share/cups/doc-root/images/cups-icon.png
/usr/share/cups/doc-root/pl
/usr/share/cups/doc-root/pl/index.html
/usr/share/cups/doc-root/eu
/usr/share/cups/doc-root/eu/index.html
/usr/share/cups/doc-root/de
/usr/share/cups/doc-root/de/index.html
/usr/share/cups/doc-root/ru
/usr/share/cups/doc-root/ru/index.html
/usr/share/cups/doc-root/help
/usr/share/cups/doc-root/help/man-cups-lpd.html
/usr/share/cups/doc-root/help/cgi.html
/usr/share/cups/doc-root/help/ref-cupsd-conf.html
/usr/share/cups/doc-root/help/api-httpipp.html
/usr/share/cups/doc-root/help/spec-design.html
/usr/share/cups/doc-root/help/ref-ppdcfile.html
/usr/share/cups/doc-root/help/security.html
/usr/share/cups/doc-root/help/api-filedir.html
/usr/share/cups/doc-root/help/spec-banner.html
/usr/share/cups/doc-root/help/man-cupsaccept.html
/usr/share/cups/doc-root/help/man-lpc.html
/usr/share/cups/doc-root/help/man-lpinfo.html
/usr/share/cups/doc-root/help/man-ppdi.html
/usr/share/cups/doc-root/help/man-ipptool.html
/usr/share/cups/doc-root/help/whatsnew.html
/usr/share/cups/doc-root/help/man-lpadmin.html
/usr/share/cups/doc-root/help/ref-page_log.html
/usr/share/cups/doc-root/help/api-overview.html
/usr/share/cups/doc-root/help/man-ppdc.html
/usr/share/cups/doc-root/help/man-lp.html
/usr/share/cups/doc-root/help/man-ppdhtml.html
/usr/share/cups/doc-root/help/translation.html
/usr/share/cups/doc-root/help/spec-pdf.html
/usr/share/cups/doc-root/help/overview.html
/usr/share/cups/doc-root/help/man-lprm.html
/usr/share/cups/doc-root/help/man-cupsenable.html
/usr/share/cups/doc-root/help/policies.html
/usr/share/cups/doc-root/help/man-cups-config.html
/usr/share/cups/doc-root/help/man-ppdmerge.html
/usr/share/cups/doc-root/help/spec-cmp.html
/usr/share/cups/doc-root/help/man-lppasswd.html
/usr/share/cups/doc-root/help/raster-driver.html
/usr/share/cups/doc-root/help/ref-mailto-conf.html
/usr/share/cups/doc-root/help/api-cups.html
/usr/share/cups/doc-root/help/spec-stp.html
/usr/share/cups/doc-root/help/ref-subscriptions-conf.html
/usr/share/cups/doc-root/help/postscript-driver.html
/usr/share/cups/doc-root/help/man-mime.convs.html
/usr/share/cups/doc-root/help/api-mime.html
/usr/share/cups/doc-root/help/man-lpr.html
/usr/share/cups/doc-root/help/man-ipptoolfile.html
/usr/share/cups/doc-root/help/standard.html
/usr/share/cups/doc-root/help/options.html
/usr/share/cups/doc-root/help/api-cgi.html
/usr/share/cups/doc-root/help/man-notifier.html
/usr/share/cups/doc-root/help/man-cancel.html
/usr/share/cups/doc-root/help/man-lpmove.html
/usr/share/cups/doc-root/help/network.html
/usr/share/cups/doc-root/help/api-array.html
/usr/share/cups/doc-root/help/glossary.html
/usr/share/cups/doc-root/help/man-cups-polld.html
/usr/share/cups/doc-root/help/man-cupstestdsc.html
/usr/share/cups/doc-root/help/spec-command.html
/usr/share/cups/doc-root/help/spec-browsing.html
/usr/share/cups/doc-root/help/accounting.html
/usr/share/cups/doc-root/help/man-cupsd.html
/usr/share/cups/doc-root/help/spec-ppd.html
/usr/share/cups/doc-root/help/ref-error_log.html
/usr/share/cups/doc-root/help/man-cupsaddsmb.html
/usr/share/cups/doc-root/help/sharing.html
/usr/share/cups/doc-root/help/man-backend.html
/usr/share/cups/doc-root/help/api-ppd.html
/usr/share/cups/doc-root/help/man-lpq.html
/usr/share/cups/doc-root/help/man-cupstestppd.html
/usr/share/cups/doc-root/help/ref-classes-conf.html
/usr/share/cups/doc-root/help/man-mime.types.html
/usr/share/cups/doc-root/help/spec-postscript.html
/usr/share/cups/doc-root/help/license.html
/usr/share/cups/doc-root/help/man-lpstat.html
/usr/share/cups/doc-root/help/api-filter.html
/usr/share/cups/doc-root/help/man-ppdpo.html
/usr/share/cups/doc-root/help/spec-ipp.html
/usr/share/cups/doc-root/help/ref-printers-conf.html
/usr/share/cups/doc-root/help/api-raster.html
/usr/share/cups/doc-root/help/ppd-compiler.html
/usr/share/cups/doc-root/help/ref-access_log.html
/usr/share/cups/doc-root/help/ref-snmp-conf.html
/usr/share/cups/doc-root/help/ref-client-conf.html
/usr/share/cups/doc-root/help/man-lpoptions.html
/usr/share/cups/doc-root/help/man-filter.html
/usr/share/cups/doc-root/help/api-driver.html
/usr/share/cups/doc-root/help/api-ppdc.html
/usr/share/cups/doc-root/help/spec-raster.html
/usr/share/cups/doc-root/help/kerberos.html
/usr/share/cups/doc-root/ja
/usr/share/cups/doc-root/ja/index.html
/usr/share/cups/ppd-updaters
/usr/share/doc
/usr/share/doc/cups
/usr/share/doc/cups/copyright
/usr/share/doc/cups/CREDITS.txt
/usr/share/doc/cups/README.txt.gz
/usr/share/doc/cups/examples
/usr/share/doc/cups/examples/printer.schema
/usr/share/doc/cups/HOWTO_BUGREPORT.txt
/usr/sbin
/usr/sbin/cupsd
/usr/sbin/cupsfilter
/etc
/etc/apparmor.d
/etc/apparmor.d/usr.sbin.cupsd
/etc/init.d
/etc/ufw
/etc/ufw/applications.d
/etc/ufw/applications.d/cups
/etc/pam.d
/etc/pam.d/cups
/etc/default
/etc/default/cups
/etc/cups
/etc/cups/ppd
/etc/cups/cups-files.conf
/etc/cups/cupsd.conf
/etc/cups/ssl
/etc/cups/snmp.conf
/etc/cups/cupsd.conf.default
/etc/logrotate.d
/etc/logrotate.d/cups
/etc/init
/etc/init/cups.conf
/var
/var/spool
/var/spool/cups
/var/spool/cups/tmp
/var/cache
/var/cache/cups
/var/cache/cups/rss
/var/log
/var/log/cups
/usr/lib/cups/filter/rastertodymo
/usr/lib/cups/backend-available/http
/usr/lib/cups/backend-available/ipps
/usr/lib/cups/backend-available/https
/usr/share/doc/cups/online-docs
/usr/share/doc/cups/changelog.Debian.gz
/etc/init.d/cups

```

cat /var/lib/apt/extended_states
...again, cut off
```
Architecture: amd64Auto-Installed: 1


Package: x11proto-damage-dev
Architecture: amd64
Auto-Installed: 1


Package: libhdf5-serial-1.8.4
Architecture: amd64
Auto-Installed: 1


Package: libgeos-c1
Architecture: amd64
Auto-Installed: 1


Package: gdal-bin
Architecture: amd64
Auto-Installed: 1


Package: wine-mono4.5.2
Architecture: amd64
Auto-Installed: 1


Package: camlp4
Architecture: amd64
Auto-Installed: 1


Package: libghc-transformers-prof
Architecture: amd64
Auto-Installed: 1


Package: libghc-network-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-monad-control-prof
Architecture: amd64
Auto-Installed: 1


Package: libghc-vector-prof
Architecture: amd64
Auto-Installed: 1


Package: libghc-utf8-string-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-digest-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-regex-tdfa-prof
Architecture: amd64
Auto-Installed: 1


Package: libglib2.0-dev
Architecture: amd64
Auto-Installed: 1


Package: proj-data
Architecture: amd64
Auto-Installed: 1


Package: libfreexl1
Architecture: amd64
Auto-Installed: 1


Package: zlib1g-dev
Architecture: amd64
Auto-Installed: 1


Package: libantlr-java
Architecture: amd64
Auto-Installed: 1


Package: libchipmunk0d1
Architecture: amd64
Auto-Installed: 1


Package: libxcb-shm0-dev
Architecture: amd64
Auto-Installed: 1


Package: libcairo2-dev
Architecture: amd64
Auto-Installed: 1


Package: libboost-thread1.46.1
Architecture: amd64
Auto-Installed: 1


Package: libghc-largeword-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-primitive-prof
Architecture: amd64
Auto-Installed: 1


Package: libghc-conduit-dev
Architecture: amd64
Auto-Installed: 1


Package: libservlet2.5-java
Architecture: amd64
Auto-Installed: 1


Package: libzzip-0-13
Architecture: amd64
Auto-Installed: 1


Package: libfindlib-ocaml
Architecture: amd64
Auto-Installed: 1


Package: libghc-hashable-dev
Architecture: amd64
Auto-Installed: 1


Package: libpango1.0-dev
Architecture: amd64
Auto-Installed: 1


Package: libfreetype6-dev
Architecture: amd64
Auto-Installed: 1


Package: build-essential
Architecture: amd64
Auto-Installed: 1


Package: libxau-dev
Architecture: amd64
Auto-Installed: 1


Package: dpkg-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-mtl-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-event-list-dev
Architecture: amd64
Auto-Installed: 1


Package: libspatialite3
Architecture: amd64
Auto-Installed: 1


Package: libghc-cairo-dev
Architecture: amd64
Auto-Installed: 1


Package: libxpp3-java
Architecture: amd64
Auto-Installed: 1


Package: libblas3gf
Architecture: amd64
Auto-Installed: 1


Package: libghc-stm-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-resource-pool-prof
Architecture: amd64
Auto-Installed: 1


Package: proj-bin
Architecture: amd64
Auto-Installed: 1


Package: tcl8.5
Architecture: amd64
Auto-Installed: 1


Package: libghc-base-unicode-symbols-dev
Architecture: amd64
Auto-Installed: 1


Package: libasm3-java
Architecture: amd64
Auto-Installed: 1


Package: libghc-monad-loops-prof
Architecture: amd64
Auto-Installed: 1


Package: libamd2.2.0
Architecture: amd64
Auto-Installed: 1


Package: ledit
Architecture: amd64
Auto-Installed: 1


Package: ocaml-base-nox
Architecture: amd64
Auto-Installed: 1


Package: libregexp-java
Architecture: amd64
Auto-Installed: 1


Package: libghc-puremd5-prof
Architecture: amd64
Auto-Installed: 1


Package: libgeos-3.2.2
Architecture: amd64
Auto-Installed: 1


Package: libghc-monoid-transformer-prof
Architecture: amd64
Auto-Installed: 1


Package: libghc-regex-tdfa-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-puremd5-dev
Architecture: amd64
Auto-Installed: 1


Package: gir1.2-rsvg-2.0
Architecture: amd64
Auto-Installed: 1


Package: tk8.5
Architecture: amd64
Auto-Installed: 1


Package: libghc-data-default-dev
Architecture: amd64
Auto-Installed: 1


Package: libxcomposite-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-random-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-zlib-prof
Architecture: amd64
Auto-Installed: 1


Package: libghc-base-unicode-symbols-prof
Architecture: amd64
Auto-Installed: 1


Package: libgmpxx4ldbl
Architecture: amd64
Auto-Installed: 1


Package: libxcb-render0-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-crypto-api-prof
Architecture: amd64
Auto-Installed: 1


Package: libxrender-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-data-default-prof
Architecture: amd64
Auto-Installed: 1


Package: libghc-random-prof
Architecture: amd64
Auto-Installed: 1


Package: xorg-sgml-doctools
Architecture: amd64
Auto-Installed: 1


Package: libpq5
Architecture: amd64
Auto-Installed: 1


Package: libghc-parsec3-prof
Architecture: amd64
Auto-Installed: 1


Package: libgfortran3
Architecture: amd64
Auto-Installed: 1


Package: libghc-glib-prof
Architecture: amd64
Auto-Installed: 1


Package: python-support
Architecture: amd64
Auto-Installed: 1


Package: libpcre3-dev
Architecture: amd64
Auto-Installed: 1


Package: ca-certificates-java
Architecture: amd64
Auto-Installed: 1


Package: html2text
Architecture: amd64
Auto-Installed: 1


Package: libcommons-lang-java
Architecture: amd64
Auto-Installed: 1


Package: libhamcrest-java
Architecture: amd64
Auto-Installed: 1


Package: libxft-dev
Architecture: amd64
Auto-Installed: 1


Package: libx11-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-utility-ht-prof
Architecture: amd64
Auto-Installed: 1


Package: x11proto-composite-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-regex-posix-prof
Architecture: amd64
Auto-Installed: 1


Package: libcommons-parent-java
Architecture: amd64
Auto-Installed: 1


Package: libcommons-collections3-java
Architecture: amd64
Auto-Installed: 1


Package: libx11-doc
Architecture: amd64
Auto-Installed: 1


Package: libghc-hslogger-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-lifted-base-prof
Architecture: amd64
Auto-Installed: 1


Package: libgcj-common
Architecture: amd64
Auto-Installed: 1


Package: libalgorithm-diff-perl
Architecture: amd64
Auto-Installed: 1


Package: libghc-syb-dev
Architecture: amd64
Auto-Installed: 1


Package: autotools-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-entropy-prof
Architecture: amd64
Auto-Installed: 1


Package: libghc-quickcheck2-dev
Architecture: amd64
Auto-Installed: 1


Package: libhdf4-0-alt
Architecture: amd64
Auto-Installed: 1


Package: libxcb1-dev
Architecture: amd64
Auto-Installed: 1


Package: libgtk2.0-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-haskell-src-prof
Architecture: amd64
Auto-Installed: 1


Package: libmail-sendmail-perl
Architecture: amd64
Auto-Installed: 1


Package: libopenjpeg2
Architecture: amd64
Auto-Installed: 1


Package: libghc-semigroups-dev
Architecture: amd64
Auto-Installed: 1


Package: openjdk-6-jre
Architecture: amd64
Auto-Installed: 1


Package: ocaml-nox
Architecture: amd64
Auto-Installed: 1


Package: libsys-hostname-long-perl
Architecture: amd64
Auto-Installed: 1


Package: mysql-common
Architecture: amd64
Auto-Installed: 1


Package: libjline-java
Architecture: amd64
Auto-Installed: 1


Package: libghc-tagsoup-prof
Architecture: amd64
Auto-Installed: 1


Package: x11proto-core-dev
Architecture: amd64
Auto-Installed: 1


Package: freeglut3
Architecture: amd64
Auto-Installed: 1


Package: chipmunk-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-network-prof
Architecture: amd64
Auto-Installed: 1


Package: libdapclient3
Architecture: amd64
Auto-Installed: 1


Package: libxdmcp-dev
Architecture: amd64
Auto-Installed: 1


Package: libghc-transformers-base-prof
Architecture: amd64
Auto-Installed: 1


Package: libpthread-stubs0-dev
Architecture: amd64
Auto-Installed: 1


Package: libxcursor-dev
Architecture: amd64
Auto-Installed: 1


Package: python-wxversion
Architecture: amd64
Auto-Installed: 1


Package: libnetcdf6
Architecture: amd64
Auto-Installed: 1


Package: python-opengl
Architecture: amd64
Auto-Installed: 1


Package: grass
Architecture: amd64
Auto-Installed: 1


Package: libpng12-dev
Architecture: amd64
Auto-Installed: 1


Package: linux-headers-3.8.0-35
Architecture: amd64
Auto-Installed: 1


Package: grub-pc
Architecture: amd64
Auto-Installed: 1


Package: grub-gfxpayload-lists
Architecture: amd64
Auto-Installed: 1


Package: linux-headers-3.8.0-35-generic
Architecture: amd64
Auto-Installed: 1

```

cat /var/lib/dpkg/info/cups.prerm
```
#! /bin/sh
# prerm script for cups
#
# see: dh_installdeb(1)


set -e


# summary of how this script can be called:
#        * <prerm> `remove'
#        * <old-prerm> `upgrade' <new-version>
#        * <new-prerm> `failed-upgrade' <old-version>
#        * <conflictor's-prerm> `remove' `in-favour' <package> <new-version>
#        * <deconfigured's-prerm> `deconfigure' `in-favour'
#          <package-being-installed> <version> `removing'
#          <conflicting-package> <version>
# for details, see http://www.debian.org/doc/debian-policy/ or
# the debian-policy package




case "$1" in
    remove)
	(cd /usr/lib/cups/backend && rm -f http https ipp ipp14 ipps lpd socket usb snmp dnssd mdns)
        ;;
    upgrade|deconfigure)
        ;;
    failed-upgrade)
        ;;
    *)
        echo "prerm called with unknown argument \`$1'" >&2
        exit 1
    ;;
esac


# dh_installdeb will replace this with shell code automatically
# generated by other debhelper scripts.


# Automatically added by dh_installinit
if [ -e "/etc/init/cups.conf" ]; then
	invoke-rc.d cups stop || exit $?
fi
# End automatically added section




exit 0

```

---

### Post by Bashing-om on 2014-01-14
j88n; Wel,

No listing for cups in "/var/lib/apt/extended_states", Hummm. 
Gonna reboot into my 12.04 and do some poking about.

[INDENT][INDENT]I will be back
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-14
okay!

---

### Post by Bashing-om on 2014-01-14
j88n; That was fruitless !

My working 12.04.3 also does not have a listing for "cups" in /var/lib/apt/extended_states. Inconclusive.

Look'n:
```

dpkg -l cups
##and let's see how dpkg handles looking at the status file##
dpkg -s cups

```
Trying to comprehend why install/purge  attempts says cups is not installed, but all evidence is to the contrary. That is not to mention the other "trouble " packages.

Once more for handy reference:
```

apt-cache depends cups
apt-cache rdepends cups

```
and let's see if we can find some answers.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-14
dpkg -l cups
```
sean@Sean-Monster:/var/lib/apt$ dpkg -l cupsBus error (core dumped)

```


dpkg -s cups
```
sean@Sean-Monster:/var/lib/apt$ dpkg -s cupsBus error (core dumped)

```

apt-cache depends cups
```
sean@Sean-Monster:/var/lib/apt$ apt-cache depends cupscups
  Depends: libavahi-client3
  Depends: libavahi-common3
  Depends: libc6
  Depends: libcups2
  Depends: libcupscgi1
  Depends: libcupsimage2
  Depends: libcupsmime1
  Depends: libcupsppdc1
  Depends: libdbus-1-3
  Depends: libgcc1
  Depends: libgnutls26
  Depends: libgssapi-krb5-2
  Depends: libkrb5-3
  Depends: libldap-2.4-2
  Depends: libpam0g
  Depends: libpaper1
  Depends: libslp1
  Depends: libstdc++6
  Depends: libusb-1.0-0
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Depends: <upstart-job>
    upstart
  Depends: poppler-utils
  Depends: procps
  Depends: ghostscript
  Depends: lsb-base
  Depends: cups-common
  Depends: cups-client
  Depends: ssl-cert
  Depends: adduser
  Depends: bc
  Depends: cups-ppdc
  Depends: cups-filters
  PreDepends: dpkg
  Suggests: cups-bsd
 |Suggests: foomatic-db-compressed-ppds
  Suggests: foomatic-db
    foomatic-db-compressed-ppds
  Suggests: printer-driver-hpcups
  Suggests: hplip
  Suggests: cups-pdf
  Suggests: udev
  Suggests: smbclient
    samba4-clients
  Recommends: avahi-daemon
  Recommends: colord
  Recommends: foomatic-filters
  Recommends: printer-driver-gutenprint
  Recommends: ghostscript-cups
  Breaks: <cupsddk-drivers>
  Breaks: foomatic-filters
  Breaks: ghostscript-cups
  Replaces: <cupsddk-drivers>
  Replaces: ghostscript-cups

```

apt-cache rdepends cups
```
sean@Sean-Monster:/var/lib/apt$ apt-cache rdepends cupscups
Reverse Depends:
  libcupsmime1
  libcups2
  cups-dbg
  cups-client
  cups-bsd
  ubuntu-desktop
  printer-driver-postscript-hp
 |printer-driver-hpijs
  printer-driver-hpcups
 |printer-driver-hpcups
  printer-driver-gutenprint
  libcupsmime1
  libcups2
  hplip
  ghostscript-cups
 |foomatic-filters
  cups-filters
  cups-filters
  cups-dbg
  cups-client
  cups-bsd
  zentyal-printers
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-sugar-remix
  printer-driver-postscript-hp
  printer-driver-escpr
  printconf
  lubuntu-core
  libgnomeprint2.2-0
  libgnomecups1.0-1
  kubuntu-active
  ichthux-desktop
  geogebra
  cups-pdf
  ubuntu-desktop
 |printer-driver-splix
  printer-driver-sag-gdi
 |printer-driver-sag-gdi
  printer-driver-min12xxw
 |printer-driver-hpijs
  printer-driver-hpcups
 |printer-driver-hpcups
  printer-driver-gutenprint
  printer-driver-foo2zjs
  printer-driver-foo2zjs
  printer-driver-c2esp
  openprinting-ppds
  openprinting-ppds
  libcupsmime1
  libcups2
  kubuntu-desktop
  indicator-printers
  hplip
  ghostscript-cups
 |foomatic-filters
  foomatic-db-engine
  foomatic-db-engine
  foomatic-db-compressed-ppds
  foomatic-db-compressed-ppds
  foomatic-db
  foomatic-db
  cups-filters
  cups-filters
  cups-dbg
  cups-client
  cups-bsd
  bluez-cups

```

---

### Post by Bashing-om on 2014-01-14
j88n; Welp,

Not to keep you hanging, might be a long process I am looking into,
core dump as you can imagine is not good.

Bus Error. The most common cause is an invalid address alignment reference, although attempting to access a non-existent item at a particular bus address can also produce the fault.
... then the program was trying to access a memory location outside its address space.

So that tells us that there is a corrupt file  - some where - or corruption at some location (hard disk problem !). So, what is in common with all these packages that the package manager is hollering about when there is an attempt to install/purge/reconfigure ? I do not know presently !

Tell ya what, while I am thinnin, run a file system check to preclude we are dealing with hardware problems.
boot the liveDVD - because one can not run a file system check on a mounted file system - and; make sure swap is turned off, then;
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

``` Assuming  that the operating system we are trying to cope with is on that 1st hard drive "sda", and root is on the 1st partition (sda1). Otherwise adjust the commands according to hard disk and partition for root.
It would not hurt my feelings in the least if you were to take a lot of time to read the manual about file system checks:
```

man fsck
man e2fsck

```

An strace operation would probably help, but, I have high doubts of my reliability to properly read the out put.
Let me see what I can think of for an alternative, to find those corrupted files.

[INDENT][INDENT]it is a dark day when 
[INDENT][INDENT]we just don't know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-15
So I hope I did this correctly. It seems a little over my head..

sudo e2fsck -C0 -p -f -v /dev/sda1
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
  326911 inodes used (0.72%)
     607 non-contiguous files (0.2%)
     279 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 279208/107
 5258825 blocks used (2.90%)
       0 bad blocks
       1 large file

  222403 regular files
   41407 directories
      57 character device files
      25 block device files
       1 fifo
       7 links
   63007 symbolic links (47503 fast symbolic links)
       2 sockets
--------
  326909 files

```


sudo e2fsck -f -y -v /dev/sda1
```
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  326911 inodes used (0.72%)
     607 non-contiguous files (0.2%)
     279 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 279208/107
 5258825 blocks used (2.90%)
       0 bad blocks
       1 large file

  222403 regular files
   41407 directories
      57 character device files
      25 block device files
       1 fifo
       7 links
   63007 symbolic links (47503 fast symbolic links)
       2 sockets
--------
  326909 files

```

---

### Post by Bashing-om on 2014-01-15
j88nl; My moring to ya !

The output of the file checking looks fine to me ! .. whoooh. That's a load off.

Ok, - slept on it - We want to know that the problem does not reside with "dpkg" it's self.
Do these return clean, might pick a few others packages and see ? :
```

dpkg -l gedit
dpkg -- aisleriot
dpkg -l xorg
dpkg -L ia32-libs ##upper case 'l' just to look
dpkg -l | grep linux-image

``` should give us a good indication of the status of "dpkg" overall. As apt-get (front end to dpkg) runs good, I really do not expect that "dpkg" has any problems, but, need to make sure.

If all that is good, then we go hunting the corrupted file(s) common to the problem.

[INDENT][INDENT]which way did he go, George 
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-15
...Not really looking good. Here are my results:

sean@Sean-Monster:~$ dpkg -l edit
Bus error (core dumped)

sean@Sean-Monster:~$ dpkg -- aisleriot
Bus error (core dumped)

sean@Sean-Monster:~$ dpkg -l xorg
Bus error (core dumped)

sean@Sean-Monster:~$ dpkg -L ia32-libs
Bus error (core dumped)

sean@Sean-Monster:~$ dpkg -l | grep linux-image
sean@Sean-Monster:~$  ##NO RESPONSE

---

### Post by Bashing-om on 2014-01-15
j88n; Ouch !!!

That to me means that dpkg is what is broke. YUK, SO, how does one fix the package manager, when it is the package manager that is broke, we need the package manager to fix the system.

Houston, we have a problem. 
Bending my mind how software was installed onto a linux system before there was "dpkg" to do the work for us. 

Again, I do not know, presently at a loss, once more lemme go see what i can learn.

[INDENT][INDENT]who said I love this !
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-15
yeah that is troubling... =/

we obviously were able to install in the past, but some where it broke. I wish I had more insight on when it happened and why.

---

### Post by Bashing-om on 2014-01-15
j88n; Hey;

As I struggle to find a solution.
I have thought that "dpkg -l" reads the file "/var/lib/dpkg/status: - which we know is consistent - but maybe not, I am researching for documentation.
It is more reasonable that the "source" file is corrupt, rather than "dpkg: it's self (not ruling that possibility out either).

What might lead us to a hint of where to look for the source file might be to read the log file that dpkg keeps.

Take a gander at:
/var/log/dpkg.log

And see if it gives a hint to what is going on.

The last thing I want to do is download the source code for "dpkg" and compile and install - from source. I do not have the experience in ubuntu to advise on how to !

[INDENT][INDENT]mean while,
[INDENT][INDENT][INDENT]back at the ranch
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-15
The log hasn't updated in quite a while... this is the tail end of it

```
2014-01-05 16:09:44 status half-installed linux-image-generic-lts-raring 3.8.0.34.342014-01-05 16:09:44 status half-installed linux-image-generic-lts-raring 3.8.0.34.34
2014-01-05 16:09:44 status unpacked linux-image-generic-lts-raring 3.8.0.35.35
2014-01-05 16:09:44 status unpacked linux-image-generic-lts-raring 3.8.0.35.35
2014-01-05 16:09:44 trigproc man-db 2.6.1-2ubuntu1 2.6.1-2ubuntu1
2014-01-05 16:09:44 status half-configured man-db 2.6.1-2ubuntu1
2014-01-05 16:09:45 status installed man-db 2.6.1-2ubuntu1
2014-01-05 16:09:46 startup packages configure
2014-01-05 16:09:46 configure linux-image-3.8.0-35-generic 3.8.0-35.50~precise1 <none>
2014-01-05 16:09:46 status unpacked linux-image-3.8.0-35-generic 3.8.0-35.50~precise1
2014-01-05 16:09:46 status half-configured linux-image-3.8.0-35-generic 3.8.0-35.50~precise1
2014-01-05 16:10:06 status installed linux-image-3.8.0-35-generic 3.8.0-35.50~precise1
2014-01-05 16:10:06 configure linux-headers-3.8.0-35 3.8.0-35.50~precise1 <none>
2014-01-05 16:10:06 status unpacked linux-headers-3.8.0-35 3.8.0-35.50~precise1
2014-01-05 16:10:06 status half-configured linux-headers-3.8.0-35 3.8.0-35.50~precise1
2014-01-05 16:10:06 status installed linux-headers-3.8.0-35 3.8.0-35.50~precise1
2014-01-05 16:10:06 configure linux-headers-3.8.0-35-generic 3.8.0-35.50~precise1 <none>
2014-01-05 16:10:06 status unpacked linux-headers-3.8.0-35-generic 3.8.0-35.50~precise1
2014-01-05 16:10:06 status half-configured linux-headers-3.8.0-35-generic 3.8.0-35.50~precise1
2014-01-05 16:10:06 status installed linux-headers-3.8.0-35-generic 3.8.0-35.50~precise1
2014-01-05 16:10:06 configure linux-headers-generic-lts-raring 3.8.0.35.35 <none>
2014-01-05 16:10:06 status unpacked linux-headers-generic-lts-raring 3.8.0.35.35
2014-01-05 16:10:06 status half-configured linux-headers-generic-lts-raring 3.8.0.35.35
2014-01-05 16:10:07 status installed linux-headers-generic-lts-raring 3.8.0.35.35
2014-01-05 16:10:07 configure linux-image-generic-lts-raring 3.8.0.35.35 <none>
2014-01-05 16:10:07 status unpacked linux-image-generic-lts-raring 3.8.0.35.35
2014-01-05 16:10:07 status half-configured linux-image-generic-lts-raring 3.8.0.35.35
2014-01-05 16:10:07 status installed linux-image-generic-lts-raring 3.8.0.35.35
2014-01-05 16:10:07 configure grub-pc 1.99-21ubuntu3.14 <none>
2014-01-05 16:10:07 status unpacked grub-pc 1.99-21ubuntu3.14
2014-01-05 16:10:07 status unpacked grub-pc 1.99-21ubuntu3.14
2014-01-05 16:10:07 status unpacked grub-pc 1.99-21ubuntu3.14
2014-01-05 16:10:07 status half-configured grub-pc 1.99-21ubuntu3.14
2014-01-05 16:10:18 status installed grub-pc 1.99-21ubuntu3.14
2014-01-05 16:10:18 configure grub-gfxpayload-lists 0.6 <none>
2014-01-05 16:10:18 status unpacked grub-gfxpayload-lists 0.6
2014-01-05 16:10:18 status half-configured grub-gfxpayload-lists 0.6
2014-01-05 16:10:18 status installed grub-gfxpayload-lists 0.6

```

Also ran ls /var/log -l to see the last modified date and got this:
-rw-r--r-- 1 root              root    75468 Jan  5 16:10 dpkg.log

It seems weird that none of those dpkg commands aren't logging in dpkg.log

---

### Post by Bashing-om on 2014-01-15
j88n;Well,

More evidence that "dpkg" is broke. as to who what when and why, ->who knows. But until such time as confidence in the package management system is restored we are stonewalled.

I am still seeking documentation on "dpkg" . Hope to come up with a better alternative for us than compiling from source.
Might put this in out back pocket to see if dpkg will (re)install it's own self if/when all else fails. intriguing concept !

[INDENT][INDENT]it is a dark cloud
[INDENT][INDENT]that has no silver lining [/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-01-15
j88n; Maybe !

> 
3.2 What happens when dpkg reads the database

First, the status file is read. This gives dpkg an initial idea of the packages that are there. Next, the updates files are read in, overriding the status file, and if necessary, the status file is re-written, and updates files are removed. Finally, the available file is read. The available file is read with flags which preclude dpkg from updating any status information from it, though - installed version, etc., and is also told to record that the packages it reads this time are available, not installed.

Try this:
```

ls -la /var/lib/dpkg/available
sudo dpkg --clear-avail
sudo apt-get update
ls -la /var/lib/dpkg/available ##how much did that file change ?##

```

Now what results:
```

dpkg -l gedit

```

[INDENT][INDENT]hey, it is worth a shot
[/INDENT][/INDENT]

---

### Post by spencer the great on 2014-01-16
Alright, sorry to butt in here, but have you tried installing the deb package manually, without dpkg? (not a source install; manually extracting the deb package and copying the binaries and config files over). From what I've seen of this thread, it seems more like your actual dpkg is corrupted.  Especially the bus error, as one does not simply get a bus error when the configs are corrupted (in which case, the program itself will complain about the config being unable to read or something similar, like a nice old "Permission denied". of course, I could very likely be wrong).  


The solution: reinstall dpkg.

If you know how to install packages manually, without dpkg, that's the end of this post. If not:

I'm not entirely sure if this will work, but it CAN be a bit dangerous doing this manually:
debian packages (.deb packages) are simply two gzipped tar archives and a text file rolled up in an AR archive.
Before you start, back up your old dpkg binaries.
Download the dpkg deb package for your system. Make a clean extract directory for it. Extract the deb package into the directory:
```
$ mkdir dpkg
$ cd dpkg
$ ar x ../dpkg_VERSION_ARCH.deb

```
you should now have a control.tar.gz, data.tar.gz, and debian-binary. 
Untar the data archive:
```
$ tar xvzf data.tar.gz
```
As root, copy the binaries over (warning: this will overwrite your old binaries, so make sure you have backups):
```
# cp usr/bin/dpkg* /usr/bin/
```

A better, but slightly more risky, thing to do is to just copy everything over by going to / and extracting the data.tar.gz there; the usr, etc, and sbin directories will be merged and conflicting files will be overwritten, so make sure you have backups!
```
# cd /
# tar xvzf /PATH/TO/data.tar.gz
```

---

### Post by Bashing-om on 2014-01-16
@ spencer the great; A heap of thanks.

My thoughts too, I have no experience with the procedure. I welcome the guidance for a method to (Re-)install dpkg.


What will be
[INDENT][INDENT][INDENT]will be
[/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-16
so what are my next steps? It sounds tricky/dangerous... I'd like to re-install dpkg as it sounds like the root cause here, but I'm new to ubuntu, so I want to make sure I'm doing it correctly before beginning..

---

### Post by Bashing-om on 2014-01-16
j88n;
Still fairly sure we need to (re-)install "dpkg". 
Post 98 just to make sure, in spite of all indications it will fail, but to cover the base, see if clearing available has any effect.
Then I am all for the (re-)install.
Never having done it myself, will be a learning experience for me also.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-16
sean@Sean-Monster:~$ ls -la /var/lib/dpkg/available
-rw-r--r-- 1 root root 1978421 Jan  5 16:09 /var/lib/dpkg/available

sean@Sean-Monster:~$ sudo dpkg --clear-avail
[sudo] password for sean: 

sean@Sean-Monster:~$ sudo apt-get update
```
Hit http://archive.canonical.com precise Release.gpg
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://ftp.utexas.edu precise Release.gpg                                 
Hit http://archive.canonical.com precise Release
Hit http://extras.ubuntu.com precise Release                          
Get:2 http://ftp.utexas.edu precise-updates Release.gpg [198 B]       
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main amd64 Packages              
Ign http://archive.canonical.com precise/partner TranslationIndex     
Ign http://extras.ubuntu.com precise/main TranslationIndex            
Get:3 http://ftp.utexas.edu precise-security Release.gpg [198 B]
Hit http://ftp.utexas.edu precise Release                                      
Get:4 http://ftp.utexas.edu precise-updates Release [49.6 kB]                  
Get:5 http://ftp.utexas.edu precise-security Release [49.6 kB]                 
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en               
Hit http://ftp.utexas.edu precise/main Sources  
Hit http://ftp.utexas.edu precise/restricted Sources
Hit http://ftp.utexas.edu precise/universe Sources
Hit http://ftp.utexas.edu precise/multiverse Sources
Hit http://ftp.utexas.edu precise/main amd64 Packages
Hit http://ftp.utexas.edu precise/restricted amd64 Packages
Hit http://ftp.utexas.edu precise/universe amd64 Packages
Hit http://ftp.utexas.edu precise/multiverse amd64 Packages
Hit http://ftp.utexas.edu precise/main TranslationIndex
Hit http://ftp.utexas.edu precise/multiverse TranslationIndex
Hit http://ftp.utexas.edu precise/restricted TranslationIndex
Hit http://ftp.utexas.edu precise/universe TranslationIndex
Get:6 http://ftp.utexas.edu precise-updates/main Sources [448 kB]
Get:7 http://ftp.utexas.edu precise-updates/restricted Sources [7,039 B]
Get:8 http://ftp.utexas.edu precise-updates/universe Sources [101 kB]  
Get:9 http://ftp.utexas.edu precise-updates/multiverse Sources [8,486 B]
Get:10 http://ftp.utexas.edu precise-updates/main amd64 Packages [744 kB]
Get:11 http://ftp.utexas.edu precise-updates/restricted amd64 Packages [11.4 kB]
Get:12 http://ftp.utexas.edu precise-updates/universe amd64 Packages [230 kB]  
Get:13 http://ftp.utexas.edu precise-updates/multiverse amd64 Packages [14.2 kB]
Get:14 http://ftp.utexas.edu precise-updates/main TranslationIndex [3,564 B]   
Get:15 http://ftp.utexas.edu precise-updates/multiverse TranslationIndex [2,605 B]
Get:16 http://ftp.utexas.edu precise-updates/restricted TranslationIndex [2,461 B]
Get:17 http://ftp.utexas.edu precise-updates/universe TranslationIndex [2,850 B]
Get:18 http://ftp.utexas.edu precise-security/main Sources [96.3 kB]           
Get:19 http://ftp.utexas.edu precise-security/restricted Sources [2,494 B]     
Get:20 http://ftp.utexas.edu precise-security/universe Sources [30.5 kB]       
Get:21 http://ftp.utexas.edu precise-security/multiverse Sources [1,797 B]     
Get:22 http://ftp.utexas.edu precise-security/main amd64 Packages [356 kB]     
Get:23 http://ftp.utexas.edu precise-security/restricted amd64 Packages [4,627 B]
Get:24 http://ftp.utexas.edu precise-security/universe amd64 Packages [89.3 kB]
Get:25 http://ftp.utexas.edu precise-security/multiverse amd64 Packages [2,454 B]
Get:26 http://ftp.utexas.edu precise-security/main TranslationIndex [74 B]     
Get:27 http://ftp.utexas.edu precise-security/multiverse TranslationIndex [72 B]
Get:28 http://ftp.utexas.edu precise-security/restricted TranslationIndex [72 B]
Get:29 http://ftp.utexas.edu precise-security/universe TranslationIndex [73 B] 
Hit http://ftp.utexas.edu precise/main Translation-en                          
Hit http://ftp.utexas.edu precise/multiverse Translation-en                    
Hit http://ftp.utexas.edu precise/restricted Translation-en                    
Hit http://ftp.utexas.edu precise/universe Translation-en                      
Get:30 http://ftp.utexas.edu precise-updates/main Translation-en [334 kB]      
Hit http://ftp.utexas.edu precise-updates/multiverse Translation-en            
Hit http://ftp.utexas.edu precise-updates/restricted Translation-en            
Get:31 http://ftp.utexas.edu precise-updates/universe Translation-en [135 kB]  
Get:32 http://ftp.utexas.edu precise-security/main Translation-en [167 kB]     
Hit http://ftp.utexas.edu precise-security/multiverse Translation-en           
Hit http://ftp.utexas.edu precise-security/restricted Translation-en           
Get:33 http://ftp.utexas.edu precise-security/universe Translation-en [55.6 kB]
Fetched 2,951 kB in 14s (202 kB/s) 
Reading package lists... Done

```



sean@Sean-Monster:~$ ls -la /var/lib/dpkg/available
-rw-r--r-- 1 root root 1978421 Jan  5 16:09 /var/lib/dpkg/available

sean@Sean-Monster:~$ dpkg -l gedit
Bus error (core dumped)

---

### Post by Bashing-om on 2014-01-16
j88n; That is all she wrote;

(RE-)Install "dpkg" .
As per the norm, it is late here (later your time huh ) my thinking is not up to par, will look over and advise on our next after I am sure; else.
spencer the great or other with that experience may chime in here with a helping hand.

[INDENT][INDENT]look'n first prior to
[INDENT][INDENT][INDENT][INDENT]the LeaP
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by spencer the great on 2014-01-17
I don't think I read the whole thread, so pardon me for asking this (again?), but does dpkg -i <package> work?
If not, then your dpkg is broken and it shouldn't hurt to reinstall it by hand. Also, when I said download the dpkg package, I meant use the dpkg package in your /var/cache/apt directory.

The reason why I said the last method was a bit more dangerous is because it overwrites some files in /sbin and in /usr/sbin.  I'm not sure if these files belong to the dpkg package, so it would really help if someone found out what package owns the files /sbin/start-stop-daemon and /usr/sbin/install-info:
```
$ dpkg -S /usr/sbin/install-info
$ dpkg -S /sbin/start-stop-daemon
```

EDIT: Alright, I googled it and tested it a bit, and I don't think rewriting those should be a problem, as the ones provided by the dpkg package should work just fine. At least, they did on my system...

So, again, make backups of your /usr/bin/dpkg*, those two files I mentioned above, and /usr/bin/update-alternatives, and proceed with the first solution. If that doesn't work, do the more risky one at the end. If THAT doesn't work, curse your bad luck and we'll have to think of something else, but if nothing else broke during the process, you should be able to get away with not restoring the old versions.

---

### Post by Bashing-om on 2014-01-17
@ spencer the great; Thanks !

Sounds like a plan to me.

I will await your advisement on how to down load those binaries.

[INDENT][INDENT]it is all a learning experience
[/INDENT][/INDENT]

---

### Post by spencer the great on 2014-01-19
Like I said, the package should be in /var/cache/apt.  As apt is the program that dl's the packages, and it isn't corrupt, the dpkg package file should be fine.  It's either in /var/cache/apt or /var/cache/apt/archive and should be a deb package. If that doesn't work, try using apt to redownload the package. If THAT doesn't work, you could download the package from another source, like here: [http://packages.debian.org/search?keywords=dpkg](http://packages.debian.org/search?keywords=dpkg)

---

### Post by Bashing-om on 2014-01-19
@ spencer the great ;
Noted thanks, your help and guidance here is great. To this time my experience for obtaining a particular package is:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
From that source all I know to use to install is "dpkg".

We will work through this and all will be good !

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-20
Okay, I'm back! I wanted to make sure I could do this when I had some real time, just in case it went poorly. Just so everyone knows what I did...

Unfortunately, I wasn't able to back up dpkg because I got a read error. I decided to move forward, because it's probably worthless to keep the broke version of dpkg anyway...
1. I downloaded dpkg_1.16.12ubuntu1_amd64.deb from [http://packages.ubuntu.com/saucy/dpkg](http://packages.ubuntu.com/saucy/dpkg)
2. Ran the following commands (as suggested by spencer):

$ mkdir dpkg
$ cd dpkg
$ ar x ~/Downloads/dpkg_1.16.12ubuntu1_amd64.deb

3. I ran ls and verified that I know have control.tar.gz, data.tar.gz, and debian-binary listed in the directory.
4.  Then ran the following:

$ tar xvf data.tar.gz
$ cp usr/bin/dpkg* /usr/bin/

...and basically got this output for every "copied" file
cp: `/usr/bin/dpkg-trigger' and `/usr/bin/dpkg-trigger' are the same file
cp: `/usr/bin/dpkg-vendor' and `/usr/bin/dpkg-vendor' are the same file


Did I do something wrong, or is this common output if the file is named the same?? Is there something else I should try/test?

---

### Post by Bashing-om on 2014-01-20
j88n; Hang'n with you.

If I am not much mistaken: "http://packages.ubuntu.com/saucy/dpkg" are binaries in nature, and as such are subject to "dpkg" for installation on the system. - ie: dpkg -i -

Let's await advisement from the source Edward before taking action.

I also remain very interested in the method to affect this restoration.

[INDENT][INDENT]it is nice to know
[INDENT][INDENT][INDENT]a means exist
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by spencer the great on 2014-01-20
Hm. I can't really think of any explanation other than, maybe you typed the source file wrong and put a slash in front of the path? That's kinda what it looks like.

---

### Post by j88n on 2014-01-20
Okay... so I actually did include the slash when I typed it in the command line... After examining more. I think there were issues of the newly extracted folder/files being the same name as the /usr/bin/ directory, so I renamed the newly extracted folders dpkg -> dpkg2 usr ->usr2 and ran the copy command again and the copying part worked... any ideas what I should do now?

---

### Post by j88n on 2014-01-20
So out of curiousity, I ran this: 

sudo dpkg --configure -a

but got this output:
Unknown configuration key `foreign-architecture' found in your `dpkg'
configuration files.  This warning will become a hard error at a later
date, so please remove the offending configuration options and replace
them with `dpkg --add-architecture' invocations at the command line.


Thoughts..?

---

### Post by Bashing-om on 2014-01-20
j88n; hey,

I have never encountered that error, do not know what impending problems it may be referring to, as I believe full multi-arch compatibility has been established for your system (?)
At this point I would suggest just to plow ahead and see if you can get "dpkg" (RE-)installed; and deal with the results as they come up. 

[INDENT][INDENT][INDENT]no easy way out
[/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-20
Perhaps I am confused, but I thought extracting the files manually was re-installing dpkg..

---

### Post by Bashing-om on 2014-01-20
j88n; Welp,

I am stepping into waters over my head, but until those files that have been extracted properly replace the "other" files;

The job ain't done.

I bet we learn a fine appreciation of "dpkg" in it's role of package management before this is all over. What file goes where and what dependencies are extent !

Until "dpkg" is functional, I am dead in the water.
[INDENT][INDENT]sometimes I do not know
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-20
In post #112, I explained that I was able to replace the files... so I think that's good news

---

### Post by j88n on 2014-01-20
I really think I'm in a better place... so I was able to rid that multi-arch error by going to the file "multiarch" in the directory: "/etc/dpkg/dpkg.cfg.d/" and commenting out the line: "[FONT=Ubuntu Mono]foreign-architecture"

Now I decided to run some of the commands for the beginning of this post:

sudo apt-get autoclean
```
[/FONT]sean@Sean-Monster:~$ sudo apt-get autocleanReading package lists... Done
Building dependency tree       
Reading state information... Done
[FONT=Ubuntu Mono]
```

sudo apt-get autoremove
```
[/FONT]sean@Sean-Monster:~$ sudo apt-get autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 bluez-cups : Depends: cups but it is not installed
 console-setup : Depends: keyboard-configuration but it is not installed
 hplip : Depends: cups (>= 1.1.20) but it is not installed
 indicator-printers : Depends: cups (>= 1.5) but it is not installed
 lirc : Depends: setserial but it is not installed
 printer-driver-gutenprint : Depends: cups (>= 1.3.0) but it is not installed
 printer-driver-hpcups : Depends: cups but it is not installed
 xserver-xorg-core-lts-raring : Depends: keyboard-configuration but it is not installed
E: Unmet dependencies. Try using -f.
[FONT=Ubuntu Mono]
```

So I decided to run: sudo apt-get -f install
```
[/FONT]sean@Sean-Monster:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpam-winbind libnet-ssleay-perl ttf-umefont gnome-exe-thumbnailer
  gir1.2-ubuntuoneui-3.0 liburi-perl libhtml-parser-perl libhttp-daemon-perl
  libfont-afm-perl libhttp-negotiate-perl libfile-listing-perl
  libhtml-form-perl libcapi20-3 libhtml-tree-perl libencode-locale-perl
  libhttp-date-perl libmailtools-perl wine-gecko2.24
  liblwp-protocol-https-perl wine-gecko1.4 libhttp-cookies-perl winetricks
  libosmesa6 libhttp-message-perl libnet-http-perl icoutils wine-mono4.5.2
  libhtml-format-perl libubuntuoneui-3.0-1 libsocket6-perl ttf-unfonts-core
  libmpg123-0 thunderbird-globalmenu libhtml-tagset-perl libwww-perl winbind
  fonts-droid libio-socket-ssl-perl libwww-robotrules-perl
  liblwp-mediatypes-perl ttf-droid libio-socket-inet6-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cups keyboard-configuration setserial
Suggested packages:
  cups-pdf
The following NEW packages will be installed:
  cups keyboard-configuration setserial
0 upgraded, 3 newly installed, 0 to remove and 80 not upgraded.
Need to get 0 B/1,863 kB of archives.
After this operation, 6,698 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously unselected package cups.
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 270474 files and directories currently installed.)
Unpacking cups (from .../cups_1.5.3-0ubuntu8_amd64.deb) ...
Selecting previously unselected package keyboard-configuration.
Unpacking keyboard-configuration (from .../keyboard-configuration_1.70ubuntu5_all.deb) ...
Selecting previously unselected package setserial.
Unpacking setserial (from .../setserial_2.17-46_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Setting up cups (1.5.3-0ubuntu8) ...
Updating PPD files for cups ...
Setting up keyboard-configuration (1.70ubuntu5) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: deferring update (trigger activated)
Setting up setserial (2.17-46) ...
update-rc.d: warning: etc-setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: warning: setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: warning: etc-setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: warning: setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
[FONT=Ubuntu Mono]
```

What next?[/FONT]

---

### Post by Bashing-om on 2014-01-20
j88n; OK !

Let's check dpkg's integrity;
```

dpkg -l dpkg
dpkg -L dpkg
dpkg -s dpkg
dpkg -S dpkg
dpkg -l gedit
dpkg -l xorg
dpkg -S gedit

```
Not real interested presently in what returns, just that it does return meaningful output and NO ERRORS.

Then we can run the update/upgrade routines and see what errors there to be dealt with.


maybe this time ->
[INDENT][INDENT][INDENT]it's a big step forward
[/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-20
dpkg -l dpkg
```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  dpkg           1.16.1.2ubun amd64        Debian package management system

```

dpkg -L dpkg
```
/./usr
/usr/share
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/dpkg-statoverride.8.gz
/usr/share/man/man8/start-stop-daemon.8.gz
/usr/share/man/man8/dpkg-divert.8.gz
/usr/share/man/man8/update-alternatives.8.gz
/usr/share/man/es
/usr/share/man/es/man8
/usr/share/man/es/man8/dpkg-statoverride.8.gz
/usr/share/man/es/man8/dpkg-divert.8.gz
/usr/share/man/es/man8/update-alternatives.8.gz
/usr/share/man/es/man5
/usr/share/man/es/man5/dpkg.cfg.5.gz
/usr/share/man/es/man1
/usr/share/man/es/man1/dpkg-query.1.gz
/usr/share/man/es/man1/dpkg-maintscript-helper.1.gz
/usr/share/man/es/man1/dpkg-trigger.1.gz
/usr/share/man/es/man1/dpkg-deb.1.gz
/usr/share/man/es/man1/dpkg-split.1.gz
/usr/share/man/es/man1/dpkg.1.gz
/usr/share/man/hu
/usr/share/man/hu/man5
/usr/share/man/hu/man5/dpkg.cfg.5.gz
/usr/share/man/man5
/usr/share/man/man5/dpkg.cfg.5.gz
/usr/share/man/fr
/usr/share/man/fr/man8
/usr/share/man/fr/man8/dpkg-statoverride.8.gz
/usr/share/man/fr/man8/dpkg-divert.8.gz
/usr/share/man/fr/man8/update-alternatives.8.gz
/usr/share/man/fr/man5
/usr/share/man/fr/man5/dpkg.cfg.5.gz
/usr/share/man/fr/man1
/usr/share/man/fr/man1/dpkg-query.1.gz
/usr/share/man/fr/man1/dpkg-maintscript-helper.1.gz
/usr/share/man/fr/man1/dpkg-trigger.1.gz
/usr/share/man/fr/man1/dpkg-deb.1.gz
/usr/share/man/fr/man1/dpkg-split.1.gz
/usr/share/man/fr/man1/dpkg.1.gz
/usr/share/man/pl
/usr/share/man/pl/man8
/usr/share/man/pl/man8/dpkg-statoverride.8.gz
/usr/share/man/pl/man8/dpkg-divert.8.gz
/usr/share/man/pl/man8/update-alternatives.8.gz
/usr/share/man/pl/man5
/usr/share/man/pl/man5/dpkg.cfg.5.gz
/usr/share/man/pl/man1
/usr/share/man/pl/man1/dpkg-trigger.1.gz
/usr/share/man/pl/man1/dpkg-deb.1.gz
/usr/share/man/pl/man1/dpkg-split.1.gz
/usr/share/man/pl/man1/dpkg.1.gz
/usr/share/man/de
/usr/share/man/de/man8
/usr/share/man/de/man8/dpkg-statoverride.8.gz
/usr/share/man/de/man8/start-stop-daemon.8.gz
/usr/share/man/de/man8/dpkg-divert.8.gz
/usr/share/man/de/man8/update-alternatives.8.gz
/usr/share/man/de/man5
/usr/share/man/de/man5/dpkg.cfg.5.gz
/usr/share/man/de/man1
/usr/share/man/de/man1/dpkg-query.1.gz
/usr/share/man/de/man1/dpkg-maintscript-helper.1.gz
/usr/share/man/de/man1/dpkg-trigger.1.gz
/usr/share/man/de/man1/dpkg-deb.1.gz
/usr/share/man/de/man1/dpkg-split.1.gz
/usr/share/man/de/man1/dpkg.1.gz
/usr/share/man/man1
/usr/share/man/man1/dpkg-query.1.gz
/usr/share/man/man1/dpkg-maintscript-helper.1.gz
/usr/share/man/man1/dpkg-trigger.1.gz
/usr/share/man/man1/dpkg-deb.1.gz
/usr/share/man/man1/dpkg-split.1.gz
/usr/share/man/man1/dpkg.1.gz
/usr/share/man/sv
/usr/share/man/sv/man8
/usr/share/man/sv/man8/dpkg-statoverride.8.gz
/usr/share/man/sv/man8/start-stop-daemon.8.gz
/usr/share/man/sv/man8/dpkg-divert.8.gz
/usr/share/man/sv/man8/update-alternatives.8.gz
/usr/share/man/sv/man5
/usr/share/man/sv/man5/dpkg.cfg.5.gz
/usr/share/man/sv/man1
/usr/share/man/sv/man1/dpkg-query.1.gz
/usr/share/man/sv/man1/dpkg-maintscript-helper.1.gz
/usr/share/man/sv/man1/dpkg-trigger.1.gz
/usr/share/man/sv/man1/dpkg-deb.1.gz
/usr/share/man/sv/man1/dpkg-split.1.gz
/usr/share/man/sv/man1/dpkg.1.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/dpkg
/usr/share/doc
/usr/share/doc/dpkg
/usr/share/doc/dpkg/usertags.gz
/usr/share/doc/dpkg/copyright
/usr/share/doc/dpkg/README.feature-removal-schedule
/usr/share/doc/dpkg/AUTHORS
/usr/share/doc/dpkg/changelog.Debian.gz
/usr/share/doc/dpkg/THANKS.gz
/usr/share/dpkg
/usr/share/dpkg/cputable
/usr/share/dpkg/abitable
/usr/share/dpkg/ostable
/usr/share/dpkg/archtable
/usr/share/dpkg/triplettable
/usr/share/locale
/usr/share/locale/vi
/usr/share/locale/vi/LC_MESSAGES
/usr/share/locale/vi/LC_MESSAGES/dpkg.mo
/usr/share/locale/nn
/usr/share/locale/nn/LC_MESSAGES
/usr/share/locale/nn/LC_MESSAGES/dpkg.mo
/usr/share/locale/pt
/usr/share/locale/pt/LC_MESSAGES
/usr/share/locale/pt/LC_MESSAGES/dpkg.mo
/usr/share/locale/ca
/usr/share/locale/ca/LC_MESSAGES
/usr/share/locale/ca/LC_MESSAGES/dpkg.mo
/usr/share/locale/zh_CN
/usr/share/locale/zh_CN/LC_MESSAGES
/usr/share/locale/zh_CN/LC_MESSAGES/dpkg.mo
/usr/share/locale/pa
/usr/share/locale/pa/LC_MESSAGES
/usr/share/locale/pa/LC_MESSAGES/dpkg.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/dpkg.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/dpkg.mo
/usr/share/locale/ku
/usr/share/locale/ku/LC_MESSAGES
/usr/share/locale/ku/LC_MESSAGES/dpkg.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/dpkg.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/dpkg.mo
/usr/share/locale/bs
/usr/share/locale/bs/LC_MESSAGES
/usr/share/locale/bs/LC_MESSAGES/dpkg.mo
/usr/share/locale/id
/usr/share/locale/id/LC_MESSAGES
/usr/share/locale/id/LC_MESSAGES/dpkg.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/dpkg.mo
/usr/share/locale/km
/usr/share/locale/km/LC_MESSAGES
/usr/share/locale/km/LC_MESSAGES/dpkg.mo
/usr/share/locale/eo
/usr/share/locale/eo/LC_MESSAGES
/usr/share/locale/eo/LC_MESSAGES/dpkg.mo
/usr/share/locale/ko
/usr/share/locale/ko/LC_MESSAGES
/usr/share/locale/ko/LC_MESSAGES/dpkg.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/dpkg.mo
/usr/share/locale/tl
/usr/share/locale/tl/LC_MESSAGES
/usr/share/locale/tl/LC_MESSAGES/dpkg.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/dpkg.mo
/usr/share/locale/et
/usr/share/locale/et/LC_MESSAGES
/usr/share/locale/et/LC_MESSAGES/dpkg.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/dpkg.mo
/usr/share/locale/dz
/usr/share/locale/dz/LC_MESSAGES
/usr/share/locale/dz/LC_MESSAGES/dpkg.mo
/usr/share/locale/nb
/usr/share/locale/nb/LC_MESSAGES
/usr/share/locale/nb/LC_MESSAGES/dpkg.mo
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/dpkg.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/dpkg.mo
/usr/share/locale/eu
/usr/share/locale/eu/LC_MESSAGES
/usr/share/locale/eu/LC_MESSAGES/dpkg.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/dpkg.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/dpkg.mo
/usr/share/locale/el
/usr/share/locale/el/LC_MESSAGES
/usr/share/locale/el/LC_MESSAGES/dpkg.mo
/usr/share/locale/ro
/usr/share/locale/ro/LC_MESSAGES
/usr/share/locale/ro/LC_MESSAGES/dpkg.mo
/usr/share/locale/lt
/usr/share/locale/lt/LC_MESSAGES
/usr/share/locale/lt/LC_MESSAGES/dpkg.mo
/usr/share/locale/sk
/usr/share/locale/sk/LC_MESSAGES
/usr/share/locale/sk/LC_MESSAGES/dpkg.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/dpkg.mo
/usr/share/locale/mr
/usr/share/locale/mr/LC_MESSAGES
/usr/share/locale/mr/LC_MESSAGES/dpkg.mo
/usr/share/locale/ast
/usr/share/locale/ast/LC_MESSAGES
/usr/share/locale/ast/LC_MESSAGES/dpkg.mo
/usr/share/locale/th
/usr/share/locale/th/LC_MESSAGES
/usr/share/locale/th/LC_MESSAGES/dpkg.mo
/usr/share/locale/gl
/usr/share/locale/gl/LC_MESSAGES
/usr/share/locale/gl/LC_MESSAGES/dpkg.mo
/usr/share/locale/ne
/usr/share/locale/ne/LC_MESSAGES
/usr/share/locale/ne/LC_MESSAGES/dpkg.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/dpkg.mo
/usr/sbin
/usr/sbin/install-info
/usr/bin
/usr/bin/update-alternatives
/usr/bin/dpkg-statoverride
/usr/bin/dpkg-divert
/usr/bin/dpkg-trigger
/usr/bin/dpkg-maintscript-helper
/usr/bin/dpkg-split
/usr/bin/dpkg-deb
/usr/bin/dpkg
/usr/bin/dpkg-query
/etc
/etc/alternatives
/etc/alternatives/README
/etc/cron.daily
/etc/cron.daily/dpkg
/etc/logrotate.d
/etc/logrotate.d/dpkg
/etc/dpkg
/etc/dpkg/dpkg.cfg
/etc/dpkg/dpkg.cfg.d
/etc/dpkg/dpkg.cfg.d/multiarch
/sbin
/sbin/start-stop-daemon
/var
/var/lib
/var/lib/dpkg
/var/lib/dpkg/info
/var/lib/dpkg/alternatives
/var/lib/dpkg/updates
/var/lib/dpkg/parts
/usr/sbin/update-alternatives
/usr/sbin/dpkg-statoverride
/usr/sbin/dpkg-divert

```

dpkg -s dpkg
```
Package: dpkgEssential: yes
Status: install ok installed
Priority: required
Section: admin
Installed-Size: 5931
Origin: debian
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: debbugs://bugs.debian.org
Architecture: amd64
Multi-Arch: foreign
Version: 1.16.1.2ubuntu7.2
Pre-Depends: libbz2-1.0, libc6 (>= 2.14), libselinux1 (>= 1.32), zlib1g (>= 1:1.1.4), coreutils (>= 5.93-1), tar (>= 1.23), xz-utils
Suggests: apt
Breaks: apt (<< 0.7.7), aptitude (<< 0.4.7-1), dpkg-dev (<< 1.15.8), libdpkg-perl (<< 1.15.8), pinfo (<< 0.6.9-3.1), tkinfo (<< 2.8-3.1)
Conffiles:
 /etc/alternatives/README 69c4ba7f08363e998e0f2e244a04f881
 /etc/cron.daily/dpkg b6b8dc21210ea50db7cc4636f521758f
 /etc/logrotate.d/dpkg 782ea5ae536f67ff51dc8c3e2eeb4cf9
 /etc/dpkg/dpkg.cfg f4413ffb515f8f753624ae3bb365b81b
 /etc/dpkg/dpkg.cfg.d/multiarch e018c53338191b34f943e2b38e160d1a
Description: Debian package management system
 This package provides the low-level infrastructure for handling the
 installation and removal of Debian software packages.
 .
 For Debian package development tools, install dpkg-dev.
Homepage: http://wiki.debian.org/Teams/Dpkg
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>

```

dpkg -S dpkg
```
dpkg-query: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installeddpkg: /usr/share/locale/sv/LC_MESSAGES/dpkg.mo
libghc-dpkg-dev: /usr/share/doc/libghc-dpkg-dev/changelog.Debian.gz
libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/libHSdpkg-0.0.1_p.a
dpkg: /var/lib/dpkg/alternatives
dpkg-dev: /usr/share/man/es/man1/dpkg-scansources.1.gz
dpkg-dev: /usr/share/man/sv/man1/dpkg-buildpackage.1.gz
dpkg: /usr/share/locale/ko/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/es/man1/dpkg-architecture.1.gz
dpkg: /usr/share/man/de/man1/dpkg-trigger.1.gz
dpkg-dev: /usr/bin/dpkg-scansources
dpkg-dev: /etc/dpkg/shlibs.default
dpkg-dev: /usr/share/doc/dpkg-dev/copyright
dpkg, base-files: /var/lib/dpkg
dpkg-dev: /usr/share/man/de/man1/dpkg-architecture.1.gz
dpkg: /usr/share/man/de/man8/dpkg-divert.8.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-gensymbols.1.gz
dpkg-dev: /usr/share/doc/dpkg-dev/THANKS.gz
dpkg-dev: /usr/share/man/es/man1/dpkg-mergechangelogs.1.gz
dpkg: /var/lib/dpkg/updates
dpkg: /usr/share/locale/ast/LC_MESSAGES/dpkg.mo
dpkg: /usr/bin/dpkg-trigger
dpkg-dev: /usr/share/dpkg/default.mk
dpkg-dev: /usr/share/man/es/man1/dpkg-name.1.gz
dpkg-dev: /usr/share/dpkg/buildflags.mk
dpkg-dev: /usr/bin/dpkg-buildflags
dpkg-dev: /usr/bin/dpkg-name
dpkg: /usr/share/doc/dpkg/README.feature-removal-schedule
libdpkg-perl: /usr/lib/dpkg/parsechangelog/debian
libghc-dpkg-dev, libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian
libghc-dpkg-dev, libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg
debconf-i18n: /usr/share/man/de/man8/dpkg-reconfigure.8.gz
debconf: /usr/sbin/dpkg-preconfigure
dpkg-dev: /usr/share/man/sv/man1/dpkg-architecture.1.gz
dpkg-dev: /usr/share/man/man1/dpkg-checkbuilddeps.1.gz
debconf: /usr/share/man/man8/dpkg-preconfigure.8.gz
dpkg: /usr/share/man/man1/dpkg-maintscript-helper.1.gz
libghc-dpkg-dev: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg/DB.hi
dpkg: /usr/share/locale/es/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/es/man1/dpkg-vendor.1.gz
dpkg-dev: /usr/bin/dpkg-vendor
dpkg-dev: /usr/share/man/es/man1/dpkg-source.1.gz
dpkg-dev: /usr/share/man/de/man1/dpkg-gensymbols.1.gz
base-files: /etc/dpkg/origins
dpkg-dev: /etc/dpkg/shlibs.override
debconf-i18n: /usr/share/man/fr/man8/dpkg-reconfigure.8.gz
debconf-i18n: /usr/share/man/ru/man8/dpkg-reconfigure.8.gz
dpkg: /usr/share/man/es/man1/dpkg-query.1.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-shlibdeps.1.gz
dpkg-dev: /usr/share/man/sv/man1/dpkg-genchanges.1.gz
libghc-dpkg-dev: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/libHSdpkg-0.0.1.a
dpkg: /usr/share/man/fr/man8/dpkg-statoverride.8.gz
dpkg-dev: /usr/share/man/man1/dpkg-parsechangelog.1.gz
dpkg-dev: /usr/share/man/man1/dpkg-gencontrol.1.gz
dpkg: /usr/share/locale/eo/LC_MESSAGES/dpkg.mo
apt, libdpkg-perl: /usr/lib/dpkg
dpkg: /usr/share/locale/cs/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/bin/dpkg-buildpackage
dpkg: /usr/share/man/hu/man5/dpkg.cfg.5.gz
dpkg-dev: /usr/share/man/man1/dpkg-scanpackages.1.gz
dpkg: /usr/share/doc/dpkg/usertags.gz
dpkg-dev: /usr/share/man/de/man1/dpkg-scansources.1.gz
dpkg: /usr/share/man/fr/man1/dpkg-maintscript-helper.1.gz
dpkg-dev: /usr/share/lintian/overrides/dpkg-dev
dpkg-dev: /usr/share/man/pl/man1/dpkg-buildpackage.1.gz
dpkg: /usr/share/locale/bs/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/man/es/man8/dpkg-divert.8.gz
dpkg: /usr/share/locale/mr/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/man/de/man1/dpkg-query.1.gz
dpkg: /var/lib/dpkg/parts
dpkg: /usr/share/man/pl/man1/dpkg-deb.1.gz
dpkg-dev: /usr/share/dpkg/pkg-info.mk
dpkg: /usr/share/dpkg/archtable
dpkg-dev: /usr/share/man/fr/man1/dpkg-scansources.1.gz
dpkg-dev: /usr/share/man/es/man1/dpkg-gensymbols.1.gz
dpkg: /usr/share/locale/nn/LC_MESSAGES/dpkg.mo
apt: /usr/lib/dpkg/methods
dpkg, base-files, dpkg-dev: /etc/dpkg
libdpkg-perl: /usr/share/doc/libdpkg-perl/README.api
dpkg-dev: /usr/share/doc/dpkg-dev/triggers.txt.gz
dpkg: /usr/share/locale/pt_BR/LC_MESSAGES/dpkg.mo
apt: /usr/lib/dpkg/methods/apt/setup
language-pack-en-base: /usr/share/locale-langpack/en_GB/LC_MESSAGES/dpkg-dev.mo
libghc-dpkg-dev: /usr/share/doc/libghc-dpkg-dev/copyright
dpkg, dpkg-dev: /usr/share/dpkg
dpkg-dev: /usr/share/man/fr/man1/dpkg-genchanges.1.gz
debconf-i18n: /usr/share/man/ru/man8/dpkg-preconfigure.8.gz
libghc-dpkg-dev: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg/VersionRevision.hi
dpkg-dev: /usr/share/man/fr/man1/dpkg-vendor.1.gz
libghc-dpkg-dev: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg/Enums.hi
checkbox: /usr/share/checkbox/scripts/dpkg_resource
dpkg-dev: /usr/share/man/pl/man1/dpkg-architecture.1.gz
language-pack-en-base: /usr/share/locale-langpack/en_AU/LC_MESSAGES/dpkg-dev.mo
libghc-dpkg-dev: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg.hi
dpkg-dev: /usr/share/man/fr/man1/dpkg-source.1.gz
dpkg: /usr/share/doc/dpkg
dpkg: /usr/share/man/sv/man1/dpkg-deb.1.gz
dpkg: /etc/dpkg/dpkg.cfg.d
dpkg-dev: /usr/share/man/pl/man1/dpkg-scansources.1.gz
dpkg: /usr/share/man/sv/man1/dpkg-maintscript-helper.1.gz
dpkg: /usr/share/locale/ru/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/man/pl/man1/dpkg-trigger.1.gz
dpkg: /usr/share/locale/zh_CN/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/de/man1/dpkg-checkbuilddeps.1.gz
dpkg: /usr/share/man/pl/man5/dpkg.cfg.5.gz
dpkg-dev: /usr/bin/dpkg-source
dpkg-dev: /usr/share/man/sv/man1/dpkg-gencontrol.1.gz
dpkg: /usr/share/man/man1/dpkg.1.gz
dpkg: /usr/share/locale/dz/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/pl/man1/dpkg-genchanges.1.gz
dpkg-dev: /usr/bin/dpkg-mergechangelogs
apt: /usr/lib/dpkg/methods/apt/install
dpkg-dev: /usr/share/man/fr/man1/dpkg-name.1.gz
base-files: /etc/dpkg/origins/debian
dpkg: /usr/share/man/es/man1/dpkg-split.1.gz
dpkg: /etc/logrotate.d/dpkg
dpkg: /usr/share/man/fr/man1/dpkg-deb.1.gz
dpkg: /etc/dpkg/dpkg.cfg.d/multiarch
dpkg: /usr/share/locale/vi/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/fr/man1/dpkg-buildpackage.1.gz
dpkg: /usr/share/man/fr/man8/dpkg-divert.8.gz
dpkg-dev: /usr/bin/dpkg-scanpackages
dpkg-dev: /usr/share/man/sv/man1/dpkg-shlibdeps.1.gz
dpkg: /usr/share/man/sv/man1/dpkg.1.gz
dpkg: /usr/share/man/man8/dpkg-statoverride.8.gz
dpkg-dev: /usr/share/man/de/man1/dpkg-genchanges.1.gz
dpkg: /usr/share/locale/nb/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/man/de/man1/dpkg.1.gz
dpkg-dev: /usr/share/man/de/man1/dpkg-parsechangelog.1.gz
dpkg-dev: /usr/share/dpkg/vendor.mk
dpkg: /usr/share/locale/fr/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/lintian/overrides/dpkg
dpkg-dev: /usr/share/man/sv/man1/dpkg-distaddfile.1.gz
dpkg: /usr/share/man/sv/man5/dpkg.cfg.5.gz
dpkg: /etc/dpkg/dpkg.cfg
libghc-dpkg-dev: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg/Types.hi
dpkg: /usr/share/man/man1/dpkg-trigger.1.gz
dpkg: /usr/share/man/de/man1/dpkg-split.1.gz
dpkg: /usr/share/dpkg/triplettable
language-pack-en-base: /usr/share/locale-langpack/en_GB/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/doc/dpkg-dev/README.api
dpkg-dev: /usr/share/man/man1/dpkg-name.1.gz
dpkg-dev: /usr/share/man/pl/man1/dpkg-shlibdeps.1.gz
dpkg-dev: /usr/share/man/es/man1/dpkg-shlibdeps.1.gz
debconf: /usr/share/man/man8/dpkg-reconfigure.8.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-checkbuilddeps.1.gz
debconf-i18n: /usr/share/man/pt/man8/dpkg-reconfigure.8.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-gencontrol.1.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-architecture.1.gz
dpkg-dev: /usr/share/man/es/man1/dpkg-distaddfile.1.gz
dpkg: /usr/share/dpkg/ostable
dpkg: /usr/share/man/pl/man1/dpkg-split.1.gz
dpkg: /usr/share/man/fr/man1/dpkg-query.1.gz
dpkg: /usr/share/man/fr/man5/dpkg.cfg.5.gz
dpkg-dev: /usr/share/man/es/man1/dpkg-genchanges.1.gz
libghc-dpkg-prof: /usr/share/doc/libghc-dpkg-prof/changelog.Debian.gz
friendly-recovery: /lib/recovery-mode/options/dpkg
dpkg: /usr/share/locale/ku/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/dpkg/cputable
dpkg-dev: /usr/share/man/man1/dpkg-shlibdeps.1.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-parsechangelog.1.gz
libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg/Enums.p_hi
debconf: /usr/sbin/dpkg-reconfigure
dpkg-dev: /usr/share/man/pl/man1/dpkg-gencontrol.1.gz
dpkg-dev: /usr/share/man/man1/dpkg-mergechangelogs.1.gz
dpkg-dev: /usr/share/man/man1/dpkg-buildflags.1.gz
dpkg-dev: /usr/share/man/man1/dpkg-scansources.1.gz
dpkg: /usr/bin/dpkg-query
dpkg: /usr/share/doc/dpkg/AUTHORS
dpkg: /usr/share/man/es/man1/dpkg-trigger.1.gz
libghc-dpkg-dev: /var/lib/ghc/package.conf.d/dpkg-0.0.1.conf
dpkg-dev: /usr/share/man/de/man1/dpkg-gencontrol.1.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-mergechangelogs.1.gz
dpkg: /usr/share/man/sv/man1/dpkg-trigger.1.gz
dpkg: /usr/share/doc/dpkg/copyright
debconf-i18n: /usr/share/man/es/man8/dpkg-preconfigure.8.gz
dpkg: /usr/share/locale/hu/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/man1/dpkg-buildpackage.1.gz
dpkg-dev: /usr/share/man/de/man1/dpkg-shlibdeps.1.gz
debconf-i18n: /usr/share/man/de/man8/dpkg-preconfigure.8.gz
apt: /usr/lib/dpkg/methods/apt/names
dpkg: /usr/share/locale/zh_TW/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/locale/km/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/doc/dpkg/THANKS.gz
debconf-i18n: /usr/share/man/pt/man8/dpkg-preconfigure.8.gz
dpkg-dev: /usr/share/man/man1/dpkg-vendor.1.gz
dpkg-dev: /usr/share/man/man1/dpkg-source.1.gz
dpkg: /usr/share/locale/pa/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/locale/ne/LC_MESSAGES/dpkg.mo
language-pack-en-base: /usr/share/locale-langpack/en_AU/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/bin/dpkg-architecture
dpkg-dev: /usr/share/man/es/man1/dpkg-checkbuilddeps.1.gz
dpkg: /etc/cron.daily/dpkg
dpkg-dev: /usr/share/doc/dpkg-dev
dpkg-dev: /usr/share/man/es/man1/dpkg-scanpackages.1.gz
apt: /usr/lib/dpkg/methods/apt
dpkg-dev: /usr/share/man/de/man1/dpkg-distaddfile.1.gz
dpkg-dev: /usr/share/man/es/man1/dpkg-gencontrol.1.gz
dpkg: /usr/share/locale/eu/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/de/man1/dpkg-scanpackages.1.gz
libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg/VersionRevision.p_hi
dpkg: /usr/share/locale/tl/LC_MESSAGES/dpkg.mo
libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg/DB.p_hi
dpkg: /usr/share/locale/pt/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/bin/dpkg-gensymbols
dpkg-dev: /usr/share/man/man1/dpkg-architecture.1.gz
libdpkg-perl: /usr/share/doc/libdpkg-perl/README.feature-removal-schedule
dpkg: /usr/share/man/fr/man1/dpkg-split.1.gz
dpkg-dev: /usr/share/man/de/man1/dpkg-mergechangelogs.1.gz
dpkg-dev: /usr/bin/dpkg-genchanges
libdpkg-perl: /usr/share/doc/libdpkg-perl/changelog.Debian.gz
dpkg: /usr/share/man/man8/dpkg-divert.8.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-distaddfile.1.gz
dpkg-dev: /usr/share/man/es/man1/dpkg-parsechangelog.1.gz
dpkg: /usr/bin/dpkg-split
dpkg-dev: /usr/share/man/sv/man1/dpkg-buildflags.1.gz
dpkg: /usr/share/locale/th/LC_MESSAGES/dpkg.mo
bash-completion: /etc/bash_completion.d/dpkg
dpkg-dev: /usr/share/man/pl/man1/dpkg-name.1.gz
dpkg: /usr/bin/dpkg-maintscript-helper
dpkg-dev: /usr/share/man/sv/man1/dpkg-scanpackages.1.gz
dpkg: /usr/share/man/man1/dpkg-deb.1.gz
dpkg: /usr/share/man/es/man1/dpkg-deb.1.gz
dpkg: /usr/share/man/es/man1/dpkg.1.gz
dpkg: /usr/share/locale/pl/LC_MESSAGES/dpkg.mo
dpkg: /usr/bin/dpkg-statoverride
dpkg-dev: /usr/share/man/pl/man1/dpkg-distaddfile.1.gz
dpkg: /usr/share/locale/lt/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/sv/man1/dpkg-vendor.1.gz
dpkg-dev: /usr/share/man/sv/man1/dpkg-source.1.gz
dpkg: /usr/share/locale/ja/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/bin/dpkg-parsechangelog
dpkg: /usr/share/dpkg/abitable
apt: /usr/lib/dpkg/methods/apt/update
dpkg-dev: /usr/share/man/sv/man1/dpkg-checkbuilddeps.1.gz
dpkg-dev: /usr/share/doc/dpkg-dev/README.feature-removal-schedule
dpkg: /usr/share/locale/nl/LC_MESSAGES/dpkg.mo
libdpkg-perl: /usr/lib/dpkg/parsechangelog
dpkg: /usr/share/man/de/man1/dpkg-deb.1.gz
language-pack-en-base: /usr/share/locale-langpack/en_CA/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/dpkg/architecture.mk
dpkg: /usr/share/man/man1/dpkg-query.1.gz
apport: /usr/share/apport/testsuite/test_backend_apt_dpkg.py
dpkg: /usr/share/man/es/man8/dpkg-statoverride.8.gz
dpkg: /usr/share/locale/it/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/de/man1/dpkg-name.1.gz
dpkg: /usr/share/man/sv/man8/dpkg-divert.8.gz
dpkg-dev: /usr/share/doc/dpkg-dev/usertags.gz
dpkg: /usr/share/man/man5/dpkg.cfg.5.gz
dpkg: /usr/share/man/de/man8/dpkg-statoverride.8.gz
base-files: /etc/dpkg/origins/ubuntu
dpkg-dev: /usr/share/man/pl/man1/dpkg-checkbuilddeps.1.gz
dpkg-dev: /usr/share/man/sv/man1/dpkg-parsechangelog.1.gz
dpkg: /usr/share/man/es/man5/dpkg.cfg.5.gz
dpkg-dev: /usr/share/man/man1/dpkg-gensymbols.1.gz
dpkg: /usr/share/man/fr/man1/dpkg-trigger.1.gz
dpkg-dev: /usr/share/doc/dpkg-dev/changelog.Debian.gz
dpkg: /usr/bin/dpkg-divert
dpkg-dev: /usr/share/man/pl/man1/dpkg-vendor.1.gz
dpkg: /usr/share/locale/de/LC_MESSAGES/dpkg.mo
dpkg: /var/lib/dpkg/info
dpkg: /usr/share/man/sv/man1/dpkg-query.1.gz
dpkg: /usr/share/man/es/man1/dpkg-maintscript-helper.1.gz
libdpkg-perl: /usr/share/doc/libdpkg-perl
dpkg: /usr/sbin/dpkg-statoverride
debconf-i18n: /usr/share/man/pt_BR/man8/dpkg-preconfigure.8.gz
libghc-dpkg-dev: /usr/share/doc/libghc-dpkg-dev
libghc-dpkg-dev, libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1
libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg.p_hi
dpkg-dev: /usr/share/man/pl/man1/dpkg-parsechangelog.1.gz
dpkg: /usr/share/man/pl/man1/dpkg.1.gz
libghc-dpkg-dev: /usr/share/doc/libghc-dpkg-dev/README
dpkg-dev: /usr/share/man/de/man1/dpkg-buildflags.1.gz
dpkg: /usr/share/man/sv/man8/dpkg-statoverride.8.gz
libghc-dpkg-prof: /usr/share/doc/libghc-dpkg-prof/README
dpkg: /usr/share/man/de/man5/dpkg.cfg.5.gz
dpkg: /usr/share/locale/da/LC_MESSAGES/dpkg.mo
libdpkg-perl: /usr/share/doc/libdpkg-perl/AUTHORS
python-debian: /usr/share/doc/python-debian/examples/debfile/dpkg-info
xdiagnose: /usr/bin/dpkg-log-summary
dpkg: /usr/share/man/pl/man8/dpkg-divert.8.gz
dpkg: /usr/share/locale/et/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/doc/dpkg/changelog.Debian.gz
dpkg: /usr/share/locale/ro/LC_MESSAGES/dpkg.mo
libghc-dpkg-prof: /usr/share/doc/libghc-dpkg-prof/copyright
libdpkg-perl: /usr/share/lintian/overrides/libdpkg-perl
libghc-dpkg-dev: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/HSdpkg-0.0.1.o
dpkg: /usr/share/locale/ca/LC_MESSAGES/dpkg.mo
libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1/ghc-7.4.1/Debian/Dpkg/Types.p_hi
dpkg: /usr/share/locale/sk/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/man/de/man1/dpkg-maintscript-helper.1.gz
dpkg-dev: /usr/share/man/man1/dpkg-distaddfile.1.gz
dpkg: /usr/share/locale/gl/LC_MESSAGES/dpkg.mo
libdpkg-perl: /usr/share/doc/libdpkg-perl/copyright
dpkg-dev: /usr/share/doc/dpkg-dev/AUTHORS
dpkg: /usr/share/man/fr/man1/dpkg.1.gz
dpkg: /usr/bin/dpkg-deb
dpkg-dev: /usr/bin/dpkg-checkbuilddeps
apt: /usr/lib/dpkg/methods/apt/desc.apt
debconf-i18n: /usr/share/man/fr/man8/dpkg-preconfigure.8.gz
dpkg: /usr/bin/dpkg
dpkg-dev: /usr/share/man/sv/man1/dpkg-gensymbols.1.gz
libghc-dpkg-dev, libghc-dpkg-prof: /usr/lib/haskell-packages/ghc/lib/dpkg-0.0.1
dpkg-dev: /usr/bin/dpkg-distaddfile
libdpkg-perl: /usr/share/doc/libdpkg-perl/THANKS.gz
dpkg: /usr/share/man/man1/dpkg-split.1.gz
debconf-i18n: /usr/share/man/es/man8/dpkg-reconfigure.8.gz
dpkg-dev: /usr/share/man/es/man1/dpkg-buildpackage.1.gz
dpkg: /usr/share/locale/id/LC_MESSAGES/dpkg.mo
dpkg: /usr/share/locale/el/LC_MESSAGES/dpkg.mo
dpkg-dev: /usr/share/man/de/man1/dpkg-buildpackage.1.gz
dpkg-dev: /usr/share/man/sv/man1/dpkg-scansources.1.gz
dpkg: /usr/sbin/dpkg-divert
dpkg-dev: /usr/share/man/de/man1/dpkg-vendor.1.gz
dpkg-dev: /usr/share/man/sv/man1/dpkg-name.1.gz
dpkg-dev: /usr/share/man/de/man1/dpkg-source.1.gz
dpkg-dev: /usr/share/man/fr/man1/dpkg-scanpackages.1.gz
dpkg-dev: /usr/bin/dpkg-shlibdeps
update-manager-core: /usr/share/computerjanitor/plugins/dpkg_status_plugin.py
dpkg-dev: /usr/share/man/sv/man1/dpkg-mergechangelogs.1.gz
dpkg: /usr/share/man/sv/man1/dpkg-split.1.gz
dpkg-dev: /usr/bin/dpkg-gencontrol
libghc-dpkg-prof: /usr/share/doc/libghc-dpkg-prof
dpkg: /usr/share/man/pl/man8/dpkg-statoverride.8.gz
dpkg-dev: /usr/share/man/man1/dpkg-genchanges.1.gz

```

dpkg -l gedit
```
sean@Sean-Monster:~$ dpkg -l geditDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  gedit          3.4.1-0ubunt amd64        official text editor of the GNOME

```

dpkg -l xorg
```
sean@Sean-Monster:~$ dpkg -l xorgDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xorg           1:7.6+12ubun amd64        X.Org X Window System

```

dpkg -S gedit
...this one got caught off
```
gedit-common: /usr/share/help/th/gedit/gedit-shortcut-keys.pagegedit-common: /usr/share/help/ja/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/gedit/plugins/snippets/docbook.xml
gedit-common: /usr/share/help/gl/gedit/gedit-plugins-commander.page
gedit-common: /usr/share/help/ja/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/hu/gedit/figures/gedit-new-external-tool.png
gedit-common: /usr/share/help/ca/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/gl/gedit/gedit-plugins-pyconsole.page
gedit-common: /usr/share/help/th/gedit/gedit-undo-recent-action.page
gedit-common: /usr/share/help/fi/gedit/gedit-create-new-file.page
gedit: /usr/share/doc/gedit/BUGS
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-close-file.page
gedit-common: /usr/share/help/da/gedit/figures/gedit3-screenshot.png
gedit-common: /usr/share/help/pt_BR/gedit/gedit-open-on-server.page
gedit-common: /usr/share/help/ca/gedit/gedit-syntax-highlighting.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugins-session-saver.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/de/gedit/gedit-plugins-multi-edit.page
language-pack-gnome-en-base: /usr/share/locale-langpack/en_AU/LC_MESSAGES/gedit.mo
gedit-common: /usr/share/help/el/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/uk/gedit/gedit-change-default-font.page
language-pack-gnome-en-base: /usr/share/locale-langpack/en_CA/LC_MESSAGES/gedit.mo
gedit-common: /usr/share/help/te/gedit/gedit-tabs-moving.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-insert-date-time.page
gedit-common: /usr/share/help/ja/gedit/gedit-files-basic.page
gedit-common: /usr/share/help/oc/gedit/gedit-printing-order.page
gedit-common: /usr/share/help/te/gedit/gedit-plugins-code-assistance.page
gedit-common: /usr/share/help/el/gedit/gedit-save-file.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-insert-date-time.page
gedit: /usr/bin/gedit
gedit: /usr/share/gedit/gedit-bugreport
gedit-common: /usr/share/help/C/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-text-size.page
gedit-common: /usr/share/help/th/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/uk/gedit/gedit-printing.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-commander.page
gedit-common: /usr/share/help/hu/gedit/figures
gedit-common: /usr/share/help/sv/gedit/gedit-plugins-dashboard.page
gedit-common: /usr/share/help/ja/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/eu/gedit/gedit-syntax-highlighting.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-pyconsole.page
gedit-common: /usr/share/help/fr/gedit/gedit-quickstart.page
gedit-common: /usr/share/help/fi/gedit/gedit-plugins-character-map.page
gedit-common: /usr/share/help/fr/gedit/gedit-change-default-font.page
gedit-common: /usr/share/help/es/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/sv/gedit/figures/gedit-side-pane3.png
gedit-common: /usr/share/help/el/gedit/gedit-spellcheck.page
gedit: /usr/lib/gedit/plugins/snippets/appactivatable.py
gedit-common: /usr/share/help/ko/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/fi/gedit/gedit-plugins-word-completion.page
gedit-common: /usr/share/help/sl/gedit/gedit-view-open-files-in-sidepane.page
gedit-common: /usr/share/help/oc/gedit/gedit-plugins-bookmarks.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-create-new-file.page
gedit: /usr/lib/gedit/plugins/externaltools/__init__.py
gedit-common: /usr/share/help/es/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/fr/gedit/gedit-full-screen.page
gedit-common: /usr/share/help/sv/gedit/index.page
gedit-common: /usr/share/help/cs/gedit/figures/gedit-side-pane1.png
gedit-common: /usr/share/help/oc/gedit/figures
gedit-common: /usr/share/help/ar/gedit/gedit-tabs.page
gedit-common: /usr/share/help/fr/gedit/gedit-printing.page
gedit-common: /usr/share/help/ko/gedit/gedit-create-new-file.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-change-default-font.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/sv/gedit/gedit-plugins-word-completion.page
gedit-common: /usr/share/help/gl/gedit/figures/gedit3-screenshot.png
gedit-common: /usr/share/help/hu/gedit/gedit-printing-select.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-text-size.page
gedit-common: /usr/share/help/it/gedit/gedit-plugins-text-size.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-text-size.page
gedit-common: /usr/share/help/sv/gedit/gedit-plugins-modelines.page
gedit-common: /usr/share/help/gl/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/ca/gedit/gedit-plugins-dashboard.page
gedit-common: /usr/share/help/da/gedit/gedit-files-basic.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/de/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/bg/gedit/gedit-syntax-highlighting.page
gedit-common: /usr/share/help/it/gedit/gedit-printing-select.page
gedit-common: /usr/share/help/sl/gedit/gedit-replace.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugins-dashboard.page
gedit-common: /usr/share/help/ko/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/es/gedit/gedit-plugins-dashboard.page
gedit-common: /usr/share/help/ca/gedit/figures/gedit-side-pane3.png
gedit-common: /usr/share/help/C/gedit/gedit-plugins-code-assistance.page
gedit-common: /usr/share/help/sl/gedit/gedit-plugins-insert-date-time.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-shortcut-keys.page
gedit-common: /usr/share/help/C/gedit/gedit-plugins-session-saver.page
gedit-common: /usr/share/help/de/gedit/gedit-plugins-quick-open.page
gedit: /usr/lib/gedit/plugins/snippets/helper.py
gedit-common: /usr/share/help/it/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/hu/gedit/figures/gedit-side-pane3.png
gedit-common: /usr/share/help/ko/gedit/gedit-open-files.page
gedit-common: /usr/share/help/es/gedit/figures/gedit-side-pane3.png
gedit-common: /usr/share/help/fr/gedit/gedit-close-file.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-file-browser.page
gedit-common: /usr/share/help/th/gedit/gedit-plugins-character-map.page
gedit-common: /usr/share/help/es/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/sl/gedit/gedit-plugins-bookmarks.page
gedit-common: /usr/share/help/th/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/it/gedit/figures
gedit-common: /usr/share/help/C/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/sl/gedit/figures/gedit-icon.png
gedit: /usr/lib/gedit/plugins/snippets/windowactivatable.py
gedit-common: /usr/share/help/C/gedit/figures/gedit-new-external-tool.png
gedit-common: /usr/share/gedit/plugins/snippets/java.xml
gedit-common: /usr/share/help/fi/gedit/gedit-change-color-scheme.page
gedit-common: /usr/share/help/ca/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/ru/gedit/gedit-view-open-files-in-sidepane.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/fr/gedit/gedit-undo-recent-action.page
gedit-common: /usr/share/help/bg/gedit/gedit-spellcheck.page
gedit-common: /usr/share/help/uk/gedit/index.page
language-pack-gnome-en-base: /usr/share/locale-langpack/en_GB/LC_MESSAGES/gedit.mo
gedit-common: /usr/share/help/ar/gedit/gedit-syntax-highlighting.page
gedit-common: /usr/share/help/ca/gedit/gedit-plugins-modelines.page
gedit-common: /usr/share/help/ja/gedit/gedit-plugins-code-comment.page
gedit-common: /usr/share/help/fi/gedit/gedit-replace.page
gedit-common: /usr/share/gedit/plugins/snippets/python.xml
gedit-common: /usr/share/help/zh_CN/gedit/gedit-quickstart.page
gedit-common: /usr/share/help/oc/gedit/gedit-plugins-commander.page
gedit-common: /usr/share/help/da/gedit/gedit-plugins-character-map.page
gedit-common: /usr/share/help/ja/gedit/gedit-open-files.page
gedit-common: /usr/share/help/ko/gedit/gedit-printing.page
gedit-common: /usr/share/help/ar/gedit/gedit-plugins-snippets.page
gedit-common: /usr/share/help/ca/gedit/gedit-plugins-insert-date-time.page
gedit-common: /usr/share/help/da/gedit/gedit-search.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugins-modelines.page
gedit-common: /usr/share/help/es/gedit/gedit-plugins-modelines.page
gedit-common: /usr/share/help/oc/gedit/gedit-plugins-pyconsole.page
gedit-common: /usr/share/help/bg/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/ko/gedit/gedit-replace.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-files-basic.page
gedit-common: /usr/share/help/ja/gedit/gedit-change-default-font.page
light-themes: /usr/share/themes/Radiance/gtk-3.0/apps/gedit.css
gedit-common: /usr/share/help/ja/gedit/gedit-plugins-bracket-comp.page
gedit: /usr/lib/gedit/plugins/libfilebrowser.so
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/lv/gedit/gedit-edit-as-root.page
gedit-common: /usr/share/help/fi/gedit/gedit-search.page
gedit-common: /usr/share/help/fi/gedit/gedit-plugins-change-case.page
gedit-common: /usr/share/help/th/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/lv/gedit/gedit-change-color-scheme.page
gedit-common: /usr/share/help/oc/gedit/index.page
gedit-common: /usr/share/help/te/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/doc/gedit-common/copyright
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-bookmarks.page
gedit-common: /usr/share/help/gl/gedit/gedit-view-open-files-in-sidepane.page
gedit-common: /usr/share/help/ca/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-bookmarks.page
gedit: /usr/share/dbus-1/services/org.gnome.gedit.service
gedit-common: /usr/share/help/th/gedit/gedit-change-color-scheme.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-plugins-snippets.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/th/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/eu/gedit/gedit-open-recent.page
gedit-common: /usr/share/help/it/gedit/gedit-quickstart.page
gedit-common: /usr/share/help/ar/gedit/gedit-undo-recent-action.page
gedit-common: /usr/share/help/it/gedit/gedit-edit-as-root.page
gedit-common: /usr/share/help/es/gedit/gedit-change-default-font.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/sl/gedit/gedit-open-files.page
gedit-common: /usr/share/help/fi/gedit/gedit-plugins-join-split-lines.page
gedit-common: /usr/share/help/el/gedit/gedit-tabs.page
gedit-common: /usr/share/gedit/plugins/snippets/tcl.xml
gedit-common: /usr/share/help/zh_TW/gedit/gedit-quickstart.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/C/gedit/gedit-shortcut-keys.page
gedit-common: /usr/share/help/sl/gedit/gedit-plugins-commander.page
gedit-common: /usr/share/help/ru/gedit/gedit-full-screen.page
gedit-common: /usr/share/help/de/gedit/gedit-plugins-session-saver.page
gedit-common: /usr/share/help/sl/gedit/gedit-plugins-pyconsole.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-open-files.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-close-file.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-change-case.page
gedit-common: /usr/share/help/fr/gedit/gedit-edit-as-root.page
gedit-common: /usr/share/help/oc/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/da/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-file-browser.page
gedit-common: /usr/share/help/de/gedit/gedit-tabs-moving.page
gedit-common: /usr/share/help/es/gedit/gedit-plugins-code-comment.page
gedit-common: /usr/share/help/th/gedit/gedit-plugins-change-case.page
gedit-common: /usr/share/help/sl/gedit
gedit-common: /usr/share/help/it/gedit/gedit-tabs-moving.page
gedit-common: /usr/share/help/te/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/ca/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/es/gedit/gedit-plugins-bracket-comp.page
gedit: /usr/lib/gedit/plugins/snippets/document.py
gedit-common: /usr/share/help/fr/gedit/figures/gedit-new-external-tool.png
gedit-common: /usr/share/help/fr/gedit/gedit-tabs.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-save-file.page
gedit-common: /usr/share/gedit/plugins/snippets/mallard.xml
gedit-common: /usr/share/help/bg/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/ru/gedit/gedit-syntax-highlighting.page
gedit-common: /usr/share/help/hu/gedit/gedit-create-new-file.page
gedit-common: /usr/share/help/sl/gedit/gedit-tabs-moving.page
gedit-common: /usr/share/help/cs/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/eu/gedit/index.page
gedit-common: /usr/share/help/cs/gedit/gedit-spellcheck.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-code-comment.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/gl/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/it/gedit/gedit-close-file.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-plugins-doc-stats.page
gedit-common: /usr/share/help/it/gedit/gedit-plugins-join-split-lines.page
gedit-common: /usr/share/help/ca/gedit/gedit-plugins-session-saver.page
gedit: /usr/lib/gedit/plugins/quickopen
gedit-common: /usr/share/help/zh_HK/gedit/gedit-syntax-highlighting.page
gedit-common: /usr/share/help/it/gedit/gedit-create-new-file.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-close-file.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-commander.page
gedit-common: /usr/share/help/C/gedit/gedit-printing-order.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-commander.page
gedit-common: /usr/share/help/cs/gedit/figures
gedit-common: /usr/share/help/da/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/gl/gedit/gedit-printing.page
gedit-common: /usr/share/help/it/gedit/gedit-printing-order.page
gedit-common: /usr/share/help/th/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-bracket-comp.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/ca/gedit/gedit-printing-order.page
gedit-common: /usr/share/help/oc/gedit/gedit-printing-select.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-pyconsole.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-sort.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-pyconsole.page
gedit-common: /usr/share/help/ja/gedit/gedit-plugins-join-split-lines.page
gedit-common: /usr/share/help/ru/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/cs/gedit/gedit-undo-recent-action.page
gedit-common: /usr/share/help/ru/gedit/figures/gedit-side-pane1.png
gedit-common: /usr/share/help/eu/gedit/gedit-printing.page
gedit-common: /usr/share/help/gl/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/el/gedit/gedit-plugins-install.page
gedit-common: /usr/share/help/zh_TW/gedit/figures/gedit-new-external-tool.png
gedit-common: /usr/share/help/te/gedit/figures/gedit-side-pane2.png
gedit-common: /usr/share/help/zh_TW/gedit/gedit-undo-recent-action.page
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-plugins-bookmarks.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/el/gedit/gedit-plugins-character-map.page
gedit-common: /usr/share/help/uk/gedit/figures/gedit-new-external-tool.png
gedit-common: /usr/share/help/oc/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/it/gedit/gedit-save-file.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-sort.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugins-sort.page
gedit-common: /usr/share/help/ja/gedit/figures
gedit-common: /usr/share/help/ca/gedit/gedit-tabs-moving.page
gedit-common, gedit: /usr/share/gedit
gedit-common: /usr/share/help/es/gedit/gedit-view-open-files-in-sidepane.page
gedit-common: /usr/share/help/de/gedit/gedit-plugins-doc-stats.page
gedit-common: /usr/share/help/el/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/th/gedit/gedit-tabs-moving.page
gedit-common: /usr/share/help/te/gedit/gedit-plugins-file-browser.page
light-themes: /usr/share/themes/Ambiance/gtk-3.0/apps/gedit.css
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/es/gedit/gedit-open-on-server.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-dashboard.page
gedit-common: /usr/share/help/C/gedit/figures/gedit-side-pane1.png
gedit-common: /usr/share/help/de/gedit/gedit-printing.page
gedit-common: /usr/share/gedit/plugins/externaltools/ui/outputpanel.ui
gedit-common: /usr/share/help/uk/gedit/gedit-undo-recent-action.page
gedit-common: /usr/share/help/da/gedit
gedit-common: /usr/share/help/cs/gedit/gedit-tabs.page
gedit-common: /usr/share/help/es/gedit/gedit-plugins-sort.page
gedit-common: /usr/share/help/fr/gedit/gedit-open-files.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/ko/gedit/figures/gedit-side-pane3.png
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/lv/gedit/gedit-quickstart.page
gedit-common: /usr/share/help/ru/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/fi/gedit/gedit-plugins-code-assistance.page
gedit-common: /usr/share/help/hu/gedit/gedit-full-screen.page
gedit-common: /usr/share/help/sv/gedit/gedit-view-open-files-in-sidepane.page
gedit-common: /usr/share/help/te/gedit/gedit-plugins-install.page
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-join-split-lines.page
gedit-common: /usr/share/help/sv/gedit/gedit-replace.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-word-completion.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-snippets.page
gedit-common: /usr/share/help/sv/gedit/gedit-plugins-code-assistance.page
gedit-common: /usr/share/help/cs/gedit/gedit-plugins-file-browser.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-bookmarks.page
gedit: /usr/lib/gedit/plugins/libtime.so
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/eu/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/ar/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/hu/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/gl/gedit/gedit-printing-order.page
gedit-common: /usr/share/help/el/gedit/gedit-plugins-doc-stats.page
gedit-common: /usr/share/help/ca/gedit/figures
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-modelines.page
gedit-common: /usr/share/help/da/gedit/gedit-plugins-code-comment.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-sort.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-file-browser.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-dashboard.page
gedit-common: /usr/share/help/sl/gedit/figures/gedit-new-external-tool.png
gedit-common: /usr/share/help/it/gedit/gedit-plugins-dashboard.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-plugins-commander.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-dashboard.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-terminal.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-printing.page
gedit-common: /usr/share/help/uk/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/cs/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/ru/gedit/gedit-printing-order.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-plugins-pyconsole.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-plugins-word-completion.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-full-screen.page
gedit-common: /usr/share/help/da/gedit/gedit-plugins-bracket-comp.page
gedit-common: /usr/share/help/lv/gedit/figures/gedit-side-pane3.png
gedit-common: /usr/share/help/it/gedit/figures/gedit-side-pane3.png
gedit-common: /usr/share/help/fr/gedit/figures/gedit-side-pane3.png
gedit-common: /usr/share/help/fi/gedit/figures/gedit-side-pane1.png
gedit-common: /usr/share/help/uk/gedit/gedit-files-basic.page
gedit-common: /usr/share/help/fi/gedit/gedit-open-recent.page
gedit-common: /usr/share/help/de/gedit/gedit-plugins-word-completion.page
gedit-common: /usr/share/help/lv/gedit/gedit-close-file.page
gedit-common: /usr/share/help/cs/gedit/gedit-printing-order.page
gedit-common: /usr/share/help/ru/gedit/figures/gedit3-screenshot.png
gedit-common: /usr/share/help/gl/gedit/gedit-tabs-moving.page
gedit-common: /usr/share/help/ar/gedit/gedit-printing.page
gedit-common: /usr/share/help/es/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/fi/gedit/gedit-plugins-file-browser.page
gedit-common: /usr/share/help/ja/gedit/gedit-plugins-word-completion.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/ko/gedit/gedit-spellcheck.page
gedit-common: /usr/share/help/da/gedit/gedit-plugins-doc-stats.page
gedit-common: /usr/share/help/ja/gedit/index.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/ar/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/th/gedit/gedit-replace.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-open-files.page
gedit-common: /usr/share/help/ca/gedit/figures/gedit-new-external-tool.png
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/el/gedit/gedit-tabs-moving.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-modelines.page
gedit-common: /usr/share/help/it/gedit/gedit-plugins-modelines.page
gedit-common: /usr/share/help/C/gedit/gedit-change-color-scheme.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-modelines.page
gedit-common: /usr/share/help/ru/gedit/gedit-plugins-code-comment.page
gedit-common: /usr/share/help/th/gedit/figures/gedit-side-pane1.png
gedit-common: /usr/share/help/sl/gedit/gedit-plugins-snippets.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-commander.page
gedit-common: /usr/share/help/C/gedit/gedit-save-file.page
gedit-common: /usr/share/help/ja/gedit/gedit-undo-recent-action.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-full-screen.page
gedit-common: /usr/share/help/oc/gedit/gedit-create-new-file.page
gedit-common: /usr/share/help/sv/gedit/gedit-undo-recent-action.page
gedit-common: /usr/share/help/ja/gedit/gedit-spellcheck.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-pyconsole.page
gedit-common: /usr/share/glib-2.0/schemas/org.gnome.gedit.plugins.externaltools.gschema.xml
gedit-common: /usr/share/help/ru/gedit/gedit-plugins-bracket-comp.page
gedit-common: /usr/share/help/es/gedit/gedit-files-basic.page
gedit: /usr/lib/gedit/plugins/externaltools/outputpanel.py
gedit-common: /usr/share/help/cs/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-syntax-highlighting.page
gedit-common: /usr/share/help/ko/gedit/gedit-open-on-server.page
gedit-common: /usr/share/gedit/plugins/snippets/php.xml
gedit-common: /usr/share/help/te/gedit/gedit-plugins-text-size.page
gedit-common: /usr/share/help/ja/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/gedit/plugins/snippets/xml.xml
gedit-common: /usr/share/help/te/gedit/gedit-save-file.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/ar/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-code-comment.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/it/gedit/gedit-open-files.page
gedit-common: /usr/share/help/C/gedit/gedit-plugins-change-case.page
gedit: /usr/lib/gedit/plugins/spell.plugin
gedit-common: /usr/share/help/te/gedit/gedit-full-screen.page
gedit-common: /usr/share/help/cs/gedit/gedit-files-basic.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-sort.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-open-files.page
gedit-common: /usr/share/help/sv/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/ko/gedit/gedit-save-file.page
gedit-common: /usr/share/help/fi/gedit/gedit-view-open-files-in-sidepane.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-bracket-comp.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-code-comment.page
gedit-common: /usr/share/help/ar/gedit/gedit-quickstart.page
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-file-browser.page
gedit-common: /usr/share/help/th/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/ja/gedit/gedit-open-recent.page
gedit-common: /usr/share/help/it/gedit/gedit-plugins-terminal.page
gedit: /usr/lib/gedit/plugins/snippets/parser.py
gedit-common: /usr/share/help/ru/gedit/gedit-plugins-install.page
gedit-common: /usr/share/help/es/gedit/gedit-plugins-character-map.page
gedit-common: /usr/share/help/ar/gedit/gedit-replace.page
gedit-common: /usr/share/help/ru/gedit/gedit-plugins-insert-date-time.page
gedit-common: /usr/share/help/da/gedit/gedit-shortcut-keys.page
gedit-common: /usr/share/help/sl/gedit/gedit-spellcheck.page
gedit-common: /usr/share/help/es/gedit/gedit-plugins-draw-spaces.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/de/gedit/gedit-change-default-font.page
gedit-common: /usr/share/help/oc/gedit/gedit-view-open-files-in-sidepane.page
gedit-common: /usr/share/help/it/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-install.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-terminal.page
gedit-common: /usr/share/help/ja/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-bracket-comp.page
gedit-common: /usr/share/help/hu/gedit/figures/gedit3-screenshot.png
gedit-common: /usr/share/gedit/plugins/snippets/latex.xml
gedit-common: /usr/share/help/zh_HK/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/fi/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/te/gedit/gedit-plugins-sort.page
gedit-common: /usr/share/help/sl/gedit/figures/gedit3-screenshot.png
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-spellcheck.page
gedit-common: /usr/share/help/ar/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/eu/gedit/figures/gedit-side-pane1.png
gedit-common: /usr/share/help/ja/gedit/gedit-replace.page
gedit-common: /usr/share/help/zh_TW/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/C/gedit/index.page
gedit-common: /usr/share/help/gl/gedit/gedit-shortcut-keys.page
gedit-common: /usr/share/help/th/gedit/gedit-tabs.page
gedit-common: /usr/share/help/ja/gedit/gedit-plugins-doc-stats.page
gedit-common: /usr/share/help/te/gedit/gedit-search.page
gedit-common: /usr/share/help/es/gedit/gedit-replace.page
gedit-common: /usr/share/gedit/plugins/snippets/ui/snippets.ui
gedit-common: /usr/share/help/ko/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/ar/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-join-split-lines.page
gedit-common: /usr/share/help/da/gedit/gedit-change-color-scheme.page
gedit: /usr/lib/gedit/plugins/libspell.so
gedit-common: /usr/share/help/C/gedit/figures
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-character-map.page
gedit-common: /usr/share/help/ru/gedit/gedit-printing.page
gedit-common: /usr/share/help/es/gedit/gedit-printing-select.page
gedit-common: /usr/share/gedit/plugins/pythonconsole/ui
gedit-common: /usr/share/help/cs/gedit/figures/gedit-side-pane2.png
gedit-common: /usr/share/help/ja/gedit/gedit-tabs.page
gedit-common: /usr/share/help/ko/gedit/gedit-plugins-session-saver.page
gedit-common: /usr/share/help/C/gedit/gedit-plugins-terminal.page
gedit-common: /usr/share/help/de/gedit/gedit-plugins-install.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-tabs.page
gedit-common: /usr/share/help/el/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/ar/gedit/gedit-open-files-from-sidepane.page
gedit: /usr/lib/gedit/plugins/externaltools.plugin
gedit-common: /usr/share/help/cs/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/it/gedit/figures/gedit-open-location.png
gedit-common: /usr/share/help/ar/gedit/gedit-close-file.page
gedit-common: /usr/share/help/C/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/it/gedit/gedit-replace.page
gedit-common: /usr/share/help/es/gedit/gedit-printing.page
gedit-common: /usr/share/help/fr/gedit/gedit-printing-select.page
gedit-common: /usr/share/gedit/plugins/externaltools/tools/open-terminal-here
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-snippets-guide.page
gedit-common: /usr/share/help/gl/gedit/figures/gedit-side-pane1.png
gedit-common: /usr/share/help/de/gedit
gedit-common: /usr/share/help/da/gedit/gedit-open-recent.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/sv/gedit/gedit-files-basic.page
gedit-common: /usr/share/help/da/gedit/gedit-plugins-change-case.page
gedit-common: /usr/share/help/sv/gedit/gedit-plugins-file-browser.page
gedit-common: /usr/share/help/de/gedit/gedit-view-open-files-in-sidepane.page
gedit-common: /usr/share/help/th/gedit/gedit-plugins-install.page
gedit-common: /usr/share/help/bg/gedit/gedit-save-file.page
gedit-common: /usr/share/help/ru/gedit/gedit-plugins-terminal.page
gedit-common: /usr/share/help/oc/gedit/gedit-plugins-join-split-lines.page
gedit-common: /usr/share/help/pt_BR/gedit
gedit-common: /usr/share/help/zh_HK/gedit/gedit-plugins-file-browser.page
gedit-common: /usr/share/help/sv/gedit/gedit-plugins-external-tools.page
gedit-common: /usr/share/help/uk/gedit/gedit-plugins-quick-open.page
gedit-common: /usr/share/help/zh_CN/gedit/figures/gedit-icon.png
gedit-common: /usr/share/help/bg/gedit
gedit-common: /usr/share/help/ar/gedit/gedit-plugins-doc-stats.page
gedit-common: /usr/share/help/fr/gedit/gedit-plugins-terminal.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-install.page
gedit-common: /usr/share/help/el/gedit/gedit-plugins-color-picker.page
gedit-common: /usr/share/help/eu/gedit/gedit-plugins-insert-date-time.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-plugins-join-split-lines.page
gedit-common: /usr/share/help/te/gedit/gedit-open-files-from-sidepane.page
gedit-common: /usr/share/help/gl/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/uk/gedit/figures/gedit-side-pane1.png
gedit-common: /usr/share/help/sl/gedit/gedit-plugin-guide.page
gedit-common: /usr/share/help/it/gedit/gedit-plugins-session-saver.page
gedit-common: /usr/share/help/uk/gedit/gedit-printing-select.page
gedit-common: /usr/share/help/lv/gedit/gedit-open-files.page
gedit-common: /usr/share/help/de/gedit/gedit-plugins-tag-list.page
gedit-common: /usr/share/help/oc/gedit/gedit-files-basic.page
gedit-common: /usr/share/help/it/gedit/gedit-plugins-word-completion.page
gedit-common: /usr/share/help/pt_BR/gedit/gedit-plugins-join-split-lines.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-code-comment.page
gedit-common: /usr/share/GConf/gsettings/gedit.convert
gedit-common: /usr/share/help/ja/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/zh_CN/gedit/gedit-edit-as-root.page
gedit-common: /usr/share/help/sv/gedit/gedit-plugins-multi-edit.page
gedit-common: /usr/share/help/de/gedit/gedit-plugins-insert-date-time.page
gedit-common: /usr/share/help/sv/gedit/gedit-plugins-session-saver.page
gedit-common: /usr/share/help/fr/gedit/gedit-spellcheck.page
gedit-common: /usr/share/help/bg/gedit/gedit-plugins-code-assistance.page
gedit-common: /usr/share/help/lv/gedit/gedit-plugins-character-map.page
gedit-common: /usr/share/help/zh_TW/gedit/gedit-plugins-sort.page
gedit-common: /usr/share/help/zh_HK/gedit/gedit-open-recent.page

```

---

### Post by Bashing-om on 2014-01-20
j88n; By Golly !

That tells us we are in business.. all  looks fine to me.

OK, back to the original issue, from square one:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
to show what there is now to fix.

[INDENT][INDENT][INDENT]off once more and running strong
[/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-20
sudo apt-get upgrade
```
Fetched 27.9 MB in 58s (480 kB/s)                                              Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 271527 files and directories currently installed.)
Preparing to replace base-files 6.5ubuntu6.6 (using .../base-files_6.5ubuntu6.7_amd64.deb) ...
Unpacking replacement base-files ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
Setting up base-files (6.5ubuntu6.7) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
Setting up base-files (6.5ubuntu6.7) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 271527 files and directories currently installed.)
Preparing to replace libssl1.0.0:amd64 1.0.1-4ubuntu5.10 (using .../libssl1.0.0_1.0.1-4ubuntu5.11_amd64.deb) ...
Unpacking replacement libssl1.0.0:amd64 ...
Setting up libssl1.0.0:amd64 (1.0.1-4ubuntu5.11) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 271527 files and directories currently installed.)
Preparing to replace libdrm2:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm2_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm2:amd64 ...
Preparing to replace libdrm-intel1:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm-intel1_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm-intel1:amd64 ...
Preparing to replace libdrm-nouveau1a:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm-nouveau1a_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm-nouveau1a:amd64 ...
Preparing to replace libdrm-radeon1:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm-radeon1_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm-radeon1:amd64 ...
Preparing to replace language-pack-en 1:12.04+20130128 (using .../language-pack-en_1%3a12.04+20140106_all.deb) ...
Unpacking replacement language-pack-en ...
Preparing to replace language-pack-en-base 1:12.04+20130128 (using .../language-pack-en-base_1%3a12.04+20140106_all.deb) ...
Unpacking replacement language-pack-en-base ...
Preparing to replace language-pack-gnome-en 1:12.04+20130128 (using .../language-pack-gnome-en_1%3a12.04+20140106_all.deb) ...
Unpacking replacement language-pack-gnome-en ...
Preparing to replace language-pack-gnome-en-base 1:12.04+20130128 (using .../language-pack-gnome-en-base_1%3a12.04+20140106_all.deb) ...
Unpacking replacement language-pack-gnome-en-base ...
Preparing to replace libdrm-nouveau2:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm-nouveau2_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm-nouveau2:amd64 ...
Preparing to replace libgtk-3-bin 3.4.2-0ubuntu0.5 (using .../libgtk-3-bin_3.4.2-0ubuntu0.6_amd64.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace libgail-3-0:amd64 3.4.2-0ubuntu0.5 (using .../libgail-3-0_3.4.2-0ubuntu0.6_amd64.deb) ...
Unpacking replacement libgail-3-0:amd64 ...
Preparing to replace libgtk-3-0:amd64 3.4.2-0ubuntu0.5 (using .../libgtk-3-0_3.4.2-0ubuntu0.6_amd64.deb) ...
Unpacking replacement libgtk-3-0:amd64 ...
Preparing to replace libgtk-3-common 3.4.2-0ubuntu0.5 (using .../libgtk-3-common_3.4.2-0ubuntu0.6_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace libxfixes-dev 1:5.0-4ubuntu4.1 (using .../libxfixes-dev_1%3a5.0-4ubuntu4.2_amd64.deb) ...
Unpacking replacement libxfixes-dev ...
Preparing to replace libxfixes3:amd64 1:5.0-4ubuntu4.1 (using .../libxfixes3_1%3a5.0-4ubuntu4.2_amd64.deb) ...
Unpacking replacement libxfixes3:amd64 ...
Preparing to replace x11proto-input-dev 2.1.99.6-1 (using .../x11proto-input-dev_2.3-1~precise1_all.deb) ...
Unpacking replacement x11proto-input-dev ...
Preparing to replace libxi-dev 2:1.6.0-0ubuntu2.1 (using .../libxi-dev_2%3a1.7.1.901-1ubuntu1~precise1_amd64.deb) ...
Unpacking replacement libxi-dev ...
Preparing to replace libxi6:amd64 2:1.6.0-0ubuntu2.1 (using .../libxi6_2%3a1.7.1.901-1ubuntu1~precise1_amd64.deb) ...
Unpacking replacement libxi6:amd64 ...
Preparing to replace libpixman-1-dev 0.24.4-1ubuntu0.1 (using .../libpixman-1-dev_0.30.2-1ubuntu0.0.0.0.1_amd64.deb) ...
Unpacking replacement libpixman-1-dev ...
Preparing to replace libpixman-1-0:amd64 0.24.4-1ubuntu0.1 (using .../libpixman-1-0_0.30.2-1ubuntu0.0.0.0.1_amd64.deb) ...
Unpacking replacement libpixman-1-0:amd64 ...
Preparing to replace libqt4-sql-sqlite:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-sql-sqlite_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-sql-sqlite:amd64 ...
Preparing to replace libqt4-help:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-help_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-help:amd64 ...
Preparing to replace libqt4-svg:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-svg_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-svg:amd64 ...
Preparing to replace libqt4-scripttools:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-scripttools_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-scripttools:amd64 ...
Preparing to replace libqt4-opengl:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-opengl_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-opengl:amd64 ...
Preparing to replace libqt4-designer:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-designer_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-designer:amd64 ...
Preparing to replace libqtgui4:amd64 4:4.8.1-0ubuntu4.5 (using .../libqtgui4_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqtgui4:amd64 ...
Preparing to replace libqt4-declarative:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-declarative_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-declarative:amd64 ...
Preparing to replace libqt4-sql:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-sql_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-sql:amd64 ...
Preparing to replace libqt4-xmlpatterns:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-xmlpatterns:amd64 ...
Preparing to replace libqt4-network:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-network_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-network:amd64 ...
Preparing to replace libqt4-script:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-script_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-script:amd64 ...
Preparing to replace libqt4-test:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-test_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-test:amd64 ...
Preparing to replace qdbus 4:4.8.1-0ubuntu4.5 (using .../qdbus_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement qdbus ...
Preparing to replace libqt4-dbus:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-dbus_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-dbus:amd64 ...
Preparing to replace libqt4-xml:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-xml_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-xml:amd64 ...
Preparing to replace libqtcore4:amd64 4:4.8.1-0ubuntu4.5 (using .../libqtcore4_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqtcore4:amd64 ...
Preparing to replace libglu1-mesa:amd64 8.0.4-0ubuntu0.6 (using .../libglu1-mesa_8.0.4-0ubuntu0.7_amd64.deb) ...
Unpacking replacement libglu1-mesa:amd64 ...
Preparing to replace iproute 20111117-1ubuntu2 (using .../iproute_20111117-1ubuntu2.1_amd64.deb) ...
Unpacking replacement iproute ...
Preparing to replace bind9-host 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../bind9-host_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement bind9-host ...
Preparing to replace dnsutils 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../dnsutils_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement dnsutils ...
Preparing to replace libisc83 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libisc83_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libisc83 ...
Preparing to replace libdns81 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libdns81_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libdns81 ...
Preparing to replace libisccc80 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libisccc80_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libisccc80 ...
Preparing to replace libisccfg82 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libisccfg82_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libisccfg82 ...
Preparing to replace liblwres80 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../liblwres80_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement liblwres80 ...
Preparing to replace libbind9-80 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libbind9-80_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libbind9-80 ...
Preparing to replace openssl 1.0.1-4ubuntu5.10 (using .../openssl_1.0.1-4ubuntu5.11_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace bc 1.06.95-2 (using .../bc_1.06.95-2ubuntu1_amd64.deb) ...
Unpacking replacement bc ...
Preparing to replace libck-connector0 0.4.5-2 (using .../libck-connector0_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libck-connector0 ...
Preparing to replace consolekit 0.4.5-2 (using .../consolekit_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement consolekit ...
Preparing to replace dc 1.06.95-2 (using .../dc_1.06.95-2ubuntu1_amd64.deb) ...
Unpacking replacement dc ...
Preparing to replace duplicity 0.6.18-0ubuntu3.3 (using .../duplicity_0.6.18-0ubuntu3.4_amd64.deb) ...
Unpacking replacement duplicity ...
Preparing to replace flashplugin-installer 11.2.202.332ubuntu0.12.04.1 (using .../flashplugin-installer_11.2.202.335ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement flashplugin-installer ...
Preparing to replace gir1.2-gtk-3.0 3.4.2-0ubuntu0.5 (using .../gir1.2-gtk-3.0_3.4.2-0ubuntu0.6_amd64.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace libappindicator3-1 0.4.92-0ubuntu1 (using .../libappindicator3-1_0.4.92-0ubuntu1.1_amd64.deb) ...
Unpacking replacement libappindicator3-1 ...
Preparing to replace gir1.2-appindicator3-0.1 0.4.92-0ubuntu1 (using .../gir1.2-appindicator3-0.1_0.4.92-0ubuntu1.1_amd64.deb) ...
Unpacking replacement gir1.2-appindicator3-0.1 ...
Preparing to replace python-appindicator 0.4.92-0ubuntu1 (using .../python-appindicator_0.4.92-0ubuntu1.1_amd64.deb) ...
Unpacking replacement python-appindicator ...
Preparing to replace libappindicator1 0.4.92-0ubuntu1 (using .../libappindicator1_0.4.92-0ubuntu1.1_amd64.deb) ...
Unpacking replacement libappindicator1 ...
Preparing to replace libcdt4 2.26.3-10ubuntu1 (using .../libcdt4_2.26.3-10ubuntu1.1_amd64.deb) ...
Unpacking replacement libcdt4 ...
Preparing to replace libgraph4 2.26.3-10ubuntu1 (using .../libgraph4_2.26.3-10ubuntu1.1_amd64.deb) ...
Unpacking replacement libgraph4 ...
Preparing to replace libpathplan4 2.26.3-10ubuntu1 (using .../libpathplan4_2.26.3-10ubuntu1.1_amd64.deb) ...
Unpacking replacement libpathplan4 ...
Preparing to replace libgvc5 2.26.3-10ubuntu1 (using .../libgvc5_2.26.3-10ubuntu1.1_amd64.deb) ...
Unpacking replacement libgvc5 ...
Preparing to replace libpam-ck-connector 0.4.5-2 (using .../libpam-ck-connector_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libpam-ck-connector ...
Preparing to replace unity 5.20.0-0ubuntu2 (using .../unity_5.20.0-0ubuntu3_amd64.deb) ...
Unpacking replacement unity ...
Preparing to replace unity-common 5.20.0-0ubuntu2 (using .../unity-common_5.20.0-0ubuntu3_all.deb) ...
Unpacking replacement unity-common ...
Preparing to replace libunity-core-5.0-5 5.20.0-0ubuntu2 (using .../libunity-core-5.0-5_5.20.0-0ubuntu3_amd64.deb) ...
Unpacking replacement libunity-core-5.0-5 ...
Preparing to replace unity-services 5.20.0-0ubuntu2 (using .../unity-services_5.20.0-0ubuntu3_amd64.deb) ...
Unpacking replacement unity-services ...
Preparing to replace unity-2d-panel 5.14.0-0ubuntu1 (using .../unity-2d-panel_5.14.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity-2d-panel ...
Preparing to replace unity-2d-shell 5.14.0-0ubuntu1 (using .../unity-2d-shell_5.14.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity-2d-shell ...
Preparing to replace unity-2d-spread 5.14.0-0ubuntu1 (using .../unity-2d-spread_5.14.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity-2d-spread ...
Preparing to replace unity-2d-common 5.14.0-0ubuntu1 (using .../unity-2d-common_5.14.0-0ubuntu2_all.deb) ...
Unpacking replacement unity-2d-common ...
Preparing to replace libunity-2d-private0 5.14.0-0ubuntu1 (using .../libunity-2d-private0_5.14.0-0ubuntu2_amd64.deb) ...
Unpacking replacement libunity-2d-private0 ...
Preparing to replace libxfont1 1:1.4.4-1 (using .../libxfont1_1%3a1.4.4-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libxfont1 ...
Preparing to replace python-software-properties 0.82.7.6 (using .../python-software-properties_0.82.7.7_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace software-properties-common 0.82.7.6 (using .../software-properties-common_0.82.7.7_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.6 (using .../software-properties-gtk_0.82.7.7_all.deb) ...
Unpacking replacement software-properties-gtk ...
Preparing to replace unity-2d 5.14.0-0ubuntu1 (using .../unity-2d_5.14.0-0ubuntu2_all.deb) ...
Unpacking replacement unity-2d ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.335.orig.tar.gz
Installing from local file /tmp/tmp5ynCJ6.gz
Flash Plugin installed.
Processing triggers for gconf2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Setting up libdrm2:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libdrm-intel1:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libdrm-nouveau1a:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libdrm-radeon1:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libdrm-nouveau2:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libgtk-3-common (3.4.2-0ubuntu0.6) ...
Setting up libxfixes3:amd64 (1:5.0-4ubuntu4.2) ...
Setting up libxi6:amd64 (2:1.7.1.901-1ubuntu1~precise1) ...
Setting up libgtk-3-0:amd64 (3.4.2-0ubuntu0.6) ...
Setting up libgtk-3-bin (3.4.2-0ubuntu0.6) ...
Setting up libgail-3-0:amd64 (3.4.2-0ubuntu0.6) ...
Setting up libxfixes-dev (1:5.0-4ubuntu4.2) ...
Setting up x11proto-input-dev (2.3-1~precise1) ...
Setting up libxi-dev (2:1.7.1.901-1ubuntu1~precise1) ...
Setting up libpixman-1-0:amd64 (0.30.2-1ubuntu0.0.0.0.1) ...
Setting up libpixman-1-dev (0.30.2-1ubuntu0.0.0.0.1) ...
Setting up libqtcore4:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-sql:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-sql-sqlite:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-xml:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-dbus:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-network:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-script:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-xmlpatterns:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-test:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up qdbus (4:4.8.1-0ubuntu4.6) ...
Setting up libglu1-mesa:amd64 (8.0.4-0ubuntu0.7) ...
Setting up iproute (20111117-1ubuntu2.1) ...
Setting up libisc83 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up libisccc80 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up liblwres80 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up bind9-host (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up dnsutils (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up openssl (1.0.1-4ubuntu5.11) ...
Setting up bc (1.06.95-2ubuntu1) ...
Setting up libck-connector0 (0.4.5-2ubuntu0.1) ...
Setting up consolekit (0.4.5-2ubuntu0.1) ...
Setting up dc (1.06.95-2ubuntu1) ...
Setting up duplicity (0.6.18-0ubuntu3.4) ...
Setting up flashplugin-installer (11.2.202.335ubuntu0.12.04.1) ...
Setting up gir1.2-gtk-3.0 (3.4.2-0ubuntu0.6) ...
Setting up libappindicator3-1 (0.4.92-0ubuntu1.1) ...
Setting up gir1.2-appindicator3-0.1 (0.4.92-0ubuntu1.1) ...
Setting up libappindicator1 (0.4.92-0ubuntu1.1) ...
Setting up python-appindicator (0.4.92-0ubuntu1.1) ...
Setting up libcdt4 (2.26.3-10ubuntu1.1) ...
Setting up libgraph4 (2.26.3-10ubuntu1.1) ...
Setting up libpathplan4 (2.26.3-10ubuntu1.1) ...
Setting up libgvc5 (2.26.3-10ubuntu1.1) ...
Setting up libpam-ck-connector (0.4.5-2ubuntu0.1) ...
Setting up unity-services (5.20.0-0ubuntu3) ...
Setting up libunity-core-5.0-5 (5.20.0-0ubuntu3) ...
Setting up unity-common (5.20.0-0ubuntu3) ...
Setting up unity (5.20.0-0ubuntu3) ...
Setting up unity-2d-common (5.14.0-0ubuntu2) ...
Setting up libxfont1 (1:1.4.4-1ubuntu0.1) ...
Setting up python-software-properties (0.82.7.7) ...
Setting up software-properties-common (0.82.7.7) ...
Setting up software-properties-gtk (0.82.7.7) ...
Setting up language-pack-en (1:12.04+20140106) ...
Setting up language-pack-en-base (1:12.04+20140106) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
Setting up language-pack-gnome-en (1:12.04+20140106) ...
Setting up language-pack-gnome-en-base (1:12.04+20140106) ...
Setting up libqtgui4:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-declarative:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-help:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-svg:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-scripttools:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-opengl:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-designer:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libunity-2d-private0 (5.14.0-0ubuntu2) ...
Setting up unity-2d-panel (5.14.0-0ubuntu2) ...
Setting up unity-2d-shell (5.14.0-0ubuntu2) ...
Setting up unity-2d-spread (5.14.0-0ubuntu2) ...
Setting up unity-2d (5.14.0-0ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...

```

sudo apt-get dist-upgrade
```
sean@Sean-Monster:~$ sudo apt-get dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2014-01-20
j88n; Out standing !

Package manager is all happy !
So, play with the system and insure all application are functioning.

[INDENT][INDENT][INDENT]Glory be
[/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-20
Cool! Looks like dpkg works well now.. but I still can't open "gnome-control-center"

...is there a way to re-install that since dpkg is working now?

---

### Post by Bashing-om on 2014-01-20
j88n; Good.

Is  "gnome-control-center" the only malfuction at this time ?

Let's see if we can find the problem with control-center" (yeah we can re-install it ):
What errors are reported when starting from terminal ?
```

gnome-control-center

```
[INDENT][INDENT]can not be much to this
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-20
I get that wretched "core dump: bus error"

---

### Post by Bashing-om on 2014-01-20
j88n; EEEkkk

OK, let's poke about.
What returns:
```

gksudo gedit /etc/apt/sources.list

``` this is just a test of the operating system, as this is a system file and you have elevated privileges, no messing around. Open the file and close it at once.

Think'n if it is "safe" to (un)install gnome-control-center.

[INDENT][INDENT]snakes snakes, every where are snakes 
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-20
```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.utexas.edu/ubuntu/ precise main restricted
deb-src http://ftp.utexas.edu/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.utexas.edu/ubuntu/ precise-updates main restricted
deb-src http://ftp.utexas.edu/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.utexas.edu/ubuntu/ precise universe
deb-src http://ftp.utexas.edu/ubuntu/ precise universe
deb http://ftp.utexas.edu/ubuntu/ precise-updates universe
deb-src http://ftp.utexas.edu/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.utexas.edu/ubuntu/ precise multiverse
deb-src http://ftp.utexas.edu/ubuntu/ precise multiverse
deb http://ftp.utexas.edu/ubuntu/ precise-updates multiverse
deb-src http://ftp.utexas.edu/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://ftp.utexas.edu/ubuntu/ precise-security main restricted
deb-src http://ftp.utexas.edu/ubuntu/ precise-security main restricted
deb http://ftp.utexas.edu/ubuntu/ precise-security universe
deb-src http://ftp.utexas.edu/ubuntu/ precise-security universe
deb http://ftp.utexas.edu/ubuntu/ precise-security multiverse
deb-src http://ftp.utexas.edu/ubuntu/ precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by Bashing-om on 2014-01-20
j88n; OK

Let's prod at it a tad bit, to see what might happen when we remove the control center:
```

apt-get remove -s gnome-control-center

``` and make note of what is going to be removed. the '-s' option is "simulate" tell us what it will do but don't do it.

[INDENT][INDENT]treading on thin ice, step soft
[/INDENT][/INDENT]

---

### Post by mc4man on 2014-01-21
Looks like you made some great progress..
Maybe check & see if you have saucy's gnome-control center

apt-cache policy gnome-control-center

As you move forward try to be careful about mixing saucy packages in, - while it hasn't hurt yet & certainly best to leave well enough alone you used saucy's dpkg to replace the dpkg binaries.

For future use & to make life easier consider installing synaptic package manager.
Also, if full scroll back in a terminal is desired adjust in gnome terminal's edit menu > profile preferences > Scrolling (I use unlimited here

---

### Post by j88n on 2014-01-21
sean@Sean-Monster:~$ apt-get remove -s gnome-control-cent
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-control-center indicator-datetime indicator-power
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Remv indicator-power [2.0-0ubuntu1]
Remv indicator-datetime [0.3.94-0ubuntu2]
Remv gnome-control-center [1:3.4.2-0ubuntu0.13.1]

---

### Post by Bashing-om on 2014-01-21
@ mc4man Hi ! Thanks ! great to have you at our back.

@ j88n; Dont look like it will remove as much as I feared .

ok let's follow mc4man's advise and look:
```

apt-cache policy gnome-control-center

```

[INDENT][INDENT]measure twice, cut once
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
@mc4man thanks! I didn't know how to set the terminal window size, cool!

@bashing-om
my output:
gnome-control-center:
  Installed: 1:3.4.2-0ubuntu0.13.1
  Candidate: 1:3.4.2-0ubuntu0.13.1
  Version table:
 *** 1:3.4.2-0ubuntu0.13.1 0
        500 [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.4.1-0ubuntu1 0
        500 [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) precise/main amd64 Packages

---

### Post by Bashing-om on 2014-01-21
j88n; OK, looking good,

Let's do this for real.
```

sudo apt-get remove gnome-control-center

```
IF there are errors and horrible things reported - stop and tell us what is:
else let's put it back !
```

sudo apt-get install gnome-control-center

```

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
```
sean@Sean-Monster:~$ sudo apt-get remove gnome-control-center
[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-control-center indicator-datetime indicator-power
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 3,737 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 270841 files and directories currently installed.)
Removing indicator-power ...
Removing indicator-datetime ...
Removing gnome-control-center ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...

```

looked okay... so I continued..
```

sean@Sean-Monster:~$ sudo apt-get install gnome-control-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtimezonemap1 geoclue-ubuntu-geoip libedataserverui-3.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  indicator-power
The following NEW packages will be installed:
  gnome-control-center indicator-power
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 676 kB of archives.
After this operation, 3,409 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.utexas.edu/ubuntu/ precise-updates/main gnome-control-center amd64 1:3.4.2-0ubuntu0.13.1 [662 kB]
Get:2 http://ftp.utexas.edu/ubuntu/ precise/main indicator-power amd64 2.0-0ubuntu1 [13.8 kB]
Fetched 676 kB in 1s (486 kB/s)         
Selecting previously unselected package gnome-control-center.
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 270774 files and directories currently installed.)
Unpacking gnome-control-center (from .../gnome-control-center_1%3a3.4.2-0ubuntu0.13.1_amd64.deb) ...
Selecting previously unselected package indicator-power.
Unpacking indicator-power (from .../indicator-power_2.0-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libglib2.0-0:amd64 ...
Setting up gnome-control-center (1:3.4.2-0ubuntu0.13.1) ...
Setting up indicator-power (2.0-0ubuntu1) ...

```

but if i try to open gnome-control-center, I still get the bus error... =/

---

### Post by j88n on 2014-01-21
I think I'm calling it for tonight, let me know if you think of anything I should try tomorrow.. thanks again for the help!

---

### Post by Bashing-om on 2014-01-21
j88n; umhmp,

Well. it is late. my brain is turning into mush and synapses are miss firing.

Let's take a look at the log file and see what it has logged for this episode. Maybe get a hint where ubuntu's synapses are misfiring:
- I do not recall how to activate 12.04's log file viewer, you can play with dash and find it - OR
look at it in the file manager OR just from the terminal:
```

cat /var/log/syslog
cat /var/log/kern.log

```
dmesg might have a lot to say:
```

dmesg

```

And I will pick this back up in my AM .

[INDENT][INDENT]when all esle fails 
[INDENT][INDENT][INDENT]read the directions ?[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
What should I be looking for exactly? It seems to be way too much to copy and paste in the forum..

---

### Post by Bashing-om on 2014-01-21
j88n; Well
In respect to looking at the logs, we can narrow things down a bunch:
```

cat /var/log/syslog | grep EE
cat /var/log/syslog | grep WW

```
for instance 
And look closer at the logs in the times the errors are indicated- before and after those time stamps.
Someone who is real smart would do an "strace" on the command and be able to tell where it is failing from "strace's" log.
Unfortunantely, that is not me .

So all I know to do is poke and prod and see what gives.
Once more it is make sure the packages on the system all say they are stable:
```

sudo dpkg -C

```
See what might be interacting with gnome-control-center :
```

apt-cache depends gnome-control-center
apt-cache rdepends gnome-control-center

``` check these dependencies and verify they too are the correct versions.

[INDENT][INDENT]maybe some day I will learn how to read
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
With respect to the logs, does EE and WW stand for something? Because typing as-is, nothing returns..

sudo dpkg -C
```
sean@Sean-Monster:~$ sudo dpkg -C[sudo] password for sean: 
The following packages are missing the list control file in the
database, they need to be reinstalled:
 humanity-icon-theme  Humanity Icon theme


The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 humanity-icon-theme  Humanity Icon theme
 g++                  GNU C++ compiler
 libaudio2:amd64      Network Audio System - shared libraries
 binutils             GNU assembler, linker and binary utilities


The following packages have an unknown foreign architecture, which will
cause dependency issues on front-ends. This can be fixed by registering
the foreign architecture with dpkg --add-architecture:
 libavahi-common-data:i386 Avahi common data files
 gcc-4.6-base:i386    GCC, the GNU Compiler Collection (base package)

```

apt-cache depends gnome-control-center
```
sean@Sean-Monster:~$ apt-cache depends gnome-control-center
gnome-control-center
  Depends: gconf-service
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libcanberra-gtk3-0
  Depends: libcanberra0
  Depends: libcolord1
  Depends: libcups2
  Depends: libdbus-glib-1-2
  Depends: libfontconfig1
  Depends: libgconf-2-4
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgnome-control-center1
  Depends: libgnome-desktop-3-2
  Depends: libgnome-menu-3-0
  Depends: libgnomekbd7
  Depends: libgoa-1.0-0
  Depends: libgtk-3-0
  Depends: libgtop2-7
  Depends: libnm-glib4
  Depends: libnm-gtk0
  Depends: libnm-util2
  Depends: libnotify4
  Depends: libpango1.0-0
  Depends: libpolkit-gobject-1-0
  Depends: libpulse-mainloop-glib0
  Depends: libpulse0
  Depends: libupower-glib1
  Depends: libwacom2
  Depends: libx11-6
  Depends: libxi6
  Depends: libxklavier16
  Depends: libxml2
  Depends: accountsservice
  Depends: apg
  Depends: desktop-file-utils
  Depends: gnome-control-center-data
  Depends: gnome-control-center-data
  Depends: gnome-desktop3-data
  Depends: gnome-icon-theme
  Depends: gnome-icon-theme-symbolic
  Depends: gnome-menus
  Depends: gnome-settings-daemon
  Depends: gsettings-desktop-schemas
  Depends: ubuntu-system-service
 |Suggests: gnome-screensaver
  Suggests: xscreensaver
  Suggests: gstreamer0.10-pulseaudio
  Suggests: libcanberra-gtk-module
  Suggests: x11-xserver-utils
  Recommends: gnome-online-accounts
  Recommends: gnome-session-bin
  Recommends: iso-codes
  Recommends: mousetweaks
  Recommends: policykit-1-gnome
  Recommends: ubuntu-docs
  Recommends: indicator-sound
  Recommends: indicator-power
  Breaks: gnome-power-manager
  Breaks: gnome-session
  Breaks: libglib2.0-0

```

apt-cache rdepends gnome-control-center
```
sean@Sean-Monster:~$ apt-cache rdepends gnome-control-center
gnome-control-center
Reverse Depends:
  rhythmbox
  accountsservice
  sawfish
  gnome-panel
  gnome-panel
  ubuntu-desktop
  ubiquity-frontend-gtk
  totem
  rhythmbox
  libglib2.0-0
  gnome-settings-daemon
  gnome-online-accounts
  gnome-media
  gnome-media
  gnome-control-center-data
  accountsservice
  ubuntu-sugar-remix
  sawfish
  ontv
  mutter
  krb5-auth-dialog
  indicator-datetime-gtk2
  icewm-gnome-support
  gpe-conf
  gnome-system-tools
  gnome-shell
  gnome-shell
  gnome-panel
  gnome-panel
  gnome-gmail
  gnome-core
  xscreensaver
  ubuntu-desktop
  ubiquity-frontend-gtk
  totem
  rhythmbox
  mousetweaks
  metacity
  libglib2.0-0
  indicator-power
  indicator-datetime
  gnome-settings-daemon
  gnome-online-accounts
  gnome-menus
  gnome-media
  gnome-media
  gnome-font-viewer
  gnome-font-viewer
  gnome-control-center-data
  gnome-bluetooth
  accountsservice

```

---

### Post by Bashing-om on 2014-01-21
j88n; Well, well;

EE and WW -> error and warning conditions, none output with the command sequence, then none are reported.
At that time, try the commands on the logfiles syslog, kern.log, and dmesg --as SOON after trying to start "gnome-control-center".
Then see if any errors or warning are reported.

Do not know where the dpkg issues could have cropped up from, but;
Let's go ahead and fix them per dpkg's advise;
```

sudo apt-get install humanity-icon-theme
sudo apt-get install g++
sudo apt-get install libaudio2:amd64
sudo apt-get install binutils
sudo dpkg --add-architecture i386

```
Though I fail to see how any of this relates to our current situation.
Then see if "gnome-control-center" will run from terminal. (we might be pleasantly surprised)

In the meantime I will see what relationships I can find in the list of dependencies.

looking at the effect
[INDENT][INDENT]maybe find a cause
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
...doesn't look like it actually did anything



sudo apt-get install humanity-icon-theme
```
sean@Sean-Monster:~$ sudo apt-get install humanity-icon-theme
[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
humanity-icon-theme is already the newest version.
humanity-icon-theme set to manually installed.
The following packages were automatically installed and are no longer required:
  libtimezonemap1 geoclue-ubuntu-geoip libedataserverui-3.0-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


sudo apt-get install g++
```

sean@Sean-Monster:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
g++ set to manually installed.
The following packages were automatically installed and are no longer required:
  libtimezonemap1 geoclue-ubuntu-geoip libedataserverui-3.0-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


sudo apt-get install libaudio2:amd64
```

sean@Sean-Monster:~$ sudo apt-get install libaudio2:amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libaudio2 is already the newest version.
libaudio2 set to manually installed.
The following packages were automatically installed and are no longer required:
  libtimezonemap1 geoclue-ubuntu-geoip libedataserverui-3.0-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


sudo apt-get install binutils
```

sean@Sean-Monster:~$ sudo apt-get install binutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
binutils is already the newest version.
binutils set to manually installed.
The following packages were automatically installed and are no longer required:
  libtimezonemap1 geoclue-ubuntu-geoip libedataserverui-3.0-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

....doing the logs now!

---

### Post by j88n on 2014-01-21
After running the commands above, I tried to open gnome-control-center again, I got an error, so I tried the logs again, but nothing! ...see below:

```
sean@Sean-Monster:~$ gnome-control-centerBus error (core dumped)
sean@Sean-Monster:~$ cat /var/log/syslog | grep EE
sean@Sean-Monster:~$ cat /var/log/syslog | grep WW
sean@Sean-Monster:~$ cat /var/log/kern.log | grep WW
sean@Sean-Monster:~$ cat /var/log/kern.log | grep EE
sean@Sean-Monster:~$ dmesg | grep EE
sean@Sean-Monster:~$ dmesg | grep WW
sean@Sean-Monster:~$ 

```

---

### Post by j88n on 2014-01-21
I'm going to run apt-get autoremove...

-------

sean@Sean-Monster:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  geoclue-ubuntu-geoip libedataserverui-3.0-1 libtimezonemap1
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 1,441 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 270828 files and directories currently installed.)
Removing geoclue-ubuntu-geoip ...
Removing libedataserverui-3.0-1 ...
Removing libtimezonemap1 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by Bashing-om on 2014-01-21
j88n; Hey,

An accepted directive (command) to the system, when it is accepted, there will be no output. The system just does what it is told.
We can run the dpkg command again now and see if the result was positive and as expected:
```

sudo dpkg -C

```

not finished my work on relationships either to this time.

[INDENT][INDENT]keep plugging away, something has got to give
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
hmmm

sean@Sean-Monster:~$ sudo dpkg -C
The following packages are missing the list control file in the
database, they need to be reinstalled:
 humanity-icon-theme  Humanity Icon theme


The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 humanity-icon-theme  Humanity Icon theme
 g++                  GNU C++ compiler
 libaudio2:amd64      Network Audio System - shared libraries
 binutils             GNU assembler, linker and binary utilities

---

### Post by Bashing-om on 2014-01-21
j88n; humph,
Poke:
```

sudo apt-get purge humanity-icon-theme
sudo apt-get install humanity-icon-theme

```

and let's see what results before we do else.

[INDENT][INDENT]one of those time I wonder
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
sudo apt-get purge humanity-icon-theme
```

sean@Sean-Monster:~$ sudo apt-get install humanity-icon-theme
Fetched 27.9 MB in 58s (480 kB/s)                                              
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 271527 files and directories currently installed.)
Preparing to replace base-files 6.5ubuntu6.6 (using .../base-files_6.5ubuntu6.7_amd64.deb) ...
Unpacking replacement base-files ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
Setting up base-files (6.5ubuntu6.7) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
Setting up base-files (6.5ubuntu6.7) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 271527 files and directories currently installed.)
Preparing to replace libssl1.0.0:amd64 1.0.1-4ubuntu5.10 (using .../libssl1.0.0_1.0.1-4ubuntu5.11_amd64.deb) ...
Unpacking replacement libssl1.0.0:amd64 ...
Setting up libssl1.0.0:amd64 (1.0.1-4ubuntu5.11) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dpkg: warning: files list file for package 'humanity-icon-theme' missing; assuming package has no files currently installed
(Reading database ... 271527 files and directories currently installed.)
Preparing to replace libdrm2:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm2_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm2:amd64 ...
Preparing to replace libdrm-intel1:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm-intel1_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm-intel1:amd64 ...
Preparing to replace libdrm-nouveau1a:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm-nouveau1a_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm-nouveau1a:amd64 ...
Preparing to replace libdrm-radeon1:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm-radeon1_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm-radeon1:amd64 ...
Preparing to replace language-pack-en 1:12.04+20130128 (using .../language-pack-en_1%3a12.04+20140106_all.deb) ...
Unpacking replacement language-pack-en ...
Preparing to replace language-pack-en-base 1:12.04+20130128 (using .../language-pack-en-base_1%3a12.04+20140106_all.deb) ...
Unpacking replacement language-pack-en-base ...
Preparing to replace language-pack-gnome-en 1:12.04+20130128 (using .../language-pack-gnome-en_1%3a12.04+20140106_all.deb) ...
Unpacking replacement language-pack-gnome-en ...
Preparing to replace language-pack-gnome-en-base 1:12.04+20130128 (using .../language-pack-gnome-en-base_1%3a12.04+20140106_all.deb) ...
Unpacking replacement language-pack-gnome-en-base ...
Preparing to replace libdrm-nouveau2:amd64 2.4.43-0ubuntu0.0.3 (using .../libdrm-nouveau2_2.4.46-1ubuntu0.0.0.1_amd64.deb) ...
Unpacking replacement libdrm-nouveau2:amd64 ...
Preparing to replace libgtk-3-bin 3.4.2-0ubuntu0.5 (using .../libgtk-3-bin_3.4.2-0ubuntu0.6_amd64.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace libgail-3-0:amd64 3.4.2-0ubuntu0.5 (using .../libgail-3-0_3.4.2-0ubuntu0.6_amd64.deb) ...
Unpacking replacement libgail-3-0:amd64 ...
Preparing to replace libgtk-3-0:amd64 3.4.2-0ubuntu0.5 (using .../libgtk-3-0_3.4.2-0ubuntu0.6_amd64.deb) ...
Unpacking replacement libgtk-3-0:amd64 ...
Preparing to replace libgtk-3-common 3.4.2-0ubuntu0.5 (using .../libgtk-3-common_3.4.2-0ubuntu0.6_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace libxfixes-dev 1:5.0-4ubuntu4.1 (using .../libxfixes-dev_1%3a5.0-4ubuntu4.2_amd64.deb) ...
Unpacking replacement libxfixes-dev ...
Preparing to replace libxfixes3:amd64 1:5.0-4ubuntu4.1 (using .../libxfixes3_1%3a5.0-4ubuntu4.2_amd64.deb) ...
Unpacking replacement libxfixes3:amd64 ...
Preparing to replace x11proto-input-dev 2.1.99.6-1 (using .../x11proto-input-dev_2.3-1~precise1_all.deb) ...
Unpacking replacement x11proto-input-dev ...
Preparing to replace libxi-dev 2:1.6.0-0ubuntu2.1 (using .../libxi-dev_2%3a1.7.1.901-1ubuntu1~precise1_amd64.deb) ...
Unpacking replacement libxi-dev ...
Preparing to replace libxi6:amd64 2:1.6.0-0ubuntu2.1 (using .../libxi6_2%3a1.7.1.901-1ubuntu1~precise1_amd64.deb) ...
Unpacking replacement libxi6:amd64 ...
Preparing to replace libpixman-1-dev 0.24.4-1ubuntu0.1 (using .../libpixman-1-dev_0.30.2-1ubuntu0.0.0.0.1_amd64.deb) ...
Unpacking replacement libpixman-1-dev ...
Preparing to replace libpixman-1-0:amd64 0.24.4-1ubuntu0.1 (using .../libpixman-1-0_0.30.2-1ubuntu0.0.0.0.1_amd64.deb) ...
Unpacking replacement libpixman-1-0:amd64 ...
Preparing to replace libqt4-sql-sqlite:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-sql-sqlite_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-sql-sqlite:amd64 ...
Preparing to replace libqt4-help:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-help_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-help:amd64 ...
Preparing to replace libqt4-svg:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-svg_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-svg:amd64 ...
Preparing to replace libqt4-scripttools:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-scripttools_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-scripttools:amd64 ...
Preparing to replace libqt4-opengl:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-opengl_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-opengl:amd64 ...
Preparing to replace libqt4-designer:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-designer_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-designer:amd64 ...
Preparing to replace libqtgui4:amd64 4:4.8.1-0ubuntu4.5 (using .../libqtgui4_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqtgui4:amd64 ...
Preparing to replace libqt4-declarative:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-declarative_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-declarative:amd64 ...
Preparing to replace libqt4-sql:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-sql_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-sql:amd64 ...
Preparing to replace libqt4-xmlpatterns:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-xmlpatterns_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-xmlpatterns:amd64 ...
Preparing to replace libqt4-network:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-network_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-network:amd64 ...
Preparing to replace libqt4-script:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-script_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-script:amd64 ...
Preparing to replace libqt4-test:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-test_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-test:amd64 ...
Preparing to replace qdbus 4:4.8.1-0ubuntu4.5 (using .../qdbus_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement qdbus ...
Preparing to replace libqt4-dbus:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-dbus_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-dbus:amd64 ...
Preparing to replace libqt4-xml:amd64 4:4.8.1-0ubuntu4.5 (using .../libqt4-xml_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqt4-xml:amd64 ...
Preparing to replace libqtcore4:amd64 4:4.8.1-0ubuntu4.5 (using .../libqtcore4_4%3a4.8.1-0ubuntu4.6_amd64.deb) ...
Unpacking replacement libqtcore4:amd64 ...
Preparing to replace libglu1-mesa:amd64 8.0.4-0ubuntu0.6 (using .../libglu1-mesa_8.0.4-0ubuntu0.7_amd64.deb) ...
Unpacking replacement libglu1-mesa:amd64 ...
Preparing to replace iproute 20111117-1ubuntu2 (using .../iproute_20111117-1ubuntu2.1_amd64.deb) ...
Unpacking replacement iproute ...
Preparing to replace bind9-host 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../bind9-host_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement bind9-host ...
Preparing to replace dnsutils 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../dnsutils_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement dnsutils ...
Preparing to replace libisc83 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libisc83_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libisc83 ...
Preparing to replace libdns81 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libdns81_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libdns81 ...
Preparing to replace libisccc80 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libisccc80_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libisccc80 ...
Preparing to replace libisccfg82 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libisccfg82_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libisccfg82 ...
Preparing to replace liblwres80 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../liblwres80_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement liblwres80 ...
Preparing to replace libbind9-80 1:9.8.1.dfsg.P1-4ubuntu0.7 (using .../libbind9-80_1%3a9.8.1.dfsg.P1-4ubuntu0.8_amd64.deb) ...
Unpacking replacement libbind9-80 ...
Preparing to replace openssl 1.0.1-4ubuntu5.10 (using .../openssl_1.0.1-4ubuntu5.11_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace bc 1.06.95-2 (using .../bc_1.06.95-2ubuntu1_amd64.deb) ...
Unpacking replacement bc ...
Preparing to replace libck-connector0 0.4.5-2 (using .../libck-connector0_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libck-connector0 ...
Preparing to replace consolekit 0.4.5-2 (using .../consolekit_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement consolekit ...
Preparing to replace dc 1.06.95-2 (using .../dc_1.06.95-2ubuntu1_amd64.deb) ...
Unpacking replacement dc ...
Preparing to replace duplicity 0.6.18-0ubuntu3.3 (using .../duplicity_0.6.18-0ubuntu3.4_amd64.deb) ...
Unpacking replacement duplicity ...
Preparing to replace flashplugin-installer 11.2.202.332ubuntu0.12.04.1 (using .../flashplugin-installer_11.2.202.335ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement flashplugin-installer ...
Preparing to replace gir1.2-gtk-3.0 3.4.2-0ubuntu0.5 (using .../gir1.2-gtk-3.0_3.4.2-0ubuntu0.6_amd64.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace libappindicator3-1 0.4.92-0ubuntu1 (using .../libappindicator3-1_0.4.92-0ubuntu1.1_amd64.deb) ...
Unpacking replacement libappindicator3-1 ...
Preparing to replace gir1.2-appindicator3-0.1 0.4.92-0ubuntu1 (using .../gir1.2-appindicator3-0.1_0.4.92-0ubuntu1.1_amd64.deb) ...
Unpacking replacement gir1.2-appindicator3-0.1 ...
Preparing to replace python-appindicator 0.4.92-0ubuntu1 (using .../python-appindicator_0.4.92-0ubuntu1.1_amd64.deb) ...
Unpacking replacement python-appindicator ...
Preparing to replace libappindicator1 0.4.92-0ubuntu1 (using .../libappindicator1_0.4.92-0ubuntu1.1_amd64.deb) ...
Unpacking replacement libappindicator1 ...
Preparing to replace libcdt4 2.26.3-10ubuntu1 (using .../libcdt4_2.26.3-10ubuntu1.1_amd64.deb) ...
Unpacking replacement libcdt4 ...
Preparing to replace libgraph4 2.26.3-10ubuntu1 (using .../libgraph4_2.26.3-10ubuntu1.1_amd64.deb) ...
Unpacking replacement libgraph4 ...
Preparing to replace libpathplan4 2.26.3-10ubuntu1 (using .../libpathplan4_2.26.3-10ubuntu1.1_amd64.deb) ...
Unpacking replacement libpathplan4 ...
Preparing to replace libgvc5 2.26.3-10ubuntu1 (using .../libgvc5_2.26.3-10ubuntu1.1_amd64.deb) ...
Unpacking replacement libgvc5 ...
Preparing to replace libpam-ck-connector 0.4.5-2 (using .../libpam-ck-connector_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libpam-ck-connector ...
Preparing to replace unity 5.20.0-0ubuntu2 (using .../unity_5.20.0-0ubuntu3_amd64.deb) ...
Unpacking replacement unity ...
Preparing to replace unity-common 5.20.0-0ubuntu2 (using .../unity-common_5.20.0-0ubuntu3_all.deb) ...
Unpacking replacement unity-common ...
Preparing to replace libunity-core-5.0-5 5.20.0-0ubuntu2 (using .../libunity-core-5.0-5_5.20.0-0ubuntu3_amd64.deb) ...
Unpacking replacement libunity-core-5.0-5 ...
Preparing to replace unity-services 5.20.0-0ubuntu2 (using .../unity-services_5.20.0-0ubuntu3_amd64.deb) ...
Unpacking replacement unity-services ...
Preparing to replace unity-2d-panel 5.14.0-0ubuntu1 (using .../unity-2d-panel_5.14.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity-2d-panel ...
Preparing to replace unity-2d-shell 5.14.0-0ubuntu1 (using .../unity-2d-shell_5.14.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity-2d-shell ...
Preparing to replace unity-2d-spread 5.14.0-0ubuntu1 (using .../unity-2d-spread_5.14.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity-2d-spread ...
Preparing to replace unity-2d-common 5.14.0-0ubuntu1 (using .../unity-2d-common_5.14.0-0ubuntu2_all.deb) ...
Unpacking replacement unity-2d-common ...
Preparing to replace libunity-2d-private0 5.14.0-0ubuntu1 (using .../libunity-2d-private0_5.14.0-0ubuntu2_amd64.deb) ...
Unpacking replacement libunity-2d-private0 ...
Preparing to replace libxfont1 1:1.4.4-1 (using .../libxfont1_1%3a1.4.4-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libxfont1 ...
Preparing to replace python-software-properties 0.82.7.6 (using .../python-software-properties_0.82.7.7_all.deb) ...
Unpacking replacement python-software-properties ...
Preparing to replace software-properties-common 0.82.7.6 (using .../software-properties-common_0.82.7.7_all.deb) ...
Unpacking replacement software-properties-common ...
Preparing to replace software-properties-gtk 0.82.7.6 (using .../software-properties-gtk_0.82.7.7_all.deb) ...
Unpacking replacement software-properties-gtk ...
Preparing to replace unity-2d 5.14.0-0ubuntu1 (using .../unity-2d_5.14.0-0ubuntu2_all.deb) ...
Unpacking replacement unity-2d ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.335.orig.tar.gz
Installing from local file /tmp/tmp5ynCJ6.gz
Flash Plugin installed.
Processing triggers for gconf2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Setting up libdrm2:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libdrm-intel1:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libdrm-nouveau1a:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libdrm-radeon1:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libdrm-nouveau2:amd64 (2.4.46-1ubuntu0.0.0.1) ...
Setting up libgtk-3-common (3.4.2-0ubuntu0.6) ...
Setting up libxfixes3:amd64 (1:5.0-4ubuntu4.2) ...
Setting up libxi6:amd64 (2:1.7.1.901-1ubuntu1~precise1) ...
Setting up libgtk-3-0:amd64 (3.4.2-0ubuntu0.6) ...
Setting up libgtk-3-bin (3.4.2-0ubuntu0.6) ...
Setting up libgail-3-0:amd64 (3.4.2-0ubuntu0.6) ...
Setting up libxfixes-dev (1:5.0-4ubuntu4.2) ...
Setting up x11proto-input-dev (2.3-1~precise1) ...
Setting up libxi-dev (2:1.7.1.901-1ubuntu1~precise1) ...
Setting up libpixman-1-0:amd64 (0.30.2-1ubuntu0.0.0.0.1) ...
Setting up libpixman-1-dev (0.30.2-1ubuntu0.0.0.0.1) ...
Setting up libqtcore4:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-sql:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-sql-sqlite:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-xml:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-dbus:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-network:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-script:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-xmlpatterns:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-test:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up qdbus (4:4.8.1-0ubuntu4.6) ...
Setting up libglu1-mesa:amd64 (8.0.4-0ubuntu0.7) ...
Setting up iproute (20111117-1ubuntu2.1) ...
Setting up libisc83 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up libisccc80 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up liblwres80 (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up bind9-host (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up dnsutils (1:9.8.1.dfsg.P1-4ubuntu0.8) ...
Setting up openssl (1.0.1-4ubuntu5.11) ...
Setting up bc (1.06.95-2ubuntu1) ...
Setting up libck-connector0 (0.4.5-2ubuntu0.1) ...
Setting up consolekit (0.4.5-2ubuntu0.1) ...
Setting up dc (1.06.95-2ubuntu1) ...
Setting up duplicity (0.6.18-0ubuntu3.4) ...
Setting up flashplugin-installer (11.2.202.335ubuntu0.12.04.1) ...
Setting up gir1.2-gtk-3.0 (3.4.2-0ubuntu0.6) ...
Setting up libappindicator3-1 (0.4.92-0ubuntu1.1) ...
Setting up gir1.2-appindicator3-0.1 (0.4.92-0ubuntu1.1) ...
Setting up libappindicator1 (0.4.92-0ubuntu1.1) ...
Setting up python-appindicator (0.4.92-0ubuntu1.1) ...
Setting up libcdt4 (2.26.3-10ubuntu1.1) ...
Setting up libgraph4 (2.26.3-10ubuntu1.1) ...
Setting up libpathplan4 (2.26.3-10ubuntu1.1) ...
Setting up libgvc5 (2.26.3-10ubuntu1.1) ...
Setting up libpam-ck-connector (0.4.5-2ubuntu0.1) ...
Setting up unity-services (5.20.0-0ubuntu3) ...
Setting up libunity-core-5.0-5 (5.20.0-0ubuntu3) ...
Setting up unity-common (5.20.0-0ubuntu3) ...
Setting up unity (5.20.0-0ubuntu3) ...
Setting up unity-2d-common (5.14.0-0ubuntu2) ...
Setting up libxfont1 (1:1.4.4-1ubuntu0.1) ...
Setting up python-software-properties (0.82.7.7) ...
Setting up software-properties-common (0.82.7.7) ...
Setting up software-properties-gtk (0.82.7.7) ...
Setting up language-pack-en (1:12.04+20140106) ...
Setting up language-pack-en-base (1:12.04+20140106) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
Setting up language-pack-gnome-en (1:12.04+20140106) ...
Setting up language-pack-gnome-en-base (1:12.04+20140106) ...
Setting up libqtgui4:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-declarative:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-help:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-svg:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-scripttools:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-opengl:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libqt4-designer:amd64 (4:4.8.1-0ubuntu4.6) ...
Setting up libunity-2d-private0 (5.14.0-0ubuntu2) ...
Setting up unity-2d-panel (5.14.0-0ubuntu2) ...
Setting up unity-2d-shell (5.14.0-0ubuntu2) ...
Setting up unity-2d-spread (5.14.0-0ubuntu2) ...
Setting up unity-2d (5.14.0-0ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...

```


sudo apt-get install humanity-icon-theme
```

sean@Sean-Monster:~$ sudo apt-get install humanity-icon-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpurple0 libical0 telepathy-indicator usb-modeswitch indicator-printers
  dnsmasq-base python-cupshelpers folks-common libmtp9 telepathy-logger
  gir1.2-rb-3.0 gir1.2-gstreamer-0.10 libnl-3-200 telepathy-gabble
  libebackend-1.2-1 libpurple-bin ubuntu-docs python-mako libgmime-2.6-0
  libdmapsharing-3.0-2 rhythmbox-data libmeanwhile1 gir1.2-gmenu-3.0
  libkpathsea5 oneconf libdiscid0 libmtp-runtime unity-lens-video libspectre1
  libnm-gtk0 libgpod-common libevince3-3 python-piston-mini-client
  unity-scope-video-remote libburn4 telepathy-haze libtelepathy-logger2
  unity-common libnm-util2 ubuntu-extras-keyring gnome-menus empathy-common
  libgoa-1.0-0 libgupnp-1.0-4 usb-modeswitch-data
  mobile-broadband-provider-info libindicate-gtk3 libgweather-3-0
  python-gnomekeyring gnome-control-center-data libunity-misc4
  librhythmbox-core5 libtotem0 telepathy-salut apturl-common libgpod4
  libedata-book-1.2-11 libgweather-common libgnome-menu-3-0
  gtk2-engines-murrine network-manager-pptp pptp-linux unity-lens-music
  avahi-utils gtk3-engines-unico libfarstream-0.1-0 unity-2d-spread libfolks25
  python-debtagshw libedata-cal-1.2-13 gir1.2-totem-1.0 libgrip0 libnice10
  libgdata-common apg libnetfilter-conntrack3 network-manager libgdata13
  libnl-genl-3-200 unity-lens-files libnm-gtk-common libt1-5 libgnome2-common
  gir1.2-totem-plparser-1.0 libnm-glib-vpn1 iputils-arping libcurl3-nss
  libnm-glib4 libnl-route-3-200 modemmanager python-smbc
  system-config-printer-udev gir1.2-gst-plugins-base-0.10 evince-common
  mousetweaks libpoppler-glib8 libtelepathy-farstream2 growisofs
  libecal-1.2-10 wpasupplicant network-manager-pptp-gnome libfolks-eds25
  libtotem-plparser17 gir1.2-gudev-1.0 libquvi7 libmtp-common
  libgupnp-igd-1.0-4 python-cups brasero-cdrkit ubuntu-wallpapers
  libmission-control-plugins0 brasero-common media-player-info
  gir1.2-launchpad-integration-3.0 libquvi-scripts python-markupsafe
  evolution-data-server-common libmusicbrainz3-6 evolution-data-server
  libzephyr4 gnome-online-accounts nux-tools libjte1
  software-center-aptdaemon-plugins libgnome-menu2
  system-config-printer-common libisofs6 dvd+rw-tools libavahi-gobject0
  unity-lens-applications gstreamer0.10-nice libfolks-telepathy25 liboauth0
  libgoa-1.0-common totem-common python-gconf adium-theme-ubuntu
  libgssdp-1.0-3 libbrasero-media3-1 nautilus-sendto-empathy
  telepathy-mission-control-5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gnome-icon-theme
The following NEW packages will be installed:
  gnome-icon-theme humanity-icon-theme
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,548 kB of archives.
After this operation, 21.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.utexas.edu/ubuntu/ precise/main humanity-icon-theme all 0.5.3.11 [2,889 kB]
Get:2 http://ftp.utexas.edu/ubuntu/ precise-updates/main gnome-icon-theme all 3.4.0-0ubuntu1.1 [659 kB]
Fetched 3,548 kB in 6s (588 kB/s)                                              
Selecting previously unselected package humanity-icon-theme.
(Reading database ... 264493 files and directories currently installed.)
Unpacking humanity-icon-theme (from .../humanity-icon-theme_0.5.3.11_all.deb) ...
Selecting previously unselected package gnome-icon-theme.
Unpacking gnome-icon-theme (from .../gnome-icon-theme_3.4.0-0ubuntu1.1_all.deb) ...
Setting up gnome-icon-theme (3.4.0-0ubuntu1.1) ...
Setting up humanity-icon-theme (0.5.3.11) ...

```


...decided to run sudo dpkg -C again..
```

sean@Sean-Monster:~$ sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 g++                  GNU C++ compiler
 libaudio2:amd64      Network Audio System - shared libraries
 binutils             GNU assembler, linker and binary utilities

```

---

### Post by j88n on 2014-01-21
...i should say that I'm noticing a lot of missing icons now, which is kind of concerning =/

---

### Post by Bashing-om on 2014-01-21
j88n; Wow, all that for a little bitty icon theme !

Ok, rinse and repeat with the other three packages, purge them and install them, one at a time.

carefully and see what happens.

[INDENT][INDENT]simply amazing
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-01-21
j88n; welll,

The missing icons I expect will reappear when you reboot.
We took them out, and the files have been replaced, but the linkage has not till the system is rebooted.

[INDENT]leastways
[INDENT][INDENT]in a perfect world
[/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
Okay I ran..

sudo apt-get purge g++
sudo apt-get install g++
sudo apt-get purge libaudio2:amd64
sudo apt-get install libaudio2:amd64
sudo apt-get purge binutils
sudo apt-get install binutils

then...
sudo dpkg -C 

and returned not result.. so i think that's good. Should I apt-get update/upgrade? I am still missing some icons

---

### Post by Bashing-om on 2014-01-21
j88n; welp;
I am surprised,

Yeah go ahead update/upgrade, may not help but sure can not hurt.

then reboot and see what is.

[INDENT][INDENT]breaking it 
[INDENT][INDENT][INDENT]to fix it ???
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
this was the output from upgrading:

```

sean@Sean-Monster:~$ sudo apt-get update
Hit http://ftp.utexas.edu precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg                           
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://archive.canonical.com precise Release                      
Hit http://extras.ubuntu.com precise Release    
Get:2 http://ftp.utexas.edu precise-updates Release.gpg [198 B]       
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://extras.ubuntu.com precise/main amd64 Packages              
Get:3 http://archive.canonical.com precise/partner i386 Packages [8,948 B]
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:4 http://extras.ubuntu.com precise/main i386 Packages [10.8 kB]            
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:5 http://ftp.utexas.edu precise-security Release.gpg [198 B]               
Hit http://ftp.utexas.edu precise Release                                      
Get:6 http://ftp.utexas.edu precise-updates Release [49.6 kB]                  
Get:7 http://ftp.utexas.edu precise-security Release [49.6 kB]                 
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://ftp.utexas.edu precise/main Sources                                 
Ign http://extras.ubuntu.com precise/main Translation-en_US            
Hit http://ftp.utexas.edu precise/restricted Sources
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://ftp.utexas.edu precise/universe Sources
Hit http://ftp.utexas.edu precise/multiverse Sources
Hit http://ftp.utexas.edu precise/main amd64 Packages
Hit http://ftp.utexas.edu precise/restricted amd64 Packages
Hit http://ftp.utexas.edu precise/universe amd64 Packages
Hit http://ftp.utexas.edu precise/multiverse amd64 Packages
Get:8 http://ftp.utexas.edu precise/main i386 Packages [1,274 kB]
Get:9 http://ftp.utexas.edu precise/restricted i386 Packages [8,431 B]  
Get:10 http://ftp.utexas.edu precise/universe i386 Packages [4,796 kB]  
Get:11 http://ftp.utexas.edu precise/multiverse i386 Packages [121 kB]         
Hit http://ftp.utexas.edu precise/main TranslationIndex                        
Hit http://ftp.utexas.edu precise/multiverse TranslationIndex                  
Hit http://ftp.utexas.edu precise/restricted TranslationIndex                  
Hit http://ftp.utexas.edu precise/universe TranslationIndex                    
Get:12 http://ftp.utexas.edu precise-updates/main Sources [448 kB]             
Get:13 http://ftp.utexas.edu precise-updates/restricted Sources [7,039 B]      
Get:14 http://ftp.utexas.edu precise-updates/universe Sources [101 kB]         
Get:15 http://ftp.utexas.edu precise-updates/multiverse Sources [8,486 B]      
Get:16 http://ftp.utexas.edu precise-updates/main amd64 Packages [744 kB]      
Get:17 http://ftp.utexas.edu precise-updates/restricted amd64 Packages [11.4 kB]
Get:18 http://ftp.utexas.edu precise-updates/universe amd64 Packages [231 kB]  
Get:19 http://ftp.utexas.edu precise-updates/multiverse amd64 Packages [14.2 kB]
Get:20 http://ftp.utexas.edu precise-updates/main i386 Packages [768 kB]       
Get:21 http://ftp.utexas.edu precise-updates/restricted i386 Packages [11.5 kB]
Get:22 http://ftp.utexas.edu precise-updates/universe i386 Packages [236 kB]   
Get:23 http://ftp.utexas.edu precise-updates/multiverse i386 Packages [14.4 kB]
Get:24 http://ftp.utexas.edu precise-updates/main TranslationIndex [3,564 B]   
Get:25 http://ftp.utexas.edu precise-updates/multiverse TranslationIndex [2,605 B]
Get:26 http://ftp.utexas.edu precise-updates/restricted TranslationIndex [2,461 B]
Get:27 http://ftp.utexas.edu precise-updates/universe TranslationIndex [2,850 B]
Get:28 http://ftp.utexas.edu precise-security/main Sources [96.7 kB]           
Get:29 http://ftp.utexas.edu precise-security/restricted Sources [2,494 B]     
Get:30 http://ftp.utexas.edu precise-security/universe Sources [30.5 kB]       
Get:31 http://ftp.utexas.edu precise-security/multiverse Sources [1,797 B]     
Get:32 http://ftp.utexas.edu precise-security/main amd64 Packages [357 kB]     
Get:33 http://ftp.utexas.edu precise-security/restricted amd64 Packages [4,627 B]
Get:34 http://ftp.utexas.edu precise-security/universe amd64 Packages [90.1 kB]
Get:35 http://ftp.utexas.edu precise-security/multiverse amd64 Packages [2,454 B]
Get:36 http://ftp.utexas.edu precise-security/main i386 Packages [377 kB]      
Get:37 http://ftp.utexas.edu precise-security/restricted i386 Packages [4,620 B]
Get:38 http://ftp.utexas.edu precise-security/universe i386 Packages [94.3 kB] 
Get:39 http://ftp.utexas.edu precise-security/multiverse i386 Packages [2,650 B]
Get:40 http://ftp.utexas.edu precise-security/main TranslationIndex [74 B]     
Get:41 http://ftp.utexas.edu precise-security/multiverse TranslationIndex [72 B]
Get:42 http://ftp.utexas.edu precise-security/restricted TranslationIndex [72 B]
Get:43 http://ftp.utexas.edu precise-security/universe TranslationIndex [73 B] 
Hit http://ftp.utexas.edu precise/main Translation-en                          
Hit http://ftp.utexas.edu precise/multiverse Translation-en                    
Hit http://ftp.utexas.edu precise/restricted Translation-en                    
Hit http://ftp.utexas.edu precise/universe Translation-en                      
Get:44 http://ftp.utexas.edu precise-updates/main Translation-en [334 kB]      
Hit http://ftp.utexas.edu precise-updates/multiverse Translation-en            
Hit http://ftp.utexas.edu precise-updates/restricted Translation-en            
Get:45 http://ftp.utexas.edu precise-updates/universe Translation-en [135 kB]  
Get:46 http://ftp.utexas.edu precise-security/main Translation-en [168 kB]     
Hit http://ftp.utexas.edu precise-security/multiverse Translation-en           
Hit http://ftp.utexas.edu precise-security/restricted Translation-en           
Get:47 http://ftp.utexas.edu precise-security/universe Translation-en [56.1 kB]
Fetched 10.7 MB in 26s (406 kB/s)                                              
Reading package lists... Done
sean@Sean-Monster:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  hplip hplip-data libhpmud0 libmysqlclient18 libsane-hpaio mysql-common
  printer-driver-hpcups printer-driver-hpijs printer-driver-postscript-hp
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,386 kB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://ftp.utexas.edu/ubuntu/ precise-updates/main mysql-common all 5.5.35-0ubuntu0.12.04.1 [13.0 kB]
Get:2 http://ftp.utexas.edu/ubuntu/ precise-updates/main libmysqlclient18 amd64 5.5.35-0ubuntu0.12.04.1 [945 kB]
Get:3 http://ftp.utexas.edu/ubuntu/ precise-updates/universe printer-driver-postscript-hp all 3.12.2-1ubuntu3.4 [776 kB]
Get:4 http://ftp.utexas.edu/ubuntu/ precise-updates/main printer-driver-hpijs amd64 3.12.2-1ubuntu3.4 [354 kB]
Get:5 http://ftp.utexas.edu/ubuntu/ precise-updates/main libsane-hpaio amd64 3.12.2-1ubuntu3.4 [129 kB]
Get:6 http://ftp.utexas.edu/ubuntu/ precise-updates/main hplip amd64 3.12.2-1ubuntu3.4 [88.9 kB]
Get:7 http://ftp.utexas.edu/ubuntu/ precise-updates/main libhpmud0 amd64 3.12.2-1ubuntu3.4 [112 kB]
Get:8 http://ftp.utexas.edu/ubuntu/ precise-updates/main hplip-data all 3.12.2-1ubuntu3.4 [6,663 kB]
Get:9 http://ftp.utexas.edu/ubuntu/ precise-updates/main printer-driver-hpcups amd64 3.12.2-1ubuntu3.4 [305 kB]
Fetched 9,386 kB in 10s (861 kB/s)                                             
(Reading database ... 265883 files and directories currently installed.)
Preparing to replace mysql-common 5.5.34-0ubuntu0.12.04.1 (using .../mysql-common_5.5.35-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient18:amd64 5.5.34-0ubuntu0.12.04.1 (using .../libmysqlclient18_5.5.35-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libmysqlclient18:amd64 ...
Preparing to replace printer-driver-postscript-hp 3.12.2-1ubuntu3.3 (using .../printer-driver-postscript-hp_3.12.2-1ubuntu3.4_all.deb) ...
Unpacking replacement printer-driver-postscript-hp ...
Preparing to replace printer-driver-hpijs 3.12.2-1ubuntu3.3 (using .../printer-driver-hpijs_3.12.2-1ubuntu3.4_amd64.deb) ...
Unpacking replacement printer-driver-hpijs ...
Preparing to replace libsane-hpaio 3.12.2-1ubuntu3.3 (using .../libsane-hpaio_3.12.2-1ubuntu3.4_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip 3.12.2-1ubuntu3.3 (using .../hplip_3.12.2-1ubuntu3.4_amd64.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.12.2-1ubuntu3.3 (using .../libhpmud0_3.12.2-1ubuntu3.4_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.12.2-1ubuntu3.3 (using .../hplip-data_3.12.2-1ubuntu3.4_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace printer-driver-hpcups 3.12.2-1ubuntu3.3 (using .../printer-driver-hpcups_3.12.2-1ubuntu3.4_amd64.deb) ...
Unpacking replacement printer-driver-hpcups ...
Processing triggers for cups ...
Updating PPD files for hpcups ...
Updating PPD files for hpijs ...
Updating PPD files for postscript-hp ...
Processing triggers for man-db ...
Setting up mysql-common (5.5.35-0ubuntu0.12.04.1) ...
Setting up libmysqlclient18:amd64 (5.5.35-0ubuntu0.12.04.1) ...
Setting up libhpmud0 (3.12.2-1ubuntu3.4) ...
Setting up libsane-hpaio (3.12.2-1ubuntu3.4) ...
Setting up hplip-data (3.12.2-1ubuntu3.4) ...
Setting up printer-driver-hpcups (3.12.2-1ubuntu3.4) ...
Setting up hplip (3.12.2-1ubuntu3.4) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.12.2-1ubuntu3.4) ...
Setting up printer-driver-hpijs (3.12.2-1ubuntu3.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

...restarting now

---

### Post by j88n on 2014-01-21
...so it seems to be completely broke now. I can't open anything... The side bar and top bar are completely missing :(

---

### Post by Bashing-om on 2014-01-21
j88n; What in the world IS going on !

Try this:
boot to the login GUI ->ctl+alt+f1 to gain a console:
terminal command:
```

unity --reset

```
Which should first reset compiz then unity to the default settings.

[INDENT][INDENT]getting curiouser and curiouser
 [/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
When I try to open the terminal... It's just a black screen, I can't type anything

---

### Post by Bashing-om on 2014-01-21
j88n; yuk, again

Maybe just as well, seems I recall that to reset unity one has to do so while the GUI is active,

lets try that .. see if you can boot to the GUI desktop and ctl+alt+t to gain a terminal:
then run the unity --reset command.

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to keep
[INDENT][INDENT]an operating system like you - satisfied [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
Wondering if I can boot from a LiveCD to restore some functionality... Do you have some thoughts on how..?

---

### Post by j88n on 2014-01-21
It boots to the GUI desktop normally... Opening the terminal produces the same result, black terminal screen with no way to type

---

### Post by Bashing-om on 2014-01-21
j88n;

That makes no sense at all, just the way it is.

Nope, I see no way to fix this from the liveCD.
But let's try this:
Boot to grub, normal boot kernel highlighted, 'e' key for edit mode;
arrow down and across to the terms "quiet splash" enter the term "text" - without the quotes - remove the terms quiet splash and all after,
key combo ctl+x to continue the boot process to a terminal login (TTY1).
Log in and enter password
terminal command:
```

sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop

```
This will install the desktop environment again. After that, reboot and (fingers crossed) you'll get a desktop again.
But the way things are going I have to wonder what else is going to break !

[INDENT][INDENT][INDENT]try try and try again
[/INDENT][/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
I'm not familiar with how to boot to grub...how do I do that?

---

### Post by Bashing-om on 2014-01-21
j88n; not a problem'

reboot, and as soon as the bios screen clears, depress and hold the left shift key
the grub boot menu should appear.

[INDENT][INDENT]more than one way to skin 3 cats
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
Just to verify... I remove "quiet splash $vt_handoff intrd /boot/initrd.img-3.8.0-35-generic" and replace with "text" then press ctrl-x??

---

### Post by Bashing-om on 2014-01-21
j88n; Ouch,

that does not look right at all !
should be something similar:
linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff

OR should I reboot my system just to make real real sure ( rather a pain right now, but can do. 4 windows going .. and 4 others in IRC ..
take me a bit to back out) .. call it !

better safe than sorry

---

### Post by j88n on 2014-01-21
i see that line you wrote but that's BEFORE quiet splash, not AFTER..

I just want to make sure I am not removing too much

---

### Post by Bashing-om on 2014-01-21
j88nl some thing stinks!

best be safe,, give me a few and I will be back .. going to look at my 12.04.

hang loose
[INDENT][INDENT]or not too uptight
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
This is what I see now:

setparams 'Ubuntu, with Linux 3.8.0-35-generic'

recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 2a79eaa8-e1b8-4b33-83d1-a2912a703525
linux /boot/vmlinuz-3.8.0-35-generic root=UUID=2a79eaa8-e1b8-4b33-83d1-a2912a703525 ro quiet splash $vt_handoff
initrd /boot/initrd.img-3.8.0-35-generic

---

### Post by Bashing-om on 2014-01-21
j88n: yes !

That I can confirm, so; before "quiet splash $vt_handoff" enter the term "text" - without those quotes - and delete "quiet splash $vt_handoff".
ctl+x to continue the boot process -> to a text terminal.
yes ?

[INDENT][INDENT]where there is life there is hope
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
okay now it looks like:[COLOR=#000000]setparams 'Ubuntu, with Linux 3.8.0-35-generic'[/COLOR]

[COLOR=#000000]recordfail[/COLOR]
[COLOR=#000000]gfxmode $linux_gfx_mode[/COLOR]
[COLOR=#000000]insmod gzio[/COLOR]
[COLOR=#000000]insmod part_msdos[/COLOR]
[COLOR=#000000]insmod ext2[/COLOR]
[COLOR=#000000]set root='(hd0,msdos1)'[/COLOR]
[COLOR=#000000]search --no-floppy --fs-uuid --set=root 2a79eaa8-e1b8-4b33-83d1-a2912a703525[/COLOR]
[COLOR=#000000]linux /boot/vmlinuz-3.8.0-35-generic root=UUID=2a79eaa8-e1b8-4b33-83d1-a2912a703525 ro text[/COLOR]
[COLOR=#000000]initrd /boot/initrd.img-3.8.0-35-generic

...hitting ctrl-x and logging in now[/COLOR]

---

### Post by j88n on 2014-01-21
I ran: sudo apt-get purge ubuntu-desktop

and the response was that it wasn't installed, so won't be removed.

Running the command:

sudo apt-get install ubuntu-desktop

...it's moving along , should I restart when it's done?

---

### Post by Bashing-om on 2014-01-21
j88n; uhm..
No, let's not reboot yet.

When it completes;
What results from:
```

sudo service lightdm start

```
I ask again ->
[INDENT][INDENT]what in the world is going on ? [/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
looks like it automatically started the GUI login page, yay!

I logged in and the desktop seems to be restored, as well as the side bar and top menu bar! The terminal window also opens successfully

---

### Post by Bashing-om on 2014-01-21
j88n; Great !

okay ->
```

sudo dpkg -C

```
we want to know !

[INDENT][INDENT]are we still together
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
Yup!

No output when running 'sudo dpkg -C' ...that's a good sign, right?!

---

### Post by Bashing-om on 2014-01-21
j88n; That is an excellent sign !

Sure relieves a lot of anxiety !..

OK, play with the system,, see that all works .. and open a few personal files... all good ?

now reboot .. and tell me all is still good !

I have some other things to get caught up on,
I will be back shortly.

[INDENT][INDENT]who was that masked man
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-21
Thanks for walking me through this!!!

Everything looks good, except after rebooting & opening chrome, I experienced an internal error. Not sure what triggered it though.. rebooting or opening chrome:

ExecutablePath
/usr/lib/gnome-online-accounts/goa-daemon

Package
gnome-online-accounts 3.4.0-0ubuntu1.1

ProblemType
Crash

Title
goa-daemon crashed with signal 7

ApportVersion
2.0.1-0ubuntu17.6

Architecture
amd64

CoreDump
(binary data)

etc...

---

### Post by Bashing-om on 2014-01-21
j88n; erre;

Maybe we are not out of the woods after all.

Play around in the system some and reboot a few times, see if anything breaks...

I still have my suspistions (sp) that all is not !

[INDENT][INDENT]but it could be all is good,, 
[/INDENT][/INDENT]

---

### Post by j88n on 2014-01-22
Also gnome-control-center still won't open. I get the bus error and pop-up that says that the application has closed unexpectedly.

I'm going to continue to play around with everything

---

### Post by Bashing-om on 2014-01-22
j88n; not good !

see what else, -> broken

other things but I will be back

---

### Post by j88n on 2014-01-22
After a reboot, the error has not reappeared (yet) after opening chrome. I ran the command:

sudo apt-get autoremove

there is quite a bit of packages to be removed. Do you think I should I do it?

```
sean@Sean-Monster:~$ sudo apt-get autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  chipmunk-dev dh-apparmor gir1.2-rsvg-2.0 html2text intltool-debian ledit
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libatk1.0-dev libbsd-dev libcairo-script-interpreter2 libcairo2-dev
  libchipmunk0d1 libdpkg-perl libexpat1-dev libffi-dev libfontconfig1-dev
  libfreetype6-dev libgdk-pixbuf2.0-dev libglib2.0-dev libgmp-dev
  libgmpxx4ldbl libgtk2.0-dev libice-dev libmail-sendmail-perl libncurses5-dev
  libpango1.0-dev libpcre3-dev libpcrecpp0 libpixman-1-dev libpng12-dev
  libpthread-stubs0 libpthread-stubs0-dev libqt4-test libqtassistantclient4
  librsvg2-dev libsm-dev libsys-hostname-long-perl libtimedate-perl
  libtinfo-dev libx11-dev libx11-doc libxau-dev libxcb-render0-dev
  libxcb-shm0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev
  libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxrandr-dev libxrender-dev ocaml-interp po-debconf python-sip
  ubuntuone-control-panel-common x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev zlib1g-dev
0 upgraded, 0 newly installed, 75 to remove and 0 not upgraded.
After this operation, 74.7 MB disk space will be freed.

```

---

### Post by j88n on 2014-01-22
Calling it quits for me tonight. Will spend the day playing around with the computer and will see if I notice anything else, thanks again!!

---

### Post by Bashing-om on 2014-01-22
j88n; hey !


Good for me too, my thinkability has become impaired once more .

[INDENT][INDENT]tomorrow
[/INDENT][/INDENT]

---

### Post by spencer the great on 2014-01-27
If your problem is fixed, don't autoremove.  Maybe it's just me, but I manage to break everything upon autoremove.  Just don't do it if your problem is fixed and you have plenty of free disk space.

---

