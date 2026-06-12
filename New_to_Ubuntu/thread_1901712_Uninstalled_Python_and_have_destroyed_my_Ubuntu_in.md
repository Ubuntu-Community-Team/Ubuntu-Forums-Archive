---
title: "Uninstalled Python and have destroyed my Ubuntu install"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by SNIFFER_dog on 2011-12-29
Hi Ubuntu community,

I have been trying to get Python to work with some modules from a book I'm reading. Anyway I decided to uninstal python and reinstall to try and start again, however I have removed some important files that were obviously used by Ubuntu and have bust my install.

When I boot now I get too the new unity login screen but with many options missing and a black background. When I try and login from here it tries then comes back to the login screen.

I can however login as root at the command line only.

Does anyone know what python files, libuaries I need to install so I can try and fix this?

Any help would be very much appreciated.

Kind regards

SNIFFY.

---

### Post by nothingspecial on 2011-12-29
Hi, this is what apt want's to remove along with python from my system

```
  aisleriot alacarte apparmor apport apport-gtk apt-xapian-index aptdaemon
  apturl apturl-common banshee-extension-ubuntuonemusicstore bluez bluez-alsa
  bluez-gstreamer c2esp caribou checkbox checkbox-gtk comix command-not-found
  compiz compiz-gnome compiz-plugins-main compiz-plugins-main-default
  compizconfig-backend-gconf compizconfig-settings-manager deja-dup duplicity
  evolution-data-server firefox firefox-globalmenu firefox-gnome-support
  foo2zjs foomatic-db-compressed-ppds gconf2 gedit gir1.2-mutter-3.0 gksu
  gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install
  gnome-control-center gnome-media gnome-orca gnome-panel gnome-panel-data
  gnome-search-tool gnome-session gnome-session-fallback gnome-shell
  gnome-sudoku gnome-terminal gnome-terminal-data gnome-themes-standard
  gnome-user-share gstreamer0.10-gconf gucharmap gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hplip hplip-data ibus ibus-pinyin ibus-table indicator-datetime
  indicator-power jockey-common jockey-gtk language-selector-common
  language-selector-gnome launchpad-integration libcompizconfig0 libgksu2-0
  libgnome-media-profiles-3.0-0 libgnome2-common libgnomevfs2-0
  libgnomevfs2-common libgweather-3-0 libgweather-common libgwibber-gtk2
  libgwibber2 libmetacity-private0 libmutter0 libpurple-bin
  libreoffice-emailmerge libreoffice-gnome libsyncdaemon-1.0-1
  libubuntuone-1.0-1 libubuntuone1.0-cil libunity-2d-private0 light-themes
  lsb-release metacity metacity-common mutter-common nautilus-share
  network-manager-gnome nvidia-common onboard oneconf openprinting-ppds
  pastebinit ptouch-driver pxljr python python-appindicator python-apport
  python-apt python-apt-common python-aptdaemon python-aptdaemon-gtk
  python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-brlapi
  python-cairo python-central python-chardet python-compizconfig
  python-configglue python-configobj python-crypto python-cups
  python-cupshelpers python-dateutil python-dbus python-debian python-defer
  python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gconf
  python-gdbm python-glade2 python-gmenu python-gnomekeyring
  python-gnupginterface python-gobject python-gobject-2 python-gobject-cairo
  python-gst0.10 python-gtk2 python-httplib2 python-ibus python-imaging
  python-indicate python-keyring python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-libproxy python-libxml2 python-louis python-lxml
  python-notify python-oauth python-openssl python-pam python-papyon
  python-pexpect python-piston-mini-client python-pkg-resources
  python-problem-report python-protobuf python-pyatspi2 python-pycurl
  python-pyinotify python-serial python-simplejson python-smbc
  python-software-properties python-speechd python-support python-telepathy
  python-twisted-bin python-twisted-core python-twisted-names
  python-twisted-web python-ubuntuone-client python-ubuntuone-control-panel
  python-ubuntuone-storageprotocol python-uno python-virtkey python-vte
  python-wadllib python-webkit python-wnck python-xapian python-xdg
  python-xkit python-zope.interface radiotray rastertosag-gdi sessioninstaller
  software-center software-properties-common software-properties-gtk splix
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-butterfly tomboy totem totem-mozilla
  totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-minimal ubuntu-sso-client
  ubuntu-standard ubuntu-system-service ubuntu-wallpapers ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk
  ubuntuone-couch ubuntuone-installer ufw unattended-upgrades unity unity-2d
  unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread
  unity-common unity-lens-applications unity-lens-files update-manager
  update-manager-core update-notifier update-notifier-common
  usb-creator-common usb-creator-gtk xdiagnose xul-ext-ubufox zeitgeist
  zeitgeist-core zeitgeist-datahub zeitgeist-extension-fts
The following NEW packages will be installed
  docbook-xsl icoutils kate-data katepart kde-runtime kde-runtime-data
  kdebase-runtime kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools
  kubuntu-debug-installer libattica0 libclucene0ldbl libdlrestrictions1
  libencode-locale-perl libfile-listing-perl libfont-afm-perl
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libilmbase6 libio-socket-ssl-perl libiodbc2
  libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5
  libkidletime4 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4
  libkrosscore4 libktexteditor4 liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmailtools-perl libnepomuk4 libnepomukquery4a
  libnepomukutils4 libnet-http-perl libnet-ssleay-perl libntrack-qt4-1
  libntrack0 libopenexr6 libphonon4 libplasma3 libpolkit-qt-1-1
  libqapt-runtime libqapt1 libqca2 libqt4-designer libqt4-qt3support
  libqtwebkit4 libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0
  libthreadweaver4 libtimedate-perl liburi-perl libvirtodbc0 libwww-perl
  libwww-robotrules-perl libxml2-utils libxss1 ntrack-module-libnl-0 odbcinst
  odbcinst1debian2 oxygen-icon-theme phonon phonon-backend-gstreamer
  plasma-scriptengine-javascript python3 python3-minimal python3.2
  python3.2-minimal qapt-batch shared-desktop-ontologies soprano-daemon
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common

```

