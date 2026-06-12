---
title: "Update Error E: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by ironmaiden943 on 2012-08-20
Hi,
i'm trying to upgrade my computer and when i run apt-get upgrade I get the following error message:
```
chiara@chiara-Inspiron-1420:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  aisleriot akonadi-backend-mysql akonadi-server anjuta-common apt
  apt-transport-https apt-utils at-spi banshee banshee-extension-soundmenu
  baobab bind9-host brasero brasero-cdrkit brasero-common brltty brltty-x11
  byobu c2esp cheese cheese-common compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default compiz-plugins-main
  compiz-plugins-main-default compizconfig-backend-gconf couchdb-bin cups
  cups-driver-gutenprint dconf-gsettings-backend deja-dup dnsmasq-base
  dnsutils dolphin ecryptfs-utils empathy empathy-common eog espeak
  espeak-data evince evince-common evolution evolution-common
  evolution-couchdb evolution-couchdb-backend evolution-data-server
  evolution-data-server-common evolution-exchange evolution-indicator
  evolution-plugins evolution-webcal exiv2 file-roller foo2zjs
  foomatic-db-compressed-ppds fuse-utils gconf-defaults-service gconf-editor
  gconf2 gconf2-common gdm gedit gedit-common geoclue gir1.2-appindicator3-0.1
  gir1.2-gconf-2.0 gir1.2-gdkpixbuf-2.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-rb-3.0 gir1.2-soup-2.4
  gir1.2-totem-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 glib-networking
  gnome-bluetooth gnome-control-center gnome-control-center-data
  gnome-desktop-data gnome-desktop3-data gnome-dictionary gnome-disk-utility
  gnome-keyring gnome-media gnome-online-accounts gnome-orca
  gnome-power-manager gnome-search-tool gnome-session gnome-session-bin
  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-share gnomine
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
  gtkpod gtkpod-data gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber
  gwibber-service hpijs hplip hplip-cups hplip-data ibus icedtea-netx
  icedtea-plugin icedtea6-plugin imagemagick indicator-application
  indicator-appmenu indicator-datetime indicator-messages indicator-power
  indicator-session indicator-sound kamoso katepart kde-baseapps-bin
  kde-runtime kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime
  kdepimlibs-kio-plugins kdoctools kipi-plugins kipi-plugins-common konqueror
  konqueror-nsplugins libakonadi-contact4 libakonadi-kcal4 libakonadi-kde4
  libakonadi-kmime4 libakonadiprotocolinternals1 libalgorithm-diff-xs-perl
  libanjuta-3-0 libapparmor-perl libappindicator1 libappindicator3-1
  libatk-adaptor libavcodec53 libavformat53 libavutil51 libbonoboui2-0
  libbrasero-media3-1 libcairo-perl libcamel-1.2-29 libcanberra-gtk3-module
  libcap2-bin libclutter-1.0-0 libclutter-gst-1.0-0 libclutter-gtk-1.0-0
  libcompizconfig0 libcups2 libcurl3 libcurl3-gnutls libdecoration0
  libebackend-1.2-1 libedata-book-1.2-11 libedata-cal-1.2-13
  libedataserverui-3.0-1 libenchant1c2a libespeak1 libevince3-3 libevolution
  libfolks-telepathy25 libfolks25 libfuse2 libgail-3-0 libgconf2-4 libgcr-3-1
  libgdata13 libgdict-1.0-6 libgdk-pixbuf2.0-0 libgdl-3-common libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libglib-perl libglib2.0-cil
  libgnome-desktop-3-2 libgnome-keyring0 libgnome2-canvas-perl libgnome2-perl
  libgnome2-vfs-perl libgnomeui-0 libgoa-1.0-0 libgssapi-krb5-2 libgtk-3-0
  libgtk-3-bin libgtk2-perl libgtk2.0-cil libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtkpod1
  libgtksourceview-3.0-0 libgtksourceview-3.0-common libgucharmap-2-90-7
  libgweather-3-0 libgwibber-gtk2 libgwibber2 libhpmud0 libhtml-parser-perl
  libidl0 libindicate5 libio-socket-ssl-perl libjpeg8 libk5crypto3 libkabc4
  libkatepartinterfaces4 libkcal4 libkcalcore4 libkcalutils4 libkcmutils4
  libkdcraw20 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkexiv2-10 libkfile4 libkgeomap1 libkhtml5
  libkidletime4 libkimap4 libkio5 libkipi8 libkjsapi4 libkjsembed4 libkldap4
  libkmbox4 libkmediaplayer4 libkmime4 libknewstuff3-4 libknotifyconfig4
  libkntlm4 libkonq-common libkonq5abi1 libkonqsidebarplugin4a libkparts4
  libkpimidentities4 libkpimtextedit4 libkpimutils4 libkpty4 libkrb5-3
  libkrb5support0 libkresources4 libkrosscore4 libksane0 libktexteditor4
  libldap-2.4-2 liblocale-gettext-perl liblockfile1 libmailtransport4
  libmicroblog4 libmission-control-plugins0 libmx-1.0-2 libnepomuk4
  libnepomukquery4a libnepomukutils4 libnet-dbus-perl libnet-ssleay-perl
  libnice10 libnm-gtk0 liboauth0 liboverlay-scrollbar3-0.2-0 libpango-perl
  libplasma3 libpostproc52 libpurple0 libqapt-runtime libqapt1 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtdee2 libqtgui4 libqtwebkit4
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-impress libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-math libreoffice-writer librpc-xml-perl
  libsane libsane-hpaio libsdl1.2debian libsmbclient libsnmp15 libsolid4
  libsoprano4 libsoup2.4-1 libssl1.0.0 libstreamanalyzer0 libstreams0
  libswscale2 libsyncdaemon-1.0-1 libterm-readkey-perl libtext-charwidth-perl
  libtext-iconv-perl libthreadweaver4 libtotem-plparser17 libunity-2d-private0
  libuuid-perl libv4l-0 libvcdinfo0 libvlc5 libvte-2.90-9 libvte-common
  libvte9 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwildmidi1 libxfixes3
  libxml-parser-perl libyelp0 linux-generic linux-headers-generic
  linux-image-generic marble-plugins metacity min12xxw mysql-common nautilus
  nautilus-data nautilus-sendto-empathy nautilus-share network-manager
  network-manager-gnome ntfs-3g ntrack-module-libnl-0 odbcinst1debian2
  openjdk-6-jre openssh-client openssl perl perl-base perl-modules
  plasma-scriptengine-javascript pnm2ppa poppler-utils ptouch-driver
  pulseaudio-module-gconf pulseaudio-utils pxljr python-appindicator
  python-apt python-dbus python-gnomekeyring python-gobject python-ibus
  python-indicate python-libproxy python-pycurl python-ubuntuone-client
  python-ubuntuone-control-panel python-uno python-vte qdbus qt-at-spi
  quadrapassel rastertosag-gdi rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins samba-common samba-common-bin seahorse sessioninstaller
  shotwell smbclient software-center soprano-daemon splix synaptic
  telepathy-indicator telepathy-mission-control-5 thunderbird
  thunderbird-globalmenu thunderbird-gnome-support tomboy totem totem-common
  totem-mozilla totem-plugins transmission-common transmission-gtk
  ttf-kacst-one ttf-khmeros-core ttf-lao ttf-liberation
  ttf-mscorefonts-installer ttf-opensymbol ttf-takao-pgothic ttf-thai-tlwg
  ttf-unfonts-core ubuntu-desktop ubuntu-minimal ubuntu-sso-client
  ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome
  ubuntuone-control-panel ubuntuone-control-panel-gtk udisks unity unity-2d
  unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread
  unity-common unity-greeter unity-lens-applications unity-lens-files
  unity-lens-music unity-scope-musicstores unity-services update-manager
  update-manager-core usb-creator-common usb-creator-gtk vino vlc vlc-data
  vlc-nox vlc-plugin-notify vlc-plugin-pulse wireless-crda wpasupplicant
  xdiagnose xorg xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo xz-utils yelp zeitgeist zeitgeist-core
The following packages will be upgraded:
  accountsservice acl acpi-support acpid adduser adium-theme-ubuntu alacarte
  alsa-base alsa-utils app-install-data app-install-data-partner apparmor
  apparmor-utils appmenu-gtk appmenu-gtk3 appmenu-qt apport apport-gtk
  apt-xapian-index aptdaemon aptdaemon-data apturl apturl-common aspell at
  at-spi2-core avahi-autoipd avahi-daemon avahi-utils b43-fwcutter bamfdaemon
  base-files base-passwd bash bash-completion binfmt-support binutils bluez
  bluez-alsa bluez-cups bluez-gstreamer bogofilter bogofilter-bdb
  bogofilter-common bsdmainutils bsdutils build-essential busybox-initramfs
  busybox-static bzip2 ca-certificates ca-certificates-java checkbox
  checkbox-gtk cli-common colord command-not-found command-not-found-data
  compiz-fusion-plugins-main compizconfig-settings-manager computer-janitor
  computer-janitor-gtk console-setup consolekit coreutils cpio cpp cpp-4.4
  cpp-4.5 cpp-4.6 cpu-checker cron cups-bsd cups-client cups-common cups-ppdc
  dash dbus dbus-x11 debconf debconf-i18n debianutils desktop-file-utils
  desktopcouch dhcp3-client dhcp3-common dictionaries-common diffutils dkms
  dmidecode dmsetup doc-base docbook-xml docbook-xsl dosfstools dpkg dpkg-dev
  duplicity e2fslibs e2fsprogs ed eject erlang-base erlang-crypto erlang-inets
  erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl example-content fakeroot fancontrol file
  findutils firefox firefox-branding firefox-globalmenu firefox-gnome-support
  firefox-locale-en firmware-b43-installer flashplugin-downloader
  flashplugin-installer fontconfig fontconfig-config foomatic-filters
  friendly-recovery g++ g++-4.6 gamin gbrainy gcalctool gcc gcc-4.4
  gcc-4.4-base gcc-4.5 gcc-4.5-base gcc-4.6 gcc-4.6-base gdb genisoimage
  geoip-database gettext-base ghostscript ghostscript-cups ghostscript-x
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-gmenu-3.0
  gir1.2-gstreamer-0.10 gir1.2-gtk-2.0 gir1.2-launchpad-integration-3.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-totem-plparser-1.0
  gir1.2-wnck-3.0 gksu gnome-accessibility-themes gnome-applets-data
  gnome-codec-install gnome-doc-utils gnome-font-viewer gnome-icon-theme
  gnome-icon-theme-symbolic gnome-menus gnome-nettool gnome-panel-data
  gnome-screensaver gnome-screenshot gnome-session-canberra gnome-system-log
  gnome-system-tools gnome-user-guide gnome-utils gnome-video-effects gnupg
  gpgv grep groff-base grub-common grub-gfxpayload-lists grub-pc grub-pc-bin
  grub2-common gs-cjk-resource gsettings-desktop-schemas gstreamer0.10-alsa
  gstreamer0.10-fluendo-mp3 gstreamer0.10-gconf gstreamer0.10-nice
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gtk3-engines-unico gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter gzip hdparm hicolor-icon-theme hunspell-en-us hwdata
  hyphen-en-us ibus-gtk ibus-gtk3 ibus-pinyin ibus-pinyin-db-android
  ibus-pinyin-db-open-phrase ibus-table icc-profiles-free icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icoutils ifupdown indicator-status-provider-mc5 info
  initramfs-tools initramfs-tools-bin initscripts inputattach insserv
  install-info intel-gpu-tools iproute iptables iputils-arping iputils-ping
  iputils-tracepath irqbalance isc-dhcp-client isc-dhcp-common iso-codes
  java-common jockey-common jockey-gtk kate-data kbd kde-baseapps-data
  kde-runtime-data kdebase-runtime kerneloops-daemon keyboard-configuration
  keyutils klibc-utils language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common language-selector-gnome launchpad-integration lftp
  liba52-0.7.4 libaa1 libaccess-bridge-java libaccess-bridge-java-jni
  libaccountsservice0 libacl1 libakonadi-kabc4 libao-common libao4
  libapparmor1 libappindicator0.1-cil libasound2 libasound2-plugins
  libaspell15 libass4 libatasmart4 libatk1.0-0 libatk1.0-data libatkmm-1.6-1
  libatm1 libatspi1.0-0 libatspi2.0-0 libattr1 libaudio2 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1
  libavahi-gobject0 libavahi-ui-gtk3-0 libavahi-ui0 libavc1394-0 libbamf0
  libbamf3-0 libblkid1 libbluetooth3 libbonobo2-0 libbonobo2-common
  libbonoboui2-common libboost-program-options1.46.1
  libboost-serialization1.46.1 libbrlapi0.5 libbsd0 libburn4 libbz2-1.0
  libc-bin libc-dev-bin libc6 libc6-dev libcaca0 libcairo-gobject2 libcairo2
  libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-pulse libcanberra0 libcap-ng0 libcap2 libcdaudio1 libcddb2
  libcdparanoia0 libcdt4 libck-connector0 libclass-isa-perl
  libclutter-1.0-common libclutter-imcontext-0.1-0 libcluttergesture-0.0.2-0
  libcogl-common libcolord1 libcomerr2 libcouchdb-glib-1.0-2 libcroco3
  libcrypt-passwdmd5-perl libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdatrie1 libdb4.8 libdb5.1 libdbus-1-3
  libdbus-glib-1-2 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4
  libdbusmenu-qt2 libdc1394-22 libdca0 libdconf-dbus-1-0 libdconf-qt0
  libdconf0 libdesktopcouch-glib-1.0-2 libdevmapper-event1.02.1
  libdevmapper1.02.1 libdirac-encoder0 libdirectfb-1.2-9 libdjvulibre-text
  libdjvulibre21 libdlrestrictions1 libdmapsharing-3.0-2 libdmtx0a
  libdpkg-perl libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libdv4
  libdvbpsi7 libdvdnav4 libdvdread4 libebml3 libecryptfs0 libedit2 libelf1
  libencode-locale-perl libevent-2.0-5 libexempi3 libexif12 libexpat1 libfaad2
  libffi6 libfftw3-3 libfile-desktopentry-perl libfile-listing-perl
  libfile-mimeinfo-perl libflac8 libflite1 libfontconfig1 libfreetype6
  libgadu3 libgail-common libgail18 libgamin0 libgc1c2 libgcc1 libgck-1-0
  libgcrypt11 libgd2-xpm libgdata-common libgdiplus libgdu-gtk0 libgdu0
  libgee2 libgeoclue0 libgeoip1 libgfortran3 libgif4 libgirepository-1.0-1
  libgksu2-0 libglade2-0 libglade2.0-cil libgladeui-1-11 libglib2.0-0
  libglib2.0-bin libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa libgmp10
  libgnome-bluetooth8 libgnome-control-center1 libgnome-desktop-2-17
  libgnome-media-profiles-3.0-0 libgnome-menu-3-0 libgnome-menu2 libgnome2-0
  libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common
  libgnomekbd7 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgnutls26 libgomp1 libgpg-error0 libgpgme11
  libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgpm2 libgpod-common
  libgpod4 libgraph4 libgraphite3 libgrip0 libgs9 libgs9-common libgsl0ldbl
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-3-common
  libgtk-vnc-1.0-0 libgtk-vnc-2.0-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19
  libgtkmm-2.4-1c2a libgtkspell0 libgtop2-7 libgtop2-common libgudev-1.0-0
  libgutenprint2 libgvc5 libgvnc-1.0-0 libgweather-common libhyphen0
  libibus-1.0-0 libical0 libice6 libid3-3.8.3c2a libidn11 libido-0.1-0
  libido3-0.1-0 libiec61883-0 libieee1284-3 libijs-0.35 libimobiledevice2
  libindicate-gtk3 libindicator-messages-status-provider1 libiodbc2
  libiptcdata0 libisofs6 libiw30 libjack-jackd2-0 libjasper1 libjpeg62
  libjs-jquery libjson-glib-1.0-0 libkate1 libkdcraw-data libkexiv2-data
  libkeyutils1 libkgeomap-data libkipi-data libklibc libkonq5-templates
  libkpathsea5 libksane-data libkvkontakte1 liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblcms1 liblcms2-2 liblightdm-gobject-1-0
  libllvm2.9 liblouis-data liblouis2 liblqr-1-0 libltdl7 liblua5.1-0
  liblvm2app2.2 libmad0 libmagic1 libmeanwhile1 libmetacity-private0 libmimic0
  libmng1 libmodplug1 libmono-addins-gui0.2-cil libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-cairo4.0-cil libmono-corlib2.0-cil
  libmono-corlib4.0-cil libmono-csharp4.0-cil libmono-i18n-west2.0-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-management2.0-cil
  libmono-management4.0-cil libmono-posix2.0-cil libmono-posix4.0-cil
  libmono-security2.0-cil libmono-security4.0-cil libmono-sharpzip2.84-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil
  libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil
  libmono-system2.0-cil libmono-system4.0-cil libmono-zeroconf1.0-cil
  libmount1 libmozjs185-1.0 libmp3lame0 libmpc2 libmpfr4 libmtp-common
  libmtp-runtime libmtp9 libmythes-1.2-0 libncurses5 libncursesw5
  libnet-http-perl libnetpbm10 libnewt0.52 libnih-dbus1 libnih1 libnl1
  libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-util2 libnotify-bin
  libnotify0.4-cil libnotify4 libnspr4 libnspr4-0d libnss-mdns libnss3
  libnss3-1d libntrack-qt4-1 libntrack0 libofa0 liboil0.3 liboobs-1-5
  libopencc1 liborbit2 liborc-0.4-0 liboverlay-scrollbar-0.2-0 libp11-kit0
  libpam-ck-connector libpam-gnome-keyring libpam-modules libpam-modules-bin
  libpam-runtime libpam0g libpango1.0-0 libpangomm-1.4-1 libpaper-utils
  libpaper1 libparted0debian1 libpathplan4 libpcap0.8 libpci3 libpciaccess0
  libpcre3 libpcsclite1 libpeas-1.0-0 libpeas-common libphonon4 libpipeline1
  libpixman-1-0 libplist1 libplymouth2 libpng12-0 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpolkit-qt-1-1 libpopt0
  libportaudio2 libprison0 libprotobuf7 libprotoc7 libpth20
  libpulse-mainloop-glib0 libpulse0 libpurple-bin libpython2.7 libqjson0
  libqtbamf1 libqtglib-2.0-0 libqtgstreamer-0.10-0 libqtgstreamerui-0.10-0
  libquadmath0 libraptor1 libraptor2-0 librasqal3 libraw1394-11 librdf0
  libreadline6 libreoffice-emailmerge libreoffice-style-human librest-0.7-0
  librsvg2-2 librsvg2-common librsync1 librtmp0 libsamplerate0 libsasl2-2
  libsasl2-modules libschroedinger-1.0-0 libsdl-image1.2 libselinux1
  libsensors4 libsepol1 libsgutils2-2 libshout3 libsigc++-2.0-0c2a libslang2
  libslv2-9 libsm6 libsndfile1 libsnmp-base libsoundtouch0 libsoup-gnome2.4-1
  libspeechd2 libspeex1 libspeexdsp1 libsqlite3-0 libss2 libssl0.9.8
  libstartup-notification0 libstdc++6 libstdc++6-4.6-dev libswitch-perl
  libt1-5 libtag1-vanilla libtag1c2a libtaglib2.0-cil libtalloc2 libtasn1-3
  libtdb1 libtelepathy-glib0 libtelepathy-logger2 libtextcat-data libtextcat0
  libthai-data libthai0 libtheora0 libtiff4 libtinfo5 libtotem0 libts-0.0-0
  libtwolame0 libudev0 libunique-1.0-0 libunique-3.0-0 libupower-glib1
  liburi-perl libusb-0.1-4 libusb-1.0-0 libusbmuxd1 libutouch-evemu1
  libutouch-frame1 libutouch-geis1 libutouch-grail1 libuuid1 libva-x11-1
  libva1 libvirtodbc0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a
  libvorbisenc2 libvorbisfile3 libwavpack1 libwbclient0
  libwebkitgtk-1.0-common libwebkitgtk-3.0-common libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
  libwww-perl libx11-6 libx11-data libx11-xcb1 libx86-1 libxapian22 libxau6
  libxaw7 libxcb-dri2-0 libxcb-keysyms1 libxcb-randr0 libxcb-render0
  libxcb-shape0 libxcb-shm0 libxcb-util0 libxcb-xv0 libxcb1 libxcomposite1
  libxdamage1 libxdmcp6 libxext6 libxft2 libxi6 libxinerama1 libxkbfile1
  libxklavier16 libxml-twig-perl libxml2 libxml2-utils libxmu6 libxmuu1 libxp6
  libxpm4 libxrender1 libxslt1.1 libxt6 libxtst6 libxv1 libxxf86vm1 libyajl1
  libzbar0 libzeitgeist-1.0-1 light-themes lightdm linux-firmware
  linux-libc-dev linux-sound-base lm-sensors locales lockfile-progs login
  lsb-base lsb-release lshw ltrace lzma makedev man-db manpages manpages-dev
  marble-data mawk media-player-info memtest86+ metacity-common
  mobile-broadband-provider-info modemmanager module-init-tools mono-2.0-gac
  mono-4.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime mount
  mountall mousetweaks multiarch-support myspell-en-au mythes-en-au
  nautilus-sendto ncurses-base ncurses-bin net-tools netbase netpbm
  network-manager-pptp network-manager-pptp-gnome notify-osd ntpdate nux-tools
  nvidia-common obexd-client odbcinst onboard oneconf openjdk-6-jre-headless
  openjdk-6-jre-lib openoffice.org-calc openoffice.org-common
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us
  openoffice.org-hyphenation-en-us openoffice.org-impress
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-thesaurus-en-au openoffice.org-thesaurus-en-us
  openoffice.org-writer openprinting-ppds os-prober overlay-scrollbar
  oxygen-icon-theme parted passwd patch pciutils pcmciautils phonon
  phonon-backend-gstreamer pitivi plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pm-utils policykit-1
  policykit-1-gnome policykit-desktop-privileges pppconfig procps
  protobuf-compiler psmisc pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-x11 python python-apport
  python-apt-common python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-avahi
  python-brlapi python-cairo python-central python-chardet python-compizconfig
  python-configglue python-couchdb python-crypto python-cups
  python-cupshelpers python-dateutil python-debian python-defer
  python-desktopcouch-application python-desktopcouch-records
  python-egenix-mxdatetime python-egenix-mxtools python-gconf python-gdbm
  python-glade2 python-gmenu python-gnome2 python-gnupginterface
  python-gobject-2 python-gst0.10 python-gtk2 python-gtksourceview2
  python-gtkspell python-httplib2 python-imaging python-keyring
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-libxml2 python-louis python-mako python-markupsafe
  python-minimal python-newt python-notify python-oauth python-openssl
  python-pam python-pexpect python-piston-mini-client python-pkg-resources
  python-problem-report python-protobuf python-pyatspi2 python-pygoocanvas
  python-pyinotify python-pyorbit python-rdflib python-serial
  python-simplejson python-smbc python-software-properties python-speechd
  python-support python-telepathy python-twisted-bin python-twisted-core
  python-twisted-names python-twisted-web python-ubuntuone-storageprotocol
  python-virtkey python-wadllib python-webkit python-wnck python-xapian
  python-xdg python-xkit python-zope.interface python2.7 python2.7-minimal
  qapt-batch radeontool readline-common rfkill rsync rsyslog rtkit sane-utils
  screen-resolution-extra shared-desktop-ontologies shared-mime-info
  simple-scan software-properties-common software-properties-gtk
  sound-theme-freedesktop speech-dispatcher ssh-askpass-gnome ssl-cert sudo
  syslinux syslinux-common system-config-printer-common
  system-config-printer-gnome system-config-printer-udev system-tools-backends
  sysv-rc sysvinit-utils tar tcl8.5 tcpdump telepathy-gabble telepathy-haze
  telepathy-idle telepathy-logger telepathy-salut toshset tsconf
  ttf-dejavu-core ttf-dejavu-extra ttf-ubuntu-font-family ttf-wqy-microhei
  tzdata tzdata-java ubufox ubuntu-artwork ubuntu-docs ubuntu-keyring
  ubuntu-mono ubuntu-restricted-addons ubuntu-standard ubuntu-system-service
  ubuntuone-couch ubuntuone-installer udev ufw unattended-upgrades
  unity-asset-pool unity-place-applications uno-libs3 update-inetd
  update-notifier update-notifier-common upower upstart ure ureadahead
  usb-modeswitch usb-modeswitch-data usbmuxd usbutils util-linux uuid-runtime
  vim-common vim-tiny vinagre virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common vorbis-tools w3m wamerican wbritish wget
  whiptail whois wireless-tools wodim x11-apps x11-common x11-session-utils
  x11-utils xdg-user-dirs xdg-user-dirs-gtk xfonts-encodings xinput xkb-data
  xscreensaver-data xscreensaver-gl xserver-common xserver-xorg-input-all
  xserver-xorg-video-all xsltproc xul-ext-ubufox yelp-xsl zeitgeist-datahub
  zenity zenity-common zlib1g
1071 upgraded, 0 newly installed, 0 to remove and 514 not upgraded.
Need to get 0 B/441 MB of archives.
After this operation, 67.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `liba52-0.7.4' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
chiara@chiara-Inspiron-1420:~$ 

