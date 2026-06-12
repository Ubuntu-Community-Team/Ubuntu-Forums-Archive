---
title: "Tried to upgrade to 12.04 from 10.04 and broke packages?"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by JDM_SOHC on 2012-04-09
So I tried to do an upgrade via the server yesterday and it stuck @ 28% for a while than all the windows closed and it was just my wallpaper on a blank desktop for like 15 minutes.. So I rebooted the computer and tried to do the update again and no luck, it says I have broken packages that need to be fixed now..

When I do sudo apt-get update I get this..
```
shane@shanes-desktop:~$ sudo apt-get update
[sudo] password for shane: 
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [769B]                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main Translation-en_US        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en_US   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Fetched 2,314B in 6s (379B/s)                                                  
Reading package lists... Done
shane@shanes-desktop:~$ 

```

And when I run sudo apt-get upgrade, I get this..
```
shane@shanes-desktop:~$ sudo apt-get upgrade
[sudo] password for shane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  adobe-flash-properties-gtk adobe-flashplugin aisleriot alacarte alsa-utils
  apparmor apparmor-utils apport apport-gtk apt apt-transport-https apt-utils
  apt-xapian-index aptdaemon aptitude apturl apturl-common aspell at-spi
  audacity audacity-data avahi-daemon avant-window-navigator base-files bash
  bash-completion bind9-host binfmt-support binutils bluez bluez-alsa
  bluez-cups bluez-gstreamer bogofilter-bdb brasero brasero-common brltty
  brltty-x11 bsdmainutils bzip2 bzr bzrtools ca-certificates
  ca-certificates-java cdrdao checkbox checkbox-gtk cheese cheese-common
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
  command-not-found compiz compiz-core compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compiz-plugins
  compizconfig-backend-gconf compizconfig-settings-manager computer-janitor
  computer-janitor-gtk console-setup consolekit coreutils couchdb-bin cpp
  cpp-4.4 cpu-checker cron cups cups-bsd cups-client cups-driver-gutenprint
  cvs dbus-x11 dcraw debhelper debianutils default-jdk default-jre
  default-jre-headless desktop-file-utils desktopcouch dhcp3-client
  dhcp3-common dnsmasq-base dnsutils doc-base dpkg dpkg-dev dvd+rw-tools
  dvd-slideshow dvdauthor e2fslibs e2fsprogs eclipse eclipse-jdt eclipse-pde
  eclipse-platform eclipse-platform-data eclipse-rcp empathy empathy-common
  eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key
  erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl
  esound-common espeak espeak-data evince evolution evolution-common
  evolution-couchdb evolution-data-server evolution-data-server-common
  evolution-exchange evolution-indicator evolution-plugins evolution-webcal
  exiv2 f-spot ffmpeg file-roller firefox firefox-branding
  firefox-gnome-support fontconfig-config foo2zjs foomatic-db
  foomatic-db-engine friendly-recovery fuse-utils g++ g++-4.4 gawk gbrainy
  gcalctool gcc gcc-4.4 gcc-4.4-base gconf-defaults-service gconf-editor
  gconf2 gconf2-common gdb gdebi gdebi-core gdebi-kde gdm gedit gedit-common
  gettext ghostscript ghostscript-x gimp gimp-data gnome-applets
  gnome-applets-data gnome-bluetooth gnome-codec-install gnome-control-center
  gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-icon-theme
  gnome-keyring gnome-mag gnome-media gnome-menus gnome-nettool gnome-orca
  gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver
  gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon
  gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-user-guide gnome-user-share gnome-utils gnomine
  gparted grub-common grub-pc gstreamer0.10-alsa gstreamer0.10-ffmpeg
  gstreamer0.10-gnonlin gstreamer0.10-nice gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber
  gwibber-service hal hpijs hplip hplip-data ibus ibus-gtk ibus-m17n
  ibus-table icedtea-6-jre-cacao ifupdown imagemagick indicator-applet
  indicator-applet-session indicator-application indicator-messages
  indicator-session indicator-sound info initscripts intel-gpu-tools iproute
  iptables iputils-ping jockey-common jockey-gtk kbd kdebase-runtime
  kdelibs-bin kdelibs5 kdelibs5-data kdepimlibs5 kdesudo kpackagekit
  kubuntu-debug-installer lame language-selector language-selector-common
  launchpad-integration lftp libaa1 libaccess-bridge-java-jni libacl1
  libapparmor-perl libapt-inst1.4 libapt-pkg4.12 libart2.0-cil libasound2
  libasound2-plugins libaspell15 libass4 libatasmart4 libatk1.0-0 libatm1
  libattr1 libaudio2 libavahi-client3 libavahi-common3 libavahi-glib1
  libavahi-gobject0 libavahi-ui0 libavc1394-0 libawn1 libblkid1 libbluetooth3
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbsd0 libbz2-1.0 libc-bin
  libc-dev-bin libc6 libc6-dev libcaca0 libcairo-perl libcairo2
  libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse
  libcanberra0 libcap2 libcdparanoia0 libclutter-1.0-0 libcomerr2
  libcommons-logging-java libcompizconfig0 libcouchdb-glib-1.0-2 libcroco3
  libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
  libcurl3 libcurl3-gnutls libcwidget3 libdatrie1 libdb4.8 libdbus-1-3
  libdbus-glib-1-2 libdbusmenu-qt2 libdc1394-22 libdesktop-agnostic-cfg-gconf
  libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio
  libdesktop-agnostic0 libdesktopcouch-glib-1.0-2 libdjvulibre21 libdrm-intel1
  libdrm-radeon1 libdrm2 libdv4 libedit2 libelf1 libenchant1c2a
  libequinox-osgi-java libesd0 libespeak1 libexempi3 libexif12 libexpat1
  libflac++6 libflac8 libflickrnet2.2-cil libflite1 libfontconfig1
  libfreetype6 libfuse2 libgadu3 libgail-common libgail18 libgcc1 libgcj-bc
  libgconf2-4 libgconf2.0-cil libgcrypt11 libgd2-xpm libgdbm3 libgdict-1.0-6
  libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libgif4 libgimp2.0 libgksu2-0
  libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglade2.0-cil libglib-perl
  libglib2.0-0 libglib2.0-cil libglibmm-2.4-1c2a libglu1-mesa libgmime-2.4-2
  libgmime2.4-cil libgnome-desktop-2-17 libgnome-keyring0
  libgnome-keyring1.0-cil libgnome-vfs2.0-cil libgnome2-0
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnome2.24-cil libgnomecanvas2-0 libgnomekbd-common libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgnutls26 libgomp1
  libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpm2
  libgpod-common libgpod4 libgssapi-krb5-2 libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-cil libgtk2.0-common libgtkhtml-editor-common libgtkhtml-editor0
  libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgudev-1.0-0
  libgutenprint2 libgweather-common libhpmud0 libhtml-parser-perl libice-dev
  libice6 libidl0 libidn11 libido-0.1-0 libiec61883-0 libieee1284-3 libjack0
  libjasper1 libjpeg-progs libjson-glib-1.0-0 libk5crypto3 libkeyutils1
  libkrb5-3 libkrb5support0 liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblcms1 libldap-2.4-2
  liblocale-gettext-perl liblockfile1 libloudmouth1-0 libltdl7 liblua5.1-0
  liblucene2-java liblzo2-2 libmad0 libmetacity-private0 libmjpegtools-1.9
  libmng1 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil
  libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-runtime2.0-cil libmono-system-web2.0-cil
  libmono-system2.0-cil libmono2.0-cil libmp3lame0 libmpg123-0 libncurses5
  libncursesw5 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls
  libnet-dbus-perl libnetpbm10 libnewt0.52 libnih-dbus1 libnih1 libnl1
  libnspr4-0d libnss3-1d libogg0 liboil0.3 libopenal1 liborc-0.4-0
  libpam-modules libpam0g libpango-perl libpango1.0-0 libpangomm-1.4-1
  libparted0debian1 libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1
  libphonon4 libpisock9 libpixman-1-0 libplasma3 libplymouth2 libpng12-0
  libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpopt0
  libportaudio2 libpst4 libpulse-mainloop-glib0 libpulse0 libpurple0
  libpython2.6 libqca2 libqt3-mt libqt4-assistant libqt4-dbus libqt4-designer
  libqt4-gui libqt4-help libqt4-network libqt4-opengl libqt4-qt3support
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libraw1394-11 librdf0 libreadline6 librpc-xml-perl librsvg2-2
  librsvg2-common libsamplerate0 libsane libsasl2-2 libsasl2-modules
  libschroedinger-1.0-0 libsdl-image1.2 libsdl1.2debian libselinux1
  libsensors4 libsepol1 libshout3 libsigc++-2.0-0c2a libslang2 libsm-dev
  libsm6 libsmbclient libsndfile1 libsnmp15 libsoprano4 libsoup-gnome2.4-1
  libsoup2.4-1 libsox-fmt-alsa libsox-fmt-base libspectre1 libspeex1
  libspeexdsp1 libsqlite3-0 libss2 libssh-4 libssl0.9.8
  libstartup-notification0 libstdc++6 libstdc++6-4.4-dev libstreamanalyzer0
  libstreams0 libsub-name-perl libtag1-vanilla libtag1c2a libtalloc2
  libtasn1-3 libtdb1 libtelepathy-glib0 libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libthai0 libtheora0 libtiff4
  libtotem-plparser17 libts-0.0-0 libudev0 libunique-1.0-0 libusb-0.1-4
  libusb-1.0-0 libuuid-perl libuuid1 libv4l-0 libvcdinfo0 libvisual-0.4-0
  libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common
  libvte9 libwavpack1 libwbclient0 libwmf0.2-7 libwmf0.2-7-gtk libwnck22
  libwrap0 libwww-perl libwxbase2.8-0 libwxgtk2.8-0 libx11-6 libx11-data
  libx11-dev libxau-dev libxau6 libxaw7 libxcb-render0 libxcb-shape0
  libxcb-shm0 libxcb-xv0 libxcb1 libxcb1-dev libxcomposite1 libxcursor1
  libxdmcp-dev libxdmcp6 libxerces2-java libxext6 libxfixes3 libxft2 libxi6
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins
  libxine1-x libxinerama1 libxml-libxml-perl libxml-parser-perl
  libxml-sax-perl libxml2 libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2
  libxslt1.1 libxss1 libxt-dev libxt6 libxtst6 libxv1 libxvidcore4 libxxf86vm1
  light-themes linux-generic linux-headers-generic linux-image-generic
  logrotate lsb-release man-db mencoder metacity metacity-common min12xxw
  mjpegtools modemmanager module-init-tools mono-2.0-gac mono-gac mono-runtime
  mount mountall mousetweaks mozilla-plugin-vlc mplayer nano nautilus
  nautilus-data nautilus-dropbox nautilus-open-terminal nautilus-sendto
  nautilus-sendto-empathy nautilus-share ncurses-bin netpbm network-manager
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome
  notify-osd ntfs-3g ntpdate nvidia-common nvidia-current nvidia-settings
  obex-data-server obexd-client odbcinst onboard openjdk-6-jdk openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-calc
  openoffice.org-common openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-hyphenation-en-us
  openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-math openoffice.org-thesaurus-en-au
  openoffice.org-thesaurus-en-us openoffice.org-writer openprinting-ppds
  openssh-client openssl packagekit packagekit-backend-apt parted passwd
  pciutils pcmciautils perl perl-base perl-modules phonon pitivi pkg-config
  plasma-scriptengine-javascript plymouth plymouth-label plymouth-x11 pm-utils
  pnm2ppa policykit-1 policykit-1-gnome polkit-kde-1 poppler-utils ppp procps
  protobuf-compiler psmisc pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils pxljr python python-appindicator python-apport python-apt
  python-aptdaemon python-aptdaemon-gtk python-avahi python-awn
  python-awn-extras python-brlapi python-cairo python-chardet
  python-compizconfig python-configglue python-configobj python-couchdb
  python-crypto python-cups python-cupshelpers python-dateutil python-dbus
  python-debian python-desktop-agnostic python-desktopcouch
  python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools
  python-feedparser python-gconf python-glade2 python-gmenu python-gnome2
  python-gnomedesktop python-gnomekeyring python-gnupginterface python-gobject
  python-gst0.10 python-gtk2 python-gtksourceview2 python-gtkspell
  python-httplib2 python-ibus python-imaging python-indicate python-kde4
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-libxml2 python-louis python-mako python-minimal
  python-newt python-notify python-oauth python-openssl python-packagekit
  python-pam python-paramiko python-pexpect python-problem-report
  python-protobuf python-pyatspi python-pycurl python-pygoocanvas
  python-pyinotify python-pyorbit python-qt4 python-rdflib python-rsvg
  python-serial python-simplejson python-sip python-smbc
  python-software-properties python-speechd python-telepathy
  python-twisted-bin python-twisted-core python-twisted-names
  python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol
  python-uno python-utidylib python-virtkey python-vobject python-vte
  python-wadllib python-webkit python-wnck python-xapian python-xdg
  python-xkit python-zope.interface python2.6 python2.6-minimal qbittorrent
  quadrapassel rdesktop rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugins rpm rpm2cpio rsync rsyslog samba-common samba-common-bin
  sat4j screen-resolution-extra seahorse simple-scan smbclient software-center
  software-properties-gtk software-properties-kde soprano-daemon sox
  speech-dispatcher splix swfdec-mozilla synaptic syslinux
  system-config-printer-common system-config-printer-udev
  system-tools-backends sysvinit-utils tcl tcpdump telepathy-gabble
  telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut
  tomboy toshset totem totem-common totem-mozilla totem-plugins transcode
  transmission-common transmission-gtk ttf-droid ttf-kacst-one
  ttf-khmeros-core ttf-lao ttf-liberation ttf-mscorefonts-installer
  ttf-opensymbol ttf-takao-pgothic ttf-thai-tlwg ttf-umefont ttf-unfonts-core
  ubufox ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-system-service
  ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome udev udisks ufw
  unixodbc uno-libs3 update-manager update-manager-core update-manager-kde
  update-notifier update-notifier-common upower upstart ure ureadahead
  usb-creator-common usb-creator-gtk usbmuxd usbutils util-linux uuid-runtime
  vbetool vim-common vim-tiny vinagre vino virtuoso-nepomuk vlc vlc-data
  vlc-nox vlc-plugin-pulse w3m wget whiptail whois winbind wine wine1.2
  wireless-crda wireless-tools wpasupplicant x11-utils x11proto-core-dev xchat
  xchat-common xdg-user-dirs-gtk xkb-data xorg xscreensaver-data
  xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xz-utils yelp
  zenity zlib1g
0 upgraded, 0 newly installed, 0 to remove and 1021 not upgraded.
shane@shanes-desktop:~$ 

```

