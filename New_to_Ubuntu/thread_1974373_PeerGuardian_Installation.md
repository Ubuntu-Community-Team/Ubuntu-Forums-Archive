---
title: "PeerGuardian Installation"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by whistlerspa on 2012-05-06
I have been unable to work out how to install this program in 12.04. I cannot find a repository to use apt, and the tar.gz version I downloaded from sourceforge wouldn't install once extracted on either my netbook or desktop.

If you are able to assist it would be most appreciated.

---

### Post by terrykiwi83 on 2012-05-06
It is in my software centre under pgld and pgl-gui

Give them a search? maybe it will work?

---

### Post by whistlerspa on 2012-05-07
It isn't in mine. have you addded any extra repositories?

---

### Post by whistlerspa on 2012-05-10
Bump Anyone?

---

### Post by jre on 2012-05-10
The tar gz is for unsupported distributions. It needs to be extracted, compiled and installed. All explained in the documentation, but not a task for a normal user.
So you should try the packages? See [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) 
For now, probably try the sources.list entry from natty. so add this to your /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu natty main
```

Then to add my gpg key, execute:
```
gpg --keyserver keyserver.ubuntu.com --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -
```


This repository will soon be updated.

---

### Post by KegHead on 2012-06-11
Hi jre!

I've used moblocker for years.

After upgrading to 12.04 I lost my gui.

I love the program!

Please advise!

Thanks!

KegHead

---

### Post by jre on 2012-06-11
Which version do you use?

Please post the output of
```
dpkg -l "pgl*"
```
I uploded a preview of the upcoming version last weekend. pgl-gui has been renamed to pglgui.

---

### Post by KegHead on 2012-06-12
ii  mono-gmcs      2.10.8.1-1ubun Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
ii  mono-runtime   2.10.8.1-1ubun Mono runtime
ii  mount          2.20.1-1ubuntu Tools for mounting and manipulating filesyst
ii  mountall       2.36           filesystem mounting tool
ii  mousetweaks    3.4.1-0ubuntu1 mouse accessibility enhancements for the GNO
ii  mscompress     0.3-3.1        Microsoft "compress.exe/expand.exe" compatib
ii  mtools         4.0.12-1       Tools for manipulating MSDOS files
ii  mtpfs          0.9-3build1    FUSE filesystem for Media Transfer Protocol 
ii  mtr-tiny       0.80-1ubuntu1  Full screen ncurses traceroute tool
ii  multiarch-supp 2.15-0ubuntu10 Transitional package to ensure multiarch com
ii  myspell-en-au  2.1-5.3ubuntu1 English_australian dictionary for myspell
ii  myspell-en-gb  1:3.3.0-2ubunt English_british dictionary for myspell
ii  myspell-en-za  1:3.3.0-2ubunt English_southafrican dictionary for myspell
ii  mysql-common   5.5.24-0ubuntu MySQL database common files, e.g. /etc/mysql
ii  mythes-en-us   1:3.3.0-2ubunt English Thesaurus for LibreOffice/OpenOffice
ii  nano           2.2.6-1        small, friendly text editor inspired by Pico
ii  nautilus       1:3.4.2-0ubunt file manager and graphical shell for GNOME
ii  nautilus-data  1:3.4.2-0ubunt data files for nautilus
ii  nautilus-sendt 3.0.1-2ubuntu2 integrates Evolution and Pidgin into the Nau
ii  nautilus-sendt 3.4.2-0ubuntu1 GNOME multi-protocol chat and call client (n
ii  nautilus-share 0.7.3-1ubuntu2 Nautilus extension to share folder using Sam
ii  ncurses-base   5.9-4          basic terminal type definitions
ii  ncurses-bin    5.9-4          terminal-related programs and man pages
ii  net-tools      1.60-24.1ubunt The NET-3 networking toolkit
ii  netbase        4.47ubuntu1    Basic TCP/IP networking system
ii  netcat-openbsd 1.89-4ubuntu1  TCP/IP swiss army knife
ii  network-manage 0.9.4.0-0ubunt network management framework (daemon and use
ii  network-manage 0.9.4.1-0ubunt network management framework (GNOME frontend
ii  network-manage 0.9.4.0-0ubunt network management framework (PPTP plugin co
ii  network-manage 0.9.4.0-0ubunt network management framework (PPTP plugin GN
ii  notify-osd     0.9.34-0ubuntu daemon that displays passive pop-up notifica
ii  notify-osd-ico 0.7            Notify-OSD icons
ii  ntfs-3g        1:2012.1.15AR. read/write NTFS driver for FUSE
ii  ntpdate        1:4.2.6.p3+dfs client for setting system time from NTP serv
ii  nux-tools      2.12.0-0ubuntu Visual rendering toolkit for real-time appli
ii  nvidia-common  1:0.2.44       Find obsolete NVIDIA drivers
ii  obex-data-serv 0.4.6-0ubuntu1 D-Bus service for OBEX client and server sid
ii  obexd-client   0.44-0ubuntu1  D-Bus OBEX client
ii  onboard        0.97.0-0ubuntu Simple On-screen Keyboard
ii  oneconf        0.2.8          synchronize your configuration data over the
ii  openjdk-6-doc  6b24-1.11.1-4u OpenJDK Development Kit (JDK) documentation
ii  openjdk-6-jre  6b24-1.11.1-4u OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre- 6b24-1.11.1-4u OpenJDK Java runtime, using Hotspot JIT (hea
ii  openjdk-6-jre- 6b24-1.11.1-4u OpenJDK Java runtime (architecture independe
ii  openoffice.org 0.6            Hyphenation patterns for OpenOffice.org
ii  openprinting-p 20120322-0ubun OpenPrinting printer support - PostScript PP
ii  openssh-client 1:5.9p1-5ubunt secure shell (SSH) client, for secure access
ii  openssl        1.0.1-4ubuntu5 Secure Socket Layer (SSL) binary and related
ii  os-prober      1.51ubuntu3    utility to detect other OSes on a set of dri
ii  overlay-scroll 0.2.16-0ubuntu Scrollbar overlayed widget
ii  p7zip-full     9.20.1~dfsg.1- 7z and 7za file archivers with high compress
ii  parted         2.3-8ubuntu5   disk partition manipulator
ii  passwd         1:4.1.4.2+svn3 change and administer password and group dat
ii  patch          2.6.1-3        Apply a diff file to an original
ii  patchutils     0.3.2-1.1      Utilities to work with patches
ii  pciutils       1:3.1.8-2ubunt Linux PCI Utilities
ii  pcmciautils    018-6          PCMCIA utilities for Linux 2.6
ii  perl           5.14.2-6ubuntu Larry Wall's Practical Extraction and Report
ii  perl-base      5.14.2-6ubuntu minimal Perl system
ii  perl-modules   5.14.2-6ubuntu Core Perl modules
ii  pitivi         0.15.2-0ubuntu non-linear audio/video editor using GStreame
ii  pkg-config     0.26-1ubuntu1  manage compile and link flags for libraries
ii  plymouth       0.8.2-2ubuntu3 graphical boot animation and logger - main p
ii  plymouth-label 0.8.2-2ubuntu3 graphical boot animation and logger - label 
ii  plymouth-theme 0.8.2-2ubuntu3 graphical boot animation and logger - ubuntu
ii  plymouth-theme 0.8.2-2ubuntu3 graphical boot animation and logger - ubuntu
ii  pm-utils       1.4.1-9        utilities and scripts for power management
ii  pnm2ppa        1.13+nondbs-0u transitional dummy package for pnm2ppa print
ii  po-debconf     1.0.16+nmu2ubu tool for managing templates file translation
ii  policykit-1    0.104-1ubuntu1 framework for managing administrative polici
ii  policykit-1-gn 0.105-1ubuntu3 GNOME authentication agent for PolicyKit-1
ii  policykit-desk 0.10           run common desktop actions without password
ii  poppler-utils  0.18.4-1ubuntu PDF utilities (based on Poppler)
ii  popularity-con 1.53ubuntu1    Vote for your favourite packages automatical
ii  powermgmt-base 1.31           Common utils and configs for power managemen
ii  ppa-purge      0.2.8+bzr56    disables a PPA and reverts to official packa
ii  ppp            2.4.5-5ubuntu1 Point-to-Point Protocol (PPP) - daemon
ii  pppconfig      2.3.18+nmu3ubu A text menu based utility for configuring pp
ii  pppoeconf      1.20ubuntu1    configures PPPoE/ADSL connections
ii  pptp-linux     1.7.2-6        Point-to-Point Tunneling Protocol (PPTP) Cli
ii  printer-driver 23-1           printer driver for Kodak ESP AiO color inkje
ii  printer-driver 20111202dfsg0- printer driver for ZjStream-based printers
ii  printer-driver 5.2.8~pre1-0ub printer drivers for CUPS
ii  printer-driver 3.12.2-1ubuntu HP Linux Printing and Imaging - CUPS Raster 
ii  printer-driver 3.12.2-1ubuntu HP Linux Printing and Imaging - gs IJS drive
ii  printer-driver 0.0.9-6ubuntu1 printer driver for KonicaMinolta PagePro 1[2
ii  printer-driver 1.13+nondbs-0u printer driver for HP-GDI printers
ii  printer-driver 1.3-3ubuntu0.1 printer driver Brother P-touch label printer
ii  printer-driver 1.3+repack0-2  printer driver for HP Color LaserJet 35xx/36
ii  printer-driver 0.1-3          printer driver for Ricoh Aficio SP 1000s/SP 
ii  printer-driver 2.0.0+svn300-1 Driver for Samsung and Xerox SPL2 and SPLc l
ii  procps         1:3.2.8-11ubun /proc file system utilities
ii  protobuf-compi 2.4.1-1ubuntu2 compiler for protocol buffer definition file
ii  psmisc         22.15-2ubuntu1 utilities that use the proc file system
ii  ptouch-driver  1.3-3ubuntu0.1 transitional dummy package for ptouch printe
ii  pulseaudio     1:1.1-0ubuntu1 PulseAudio sound server
ii  pulseaudio-eso 1:1.1-0ubuntu1 PulseAudio ESD compatibility layer
ii  pulseaudio-mod 1:1.1-0ubuntu1 Bluetooth module for PulseAudio sound server
ii  pulseaudio-mod 1:1.1-0ubuntu1 GConf module for PulseAudio sound server
ii  pulseaudio-mod 1:1.1-0ubuntu1 X11 module for PulseAudio sound server
ii  pulseaudio-uti 1:1.1-0ubuntu1 Command line tools for the PulseAudio sound 
ii  pxljr          1.3+repack0-2  transitional dummy package for pxljr printer
ii  python         2.7.3-0ubuntu2 interactive high-level object-oriented langu
ii  python-appindi 0.4.92-0ubuntu Python bindings for libappindicator
ii  python-apport  2.0.1-0ubuntu8 apport crash report handling library
ii  python-apt     0.8.3ubuntu7   Python interface to libapt-pkg
ii  python-apt-com 0.8.3ubuntu7   Python interface to libapt-pkg (locales)
ii  python-aptdaem 0.43+bzr805-0u Python module for the server and client of a
ii  python-aptdaem 0.43+bzr805-0u Transitional dummy package
ii  python-aptdaem 0.43+bzr805-0u Python GTK+ 3 widgets to run an aptdaemon cl
ii  python-aptdaem 0.43+bzr805-0u Python GTK+ 2 widgets to run an aptdaemon cl
ii  python-aptdaem 0.43+bzr805-0u PackageKit compatibilty for AptDaemon
ii  python-brlapi  4.3-1ubuntu5   Python bindings for BrlAPI
ii  python-cairo   1.8.8-1ubuntu3 Python bindings for the Cairo vector graphic
ii  python-central 0.6.17ubuntu2  register and build utility for Python packag
ii  python-chardet 2.0.1-2build1  universal character encoding detector
ii  python-compizc 0.9.5.94-0ubun Compizconfig bindings for python
ii  python-configg 1.0-1build1    Glues together optparse.OptionParser and Con
ii  python-crypto  2.4.1-1        cryptographic algorithms and protocols for P
ii  python-cups    1.9.61-0ubuntu Python bindings for CUPS
ii  python-cupshel 1.3.8+20120201 Python modules for printer configuration wit
ii  python-dateuti 1.5-1          powerful extensions to the standard datetime
ii  python-dbus    1.0.0-1ubuntu1 simple interprocess messaging system (Python
ii  python-dbus-de 1.0.0-1ubuntu1 main loop integration development files for 
ii  python-debian  0.1.21ubuntu1  Python modules to work with Debian-related d
ii  python-debtags 1.9+git2012032 Match debtags hardware:: tags against the ac
ii  python-defer   1.0.2+bzr481-1 Small framework for asynchronous programming
ii  python-dirspec 3.0.0-0ubuntu1 Python User Folders Specification Library
ii  python-egenix- 3.2.1-1ubuntu1 date and time handling routines for Python
ii  python-egenix- 3.2.1-1ubuntu1 collection of additional builtins for Python
ii  python-gconf   2.28.1+dfsg-1  Python bindings for the GConf configuration 
ii  python-gdbm    2.7.3-1ubuntu1 GNU dbm database support for Python
ii  python-gi      3.2.2-1~precis Python 2.x bindings for gobject-introspectio
ii  python-gi-cair 3.2.2-1~precis Python Cairo bindings for the GObject librar
ii  python-glade2  2.24.0-3       GTK+ bindings: Glade support
ii  python-gmenu   3.0.1-0ubuntu7 GNOME implementation of the freedesktop menu
ii  python-gnome2  2.28.1+dfsg-1  Python bindings for the GNOME desktop enviro
ii  python-gnomeke 2.32.0+dfsg-1  Python bindings for the GNOME keyring librar
ii  python-gnupgin 0.3.2-9.1ubunt Python interface to GnuPG (GPG)
ii  python-gobject 3.2.2-1~precis Python 2.x bindings for GObject - transition
ii  python-gobject 2.28.6-10ubunt deprecated static Python bindings for the GO
ii  python-gst0.10 0.10.22-3      generic media-playing framework (Python bind
ii  python-gtk2    2.24.0-3       Python bindings for the GTK+ widget set
ii  python-gtksour 2.10.1-2build1 Python bindings for the GtkSourceView widget
ii  python-gtkspel 2.25.3-11      Python bindings for the GtkSpell library
ii  python-httplib 0.7.2-1ubuntu2 comprehensive HTTP client library written fo
ii  python-ibus    1.4.1-3ubuntu1 Intelligent Input Bus - Python support
ii  python-imaging 1.1.7-4        Python Imaging Library
ii  python-indicat 0.6.92-0ubuntu Python bindings for libindicate
ii  python-keyring 0.7.1-1fakesyn store and access your passwords safely
ii  python-launchp 0.1.56         library for launchpad integration
ii  python-launchp 1.9.12-1       Launchpad web services client library
ii  python-lazr.re 0.12.0-1ubuntu client for lazr.restful-based web services
ii  python-lazr.ur 1.0.3-1        library for parsing, manipulating, and gener
ii  python-libprox 0.4.7-0ubuntu4 automatic proxy configuration management lib
ii  python-libxml2 2.7.8.dfsg-5.1 Python bindings for the GNOME XML library
ii  python-louis   2.3.0-3        Python bindings for liblouis
ii  python-lxml    2.3.2-1        pythonic binding for the libxml2 and libxslt
ii  python-mako    0.5.0-1        fast and lightweight templating for the Pyth
ii  python-markups 0.15-1         XML/HTML/XHTML Markup safe string for Python
ii  python-minimal 2.7.3-0ubuntu2 minimal subset of the Python language (defau
ii  python-notify  0.1.1-3        Python bindings for libnotify
ii  python-oauth   1.0.1-3build1  Python library implementing of the OAuth pro
ii  python-openssl 0.12-1ubuntu2  Python wrapper around the OpenSSL library
ii  python-package 0.7.2-4ubuntu3 PackageKit Python bindings
ii  python-pam     0.4.2-12.2ubun A Python interface to the PAM library
ii  python-pexpect 2.3-1ubuntu2   Python module for automating interactive app
ii  python-piston- 0.7.2-0ubuntu1 library for writing clients for Django's Pis
ii  python-pkg-res 0.6.24-1ubuntu Package Discovery and Resource Access using 
ii  python-problem 2.0.1-0ubuntu8 Python library to handle problem reports
ii  python-protobu 2.4.1-1ubuntu2 Python bindings for protocol buffers
ii  python-pyatspi 2.4.0+dfsg-0ub Assistive Technology Service Provider Interf
ii  python-pycurl  7.19.0-4ubuntu Python bindings to libcurl
ii  python-pygooca 0.14.1-1ubuntu GooCanvas Python bindings
ii  python-pyinoti 0.9.2-1        simple Linux inotify Python bindings
ii  python-pyorbit 2.24.0-6ubuntu A Python language binding for the ORBit2 COR
ii  python-qt4     4.9.1-2ubuntu1 Python bindings for Qt4
ii  python-qt4-dbu 4.9.1-2ubuntu1 DBus Support for PyQt4
ii  python-rdflib  2.4.2-1ubuntu1 RDF library containing an RDF triple store a
ii  python-renderp 2.5-1.1build1  python low level render interface
ii  python-reportl 2.5-1.1build1  ReportLab library to create PDF documents us
ii  python-reportl 2.5-1.1build1  C coded extension accelerator for the Report
ii  python-serial  2.5-2.1build1  pyserial - module encapsulating access for t
ii  python-simplej 2.3.2-1        simple, fast, extensible JSON encoder/decode
ii  python-sip     4.13.2-1       Python/C++ bindings generator runtime librar
ii  python-smbc    1.0.13-0ubuntu Python bindings for Samba clients (libsmbcli
ii  python-softwar 0.82.7.1       manage the repositories that you install sof
ii  python-speechd 0.7.1-6ubuntu3 Python interface to Speech Dispatcher
ii  python-support 1.0.14ubuntu2  automated rebuilding support for Python modu
ii  python-telepat 0.15.19-2.1bui Python language bindings for telepathy
ii  python-twisted 11.1.0-1ubuntu Event-based framework for internet applicati
ii  python-twisted 11.1.0-1ubuntu Event-based framework for internet applicati
ii  python-twisted 11.1.0-1       DNS protocol implementation with client and 
ii  python-twisted 11.1.0-1       HTTP protocol implementation together with c
ii  python-ubuntu- 3.0.0-0ubuntu2 Ubuntu Single Sign-On client - Python librar
ii  python-ubuntuo 3.0.0-0ubuntu1 Ubuntu One client Python libraries
ii  python-ubuntuo 3.0.0-0ubuntu1 Ubuntu One Control Panel - Python Libraries
ii  python-ubuntuo 3.0.0-0ubuntu1 Python library for Ubuntu One file storage a
ii  python-uno     1:3.5.3-0ubunt Python-UNO bridge
ii  python-virtkey 0.60.0-0ubuntu Library to emulate keyboard keypresses.
ii  python-vte     1:0.28.2-3ubun Python bindings for the VTE widget set
ii  python-wadllib 1.3.0-2        Python library for navigating WADL files
ii  python-webkit  1.1.8-2ubuntu2 WebKit/Gtk Python bindings
ii  python-wnck    2.32.0+dfsg-1  Python bindings for the WNCK library
ii  python-wsgi-in 0.4-0ubuntu3   installs a WSGI application in place of a re
ii  python-xapian  1.2.8-1        Xapian search engine interface for Python
ii  python-xdg     0.19-3ubuntu2  Python library to access freedesktop.org sta
ii  python-xkit    0.4.2.3build1  library for the manipulation of the xorg.con
ii  python-zeitgei 0.9.0-1ubuntu1 event logging framework - Python bindings
ii  python-zope.in 3.6.1-1ubuntu3 Interfaces for Python
ii  python2.7      2.7.3-0ubuntu3 Interactive high-level object-oriented langu
ii  python2.7-mini 2.7.3-0ubuntu3 Minimal subset of the Python language (versi
ii  qdbus          4:4.8.1-0ubunt Qt 4 D-Bus tool
ii  qt-at-spi      0.2.0+git20120 accessibility plugin for Qt
ii  quadrapassel   1:3.4.1-0ubunt popular Russian game, similar to Tetris
ii  radeontool     1.6.2-1.1      utility to control ATI Radeon backlight func
ii  rarian-compat  0.8.1-5        Documentation meta-data library (compatibili
ii  rastertosag-gd 0.1-3          transitional dummy package for rastertosag-g
ii  rdesktop       1.7.0-1ubuntu2 RDP client for Windows NT/2000 Terminal Serv
ii  readline-commo 6.2-8          GNU readline and history libraries, common f
ii  remmina        1.0.0-1ubuntu6 remote desktop client for GNOME desktop envi
ii  remmina-common 1.0.0-1ubuntu6 common files for remmina remote desktop clie
ii  remmina-plugin 1.0.0-1ubuntu6 RDP plugin for remmina remote desktop client
ii  remmina-plugin 1.0.0-1ubuntu6 VNC plugin for remmina remote desktop client
ii  resolvconf     1.63ubuntu14   name server information handler
ii  rfkill         0.4-1ubuntu2   tool for enabling and disabling wireless dev
ii  rhythmbox      2.96-0ubuntu4  music player and organizer for GNOME
ii  rhythmbox-data 2.96-0ubuntu4  data files for rhythmbox
ii  rhythmbox-mozi 2.96-0ubuntu4  Rhythmbox Mozilla plugin
ii  rhythmbox-plug 2.96-0ubuntu4  burning plugin for rhythmbox music player
ii  rhythmbox-plug 2.96-0ubuntu4  Magnatune plugin for rhythmbox music player
ii  rhythmbox-plug 2.96-0ubuntu4  zeitgeist plugin for rhythmbox music player
ii  rhythmbox-plug 2.96-0ubuntu4  plugins for rhythmbox music player
ii  rhythmbox-ubun 3.0.0-0ubuntu1 Ubuntu One Rhythmbox plugin
ii  rsync          3.0.9-1ubuntu1 fast, versatile, remote (and local) file-cop
ii  rsyslog        5.8.6-1ubuntu8 reliable system and kernel logging daemon
ii  rtkit          0.10-2         Realtime Policy and Watchdog Daemon
ii  samba-common   2:3.6.3-2ubunt common files used by both the Samba server a
ii  samba-common-b 2:3.6.3-2ubunt common files used by both the Samba server a
ii  sane-utils     1.0.22-7ubuntu API library for scanners -- utilities
rc  scangearmp-com 1.60-1         ScanGear MP for Linux.
rc  scangearmp-mp2 1.60-1         ScanGear MP for Linux.
ii  screensaver-de 0.2-1          Wallpapers for image processing screensavers
ii  seahorse       3.2.2-0ubuntu2 GNOME front end for GnuPG
ii  sed            4.2.1-9        The GNU sed stream editor
ii  sensible-utils 0.0.6ubuntu2   Utilities for sensible alternative selection
ii  sessioninstall 0.20+bzr128-0u APT based installer using PackageKit's sessi
ii  sgml-base      1.26+nmu1ubunt SGML infrastructure and SGML catalog file su
ii  sgml-data      2.0.6          common SGML and XML data
ii  shared-mime-in 1.0-0ubuntu4.1 FreeDesktop.org shared MIME database and spe
ii  shotwell       0.12.3-0ubuntu digital photo organizer
ii  simple-scan    3.4.1-0ubuntu1 Simple Scanning Utility
ii  smbclient      2:3.6.3-2ubunt command-line SMB/CIFS clients for Unix
ii  sni-qt         0.2.5-0ubuntu3 indicator support for Qt
ii  software-cente 5.2.2.2        Utility for browsing, installing, and removi
ii  software-cente 0.1.2          The aptdaemon plugins for software-center
ii  software-prope 0.82.7.1       manage the repositories that you install sof
ii  software-prope 0.82.7.1       manage the repositories that you install sof
ii  sound-theme-fr 0.7.pristine-2 freedesktop.org sound theme
ii  speech-dispatc 0.7.1-6ubuntu3 Common interface to speech synthesizers
ii  splix          2.0.0+svn300-1 transitional dummy package for splix printer
ii  ssh-askpass-gn 1:5.9p1-5ubunt interactive X program to prompt users for a 
ii  ssl-cert       1.0.28ubuntu0. simple debconf wrapper for OpenSSL
ii  strace         4.5.20-2.3ubun A system call tracer
ii  sudo           1.8.3p1-1ubunt Provide limited super user privileges to spe
ii  swell-foop     1:3.4.1-0ubunt Colored ball puzzle game
ii  synaptic       0.75.9ubuntu1  Graphical package manager
ii  syslinux       2:4.05+dfsg-2  collection of boot loaders
ii  syslinux-commo 2:4.05+dfsg-2  collection of boot loaders (common files)
ii  syslinux-legac 2:3.63+dfsg-2u Bootloader for Linux/i386 using MS-DOS flopp
ii  syslinux-theme 10-1           collection of boot loaders (theme metapackag
ii  syslinux-theme 10-1           collection of boot loaders (debian-squeeze t
ii  system-config- 1.3.8+20120201 Printer configuration GUI
ii  system-config- 1.3.8+20120201 Printer configuration GUI
ii  system-config- 1.3.8+20120201 Printer auto-configuration facility based on
ii  system-tools-b 2.10.2-1ubuntu System Tools to manage computer configuratio
ii  sysv-rc        2.88dsf-13.10u System-V-like runlevel change mechanism
ii  sysvinit-utils 2.88dsf-13.10u System-V-like utilities
ii  tar            1.26-4ubuntu1  GNU version of the tar archiving utility
ii  tcl            8.5.0-2        The Tool Command Language (default version) 
ii  tcl8.4         8.4.19-4ubuntu Tcl (the Tool Command Language) v8.4 - run-t
ii  tcl8.5         8.5.11-1ubuntu Tcl (the Tool Command Language) v8.5 - run-t
ii  tcpd           7.6.q-21       Wietse Venema's TCP wrapper utilities
ii  tcpdump        4.2.1-1ubuntu2 command-line network traffic analyzer
ii  telepathy-gabb 0.16.0-0ubuntu Jabber/XMPP connection manager
ii  telepathy-haze 0.6.0-0ubuntu1 Telepathy connection manager that uses libpu
ii  telepathy-idle 0.1.11-2       IRC connection manager for Telepathy
ii  telepathy-indi 0.2.1-0ubuntu1 Desktop service to integrate Telepathy with 
ii  telepathy-logg 0.4.0-0ubuntu1 Telepathy logger service - Daemon
ii  telepathy-miss 1:5.12.0-0ubun management daemon for Telepathy real-time co
ii  telepathy-salu 0.8.0-0ubuntu1 Link-local XMPP connection manager for the T
ii  telnet         0.17-36build1  The telnet client
ii  thunderbird    12.0.1+build1- Email, RSS and newsgroup client with integra
ii  thunderbird-gl 12.0.1+build1- Unity appmenu integration for Thunderbird
ii  time           1.7-23.1       The GNU time program for measuring cpu resou
ii  tomboy         1.10.1-0ubuntu desktop note taking program using Wiki style
ii  toshset        1.76-2         Access much of the Toshiba laptop hardware i
ii  totem          3.0.1-0ubuntu2 Simple media player for the GNOME desktop ba
ii  totem-common   3.0.1-0ubuntu2 Data files for the Totem media player
ii  totem-mozilla  3.0.1-0ubuntu2 Totem Mozilla plugin
ii  totem-plugins  3.0.1-0ubuntu2 Plugins for the Totem media player
ii  transmission-c 2.51-0ubuntu1  lightweight BitTorrent client (common files)
ii  transmission-g 2.51-0ubuntu1  lightweight BitTorrent client (GTK interface
ii  tsconf         1.0-10         touch screen library common files
ii  ttf-dejavu     2.33-2ubuntu1  Metapackage to pull in ttf-dejavu-core and t
ii  ttf-dejavu-cor 2.33-2ubuntu1  Vera font family derivate with additional ch
ii  ttf-dejavu-ext 2.33-2ubuntu1  Vera font family derivate with additional ch
ii  ttf-freefont   20100919-1     Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-font 1:0.5.11ubuntu Core collection of free fonts for languages 
ii  ttf-kacst-one  5.0+svn11846-2 transitional dummy package
ii  ttf-khmeros-co 5.0-5ubuntu1   transitional dummy package
ii  ttf-lao        0.0.20060226-8 transitional dummy package
ii  ttf-liberation 1.07.0-2       transitional dummy package
ii  ttf-opensymbol 2:102.2+LibO3. transitional package for fonts-opensymbol
ii  ttf-punjabi-fo 1:0.5.11ubuntu Free TrueType fonts for the Punjabi language
ii  ttf-sil-gentiu 1.1-5          transitional dummy package
ii  ttf-takao-pgot 003.02.01-5ubu transitional dummy package
ii  ttf-thai-tlwg  1:0.4.17-1ubun transitional dummy package
ii  ttf-ubuntu-fon 0.80-0ubuntu2  Ubuntu Font Family, sans-serif typeface hint
ii  ttf-unfonts-co 1.0.3.is.1.0.2 transitional dummy package
ii  ttf-wqy-microh 0.2.0-beta-1ub A droid derived Sans-Seri style CJK font
ii  tweak          3.01-7         an efficient hex editor
ii  tzdata         2012b-1        time zone and daylight-saving time data
ii  tzdata-java    2012b-1        time zone and daylight-saving time data for 
ii  ubuntu-artwork 57             Ubuntu themes and artwork
ii  ubuntu-desktop 1.267          The Ubuntu desktop system
ii  ubuntu-docs    12.04.5        Ubuntu Desktop Guide
ii  ubuntu-extras- 2010.09.27     GnuPG keys of the Ubuntu extras archive
ii  ubuntu-keyring 2011.11.21     GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal 1.267          Minimal core of Ubuntu
ii  ubuntu-mono    0.0.40         Ubuntu Mono Icon theme
ii  ubuntu-restric 12             Commonly used restricted packages for Ubuntu
ii  ubuntu-sounds  0.13           Ubuntu's GNOME audio theme
ii  ubuntu-sso-cli 3.0.0-0ubuntu2 Ubuntu Single Sign-On client
ii  ubuntu-sso-cli 3.0.0-0ubuntu2 Ubuntu Single Sign-On client - GTK+ frontend
ii  ubuntu-sso-cli 3.0.0-0ubuntu2 Ubuntu Single Sign-On client - Qt frontend
ii  ubuntu-standar 1.267          The Ubuntu standard system
ii  ubuntu-system- 0.2.2          Dbus service to set various system-wide conf
ii  ubuntu-tweak   0.7.2-1~precis Ubuntu Tweak
ii  ubuntu-wallpap 0.34.1         Ubuntu Wallpapers
ii  ubuntu-wallpap 0.34.1         Ubuntu 12.04 Wallpapers
ii  ubuntuone-clie 3.0.0-0ubuntu1 Ubuntu One client
ii  ubuntuone-clie 3.0.1-0ubuntu1 Ubuntu One client GNOME integration
ii  ubuntuone-cont 3.0.0-0ubuntu1 Ubuntu One Control Panel
ii  ubuntuone-cont 3.0.0-0ubuntu1 Ubuntu One Control Panel - Common frontend f
ii  ubuntuone-cont 3.0.0-0ubuntu1 Ubuntu One Control Panel - transitional dumm
ii  ubuntuone-cont 3.0.0-0ubuntu1 Ubuntu One Control Panel - Qt frontend
ii  ubuntuone-couc 0.3.0-0ubuntu4 Ubuntu One CouchDB
ii  ubuntuone-inst 3.0.0-0ubuntu1 Ubuntu One Installer
ii  ucf            3.0025+nmu2ubu Update Configuration File: preserve user cha
ii  udev           175-0ubuntu9   rule-based device node and kernel event mana
ii  udisks         1.0.4-5ubuntu2 storage media interface
ii  ufw            0.31.1-1       program for managing a Netfilter firewall
ii  unattended-upg 0.76           automatic installation of security upgrades
ii  unetbootin     565-3          installer of Linux/BSD distributions to a pa
ii  unetbootin-tra 565-3          translations for unetbootin distribution ins
ii  unity          5.12-0ubuntu1. Interface designed for efficiency of space a
ii  unity-2d       5.12.0-0ubuntu Unity interface for non-accelerated graphics
ii  unity-2d-commo 5.12.0-0ubuntu Common files for Unity 2D Shell
ii  unity-2d-panel 5.12.0-0ubuntu Unity 2D Panel
ii  unity-2d-shell 5.12.0-0ubuntu Dash and Launcher for the Unity 2D environme
ii  unity-2d-sprea 5.12.0-0ubuntu Unity 2D Spread
ii  unity-asset-po 0.8.23-0ubuntu Unity Assets Pool
ii  unity-common   5.12-0ubuntu1. Common files for the Unity interface.
ii  unity-greeter  0.2.8-0ubuntu1 Unity Greeter
ii  unity-lens-app 5.12.0-0ubuntu Application lens for unity
ii  unity-lens-fil 5.10.0-0ubuntu File lens for unity
ii  unity-lens-mus 5.12.0-0ubuntu Music lens for unity
ii  unity-lens-vid 0.3.5-0ubuntu1 Unity Video lens
ii  unity-place-ap 5.12.0-0ubuntu transitional package
ii  unity-place-fi 5.10.0-0ubuntu transitional package
ii  unity-scope-mu 5.12.0-0ubuntu Store music lens for unity
ii  unity-scope-vi 0.3.5-0ubuntu2 Remote videos engine
ii  unity-services 5.12-0ubuntu1. Services for the Unity interface
ii  uno-libs3      3.5.3-0ubuntu1 LibreOffice UNO runtime environment -- publi
ii  unzip          6.0-4ubuntu1   De-archiver for .zip files
ii  update-inetd   4.41           inetd configuration file updater
ii  update-manager 1:0.156.14.5   GNOME application that manages apt updates
ii  update-manager 1:0.156.14.5   manage release upgrades
ii  update-notifie 0.119ubuntu8.4 Daemon which notifies about package updates
ii  update-notifie 0.119ubuntu8.4 Files shared between update-notifier and oth
ii  upower         0.9.15-3git1   abstraction for power management
ii  upstart        1.5-0ubuntu7   event-based init daemon
ii  ure            3.5.3-0ubuntu1 LibreOffice UNO runtime environment
ii  ureadahead     0.100.0-12     Read required files in advance
ii  usb-creator-co 0.2.38         create a startup disk using a CD or disc ima
ii  usb-creator-gt 0.2.38         create a startup disk using a CD or disc ima
ii  usb-modeswitch 1.2.3+repack0- mode switching tool for controlling "flip fl
ii  usb-modeswitch 20120120-0ubun mode switching data for usb-modeswitch
ii  usbmuxd        1.0.7-2        USB multiplexor daemon for iPhone and iPod T
ii  usbutils       1:005-1        Linux USB utilities
ii  util-linux     2.20.1-1ubuntu Miscellaneous system utilities
ii  uuid-runtime   2.20.1-1ubuntu runtime components for the Universally Uniqu
ii  vbetool        1.1-2ubuntu1   run real-mode video BIOS code to alter hardw
ii  vim-common     2:7.3.429-2ubu Vi IMproved - Common files
ii  vim-tiny       2:7.3.429-2ubu Vi IMproved - enhanced vi editor - compact v
ii  vinagre        3.4.2-0ubuntu1 remote desktop client for the GNOME Desktop
ii  vino           3.4.2-0ubuntu1 VNC server for GNOME
ii  vlc            2.0.1-4        multimedia player and streamer
ii  vlc-data       2.0.1-4        Common data for VLC
ii  vlc-nox        2.0.1-4        multimedia player and streamer (without X su
ii  vlc-plugin-not 2.0.1-4        LibNotify plugin for VLC
ii  vlc-plugin-pul 2.0.1-4        PulseAudio plugin for VLC
ii  wamerican      7.1-1          American English dictionary words for /usr/s
ii  wbritish       7.1-1          British English dictionary words for /usr/sh
ii  wget           1.13.4-2ubuntu retrieves files from the web
ii  whiptail       0.52.11-2ubunt Displays user-friendly dialog boxes from she
ii  whois          5.0.15ubuntu2  intelligent WHOIS client
ii  whoopsie       0.1.32         Ubuntu crash database submission daemon
ii  wireless-crda  1.16           Wireless Central Regulatory Domain Agent
ii  wireless-regdb 2011.04.28-1ub wireless regulatory database
ii  wireless-tools 30~pre9-5ubunt Tools for manipulating Linux Wireless Extens
ii  wodim          9:1.1.11-2ubun command line CD/DVD writing tool
ii  wpasupplicant  0.7.3-6ubuntu2 client support for WPA and WPA2 (IEEE 802.11
ii  x-ttcidfont-co 32+nmu2        TrueType and CID fonts configuration for X
ii  x11-apps       7.6+5ubuntu1   X applications
ii  x11-common     1:7.6+12ubuntu X Window System (X.Org) infrastructure
ii  x11-session-ut 7.6+2          X session utilities
ii  x11-utils      7.6+4          X11 utilities
ii  x11-xfs-utils  7.6+1          X font server utilities
ii  x11-xkb-utils  7.6+4          X11 XKB utilities
ii  x11-xserver-ut 7.6+3          X server utilities
ii  x11proto-compo 1:0.4.2-2      X11 Composite extension wire protocol
ii  x11proto-core- 7.0.22-1       X11 core wire protocol and auxiliary headers
ii  x11proto-damag 1:1.2.1-2      X11 Damage extension wire protocol
ii  x11proto-fixes 1:5.0-2ubuntu1 X11 Fixes extension wire protocol
ii  x11proto-input 2.1.99.6-1     X11 Input extension wire protocol
ii  x11proto-kb-de 1.0.5-2        X11 XKB extension wire protocol
ii  x11proto-randr 1.4.0+git20101 X11 RandR extension wire protocol
ii  x11proto-rende 2:0.11.1-2     X11 Render extension wire protocol
ii  x11proto-xext- 7.2.0-3        X11 various extension wire protocol
ii  x11proto-xiner 1.2.1-2        X11 Xinerama extension wire protocol
ii  xauth          1:1.0.6-1      X authentication utility
ii  xbitmaps       1.1.1-1        Base X bitmaps
ii  xcursor-themes 1.0.3-1        Base X cursor themes
ii  xdg-user-dirs  0.14-0ubuntu2  tool to manage well known user directories
ii  xdg-user-dirs- 0.9-0ubuntu1   tool to manage well known user directories (
ii  xdg-utils      1.1.0~rc1-2ubu desktop integration utilities from freedeskt
ii  xdiagnose      2.5            X.org diagnosis tool
ii  xfonts-base    1:1.0.3        standard fonts for X
ii  xfonts-encodin 1:1.0.4-1ubunt Encodings for X.Org fonts
ii  xfonts-mathml  4ubuntu1       Type1 Symbol font for MathML
ii  xfonts-scalabl 1:1.0.3-1      scalable fonts for X
ii  xfonts-utils   1:7.6+1        X Window System font utility programs
ii  xinit          1.3.1-1        X server initialisation tool
ii  xinput         1.5.99.1-0ubun Runtime configuration and test of XInput dev
ii  xkb-data       2.5-1ubuntu1   X Keyboard Extension (XKB) configuration dat
ii  xml-core       0.13           XML infrastructure and XML catalog file supp
ii  xorg           1:7.6+12ubuntu X.Org X Window System
ii  xorg-docs-core 1:1.6-1ubuntu2 Core documentation for the X.org X Window Sy
ii  xorg-sgml-doct 1:1.10-1       Common tools for building X.Org SGML documen
ii  xscreensaver-d 5.15-2ubuntu1  data files to be shared among screensaver fr
ii  xscreensaver-g 5.15-2ubuntu1  GL(Mesa) screen hacks for xscreensaver
ii  xserver-common 2:1.11.4-0ubun common files used by various X servers
ii  xserver-xorg   1:7.6+12ubuntu X.Org X server
ii  xserver-xorg-c 2:1.11.4-0ubun Xorg X server - core server
ii  xserver-xorg-i 1:7.6+12ubuntu X.Org X server -- input driver metapackage
ii  xserver-xorg-i 1:2.7.0-0ubunt X.Org X server -- evdev input driver
ii  xserver-xorg-i 1:1.7.1-1build X.Org X server -- mouse input driver
ii  xserver-xorg-i 1.6.0-0ubuntu1 Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-i 1:12.8.0-1     X.Org X server -- VMMouse input driver to us
ii  xserver-xorg-i 1:0.14.0-0ubun X.Org X server -- Wacom input driver
ii  xserver-xorg-v 1:7.6+12ubuntu X.Org X server -- output driver metapackage
ii  xserver-xorg-v 1:1.2.3-2build X.Org X server -- APM display driver
ii  xserver-xorg-v 1:0.7.3-2build X.Org X server -- ark display driver
ii  xserver-xorg-v 1:6.14.99~git2 X.Org X server -- AMD/ATI display driver wra
ii  xserver-xorg-v 1:1.2.4-1build X.Org X server -- Chips display driver
ii  xserver-xorg-v 1:1.3.2-4build X.Org X server -- Cirrus display driver
ii  xserver-xorg-v 1:0.4.2-4ubunt X.Org X server -- fbdev display driver
ii  xserver-xorg-v 2.11.13-2build X.Org X server -- Geode GX2/LX display drive
ii  xserver-xorg-v 1:1.3.4-2build X.Org X server -- i128 display driver
ii  xserver-xorg-v 1:1.3.2-4build X.Org X server -- i740 display driver
ii  xserver-xorg-v 2:2.17.0-1ubun X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-v 6.9.0-1build2  X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-v 1:1.4.13.dfsg- X.Org X server -- MGA display driver
ii  xserver-xorg-v 1:1.2.5-2build X.Org X server -- Neomagic display driver
ii  xserver-xorg-v 1:0.0.16+git20 X.Org X server -- Nouveau display driver
ii  xserver-xorg-v 1:0.2.904+svn1 X.Org X server -- VIA display driver
ii  xserver-xorg-v 0.0.16-2       X.Org X server -- QXL display driver
ii  xserver-xorg-v 6.8.1-5build2  X.Org X server -- ATI r128 display driver
ii  xserver-xorg-v 1:6.14.99~git2 X.Org X server -- AMD/ATI Radeon display dri
ii  xserver-xorg-v 1:4.2.4-2ubunt X.Org X server -- Rendition display driver
ii  xserver-xorg-v 1:0.6.3-4build X.Org X server -- legacy S3 display driver
ii  xserver-xorg-v 1:1.10.4-4buil X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-v 1:2.3.3-1ubunt X.Org X server -- Savage display driver
ii  xserver-xorg-v 1:1.7.5-1build X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-v 1:0.10.3-3buil X.Org X server -- SiS display driver
ii  xserver-xorg-v 1:0.9.4-2build X.Org X server -- SiS USB display driver
ii  xserver-xorg-v 1:1.4.3-4build X.Org X server -- tdfx display driver
ii  xserver-xorg-v 1:1.3.4-2build X.Org X server -- Trident display driver
ii  xserver-xorg-v 1:1.2.4-2build X.Org X server -- Tseng display driver
ii  xserver-xorg-v 1:2.3.0-7build X.Org X server -- VESA display driver
ii  xserver-xorg-v 1:12.0.1-1ubun X.Org X server -- VMware display driver
ii  xserver-xorg-v 1:1.2.4-2build X.Org X server -- Voodoo display driver
ii  xsltproc       1.1.26-8ubuntu XSLT 1.0 command line processor
ii  xterm          271-1ubuntu2   X terminal emulator
ii  xtrans-dev     1.2.6-2        X transport library (development files)
ii  xul-ext-ubufox 2.0.3-0ubuntu1 Ubuntu-specific configuration defaults and a
ii  xz-lzma        5.1.1alpha+201 XZ-format compression utilities - compatibil
ii  xz-utils       5.1.1alpha+201 XZ-format compression utilities
ii  yelp           3.4.1-0ubuntu1 Help browser for GNOME
ii  yelp-xsl       3.4.1-1        XSL stylesheets for the yelp help browser
ii  zeitgeist      0.9.0-1ubuntu1 event logging framework
ii  zeitgeist-core 0.9.0-1ubuntu1 event logging framework - engine
ii  zeitgeist-data 0.8.2-1ubuntu2 event logging framework - passive logging da
ii  zeitgeist-exte 0.0.13-0ubuntu Extensions for zeitgeist engine - fts extens
ii  zenity         3.4.0-0ubuntu4 Display graphical dialog boxes from shell sc
ii  zenity-common  3.4.0-0ubuntu4 Display graphical dialog boxes from shell sc
ii  zip            3.0-4          Archiver for .zip files
ii  zlib1g         1:1.2.3.4.dfsg compression library - runtime
ii  zlib1g-dev     1:1.2.3.4.dfsg compression library - development
jim@jim:~$

---

### Post by jre on 2012-06-12
First off, please post such output in CODE tags (see my signature).

Second, this is not the output I asked for, please try again, you may also just try this command:
```
dpkg -l pglgui pgl-gui
```

---

### Post by KegHead on 2012-06-12
Hi!

Sorry, I've not been on this forum for years.

jim@jim:~$ dpkg -l pglgui pgl-gui
No packages found matching pglgui.
No packages found matching pgl-gu

---

### Post by jre on 2012-06-13
You can get to the CODE tags by clicking "Go Advanced". Please use them.


I (probably) fixed the repository. Please update your packages. Now there should be a package "pglgui" available to be installed.

---

### Post by KegHead on 2012-06-14
Hi!

Downloaded the update.

Works perfectly!

Thanks!

KegHead

---

### Post by KegHead on 2012-06-15
Hi!

This is weird.

Did the following;

sudo aptitude install linux-image -f

pglgui  unintalled.

Any ideas?

KegHead

---

### Post by jre on 2012-06-15
You used the "-f" switch of aptitude, that means:
```
-f
  Try hard to fix the dependencies of broken packages, even if it
  means ignoring the actions requested on the command line.

  This corresponds to the configuration item
  Aptitude::CmdLine::Fix-Broken.
