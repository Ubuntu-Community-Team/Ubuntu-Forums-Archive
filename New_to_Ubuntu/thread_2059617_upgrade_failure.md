---
title: "upgrade failure"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by ddg on 2012-09-18
Hallo Ubuntu team,

I tried to upgrade my ubuntu 10.04 to 12.04. After downloading many files and unpacking all of them but it is still 10.04. The system asking to restart but it still the same. After restarting my desktop background changed and I cannot open my open office application.

Here is the error message: 

'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

Can some body help me with solving this.?
Thank you,
Deepak

---

### Post by newb85 on 2012-09-18
Hello, Deepak,

Open Office has been replaced by Libre Office.  Try using that instead.

---

### Post by jerrrys on 2012-09-18
sudo apt-get clean

sudo apt-get autoclean

sudo apt-get update

do any good?

---

### Post by newb85 on 2012-09-18
> **jerrrys said:**
> sudo apt-get clean

sudo apt-get autoclean

sudo apt-get update

do any good?

That approach should probably be finished.

```
sudo apt-get upgrade
```

---

### Post by raja.genupula on 2012-09-18
Actually Held packages can be get back with 

```
sudo apt-get dist-upgrade
```

---

### Post by ddg on 2012-09-18
> **raja.genupula said:**
> Actually Held packages can be get back with 

```
sudo apt-get dist-upgrade
```
Hallo Raja, 

 I have done what you said and below is the error message

libgl1-mesa-dri: Breaks: xserver-xorg-core (< 2:1.10.2-2) but 2:1.7.6-2ubuntu7.6 is to be installed

---

### Post by ddg on 2012-09-18
> **jerrrys said:**
> sudo apt-get clean

sudo apt-get autoclean

sudo apt-get update

do any good?
Hallo Jerry and New85,