So I'm just taking shots in the dark now, I've Googled and searched around but it seems like everyone with broken packages has different ones and so far none of the terminal commands have fixed my issue.. Thanks in advance..

---

### Post by Frogs Hair on 2012-04-09
12.04 has is not final yet and upgrades go in order. The output looks like you have 10.10 and not 10.04 . That means that you would have had to upgrade from 10.10 > 11.04 > 11.10 > 12.04. This may have worked if you were using 10.04 because both 10.04 and 12.04 are long term support releases. If you did in fact start from 10.10 you may be able to complete the upgrade with a 12.04 disk. Here are a couple of commands to try without a disk.```
sudo dpkg --configure -a 
``````
sudo apt-get -f install 
```
Post any output from these commands it may help.

This is why it looks like 10.10 and not 10.04
 ```
gn cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
 Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
```

---

### Post by JDM_SOHC on 2012-04-09
> **Frogs Hair said:**
> 12.04 has is not final yet and upgrades go in order. The output looks like you have 10.10 and not 10.04 . That means that you would have had to upgrade from 10.10 > 11.04 > 11.10 > 12.04. This may have worked if you were using 10.04 because both 10.04 and 12.04 are long term support releases. If you did in fact start from 10.10 you may be able to complete the upgrade with a 12.04 disk. Here are a couple of commands to try without a disk.```
sudo dpkg --configure -a 
``````
sudo apt-get -f install 
```
Post any output from these commands it may help.

