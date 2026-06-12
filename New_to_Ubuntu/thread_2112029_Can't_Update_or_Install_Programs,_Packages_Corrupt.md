---
title: "Can't Update or Install Programs, Packages Corrupt?"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by DesertFox001 on 2013-02-03
Hello all and thank you ahead of time for any help I might get. I am unable to update ubuntu and after looking up as much as I can understand I have been unable to fix the problem. The desktop (Kitt) is up and running still just fine but I can't update or install new software. Pretty sure it won't let me install or remove any packages. I apologize for the walls of code that follow.

Runnig Ubuntu 12.04, tried updating to 12.10 but it had the same failure as trying to update 12.04 normally. 

What I have tried doing

```

sudo apt-get update

```Returns 
```
 
Ign http://us.archive.ubuntu.com quantal InRelease
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Ign http://us.archive.ubuntu.com quantal-proposed InRelease                    
Hit http://us.archive.ubuntu.com quantal Release.gpg                 
Hit http://us.archive.ubuntu.com quantal-updates Release.gpg                   
Hit http://us.archive.ubuntu.com quantal-proposed Release.gpg                  
Hit http://us.archive.ubuntu.com quantal Release                               
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://security.ubuntu.com quantal-security InRelease            
Ign http://archive.canonical.com quantal InRelease                   
Hit http://us.archive.ubuntu.com quantal-updates Release                       
Hit http://us.archive.ubuntu.com quantal-proposed Release                      
Hit http://us.archive.ubuntu.com quantal/main Sources                          
Hit http://us.archive.ubuntu.com quantal/restricted Sources                    
Hit http://us.archive.ubuntu.com quantal/universe Sources            
Hit http://us.archive.ubuntu.com quantal/multiverse Sources                    
Hit http://us.archive.ubuntu.com quantal/main i386 Packages                    
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages              
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages                
Hit http://extras.ubuntu.com quantal Release.gpg                               
Hit http://security.ubuntu.com quantal-security Release.gpg                    
Hit http://archive.canonical.com quantal Release.gpg                 
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com quantal/main TranslationIndex       
Hit http://us.archive.ubuntu.com quantal/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com quantal/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com quantal/universe TranslationIndex   
Hit http://us.archive.ubuntu.com quantal-updates/main Sources                  
Hit http://us.archive.ubuntu.com quantal-updates/restricted Sources            
Hit http://us.archive.ubuntu.com quantal-updates/universe Sources              
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com quantal-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com quantal-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com quantal-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com quantal-updates/multiverse TranslationIndex
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://security.ubuntu.com quantal-security Release                        
Hit http://archive.canonical.com quantal Release                               
Hit http://us.archive.ubuntu.com quantal-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com quantal-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com quantal-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com quantal-proposed/main i386 Packages           
Hit http://us.archive.ubuntu.com quantal-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com quantal-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com quantal-proposed/main TranslationIndex
Hit http://us.archive.ubuntu.com quantal-proposed/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com quantal-proposed/restricted TranslationIndex
Hit http://us.archive.ubuntu.com quantal-proposed/universe TranslationIndex
Hit http://us.archive.ubuntu.com quantal/main Translation-en                   
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en   
Hit http://us.archive.ubuntu.com quantal/universe Translation-en     
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en 
Hit http://extras.ubuntu.com quantal/main Sources                    
Hit http://security.ubuntu.com quantal-security/main Sources         
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Hit http://archive.canonical.com quantal/partner i386 Packages       
Hit http://us.archive.ubuntu.com quantal-proposed/main Translation-en
Hit http://us.archive.ubuntu.com quantal-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-proposed/universe Translation-en
Hit http://extras.ubuntu.com quantal/main i386 Packages              
Ign http://extras.ubuntu.com quantal/main TranslationIndex           
Hit http://security.ubuntu.com quantal-security/restricted Sources
Hit http://security.ubuntu.com quantal-security/universe Sources
Hit http://security.ubuntu.com quantal-security/multiverse Sources
Hit http://security.ubuntu.com quantal-security/main i386 Packages
Hit http://security.ubuntu.com quantal-security/restricted i386 Packages
Hit http://security.ubuntu.com quantal-security/universe i386 Packages
Hit http://security.ubuntu.com quantal-security/multiverse i386 Packages
Hit http://security.ubuntu.com quantal-security/main TranslationIndex
Hit http://security.ubuntu.com quantal-security/multiverse TranslationIndex
Hit http://security.ubuntu.com quantal-security/restricted TranslationIndex
Ign http://archive.canonical.com quantal/partner TranslationIndex    
Hit http://security.ubuntu.com quantal-security/universe TranslationIndex
Hit http://security.ubuntu.com quantal-security/main Translation-en  
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Ign http://extras.ubuntu.com quantal/main Translation-en_US
Ign http://archive.canonical.com quantal/partner Translation-en_US
Ign http://extras.ubuntu.com quantal/main Translation-en
Ign http://archive.canonical.com quantal/partner Translation-en
Reading package lists... Done

```Everything seems normal there. Next I run 

```

sudo apt-get upgrade

```which is where the problems arise. Output as follows.