I tried what you suggested but it gave very long error message. I cut some of it as below.
W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise/main/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise/main/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise/multiverse/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise/universe/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise/universe/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/Release.gpg](http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/main/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-security/Release.gpg](http://dl2.foss-id.web.id/ubuntu/dists/precise-security/Release.gpg)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-security/main/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-security/main/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-security/universe/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:
Thanks,

---

### Post by raja.genupula on 2012-09-18
> **ddg said:**
> Hallo Jerry and New85,

I tried what you suggested but it gave very long error message. I cut some of it as below.
W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise/main/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise/main/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise/multiverse/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise/universe/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise/universe/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/Release.gpg](http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/main/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-security/Release.gpg](http://dl2.foss-id.web.id/ubuntu/dists/precise-security/Release.gpg)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-security/main/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-security/main/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:

W: Failed to fetch [http://dl2.foss-id.web.id/ubuntu/dists/precise-security/universe/i18n/Translation-en_US.bz2](http://dl2.foss-id.web.id/ubuntu/dists/precise-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to dl2.foss-id.web.id:http:
Thanks,


for this issue , you have to give a try by changing your server from update manager settings . 

for the above issue you have to do as 

```
sudo apt-get install -f
```

---

### Post by ddg on 2012-09-18
Hallo Newb85,


> **newb85 said:**
> That approach should probably be finished.

```
sudo apt-get upgrade
```

Here is what I got:

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  acl adobe-flash-properties-gtk adobe-flashplugin aisleriot alsa-utils apparmor apparmor-utils apport apport-gtk apt apt-transport-https apt-utils
  apt-xapian-index aptdaemon aptitude apturl apturl-common aspell avahi-daemon base-files bash bash-completion bind9-host binfmt-support binutils bluez
  bluez-alsa bluez-cups bluez-gstreamer brasero brasero-common brltty bsdmainutils bzip2 ca-certificates cdparanoia-dbg cdrdao checkbox checkbox-gtk
  command-not-found compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor console-setup
  consolekit coreutils cpp cpp-4.4 cpu-checker cron cups cups-bsd cups-client cups-driver-gutenprint dbus-x11 debianutils desktop-file-utils dnsmasq-base
  dnsutils doc-base dpkg dpkg-dev dvd+rw-tools e2fslibs e2fsprogs empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia
  erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-common espeak espeak-data evince evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal file-roller firefox
  firefox-branding firefox-gnome-support fontconfig-config foo2zjs foomatic-db foomatic-db-engine friendly-recovery fuse-utils g++ g++-4.4 gawk gcalctool
  gcc gcc-4.4 gcc-4.4-base gconf2 gconf2-common gdb gedit gedit-common ggzcore-bin ghostscript ghostscript-x gimp gimp-data gnome-bluetooth
  gnome-control-center gnome-disk-utility gnome-doc-utils gnome-icon-theme gnome-keyring gnome-media gnome-menus gnome-nettool gnome-orca
  gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor
  gnome-terminal gnome-terminal-data gnome-user-guide gnome-user-share gnomine grub grub-common gstreamer0.10-alsa gstreamer0.10-gnonlin gstreamer0.10-nice
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x
  gtk2-engines gtk2-engines-murrine gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse gwenview gwibber gwibber-service hpijs hplip hplip-data
  ibus ibus-gtk ibus-table ifupdown imagemagick indicator-application indicator-messages indicator-session indicator-sound info initscripts inkscape
  intel-gpu-tools iproute iptables iputils-ping jockey-common jockey-gtk kbd kdebase-runtime kdelibs-bin kdelibs5-data kdepimlibs5 kdesudo
  kubuntu-debug-installer language-selector-common launchpad-integration lftp libaa1 libacl1 libapparmor-perl libapt-inst1.4 libapt-pkg4.12 libart2.0-cil
  libasound2 libasound2-plugins libaspell15 libatasmart4 libatk1.0-0 libatm1 libattr1 libaudio2 libavahi-client3 libavahi-common3 libavahi-compat-libdnssd1
  libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libblkid1 libbluetooth3 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbsd0 libbz2-1.0
  libc-bin libc-dev-bin libc6 libc6-dev libcaca0 libcairo-perl libcairo2 libcairomm-1.0-1 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse
  libcanberra0 libcap2 libcdparanoia-dev libcdparanoia0 libclutter-1.0-0 libcomerr2 libcompizconfig0 libcompress-raw-zlib-perl libcroco3 libcups2
  libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libcwidget3 libdatrie1 libdb4.8 libdbus-1-3 libdbus-glib-1-2
  libdbusmenu-qt2 libdc1394-22 libdiscid0 libdjvulibre21 libdrm-intel1 libdrm-radeon1 libdrm2 libdv4 libedit2 libelf1 libenchant1c2a libesd0 libespeak1
  libexempi3 libexif12 libexpat1 libflac8 libflite1 libfontconfig1 libfreetype6 libfuse2 libgadu3 libgail-common libgail18 libgcc1 libgconf2-4
  libgconf2.0-cil libgcrypt11 libgd2-xpm libgdbm3 libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libgfortran3 libggz2 libggzcore9 libggzmod4 libgif4
  libgimp2.0 libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglade2.0-cil libglib-perl libglib2.0-0 libglib2.0-cil libglibmm-2.4-1c2a
  libglu1-mesa libgnome-desktop-2-17 libgnome-keyring0 libgnome-vfs2.0-cil libgnome2-0 libgnome2-common libgnome2.24-cil libgnomecanvas2-0
  libgnomekbd-common libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgnutls26 libgomp1 libgpg-error0 libgpgme11 libgphoto2-2
  libgphoto2-port0 libgpm2 libgpod-common libgpod4 libgssapi-krb5-2 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-vnc-1.0-0 libgtk2-perl
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkmm-2.4-1c2a libgudev-1.0-0 libgutenprint2 libgweather-common libhpmud0 libhtml-parser-perl
  libice6 libidl0 libidn11 libido-0.1-0 libiec61883-0 libieee1284-3 libjack0 libjasper1 libjson-glib-1.0-0 libk5crypto3 libkeyutils1 libkrb5-3
  libkrb5support0 liblapack3gf liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblcms1 libldap-2.4-2 liblocale-gettext-perl liblockfile1
  libloudmouth1-0 libltdl7 liblzo2-2 libmad0 libmetacity-private0 libmng1 libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-i18n-west2.0-cil libmono-i18n2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-runtime2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libncurses5 libncursesw5
  libneon27 libneon27-gnutls libnewt0.52 libnih-dbus1 libnih1 libnss3-1d libogg0 libopenal1 liborc-0.4-0 libotr2 libpam-modules libpam0g libpango-perl
  libpango1.0-0 libpangomm-1.4-1 libparted0debian1 libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1 libphonon4 libpisock9 libpixman-1-0 libplasma3
  libplymouth2 libpng12-0 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpopt0 libportaudio2 libpst4 libpulse-mainloop-glib0 libpulse0
  libpurple0 libqca2 libqt4-dbus libqt4-designer libqt4-gui libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools
  libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraw1394-11 librdf0 libreadline5 libreadline6
  librpc-xml-perl librsvg2-2 librsvg2-common libruby libruby1.8 libsamplerate0 libsane libsasl2-2 libsasl2-modules libschroedinger-1.0-0 libsdl1.2debian
  libselinux1 libsensors4 libsepol1 libshout3 libsigc++-2.0-0c2a libslang2 libsm6 libsmbclient libsndfile1 libsnmp15 libsoprano4 libsoup-gnome2.4-1
  libsoup2.4-1 libspectre1 libspeex1 libspeexdsp1 libsqlite3-0 libss2 libssh-4 libstartup-notification0 libstdc++6 libstdc++6-4.4-dev libstreamanalyzer0
  libstreams0 libsub-name-perl libtag1-vanilla libtag1c2a libtalloc2 libtasn1-3 libtdb1 libtelepathy-glib0 libterm-readkey-perl libtext-charwidth-perl
  libtext-iconv-perl libthai0 libtheora0 libtiff4 libtotem-plparser17 libudev0 libunique-1.0-0 libusb-0.1-4 libusb-1.0-0 libuuid-perl libuuid1 libv4l-0
  libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common libvte9 libwavpack1 libwbclient0 libwmf0.2-7 libwmf0.2-7-gtk
  libwnck22 libwrap0 libwww-perl libx11-6 libx11-data libxau6 libxaw7 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxcomposite1
  libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxml-libxml-perl libxml-parser-perl libxml-sax-perl libxml2 libxmu6
  libxmuu1 libxp6 libxpm4 libxrandr2 libxrender1 libxslt1.1 libxss1 libxt6 libxtst6 libxv1 libxxf86vm1 light-themes linux-generic linux-headers-generic
  linux-image-generic logrotate lsb-release man-db metacity metacity-common min12xxw modemmanager module-init-tools mono-gac mono-runtime mount mountall
  mousetweaks nano nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share ncurses-bin network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome notify-osd ntfs-3g ntpdate nvidia-common obex-data-server obexd-client odbcinst onboard
  openoffice.org-calc openoffice.org-common openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-hyphenation-en-us openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-thesaurus-en-au openoffice.org-thesaurus-en-us openoffice.org-writer openprinting-ppds openssh-client openssl parted passwd pciutils
  pcmciautils perl perl-base perl-modules perlmagick phonon pidgin pidgin-data pidgin-libnotify pitivi pkg-config plasma-scriptengine-javascript plymouth
  plymouth-label pnm2ppa policykit-1 policykit-1-gnome polkit-kde-1 poppler-utils ppp procps protobuf-compiler psmisc pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr python python-appindicator python-apport python-apt
  python-aptdaemon python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-cups python-cupshelpers python-dbus
  python-debian python-egenix-mxdatetime python-egenix-mxtools python-evolution python-gconf python-gdbm python-glade2 python-gmenu python-gnome2
  python-gnomedesktop python-gnomekeyring python-gnupginterface python-gobject python-gst0.10 python-gtk2 python-gtop python-httplib2 python-ibus
  python-imaging python-kde4 python-launchpad-integration python-launchpadlib python-lazr.restfulclient python-lazr.uri python-libxml2 python-louis
  python-lxml python-mako python-metacity python-minimal python-newt python-notify python-numpy python-oauth python-openssl python-packagekit python-pam
  python-pexpect python-problem-report python-protobuf python-pycurl python-pygoocanvas python-pyinotify python-pyorbit python-qt4 python-rdflib
  python-renderpm python-reportlab python-reportlab-accel python-rsvg python-serial python-simplejson python-sip python-smbc python-software-properties
  python-speechd python-totem-plparser python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client
  python-ubuntuone-storageprotocol python-uniconvertor python-uno python-virtkey python-vte python-wadllib python-webkit python-wnck python-xapian
  python-xdg python-xkit python-zope.interface rdesktop rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rsync rsyslog ruby ruby1.8 samba-common
  samba-common-bin screen-resolution-extra seahorse simple-scan skype smbclient software-center software-properties-gtk software-properties-kde
  soprano-daemon speech-dispatcher splix syslinux system-config-printer-common system-config-printer-udev sysvinit-utils tcpdump telepathy-gabble
  telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut thunderbird thunderbird-locale-en-gb toshset totem totem-common totem-mozilla
  totem-plugins transmission-common transmission-gtk ttf-arabeyes ttf-arphic-uming ttf-liberation ttf-opensymbol ttf-thai-tlwg ubuntu-desktop ubuntu-docs
  ubuntu-minimal ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome udev udisks ufw unixodbc uno-libs3 update-manager
  update-manager-core update-manager-kde update-notifier update-notifier-common upower upstart ure ureadahead usb-creator-common usb-creator-gtk usbmuxd
  usbutils util-linux uuid-runtime vbetool vim-common vim-tiny vino virtuoso-nepomuk vorbis-tools w3m wget whiptail whois wireless-crda wireless-tools
  wpasupplicant x11-utils xdg-user-dirs-gtk xkb-data xorg xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xterm xz-utils yelp zenity zlib1g
0 upgraded, 0 newly installed, 0 to remove and 848 not upgraded.

Thanks:

---

### Post by 123076007 on 2012-09-18
root@ubuntu:~# apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



Hello
I am trying to update using terminal

I get the following message.

What am I doing wrong.

I have to use a proxy 

i have edit apt.conf with my proxy settings along with username:password@proxy:port

---

### Post by newb85 on 2012-09-18
> **123076007 said:**
> root@ubuntu:~# apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



Hello
I am trying to update using terminal

I get the following message.

What am I doing wrong.

I have to use a proxy 

i have edit apt.conf with my proxy settings along with username:password@proxy:port

This probably means another instance of an installer or updater is already running on your system.  (Perhaps updates in the background?)  Two instances are not allowed.

---

### Post by jerrrys on 2012-09-18
ddg:

Please post the output of:

gedit /etc/apt/sources.list

123076007:

You should start your own thread, but to answer your question:

you have another package manager open (maybe the software center), close it and then apt-get update.

---

### Post by raja.genupula on 2012-09-19
> **123076007 said:**
> root@ubuntu:~# apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



OK in this to get rid of the first issue  
```
sudo rm -rf /var/lib/apt/lists/lock
```
and for the second issue 
```
sudo rm -rf /var/lib/dpkg/lock 
```

---

### Post by ddg on 2012-09-22
Hallo Ubuntu team,

This case is closed, I tried to upgrade again on the next day from the update manager and finally it worked.

Thanks,
Deepak

---

