---
title: "Broken Packages"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by shoaibi on 2008-06-28
i was installing some software and then i saw the red stop sign appear in my notification area. It says that i have 2 broken packages. How do i locate them and uninstall them???


```

#dpkg -l
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                            Description
+++-==========================================-==================================-============================================
ii  acl                                        2.2.45-1                           Access control list utilities
ii  acpi                                       0.09-3ubuntu1                      displays information on ACPI devices
ii  acpi-support                               0.109                              a collection of useful events for acpi
ii  acpid                                      1.0.4-5ubuntu9                     Utilities for using ACPI power management
ii  adduser                                    3.105ubuntu1                       add and remove users and groups
ii  alacarte                                   0.11.5-0ubuntu1                    easy GNOME menu editing tool
ii  alsa-base                                  1.0.16-0ubuntu4                    ALSA driver configuration files
ii  alsa-utils                                 1.0.15-3ubuntu2                    ALSA utilities
ii  anacron                                    2.3-13ubuntu2                      cron-like program that doesn't go by time
ii  apmd                                       3.2.2-8.1ubuntu1                   Utilities for Advanced Power Management (APM
ii  app-install-data                           0.5.10.3                           Ubuntu applications (data files)
ii  app-install-data-commercial                9                                  Application Installer (data files for commer
ii  apparmor                                   2.1+1075-0ubuntu9.1                User-space parser utility for AppArmor
ii  apparmor-utils                             2.1+1075-0ubuntu9.1                Utilities for controlling AppArmor
ii  apport                                     0.108.2                            automatically generate crash reports for deb
ii  apport-gtk                                 0.108.2                            GTK+ frontend for the apport crash report sy
ii  apt                                        0.7.9ubuntu17                      Advanced front-end for dpkg
ii  apt-utils                                  0.7.9ubuntu17                      APT utility programs
ii  aptitude                                   0.4.9-2ubuntu5                     terminal-based package manager
ii  apturl                                     0.2.2ubuntu1                       Install package with the apt protocol
ii  aspell                                     0.60.5-1ubuntu2                    GNU Aspell spell-checker
ii  aspell-en                                  6.0-0-5.1                          English dictionary for GNU Aspell
ii  at                                         3.1.10ubuntu4                      Delayed job execution and batch processing
ii  at-spi                                     1.22.1-0ubuntu1                    Assistive Technology Service Provider Interf
ii  avahi-autoipd                              0.6.22-2ubuntu4                    Avahi IPv4LL network address configuration d
ii  avahi-daemon                               0.6.22-2ubuntu4                    Avahi mDNS/DNS-SD daemon
ii  base-files                                 4.0.1ubuntu5                       Debian base system miscellaneous files
ii  base-passwd                                3.5.16                             Debian base system master password and group
ii  bash                                       3.2-0ubuntu18                      The GNU Bourne Again SHell
ii  bash-completion                            20060301-3ubuntu3                  programmable completion for the bash shell
ii  bc                                         1.06.94-3ubuntu1                   The GNU bc arbitrary precision calculator la
ii  belocs-locales-bin                         2.4-2.2ubuntu7                     tools for compiling locale data files
ii  bind9-host                                 1:9.4.2-10                         Version of 'host' bundled with BIND 9.X
ii  binutils                                   2.18.1~cvs20080103-0ubuntu1        The GNU assembler, linker and binary utiliti
ii  binutils-static                            2.18.1~cvs20080103-0ubuntu1        statically linked binutils tools
ii  bluez-audio                                3.26-0ubuntu6                      Bluetooth audio support
ii  bluez-cups                                 3.26-0ubuntu6                      Bluetooth printer driver for CUPS
ii  bluez-gnome                                0.25-0ubuntu1                      Bluetooth utilities for GNOME
ii  bluez-utils                                3.26-0ubuntu6                      Bluetooth tools and daemons
ii  bogofilter                                 1.1.5-2ubuntu5                     a fast Bayesian spam filter (dummy package)
ii  bogofilter-bdb                             1.1.5-2ubuntu5                     a fast Bayesian spam filter (Berkeley DB)
ii  bogofilter-common                          1.1.5-2ubuntu5                     a fast Bayesian spam filter (common files)
ii  brasero                                    0.7.1-3ubuntu1                     CD/DVD burning application for GNOME
ii  brltty                                     3.9-6ubuntu1                       Access software for a blind person using a b
ii  brltty-x11                                 3.9-6ubuntu1                       Access software for a blind person using a b
ii  bsdmainutils                               6.1.10ubuntu2                      collection of more utilities from FreeBSD
ii  bsdutils                                   1:2.13.1-5ubuntu2                  Basic utilities from 4.4BSD-Lite
ii  bug-buddy                                  2.22.0+dfsg-2                      GNOME Desktop Environment bug reporting tool
ii  busybox-initramfs                          1:1.1.3-5ubuntu12                  Standalone shell setup for initramfs
ii  bzip2                                      1.0.4-2ubuntu4                     high-quality block-sorting file compressor -
ii  ca-certificates                            20070303-0ubuntu3                  Common CA Certificates PEM files
ii  capplets-data                              1:2.22.1-0ubuntu4.1                configuration applets for GNOME 2 - data fil
ii  cdparanoia                                 3.10+debian~pre0-6                 audio extraction tool for sampling CDs
ii  cdrdao                                     1:1.2.2-8ubuntu3                   records CDs in Disk-At-Once (DAO) mode
ii  cli-common                                 0.5.6                              common files between all CLI packages
ii  command-not-found                          0.2.17ubuntu1                      Suggest installation of packages in interact
ii  command-not-found-data                     0.2.17ubuntu1                      Set of data files for command-not-found.
ii  compiz                                     1:0.7.4-0ubuntu7                   OpenGL window and compositing manager
ii  compiz-core                                1:0.7.4-0ubuntu7                   OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                     Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                     Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.7.4-0ubuntu7                   OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.4-0ubuntu7                   OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                     Settings library for plugins - OpenCompositi
ii  console-setup                              1.21ubuntu8                        Set up the font and the keyboard on the cons
ii  console-terminus                           4.20-6                             Fixed-width fonts for fast reading on the Li
ii  console-tools                              1:0.2.3dbs-65ubuntu7               Linux console and font utilities
ii  consolekit                                 0.2.3-3ubuntu5                     framework for defining and tracking users, s
ii  contact-lookup-applet                      0.16-1                             contact lookup applet for GNOME
ii  coreutils                                  6.10-3ubuntu2                      The GNU core utilities
ii  cpio                                       2.9-6ubuntu1                       GNU cpio -- a program to manage archives of 
ii  cpp                                        4:4.2.3-1ubuntu6                   The GNU C preprocessor (cpp)
ii  cpp-4.2                                    4.2.3-2ubuntu7                     The GNU C preprocessor
ii  cron                                       3.0pl1-100ubuntu2                  management of regular background processing
ii  cups-pdf                                   2.4.6-4ubuntu2                     PDF printer for CUPS
ii  cupsddk                                    1.2.0-0ubuntu1                     CUPS Driver Development Kit
ii  cupsddk-drivers                            1.2.0-0ubuntu1                     CUPS Driver Development Kit - Driver files
ii  cupsys                                     1.3.7-1ubuntu3                     Common UNIX Printing System(tm) - server
ii  cupsys-bsd                                 1.3.7-1ubuntu3                     Common UNIX Printing System(tm) - BSD comman
ii  cupsys-client                              1.3.7-1ubuntu3                     Common UNIX Printing System(tm) - client pro
ii  cupsys-common                              1.3.7-1ubuntu3                     Common UNIX Printing System(tm) - common fil
ii  cupsys-driver-gutenprint                   5.0.2-2ubuntu1                     printer drivers for CUPS
ii  dash                                       0.5.4-8ubuntu1                     POSIX-compliant shell
ii  dbus                                       1.1.20-1ubuntu2                    simple interprocess messaging system
ii  dbus-x11                                   1.1.20-1ubuntu2                    simple interprocess messaging system (X11 de
ii  dc                                         1.06.94-3ubuntu1                   The GNU dc arbitrary precision reverse-polis
ii  dcraw                                      8.80-1                             decode raw digital camera images
ii  debconf                                    1.5.20                             Debian configuration management system
ii  debconf-i18n                               1.5.20                             full internationalization support for debcon
ii  debianutils                                2.28.2-0ubuntu1                    Miscellaneous utilities specific to Debian
ii  defoma                                     0.11.10-0.2                        Debian Font Manager -- automatic font config
ii  deskbar-applet                             2.22.2.1-0ubuntu1                  universal search and navigation bar for GNOM
ii  desktop-file-utils                         0.15-1ubuntu4                      Utilities for .desktop files
ii  dhcdbd                                     3.0-1ubuntu1                       D-Bus interface to the ISC DHCP client
ii  dhcp3-client                               3.0.6.dfsg-1ubuntu9                DHCP client
ii  dhcp3-common                               3.0.6.dfsg-1ubuntu9                common files used by all the dhcp3* packages
ii  dictionaries-common                        0.90.0ubuntu2                      Common utilities for spelling dictionary too
ii  diff                                       2.8.1-12ubuntu1                    File comparison utilities
ii  displayconfig-gtk                          0.3.10                             Simple tool to change xserver settings
ii  diveintopython                             5.4-2ubuntu2                       free Python book for experienced programmers
ii  dmidecode                                  2.9-1ubuntu1                       Dump Desktop Management Interface data
ii  dmz-cursor-theme                           0.4.1                              Style neutral, scalable cursor theme
ii  dnsutils                                   1:9.4.2-10                         Clients provided with BIND
ii  doc-base                                   0.8.7                              utilities to manage online documentation
ii  docbook-xml                                4.5-5                              standard XML documentation system, for softw
ii  dosfstools                                 2.11-2.3ubuntu1                    Utilities to create and check MS-DOS FAT fil
ii  dpkg                                       1.14.16.6ubuntu4                   package maintenance system for Debian
ii  dvd+rw-tools                               7.0-9ubuntu1                       DVD+-RW/R tools
ii  e2fslibs                                   1.40.8-2ubuntu2                    ext2 filesystem libraries
ii  e2fsprogs                                  1.40.8-2ubuntu2                    ext2 file system utilities and libraries
ii  ed                                         0.7-1ubuntu1                       The classic unix line editor
ii  eject                                      2.1.5-6                            ejects CDs and operates CD-Changers under Li
ii  ekiga                                      2.0.12-0ubuntu2                    H.323 and SIP compatible VoIP client
ii  eog                                        2.22.2-0ubuntu1                    Eye of GNOME graphics viewer program
ii  esound-common                              0.2.38-0ubuntu9                    Enlightened Sound Daemon - Common files
ii  espeak                                     1.36-0ubuntu1                      A multi-lingual software speech synthesizer
ii  espeak-data                                1.36-0ubuntu1                      A multi-lingual software speech synthesizer:
ii  ethtool                                    6-0                                display or change ethernet card settings
ii  evince                                     2.22.2-0ubuntu1                    Document (postscript, pdf) viewer
ii  evolution                                  2.22.2-0ubuntu2                    groupware suite with mail client and organiz
ii  evolution-common                           2.22.2-0ubuntu2                    architecture independent files for Evolution
ii  evolution-data-server                      2.22.2-0ubuntu2                    evolution database backend server
ii  evolution-data-server-common               2.22.2-0ubuntu2                    architecture independent files for Evolution
ii  evolution-exchange                         2.22.2-0ubuntu1                    Exchange plugin for the Evolution groupware 
ii  evolution-plugins                          2.22.2-0ubuntu2                    standard plugins for Evolution
ii  evolution-webcal                           2.21.92-0ubuntu1                   webcal: URL handler for GNOME and Evolution
ii  example-content                            31                                 Ubuntu example content
ii  f-spot                                     0.4.2-1ubuntu3                     personal photo management application
ii  fast-user-switch-applet                    2.22.0-0ubuntu2                    Applet for the GNOME panel providing a menu 
ii  fdutils                                    5.5-20060227-1.1                   Linux floppy utilities
ii  file                                       4.21-3ubuntu1                      Determines file type using "magic" numbers
ii  file-roller                                2.22.3-0ubuntu1                    an archive manager for GNOME
ii  findutils                                  4.2.32-1ubuntu2                    utilities for finding files--find, xargs
ii  finger                                     0.17-11                            user information lookup program
ii  firefox                                    3.0+nobinonly-0ubuntu0.8.04.1      meta package for the popular mozilla web bro
ii  firefox-3.0                                3.0+nobinonly-0ubuntu0.8.04.1      safe and easy web browser from Mozilla
ii  firefox-3.0-gnome-support                  3.0+nobinonly-0ubuntu0.8.04.1      Support for Gnome in Mozilla Firefox
ii  firefox-gnome-support                      3.0+nobinonly-0ubuntu0.8.04.1      meta package pointing to the latest gnome-su
ii  fontconfig                                 2.5.0-2ubuntu3                     generic font configuration library - support
ii  fontconfig-config                          2.5.0-2ubuntu3                     generic font configuration library - configu
ii  foo2zjs                                    20071205-0ubuntu3                  Support for printing to ZjStream-based print
ii  foomatic-db                                20080211-0ubuntu1                  OpenPrinting printer support - database
ii  foomatic-db-engine                         3.0.2-20070719-0ubuntu4            OpenPrinting printer support - programs
ii  foomatic-db-hpijs                          20070813-0ubuntu2                  OpenPrinting printer support - database for 
ii  foomatic-filters                           3.0.2-20071204-0ubuntu2.1          OpenPrinting printer support - filters
ii  fortune-mod                                1:1.99.1-3ubuntu3                  provides fortune cookies on demand
ii  fortunes-min                               1:1.99.1-3ubuntu3                  Data files containing fortune cookies
ii  freeglut3                                  2.4.0-6                            OpenGL Utility Toolkit
ii  friendly-recovery                          0.1.2                              Make recovery more user-friendly
ii  ftp                                        0.17-16build1                      The FTP client
ii  fuse-utils                                 2.7.2-1ubuntu2                     Filesystem in USErspace (utilities)
ii  gamin                                      0.1.9-2ubuntu2                     File and directory monitoring system
ii  gcalctool                                  5.22.2-0ubuntu1                    A GTK2 desktop calculator
ii  gcc                                        4:4.2.3-1ubuntu6                   The GNU C compiler
ii  gcc-4.2                                    4.2.3-2ubuntu7                     The GNU C compiler
ii  gcc-4.2-base                               4.2.3-2ubuntu7                     The GNU Compiler Collection (base package)
ii  gconf-editor                               2.22.0-0ubuntu2                    An editor for the GConf configuration system
ii  gconf2                                     2.22.0-0ubuntu3                    GNOME configuration database system (support
ii  gconf2-common                              2.22.0-0ubuntu3                    GNOME configuration database system (common 
ii  gdb                                        6.8-1ubuntu2                       The GNU Debugger
ii  gdebi                                      0.3.8                              Simple tool to install deb files
ii  gdebi-core                                 0.3.8                              Simple tool to install deb files
ii  gdm                                        2.20.6-0ubuntu2                    GNOME Display Manager
ii  gedit                                      2.22.3-0ubuntu1                    official text editor of the GNOME desktop en
ii  gedit-common                               2.22.3-0ubuntu1                    official text editor of the GNOME desktop en
ii  genisoimage                                9:1.1.6-1ubuntu6                   Creates ISO-9660 CD-ROM filesystem images
ii  gettext-base                               0.17-2ubuntu1                      GNU Internationalization utilities for the b
ii  ghostscript                                8.61.dfsg.1-1ubuntu3               The GPL Ghostscript PostScript/PDF interpret
ii  ghostscript-x                              8.61.dfsg.1-1ubuntu3               The GPL Ghostscript PostScript/PDF interpret
ii  gimp                                       2.4.5-1ubuntu2                     The GNU Image Manipulation Program
ii  gimp-data                                  2.4.5-1ubuntu2                     Data files for GIMP
ii  gimp-gnomevfs                              2.4.5-1ubuntu2                     GNOME-VFS URI plugin for GIMP
ii  gimp-help-common                           2.4.0-2                            Data files for the GIMP documentation
ii  gimp-help-en                               2.4.0-2                            Documentation for the GIMP (English)
ii  gimp-python                                2.4.5-1ubuntu2                     Python support and plugins for GIMP
ii  gksu                                       2.0.0-5ubuntu3                     graphical frontend to su
ii  gnome-about                                1:2.22.2-0ubuntu3                  The GNOME about box
ii  gnome-accessibility-themes                 2.22.0-0ubuntu1                    accessibility themes for the GNOME 2 desktop
ii  gnome-app-install                          0.5.2.8-0ubuntu1                   GNOME Application Installer
ii  gnome-applets                              2.22.2-0ubuntu2                    Various applets for GNOME 2 panel - binary f
ii  gnome-applets-data                         2.22.2-0ubuntu2                    Various applets for GNOME 2 panel - data fil
ii  gnome-cards-data                           1:2.22.2.1-0ubuntu1                data files for the GNOME card games
ii  gnome-control-center                       1:2.22.1-0ubuntu4.1                utilities to configure the GNOME desktop
ii  gnome-desktop-data                         1:2.22.2-0ubuntu3                  Common files for GNOME 2 desktop apps
ii  gnome-doc-utils                            0.12.2-1ubuntu1                    a collection of documentation utilities for 
ii  gnome-games                                1:2.22.2.1-0ubuntu1                games for the GNOME desktop
ii  gnome-games-data                           1:2.22.2.1-0ubuntu1                data files for the GNOME games
ii  gnome-icon-theme                           2.22.0-1ubuntu2                    GNOME Desktop icon theme
ii  gnome-keyring                              2.22.2-0ubuntu1                    GNOME keyring services (daemon and tools)
ii  gnome-mag                                  1:0.15.0-0ubuntu1                  a screen magnifier for the GNOME desktop
ii  gnome-media                                2.22.0-0ubuntu3                    GNOME media utilities
ii  gnome-media-common                         2.22.0-0ubuntu3                    GNOME media utilities - common files
ii  gnome-menus                                2.22.2-0ubuntu1                    an implementation of the freedesktop menu sp
ii  gnome-mime-data                            2.18.0-1                           base MIME and Application database for GNOME
ii  gnome-mount                                0.8~svn20080225-0ubuntu4           wrapper for (un)mounting and ejecting storag
ii  gnome-netstatus-applet                     2.12.1-1ubuntu1                    Network status applet for GNOME 2
ii  gnome-nettool                              2.22.0-0ubuntu2                    network information tool for GNOME
ii  gnome-orca                                 2.22.1-0ubuntu1                    Scriptable screen reader
ii  gnome-panel                                1:2.22.2-0ubuntu1                  launcher and docking facility for GNOME
ii  gnome-panel-data                           1:2.22.2-0ubuntu1                  common files for the GNOME Panel
ii  gnome-pilot                                2.0.15-2ubuntu3                    A GNOME applet for management of your Palm P
ii  gnome-pilot-conduits                       2.0.15-1ubuntu2                    conduits for gnome-pilot
ii  gnome-power-manager                        2.22.1-1ubuntu4                    frontend for gnome-powermanager
ii  gnome-screensaver                          2.22.2-0ubuntu1                    GNOME screen saver and locker
ii  gnome-session                              2.22.1.1-0ubuntu2                  The GNOME 2 Session Manager
ii  gnome-settings-daemon                      2.22.1-0ubuntu2                    GNOME settings daemon
ii  gnome-spell                                1.0.7-1ubuntu2                     GNOME/Bonobo component for spell checking
ii  gnome-system-monitor                       2.22.1-0ubuntu2                    Process viewer and system resource monitor f
ii  gnome-system-tools                         2.22.0-0ubuntu9                    Cross-platform configuration utilities for G
ii  gnome-terminal                             2.22.1-0ubuntu2                    The GNOME 2 terminal emulator application
ii  gnome-terminal-data                        2.22.1-0ubuntu2                    Data files for the GNOME terminal emulator
ii  gnome-themes                               2.22.0-0ubuntu1                    official themes for the GNOME 2 desktop
ii  gnome-user-guide                           2.22.0+svn20080407ubuntu1          GNOME user's guide
ii  gnome-utils                                2.20.0.1-1ubuntu5                  GNOME desktop utilities
ii  gnome-volume-manager                       2.22.1-1ubuntu6                    GNOME daemon to auto-mount and manage media 
ii  gnupg                                      1.4.6-2ubuntu5                     GNU privacy guard - a free PGP replacement
ii  gpgv                                       1.4.6-2ubuntu5                     GNU privacy guard - signature verification t
ii  grep                                       2.5.3~dfsg-3                       GNU grep, egrep and fgrep
ii  groff-base                                 1.18.1.1-16                        GNU troff text-formatting system (base syste
ii  grub                                       0.97-29ubuntu21                    GRand Unified Bootloader
ii  gsfonts                                    1:8.11+urwcyr1.0.7~pre43-1         Fonts for the Ghostscript interpreter(s)
ii  gstreamer0.10-alsa                         0.10.18-3                          GStreamer plugin for ALSA
ii  gstreamer0.10-gnomevfs                     0.10.18-3                          GStreamer plugin for GnomeVFS
ii  gstreamer0.10-plugins-base                 0.10.18-3                          GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps            0.10.18-3                          GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good                 0.10.7-3ubuntu0.1                  GStreamer plugins from the "good" set
ii  gstreamer0.10-pulseaudio                   0.9.7-2                            GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                        0.10.18-4ubuntu1                   Tools for use with GStreamer
ii  gstreamer0.10-x                            0.10.18-3                          GStreamer plugins for X11 and Pango
ii  gtk2-engines                               1:2.14.1-0ubuntu1                  theme engines for GTK+ 2.x
ii  gtk2-engines-murrine                       0.53.1-1ubuntu1                    cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf                        2.12.9-3ubuntu4                    Pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-ubuntulooks                   0.9.12-11                          'ubuntulooks' theme for GTK+ 2.x
ii  gtkhtml3.14                                3.18.2-0ubuntu1                    HTML rendering/editing library - bonobo comp
ii  gucharmap                                  1:2.22.1-0ubuntu2                  Unicode character picker and font browser
ii  guidance-backends                          0.8.0svn20080103-0ubuntu16.1       collection of system administration tools fo
ii  guile-1.6-libs                             1.6.8-6ubuntu1                     Main Guile libraries
ii  gvfs                                       0.2.4-0ubuntu1                     userspace virtual filesystem - server
ii  gvfs-backends                              0.2.4-0ubuntu1                     userspace virtual filesystem - backends
ii  gvfs-fuse                                  0.2.4-0ubuntu1                     userspace virtual filesystem - fuse server
ii  gzip                                       1.3.12-3.2                         The GNU compression utility
ii  hal                                        0.5.11~rc2-1ubuntu8.1              Hardware Abstraction Layer
ii  hal-cups-utils                             0.6.13+svn86-0ubuntu4              CUPS integration with HAL
ii  hal-info                                   20080508+git20080601-0ubuntu0.8.04 Hardware Abstraction Layer - fdi files
ii  hdparm                                     8.6-1ubuntu1                       tune hard disk parameters for high performan
ii  hicolor-icon-theme                         0.10-1ubuntu1                      default fallback theme for FreeDesktop.org i
ii  hostname                                   2.94                               utility to set/show the host name or domain 
ii  hotkey-setup                               0.1-17ubuntu21                     auto-configures laptop hotkeys
ii  hpijs                                      2.8.2+2.8.2-0ubuntu8               HP Linux Printing and Imaging - gs IJS drive
ii  hplip                                      2.8.2-0ubuntu8                     HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                                 2.8.2-0ubuntu8                     HP Linux Printing and Imaging - data files
ii  human-icon-theme                           0.28                               Human Icon theme
ii  human-theme                                0.18                               Human theme
ii  hwtest                                     0.1-0ubuntu10                      Hardware Testing
ii  hwtest-gtk                                 0.1-0ubuntu10                      GTK interface for the hwtest program
ii  iamerican                                  3.1.20.0-4.4                       An American English dictionary for ispell
ii  ibritish                                   3.1.20.0-4.4                       A British English dictionary for ispell
ii  ifupdown                                   0.6.8ubuntu8                       high level tools to configure network interf
ii  im-switch                                  1.16ubuntu1                        Input method switch framework
ii  info                                       4.11.dfsg.1-4                      Standalone GNU Info documentation browser
ii  initramfs-tools                            0.85eubuntu39.1                    tools for generating an initramfs
ii  initscripts                                2.86.ds1-14.1ubuntu45              Scripts for initializing and shutting down t
ii  inputattach                                1.23-0ubuntu2                      utility to attach serial devices to the inpu
ii  iproute                                    20071016-2ubuntu1                  Professional tools to control the networking
ii  iptables                                   1.3.8.0debian1-1ubuntu2            administration tools for packet filtering an
ii  iputils-arping                             3:20071127-1                       Tool to send ICMP echo requests to an ARP ad
ii  iputils-ping                               3:20071127-1                       Tools to test the reachability of network ho
ii  iputils-tracepath                          3:20071127-1                       Tools to trace the network path to a remote 
ii  iso-codes                                  1.7-1ubuntu1                       ISO language, territory, currency, script co
ii  ispell                                     3.1.20.0-4.4                       International Ispell (an interactive spellin
ii  jockey-common                              0.3.3-0ubuntu8                     user interface and desktop integration for d
ii  jockey-gtk                                 0.3.3-0ubuntu8                     GNOME user interface and desktop integration
iU  kannel                                     1.4.1-1sarge.1                     WAP and SMS gateway
ii  kannel-docs                                1.4.1-1sarge.1                     WAP and SMS gateway documentation
iU  kannel-extras                              1.4.1-1sarge.1                     WAP and SMS gateway extras
ii  klibc-utils                                1.5.7-4ubuntu4                     small statically-linked utilities built with
ii  klogd                                      1.5-1ubuntu1                       Kernel Logging Daemon
ii  landscape-client                           0.1                                Placeholder for the Landscape client
ii  language-pack-en                           1:8.04+20080527                    translation updates for language English
ii  language-pack-en-base                      1:8.04+20080527                    translations for language English
ii  language-pack-gnome-en                     1:8.04+20080527                    GNOME translation updates for language Engli
ii  language-pack-gnome-en-base                1:8.04+20080527                    GNOME translations for language English
ii  language-selector                          0.3.4                              Language selector for ubuntu linux
ii  language-selector-common                   0.3.4                              Language selector for ubuntu linux
ii  language-support-en                        1:8.04+20080218                    metapackage for English language support
ii  language-support-translations-en           1:8.04+20080407                    Additional translations metapackage for Engl
ii  language-support-writing-en                1:8.04+20080410                    Writing aids metapackage for English
ii  laptop-detect                              0.13.2ubuntu1                      attempt to detect a laptop
ii  laptop-mode-tools                          1.35-1ubuntu1                      Scripts to spin down hard drive and save pow
ii  launchpad-integration                      0.1.19                             launchpad integration
ii  less                                       418-1                              Pager program similar to more
ii  lftp                                       3.6.1-1                            Sophisticated command-line FTP/HTTP client p
ii  libaa1                                     1.4p5-33ubuntu1                    ascii art library
ii  libacl1                                    2.2.45-1                           Access control list shared library
ii  libalut0                                   1.1.0-1                            OpenAL Utility Toolkit
ii  libao2                                     0.8.8-3                            Cross Platform Audio Output Library
ii  libapm1                                    3.2.2-8.1ubuntu1                   Library for interacting with APM driver in k
ii  libarchive1                                2.2.4-1ubuntu1                     Single library to read/write tar, cpio, pax,
ii  libart-2.0-2                               2.3.20-1                           Library of functions for 2D graphics - runti
ii  libart2.0-cil                              2.20.0-2ubuntu3                    CLI binding for libart 2.3
ii  libasound2                                 1.0.15-3ubuntu4                    ALSA library
ii  libaspell15                                0.60.5-1ubuntu2                    GNU Aspell spell-checker runtime library
ii  libatk1.0-0                                1.22.0-0ubuntu1                    The ATK accessibility toolkit
ii  libatm1                                    2.4.1-17.1build1                   shared library for ATM (Asynchronous Transfe
ii  libatspi1.0-0                              1.22.1-0ubuntu1                    C binding libraries of at-spi for GNOME Acce
ii  libattr1                                   1:2.4.39-1                         Extended attribute shared library
ii  libaudiofile0                              0.2.6-7ubuntu1                     Open-source version of SGI's audiofile libra
ii  libavahi-client3                           0.6.22-2ubuntu4                    Avahi client library
ii  libavahi-common-data                       0.6.22-2ubuntu4                    Avahi common data files
ii  libavahi-common3                           0.6.22-2ubuntu4                    Avahi common library
ii  libavahi-compat-libdnssd1                  0.6.22-2ubuntu4                    Avahi Apple Bonjour compatibility library
ii  libavahi-core5                             0.6.22-2ubuntu4                    Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-glib1                             0.6.22-2ubuntu4                    Avahi glib integration library
ii  libavahi-ui0                               0.6.22-2ubuntu4                    Avahi GTK User interface library
ii  libavc1394-0                               0.5.3-1build1                      control IEEE 1394 audio/video devices
ii  libbeagle1                                 0.3.0-2ubuntu1                     library for accessing beagle using C
ii  libbind9-30                                1:9.4.2-10                         BIND9 Shared Library used by BIND
ii  libblkid1                                  1.40.8-2ubuntu2                    block device id library
ii  libbluetooth2                              3.29-0ubuntu1                      Library to use the BlueZ Linux Bluetooth sta
ii  libbonobo2-0                               2.22.0-0ubuntu1                    Bonobo CORBA interfaces library
ii  libbonobo2-common                          2.22.0-0ubuntu1                    Bonobo CORBA interfaces library -- support f
ii  libbonoboui2-0                             2.21.90-1                          The Bonobo UI library
ii  libbonoboui2-common                        2.21.90-1                          The Bonobo UI library -- common files
ii  libbrlapi0.5                               3.9-6ubuntu1                       braille display access via BRLTTY - shared l
ii  libbz2-1.0                                 1.0.4-2ubuntu4                     high-quality block-sorting file compressor l
ii  libc6                                      2.7-10ubuntu3                      GNU C Library: Shared libraries
ii  libc6-i686                                 2.7-10ubuntu3                      GNU C Library: Shared libraries [i686 optimi
ii  libcaca0                                   0.99.beta13b-4                     colour ASCII art library
ii  libcairo-perl                              1.043-1                            Perl interface to the Cairo graphics library
ii  libcairo2                                  1.6.0-0ubuntu1                     The Cairo 2D vector graphics library
ii  libcairomm-1.0-1                           1.4.2-1                            C++ wrappers for Cairo (shared libraries)
ii  libcamel1.2-11                             2.22.2-0ubuntu2                    The Evolution MIME message handling library
ii  libcap1                                    1:1.10-14build1                    support for getting/setting POSIX.1e capabil
ii  libcdio-cdda0                              0.78.2+dfsg1-2ubuntu1              library to read and control digital audio CD
ii  libcdio-paranoia0                          0.78.2+dfsg1-2ubuntu1              library to read digital audio CDs with error
ii  libcdio7                                   0.78.2+dfsg1-2ubuntu1              library to read and control CD-ROM
ii  libcdparanoia0                             3.10+debian~pre0-6                 audio extraction tool for sampling CDs (libr
ii  libchromexvmc1                             1:0.2.901-0ubuntu4                 XvMC Libraries used by the Openchrome VIA dr
ii  libchromexvmcpro1                          1:0.2.901-0ubuntu4                 XvMC Pro Libraries used by the Openchrome VI
ii  libck-connector0                           0.2.3-3ubuntu5                     ConsoleKit libraries
ii  libcomerr2                                 1.40.8-2ubuntu2                    common error description library
ii  libcompizconfig0                           0.7.4-0ubuntu1                     Settings library for plugins - OpenCompositi
ii  libconsole                                 1:0.2.3dbs-65ubuntu7               Shared libraries for Linux console and font 
ii  libcroco3                                  0.6.1-1build2                      a generic Cascading Style Sheet (CSS) parsin
ii  libcucul0                                  0.99.beta13b-4                     low-level Unicode character drawing library
ii  libcupsimage2                              1.3.7-1ubuntu3                     Common UNIX Printing System(tm) - image libs
ii  libcupsys2                                 1.3.7-1ubuntu3                     Common UNIX Printing System(tm) - libs
ii  libcurl3                                   7.18.0-1ubuntu2                    Multi-protocol file transfer library (OpenSS
ii  libcurl3-gnutls                            7.18.0-1ubuntu2                    Multi-protocol file transfer library (GnuTLS
ii  libcwidget3                                0.5.8-1ubuntu1                     high-level terminal interface library for C+
ii  libdaemon0                                 0.12-0.1                           lightweight C library for daemons
ii  libdatrie0                                 0.1.2-2                            Double-array trie library
ii  libdb4.6                                   4.6.21-6ubuntu1                    Berkeley v4.6 Database Libraries [runtime]
ii  libdbus-1-3                                1.1.20-1ubuntu2                    simple interprocess messaging system
ii  libdbus-glib-1-2                           0.74-2                             simple interprocess messaging system (GLib-b
ii  libdecoration0                             1:0.7.4-0ubuntu7                   Compiz window decoration library
ii  libdeskbar-tracker                         0.6.6-0ubuntu3.8.04.1              metadata database, indexer and search tool -
ii  libdevmapper1.02.1                         2:1.02.20-2ubuntu2                 The Linux Kernel Device Mapper userspace lib
ii  libdirectfb-1.0-0                          1.0.1-7ubuntu3                     direct frame buffer graphics - shared librar
ii  libdjvulibre15                             3.5.20-2                           Runtime support for the DjVu image format
ii  libdmx1                                    1:1.0.2-2build1                    X11 Distributed Multihead extension library
ii  libdns32                                   1:9.4.2-10                         DNS Shared Library used by BIND
ii  libdrm2                                    2.3.0-4ubuntu1                     Userspace interface to kernel DRM services -
ii  libdv4                                     1.0.0-1ubuntu1                     software library for DV format digital video
ii  libebook1.2-9                              2.22.2-0ubuntu2                    Client library for evolution address books
ii  libecal1.2-7                               2.22.2-0ubuntu2                    Client library for evolution calendars
ii  libedata-book1.2-2                         2.22.2-0ubuntu2                    Backend library for evolution address books
ii  libedata-cal1.2-6                          2.22.2-0ubuntu2                    Backend library for evolution calendars
ii  libedataserver1.2-9                        2.22.2-0ubuntu2                    Utility library for evolution data servers
ii  libedataserverui1.2-8                      2.22.2-0ubuntu2                    GUI utility library for evolution data serve
ii  libedit2                                   2.9.cvs.20050518-4                 BSD editline and history libraries
ii  libeel2-2                                  2.22.2-0ubuntu1                    Eazel Extensions Library (for GNOME2)
ii  libeel2-data                               2.22.2-0ubuntu1                    Eazel Extensions Library - data files (for G
ii  libegroupwise1.2-13                        2.22.2-0ubuntu2                    Client library for accessing groupwise POA t
ii  libelfg0                                   0.8.6-4                            an ELF object file access library
ii  libenchant1c2a                             1.3.0-5                            a wrapper library for various spell checker 
ii  libesd-alsa0                               0.2.38-0ubuntu9                    Enlightened Sound Daemon (ALSA) - Shared lib
ii  libespeak1                                 1.36-0ubuntu1                      A multi-lingual software speech synthesizer:
ii  libexchange-storage1.2-3                   2.22.2-0ubuntu2                    Backend library for evolution calendars
ii  libexempi3                                 1.99.9-1                           library to parse XMP metadata (Library)
ii  libexif12                                  0.6.16-2.1                         library to parse EXIF files
ii  libexpat1                                  2.0.1-0ubuntu1                     XML parsing C library - runtime library
ii  libffi4                                    4.2.3-2ubuntu7                     Foreign Function Interface library runtime
ii  libflac8                                   1.2.1-1ubuntu2                     Free Lossless Audio Codec - runtime C librar
ii  libflickrnet2.1.5-cil                      25277-6build1                      Flickr.Net API Library
ii  libfontconfig1                             2.5.0-2ubuntu3                     generic font configuration library - runtime
ii  libfontenc1                                1:1.0.4-2                          X11 font encoding library
ii  libfreetype6                               2.3.5-1ubuntu4                     FreeType 2 font engine, shared library files
ii  libfribidi0                                0.10.9-1                           Free Implementation of the Unicode BiDi algo
ii  libfs6                                     2:1.0.0-4ubuntu2                   X11 Font Services library
ii  libfuse2                                   2.7.2-1ubuntu2                     Filesystem in USErspace library
ii  libgadu3                                   1:1.7~rc2-2                        Gadu-Gadu protocol library - runtime files
ii  libgail-common                             1.22.1-0ubuntu1                    GNOME Accessibility Implementation Library -
ii  libgail-gnome-module                       1.20.0-1                           GNOME Accessibility Implementation Module fo
ii  libgail18                                  1.22.1-0ubuntu1                    GNOME Accessibility Implementation Library -
ii  libgamin0                                  0.1.9-2ubuntu2                     Client library for the gamin file and direct
ii  libgc1c2                                   1:6.8-1.1                          conservative garbage collector for C and C++
ii  libgcc1                                    1:4.2.3-2ubuntu7                   GCC support library
ii  libgconf2-4                                2.22.0-0ubuntu3                    GNOME configuration database system (shared 
ii  libgconf2.0-cil                            2.20.0-2ubuntu3                    CLI binding for GConf 2.20
ii  libgcrypt11                                1.2.4-2ubuntu7                     LGPL Crypto library - runtime library
ii  libgd2-noxpm                               2.0.35.dfsg-3ubuntu2               GD Graphics Library version 2 (without XPM s
ii  libgdata-google1.2-1                       2.22.2-0ubuntu2                    Client library for accessing google POA thro
ii  libgdata1.2-1                              2.22.2-0ubuntu2                    Client library for accessing google POA thro
ii  libgdbm3                                   1.8.3-3                            GNU dbm database routines (runtime version)
ii  libggz2                                    0.0.14-1                           GGZ Gaming Zone: common utilities library
ii  libggzcore9                                0.0.14-2                           GGZ Gaming Zone: core client frontend librar
ii  libggzmod4                                 0.0.14-2                           GGZ Gaming Zone: game frontend library
ii  libgimp2.0                                 2.4.5-1ubuntu2                     Libraries for the GNU Image Manipulation Pro
ii  libgksu2-0                                 2.0.5-1ubuntu5.1                   library providing su and sudo functionality
ii  libgl1-mesa-dri                            7.0.3~rc2-1ubuntu3                 A free implementation of the OpenGL API -- D
ii  libgl1-mesa-glx                            7.0.3~rc2-1ubuntu3                 A free implementation of the OpenGL API -- G
ii  libglade2-0                                1:2.6.2-1                          library to load .glade files at runtime
ii  libglade2.0-cil                            2.12.0-2ubuntu3                    CLI binding for the Glade libraries 2.6
ii  libglew1.5                                 1.5.0dfsg1-3ubuntu1                The OpenGL Extension Wrangler - runtime envi
ii  libglib-perl                               1:1.161-1                          Perl interface to the GLib and GObject libra
ii  libglib2.0-0                               2.16.3-1ubuntu3                    The GLib library of C routines
ii  libglib2.0-cil                             2.12.0-2ubuntu3                    CLI binding for the GLib utility library 2.1
ii  libglibmm-2.4-1c2a                         2.16.0-1                           C++ wrapper for the GLib toolkit (shared lib
ii  libglu1-mesa                               7.0.3~rc2-1ubuntu3                 The OpenGL utility library (GLU)
ii  libglut3                                   3.7-25                             the OpenGL Utility Toolkit
ii  libgmime-2.0-2                             2.2.11-2ubuntu1                    MIME library
ii  libgmime2.2-cil                            2.2.11-2ubuntu1                    CLI binding for the MIME library
ii  libgnome-desktop-2                         1:2.22.2-0ubuntu3                  Utility library for loading .desktop files -
ii  libgnome-keyring0                          2.22.2-0ubuntu1                    GNOME keyring services library
ii  libgnome-mag2                              1:0.15.0-0ubuntu1                  screen magnification library for the GNOME d
ii  libgnome-media0                            2.22.0-0ubuntu3                    runtime libraries for the GNOME media utilit
ii  libgnome-menu2                             2.22.2-0ubuntu1                    an implementation of the freedesktop menu sp
ii  libgnome-pilot2                            2.0.15-2ubuntu3                    Support libraries for gnome-pilot
ii  libgnome-speech7                           1:0.4.18-0ubuntu2                  GNOME text-to-speech library
ii  libgnome-vfs2.0-cil                        2.20.0-2ubuntu3                    CLI binding for GnomeVFS 2.20
ii  libgnome-window-settings1                  1:2.22.1-0ubuntu4.1                Utility library for getting window manager s
ii  libgnome2-0                                2.22.0-0ubuntu1                    The GNOME 2 library - runtime files
ii  libgnome2-canvas-perl                      1.002-1+b1ubuntu1                  Perl interface to the GNOME canvas library
ii  libgnome2-common                           2.22.0-0ubuntu1                    The GNOME 2 library - common files
ii  libgnome2-perl                             1.040-1                            Perl interface to the GNOME libraries
ii  libgnome2-vfs-perl                         1.080-1                            Perl interface to the 2.x series of the GNOM
ii  libgnome2.0-cil                            2.20.0-2ubuntu3                    CLI binding for GNOME 2.20
ii  libgnomecanvas2-0                          2.20.1.1-1                         A powerful object-oriented display - runtime
ii  libgnomecanvas2-common                     2.20.1.1-1                         A powerful object-oriented display - common 
ii  libgnomecups1.0-1                          0.2.3-1ubuntu1                     GNOME library for CUPS interaction
ii  libgnomekbd-common                         2.22.0-1                           GNOME library to manage keyboard configurati
ii  libgnomekbd2                               2.22.0-1                           GNOME library to manage keyboard configurati
ii  libgnomekbdui2                             2.22.0-1                           User interface library for libgnomekbd - sha
ii  libgnomeprint2.2-0                         2.18.4-1                           The GNOME 2.2 print architecture - runtime f
ii  libgnomeprint2.2-data                      2.18.4-1                           The GNOME 2.2 print architecture - data file
ii  libgnomeprintui2.2-0                       2.18.2-1                           GNOME 2.2 print architecture User Interface 
ii  libgnomeprintui2.2-common                  2.18.2-1                           GNOME 2.2 print architecture User Interface 
ii  libgnomeui-0                               2.22.1.0-0ubuntu2                  The GNOME 2 libraries (User Interface) - run
ii  libgnomeui-common                          2.22.1.0-0ubuntu2                  The GNOME 2 libraries (User Interface) - com
ii  libgnomevfs2-0                             1:2.22.0-2ubuntu1                  GNOME Virtual File System (runtime libraries
ii  libgnomevfs2-bin                           1:2.22.0-2ubuntu1                  GNOME Virtual File System (support binaries)
ii  libgnomevfs2-common                        1:2.22.0-2ubuntu1                  GNOME Virtual File System (common files)
ii  libgnomevfs2-extra                         1:2.22.0-2ubuntu1                  GNOME Virtual File System (extra modules)
ii  libgnutls13                                2.0.4-1ubuntu2.1                   the GNU TLS library - runtime library
ii  libgomp1                                   4.2.3-2ubuntu7                     GCC OpenMP (GOMP) support library
ii  libgpg-error0                              1.4-2ubuntu7                       library for common error values and messages
ii  libgpgme11                                 1.1.5-2ubuntu1                     GPGME - GnuPG Made Easy
ii  libgphoto2-2                               2.4.0-8ubuntu7                     gphoto2 digital camera library
ii  libgphoto2-port0                           2.4.0-8ubuntu7                     gphoto2 digital camera port library
ii  libgpmg1                                   1.19.6-25ubuntu1                   General Purpose Mouse - shared library
ii  libgpod-common                             0.6.0-3ubuntu3                     a library to read and write songs and artwor
ii  libgpod3                                   0.6.0-3ubuntu3                     a library to read and write songs and artwor
ii  libgraphviz4                               2.16-3ubuntu2                      rich set of graph drawing tools
ii  libgs8                                     8.61.dfsg.1-1ubuntu3               The Ghostscript PostScript/PDF interpreter L
ii  libgsf-1-114                               1.14.7-2ubuntu1                    Structured File Library - runtime version
ii  libgsf-1-common                            1.14.7-2ubuntu1                    Structured File Library - common files
ii  libgsl0ldbl                                1.10-4                             GNU Scientific Library (GSL) -- library pack
ii  libgstreamer-plugins-base0.10-0            0.10.18-3                          GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                         0.10.18-4ubuntu1                   Core GStreamer libraries and elements
ii  libgtk-vnc-1.0-0                           0.3.4-0ubuntu2                     A VNC viewer widget for GTK+ (runtime librar
ii  libgtk2-perl                               1:1.161-1                          Perl interface to the 2.x series of the Gimp
ii  libgtk2.0-0                                2.12.9-3ubuntu4                    The GTK+ graphical user interface library
ii  libgtk2.0-bin                              2.12.9-3ubuntu4                    The programs for the GTK+ graphical user int
ii  libgtk2.0-cil                              2.12.0-2ubuntu3                    CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                           2.12.9-3ubuntu4                    Common files for the GTK+ graphical user int
ii  libgtkhtml2-0                              2.11.1-1                           HTML rendering/editing library - runtime fil
ii  libgtkhtml3.14-19                          3.18.2-0ubuntu1                    HTML rendering/editing library - runtime fil
ii  libgtkhtml3.16-cil                         2.20.1-2ubuntu2                    CLI binding for GtkHTML 3.16
ii  libgtkmm-2.4-1c2a                          1:2.12.5-2                         C++ wrappers for GTK+ 2.4 (shared libraries)
ii  libgtksourceview-common                    1.8.5-1                            common files for the GTK+ syntax highlightin
ii  libgtksourceview1.0-0                      1.8.5-1                            shared libraries for the GTK+ syntax highlig
ii  libgtksourceview2.0-0                      2.2.1-1                            shared libraries for the GTK+ syntax highlig
ii  libgtksourceview2.0-common                 2.2.1-1                            common files for the GTK+ syntax highlightin
ii  libgtkspell0                               2.0.10-4                           a spell-checking addon for GTK's TextView wi
ii  libgtop2-7                                 2.22.0-0ubuntu1                    gtop system monitoring library
ii  libgtop2-common                            2.22.0-0ubuntu1                    common files for the gtop system monitoring 
ii  libgucharmap6                              1:2.22.1-0ubuntu2                  Unicode browser widget library (shared libra
ii  libguile-ltdl-1                            1.6.8-6ubuntu1                     Guile's patched version of libtool's libltdl
ii  libgutenprint2                             5.0.2-2ubuntu1                     runtime for the Gutenprint printer driver li
ii  libgvfscommon0                             0.2.4-0ubuntu1                     userspace virtual filesystem - library
ii  libgweather-common                         2.22.1.1-0ubuntu2                  GWeather shared library
ii  libgweather1                               2.22.1.1-0ubuntu2                  GWeather shared library
ii  libhal-storage1                            0.5.11~rc2-1ubuntu8.1              Hardware Abstraction Layer - shared library 
ii  libhal1                                    0.5.11~rc2-1ubuntu8.1              Hardware Abstraction Layer - shared library
ii  libhesiod0                                 3.0.2-18.1                         Libraries for hesiod, a service name resolut
ii  libhtml-parser-perl                        3.56-1                             A collection of modules that parse HTML text
ii  libhtml-tagset-perl                        3.10-2                             Data tables pertaining to HTML
ii  libhtml-tree-perl                          3.23-1                             represent and create HTML syntax trees
ii  libhunspell-1.1-0                          1.1.9-1                            spell checker and morphological analyzer (sh
ii  libice6                                    2:1.0.4-1                          X11 Inter-Client Exchange library
ii  libicu38                                   3.8-6                              International Components for Unicode
ii  libidl0                                    0.8.10-0.1                         library for parsing CORBA IDL files
ii  libidn11                                   1.1-1                              GNU libidn library, implementation of IETF I
ii  libiec61883-0                              1.1.0-2ubuntu2                     an partial implementation of IEC 61883
ii  libieee1284-3                              0.2.11-3                           cross-platform library for parallel port acc
ii  libisc32                                   1:9.4.2-10                         ISC Shared Library used by BIND
ii  libisccc30                                 1:9.4.2-10                         Command Channel Library used by BIND
ii  libisccfg30                                1:9.4.2-10                         Config File Handling Library used by BIND
ii  libiw29                                    29-1ubuntu2                        Wireless tools - library
ii  libjasper1                                 1.900.1-3                          The JasPer JPEG-2000 runtime library
ii  libjpeg62                                  6b-14                              The Independent JPEG Group's JPEG runtime li
ii  libkeyutils1                               1.2-4                              Linux Key Management Utilities (library)
ii  libklibc                                   1.5.7-4ubuntu4                     minimal libc subset for use with initramfs
ii  libkpathsea4                               2007.dfsg.1-2                      TeX Live: path search library for TeX (runti
ii  libkrb53                                   1.6.dfsg.3~beta1-2ubuntu1          MIT Kerberos runtime libraries
ii  liblaunchpad-integration1                  0.1.19                             library for launchpad integration
ii  liblcms1                                   1.16-7ubuntu1                      Color management library
ii  libldap-2.4-2                              2.4.9-0ubuntu0.8.04                OpenLDAP libraries
ii  liblircclient0                             0.8.3~pre1-0ubuntu7.1              LIRC client library
ii  liblocale-gettext-perl                     1.05-2ubuntu1                      Using libc functions for internationalizatio
ii  liblpint-bonobo0                           0.1.19                             library for launchpad integration
ii  libltdl3                                   1.5.26-1ubuntu1                    A system independent dlopen wrapper for GNU 
ii  liblwres30                                 1:9.4.2-10                         Lightweight Resolver Library used by BIND
ii  liblzo2-2                                  2.02-3                             data compression library
ii  libmagic1                                  4.21-3ubuntu1                      File type determination library using "magic
ii  libmagick10                                7:6.3.7.9.dfsg1-2ubuntu1           image manipulation library
ii  libmeanwhile1                              1.0.2-3                            open implementation of the Lotus Sametime Co
ii  libmetacity0                               1:2.22.0-0ubuntu4                  library of lightweight GTK2 based Window Man
ii  libmng1                                    1.0.9-1                            Multiple-image Network Graphics library
ii  libmono-addins-gui0.2-cil                  0.3.1-4                            GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                      0.3.1-4                            addin framework for extensible CLI applicati
ii  libmono-cairo1.0-cil                       1.2.6+dfsg-6ubuntu3                Mono Cairo library
ii  libmono-corlib1.0-cil                      1.2.6+dfsg-6ubuntu3                Mono core library (1.0)
ii  libmono-corlib2.0-cil                      1.2.6+dfsg-6ubuntu3                Mono core library (2.0)
ii  libmono-data-tds1.0-cil                    1.2.6+dfsg-6ubuntu3                Mono Data library
ii  libmono-data-tds2.0-cil                    1.2.6+dfsg-6ubuntu3                Mono Data Library
ii  libmono-security1.0-cil                    1.2.6+dfsg-6ubuntu3                Mono Security library
ii  libmono-security2.0-cil                    1.2.6+dfsg-6ubuntu3                Mono Security library
ii  libmono-sharpzip0.84-cil                   1.2.6+dfsg-6ubuntu3                Mono SharpZipLib library
ii  libmono-sharpzip2.84-cil                   1.2.6+dfsg-6ubuntu3                Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                      1.2.6+dfsg-6ubuntu3                Mono Sqlite library
ii  libmono-system-data1.0-cil                 1.2.6+dfsg-6ubuntu3                Mono System.Data library
ii  libmono-system-data2.0-cil                 1.2.6+dfsg-6ubuntu3                Mono System.Data Library
ii  libmono-system-web1.0-cil                  1.2.6+dfsg-6ubuntu3                Mono System.Web library
ii  libmono-system-web2.0-cil                  1.2.6+dfsg-6ubuntu3                Mono System.Web Library
ii  libmono-system1.0-cil                      1.2.6+dfsg-6ubuntu3                Mono System libraries (1.0)
ii  libmono-system2.0-cil                      1.2.6+dfsg-6ubuntu3                Mono System libraries (2.0)
ii  libmono0                                   1.2.6+dfsg-6ubuntu3                libraries for the Mono JIT
ii  libmono1.0-cil                             1.2.6+dfsg-6ubuntu3                Mono libraries (1.0)
ii  libmono2.0-cil                             1.2.6+dfsg-6ubuntu3                Mono libraries (2.0)
ii  libmtp7                                    0.2.6.1-2ubuntu1                   Media Transfer Protocol (MTP) library
ii  libmusicbrainz4c2a                         2.1.5-1ubuntu2                     Second generation incarnation of the CD Inde
ii  libmysqlclient15off                        5.0.51a-3ubuntu5.1                 MySQL database client library
ii  libnautilus-burn4                          2.22.1-0ubuntu1                    Nautilus Burn Library - runtime version
ii  libnautilus-extension1                     1:2.22.3-0ubuntu2                  libraries for nautilus components - runtime 
ii  libncurses5                                5.6+20071124-1ubuntu2              Shared libraries for terminal handling
ii  libncursesw5                               5.6+20071124-1ubuntu2              Shared libraries for terminal handling (wide
ii  libndesk-dbus-glib1.0-cil                  0.4.1-1                            CLI implementation of D-Bus (GLib mainloop i
ii  libndesk-dbus1.0-cil                       0.6.0-1                            CLI implementation of D-Bus
ii  libneon27                                  0.27.2-1                           An HTTP and WebDAV client library
ii  libnet-dbus-perl                           0.33.5-1                           Perl extension for the DBus message system
ii  libnewt0.52                                0.52.2-11.2ubuntu1                 Not Erik's Windowing Toolkit - text mode win
ii  libnl1                                     1.1-1                              Library for dealing with netlink sockets
ii  libnm-glib0                                0.6.6-0ubuntu5                     network management framework (GLib shared li
ii  libnm-util0                                0.6.6-0ubuntu5                     network management framework (shared library
ii  libnotify1                                 0.4.4-3build1                      sends desktop notifications to a notificatio
ii  libnspr4-0d                                4.7.1+1.9-0ubuntu0.8.04.1          NetScape Portable Runtime Library
ii  libnss-mdns                                0.10-3ubuntu2                      NSS module for Multicast DNS name resolution
ii  libnss3-1d                                 3.12.0.2+1.9-0ubuntu0.8.04.1       Network Security Service libraries
ii  libntfs-3g23                               1:1.2216-1ubuntu2                  ntfs-3g filesystem in userspace (FUSE) libra
ii  libogg0                                    1.1.3-3ubuntu1                     Ogg Bitstream Library
ii  liboil0.3                                  0.3.14-3                           Library of Optimized Inner Loops
ii  liboobs-1-4                                2.22.0-0ubuntu1                    GObject based interface to system-tools-back
ii  libopal-2.2                                2.2.11~dfsg1-3ubuntu2              Open Phone Abstraction Library - successor o
ii  libopenal0a                                1:0.0.8-7                          OpenAL is a portable library for 3D spatiali
ii  libopencdk10                               0.6.6-1ubuntu1                     Open Crypto Development Kit (OpenCDK) (runti
ii  libopenexr2ldbl                            1.2.2-4.4ubuntu1                   runtime files for the OpenEXR image library
ii  libopenobex1                               1.3-3ubuntu1                       OBEX protocol library
ii  liborbit2                                  1:2.14.12-0.1                      libraries for ORBit2 - a CORBA ORB
ii  libotr2                                    3.1.0-2                            Off-the-Record Messaging library
ii  libpam-gnome-keyring                       2.22.2-0ubuntu1                    PAM module to unlock the GNOME keyring upon 
ii  libpam-modules                             0.99.7.1-5ubuntu6.1                Pluggable Authentication Modules for PAM
ii  libpam-runtime                             0.99.7.1-5ubuntu6.1                Runtime support for the PAM library
ii  libpam0g                                   0.99.7.1-5ubuntu6.1                Pluggable Authentication Modules library
ii  libpanel-applet2-0                         1:2.22.2-0ubuntu1                  library for GNOME Panel applets
ii  libpango1.0-0                              1.20.1-1                           Layout and rendering of internationalized te
ii  libpango1.0-common                         1.20.1-1                           Modules and configuration files for the Pang
ii  libpaper-utils                             1.1.23                             library for handling paper characteristics (
ii  libpaper1                                  1.1.23                             library for handling paper characteristics
ii  libparted1.7-1                             1.7.1-5.1ubuntu9.1                 The GNU Parted disk partitioning shared libr
ii  libpcap0.8                                 0.9.8-2                            System interface for user-level packet captu
ii  libpcre3                                   7.4-1ubuntu2                       Perl 5 Compatible Regular Expression Library
ii  libperl5.8                                 5.8.8-12                           Shared Perl library
ii  libpisock9                                 0.12.3-4ubuntu1                    library for communicating with a PalmOS PDA
ii  libpisync1                                 0.12.3-4ubuntu1                    synchronization library for PalmOS devices
ii  libpixman-1-0                              0.10.0-0ubuntu1                    pixel-manipulation library for X and cairo
ii  libpng12-0                                 1.2.15~beta5-3                     PNG library - runtime
ii  libpolkit-dbus2                            0.7-2ubuntu7                       library for accessing PolicyKit via D-Bus
ii  libpolkit-gnome0                           0.7-2ubuntu1.1                     PolicyKit-gnome library
ii  libpolkit-grant2                           0.7-2ubuntu7                       library for obtaining privileges via PolicyK
ii  libpolkit2                                 0.7-2ubuntu7                       library for accessing PolicyKit
ii  libpoppler-glib2                           0.6.4-1ubuntu2                     PDF rendering library (GLib-based shared lib
ii  libpoppler2                                0.6.4-1ubuntu2                     PDF rendering library
ii  libpopt0                                   1.10-3build1                       lib for parsing cmdline parameters
ii  libportaudio0                              18.1-6                             Portable audio I/O - shared library
ii  libpt-1.10.10                              1.10.10-1ubuntu6                   Portable Windows Library
ii  libpt-1.10.10-plugins-alsa                 1.10.10-1ubuntu6                   Portable Windows Library Audio Plugin for th
ii  libpt-1.10.10-plugins-v4l                  1.10.10-1ubuntu6                   Portable Windows Library Video Plugin for Vi
ii  libpt-1.10.10-plugins-v4l2                 1.10.10-1ubuntu6                   Portable Windows Library Video Plugin for Vi
ii  libpth20                                   2.0.7-8                            The GNU Portable Threads
ii  libpulse-browse0                           0.9.10-1ubuntu1                    PulseAudio client libraries (zeroconf suppor
ii  libpulse0                                  0.9.10-1ubuntu1                    PulseAudio client libraries
ii  libpulsecore5                              0.9.10-1ubuntu1                    PulseAudio sound server core
ii  libpurple0                                 1:2.4.1-1ubuntu2                   multi-protocol instant messaging library
ii  libqthreads-12                             1.6.8-6ubuntu1                     QuickThreads library for Guile
ii  librarian0                                 0.8.0-0ubuntu1                     Rarian is a documentation meta-data library 
ii  libraw1394-8                               1.3.0-2                            library for direct access to IEEE 1394 bus (
ii  libreadline5                               5.2-3build1                        GNU readline and history libraries, run-time
ii  librecode0                                 3.6-14ubuntu1                      Shared library on which recode is based
ii  librpc-xml-perl                            0.59-2                             Perl module implementation of XML-RPC
ii  librsvg2-2                                 2.22.2-2                           SAX-based renderer library for SVG files (ru
ii  librsvg2-common                            2.22.2-2                           SAX-based renderer library for SVG files (ex
ii  libsamplerate0                             0.1.2-5ubuntu1                     audio rate conversion library
ii  libsane                                    1.0.19-1ubuntu3                    API library for scanners
ii  libsasl2-2                                 2.1.22.dfsg1-18ubuntu2             Cyrus SASL - authentication abstraction libr
ii  libsasl2-modules                           2.1.22.dfsg1-18ubuntu2             Cyrus SASL - pluggable authentication module
ii  libscim8c2a                                1.4.7-3ubuntu8                     library for SCIM platform
ii  libscrollkeeper0                           0.3.14-15ubuntu1                   Library to load .omf files (runtime files)
ii  libsdl1.2debian                            1.2.13-1ubuntu1                    Simple DirectMedia Layer
ii  libsdl1.2debian-alsa                       1.2.13-1ubuntu1                    Simple DirectMedia Layer (with X11 and ALSA 
ii  libselinux1                                2.0.55-0ubuntu4                    SELinux policy enforcement, run-time librari
ii  libsensors3                                1:2.10.5-3ubuntu1                  library to read temperature/voltage/fan sens
ii  libsepol1                                  2.0.20-0ubuntu3                    SELinux binary policy, run-time library
ii  libsexy2                                   0.1.11-2                           collection of additional GTK+ widgets - libr
ii  libsgutils1                                1.24-1                             Utilities for working with generic SCSI devi
ii  libshout3                                  2.2.2-2                            MP3/Ogg Vorbis broadcast streaming library
ii  libsigc++-2.0-0c2a                         2.0.17-2ubuntu3                    type-safe Signal Framework for C++ - runtime
ii  libslang2                                  2.1.3-2                            The S-Lang programming library - runtime ver
ii  libslp1                                    1.2.1-7.1                          OpenSLP libraries
ii  libsm6                                     2:1.0.3-1                          X11 Session Management library
ii  libsmbclient                               3.0.28a-1ubuntu4.3                 shared library that allows applications to t
ii  libsmbios1                                 0.13.10-1ubuntu1                   Provide access to (SM)BIOS information -- dy
ii  libsndfile1                                1.0.17-4                           Library for reading/writing audio files
ii  libsnmp-base                               5.4.1~dfsg-4ubuntu4                SNMP (Simple Network Management Protocol) MI
ii  libsnmp15                                  5.4.1~dfsg-4ubuntu4                SNMP (Simple Network Management Protocol) li
ii  libsoup2.4-1                               2.4.1-1                            an HTTP library implementation in C -- Share
ii  libspeex1                                  1.1.12-3ubuntu0.8.04.1             The Speex Speech Codec
ii  libsqlite0                                 2.8.17-4build1                     SQLite shared library
ii  libsqlite3-0                               3.4.2-2                            SQLite 3 shared library
ii  libss2                                     1.40.8-2ubuntu2                    command-line interface parsing library
ii  libssl0.9.8                                0.9.8g-4ubuntu3.3                  SSL shared libraries
ii  libstartup-notification0                   0.9-1                              library for program launch feedback (shared 
ii  libstdc++6                                 4.2.3-2ubuntu7                     The GNU Standard C++ Library v3
ii  libsysfs2                                  2.1.0-4                            interface library to sysfs
ii  libtag1c2a                                 1.4-8ubuntu1                       TagLib Audio Meta-Data Library
ii  libtasn1-3                                 1.1-1                              Manage ASN.1 structures (runtime)
ii  libterm-readkey-perl                       2.30-3ubuntu1                      A perl module for simple terminal control
ii  libtext-charwidth-perl                     0.04-4build1                       get display widths of characters on the term
ii  libtext-iconv-perl                         1.4-3                              converts between character sets in Perl
ii  libtext-wrapi18n-perl                      0.06-5                             internationalized substitute of Text::Wrap
ii  libthai-data                               0.1.9-1                            Data files for Thai language support library
ii  libthai0                                   0.1.9-1                            Thai language support library
ii  libtheora0                                 1.0~beta2-2                        The Theora Video Compression Codec
ii  libtiff4                                   3.8.2-7ubuntu3                     Tag Image File Format (TIFF) library
ii  libtotem-plparser10                        2.22.3-0ubuntu2                    Totem Playlist Parser library - runtime vers
ii  libtracker-gtk0                            0.6.6-0ubuntu3.8.04.1              GTK+ widgets for apps that use tracker
ii  libtrackerclient0                          0.6.6-0ubuntu3.8.04.1              metadata database, indexer and search tool -
ii  libuniconf4.4                              4.4.1-0ubuntu2                     C++ network libraries for rapid application 
ii  liburi-perl                                1.35.dfsg.1-1                      Manipulates and accesses URI strings
ii  libusb-0.1-4                               2:0.1.12-8                         userspace USB programming library
ii  libusplash0                                0.5.19                             userspace bootsplash library
ii  libuuid1                                   1.40.8-2ubuntu2                    universally unique id library
ii  libvisual-0.4-0                            0.4.0-2                            Audio visualization framework
ii  libvolume-id0                              117-8                              volume identification library
ii  libvorbis0a                                1.2.0.dfsg-2                       The Vorbis General Audio Compression Codec
ii  libvorbisenc2                              1.2.0.dfsg-2                       The Vorbis General Audio Compression Codec
ii  libvorbisfile3                             1.2.0.dfsg-2                       The Vorbis General Audio Compression Codec
ii  libvte-common                              1:0.16.13-1ubuntu1                 Terminal emulator widget for GTK+ 2.0 - comm
ii  libvte9                                    1:0.16.13-1ubuntu1                 Terminal emulator widget for GTK+ 2.0 - runt
ii  libwavpack1                                4.41.0-1                           an audio codec (lossy and lossless) - librar
ii  libwmf0.2-7                                0.2.8.4-6                          Windows metafile conversion library
ii  libwnck-common                             2.22.1-0ubuntu1                    Window Navigator Construction Kit - common f
ii  libwnck22                                  2.22.1-0ubuntu1                    Window Navigator Construction Kit - runtime 
ii  libwpd8c2a                                 0.8.12-1ubuntu1                    Library for handling WordPerfect documents (
ii  libwpg-0.1-1                               0.1.1-1                            WordPerfect graphics import/convert library 
ii  libwps-0.1-1                               0.1.1-1                            Works text file format import filter library
ii  libwrap0                                   7.6.dbs-14                         Wietse Venema's TCP wrappers library
ii  libwvstreams4.4-base                       4.4.1-0ubuntu2                     C++ network libraries for rapid application 
ii  libwvstreams4.4-extras                     4.4.1-0ubuntu2                     C++ network libraries for rapid application 
ii  libwww-perl                                5.808-1                            WWW client/server library for Perl (aka LWP)
ii  libx11-6                                   2:1.1.3-1ubuntu2                   X11 client-side library
ii  libx11-data                                2:1.1.3-1ubuntu2                   X11 client-side library
ii  libx11-xcb1                                2:1.1.3-1ubuntu2                   Xlib/XCB interface library
ii  libx86-1                                   0.99-1.2ubuntu4                    x86 real-mode library
ii  libxau6                                    1:1.0.3-2                          X11 authorisation library
ii  libxaw7                                    2:1.0.4-1                          X11 Athena Widget library
ii  libxcb-xlib0                               1.1-1ubuntu1                       X C Binding, Xlib/XCB interface library
ii  libxcb1                                    1.1-1ubuntu1                       X C Binding
ii  libxcomposite1                             1:0.4.0-1                          X11 Composite extension library
ii  libxcursor1                                1:1.1.9-1                          X cursor management library
ii  libxdamage1                                1:1.1.1-3                          X11 damaged region extension library
ii  libxdmcp6                                  1:1.0.2-2                          X11 Display Manager Control Protocol library
ii  libxevie1                                  1:1.0.2-2                          X11 EvIE extension library
ii  libxext6                                   2:1.0.3-2build1                    X11 miscellaneous extension library
ii  libxfixes3                                 1:4.0.3-2                          X11 miscellaneous 'fixes' extension library
ii  libxfont1                                  1:1.3.1-2                          X11 font rasterisation library
ii  libxft2                                    2.1.12-2ubuntu5                    FreeType-based font drawing library for X
ii  libxi6                                     2:1.1.3-1                          X11 Input extension library
ii  libxinerama1                               2:1.0.2-1build1                    X11 Xinerama extension library
ii  libxkbfile1                                1:1.0.4-1                          X11 keyboard file manipulation library
ii  libxklavier12                              3.5-1                              X Keyboard Extension high-level API
ii  libxml-parser-perl                         2.34-4.3                           Perl module for parsing XML files
ii  libxml-twig-perl                           1:3.32-1                           Perl module for processing huge XML document
ii  libxml2                                    2.6.31.dfsg-2ubuntu1               GNOME XML library
ii  libxml2-utils                              2.6.31.dfsg-2ubuntu1               XML utilities
ii  libxmu6                                    2:1.0.4-1                          X11 miscellaneous utility library
ii  libxmuu1                                   2:1.0.4-1                          X11 miscellaneous micro-utility library
ii  libxp6                                     1:1.0.0.xsf1-1build1               X Printing Extension (Xprint) client library
ii  libxplc0.3.13                              0.3.13-1build1                     Light weight component system
ii  libxpm4                                    1:3.5.7-1                          X11 pixmap library
ii  libxrandr2                                 2:1.2.2-1                          X11 RandR extension library
ii  libxrender1                                1:0.9.4-1                          X Rendering Extension client library
ii  libxres1                                   2:1.0.3-1                          X11 Resource extension library
ii  libxslt1.1                                 1.1.22-1ubuntu1                    XSLT processing library - runtime library
ii  libxss1                                    1:1.1.2-1                          X11 Screen Saver extension library
ii  libxt6                                     1:1.0.5-3                          X11 toolkit intrinsics library
ii  libxtrap6                                  2:1.0.0-4build1                    X11 event trapping extension library
ii  libxtst6                                   2:1.0.3-1                          X11 Testing -- Resource extension library
ii  libxv1                                     2:1.0.3-1ubuntu1                   X11 Video extension library
ii  libxxf86dga1                               2:1.0.2-1                          X11 Direct Graphics Access extension library
ii  libxxf86misc1                              1:1.0.1-2                          X11 XFree86 miscellaneous extension library
ii  libxxf86vm1                                1:1.0.1-2                          X11 XFree86 video mode extension library
ii  libzephyr3                                 2.1.20070719.SNAPSHOT-1            The original "Instant Message" system librar
ii  linux-generic                              2.6.24.16.18                       Complete Generic Linux kernel
ii  linux-headers-2.6.24-16                    2.6.24-16.30                       Header files related to Linux kernel version
ii  linux-headers-2.6.24-16-generic            2.6.24-16.30                       Linux kernel headers for version 2.6.24 on x
ii  linux-headers-generic                      2.6.24.16.18                       Generic Linux kernel headers
ii  linux-image-2.6.24-16-generic              2.6.24-16.30                       Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.16.18                       Generic Linux kernel image
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.13-19.42                    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.16.18                       Restricted Linux modules for generic kernels
ii  linux-sound-base                           1.0.16-0ubuntu4                    base package for ALSA and OSS sound systems
ii  linux-ubuntu-modules-2.6.24-16-generic     2.6.24-16.23                       Ubuntu supplied Linux modules for version 2.
ii  locales                                    2.7.9-4                            common files for locale support
ii  login                                      1:4.0.18.2-1ubuntu2                system login tools
ii  logrotate                                  3.7.1-3                            Log rotation utility
ii  lsb-base                                   3.2-4ubuntu1                       Linux Standard Base 3.2 init script function
ii  lsb-release                                3.2-4ubuntu1                       Linux Standard Base version reporting utilit
ii  lshw                                       02.12.01-2ubuntu1.1                information about hardware configuration
ii  lsof                                       4.78.dfsg.1-3                      List open files
ii  ltrace                                     0.5-3ubuntu1                       Tracks runtime library calls in dynamically 
ii  lzma                                       4.43-12ubuntu1                     Compression method of 7z format in 7-Zip pro
ii  make                                       3.81-3build1                       The GNU version of the "make" utility.
ii  makedev                                    2.3.1-84ubuntu1                    creates device files in /dev
ii  man-db                                     2.5.1-3                            on-line manual pager
ii  manpages                                   2.77-1                             Manual pages about using a GNU/Linux system
ii  mawk                                       1.3.3-11ubuntu2                    a pattern scanning and text processing langu
ii  mdetect                                    0.5.2.1ubuntu4                     mouse device autodetection tool
ii  memtest86+                                 1.70-3ubuntu1                      thorough real-mode memory tester
ii  mesa-utils                                 7.0.3~rc2-1ubuntu3                 Miscellaneous Mesa GL utilities
ii  metacity                                   1:2.22.0-0ubuntu4                  A lightweight GTK2 based Window Manager
ii  metacity-common                            1:2.22.0-0ubuntu4                  Shared files of lightweight GTK2 based Windo
ii  mii-diag                                   2.11-2                             A little tool to manipulate network cards
ii  mime-support                               3.39-1ubuntu1                      MIME files 'mime.types' & 'mailcap', and sup
ii  min12xxw                                   0.0.9-1build1                      Printer driver for KonicaMinolta PagePro 1[2
ii  mktemp                                     1.5-5ubuntu2                       Makes unique filenames for temporary files
ii  mlocate                                    0.18-2ubuntu1                      quickly find files on the filesystem based o
ii  module-init-tools                          3.3-pre11-4ubuntu5                 tools for managing Linux kernel modules
ii  mono-common                                1.2.6+dfsg-6ubuntu3                common files for Mono
ii  mono-gac                                   1.2.6+dfsg-6ubuntu3                Mono GAC tool
ii  mono-jit                                   1.2.6+dfsg-6ubuntu3                fast CLI JIT/AOT compiler for Mono
ii  mono-runtime                               1.2.6+dfsg-6ubuntu3                Mono runtime
ii  mount                                      2.13.1-5ubuntu2                    Tools for mounting and manipulating filesyst
ii  mousetweaks                                2.22.1-0ubuntu2                    mouse accessibility enhancements for the GNO
ii  mscompress                                 0.3-2ubuntu1                       Microsoft "compress.exe/expand.exe" compatib
ii  mtr-tiny                                   0.72-2ubuntu1                      Full screen ncurses traceroute tool
ii  myspell-en-gb                              1:2.4.0~m240-1ubuntu1              English_british dictionary for myspell
ii  myspell-en-us                              1:2.4.0~m240-1ubuntu1              English_american dictionary for myspell
ii  myspell-en-za                              1:2.4.0~m240-1ubuntu1              English_shouthafrican dictionary for myspell
ii  mysql-common                               5.0.51a-3ubuntu5.1                 MySQL database common files
ii  nano                                       2.0.7-1ubuntu1                     free Pico clone with some new features
ii  nautilus                                   1:2.22.3-0ubuntu2                  file manager and graphical shell for GNOME
ii  nautilus-cd-burner                         2.22.1-0ubuntu1                    CD Burning front-end for Nautilus
ii  nautilus-data                              1:2.22.3-0ubuntu2                  data files for nautilus
ii  nautilus-sendto                            0.13.2-0ubuntu1                    integrates Evolution and Pidgin into the Nau
ii  nautilus-share                             0.7.2-0ubuntu5                     Nautilus extension to share folder using Sam
ii  ncurses-base                               5.6+20071124-1ubuntu2              Descriptions of common terminal types
ii  ncurses-bin                                5.6+20071124-1ubuntu2              Terminal-related programs and man pages
ii  net-tools                                  1.60-19ubuntu1                     The NET-3 networking toolkit
ii  netbase                                    4.30ubuntu1                        Basic TCP/IP networking system
ii  netcat                                     1.10-36                            TCP/IP swiss army knife -- transitional pack
ii  netcat-traditional                         1.10-36                            TCP/IP swiss army knife
ii  network-manager                            0.6.6-0ubuntu5                     network management framework daemon
ii  network-manager-gnome                      0.6.6-0ubuntu3                     network management framework (GNOME frontend
ii  notification-daemon                        0.3.7-1ubuntu11.2                  a daemon that displays passive pop-up notifi
ii  ntfs-3g                                    1:1.2216-1ubuntu2                  read-write NTFS driver for FUSE
ii  ntpdate                                    1:4.2.4p4+dfsg-3ubuntu2            client for setting system time from NTP serv
ii  nvidia-kernel-common                       20051028+1ubuntu8                  NVIDIA binary kernel module common files
ii  o3read                                     0.0.4-1                            standalone converter for OpenOffice.org docu
ii  obex-data-server                           0.3.1-0ubuntu1                     D-Bus service for OBEX client and server sid
ii  onboard                                    0.91ubuntu2                        Simple On-screen Keyboard
ii  openoffice.org-base-core                   1:2.4.1-1ubuntu1                   OpenOffice.org office suite -- libdba
ii  openoffice.org-calc                        1:2.4.1-1ubuntu1                   OpenOffice.org office suite - spreadsheet
ii  openoffice.org-common                      1:2.4.1-1ubuntu1                   OpenOffice.org office suite architecture ind
ii  openoffice.org-core                        1:2.4.1-1ubuntu1                   OpenOffice.org office suite architecture dep
ii  openoffice.org-draw                        1:2.4.1-1ubuntu1                   OpenOffice.org office suite - drawing
ii  openoffice.org-gnome                       1:2.4.1-1ubuntu1                   GNOME Integration for OpenOffice.org (VFS, G
ii  openoffice.org-gtk                         1:2.4.1-1ubuntu1                   GTK+ Integration for OpenOffice.org (Widgets
ii  openoffice.org-help-en-gb                  1:2.4.1-1ubuntu1                   English_british help for OpenOffice.org
ii  openoffice.org-help-en-us                  1:2.4.1-1ubuntu1                   English_american help for OpenOffice.org
ii  openoffice.org-hyphenation                 0.3                                Hyphenation patterns for OpenOffice.org
ii  openoffice.org-impress                     1:2.4.1-1ubuntu1                   OpenOffice.org office suite - presentation
ii  openoffice.org-l10n-common                 1:2.4.1-1ubuntu1                   common files for OpenOffice.org language and
ii  openoffice.org-l10n-en-gb                  1:2.4.1-1ubuntu1                   English_british language package for OpenOff
ii  openoffice.org-l10n-en-za                  1:2.4.1-1ubuntu1                   English_southafrican language package for Op
ii  openoffice.org-style-human                 1:2.4.1-1ubuntu1                   Human symbol style for OpenOffice.org
ii  openoffice.org-thesaurus-en-au             2.1-3ubuntu1                       Australian English Thesaurus for OpenOffice.
ii  openoffice.org-thesaurus-en-us             1:2.4.0~m240-1ubuntu1              English Thesaurus for OpenOffice.org
ii  openoffice.org-writer                      1:2.4.1-1ubuntu1                   OpenOffice.org office suite - word processor
ii  openprinting-ppds                          20080211-0ubuntu1                  OpenPrinting printer support - PostScript PP
ii  openssh-blacklist                          0.1-1ubuntu0.8.04.1                list of blacklisted OpenSSH RSA and DSA keys
ii  openssh-client                             1:4.7p1-8ubuntu1.2                 secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server                             1:4.7p1-8ubuntu1.2                 secure shell server, an rshd replacement
ii  openssl                                    0.9.8g-4ubuntu3.3                  Secure Socket Layer (SSL) binary and related
ii  parted                                     1.7.1-5.1ubuntu9.1                 The GNU Parted disk partition resizing progr
ii  passwd                                     1:4.0.18.2-1ubuntu2                change and administer password and group dat
ii  pciutils                                   1:2.2.4-1.1ubuntu4                 Linux PCI Utilities
ii  pcmciautils                                014-4ubuntu1                       PCMCIA utilities for Linux 2.6
ii  perl                                       5.8.8-12                           Larry Wall's Practical Extraction and Report
ii  perl-base                                  5.8.8-12                           The Pathologically Eclectic Rubbish Lister
ii  perl-modules                               5.8.8-12                           Core Perl modules
ii  pidgin                                     1:2.4.1-1ubuntu2                   graphical multi-protocol instant messaging c
ii  pidgin-data                                1:2.4.1-1ubuntu2                   multi-protocol instant messaging client - da
ii  pidgin-otr                                 3.1.0-1                            Off-the-Record Messaging plugin for pidgin
ii  pkg-config                                 0.22-1                             manage compile and link flags for libraries
ii  pm-utils                                   0.99.2-3ubuntu10                   utilities and scripts for power management
ii  pnm2ppa                                    1.12-16                            PPM to PPA converter
ii  policykit                                  0.7-2ubuntu7                       framework for managing administrative polici
ii  policykit-gnome                            0.7-2ubuntu1.1                     GNOME dialogs for PolicyKit
ii  poppler-utils                              0.6.4-1ubuntu2                     PDF utilitites (based on libpoppler)
ii  popularity-contest                         1.43ubuntu1                        Vote for your favourite packages automatical
ii  powermanagement-interface                  0.3.18                             platform neutral powermanagement interface
ii  powermgmt-base                             1.29build1                         Common utils and configs for power managemen
ii  powernowd                                  0.97-2ubuntu4                      control cpu speed and voltage using 2.6 kern
ii  ppp                                        2.4.4rel-9ubuntu2                  Point-to-Point Protocol (PPP) daemon
ii  pppconfig                                  2.3.17ubuntu1                      A text menu based utility for configuring pp
ii  pppoeconf                                  1.17ubuntu1                        configures PPPoE/ADSL connections
ii  procps                                     1:3.2.7-5ubuntu2                   /proc file system utilities
ii  psmisc                                     22.6-1                             Utilities that use the proc filesystem
ii  pulseaudio                                 0.9.10-1ubuntu1                    PulseAudio sound server
ii  pulseaudio-esound-compat                   0.9.10-1ubuntu1                    PulseAudio ESD compatibility layer
ii  pulseaudio-module-gconf                    0.9.10-1ubuntu1                    GConf module for PulseAudio sound server
ii  pulseaudio-module-hal                      0.9.10-1ubuntu1                    HAL device detection module for PulseAudio s
ii  pulseaudio-module-x11                      0.9.10-1ubuntu1                    X11 module for PulseAudio sound server
ii  pulseaudio-utils                           0.9.10-1ubuntu1                    Command line tools for the PulseAudio sound 
ii  pxljr                                      1.1-0ubuntu1                       Driver for HP's Color LaserJet 35xx/36xx col
ii  python                                     2.5.2-0ubuntu1                     An interactive high-level object-oriented la
ii  python-apport                              0.108.2                            apport crash report handling library
ii  python-apt                                 0.7.4ubuntu7                       Python interface to libapt-pkg
ii  python-brlapi                              3.9-6ubuntu1                       Python bindings for BrlAPI
ii  python-cairo                               1.4.0-2ubuntu2                     Python bindings for the Cairo vector graphic
ii  python-central                             0.6.7ubuntu0.1                     register and build utility for Python packag
ii  python-cups                                1.9.34-0ubuntu1                    Python bindings for CUPS
ii  python-dbus                                0.82.4-1ubuntu1                    simple interprocess messaging system (Python
ii  python-gconf                               2.22.0-0ubuntu1                    Python bindings for GConf2
ii  python-gdata                               1.0.9-1ubuntu1                     Google Data Python client library
ii  python-gdbm                                2.5.2-0ubuntu2                     GNU dbm database support for Python
ii  python-glade2                              2.12.1-0ubuntu1                    GTK+ bindings: Glade support
ii  python-gmenu                               2.22.2-0ubuntu1                    an implementation of the freedesktop menu sp
ii  python-gnome2                              2.22.0-0ubuntu1                    Python bindings for the GNOME desktop enviro
ii  python-gnome2-desktop                      2.22.0-0ubuntu1                    Python bindings for the GNOME desktop enviro
ii  python-gnomecanvas                         2.22.0-0ubuntu1                    Python bindings for gnomecanvas (debug exten
ii  python-gnupginterface                      0.3.2-9ubuntu1                     Python interface to GnuPG (GPG)
ii  python-gobject                             2.14.1-2ubuntu2                    Python bindings for the GObject library
ii  python-gst0.10                             0.10.11-1                          generic media-playing framework (Python bind
ii  python-gtk2                                2.12.1-0ubuntu1                    Python bindings for the GTK+ widget set
ii  python-gtkhtml2                            2.19.1-0ubuntu7                    Python bindings for the GtkHTML2 library
ii  python-gtksourceview2                      2.2.0-0ubuntu2                     Python bindings for the GtkSourceView widget
ii  python-imaging                             1.1.6-1ubuntu5                     Python Imaging Library
ii  python-launchpad-bugs                      0.2.30.1                           simple Python Interface to Bugs in Launchpad
ii  python-launchpad-integration               0.1.19                             library for launchpad integration
ii  python-libxml2                             2.6.31.dfsg-2ubuntu1               Python bindings for the GNOME XML library
ii  python-minimal                             2.5.2-0ubuntu1                     A minimal subset of the Python language (def
ii  python-notify                              0.1.1-2                            Python bindings for libnotify
ii  python-numeric                             24.2-8ubuntu2                      Numerical (matrix-oriented) Mathematics for 
ii  python-problem-report                      0.108.2                            Python library to handle problem reports
ii  python-pyatspi                             1.22.1-0ubuntu1                    Assistive Technology Service Provider Interf
ii  python-pyorbit                             2.14.3-2ubuntu1                    A Python language binding for the ORBit2 COR
ii  python-sexy                                0.1.9-1ubuntu1                     python language bindings for libsexy
ii  python-software-properties                 0.63ubuntu1                        manage the repositories that you install sof
ii  python-support                             0.7.5ubuntu1                       automated rebuilding support for python modu
ii  python-uno                                 1:2.4.1-1ubuntu1                   Python interface for OpenOffice.org
ii  python-virtkey                             0.50ubuntu0.1                      Library to emulate keyboard keypresses.
ii  python-vte                                 1:0.16.13-1ubuntu1                 Python bindings for the VTE widget set
ii  python-xdg                                 0.15-1.1ubuntu3                    A python library to access freedesktop.org s
ii  python2.5                                  2.5.2-2ubuntu4                     An interactive high-level object-oriented la
ii  python2.5-minimal                          2.5.2-2ubuntu4                     A minimal subset of the Python language (ver
ii  radeontool                                 1.5-5build1                        utility to control ATI Radeon backlight func
ii  rdesktop                                   1.5.0-3+cvs20071006                RDP client for Windows NT/2000 Terminal Serv
ii  readahead                                  1:0.20050517.0220-0ubuntu14        read files into the page cache
ii  readline-common                            5.2-3build1                        GNU readline and history libraries, common f
ii  reiserfsprogs                              1:3.6.19-6                         User-level tools for ReiserFS filesystems
ii  rhythmbox                                  0.11.5-0ubuntu8                    music player and organizer for GNOME
ii  rss-glx                                    0.8.1-8ubuntu4                     Really Slick Screensavers GLX Port
ii  rsync                                      2.6.9-6ubuntu2                     fast remote file copy program (like rcp)
ii  samba-common                               3.0.28a-1ubuntu4.3                 Samba common files used by both the server a
ii  scim                                       1.4.7-3ubuntu8                     smart common input method platform
ii  scim-bridge-agent                          0.4.14-1ubuntu2                    IME server of scim-bridge communicate with S
ii  scim-bridge-client-gtk                     0.4.14-1ubuntu2                    IME server of scim-bridge communicate with S
ii  scim-gtk2-immodule                         1.4.7-3ubuntu8                     GTK+2 input method module with SCIM as backe
ii  scim-modules-socket                        1.4.7-3ubuntu8                     socket modules for SCIM platform
ii  screen                                     4.0.3-7ubuntu1                     terminal multiplexor with VT100/ANSI termina
ii  screensaver-default-images                 0.2-1                              Wallpapers for image processing screensavers
ii  scrollkeeper                               0.3.14-15ubuntu1                   A free electronic cataloging system for docu
ii  seahorse                                   2.22.2-0ubuntu1                    A Gnome front end for GnuPG
ii  sed                                        4.1.5-5                            The GNU sed stream editor
ii  sgml-base                                  1.26                               SGML infrastructure and SGML catalog file su
ii  sgml-data                                  2.0.3                              common SGML and XML data
ii  shared-mime-info                           0.23-5                             FreeDesktop.org shared MIME database and spe
ii  smartdimmer                                0.1-2build1                        Change LCD brightness on Geforce 6200Go card
ii  smbclient                                  3.0.28a-1ubuntu4.3                 a LanManager-like simple client for Unix
ii  software-properties-gtk                    0.63ubuntu1                        manage the repositories that you install sof
ii  sound-juicer                               2.22.0-1ubuntu2                    GNOME 2 CD Ripper
ii  splix                                      1.1.1-0ubuntu1                     Driver for Samsung's SPL2 (bw) and SPLc (col
ii  sqlite                                     2.8.17-4build1                     command line interface for SQLite
ii  sqlite3                                    3.4.2-2                            A command line interface for SQLite 3
ii  ssh-askpass-gnome                          1:4.7p1-8ubuntu1.2                 interactive X program to prompt users for a 
ii  ssl-cert                                   1.0.14-0ubuntu2                    Simple debconf wrapper for openssl
ii  startup-tasks                              0.3.9-2                            definitions of essential tasks to run on sta
ii  strace                                     4.5.15-1.1ubuntu1                  A system call tracer
ii  sudo                                       1.6.9p10-1ubuntu3.2                Provide limited super user privileges to spe
ii  synaptic                                   0.61ubuntu9                        Graphical package manager
ii  sysklogd                                   1.5-1ubuntu1                       System Logging Daemon
ii  system-config-printer-common               0.7.81+svn1976-0ubuntu9            Printer configuration GUI
ii  system-config-printer-gnome                0.7.81+svn1976-0ubuntu9            Printer configuration GUI
ii  system-services                            0.3.9-2                            definitions of essential system services
ii  system-tools-backends                      2.6.0-0ubuntu7                     System Tools to manage computer configuratio
ii  sysv-rc                                    2.86.ds1-14.1ubuntu45              System-V-like runlevel change mechanism
ii  sysvutils                                  2.86.ds1-14.1ubuntu45              System-V-like utilities
ii  tangerine-icon-theme                       0.26                               Tangerine Icon theme
ii  tar                                        1.19-3                             GNU version of the tar archiving utility
ii  tasksel                                    2.70ubuntu5                        Tool for selecting tasks for installation on
ii  tasksel-data                               2.70ubuntu5                        Official tasks used for installation of Debi
ii  tcpd                                       7.6.dbs-14                         Wietse Venema's TCP wrapper utilities
ii  tcpdump                                    3.9.8-2                            A powerful tool for network monitoring and d
ii  telnet                                     0.17-35ubuntu1                     The telnet client
ii  thunderbird-locale-en-gb                   1:2.0.0.0+1-0ubuntu1               Thunderbird English language/region package
ii  time                                       1.7-21build1                       The GNU time program for measuring cpu resou
ii  tomboy                                     0.10.1-1                           desktop note taking program using Wiki style
ii  toshset                                    1.72-6ubuntu1                      Access much of the Toshiba laptop hardware i
ii  totem                                      2.22.1-0ubuntu2                    A simple media player for the Gnome desktop 
ii  totem-common                               2.22.1-0ubuntu2                    Data files for the Totem media player
ii  totem-gstreamer                            2.22.1-0ubuntu2                    A simple media player for the Gnome desktop 
ii  totem-mozilla                              2.22.1-0ubuntu2                    Totem Mozilla plugin
ii  totem-plugins                              2.22.1-0ubuntu2                    Plugins for the Totem media player
ii  tracker                                    0.6.6-0ubuntu3.8.04.1              metadata database, indexer and search tool
ii  tracker-search-tool                        0.6.6-0ubuntu3.8.04.1              metadata database, indexer and search tool -
ii  transmission-common                        1.06-0ubuntu6                      free, lightweight BitTorrent client
ii  transmission-gtk                           1.06-0ubuntu6                      free, lightweight BitTorrent client (graphic
ii  tsclient                                   0.150-1ubuntu1                     front-end for viewing of remote desktops in 
ii  ttf-arabeyes                               2.0-1ubuntu1                       Arabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-uming                           0.2.20080216.1-0ubuntu1            "AR PL UMing" Chinese Unicode TrueType font 
ii  ttf-bitstream-vera                         1.10-7                             The Bitstream Vera family of free TrueType f
ii  ttf-dejavu-core                            2.23-1                             Vera font family derivate with additional ch
ii  ttf-freefont                               20060501cvs-12                     Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-fonts-core                       1:0.5.0-0ubuntu1                   Core collection of free Indian language font
ii  ttf-kochi-gothic                           1.0.20030809-4ubuntu2              Kochi Subst Gothic Japanese TrueType font wi
ii  ttf-kochi-mincho                           1.0.20030809-4ubuntu2              Kochi Subst Mincho Japanese TrueType font wi
ii  ttf-lao                                    0.0.20060226-2                     TrueType font for Lao language
ii  ttf-malayalam-fonts                        1:0.5.0-0ubuntu1                   Free TrueType fonts for the Malayalam langua
ii  ttf-opensymbol                             1:2.4.1-1ubuntu1                   The OpenSymbol TrueType font
ii  ttf-thai-tlwg                              1:0.4.8-1                          Thai fonts in TrueType format
ii  ttf-unfonts-core                           1.0.1-6ubuntu1                     Un series Korean TrueType fonts
ii  tzdata                                     2008c-1ubuntu0.8.04                time zone and daylight-saving time data
ii  ubufox                                     0.5-0ubuntu1                       Ubuntu Firefox specific configuration defaul
ii  ubuntu-artwork                             41                                 Ubuntu themes and artwork
ii  ubuntu-desktop                             1.102                              The Ubuntu desktop system
ii  ubuntu-docs                                8.04.2~hardy                       The Ubuntu Documentation Project
ii  ubuntu-gdm-themes                          0.29                               Ubuntu GDM themes
ii  ubuntu-keyring                             2008.03.04                         GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                             1.102                              Minimal core of Ubuntu
ii  ubuntu-sounds                              0.6                                Ubuntu's GNOME audio theme
ii  ubuntu-standard                            1.102                              The Ubuntu standard system
ii  ubuntu-wallpapers                          0.25                               Ubuntu Wallpapers
ii  ucf                                        3.005                              Update Configuration File: preserve user cha
ii  udev                                       117-8                              rule-based device node and kernel event mana
ii  ufw                                        0.16.2.1                           program for managing a netfilter firewall
ii  unattended-upgrades                        0.30ubuntu1                        Install security upgrades automatically
ii  unzip                                      5.52-10ubuntu2                     De-archiver for .zip files
ii  update-inetd                               4.27-0.6                           inetd.conf updater
ii  update-manager                             1:0.87.27                          GNOME application that manages apt updates
ii  update-manager-core                        1:0.87.27                          manage release upgrades
ii  update-notifier                            0.70.7                             Daemon which notifies about package updates
ii  update-notifier-common                     0.70.7                             Files shared between update-notifier and ade
ii  upstart                                    0.3.9-2                            event-based init daemon
ii  upstart-compat-sysv                        0.3.9-2                            compatibility for System-V-like init
ii  upstart-logd                               0.3.9-2                            boot logging daemon
ii  usbutils                                   0.73-5ubuntu2                      Linux USB utilities
ii  usplash                                    0.5.19                             Userspace bootsplash utility
ii  usplash-theme-ubuntu                       0.18                               Usplash theme for Ubuntu
ii  util-linux                                 2.13.1-5ubuntu2                    Miscellaneous system utilities
ii  util-linux-locales                         2.13.1-5ubuntu2                    Locales files for util-linux
ii  uuid-runtime                               1.40.8-2ubuntu2                    universally unique id library
ii  vbetool                                    1.0-1.1                            run real-mode video BIOS code to alter hardw
ii  vim-common                                 1:7.1-138+1ubuntu3                 Vi IMproved - Common files
ii  vim-tiny                                   1:7.1-138+1ubuntu3                 Vi IMproved - enhanced vi editor - compact v
ii  vinagre                                    0.5.1-0ubuntu1                     VNC client for the GNOME Desktop
ii  vino                                       2.22.2-0ubuntu1                    VNC server for GNOME
ii  w3m                                        0.5.1-5.1ubuntu1                   WWW browsable pager with excellent tables/fr
ii  wamerican                                  6-2.1                              American English dictionary words for /usr/s
ii  wbritish                                   6-2.1                              British English dictionary words for /usr/sh
ii  wget                                       1.10.2-3ubuntu1                    retrieves files from the web
ii  whiptail                                   0.52.2-11.2ubuntu1                 Displays user-friendly dialog boxes from she
ii  whois                                      4.7.24                             the GNU whois client
ii  wireless-tools                             29-1ubuntu2                        Tools for manipulating Linux Wireless Extens
ii  wodim                                      9:1.1.6-1ubuntu6                   command line CD/DVD writing tool
ii  wpasupplicant                              0.6.0+0.5.8-0ubuntu2               Client support for WPA and WPA2 (IEEE 802.11
ii  wvdial                                     1.60.1                             PPP dialer with built-in intelligence
ii  x-ttcidfont-conf                           27                                 TrueType and CID fonts configuration for X
ii  x11-apps                                   7.3+1                              X applications
ii  x11-common                                 1:7.3+10ubuntu10                   X Window System (X.Org) infrastructure
ii  x11-session-utils                          7.3+1                              X session utilities
ii  x11-utils                                  7.3+1                              X11 utilities
ii  x11-xfs-utils                              7.3+1                              X font server utilities
ii  x11-xkb-utils                              7.3+1                              X11 XKB utilities
ii  x11-xserver-utils                          7.3+2                              X server utilities
ii  xauth                                      1:1.0.2-2                          X authentication utility
ii  xbase-clients                              1:7.3+10ubuntu10                   miscellaneous X clients - metapackage
ii  xbitmaps                                   1.0.1-2ubuntu1                     Base X bitmaps
ii  xcursor-themes                             1.0.1-5ubuntu1                     Base X cursor themes
ii  xdg-user-dirs                              0.10-1ubuntu1                      tool to manage well known user directories
ii  xdg-user-dirs-gtk                          0.7-1                              tool to manage well known user directories (
ii  xdg-utils                                  1.0.2-2                            desktop integration utilities from freedeskt
ii  xfonts-100dpi                              1:1.0.0-4                          100 dpi fonts for X
ii  xfonts-75dpi                               1:1.0.0-4                          75 dpi fonts for X
ii  xfonts-base                                1:1.0.0-5                          standard fonts for X
ii  xfonts-encodings                           1:1.0.2-3                          Encodings for X.Org fonts
ii  xfonts-scalable                            1:1.0.0-6                          scalable fonts for X
ii  xfonts-utils                               1:1.0.1-2ubuntu1                   X Window System font utility programs
ii  xinit                                      1.0.7-2                            X server initialisation tool
ii  xkb-data                                   1.1~cvs.20080104.1-1ubuntu6        X Keyboard Extension (XKB) configuration dat
ii  xml-core                                   0.11                               XML infrastructure and XML catalog file supp
ii  xorg                                       1:7.3+10ubuntu10                   X.Org X Window System
ii  xsane                                      0.995-1ubuntu1                     featureful graphical frontend for SANE (Scan
ii  xsane-common                               0.995-1ubuntu1                     featureful graphical frontend for SANE (Scan
ii  xscreensaver-data                          5.04-4ubuntu1                      data files to be shared among screensaver fr
ii  xscreensaver-gl                            5.04-4ubuntu1                      GL(Mesa) screen hacks for xscreensaver
ii  xserver-xorg                               1:7.3+10ubuntu10                   the X.Org X server
ii  xserver-xorg-core                          2:1.4.1~git20080131-1ubuntu9.2     Xorg X server - core server
ii  xserver-xorg-input-all                     1:7.3+10ubuntu10                   the X.Org X server -- input driver metapacka
ii  xserver-xorg-input-evdev                   1:1.2.0-1ubuntu2                   X.Org X server -- evdev input driver
ii  xserver-xorg-input-kbd                     1:1.2.2-3ubuntu1                   X.Org X server -- keyboard input driver
ii  xserver-xorg-input-mouse                   1:1.2.3-2                          X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics               0.14.7~git20070706-1ubuntu4        Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse                 1:12.4.3-1ubuntu1                  X.Org X server -- VMMouse input driver to us
ii  xserver-xorg-input-wacom                   1:0.7.9.8-0ubuntu3                 X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                     1:7.3+10ubuntu10                   the X.Org X server -- output driver metapack
ii  xserver-xorg-video-amd                     2.8.0-7                            AMD Geode GX/LX display driver (dummy transi
ii  xserver-xorg-video-apm                     1:1.1.1-10                         X.Org X server -- APM display driver
ii  xserver-xorg-video-ark                     1:0.6.0-9                          X.Org X server -- ark display driver
ii  xserver-xorg-video-ati                     1:6.8.0-1                          X.Org X server -- ATI display driver
ii  xserver-xorg-video-chips                   1:1.1.1-9                          X.Org X server -- Chips display driver
ii  xserver-xorg-video-cirrus                  1:1.1.0-8ubuntu1                   X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-cyrix                   1:1.1.0-8                          X.Org X server -- Cyrix display driver
ii  xserver-xorg-video-dummy                   1:0.2.0-7                          X.Org X server -- dummy display driver
ii  xserver-xorg-video-fbdev                   1:0.3.1-4                          X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode                   2.8.0-7                            X.org server -- AMD Geode GX/LX display driv
ii  xserver-xorg-video-glint                   1:1.1.1-8                          X.Org X server -- Glint display driver
ii  xserver-xorg-video-i128                    1:1.2.1-4                          X.Org X server -- i128 display driver
ii  xserver-xorg-video-i740                    1:1.1.0-7                          X.Org X server -- i740 display driver
ii  xserver-xorg-video-i810                    2:1.7.4-0ubuntu7                   X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-video-imstt                   1:1.1.0-7                          X.Org X server -- IMSTT display driver
ii  xserver-xorg-video-intel                   2:2.2.1-1ubuntu13.4                X.Org X server -- Intel i8xx, i9xx display d
ii  xserver-xorg-video-mga                     1:1.4.8.dfsg.1-1                   X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic                1:1.1.1-8                          X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-newport                 1:0.2.1-4ubuntu1                   X.Org X server -- Newport display driver
ii  xserver-xorg-video-nsc                     1:2.8.3-2                          X.Org X server -- NSC display driver
ii  xserver-xorg-video-nv                      1:2.1.8-1ubuntu1                   X.Org X server -- NV display driver
ii  xserver-xorg-video-openchrome              1:0.2.901-0ubuntu4                 X.Org X server -- VIA display driver
ii  xserver-xorg-video-psb                     0.2.1-1ubuntu3                     2D graphics driver for Poulsbo
ii  xserver-xorg-video-rendition               1:4.1.3.dfsg.1-4                   X.Org X server -- Rendition display driver
ii  xserver-xorg-video-s3                      1:0.5.0-4                          X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-s3virge                 1:1.9.1-7                          X.Org X server -- S3 ViRGE display driver
ii  xserver-xorg-video-savage                  1:2.1.3-5                          X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion           1:1.5.1-3                          X.Org X server -- SiliconMotion display driv
ii  xserver-xorg-video-sis                     1:0.9.3-6                          X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                  1:0.8.1-9                          X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                    1:1.3.0-6                          X.Org X server -- tdfx display driver
ii  xserver-xorg-video-tga                     1:1.1.0-9ubuntu1                   X.Org X server -- TGA display driver
ii  xserver-xorg-video-trident                 1:1.2.4-1                          X.Org X server -- Trident display driver
ii  xserver-xorg-video-tseng                   1:1.1.1-4                          X.Org X server -- Tseng display driver
ii  xserver-xorg-video-v4l                     1:0.1.1-6ubuntu1                   X.Org X server -- Video 4 Linux display driv
ii  xserver-xorg-video-vesa                    1:1.3.0-4ubuntu4                   X.Org X server -- VESA display driver
ii  xserver-xorg-video-vga                     1:4.1.0-8                          X.Org X server -- VGA display driver
ii  xserver-xorg-video-via                     1:0.2.2-5                          X.Org X server -- VIA display driver
ii  xserver-xorg-video-vmware                  1:10.15.2-1ubuntu2                 X.Org X server -- VMware display driver
ii  xserver-xorg-video-voodoo                  1:1.1.1-5                          X.Org X server -- Voodoo display driver
ii  xsltproc                                   1.1.22-1ubuntu1                    XSLT command line processor
ii  xterm                                      229-1ubuntu1                       X terminal emulator
ii  xulrunner-1.9                              1.9+nobinonly-0ubuntu0.8.04.1      XUL + XPCOM application runner
ii  xulrunner-1.9-gnome-support                1.9+nobinonly-0ubuntu0.8.04.1      Support for Gnome in xulrunner-1.9 applicati
ii  xutils                                     1:7.3+10ubuntu10                   X Window System utility programs metapackage
ii  xutils-dev                                 1:7.2.ds2-1ubuntu1                 X Window System utility programs for develop
ii  yelp                                       2.22.1-0ubuntu2.8.04.1             Help browser for GNOME 2
ii  zenity                                     2.22.1-1                           Display graphical dialog boxes from shell sc
ii  zip                                        2.32-1                             Archiver for .zip files
ii  zlib1g                                     1:1.2.3.3.dfsg-7ubuntu1            compression library - runtime

```

---

### Post by Crafty Kisses on 2008-06-28
Try the following:
```
sudo dpkg --configure -a
```

---

### Post by sdennie on 2008-06-28
Have you tried either:

```

sudo apt-get install -f

```

or

```

sudo dpkg --configure -a

```

Both fix common problems like this.

---

### Post by Crafty Kisses on 2008-06-28
> **vor said:**
> Have you tried either:

```

sudo apt-get install -f

```

or

```

sudo dpkg --configure -a

```

Both fix common problems like this.

Yep, that should solve the problem.

---

### Post by shoaibi on 2008-06-28
i tried apt-get install -f, problem is i am installing kannel from deb files, those files are meant for debian (sarge) and idelaly should work fine on ubuntu, but they kannel needs:
libmysqlclient10 
libssl0.9.7

which are not available under ubuntu as i guess, the message that i was shown in apt-get install -f was also something like this:
"this package is linked to another package, either this package is obselete or...." (dont remember much of it, and cant check as i am doing a system upgrade...)

---

### Post by sdennie on 2008-06-28
Is there a reason you need to use the debian packages?  "kannel" is in the Ubuntu repos.  Try:

```

sudo apt-get remove kannel
sudo apt-get install kannel

```

---