```
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apparmor-utils apport apport-gtk apt-utils aptdaemon apturl apturl-common
  bamfdaemon banshee banshee-extension-soundmenu baobab bluez brltty
  brltty-x11 browser-plugin-gnash checkbox checkbox-gtk checkbox-qt cheese
  cheese-common colord command-not-found compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default couchdb-bin cpp cpp-4.6 cups-filters
  dbus dconf-gsettings-backend dconf-service dconf-tools dpkg-dev ekiga
  emesene empathy empathy-common eog epiphany-browser epiphany-browser-data
  epiphany-extensions erlang-base erlang-crypto erlang-inets erlang-mnesia
  erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools
  erlang-xmerl evince evince-common evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-plugins exiv2
  foomatic-db-compressed-ppds g++ g++-4.6 gcc gcc-4.6 gcc-4.6-base gdm
  get-flash-videos gettext gettext-base ghostscript ghostscript-x gimp
  gimp-data gir1.2-gkbd-3.0 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-mutter-3.0 gir1.2-peas-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-unity-5.0 gjs glchess glines gnash gnash-common gnect gnibbles
  gnobots2 gnome-applets gnome-applets-data gnome-bluetooth gnome-contacts
  gnome-control-center gnome-control-center-data gnome-desktop3-data
  gnome-disk-utility gnome-font-viewer gnome-games gnome-games-data
  gnome-keyring gnome-nettool gnome-online-accounts gnome-orca gnome-panel
  gnome-panel-data gnome-screensaver gnome-session gnome-session-bin
  gnome-session-common gnome-session-fallback gnome-settings-daemon
  gnome-shell gnome-shell-common gnome-sudoku gnome-system-log
  gnome-themes-standard gnome-user-share gnomine gnotravex gnotski gpodder
  grub-common grub-pc grub-pc-bin grub2-common gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-ugly gtali gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hamster-applet iagno imagemagick indicator-appmenu indicator-datetime
  indicator-messages indicator-session inkscape irqbalance
  language-selector-common language-selector-gnome libatk-adaptor libbamf0
  libbamf3-0 libblas3gf libclass-load-perl libclutter-imcontext-0.1-0
  libcompizconfig0 libcupsfilters1 libdconf-dbus-1-0 libdecoration0
  libdpkg-perl libevolution libexttextcat-data libfolks-eds25 libgail-3-0
  libgcc1 libgck-1-0 libgcr-3-1 libgdata13 libgdiplus libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-common libgettextpo0 libgexiv2-1 libgfortran3 libgimp2.0
  libgjs0c libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libgnome-control-center1 libgoa-1.0-0 libgoa-1.0-common libgomp1
  libgpod-common libgpod4 libgs9 libgs9-common libgstreamer-plugins-bad0.10-0
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 liblapack3gf
  liblua5.1-rex-pcre0 liblua5.1-sql-sqlite3-2 libmutter0 libmx-1.0-2
  libnetpbm10 libpackagekit-glib2-14 libpam-winbind libparams-validate-perl
  libpeas-1.0-0 libplymouth2 libpoppler-glib8 libqt4-dbus libqt4-declarative
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtgui4
  libquadmath0 libraptor2-0 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-impress libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-math libreoffice-style-tango libreoffice-writer libsane
  libsane-common libsdl-image1.2 libspandsp2 libstdc++6 libstdc++6-4.6-dev
  libsvn1 libtiff4 libtorrent-rasterbar6 libtotem0 libunity9 libwbclient0
  libwxgtk2.8-0 libxatracker1 lightsoff linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae lsb-release mahjongg
  metacity mudlet mutter-common nautilus nautilus-data nautilus-sendto
  nautilus-sendto-empathy netpbm network-manager-gnome nvidia-common onboard
  openprinting-ppds overlay-scrollbar perlmagick plymouth plymouth-label
  poppler-utils printer-driver-c2esp printer-driver-foo2zjs
  printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr
  printer-driver-splix procps python-apt python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-debian
  python-gpod python-packagekit python-ubuntu-sso-client
  python-ubuntuone-control-panel python-uno qbittorrent qdbus quadrapassel
  rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  samba-common screen-resolution-extra seahorse shotwell smbclient
  software-center software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk sound-juicer subversion swell-foop synaptic
  telepathy-indicator thunderbird thunderbird-globalmenu
  thunderbird-gnome-support totem totem-common totem-mozilla totem-plugins
  transmission-common transmission-gtk ttf-freefont ubuntu-desktop
  ubuntu-minimal ubuntu-sso-client ubuntu-sso-client-qt ubuntu-wallpapers
  ubuntuone-control-panel ubuntuone-control-panel-qt ufw unattended-upgrades
  unity unity-common unity-greeter unity-lens-applications unity-lens-files
  unity-lens-music unity-lens-video unity-scope-musicstores
  unity-scope-video-remote unity-services update-manager update-manager-core
  update-notifier update-notifier-common upower usbmuxd vinagre vlc vlc-nox
  vlc-plugin-notify vlc-plugin-pulse whoopsie winbind wine1.4 wine1.4-common
  wine1.4-i386 xdiagnose xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xz-utils
The following packages will be upgraded:
  accountsservice acl acpi-support acpid activity-log-manager-common
  activity-log-manager-control-center adduser adium-theme-ubuntu
  adobe-flash-properties-gtk adobe-flashplugin aisleriot alacarte alsa-base
  alsa-utils anacron apg app-install-data app-install-data-partner apparmor
  appmenu-gtk appmenu-gtk3 appmenu-qt apport-symptoms apt apt-transport-https
  apt-xapian-index aptdaemon-data aspell aspell-en at at-spi2-core
  avahi-autoipd avahi-daemon avahi-utils base-files base-passwd bash
  bash-completion bc bind9-host binfmt-support binutils bluez-alsa bluez-cups
  bluez-gstreamer bogofilter bogofilter-bdb bogofilter-common brasero
  brasero-cdrkit brasero-common bsdmainutils bsdutils build-essential
  busybox-initramfs busybox-static byobu bzip2 c2esp ca-certificates
  ca-certificates-java cabextract command-not-found-data compiz-plugins-main
  compiz-plugins-main-default compizconfig-backend-gconf console-setup
  consolekit coreutils cpio cpp-4.4 cpp-4.5 cpuburn crda cron cryptsetup
  cryptsetup-bin cups cups-bsd cups-client cups-common cups-driver-gutenprint
  cups-pk-helper cups-ppdc dash dbus-x11 dc debconf debconf-i18n debianutils
  deja-dup desktop-base desktop-file-utils dictionaries-common diffutils dkms
  dmidecode dmraid dmsetup dnsmasq-base dnsutils doc-base dosfstools dpkg
  duplicity dvd+rw-tools e2fslibs e2fsprogs ecryptfs-utils ed eject enchant
  esound-common espeak espeak-data evtest fakeroot fancontrol fglrx
  fglrx-amdcccle file file-roller findutils firefox firefox-gnome-support
  firefox-locale-en folks-common fontconfig fontconfig-config fonts-cantarell
  fonts-droid fonts-horai-umefont fonts-kacst fonts-kacst-one fonts-liberation
  fonts-nanum fonts-opensymbol fonts-thai-tlwg fonts-tlwg-garuda
  fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi
  fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter
  fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree
  fonts-unfonts-core foo2zjs foomatic-db-engine foomatic-filters ftp fuse
  fuse-utils gamin gbrainy gcalctool gcc-4.4 gcc-4.4-base gcc-4.5 gcc-4.5-base
  gconf-defaults-service gconf-service gconf-service-backend gconf2
  gconf2-common gdb gdebi gdebi-core gedit gedit-common gedit-plugins
  genisoimage geoclue geoclue-ubuntu-geoip geoip-database get-iplayer
  ghostscript-cups ginn gir1.2-accountsservice-1.0 gir1.2-appindicator3-0.1
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-dee-1.0 gir1.2-folks-0.6 gir1.2-freedesktop
  gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0
  gir1.2-gee-1.0 gir1.2-glib-2.0 gir1.2-gmenu-3.0 gir1.2-gnomekeyring-1.0
  gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 gir1.2-gtk-2.0
  gir1.2-gtksource-3.0 gir1.2-gucharmap-2.90 gir1.2-gudev-1.0
  gir1.2-indicate-0.7 gir1.2-javascriptcoregtk-3.0 gir1.2-json-1.0
  gir1.2-launchpad-integration-3.0 gir1.2-networkmanager-1.0 gir1.2-notify-0.7
  gir1.2-panelapplet-4.0 gir1.2-pango-1.0 gir1.2-polkit-1.0 gir1.2-soup-2.4
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-totem-plparser-1.0 gir1.2-ubuntuoneui-3.0 gir1.2-upowerglib-1.0
  gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-xkl-1.0 git git-man
  gksu glib-networking glib-networking-common glib-networking-services gnome
  gnome-accessibility-themes gnome-backgrounds gnome-core gnome-desktop-data
  gnome-dictionary gnome-games-extra-data gnome-icon-theme
  gnome-icon-theme-extras gnome-icon-theme-full gnome-icon-theme-symbolic
  gnome-media gnome-menus gnome-power-manager gnome-screenshot
  gnome-search-tool gnome-session-canberra gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-user-guide gnuchess gnuchess-book gnupg gpgv grep
  groff-base growisofs gsettings-desktop-schemas gstreamer0.10-alsa
  gstreamer0.10-ffmpeg gstreamer0.10-gconf gstreamer0.10-gnonlin
  gstreamer0.10-nice gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf gtk3-engines-unico gucharmap
  guile-1.8-libs gwyddion gwyddion-common gzip hdparm hostname hpijs hplip
  hplip-cups hplip-data hplip-gui humanity-icon-theme hwdata hyphen-en-us ibus
  ibus-gtk ibus-gtk3 ibus-pinyin ibus-pinyin-db-android
  ibus-pinyin-db-open-phrase ibus-table icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icedtea-7-jre-jamvm icedtea-netx icedtea-netx-common
  icoutils ifupdown im-switch imagemagick-common indicator-applet-complete
  indicator-application indicator-multiload indicator-power indicator-printers
  indicator-sound info initramfs-tools initramfs-tools-bin initscripts
  inputattach insserv install-info intel-gpu-tools iproute iptables
  iputils-arping iputils-ping iputils-tracepath isc-dhcp-client
  isc-dhcp-common iso-codes iw java-common jockey-common jockey-gtk joystick
  kbd kerneloops-daemon keyboard-configuration keyutils klibc-utils kpartx
  kpartx-boot krb5-locales landscape-client-ui-install language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  launchpad-integration less lftp libaa1 libaacs0 libaccountsservice0 libacl1
  libalgorithm-diff-xs-perl libao-common libao4 libapparmor-perl libapparmor1
  libappindicator0.1-cil libappindicator1 libappindicator3-1 libapr1
  libaprutil1 libapt-pkg4.12 libarchive12 libart-2.0-2 libart2.0-cil
  libasn1-8-heimdal libasound2 libasound2-plugins libaspell15 libasyncns0
  libatasmart4 libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0
  libatk1.0-data libatkmm-1.6-1 libatm1 libatspi2.0-0 libattr1 libaudio2
  libaudiofile1 libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-core7 libavahi-glib1 libavahi-gobject0 libavahi-ui-gtk3-0
  libavahi-ui0 libavc1394-0 libavcodec53 libavformat53 libavutil51 libbind9-80
  libblkid1 libbluetooth3 libbluray1 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libbrasero-media3-1 libbrlapi0.5 libbsd0
  libburn4 libbz2-1.0 libc-bin libc-dev-bin libc6 libc6-dev libcaca0
  libcairo-gobject2 libcairo-perl libcairo2 libcairomm-1.0-1
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcap-ng0 libcap2
  libcap2-bin libcaribou-common libcaribou0 libcdaudio1 libcdio-cdda1
  libcdio-paranoia1 libcdio13 libcdparanoia0 libcdt4 libck-connector0
  libclass-c3-perl libclass-c3-xs-perl libclass-method-modifiers-perl
  libclutter-1.0-0 libclutter-1.0-common libclutter-gst-1.0-0
  libclutter-gtk-1.0-0 libcluttergesture-0.0.2-0 libcogl-common libcogl-pango0
  libcogl9 libcolord1 libcomerr2 libcroco3 libcryptsetup4 libcrystalhd3
  libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3
  libcurl3-gnutls libcurl3-nss libdaemon0 libdatetime-format-iso8601-perl
  libdatetime-perl libdatetime-timezone-perl libdatrie1 libdb5.1 libdbus-1-3
  libdbus-glib-1-2 libdbus-glib1.0-cil libdbus1.0-cil libdbusmenu-glib4
  libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdbusmenu-qt2 libdc1394-22
  libdee-1.0-4 libdevmapper-event1.02.1 libdevmapper1.02.1 libdirac-encoder0
  libdirectfb-1.2-9 libdiscid0 libdjvulibre-text libdjvulibre21
  libdmapsharing-3.0-2 libdmraid1.0.0.rc16 libdns81 libdotconf1.0
  libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libdv4 libdvdnav4
  libdvdread4 libecryptfs0 libedit2 libelf1 libelfg0 libenca0 libenchant1c2a
  libencode-locale-perl libept1.4.12 libesd0 libespeak1 libevent-2.0-5
  libexempi3 libexif12 libexpat1 libfaad2 libfarstream-0.1-0 libffi6
  libfftw3-3 libfile-listing-perl libfile-mimeinfo-perl libflac8 libflite1
  libfolks-telepathy25 libfolks25 libfontconfig1 libfontenc1 libframe6
  libfreerdp-plugins-standard libfreerdp1 libfreetype6 libfribidi0 libfs6
  libfuse2 libgadu3 libgail-common libgail18 libgamin0 libgc1c2 libgconf-2-4
  libgconf2-4 libgconf2.0-cil libgcr-3-common libgcrypt11 libgd2-xpm
  libgdata-common libgdbm3 libgdict-1.0-6 libgdict-common libgee2 libgeis1
  libgeoclue0 libgeoip1 libgif4 libgirepository-1.0-1 libgkeyfile1.0-cil
  libgksu2-0 libglade2-0 libglade2.0-cil libglib-perl libglib2.0-0
  libglib2.0-bin libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a
  libglu1-mesa libgmime-2.6-0 libgmime2.6-cil libgmp10 libgnome-desktop-2-17
  libgnome-keyring-common libgnome-keyring0 libgnome-media-profiles-3.0-0
  libgnome-menu-3-0 libgnome-menu2 libgnome-vfs2.0-cil libgnome2-0
  libgnome2-bin libgnome2-common libgnome2.24-cil libgnomecanvas2-0
  libgnomecanvas2-common libgnomekbd-common libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgnutls-openssl27
  libgnutls26 libgoocanvas-common libgoocanvas3 libgpg-error0 libgpgme11
  libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgpm2 libgrail5 libgraph4
  libgrip0 libgsl0ldbl libgsm1 libgssapi-krb5-2 libgssapi3-heimdal
  libgssdp-1.0-3 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtk-sharp-beans-cil libgtk-vnc-1.0-0 libgtk-vnc-2.0-0 libgtk2-perl
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkmm-2.4-1c2a
  libgtksourceview-3.0-0 libgtksourceview-3.0-common libgtkspell-3-0
  libgtkspell0 libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgudev-1.0-0
  libgudev1.0-cil libgupnp-1.0-4 libgupnp-igd-1.0-4 libgutenprint2 libgvc5
  libgvnc-1.0-0 libgweather-common libgwyddion2-0 libhcrypto4-heimdal
  libheimbase1-heimdal libheimntlm0-heimdal libhpmud0 libhtml-form-perl
  libhtml-parser-perl libhtml-tree-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhunspell-1.3-0 libhx509-5-heimdal libhyphen0
  libibus-1.0-0 libical0 libice6 libicu48 libid3-3.8.3c2a libid3tag0
  libidl-common libidl0 libidn11 libido-0.1-0 libido3-0.1-0 libiec61883-0
  libieee1284-3 libijs-0.35 libilmbase6 libindicate-gtk3 libindicate5
  libindicator3-7 libindicator7 libio-socket-ssl-perl libiptcdata0 libisc83
  libisccc80 libisccfg82 libiso9660-8 libisofs6 libiw30 libjack-jackd2-0
  libjasper1 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  libjbig2dec0 libjpeg-turbo8 libjpeg62 libjs-jquery libjson-glib-1.0-0
  libjson0 libjte1 libk5crypto3 libkeyutils1 libklibc libkrb5-26-heimdal
  libkrb5-3 libkrb5support0 liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblcms1 liblcms2-2 libldap-2.4-2
  liblightdm-gobject-1-0 liblircclient0 liblist-moreutils-perl libllvm3.0
  liblocale-gettext-perl liblockfile-bin liblockfile1 liblouis-data liblouis2
  liblqr-1-0 libltdl7 liblua5.1-0 libluajit-5.1-2 libluajit-5.1-common
  liblvm2app2.2 liblwp-mediatypes-perl liblwp-protocol-https-perl liblwres80
  liblzma5 libmagic1 libmailtools-perl libmatroska5 libmeanwhile1 libmhash2
  libminiupnpc8 libmission-control-plugins0 libmms0 libmng1 libmodplug1
  libmodule-runtime-perl libmono-cairo2.0-cil libmono-cairo4.0-cil
  libmono-corlib2.0-cil libmono-corlib4.0-cil libmono-csharp4.0-cil
  libmono-i18n-west2.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-management2.0-cil libmono-management4.0-cil libmono-posix2.0-cil
  libmono-posix4.0-cil libmono-security2.0-cil libmono-security4.0-cil
  libmono-sharpzip2.84-cil libmono-sharpzip4.84-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system2.0-cil libmono-system4.0-cil
  libmono-zeroconf1.0-cil libmount1 libmouse-perl libmp3lame0 libmpc2
  libmpeg2-4 libmpfr4 libmpg123-0 libmtdev1 libmtp-common libmtp-runtime
  libmtp9 libmysqlclient18 libmythes-1.2-0 libnautilus-extension1a libncurses5
  libncursesw5 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls
  libnet-http-perl libnet-ssleay-perl libnetfilter-conntrack3 libnettle4
  libnewt0.52 libnfnetlink0 libnice10 libnih-dbus1 libnih1 libnl-3-200
  libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4
  libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify0.4-cil
  libnotify4 libnspr4 libnspr4-0d libnss-mdns libnss3 libnss3-1d liboauth0
  libodbc1 libofa0 libogg0 libopenal-data libopenal1 libopencc1
  libopencore-amrnb0 libopencore-amrwb0 libopenexr6 libopenobex1 liborc-0.4-0
  libp11-kit0 libpackage-deprecationmanager-perl libpackage-stash-xs-perl
  libpam-cap libpam-ck-connector libpam-gnome-keyring libpam-modules
  libpam-modules-bin libpam-runtime libpam0g libpanel-applet-4-0 libpango-perl
  libpango1.0-0 libpangomm-1.4-1 libpaper-utils libpaper1
  libparams-classify-perl libparams-util-perl libparted0debian1 libpathplan4
  libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1 libpeas-common
  libperl5.14 libphonon4 libpipeline1 libpixman-1-0 libplist1 libpng12-0
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpopt0
  libportaudio2 libpostproc52 libprotobuf7 libprotoc7 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpst4 libpth20
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libpython2.7 libqtassistantclient4 libqtwebkit4 libquvi-scripts libquvi7
  libraptor1 librarian0 librasqal3 libraw1394-11 libraw5 librdf0 libreadline6
  libreoffice-emailmerge libreoffice-style-human libresid-builder0c2a
  librest-0.7-0 libroken18-heimdal librpc-xml-perl librsvg2-2 librsvg2-common
  librsync1 librtmp0 libsamplerate0 libsane-hpaio libsasl2-2 libsasl2-modules
  libschroedinger-1.0-0 libsctp1 libsdl1.2debian libselinux1 libsensors4
  libsepol1 libsgutils2-2 libshout3 libsidplay2 libsigc++-2.0-0c2a libslang2
  libslp1 libslv2-9 libsm6 libsmbclient libsndfile1 libsnmp-base libsnmp15
  libsocket6-perl libsonic0 libsoundtouch0 libsoup-gnome2.4-1 libsoup2.4-1
  libspectre1 libspeechd2 libspeex1 libspeexdsp1 libsqlite3-0 libss2 libssh-4
  libssl1.0.0 libstartup-notification0 libsub-install-perl libswscale2
  libsyncdaemon-1.0-1 libsysfs2 libt1-5 libtag1-vanilla libtag1c2a libtalloc2
  libtar0 libtasn1-3 libtdb1 libtelepathy-farstream2 libtelepathy-glib0
  libtelepathy-logger2 libterm-readkey-perl libtext-charwidth-perl
  libtext-iconv-perl libthai-data libthai0 libtheora0 libtidy-0.99-0
  libtimezonemap1 libtinfo5 libtotem-plparser17 libts-0.0-0
  libubuntuoneui-3.0-1 libudev0 libunicode-string-perl libunique-1.0-0
  libunique-3.0-0 libunistring0 libunity-2d-private0 libunity-misc4
  libupower-glib1 liburi-perl libusb-0.1-4 libusb-1.0-0 libutempter0
  libuuid-perl libuuid1 libv4l-0 libv4lconvert0 libva-x11-1 libva1 libvcdinfo0
  libvisual-0.4-0 libvisual-0.4-plugins libvlc5 libvlccore5 libvncserver0
  libvo-aacenc0 libvo-amrwbenc0 libvorbis0a libvorbisenc2 libvorbisfile3
  libvpx1 libvte-2.90-9 libvte-2.90-common libvte-common libvte9
  libwacom-common libwacom2 libwavpack1 libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwildmidi-config libwildmidi1 libwind0-heimdal libwmf-bin libwmf0.2-7
  libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwnck-common libwnck22
  libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwrap0 libwww-perl libwxbase2.8-0
  libx11-6 libx11-data libx11-xcb1 libx86-1 libxapian22 libxau6 libxaw7
  libxcb-composite0 libxcb-dri2-0 libxcb-glx0 libxcb-keysyms1 libxcb-randr0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-util0 libxcb-xv0 libxcb1
  libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3
  libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 libxklavier16
  libxml-libxml-perl libxml-parser-perl libxml-sax-perl libxml-simple-perl
  libxml2 libxml2-dev libxml2-utils libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2
  libxrender1 libxres1 libxslt1.1 libxss1 libxt6 libxtst6 libxv1 libxvidcore4
  libxvmc1 libxxf86dga1 libxxf86vm1 libyaml-tiny-perl libyelp0 libzbar0
  libzephyr4 libzvbi-common libzvbi0 light-themes lightdm linux-firmware
  linux-libc-dev linux-sound-base lksctp-tools lm-sensors lockfile-progs login
  logrotate lsb-base lshw lsof ltrace make makedev man-db manpages
  manpages-dev media-player-info memtest86+ metacity-common mime-support
  min12xxw mlocate mobile-broadband-provider-info modemmanager
  module-init-tools mono-2.0-gac mono-4.0-gac mono-csharp-shell mono-gac
  mono-gmcs mono-runtime mount mountall mousetweaks mscompress mtools mtr-tiny
  multiarch-support mysql-common nano nautilus-share ncurses-base ncurses-bin
  net-tools netbase netcat-openbsd network-manager network-manager-pptp
  network-manager-pptp-gnome notification-daemon notify-osd ntfs-3g ntpdate
  nux-tools obex-data-server obexd-client odbcinst odbcinst1debian2 oneconf
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openjdk-7-jre
  openjdk-7-jre-headless openjdk-7-jre-lib openssh-client openssl os-prober
  parted passwd patch pciutils pcmciautils pdfmod perl perl-base perl-modules
  phonon phonon-backend-gstreamer pidgin pidgin-data pidgin-libnotify pitivi
  pkg-config plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pnm2ppa
  policykit-1 policykit-1-gnome policykit-desktop-privileges powermgmt-base
  ppp pptp-linux printer-driver-gutenprint printer-driver-hpcups
  printer-driver-hpijs printer-driver-min12xxw printer-driver-pnm2ppa
  protobuf-compiler psmisc ptouch-driver pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils pxljr python python-appindicator python-apport
  python-apt-common python-avahi python-cairo python-crypto python-cups
  python-cupshelpers python-dateutil python-dbus python-dbus-dev
  python-debtagshw python-defer python-dirspec python-dnspython
  python-egenix-mxdatetime python-egenix-mxtools python-farstream
  python-feedparser python-gconf python-gdbm python-gi python-gi-cairo
  python-glade2 python-gmenu python-gnome2 python-gnomekeyring python-gobject
  python-gobject-2 python-gst0.10 python-gtk2 python-gtkspell python-httplib2
  python-ibus python-imaging python-indicate python-keyring
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient
  python-libproxy python-libxml2 python-lxml python-mako python-markupsafe
  python-minimal python-newt python-notify python-numpy python-openssl
  python-pam python-pexpect python-piston-mini-client python-pkg-resources
  python-problem-report python-protobuf python-pyatspi2 python-pycurl
  python-pygoocanvas python-pyinotify python-pyorbit python-qt4
  python-qt4-dbus python-rdflib python-renderpm python-reportlab
  python-reportlab-accel python-serial python-simplejson python-sip
  python-smbc python-software-properties python-support python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web
  python-ubuntuone-client python-ubuntuone-storageprotocol python-uniconvertor
  python-virtkey python-vte python-webkit python-wnck python-wxgtk2.8
  python-wxversion python-xapian python-xdg python-xkit python-zeitgeist
  python-zope.interface python2.7 python2.7-minimal qt-at-spi radeontool
  rarian-compat rdesktop readline-common remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc resolvconf rfkill rhythmbox-ubuntuone
  rsync rsyslog rtkit rtmpdump samba-common-bin sane-utils screen sed
  sensible-utils sessioninstaller sgml-base sgml-data shared-mime-info
  simple-scan sni-qt speech-dispatcher splix ssh-askpass-gnome ssl-cert
  stellarium stellarium-data strace sudo syslinux syslinux-common
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev sysv-rc sysvinit-utils tcl8.4 tcl8.5 tcpd tcpdump
  telepathy-gabble telepathy-haze telepathy-idle telepathy-logger
  telepathy-mission-control-5 telepathy-salut telnet time tk8.4 tk8.5 tmux
  tomboy toshset tsconf ttf-droid ttf-kacst-one ttf-liberation ttf-thai-tlwg
  ttf-ubuntu-font-family ttf-umefont ttf-unfonts-core tzdata tzdata-java
  ubufox ubuntu-artwork ubuntu-docs ubuntu-keyring ubuntu-mono ubuntu-standard
  ubuntu-system-service ubuntu-wallpapers-precise ubuntuone-client
  ubuntuone-client-gnome ubuntuone-couch ucf udev udisks unity-2d
  unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
  unity-asset-pool unixodbc uno-libs3 unrar unrar-free unzip update-inetd
  upstart ure ureadahead usb-creator-common usb-creator-gtk usb-modeswitch
  usb-modeswitch-data usbutils util-linux uuid-runtime vim-common vim-tiny
  vino vlc-data w3m wget whiptail whois wine1.3 winetricks wireless-tools
  wodim wpasupplicant x11-apps x11-common x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xauth xdg-user-dirs
  xdg-user-dirs-gtk xfonts-mathml xfonts-utils xinit xinput xkb-data xml-core
  xorg xserver-common xserver-xorg xserver-xorg-input-all xsltproc xterm
  xul-ext-ubufox yelp yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub
  zenity zenity-common zip zlib1g
1406 upgraded, 0 newly installed, 0 to remove and 402 not upgraded.
Need to get 0 B/685 MB of archives.
After this operation, 45.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `fonts-kacst-one' missing, assuming package has no files currently installed.
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libgnome-keyring-common': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```I thought maybe the fonts-kacst-one package (or the package it belongs to) could be repaired so I tried