This is why it looks like 10.10 and not 10.04
 ```
gn cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
 Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
```


Hmm, when I goto system/about Ubuntu it says this "You are using Ubuntu 10.04 LTS - the Lucid Lynx released April 2010 and supported until April 2013"

And the only reason I am even in this debacle is because I just got my desktop back up an running after the power supply being bad for about 3 months (been using my laptop so wasn't to concerned about rushing it) and when I went to check for updates it said there was a new release available and I clicked Get Upgrade.. Now I'm SOL I think lol, I posted for help on another forum and one of the moderators on the site told me to enter in this code in terminal and now my terminal is continuing to say "Resolving Dependencies" over and over and over, and the open: 195 will go down to like open: 190 and right back up in #'s like it's never going to stop doing what it's doing..

He had me put this in "sudo aptitude update && sudo aptitude install gtkorphan" and that was about 15-20 minutes ago and terminal is still repeating Resolving Dependencies...

[IMG]http://i41.tinypic.com/w0sx9i.png[/IMG]

---

### Post by JDM_SOHC on 2012-04-09
Will bad things happen if I just force close this terminal window while its doing this Resolving Dependencies thing..?? This is taking far longer than I expected and I have to report back to base in less than an hour..

---

### Post by Frogs Hair on 2012-04-09
Closing the terminal will kill the running task , but you can minimize it.

---

### Post by JDM_SOHC on 2012-04-09
> **Frogs Hair said:**
> Closing the terminal will kill the running task , but you can minimize it.

when i type the command u mentioned it says its locked..

shane@shanes-desktop:~$ sudo dpkg --configure -a
[sudo] password for shane: 
dpkg: error: dpkg status database is locked by another process

---

### Post by Hylas de Niall on 2012-04-09
The naming thing must be a quirk of Ubuntu.

I'm running 10.10 on my desktop, but 'About Ubuntu' reports that i'm running 11.04 Natty! ~maybe because of updated packages or libraries? I dunno.

:lolflag:

---

### Post by JDM_SOHC on 2012-04-09
lol that is weird... oh well, I guess I just have to let this Resolving Dependencies thing run and run and run..

---

### Post by anewguy on 2012-04-09
Chances are quite high that will run for an extended period of time.

And, while it's too late for you, for others reading this thread and considering the upgrade path:

- your BEST option is to backup any thing you need, then do a complete install of the next release.

There has been an option that is supposed to work for just doing the upgrade itself, but myself and MANY others have run into problems doing so, with the end result being an install anyway.

Save some headaches, back up what you need, burn a LiveCD or USB flash drive with the new release and INSTALL that release.  This also gives you a chance to re-do partitions if you need to - perhaps a separate /home or /boot or what ever, or perhaps you want to resize or change the type to ext4, etc..

The upgrade has always left "garbage" in its' wake in terms of old libraries, old support files, etc..  This is what ends up causing the problems.

As for your current problem, JDM_SOHC, just let it run and see what your end result is.  You may need to do an install also before all is said and done.

If the upgrade process has been vastly improved for going to 12.04, then I apologize to anyone involved with it for my comments.  I know from personal experience and from a lot of others on the forum this has been a problem issue in the past.

Dave ;)

