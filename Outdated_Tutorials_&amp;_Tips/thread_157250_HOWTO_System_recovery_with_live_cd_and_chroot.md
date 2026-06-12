---
title: "HOWTO: System recovery with live cd and chroot"
date: 2006-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by tuxcantfly on 2006-04-08
Let's say your system just melted down after an upgrade, or your new kernel won't boot. You can't fix the problem with apt-get, because you can't even get to a command line; the kernel just spews out errors and hangs on bootup. Thankfully, with a live cd, you can repair your system and get it up and running. You have 2 options for the live cd: Knoppix or the Ubuntu live cd. Since Knoppix generally has better hardware detection, this will be used as an example.
First, download the iso from [http://www.knoppix.org/](http://www.knoppix.org/) and burn it to a disk.
Get your BIOS set up to boot from the cd, pop in the Knoppix disk, and boot.
Your hard drive should show up on the KDE desktop as hda1 or sdb2 or something, depending on your system.
Click on it to mount it, then right-click, actions -> change to read-write mode. It'll pop open a dialog; click yes.
Now, open a root terminal, found in the Knoppix menu (the one next to the K on the panel).
Enter: chroot /mnt/hda1 or whatever the icon for your harddrive says on the desktop.
You can now use all the commands on the hard drive, including apt-get.
If you ever get this error: /dev/null: Permission denied, do this: rm /dev/null and it should go away.
Now, use apt-get to upgrade your kernel (apt-get install linux-386) (or whatever processor you're using), udev (apt-get install udev), or anything else that's messing up your system.
Reboot, and enjoy your newly rescued system!

---

### Post by sufehmi on 2008-07-03
How do you thank someone here ? Can't find the link anywhere.

[Tuxcantfly]("http://ubuntuforums.org/member.php?u=79823")'s post may very well safe my home computer. 

I was upgrading from Feisty, but the upgrade process was botched. Can't even boot from the disk properly.

Found this post, and now I'm on the halfway fixing it.

Thanks !

---

### Post by thunderdan on 2010-08-29
My computer gets stuck on the Ubuntu 10.04 splash screen. The dots continue to flash red and white in sequence, and don't freeze, but it stays on this screen for hours with no hard drive activity, so I hold the power button to turn the computer off. I turn it back on and hold the shift key to get the Grub2 menu, and I choose Ubuntu, with Linux 2.6.32-24-generic (recovery mode). Lots of stuff scrolls across the screen and it eventually freezes with the following listed on the screen:

```
Begin: Loading essential drivers... ...
Done.
Begin: Running /scripts/init-premount...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local-top ...
Done.
Begin: Running /scripts/local-premount ...
Done.
[    1.999947] EXT4-fs (sda1): mounted filesystem with ordered data mode
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
[    2.114623] usb 4-1: configuration #1 chosen from 1 choice
Done.
[    2.372017] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    2.586383] usb 5-1: configuration #1 chosen from 1 choice
[    2.832020] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    3.009435] usb 5-2: configuration #1 chosen from 1 choice
mountall: error while loading shared libraries: /lib/libudev.so.0: invalid ELF header
init: mountall main process (310) terminated with status 127
```

The number in parenthesis on the last line seems to be different each time, but the status is always 127.

I don't know what the file /lib/libudev.so.0 is for or how to fix it. I booted a Knoppix 6.2 live CD and opened a root terminal. Here is how that went:

```
root@Microknoppix:/home/knoppix# chroot /mnt/sda1
root@Microknoppix:/# apt-get install linux-386
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.32-24-386 linux-image-386
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-386 linux-image-2.6.32-24-386 linux-image-386
0 upgraded, 3 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/31.3MB of archives.
After this operation, 99.0MB of additional disk space will be used.
Do you want to continue [Y/n]?
debconf: Perl may be unconfigured (Unrecognized character \xFF in
column 1 at /usr/share/perl/5.10/warnings.pm line 1.
Compilation failed in require at /usr/lib/perl/5.10/IO.pm line 8.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO.pm line 8.
Compilation failed in require at /usr/lib/perl/5.10/IO/Handle.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/Handle.pm line 9.
Compilation failed in require at /usr/lib/perl/5.10/IO/Seekable.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/Seekable.pm line 9.
Compilation failed in require at /usr/lib/perl/5.10/IO/File.pm line 11.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/File.pm line 11.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package linux-image-2.6.32-24-386.
(Reading database ... 70%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'openprinting-ppds' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@Microknoppix:/# apt-get install udev
Reading package lists... Done
Building dependency tree
Reading state information... Done
udev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
root@Microknoppix:/# apt-get remove udev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 x11proto-resource-dev libpopt-dev libclucene0ldbl
liborbit2-dev menu python-awn-extras dvdrip-doc libqca2 dvgrab
libqt4-assistant bzrtools
  lincity-ng-data libtasn1-3-dev libpackagekit-glib2-12 libg15render1
dia-libs libatk1.0-dev debhelper swh-plugins libaudiofile-dev
linux-headers-2.6.32-16
  x11proto-fonts-dev libxcb-keysyms1 intltool-debian
libevent-execflow-perl kdenlive-data x11proto-xf86dga-dev
x11proto-kb-dev libyaml-syck-perl
  libdesktop-agnostic0 libgpg-error-dev warzone2100-music libdiscid0
libnet-ssleay-perl python-paramiko libcvaux4 twolame
openoffice.org-java-common
  dvdrip-utils vcdimager x11proto-xinerama-dev fortunes-min libsvga1
libanyevent-perl qalc oxygen-icon-theme libboost-program-options1.40.0
libqof2
  libqt4-test x11proto-bigreqs-dev libqt4-sql-mysql libqt4-dbus
x11proto-render-dev libintl-perl libgcrypt11-dev libxcb-xv0
x11proto-video-dev libavidemux0
  libsox-fmt-ao shared-desktop-ontologies audacity-data amarok-common
qof-data po-debconf libflac++6 libcddb2 transcode-utils python-awn
transcode-doc
  libgnome-keyring-dev libboost-thread1.40.0 libpciaccess-dev
fortune-mod libxine1-bin libxdmcp-dev libsysfs-dev libdirectfb-extra
libavahi-client-dev
  libcln6 frei0r-plugins libawn1 tcl8.4-dev libsox-fmt-ffmpeg
libpng12-dev libdvbpsi5 grub-pc python-utidylib wisotool
libparse-yapp-perl python-configobj
  libxosd2 libfontconfig1-dev libpackagekit-qt-12
libmail-sendmail-perl libasync-interrupt-perl x11proto-record-dev
libakonadiprivate1 libqt4-xmlpatterns
  libtorrent-rasterbar5 libsoprano4 libdmx1 librecode0
libqtscript4-core libvlc2 libdesktop-agnostic-vfs-gio libtidy-0.99-0
gettext x11proto-dmx-dev
  linux-headers-2.6.32-16-generic libbonobo2-dev libqalculate4
libxine1-ffmpeg python-sip kdelibs5-data winetricks vlc-nox bzr cvs
libgnutls-dev
  libdesktop-agnostic-fdo-glib x11proto-scrnsaver-dev
libevent-rpc-perl ogmtools x11proto-xf86bigfont-dev libmikmod2
x11proto-randr-dev libdrm-dev libupnp3
  libdbus-1-dev qt4-qmake libxcb-shape0 libgavl1 libglc0
python-desktop-agnostic avidemux-common libwxbase2.8-0 gnuplot-nox
libjpeg62-dev lsdvd
  libqt4-sql-sqlite python-feedparser libqof2-backend-qsf
avant-window-navigator-data sauerbraten-data libao2 libwmf-bin
liblzo2-2 python-rsvg libavfilter0
  libxml2-dev libqt4-sql libidl-dev libfreetype6-dev libart-2.0-dev
libesd0-dev fping netpbm python-dateutil libcv4 libsox-fmt-mp3
libpthread-stubs0-dev
  libg15daemon-client1 libdate-manip-perl ttf-symbol-replacement
python-packagekit libstreamanalyzer0 os-prober libiso9660-7
libsox-fmt-base
  libpthread-stubs0 sox wine1.2-gecko libqtscript4-sql libqt4-network
libsox-fmt-oss nexuiz-textures libiv1 nexuiz-data libhighgui4 psutils
gocr
  libsox-fmt-alsa libexpat1-dev libqtscript4-xml libevent-perl
libattica0 libg15-1 liblua5.1-0 libcinelerra x11proto-xf86vidmode-dev
libmpg123-0
  libnetpbm10 libselinux1-dev python-imaging-dbg filezilla-common
python-vobject openoffice.org-l10n-en-gb libhsqldb-java libstreams0
html2text
  libservlet2.5-java vlc-data libboost-filesystem1.40.0
libpixman-1-dev packagekit-backend-apt libiv-unidraw1 libtag-extras1
libtar
  libgtk2-ex-formfactory-perl libxml-regexp-perl winbind grub-common
libphysfs1 liblastfm0 libqt4-script libsox1a orbit2 libavahi-glib-dev
libmlt-data
  libavahi-common-dev libcommon-sense-perl x11proto-xcmisc-dev
libjpeg-progs libssh-4 virtuoso-nepomuk libxcb-shm0 python-chardet
libvlccore2 lame
  libgraphviz4 soprano-daemon x11proto-xf86dri-dev libsepol1-dev
libvcdinfo0 amarok-utils kdebase-runtime-data libebml0
libboost-system1.40.0 libreadline5
  libiodbc2 kdepimlibs-data libqtscript4-network
libsys-hostname-long-perl libmatroska0 warzone2100-data nexuiz-music
libxine1-console libmusicbrainz3-6
  libavdevice52 python-indicate libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpackagekit-glib2-12
The following packages will be REMOVED:
  acpi-support acpid aisleriot alsa-base alsa-utils amarok anacron
apparmor apparmor-utils apport apport-gtk apport-hooks-medibuntu
aptdaemon apturl at
  at-spi audacity avahi-daemon avahi-utils avant-window-navigator
avidemux avidemux-plugins-common avidemux-plugins-gtk
awn-applets-c-core
  awn-applets-python-core awn-settings bluez bluez-cups brasero
brasero-common brltty brltty-x11 capplets-data checkbox checkbox-gtk
cheese cheese-common
  cinelerra compiz compiz-core compiz-fusion-plugins-main compiz-gnome
compiz-plugins compizconfig-backend-gconf computer-janitor-gtk
console-setup
  consolekit couchdb-bin cron cryptsetup cups cups-driver-gutenprint
dbus dbus-x11 desktopcouch devede dia-common dia-gnome dkms dmsetup
dvdauthor dvdrip
  e2fsprogs ecryptfs-utils empathy empathy-common eog erlang-base
erlang-crypto erlang-inets erlang-mnesia erlang-public-key
erlang-runtime-tools
  erlang-ssl erlang-syntax-tools erlang-xmerl evince evolution
evolution-couchdb evolution-data-server evolution-exchange
evolution-indicator
  evolution-plugins evolution-webcal f-spot ffmpeg file-roller
filezilla firefox firefox-branding firefox-gnome-support firestarter
flashplugin-installer
  flashplugin-nonfree foo2zjs foomatic-db foomatic-db-engine
friendly-recovery ftp gbrainy gcalctool gconf-defaults-service
gconf-editor gconf2
  gconf2-common gdebi gdebi-kde gdm gdm-guest-session
gecko-mediaplayer gedit ghostscript-cups ghostscript-x gimp gksu
gnome-about gnome-applets
  gnome-applets-data gnome-blackjack gnome-bluetooth
gnome-codec-install gnome-control-center gnome-disk-utility
gnome-exe-thumbnailer gnome-games-common
  gnome-keyring gnome-mag gnome-mahjongg gnome-media
gnome-media-common gnome-mplayer gnome-nettool gnome-orca gnome-panel
gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session
gnome-session-bin gnome-session-canberra gnome-settings-daemon
gnome-sudoku gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-terminal-data
gnome-user-guide gnome-user-share gnome-utils gnomine gnotime
gnuplot-x11 goobox googleearth groff
  gsfonts-x11 gstreamer0.10-gnomevfs
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good
gstreamer0.10-pulseaudio gtk-recordmydesktop gucharmap
  gvfs gvfs-backends gvfs-bin gvfs-fuse gwibber-service hal hostname
hplip hplip-cups ibus ibus-m17n ibus-table icedtea6-plugin icoutils
idle-python2.6
  ifupdown imagemagick indicator-applet indicator-applet-session
indicator-me indicator-session indicator-sound initramfs-tools
initscripts inkscape
  install-package irqbalance ivtools-bin jockey-common jockey-gtk kbd
kdebase-runtime kdelibs-bin kdelibs5 kdemultimedia-kio-plugins
kdenlive kdepimlibs5
  kdesudo kpackagekit kubuntu-debug-installer language-selector lftp
libasound2-plugins libatspi1.0-0 libaudio2 libbonoboui2-0
libbonoboui2-dev
  libbrasero-media0 libcairo2-dev libcamel1.2-14 libcanberra-pulse
libcheese-gtk18 libcompizconfig0 libcouchdb-glib-1.0-2 libcryptui0
libdbusmenu-qt2
  libdesktop-agnostic-cfg-gconf libdesktopcouch-glib-1.0-2
libdirectfb-dev libdmx-dev libebackend1.2-0 libebook1.2-9 libecal1.2-7
libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8
libegroupwise1.2-13 libexchange-storage1.2-3 libfontenc-dev libfs-dev
libgail-dev
  libgail-gnome-module libgconf2-4 libgconf2-dev libgconf2.0-cil
libgdata6 libgdu0 libgegl-0.0-0 libgksu2-0 libgl1-mesa-dev
libglu1-mesa-dev
  libgnome-desktop-2-17 libgnome-media0 libgnome-pilot2
libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
libgnome2-common libgnome2-dev
  libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil
libgnomecanvas2-dev libgnomekbd-common libgnomekbd4
libgnomepanel2.24-cil libgnomeui-0 libgnomeui-dev
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-dev
libgnomevfs2-extra libgstfarsight0.10-0 libgtk2.0-dev
libgtkhtml-editor0 libgtkhtml3.14-19
  libgweather-common libgweather1 libice-dev libice6
libio-socket-ssl-perl libkcddb4 liblpint-bonobo0 libm17n-0
libmagick++2 libmagickcore2
  libmagickcore2-extra libmagickwand2 libmetacity-private0
libmjpegtools-1.9 libmlt++3 libmlt2 libnet-dbus-perl libnss-mdns
liboobs-1-4 libpanel-applet2-0
  libpango1.0-dev libphonon4 libplasma3 libplot2c2 libpolkit-gtk-1-0
libpolkit-qt-1-0 libpstoedit0c2a libpulse-browse0
libpulse-mainloop-glib0 libpulse0
  libpurple0 libqt3-mt libqt4-designer libqt4-dev libqt4-help
libqt4-multimedia libqt4-opengl libqt4-opengl-dev libqt4-qt3support
libqt4-scripttools
  libqt4-svg libqt4-webkit libqtgui4 libqtscript4-gui
libqtscript4-uitools librpc-xml-perl libsdl-gfx1.2-4 libsdl-image1.2
libsdl-mixer1.2 libsdl-net1.2
  libsdl-ttf2.0-0 libsdl1.2debian libsdl1.2debian-pulseaudio libsm-dev
libsm6 libsmpeg0 libsoup-gnome2.4-1 libsox-dev libsox-fmt-all
libsox-fmt-pulse
  libstartup-notification0 libtelepathy-farsight0 libubuntuone-1.0-1
libwebkit-1.0-2 libwnck22 libwww-perl libwxgtk2.8-0 libx11-dev
libxau-dev libxaw7
  libxaw7-dev libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev
libxcomposite-dev libxcursor-dev libxdamage-dev libxext-dev
libxfixes-dev libxfont-dev
  libxft-dev libxi-dev libxine1 libxine1-misc-plugins libxine1-x
libxinerama-dev libxkbfile-dev libxklavier16 libxml-dom-perl
libxml-parser-perl
  libxml-perl libxml-sax-expat-perl libxml-twig-perl libxml-xpath-perl
libxml-xql-perl libxmu-dev libxmu-headers libxmu6 libxmuu-dev
libxpm-dev
  libxrandr-dev libxrender-dev libxres-dev libxres1 libxss-dev libxss1
libxt-dev libxt6 libxtst-dev libxtst6 libxv-dev libxvmc-dev libxvmc1
libxxf86dga-dev
  libxxf86dga1 libxxf86vm-dev light-themes lincity-ng linux-generic
linux-image-2.6.32-16-generic linux-image-2.6.32-22-generic
  linux-image-2.6.32-23-generic linux-image-2.6.32-24-generic
linux-image-generic linux-sound-base logrotate m17n-contrib m17n-db
mangler media-player-info
  melt mencoder mesa-common-dev metacity metacity-common mjpegtools
module-init-tools mountall mousetweaks mplayer nautilus nautilus-data
nautilus-sendto
  nautilus-sendto-empathy nautilus-share netbase network-manager
network-manager-gnome network-manager-pptp network-manager-pptp-gnome
nexuiz notify-osd
  ntfs-3g ntpdate nvidia-current nvidia-settings obex-data-server
onboard openjdk-6-jre openoffice.org-base openoffice.org-base-core
openoffice.org-calc
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-math
openoffice.org-writer openprinting-ppds packagekit pcmciautils
perlmagick phonon
  phonon-backend-xine plasma-scriptengine-javascript plymouth
plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
plymouth-x11 pm-utils
  pm-utils-powersave-policy policykit-1 policykit-1-gnome polkit-kde-1
powermgmt-base ppp pppconfig pppoeconf pptp-linux procps pstoedit
pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth
pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr
python-aptdaemon
  python-aptdaemon-gtk python-desktopcouch python-desktopcouch-records
python-farsight python-gconf python-gnome2 python-gnomeapplet
python-gnomedesktop
  python-gweather python-imaging-tk python-imaging-tk-dbg python-kde4
python-papyon python-pyatspi python-qt4 python-speechd python-tk
python-tk-dbg
  python-ubuntuone python-uno python-virtkey python-webkit python-wnck
qalculate qalculate-gtk qbittorrent qhimdtransfer qjackctl qtpfsgui
quadrapassel
  rawstudio recordmydesktop rhythmbox rhythmbox-plugin-cdrecorder
rhythmbox-plugins rhythmbox-ubuntuone-music-store rsyslog samba
sauerbraten
  sauerbraten-wake6 screen-resolution-extra screensaver-default-images
scribus seahorse simple-scan software-center software-properties-gtk
  software-properties-kde soundconverter speech-dispatcher splix
subtitleripper sun-java6-plugin system-config-printer-gnome
system-tools-backends
  telepathy-butterfly telepathy-haze telepathy-salut telnet tgif
tk8.4-dev tk8.5 tomboy totem totem-common totem-mozilla totem-plugins
transcode transfig
  tsclient ttf-mscorefonts-installer ubufox ubuntu-artwork
ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-standard
ubuntu-system-service
  ubuntu-wallpapers ubuntuone-client-gnome udev udisks ufw
update-manager update-manager-kde update-notifier upower upstart
ureadahead usb-creator-common
  usb-creator-gtk util-linux vinagre vino virtualbox-3.2 vlc
vlc-plugin-pulse wacom-dkms warzone2100 wine wine1.2 winff winff-doc
wireless-crda
  x-ttcidfont-conf x11-apps x11-common x11-session-utils x11-utils
x11-xfs-utils x11-xkb-utils x11-xserver-utils x11proto-composite-dev
x11proto-damage-dev
  x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev
x11proto-xext-dev xfonts-100dpi xfonts-75dpi xfonts-base
xfonts-encodings xfonts-mathml
  xfonts-scalable xfonts-utils xine-ui xinit xorg xorg-dev
xscreensaver-data xscreensaver-gl xserver-common xserver-xorg
xserver-xorg-core xserver-xorg-dev
  xserver-xorg-input-all xserver-xorg-input-evdev
xserver-xorg-input-mouse xserver-xorg-input-synaptics
xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark
xserver-xorg-video-ati xserver-xorg-video-chips
xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-geode
xserver-xorg-video-i128 xserver-xorg-video-i740
xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
xserver-xorg-video-nouveau xserver-xorg-video-nv
xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition
xserver-xorg-video-s3 xserver-xorg-video-s3virge
xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
xserver-xorg-video-sisusb xserver-xorg-video-tdfx
xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l
xserver-xorg-video-vesa xserver-xorg-video-vmware
xserver-xorg-video-voodoo xterm xtrans-dev
  xulrunner-1.9.2 yelp
The following packages will be upgraded:
  libpackagekit-glib2-12
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
1 upgraded, 0 newly installed, 651 to remove and 4 not upgraded.
Need to get 0B/150kB of archives.
After this operation, 2620MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] no
Abort.
root@Microknoppix:/#

```

Any ideas on what I should do?

---

### Post by rajulbhavsar on 2010-11-29
I tried to recover Ubuntu 10.10, but failed. Please look into the thread 
[http://ubuntuforums.org/showthread.php?p=10172858#post10172858]("http://ubuntuforums.org/showthread.php?p=10172858#post10172858")

---