```

sudo apt-get --reinstall install fonts-kacst-one

```Which gives me the same error basically. 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  fonts-kacst-one
1 upgraded, 0 newly installed, 0 to remove and 1807 not upgraded.
Need to get 0 B/46.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 
dpkg: warning: files list file for package `fonts-kacst-one' missing, assuming package has no files currently installed.
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libgnome-keyring-common': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```Trying the same for libgnome-keyring-common gets an identical error message. That's about the extent of what I know or can think to do. I'd vastly appreciate any help that will get Kitt feeling better, she's confused. Hopefully this is a simple fix and I'm just too green to figure it out. Once again thank you for your time.

---

### Post by srekcahrai on 2013-02-03
Try changing Ubuntu Server mirror
[http://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main](http://askubuntu.com/questions/104695/how-do-i-change-mirrors-in-ubuntu-server-from-regional-to-main)

---

### Post by DesertFox001 on 2013-02-03
I changed from the U.S. server to the international one listed on the page, ran through 
```
 
sudo apt-get update

```and
```
 
sudo apt-get upgrade

```But got the same error message.
```

dpkg: warning: files list file for package `fonts-kacst-one' missing, assuming package has no files currently installed.
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libgnome-keyring-common': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by Bashing-om on 2013-02-03
DesertFox001; Hi !

Try oldfred's methology to clean up/fix/restore and update:
#houseclean
```
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
```#refresh
```
sudo apt-get update #resync package index
sudo apt-get upgrade
``` #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
```
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```All that does is update it again.[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by DesertFox001 on 2013-02-03
I tried the codes you recommended.
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean

```They all ran fine, next I ran 
```
 
sudo apt-get update
sudo apt-get upgrade

```The first command worked with no problems, the upgrade spit out the familiar
```
 
dpkg: warning: files list file for package `fonts-kacst-one' missing, assuming package has no files currently installed.
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libgnome-keyring-common': Is a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```Running the code 
```

sudo apt-get dist-upgrade

```Responded with the same error message, I won't bother re-posting it again for the sake of everyone reading. The two following codes ran fine but didn't really change anything and when I tried to update again after them the same error code came back. Thanks for the advice though, I hadn't tried those yet. :)

---

### Post by srekcahrai on 2013-02-04
Run this command in Terminal
```

wget https://launchpad.net/ubuntu/+archive/primary/+files/fonts-kacst-one_5.0%2Bsvn11846.orig.tar.xz && tar -xf fonts-kacst-one_5.0+svn11846.orig.tar.xz && make -f kacstone-5.0~svn11846/Makefile

```

---

### Post by DesertFox001 on 2013-02-05
After running the code
```

wget https://launchpad.net/ubuntu/+archive/primary/+files/fonts-kacst-one_5.0%2Bsvn11846.orig.tar.xz && tar -xf fonts-kacst-one_5.0+svn11846.orig.tar.xz && make -f kacstone-5.0~svn11846/Makefile

```this came back
```

--2013-02-04 23:09:48--  https://launchpad.net/ubuntu/+archive/primary/+files/fonts-kacst-one_5.0%2Bsvn11846.orig.tar.xz
Resolving launchpad.net (launchpad.net)... 91.189.89.223, 91.189.89.222
Connecting to launchpad.net (launchpad.net)|91.189.89.223|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://launchpadlibrarian.net/84968089/fonts-kacst-one_5.0%2Bsvn11846.orig.tar.xz [following]
--2013-02-04 23:09:49--  https://launchpadlibrarian.net/84968089/fonts-kacst-one_5.0%2Bsvn11846.orig.tar.xz
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 91868 (90K) [application/octet-stream]
Saving to: `fonts-kacst-one_5.0+svn11846.orig.tar.xz.1'

100%[======================================>] 91,868      20.5K/s   in 4.4s    

2013-02-04 23:09:54 (20.5 KB/s) - `fonts-kacst-one_5.0+svn11846.orig.tar.xz.1' saved [91868/91868]

make: *** No rule to make target `KacstOne.ttf', needed by `ttf'.  Stop.

```However the same error code as before is given when trying to update.

---

### Post by sandyd on 2013-02-05
I think some of your packagelists are corrupt.

try
```

sudo mv /var/lib/dpkg/info/libgnome-keyring-common.list /var/lib/dpkg/info/libgnome-keyring-common.list.bak
sudo apt-get install --reinstall --download-only libgnome-keyring-common

```
Run
```

ls /var/cache/apt/archive/libgnome-keyring-common* | sort -r

```
copy the first line of output, we will refer to that as *debpackage*

```

sudo su
```
```

dpkg -c /var/cache/apt/archives/*debpackage* | awk \
{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}' \
> /var/lib/dpkg/info/libgnome-keyring-common.list
```

from [https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename](https://wiki.ubuntu.com/DebuggingInstallationIssues#files_list_file_missing_final_newline_.2BAC8_contains_empty_filename)

---

### Post by DesertFox001 on 2013-02-05
Okay, finally back from work. Booted Kitt back up and started following code. 
```
 
sudo mv /var/lib/dpkg/info/libgnome-keyring-common.list /var/lib/dpkg/info/libgnome-keyring-common.list.bak

```Ran just fine, moved onto 
```

sudo apt-get install --reinstall --download-only libgnome-keyring-common

```and got the result
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gir1.2-gnomekeyring-1.0 libgnome-keyring0
The following packages will be upgraded:
  gir1.2-gnomekeyring-1.0 libgnome-keyring-common libgnome-keyring0
3 upgraded, 0 newly installed, 0 to remove and 1805 not upgraded.
Need to get 0 B/75.8 kB of archives.
After this operation, 23.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Download complete and in download only mode

```Next I run 
```

ls libgnome-keyring-common* | sort -r

```and get 
```

ls: cannot access libgnome-keyring-common*: No such file or directory

```So what should I do next? Or did I enter it in wrong? I want to make sure I'm doing everything right before I start giving root commands. I'm still pretty new to all of this. Also thank you all for the help, I'd never be able to fix this on my own.

---

### Post by sandyd on 2013-02-06
fixed typo

---

### Post by DesertFox001 on 2013-02-07
Alright, checked the code out for a bit and found that my folder is archives, not archive. Changed that, everything seems to be running and I'll post again in the morning whether the update applied successfully or not. 
Code used
```

ls /var/cache/apt/archives/libgnome-keyring-common* | sort -r

```Responded with
```

libgnome-keyring-common_3.6.0-0ubuntu1_all.deb

```Just put that into the next code and changed archive to archives, entered as followed
```
sudo su

dpkg -c /var/cache/apt/archives//var/cache/apt/archives/libgnome-keyring-common_3.6.0-0ubuntu1_all.deb | awk \
{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}' \
> /var/lib/dpkg/info/libgnome-keyring-common.list

```Everything appears to be working, another 2-5 hours until it finishes or crashes, I'll check in the morning and update the status then. Thanks for the help, hoping it works and Kitt gets back to being fully functional.

---

### Post by DesertFox001 on 2013-02-07
Alright, new error this time. 
```

dpkg: warning: files list file for package `fonts-kacst-one' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libv4lconvert0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
It's similar to the previous error code, I should be able to fix it in the same way as libgnome-keyring-common was correct? I'll try and do so when I get back from work.  What about the fonts-kacst-one error though? Will it fix itself if the other errors stop?
Thanks for your time, be back in about twelve hours.

---

### Post by sandyd on 2013-02-07
> **DesertFox001 said:**
> Alright, new error this time. 
```

dpkg: warning: files list file for package `fonts-kacst-one' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `libv4lconvert0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
It's similar to the previous error code, I should be able to fix it in the same way as libgnome-keyring-common was correct? I'll try and do so when I get back from work.  What about the fonts-kacst-one error though? Will it fix itself if the other errors stop?
Thanks for your time, be back in about twelve hours.

Just replace anywhere you see libgnome-keyring-common in the script with fonts-kacst-one and libv4lconvert0. ;)

---

### Post by DesertFox001 on 2013-02-07
I appear to be doing something wrong between last night and tonight. I can enter all of the code fine and until 
```

dpkg -c /var/cache/apt/archives/fonts-kacst-one_5.0+svn11846-6_all.deb | awk \
{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}' \
> /var/lib/dpkg/info/fonts-kacst-one.list

```
I enter 
```

dpkg -c /var/cache/apt/archives/fonts-kacst-one_5.0+svn11846-6_all.deb | awk \

```
and it works fine, waiting patiently with >
But as soon as I enter the next line 
```

{if ($6 == "./") { print "/."; } \

```
I get the error
```
 
bash: syntax error near unexpected token `('

```
I don't know what I'm doing wrong now, advice would be welcome. Thanks for all the help so far.

---

### Post by DesertFox001 on 2013-02-12
No one knows what I'm doing wrong? It acts like I changed the interface somehow, it accepted the command before without hesitation and now it's telling me the exact same code that worked before is not okay. Did I change the environment somehow? I kept pressing ctrl and V when trying to paste (I'm stuck on that particular keyboard shortcut), might that have messed something up? Can I restore it to it's default if I did? I've already rebooted the system and that helped nothing. I'm at a loss right now and have been unable to figure it out any further.

I think I went from a packages problem to a bash command problem, should I close this thread as fixed (we did technically fix the first package list I was having problems with) and start a new one about the commands not being recognized?

---

### Post by gabcr on 2013-05-06
Hi,

exactly the same happened to me.

dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-libc-dev:i386' missing; assuming package has no files currently installed
dpkg: fatal error irrecuperable, aborting:
Reading files list file for package «linux-headers-generic-pae»: Input/output error

Did you find a solution for your problem? Thank you very much in advance =)

---

### Post by michel-b on 2013-11-24
The code to extract the list from the deb package has a mistake, use:

```
dpkg -c path/to/dep/package.deb | awk \
'{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}'

```


Works fine for me, thanks sandyd ;)

---

### Post by michel-b on 2013-11-24
For me, it was autoremove that doesn't work, i did a small script to auto fix list file and retry autoremove until all list are fixed:

```

#!/bin/bash


function ask_user {
	echo $1 ; read res
	if [ "$res" != "y" ]
	then
		echo "abort."
		exit 1
	fi
}


function fix_list {
	package=$1


	# backup corrupted list file
	list=`ls /var/lib/dpkg/info/${package}*.list | sort -r | head -n 1`


	ask_user "fix ${list} [y/n] ?"


	mv ${list} ${list}.old


	# unlock dpkg 
	dpkg --configure -a


	# download deb
	apt-get install --reinstall --download-only $package


	deb=`ls  /var/cache/apt/archives/${package}*.deb | sort -r | head -n 1`


	if [ ${#deb} -eq 0 ]
	then
		echo "error, can't get deb package"
	else
		dpkg -c $deb | awk \
		'{if ($6 == "./") { echo "/."; } \
		else if (substr($6, length($6), 1) == "/") \
		{echo substr($6, 2, length($6) - 2); } \
		else { echo substr($6, 2, length($6) - 1);}}' > $list


		echo "list extracted from $deb into $list"
	fi
}


function autoremove {
	# unlock dpkg 
	sudo dpkg --configure -a
	
	echo "try apt-get autoremove -y"


	out=`sudo apt-get autoremove -y`
	if [ $? -ne 0 ]
	then
		regex="package '([^:']*).* is missing"
		[[ $out =~ $regex ]]
		package="${BASH_REMATCH[1]}"	
		if [ ${#package} -ne 0 ]
		then
			echo "error with package '"$package"'"
			fix_list $package
			autoremove
		else
			echo "error on unknown package..."
			echo "sorry, you have to fix it manually"
			echo $out
		fi	
	fi
}


# run the first autoremove
autoremove

```

Note:
 - you may have to change the command according to your needs but I found it was really boring to fix list manually (more than 20 to fix for me...)
- the thread should be marked as "Solved" I think

---

### Post by michel-b on 2013-11-24
This link (quiet old) can be useful too: [https://lists.ubuntu.com/archives/ubuntu-server/2007-August/000662.html](https://lists.ubuntu.com/archives/ubuntu-server/2007-August/000662.html)

---