```

I guess the **pglgui** installation was **broken** because of its conflict with the outdated **pgl-gui** (note the - in the name) installation. Instead of solving this situation by updating to the new packages, aptitude probably chose to stay with the old versions.

Do a
```
sudo aptitude purge pgl-gui
sudo aptitude install pgld=2.2.0.1-1~natty pglcmd=2.2.0.1-1~natty pglgui=2.2.0.1-1~natty
```

---

### Post by KegHead on 2012-06-15
Hi!

Working!

I noticed that there is a not an option to seek info about the intruder.


jim@jim:~$ sudo aptitude purge pgl-gui
[sudo] password for jim: 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
jim@jim:~$ sudo aptitude install pgld=2.2.0.1-1~natty pglcmd=2.2.0.1-1~natty pglgui=2.2.0.1-1~natty
The following NEW packages will be installed:
  libnetfilter-queue1{a} libpolkit-qt-1-1{a} pglcmd pgld pglgui 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,564 B/437 kB of archives. After unpacking 1,435 kB will be used.
Do you want to continue? [Y/n/?] y
Get: 1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libnetfilter-queue1 i386 0.0.17-1 [8,564 B]
Fetched 8,564 B in 0s (73.9 kB/s)              
Preconfiguring packages ...
Selecting previously unselected package libnetfilter-queue1.
(Reading database ... 213737 files and directories currently installed.)
Unpacking libnetfilter-queue1 (from .../libnetfilter-queue1_0.0.17-1_i386.deb) ...
Selecting previously unselected package pgld.
Unpacking pgld (from .../pgld_2.2.0.1-1~natty_i386.deb) ...
Selecting previously unselected package pglcmd.
Unpacking pglcmd (from .../pglcmd_2.2.0.1-1~natty_all.deb) ...
Selecting previously unselected package libpolkit-qt-1-1.
Unpacking libpolkit-qt-1-1 (from .../libpolkit-qt-1-1_0.103.0-1_i386.deb) ...
Selecting previously unselected package pglgui.
Unpacking pglgui (from .../pglgui_2.2.0.1-1~natty_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libnetfilter-queue1 (0.0.17-1) ...
Setting up pgld (2.2.0.1-1~natty) ...
Setting up pglcmd (2.2.0.1-1~natty) ...

pgld will soon be started ...
If any blocklists are missing, they will be downloaded. This may take several
minutes. Please be patient and don't abort. If you want to follow the update
process, then do in another terminal a
 tail -f /var/log/pgl/pglcmd.log
The lists are saved to /var/spool/pgl/.
The installation of pglcmd will fail, if starting pgld fails. So if
downloading the blocklists fails temporarily, the installation will fail. In
this case you may turn the automatic starting off by setting in
/etc/pgl/pglcmd.conf:
 INIT="0"
Then complete the installation and turn the automatic start on again:
 sudo dpkg-reconfigure --force pglcmd
Please be patient ...
 * Starting PeerGuardian Linux pgld                                      [ OK ] 
Setting up libpolkit-qt-1-1 (0.103.0-1) ...
Setting up pglgui (2.2.0.1-1~natty) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
jim@jim:~$

---

### Post by jre on 2012-06-15
Does it hurt that much to finaly use **CODE** tags? I asked you 3 times and explained how to do that.

About the intruder info: you mean something like "right-click on blocked IP and get the *whois* information"?

---

### Post by jre on 2012-06-20
"right-click on blocked IP and get the whois information" was just added. See current code in the git repository or wait for the next release in a few days.

---

### Post by Hamburgian on 2013-02-01
Hi JRE

Having problems with the settings for pgl and thunderbird

I've set the whitelist ports as per the suggestions in /usr/lib/pgl/pglcmd.defaults

[code]WHITE_TCP_OUT="http https"
WHITE_TCP_IN=""
WHITE_TCP_OUT="80 443 22 993 143"
INIT="1"
CRON="1" [code]

I can access internet, but email (thunderbird) is blocked. Every time I white list a port, thunderbird (I assume) tried to use a different port. It's currently trying to send on port  465. 
What am I doing wrong?

I'm using Lucid by the way, and the package from your repository
http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu

---

### Post by Hamburgian on 2013-02-01
Guess I should pack this box up and take it back to the shop...I'm too stupid to have a computer.....a quick check of thunderbird account settings told me that outgoing port is indeed 465

---

### Post by jre on 2013-02-01
> **Hamburgian said:**
> 
```
WHITE_TCP_OUT="http https"
[...]
WHITE_TCP_OUT="80 443 22 993 143"
```

You set this variable twice, this doesn't work. Only the latter entry is used, in this case "80 443 22 993 143" (btw you haven't whitelisted "465" which should indeed be the correct setting for sending mails with smtp. For getting mails with imap you already have correctly inserted 993. But please read on ...)

Sidenote: "http" is the same as "80", and "https" as "443" - so you don't miss anything by your double insertion.

Now, 2  things: first I recommend that you **use pglgui**. There you can easily see the ports and IPs that were blocked. And you can whitelist them easily by right-clicking any item in the logfile in pglgui.

Further I generally **recommend not to whitelist ports, but only IPs**.
If you whitelist a port, a malicious host (IP) may just choose e.g. port 80 to listen on and you would not be protected. A port is open for every IP from 0.0.0.0 to 255.255.255.255.
Of course it takes you some time, because you have to add may IPs to get a nice system, instead of just a few ports.
Therefore you should first check the blocklist settings. The default setup is quite paranoid and you may choose to use fewer blocklists.

---

### Post by C00gan on 2013-07-08
Hi everyone,  sorry if i hijack this thread. I installed pgl with sudo add-apt-repository ppa:jre-phoenix/ppa and sudo apt-get update && sudo apt-get install pgld pglcmd pglgui. But when i start it, i can't connect to any page on the web anymore.  Please could someneone help me to configure pgl (whitelists, blacklists, settings), so i can use it properly. I'm using Kubuntu LTS and am a complete newbie to Linux.

---

### Post by jre on 2013-07-08
> **C00gan said:**
> Hi everyone,  sorry if i hijack this thread.

So you know the rules. Next time please don't do the wrong thing and say sorry, but do the right thing in the first place: search the forums and start a new thread.


> **C00gan said:**
> Hi everyone,  sorry if i hijack this thread. I installed pgl with sudo add-apt-repository ppa:jre-phoenix/ppa and sudo apt-get update && sudo apt-get install pgld pglcmd pglgui. But when i start it, i can't connect to any page on the web anymore.  Please could someneone help me to configure pgl (whitelists, blacklists, settings), so i can use it properly. I'm using Kubuntu LTS and am a complete newbie to Linux.

The answer is here:
[http://sourceforge.net/p/peerguardian/wiki/pgl-FAQ/#some-applications-cannot-connect-to-the-internet-any-more](http://sourceforge.net/p/peerguardian/wiki/pgl-FAQ/#some-applications-cannot-connect-to-the-internet-any-more)

1. decide on the correct set of blocklists
2. use right-click whitelisting of IPs in pglgui
3. use IP_REMOVE
4. use right-click whitelisting of ports in pglgui (security risk!)

---