---

### Post by edm1 on 2012-04-09
To upgrade a server you run

```
sudo apt-get install update-manager-core
sudo do-release-upgrade -d
```

instead of

```
sudo update-manager -d
```

Could this be the problem?

---

### Post by Frogs Hair on 2012-04-09
```
when i type the command u mentioned it says its locked..

 shane@shanes-desktop:~$ sudo dpkg --configure -a
 [sudo] password for shane: 
 dpkg: error: dpkg status database is locked by another process
```

That means a process is already running . The last post on previous page is very important though.

---

### Post by linxuser14 on 2012-06-16
A thought on all this - I always keep /home on a separate partition. On upgrade via version upgrade or full reinstall, I can designate that partition for /home and previous swap partition remains the same. I can still backup my /home partition first, in case of mistakes. But /home need not be formatted during install/upgrade. I also have a hidden folder in /home/username. I call mine ~/.cached-packages with folder for the different versions I've installed. {
  ~/.cached-packages/10.04-lucid/archives
  ~/.cached-packages/11.10-natty/archives
  ...etc                           }
In each I copied /var/cache/apt/archives contents to its version's folder.
i.e.     {
   ~/.cached-packages/10.04-lucid/archives/.lock
   ~/.cached-packages/10.04-lucid/archives/partial
   ~/.cached-packages/10.04-lucid/archives/*.deb
         }
I then, in /var/cache/apt, create a symlink to it. First I rename the archives folder # sudo mv /var/cache/apt/archives /var/cache/apt/archives-original #. then # sudo ln -s /home/username/.cached-packages/10.04-lucid/archives/ ./archives
That way if I break the version and need to reinstall, It can be done with just the install cd/dvd. Re establish the symlink to the saved .cached-packages/10.04-lu...
I haven't come across a way for it to use the archive without first doing a # sudo apt-get update # though. It seems to me this method has saved me a lot of internet re-downloading and time.
  Just thought I'd share that.

---

### Post by linxuser14 on 2012-06-16
An added bit of information:
my permissions for ~/.cached-packages,
username:username   ~/.cached-packages
username:username   ~/.cached-packages/10.04-lucid
root:root           ~/.cached-packages/10.04-lucid/archives
root:root           ~/.cached-packages/10.04-lucid/archives/*

  I think the OS needs to work with its *.deb packages as root. So, if I do a # sudo chown -R username:username /home/username, I go in and check and if needed, # sudo chown -R root:root /home/username/.cached-packages/[version(s)]/archives/* # (back to root:root (owner:group))
  I sometimes end up with stuff in /home/username getting root ownership, causing problems.

  This was how I used to setup my OS. My current setup is a little more involved, so I'll not explain it as yet. I did however break my OS last night, and restored it from a tar backup. Had to do a # sudo chown -R username:username /home/username # and indeed needed to restore the /home/username/.cached-packages/archives to root ownership - # sudo chown -R root:root /home/username/.cached-packages/*
  
A thing I think is correct, but not willing to test, is if as username you attempt something that tries to alter files and folders with root ownership, contained within a folder with username ownership. The OS should prompt before doing it. Since the folder is username ownership, username can allow the changes by answering (y)es. I don't know if this applies to editing, or if it does, if it'll change the owner. But I have no reason to try and edit a *.deb file currently.

---