---

### Post by houseworkshy on 2011-12-29
It may be easier to copy whatever is important to an external drive and reinstall as python is used to write much of fhe gui.  However there may be a cheating way round it you could try sudo apt-get install gnome-session-fallback which is the way of going back to gnome for people who don't like unity, in theory this should pull in the python dependancies after which you could reinstall unity if you wish.  This only an idea which I haven't tested but may be worth a shot [I]after you have saved your work.
[/I]Second thought is perhaps you could simply use a similar command to reinstall unity itself but I don't know as I'm not fond of unity and stick to the Lts versions anyway.

---

### Post by benpack101 on 2011-12-29
I believe I had a problem quite like this one a few weeks ago.

I would go ahead and boot into the recovery console, at the recovery menu choose remount, then netroot.

From there run 

sudo apt-get install ubuntu-desktop


then exit out of the terminal and restart.

Now you should be able to log back in.

(NOTE: After installing ubuntu-desktop you may also need to install your desktop interface, but I am not quite sure about that)

Hope this helps!

---

### Post by SNIFFER_dog on 2011-12-29
I have been trying to use the recovery mode to install the missing packages and although I can boot into root, from there I cannot use sudo apt-get install, it comes up with error messages:

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to var/cache/apt/
E: The package lists or status file could not be parsed or opened.

I can't access my files to do anything either as they are protected, in my home folder it says:

Access-Your-private-data.desktop

If I try and use the remount option in the recovery mode, it hangs with not other options and says:

/dev/sda5: clean, 259836/6135808 files, 2582775/24541952 blocks
[  274.708868] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro

If I press enter the screen goes up and up till nothing is displayed. If I press Ctrl-Alt-Del I get the next menu screen than after a few secs is reboots

I think I have bust it this time!!!

SNIFF

---

### Post by donkyhotay on 2011-12-29
If you can get to the CLI do what benpack suggested and run

```

sudo apt-get install ubuntu-desktop

```

that should automatically reinstall the GUI and all missing dependencies required by it. If that fails then you'll probably need to reinstall your OS.

---

### Post by SNIFFER_dog on 2011-12-29
I used Ctrl-Alt-F1 to get to the Comand line and have got it back up and running.

Thanks for your help, I must be more careful in future.

Kind regards

SNIFFY

---