```

same when I try to delete the package:
```
chiara@chiara-Inspiron-1420:~$ sudo apt-get remove liba52-0.7.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gstreamer0.10-plugins-ugly liba52-0.7.4 vlc vlc-nox vlc-plugin-notify
  vlc-plugin-pulse
0 upgraded, 0 newly installed, 6 to remove and 1579 not upgraded.
After this operation, 14.2 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 files list file for package `liba52-0.7.4' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
chiara@chiara-Inspiron-1420:~$ 

```

any help would be greatly appreciated

---

### Post by cortman on 2012-08-20
Hi, try

```
sudo rm /var/cache/apt/archives/*
sudo apt-get update
sudo apt-get upgrade
```

Please post back in full any errors received. Thanks.

---

### Post by ironmaiden943 on 2012-08-20
hi, it's still giving me the same error message:

```
chiara@chiara-Inspiron-1420:~$ sudo rm /var/cache/apt/archives/*
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory

```

then I run sudo apt-get update, with no problems, and then when I do sudo apt-get upgrade it gives me the same error message after downloading all the archives:

```
chiara@chiara-Inspiron-1420:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  aisleriot akonadi-backend-mysql akonadi-server anjuta-common apt
  apt-transport-https apt-utils at-spi banshee banshee-extension-soundmenu
  baobab bind9-host brasero brasero-cdrkit brasero-common brltty brltty-x11
  byobu c2esp cheese cheese-common compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default compiz-plugins-main
  compiz-plugins-main-default compizconfig-backend-gconf couchdb-bin cups
  cups-driver-gutenprint dconf-gsettings-backend deja-dup dnsmasq-base
  dnsutils dolphin ecryptfs-utils empathy empathy-common eog espeak
  espeak-data evince evince-common evolution evolution-common
  evolution-couchdb evolution-couchdb-backend evolution-data-server
  evolution-data-server-common evolution-exchange evolution-indicator
  evolution-plugins evolution-webcal exiv2 file-roller foo2zjs
  foomatic-db-compressed-ppds fuse-utils gconf-defaults-service gconf-editor
  gconf2 gconf2-common gdm gedit gedit-common geoclue gir1.2-appindicator3-0.1
  gir1.2-gconf-2.0 gir1.2-gdkpixbuf-2.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-rb-3.0 gir1.2-soup-2.4
  gir1.2-totem-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 glib-networking
  gnome-bluetooth gnome-control-center gnome-control-center-data
  gnome-desktop-data gnome-desktop3-data gnome-dictionary gnome-disk-utility
  gnome-keyring gnome-media gnome-online-accounts gnome-orca
  gnome-power-manager gnome-search-tool gnome-session gnome-session-bin
  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-share gnomine
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
  gtkpod gtkpod-data gucharmap gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber
  gwibber-service hpijs hplip hplip-cups hplip-data ibus icedtea-netx
  icedtea-plugin icedtea6-plugin imagemagick indicator-application
  indicator-appmenu indicator-datetime indicator-messages indicator-power
  indicator-session indicator-sound kamoso katepart kde-baseapps-bin
  kde-runtime kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime
  kdepimlibs-kio-plugins kdoctools kipi-plugins kipi-plugins-common konqueror
  konqueror-nsplugins libakonadi-contact4 libakonadi-kcal4 libakonadi-kde4
  libakonadi-kmime4 libakonadiprotocolinternals1 libalgorithm-diff-xs-perl
  libanjuta-3-0 libapparmor-perl libappindicator1 libappindicator3-1
  libatk-adaptor libavcodec53 libavformat53 libavutil51 libbonoboui2-0
  libbrasero-media3-1 libcairo-perl libcamel-1.2-29 libcanberra-gtk3-module
  libcap2-bin libclutter-1.0-0 libclutter-gst-1.0-0 libclutter-gtk-1.0-0
  libcompizconfig0 libcups2 libcurl3 libcurl3-gnutls libdecoration0
  libebackend-1.2-1 libedata-book-1.2-11 libedata-cal-1.2-13
  libedataserverui-3.0-1 libenchant1c2a libespeak1 libevince3-3 libevolution
  libfolks-telepathy25 libfolks25 libfuse2 libgail-3-0 libgconf2-4 libgcr-3-1
  libgdata13 libgdict-1.0-6 libgdk-pixbuf2.0-0 libgdl-3-common libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libglib-perl libglib2.0-cil
  libgnome-desktop-3-2 libgnome-keyring0 libgnome2-canvas-perl libgnome2-perl
  libgnome2-vfs-perl libgnomeui-0 libgoa-1.0-0 libgssapi-krb5-2 libgtk-3-0
  libgtk-3-bin libgtk2-perl libgtk2.0-cil libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libgtkmm-3.0-1 libgtkpod1
  libgtksourceview-3.0-0 libgtksourceview-3.0-common libgucharmap-2-90-7
  libgweather-3-0 libgwibber-gtk2 libgwibber2 libhpmud0 libhtml-parser-perl
  libidl0 libindicate5 libio-socket-ssl-perl libjpeg8 libk5crypto3 libkabc4
  libkatepartinterfaces4 libkcal4 libkcalcore4 libkcalutils4 libkcmutils4
  libkdcraw20 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5
  libkdnssd4 libkemoticons4 libkexiv2-10 libkfile4 libkgeomap1 libkhtml5
  libkidletime4 libkimap4 libkio5 libkipi8 libkjsapi4 libkjsembed4 libkldap4
  libkmbox4 libkmediaplayer4 libkmime4 libknewstuff3-4 libknotifyconfig4
  libkntlm4 libkonq-common libkonq5abi1 libkonqsidebarplugin4a libkparts4
  libkpimidentities4 libkpimtextedit4 libkpimutils4 libkpty4 libkrb5-3
  libkrb5support0 libkresources4 libkrosscore4 libksane0 libktexteditor4
  libldap-2.4-2 liblocale-gettext-perl liblockfile1 libmailtransport4
  libmicroblog4 libmission-control-plugins0 libmx-1.0-2 libnepomuk4
  libnepomukquery4a libnepomukutils4 libnet-dbus-perl libnet-ssleay-perl
  libnice10 libnm-gtk0 liboauth0 liboverlay-scrollbar3-0.2-0 libpango-perl
  libplasma3 libpostproc52 libpurple0 libqapt-runtime libqapt1 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-xml libqt4-xmlpatterns libqtcore4 libqtdee2 libqtgui4 libqtwebkit4
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-impress libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-math libreoffice-writer librpc-xml-perl
  libsane libsane-hpaio libsdl1.2debian libsmbclient libsnmp15 libsolid4
  libsoprano4 libsoup2.4-1 libssl1.0.0 libstreamanalyzer0 libstreams0
  libswscale2 libsyncdaemon-1.0-1 libterm-readkey-perl libtext-charwidth-perl
  libtext-iconv-perl libthreadweaver4 libtotem-plparser17 libunity-2d-private0
  libuuid-perl libv4l-0 libvcdinfo0 libvlc5 libvte-2.90-9 libvte-common
  libvte9 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwildmidi1 libxfixes3
  libxml-parser-perl libyelp0 linux-generic linux-headers-generic
  linux-image-generic marble-plugins metacity min12xxw mysql-common nautilus
  nautilus-data nautilus-sendto-empathy nautilus-share network-manager
  network-manager-gnome ntfs-3g ntrack-module-libnl-0 odbcinst1debian2
  openjdk-6-jre openssh-client openssl perl perl-base perl-modules
  plasma-scriptengine-javascript pnm2ppa poppler-utils ptouch-driver
  pulseaudio-module-gconf pulseaudio-utils pxljr python-appindicator
  python-apt python-dbus python-gnomekeyring python-gobject python-ibus
  python-indicate python-libproxy python-pycurl python-ubuntuone-client
  python-ubuntuone-control-panel python-uno python-vte qdbus qt-at-spi
  quadrapassel rastertosag-gdi rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins samba-common samba-common-bin seahorse sessioninstaller
  shotwell smbclient software-center soprano-daemon splix synaptic
  telepathy-indicator telepathy-mission-control-5 thunderbird
  thunderbird-globalmenu thunderbird-gnome-support tomboy totem totem-common
  totem-mozilla totem-plugins transmission-common transmission-gtk
  ttf-kacst-one ttf-khmeros-core ttf-lao ttf-liberation
  ttf-mscorefonts-installer ttf-opensymbol ttf-takao-pgothic ttf-thai-tlwg
  ttf-unfonts-core ubuntu-desktop ubuntu-minimal ubuntu-sso-client
  ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome
  ubuntuone-control-panel ubuntuone-control-panel-gtk udisks unity unity-2d
  unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread
  unity-common unity-greeter unity-lens-applications unity-lens-files
  unity-lens-music unity-scope-musicstores unity-services update-manager
  update-manager-core usb-creator-common usb-creator-gtk vino vlc vlc-data
  vlc-nox vlc-plugin-notify vlc-plugin-pulse wireless-crda wpasupplicant
  xdiagnose xorg xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo xz-utils yelp zeitgeist zeitgeist-core
The following packages will be upgraded:
  accountsservice acl acpi-support acpid adduser adium-theme-ubuntu alacarte
  alsa-base alsa-utils app-install-data app-install-data-partner apparmor
  apparmor-utils appmenu-gtk appmenu-gtk3 appmenu-qt apport apport-gtk
  apt-xapian-index aptdaemon aptdaemon-data apturl apturl-common aspell at
  at-spi2-core avahi-autoipd avahi-daemon avahi-utils b43-fwcutter bamfdaemon
  base-files base-passwd bash bash-completion binfmt-support binutils bluez
  bluez-alsa bluez-cups bluez-gstreamer bogofilter bogofilter-bdb
  bogofilter-common bsdmainutils bsdutils build-essential busybox-initramfs
  busybox-static bzip2 ca-certificates ca-certificates-java checkbox
  checkbox-gtk cli-common colord command-not-found command-not-found-data
  compiz-fusion-plugins-main compizconfig-settings-manager computer-janitor
  computer-janitor-gtk console-setup consolekit coreutils cpio cpp cpp-4.4
  cpp-4.5 cpp-4.6 cpu-checker cron cups-bsd cups-client cups-common cups-ppdc
  dash dbus dbus-x11 debconf debconf-i18n debianutils desktop-file-utils
  desktopcouch dhcp3-client dhcp3-common dictionaries-common diffutils dkms
  dmidecode dmsetup doc-base docbook-xml docbook-xsl dosfstools dpkg dpkg-dev
  duplicity e2fslibs e2fsprogs ed eject erlang-base erlang-crypto erlang-inets
  erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl
  erlang-syntax-tools erlang-xmerl example-content fakeroot fancontrol file
  findutils firefox firefox-branding firefox-globalmenu firefox-gnome-support
  firefox-locale-en firmware-b43-installer flashplugin-downloader
  flashplugin-installer fontconfig fontconfig-config foomatic-filters
  friendly-recovery g++ g++-4.6 gamin gbrainy gcalctool gcc gcc-4.4
  gcc-4.4-base gcc-4.5 gcc-4.5-base gcc-4.6 gcc-4.6-base gdb genisoimage
  geoip-database gettext-base ghostscript ghostscript-cups ghostscript-x
  gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-gmenu-3.0
  gir1.2-gstreamer-0.10 gir1.2-gtk-2.0 gir1.2-launchpad-integration-3.0
  gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-totem-plparser-1.0
  gir1.2-wnck-3.0 gksu gnome-accessibility-themes gnome-applets-data
  gnome-codec-install gnome-doc-utils gnome-font-viewer gnome-icon-theme
  gnome-icon-theme-symbolic gnome-menus gnome-nettool gnome-panel-data
  gnome-screensaver gnome-screenshot gnome-session-canberra gnome-system-log
  gnome-system-tools gnome-user-guide gnome-utils gnome-video-effects gnupg
  gpgv grep groff-base grub-common grub-gfxpayload-lists grub-pc grub-pc-bin
  grub2-common gs-cjk-resource gsettings-desktop-schemas gstreamer0.10-alsa
  gstreamer0.10-fluendo-mp3 gstreamer0.10-gconf gstreamer0.10-nice
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gtk3-engines-unico gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter gzip hdparm hicolor-icon-theme hunspell-en-us hwdata
  hyphen-en-us ibus-gtk ibus-gtk3 ibus-pinyin ibus-pinyin-db-android
  ibus-pinyin-db-open-phrase ibus-table icc-profiles-free icedtea-6-jre-cacao
  icedtea-6-jre-jamvm icoutils ifupdown indicator-status-provider-mc5 info
  initramfs-tools initramfs-tools-bin initscripts inputattach insserv
  install-info intel-gpu-tools iproute iptables iputils-arping iputils-ping
  iputils-tracepath irqbalance isc-dhcp-client isc-dhcp-common iso-codes
  java-common jockey-common jockey-gtk kate-data kbd kde-baseapps-data
  kde-runtime-data kdebase-runtime kerneloops-daemon keyboard-configuration
  keyutils klibc-utils language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common language-selector-gnome launchpad-integration lftp
  liba52-0.7.4 libaa1 libaccess-bridge-java libaccess-bridge-java-jni
  libaccountsservice0 libacl1 libakonadi-kabc4 libao-common libao4
  libapparmor1 libappindicator0.1-cil libasound2 libasound2-plugins
  libaspell15 libass4 libatasmart4 libatk1.0-0 libatk1.0-data libatkmm-1.6-1
  libatm1 libatspi1.0-0 libatspi2.0-0 libattr1 libaudio2 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-glib1
  libavahi-gobject0 libavahi-ui-gtk3-0 libavahi-ui0 libavc1394-0 libbamf0
  libbamf3-0 libblkid1 libbluetooth3 libbonobo2-0 libbonobo2-common
  libbonoboui2-common libboost-program-options1.46.1
  libboost-serialization1.46.1 libbrlapi0.5 libbsd0 libburn4 libbz2-1.0
  libc-bin libc-dev-bin libc6 libc6-dev libcaca0 libcairo-gobject2 libcairo2
  libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-pulse libcanberra0 libcap-ng0 libcap2 libcdaudio1 libcddb2
  libcdparanoia0 libcdt4 libck-connector0 libclass-isa-perl
  libclutter-1.0-common libclutter-imcontext-0.1-0 libcluttergesture-0.0.2-0
  libcogl-common libcolord1 libcomerr2 libcouchdb-glib-1.0-2 libcroco3
  libcrypt-passwdmd5-perl libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdatrie1 libdb4.8 libdb5.1 libdbus-1-3
  libdbus-glib-1-2 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4
  libdbusmenu-qt2 libdc1394-22 libdca0 libdconf-dbus-1-0 libdconf-qt0
  libdconf0 libdesktopcouch-glib-1.0-2 libdevmapper-event1.02.1
  libdevmapper1.02.1 libdirac-encoder0 libdirectfb-1.2-9 libdjvulibre-text
  libdjvulibre21 libdlrestrictions1 libdmapsharing-3.0-2 libdmtx0a
  libdpkg-perl libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libdv4
  libdvbpsi7 libdvdnav4 libdvdread4 libebml3 libecryptfs0 libedit2 libelf1
  libencode-locale-perl libevent-2.0-5 libexempi3 libexif12 libexpat1 libfaad2
  libffi6 libfftw3-3 libfile-desktopentry-perl libfile-listing-perl
  libfile-mimeinfo-perl libflac8 libflite1 libfontconfig1 libfreetype6
  libgadu3 libgail-common libgail18 libgamin0 libgc1c2 libgcc1 libgck-1-0
  libgcrypt11 libgd2-xpm libgdata-common libgdiplus libgdu-gtk0 libgdu0
  libgee2 libgeoclue0 libgeoip1 libgfortran3 libgif4 libgirepository-1.0-1
  libgksu2-0 libglade2-0 libglade2.0-cil libgladeui-1-11 libglib2.0-0
  libglib2.0-bin libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa libgmp10
  libgnome-bluetooth8 libgnome-control-center1 libgnome-desktop-2-17
  libgnome-media-profiles-3.0-0 libgnome-menu-3-0 libgnome-menu2 libgnome2-0
  libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common
  libgnomekbd7 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgnutls26 libgomp1 libgpg-error0 libgpgme11
  libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgpm2 libgpod-common
  libgpod4 libgraph4 libgraphite3 libgrip0 libgs9 libgs9-common libgsl0ldbl
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-3-common
  libgtk-vnc-1.0-0 libgtk-vnc-2.0-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19
  libgtkmm-2.4-1c2a libgtkspell0 libgtop2-7 libgtop2-common libgudev-1.0-0
  libgutenprint2 libgvc5 libgvnc-1.0-0 libgweather-common libhyphen0
  libibus-1.0-0 libical0 libice6 libid3-3.8.3c2a libidn11 libido-0.1-0
  libido3-0.1-0 libiec61883-0 libieee1284-3 libijs-0.35 libimobiledevice2
  libindicate-gtk3 libindicator-messages-status-provider1 libiodbc2
  libiptcdata0 libisofs6 libiw30 libjack-jackd2-0 libjasper1 libjpeg62
  libjs-jquery libjson-glib-1.0-0 libkate1 libkdcraw-data libkexiv2-data
  libkeyutils1 libkgeomap-data libkipi-data libklibc libkonq5-templates
  libkpathsea5 libksane-data libkvkontakte1 liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblcms1 liblcms2-2 liblightdm-gobject-1-0
  libllvm2.9 liblouis-data liblouis2 liblqr-1-0 libltdl7 liblua5.1-0
  liblvm2app2.2 libmad0 libmagic1 libmeanwhile1 libmetacity-private0 libmimic0
  libmng1 libmodplug1 libmono-addins-gui0.2-cil libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-cairo4.0-cil libmono-corlib2.0-cil
  libmono-corlib4.0-cil libmono-csharp4.0-cil libmono-i18n-west2.0-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-management2.0-cil
  libmono-management4.0-cil libmono-posix2.0-cil libmono-posix4.0-cil
  libmono-security2.0-cil libmono-security4.0-cil libmono-sharpzip2.84-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil
  libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil
  libmono-system2.0-cil libmono-system4.0-cil libmono-zeroconf1.0-cil
  libmount1 libmozjs185-1.0 libmp3lame0 libmpc2 libmpfr4 libmtp-common
  libmtp-runtime libmtp9 libmythes-1.2-0 libncurses5 libncursesw5
  libnet-http-perl libnetpbm10 libnewt0.52 libnih-dbus1 libnih1 libnl1
  libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-util2 libnotify-bin
  libnotify0.4-cil libnotify4 libnspr4 libnspr4-0d libnss-mdns libnss3
  libnss3-1d libntrack-qt4-1 libntrack0 libofa0 liboil0.3 liboobs-1-5
  libopencc1 liborbit2 liborc-0.4-0 liboverlay-scrollbar-0.2-0 libp11-kit0
  libpam-ck-connector libpam-gnome-keyring libpam-modules libpam-modules-bin
  libpam-runtime libpam0g libpango1.0-0 libpangomm-1.4-1 libpaper-utils
  libpaper1 libparted0debian1 libpathplan4 libpcap0.8 libpci3 libpciaccess0
  libpcre3 libpcsclite1 libpeas-1.0-0 libpeas-common libphonon4 libpipeline1
  libpixman-1-0 libplist1 libplymouth2 libpng12-0 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpolkit-qt-1-1 libpopt0
  libportaudio2 libprison0 libprotobuf7 libprotoc7 libpth20
  libpulse-mainloop-glib0 libpulse0 libpurple-bin libpython2.7 libqjson0
  libqtbamf1 libqtglib-2.0-0 libqtgstreamer-0.10-0 libqtgstreamerui-0.10-0
  libquadmath0 libraptor1 libraptor2-0 librasqal3 libraw1394-11 librdf0
  libreadline6 libreoffice-emailmerge libreoffice-style-human librest-0.7-0
  librsvg2-2 librsvg2-common librsync1 librtmp0 libsamplerate0 libsasl2-2
  libsasl2-modules libschroedinger-1.0-0 libsdl-image1.2 libselinux1
  libsensors4 libsepol1 libsgutils2-2 libshout3 libsigc++-2.0-0c2a libslang2
  libslv2-9 libsm6 libsndfile1 libsnmp-base libsoundtouch0 libsoup-gnome2.4-1
  libspeechd2 libspeex1 libspeexdsp1 libsqlite3-0 libss2 libssl0.9.8
  libstartup-notification0 libstdc++6 libstdc++6-4.6-dev libswitch-perl
  libt1-5 libtag1-vanilla libtag1c2a libtaglib2.0-cil libtalloc2 libtasn1-3
  libtdb1 libtelepathy-glib0 libtelepathy-logger2 libtextcat-data libtextcat0
  libthai-data libthai0 libtheora0 libtiff4 libtinfo5 libtotem0 libts-0.0-0
  libtwolame0 libudev0 libunique-1.0-0 libunique-3.0-0 libupower-glib1
  liburi-perl libusb-0.1-4 libusb-1.0-0 libusbmuxd1 libutouch-evemu1
  libutouch-frame1 libutouch-geis1 libutouch-grail1 libuuid1 libva-x11-1
  libva1 libvirtodbc0 libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a
  libvorbisenc2 libvorbisfile3 libwavpack1 libwbclient0
  libwebkitgtk-1.0-common libwebkitgtk-3.0-common libwmf0.2-7 libwmf0.2-7-gtk
  libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
  libwww-perl libx11-6 libx11-data libx11-xcb1 libx86-1 libxapian22 libxau6
  libxaw7 libxcb-dri2-0 libxcb-keysyms1 libxcb-randr0 libxcb-render0
  libxcb-shape0 libxcb-shm0 libxcb-util0 libxcb-xv0 libxcb1 libxcomposite1
  libxdamage1 libxdmcp6 libxext6 libxft2 libxi6 libxinerama1 libxkbfile1
  libxklavier16 libxml-twig-perl libxml2 libxml2-utils libxmu6 libxmuu1 libxp6
  libxpm4 libxrender1 libxslt1.1 libxt6 libxtst6 libxv1 libxxf86vm1 libyajl1
  libzbar0 libzeitgeist-1.0-1 light-themes lightdm linux-firmware
  linux-libc-dev linux-sound-base lm-sensors locales lockfile-progs login
  lsb-base lsb-release lshw ltrace lzma makedev man-db manpages manpages-dev
  marble-data mawk media-player-info memtest86+ metacity-common
  mobile-broadband-provider-info modemmanager module-init-tools mono-2.0-gac
  mono-4.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime mount
  mountall mousetweaks multiarch-support myspell-en-au mythes-en-au
  nautilus-sendto ncurses-base ncurses-bin net-tools netbase netpbm
  network-manager-pptp network-manager-pptp-gnome notify-osd ntpdate nux-tools
  nvidia-common obexd-client odbcinst onboard oneconf openjdk-6-jre-headless
  openjdk-6-jre-lib openoffice.org-calc openoffice.org-common
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us
  openoffice.org-hyphenation-en-us openoffice.org-impress
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-thesaurus-en-au openoffice.org-thesaurus-en-us
  openoffice.org-writer openprinting-ppds os-prober overlay-scrollbar
  oxygen-icon-theme parted passwd patch pciutils pcmciautils phonon
  phonon-backend-gstreamer pitivi plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pm-utils policykit-1
  policykit-1-gnome policykit-desktop-privileges pppconfig procps
  protobuf-compiler psmisc pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-x11 python python-apport
  python-apt-common python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-avahi
  python-brlapi python-cairo python-central python-chardet python-compizconfig
  python-configglue python-couchdb python-crypto python-cups
  python-cupshelpers python-dateutil python-debian python-defer
  python-desktopcouch-application python-desktopcouch-records
  python-egenix-mxdatetime python-egenix-mxtools python-gconf python-gdbm
  python-glade2 python-gmenu python-gnome2 python-gnupginterface
  python-gobject-2 python-gst0.10 python-gtk2 python-gtksourceview2
  python-gtkspell python-httplib2 python-imaging python-keyring
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-libxml2 python-louis python-mako python-markupsafe
  python-minimal python-newt python-notify python-oauth python-openssl
  python-pam python-pexpect python-piston-mini-client python-pkg-resources
  python-problem-report python-protobuf python-pyatspi2 python-pygoocanvas
  python-pyinotify python-pyorbit python-rdflib python-serial
  python-simplejson python-smbc python-software-properties python-speechd
  python-support python-telepathy python-twisted-bin python-twisted-core
  python-twisted-names python-twisted-web python-ubuntuone-storageprotocol
  python-virtkey python-wadllib python-webkit python-wnck python-xapian
  python-xdg python-xkit python-zope.interface python2.7 python2.7-minimal
  qapt-batch radeontool readline-common rfkill rsync rsyslog rtkit sane-utils
  screen-resolution-extra shared-desktop-ontologies shared-mime-info
  simple-scan software-properties-common software-properties-gtk
  sound-theme-freedesktop speech-dispatcher ssh-askpass-gnome ssl-cert sudo
  syslinux syslinux-common system-config-printer-common
  system-config-printer-gnome system-config-printer-udev system-tools-backends
  sysv-rc sysvinit-utils tar tcl8.5 tcpdump telepathy-gabble telepathy-haze
  telepathy-idle telepathy-logger telepathy-salut toshset tsconf
  ttf-dejavu-core ttf-dejavu-extra ttf-ubuntu-font-family ttf-wqy-microhei
  tzdata tzdata-java ubufox ubuntu-artwork ubuntu-docs ubuntu-keyring
  ubuntu-mono ubuntu-restricted-addons ubuntu-standard ubuntu-system-service
  ubuntuone-couch ubuntuone-installer udev ufw unattended-upgrades
  unity-asset-pool unity-place-applications uno-libs3 update-inetd
  update-notifier update-notifier-common upower upstart ure ureadahead
  usb-modeswitch usb-modeswitch-data usbmuxd usbutils util-linux uuid-runtime
  vim-common vim-tiny vinagre virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common vorbis-tools w3m wamerican wbritish wget
  whiptail whois wireless-tools wodim x11-apps x11-common x11-session-utils
  x11-utils xdg-user-dirs xdg-user-dirs-gtk xfonts-encodings xinput xkb-data
  xscreensaver-data xscreensaver-gl xserver-common xserver-xorg-input-all
  xserver-xorg-video-all xsltproc xul-ext-ubufox yelp-xsl zeitgeist-datahub
  zenity zenity-common zlib1g
1071 upgraded, 0 newly installed, 0 to remove and 514 not upgraded.
Need to get 441 MB of archives.
After this operation, 67.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
Fetched 441 MB in 7min 29s (980 kB/s)                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package `liba52-0.7.4' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

---

### Post by sandyd on 2012-08-20
File list corrupt

Try
```

rm /var/lib/dpkg/info/liba52*.list
sudo dpkg -i --force all /var/cache/apt/archives/liba52*deb

```

---

### Post by ironmaiden943 on 2012-08-20
hi,
the 1st command worked, however for the second command i get this error
```

chiara@chiara-Inspiron-1420:~$ sudo dpkg -i --force all /var/cache/apt/archives/liba52*deb
dpkg: error processing /var/cache/apt/archives/liba52*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/liba52*deb

```

---

### Post by cortman on 2012-08-20
> **ironmaiden943 said:**
> hi,
the 1st command worked, however for the second command i get this error
```

chiara@chiara-Inspiron-1420:~$ sudo dpkg -i --force all /var/cache/apt/archives/liba52*deb
dpkg: error processing /var/cache/apt/archives/liba52*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/liba52*deb

```

To amend my original command slightly;

```
sudo rm /var/cache/apt/archives/liba52*.deb
sudo apt-get update
```

---

### Post by sandyd on 2012-08-20
Ah well, its not in the cache - installing it from the internet then
```
sudo apt-get install liba52
```

---

