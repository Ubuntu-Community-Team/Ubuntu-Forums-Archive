---
title: "No ubuntu updates for over a week since 12.10 upgrade?"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by robothebobo on 2012-10-27
This might seem like a silly question, but since updating to xubuntu 12.10 from 12.04, I have had 0 updates required for more than a week. I access the computer via ssh and use apt-get.

I've done apt-get clean, update, dist-upgrade... I consistently get:

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I'm starting to wonder if something is broken, but I don't know where to start looking. Any help? Or has there been a complete lull in updates?

My output from *dpkg --list | grep 'ii '* is:

```
ii  a2ps                                      1:4.14-1.1                                 amd64        GNU a2ps - 'Anything to PostScript' converter and pretty-printer
ii  abiword                                   2.9.2+svn20120603-8                        amd64        efficient, featureful word processor with collaboration
ii  abiword-common                            2.9.2+svn20120603-8                        all          efficient, featureful word processor with collaboration -- common files
ii  abiword-plugin-grammar                    2.9.2+svn20120603-8                        amd64        grammar checking plugin for AbiWord
ii  abiword-plugin-mathview                   2.9.2+svn20120603-8                        amd64        equation editor plugin for AbiWord
ii  account-plugin-facebook                   0.8-0ubuntu2                               amd64        GNOME Control Center account plugin for single signon - facebook
ii  account-plugin-flickr                     0.8-0ubuntu2                               amd64        GNOME Control Center account plugin for single signon - flickr
ii  account-plugin-google                     0.8-0ubuntu2                               amd64        GNOME Control Center account plugin for single signon
ii  accountsservice                           0.6.21-6ubuntu5                            amd64        query and manipulate user account information
ii  acl                                       2.2.51-8ubuntu2                            amd64        Access control list utilities
ii  acpi-support                              0.141                                      amd64        scripts for handling many ACPI events
ii  acpid                                     1:2.0.16-1ubuntu1                          amd64        Advanced Configuration and Power Interface event daemon
ii  adduser                                   3.113+nmu1ubuntu1                          all          add and remove users and groups
ii  alsa-base                                 1.0.25+dfsg-0ubuntu3                       all          ALSA driver configuration files
ii  alsa-utils                                1.0.25-3ubuntu2                            amd64        Utilities for configuring and using ALSA
ii  anacron                                   2.3-19ubuntu1                              amd64        cron-like program that doesn't go by time
ii  apg                                       2.2.3.dfsg.1-2build1                       amd64        Automated Password Generator - Standalone version
ii  app-install-data                          0.12.10.6                                  all          Ubuntu applications (data files)
ii  app-install-data-partner                  12.12.10                                   all          Application Installer (data files for partner applications/repositories)
ii  apparmor                                  2.8.0-0ubuntu5                             amd64        User-space parser utility for AppArmor
ii  apparmor-utils                            2.8.0-0ubuntu5                             amd64        Utilities for controlling AppArmor
ii  appmenu-gtk                               12.10.2-0ubuntu1                           amd64        Export GTK menus over DBus
ii  appmenu-gtk3                              12.10.2-0ubuntu1                           amd64        Export GTK menus over DBus
ii  appmenu-qt                                0.2.6-1ubuntu1                             amd64        application menu for Qt
ii  apport                                    2.6.1-0ubuntu3                             all          automatically generate crash reports for debugging
ii  apport-gtk                                2.6.1-0ubuntu3                             all          GTK+ frontend for the apport crash report system
ii  apport-symptoms                           0.19                                       all          symptom scripts for apport
ii  apt                                       0.9.7.5ubuntu5                             amd64        commandline package manager
ii  apt-transport-https                       0.9.7.5ubuntu5                             amd64        https download transport for APT
ii  apt-utils                                 0.9.7.5ubuntu5                             amd64        package managment related utility programs
ii  apt-xapian-index                          0.44ubuntu7                                all          maintenance and search tools for a Xapian index of Debian packages
ii  aptdaemon                                 0.45+bzr861-0ubuntu9.1                     all          transaction based package management service
ii  aptdaemon-data                            0.45+bzr861-0ubuntu9.1                     all          data files for clients
ii  aptitude                                  0.6.8.1-2ubuntu1                           amd64        terminal-based package manager
ii  aptitude-common                           0.6.8.1-2ubuntu1                           all          architecture indepedent files for the aptitude package manager
ii  apturl                                    0.5.1ubuntu6                               amd64        install packages using the apt protocol - GTK+ frontend
ii  apturl-common                             0.5.1ubuntu6                               amd64        install packages using the apt protocol - common data
ii  aspell                                    0.60.7~20110707-1build1                    amd64        GNU Aspell spell-checker
ii  aspell-en                                 7.1-0-1                                    all          English dictionary for GNU Aspell
ii  at                                        3.1.13-2ubuntu1                            amd64        Delayed job execution and batch processing
ii  at-spi2-core                              2.6.0-0ubuntu1                             amd64        Assistive Technology Service Provider Interface (dbus core)
ii  avahi-autoipd                             0.6.31-1ubuntu2                            amd64        Avahi IPv4LL network address configuration daemon
ii  avahi-daemon                              0.6.31-1ubuntu2                            amd64        Avahi mDNS/DNS-SD daemon
ii  avahi-utils                               0.6.31-1ubuntu2                            amd64        Avahi browsing, publishing and discovery utilities
ii  bamfdaemon                                0.3.2-0ubuntu1                             amd64        Window matching library - daemon
ii  base-files                                6.5ubuntu11                                amd64        Debian base system miscellaneous files
ii  base-passwd                               3.5.26                                     amd64        Debian base system master password and group files
ii  bash                                      4.2-5ubuntu1                               amd64        GNU Bourne Again SHell
ii  bash-completion                           1:2.0-1ubuntu2                             all          programmable completion for the bash shell
ii  bash-doc                                  4.2-5ubuntu1                               all          Documentation and examples for the The GNU Bourne Again SHell
ii  bc                                        1.06.95-4                                  amd64        GNU bc arbitrary precision calculator language
ii  beep                                      1.3-3                                      amd64        advanced pc-speaker beeper
ii  bind9-host                                1:9.8.1.dfsg.P1-4.2ubuntu3                 amd64        Version of 'host' bundled with BIND 9.X
ii  binfmt-support                            2.0.12                                     amd64        Support for extra binary formats
ii  binutils                                  2.22.90.20120924-0ubuntu2                  amd64        GNU assembler, linker and binary utilities
ii  bison                                     1:2.5.dfsg-2.1build1                       amd64        YACC-compatible parser generator
ii  blueman                                   1.23-0ubuntu3                              amd64        A Graphical bluetooth manager
ii  bluez                                     4.101-0ubuntu6                             amd64        Bluetooth tools and daemons
ii  bluez-alsa:amd64                          4.101-0ubuntu6                             amd64        Bluetooth ALSA support
ii  bluez-cups                                4.101-0ubuntu6                             amd64        Bluetooth printer driver for CUPS
ii  brasero-common                            3.4.1-0ubuntu2                             all          Common files for the Brasero CD burning application and library
ii  brltty                                    4.4-5ubuntu3                               amd64        Access software for a blind person using a braille display
ii  brltty-x11                                4.4-5ubuntu3                               amd64        Access software for a blind person using a braille display - X11 drivers
ii  bsdmainutils                              9.0.3ubuntu1                               amd64        collection of more utilities from FreeBSD
ii  bsdutils                                  1:2.20.1-5.1ubuntu2                        amd64        Basic utilities from 4.4BSD-Lite
ii  build-essential                           11.5ubuntu3                                amd64        Informational list of build-essential packages
ii  busybox-initramfs                         1:1.19.3-7ubuntu1                          amd64        Standalone shell setup for initramfs
ii  busybox-static                            1:1.19.3-7ubuntu1                          amd64        Standalone rescue shell with tons of builtin utilities
ii  bzip2                                     1.0.6-4                                    amd64        high-quality block-sorting file compressor - utilities
ii  c2esp                                     25c-1ubuntu1                               all          transitional dummy package for c2esp printer driver
ii  ca-certificates                           20120623                                   all          Common CA certificates
ii  ca-certificates-java                      20120721                                   all          Common CA certificates (JKS keystore)
ii  camorama                                  0.19-2.2ubuntu1                            amd64        gnome utility to view and save images from a webcam
ii  catfish                                   0.4.0.2-0ubuntu1                           all          file search tool that support several different engines
ii  checkinstall                              1.6.2-3ubuntu1                             amd64        installation tracker
ii  cherokee                                  1.2.101-1                                  amd64        Very fast, flexible and easy to configure web server
ii  cherokee-admin                            1.2.101-1                                  amd64        Cherokee web server - Administrative plugin
ii  cherokee-doc                              1.2.101-1                                  all          Very fast, flexible and easy to configure web server
ii  cli-common                                0.8.2                                      all          common files between all CLI packages
ii  cmap-adobe-japan1                         0+20090930-2                               all          CMaps for Adobe-Japan1
ii  colord                                    0.1.21-1ubuntu2                            amd64        system service to manage device colour profiles -- system daemon
ii  command-not-found                         0.3ubuntu5                                 all          Suggest installation of packages in interactive bash sessions
ii  command-not-found-data                    0.3ubuntu5                                 amd64        Set of data files for command-not-found.
ii  compiz                                    1:0.9.8.4-0ubuntu2                         all          OpenGL window and compositing manager
ii  compiz-core                               1:0.9.8.4-0ubuntu2                         amd64        OpenGL window and compositing manager
ii  compiz-gnome                              1:0.9.8.4-0ubuntu2                         amd64        OpenGL window and compositing manager - GNOME window decorator
ii  compiz-plugins-default                    1:0.9.8.4-0ubuntu2                         amd64        OpenGL window and compositing manager - default plugins
ii  console-setup                             1.70ubuntu6                                all          console font and keymap setup program
ii  consolekit                                0.4.5-3                                    amd64        framework for defining and tracking users, sessions and seats
ii  coreutils                                 8.13-3.2ubuntu2                            amd64        GNU core utilities
ii  cpio                                      2.11-8ubuntu3                              amd64        GNU cpio -- a program to manage archives of files
ii  cpp                                       4:4.7.2-1ubuntu2                           amd64        GNU C preprocessor (cpp)
ii  cpp-4.5                                   4.5.4-1ubuntu2                             amd64        GNU C preprocessor
ii  cpp-4.6                                   4.6.3-10ubuntu1                            amd64        GNU C preprocessor
ii  cpp-4.7                                   4.7.2-2ubuntu1                             amd64        GNU C preprocessor
ii  cracklib-runtime                          2.8.19-1                                   amd64        runtime support for password checker library cracklib2
ii  crda                                      1.1.2-1ubuntu2                             amd64        wireless Central Regulatory Domain Agent
ii  cron                                      3.0pl1-121ubuntu1                          amd64        process scheduling daemon
ii  cups                                      1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - server
ii  cups-bsd                                  1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - BSD commands
ii  cups-client                               1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                               1.6.1-0ubuntu11                            all          Common UNIX Printing System(tm) - common files
ii  cups-driver-gutenprint                    5.2.9-1ubuntu1                             all          transitional dummy package for gutenprint printer driver
ii  cups-filters                              1.0.24-2                                   amd64        OpenPrinting CUPS Filters
ii  cups-ppdc                                 1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  curl                                      7.27.0-1ubuntu1                            amd64        command line tool for transferring data with URL syntax
ii  dash                                      0.5.7-3ubuntu1                             amd64        POSIX-compliant shell
ii  dbus                                      1.6.4-1ubuntu4                             amd64        simple interprocess messaging system (daemon and utilities)
ii  dbus-x11                                  1.6.4-1ubuntu4                             amd64        simple interprocess messaging system (X11 deps)
ii  dc                                        1.06.95-4                                  amd64        GNU dc arbitrary precision reverse-polish calculator
ii  dconf-gsettings-backend:amd64             0.14.0-0ubuntu2                            amd64        simple configuration storage system - GSettings back-end
ii  dconf-service                             0.14.0-0ubuntu2                            amd64        simple configuration storage system - D-Bus service
ii  dconf-tools                               0.14.0-0ubuntu2                            amd64        simple configuration storage system - utilities
ii  debconf                                   1.5.46ubuntu1                              all          Debian configuration management system
ii  debconf-i18n                              1.5.46ubuntu1                              all          full internationalization support for debconf
ii  debhelper                                 9.20120608ubuntu1                          all          helper programs for debian/rules
ii  debianutils                               4.3.4                                      amd64        Miscellaneous utilities specific to Debian
ii  defoma                                    0.11.12ubuntu1                             all          Debian Font Manager -- automatic font configuration framework
ii  desktop-file-utils                        0.20-0.1ubuntu1                            amd64        Utilities for .desktop files
ii  dh-apparmor                               2.8.0-0ubuntu5                             all          AppArmor debhelper routines
ii  dictionaries-common                       1.12.10                                    all          Common utilities for spelling dictionary tools
ii  diffstat                                  1.55-3                                     amd64        produces graph of changes introduced by a diff file
ii  diffutils                                 1:3.2-6ubuntu1                             amd64        File comparison utilities
ii  dmidecode                                 2.11+20120326-2                            amd64        SMBIOS/DMI table decoder
ii  dmsetup                                   2:1.02.74-4ubuntu1                         amd64        Linux Kernel Device Mapper userspace library
ii  dmz-cursor-theme                          0.4.3                                      all          Style neutral, scalable cursor theme
ii  dnsmasq-base                              2.63-1ubuntu1                              amd64        Small caching DNS proxy and DHCP/TFTP server
ii  dnsutils                                  1:9.8.1.dfsg.P1-4.2ubuntu3                 amd64        Clients provided with BIND
ii  doc-base                                  0.10.4                                     all          utilities to manage online documentation
ii  docbook-xml                               4.5-7ubuntu1                               all          standard XML documentation system for software and systems
ii  dosfstools                                3.0.13-1                                   amd64        utilities for making and checking MS-DOS FAT filesystems
ii  dpkg                                      1.16.7ubuntu6                              amd64        Debian package management system
ii  dpkg-dev                                  1.16.7ubuntu6                              all          Debian package development tools
ii  dvd+rw-tools                              7.1-10build1                               amd64        DVD+-RW/R tools
ii  e2fslibs:amd64                            1.42.5-1ubuntu2                            amd64        ext2/ext3/ext4 file system libraries
ii  e2fsprogs                                 1.42.5-1ubuntu2                            amd64        ext2/ext3/ext4 file system utilities
ii  ed                                        1.6-2                                      amd64        classic UNIX line editor
ii  eject                                     2.1.5+deb1+cvs20081104-11                  amd64        ejects CDs and operates CD-Changers under Linux
ii  elementary-icon-theme                     2.7.1-0ubuntu6                             all          simple and appealing Tango-styled icon theme
ii  enchant                                   1.6.0-7build1                              amd64        Wrapper for various spell checker engines (binary programs)
ii  esniper                                   2.27.0-1                                   amd64        simple, lightweight tool for sniping ebay auctions
ii  espeak                                    1.46.02-2ubuntu1                           amd64        Multi-lingual software speech synthesizer
ii  espeak-data:amd64                         1.46.02-2ubuntu1                           amd64        Multi-lingual software speech synthesizer: speech data files
ii  ethtool                                   1:3.4.1-1                                  amd64        display or change Ethernet device settings
ii  evince-common                             3.6.0-0ubuntu2                             all          Document (PostScript, PDF) viewer - common files
ii  evolution-data-server                     3.6.0-0ubuntu2                             amd64        evolution database backend server
ii  evolution-data-server-common              3.6.0-0ubuntu2                             all          architecture independent files for Evolution Data Server
ii  exiv2                                     0.23-1                                     amd64        EXIF/IPTC metadata manipulation tool
ii  exo-utils                                 0.8.0-1                                    amd64        Utility files for libexo
ii  fakeroot                                  1.18.4-2                                   amd64        tool for simulating superuser privileges
ii  ffmpeg                                    6:0.8.3-6ubuntu2                           amd64        Multimedia player, server, encoder and transcoder (transitional package)
ii  file                                      5.11-2                                     amd64        Determines file type using "magic" numbers
ii  file-roller                               3.6.0-0ubuntu3                             amd64        archive manager for GNOME
ii  findutils                                 4.4.2-4ubuntu2                             amd64        utilities for finding files--find, xargs
ii  finger                                    0.17-15                                    amd64        user information lookup program
ii  firefox                                   16.0.1+build1-0ubuntu1                     amd64        Safe and easy web browser from Mozilla
ii  firefox-globalmenu                        16.0.1+build1-0ubuntu1                     amd64        Unity appmenu integration for Firefox
ii  firefox-gnome-support                     16.0.1+build1-0ubuntu1                     amd64        Safe and easy web browser from Mozilla - GNOME support
ii  firefox-locale-en                         16.0.1+build1-0ubuntu1                     amd64        English language pack for Firefox
ii  flex                                      2.5.35-10.1ubuntu1                         amd64        A fast lexical analyzer generator.
ii  fontconfig                                2.10.1-0ubuntu3                            amd64        generic font configuration library - support binaries
ii  fontconfig-config                         2.10.1-0ubuntu3                            all          generic font configuration library - configuration
ii  fonts-droid                               20111207+git-1ubuntu1                      all          handheld device font with extensive style and language support
ii  fonts-freefont-ttf                        20120503-1                                 all          Freefont Serif, Sans and Mono Truetype fonts
ii  fonts-kacst                               2.01+mry-6                                 all          KACST free TrueType Arabic fonts
ii  fonts-kacst-one                           5.0+svn11846-6                             all          TrueType font designed for Arabic language
ii  fonts-khmeros-core                        5.0-5ubuntu1                               all          KhmerOS Unicode fonts for the Khmer language of Cambodia
ii  fonts-lao                                 0.0.20060226-8                             all          TrueType font for Lao language
ii  fonts-liberation                          1.07.2-5                                   all          Fonts with the same metrics as Times, Arial and Courier
ii  fonts-lyx                                 2.0.3-3                                    all          TrueType versions of some TeX fonts used by LyX
ii  fonts-takao-pgothic                       003.02.01-5ubuntu1                         all          Japanese TrueType font set, Takao P Gothic Fonts
ii  fonts-thai-tlwg                           1:0.5.0-5                                  all          Thai fonts maintained by TLWG (meta package)
ii  fonts-tlwg-garuda                         1:0.5.0-5                                  all          Thai Garuda font
ii  fonts-tlwg-kinnari                        1:0.5.0-5                                  all          Thai Kinnari font
ii  fonts-tlwg-loma                           1:0.5.0-5                                  all          Thai Loma font
ii  fonts-tlwg-mono                           1:0.5.0-5                                  all          Thai TlwgMono font
ii  fonts-tlwg-norasi                         1:0.5.0-5                                  all          Thai Norasi font
ii  fonts-tlwg-purisa                         1:0.5.0-5                                  all          Thai Purisa font
ii  fonts-tlwg-sawasdee                       1:0.5.0-5                                  all          Thai Sawasdee font
ii  fonts-tlwg-typewriter                     1:0.5.0-5                                  all          Thai TlwgTypewriter font
ii  fonts-tlwg-typist                         1:0.5.0-5                                  all          Thai TlwgTypist font
ii  fonts-tlwg-typo                           1:0.5.0-5                                  all          Thai TlwgTypo font
ii  fonts-tlwg-umpush                         1:0.5.0-5                                  all          Thai Umpush font
ii  fonts-tlwg-waree                          1:0.5.0-5                                  all          Thai Waree font
ii  fonts-unfonts-core                        1.0.3.is.1.0.2-080608-5ubuntu2             all          Un series Korean TrueType fonts
ii  foo2zjs                                   20120510dfsg0-1ubuntu1                     all          transitional dummy package for foo2zjs printer driver
ii  foomatic-db-compressed-ppds               20120823-0ubuntu4                          all          OpenPrinting printer support - Compressed PPDs derived from the database
ii  foomatic-db-engine                        4.0.8-3                                    amd64        OpenPrinting printer support - programs
ii  foomatic-filters                          4.0.17-1                                   amd64        OpenPrinting printer support - filters
ii  freepats                                  20060219-1                                 all          Free patch set for MIDI audio synthesis
ii  freerdp-x11                               1.0.1-1ubuntu7                             amd64        RDP client for Windows Terminal Services
ii  friendly-recovery                         0.2.25                                     all          Make recovery more user-friendly
ii  ftp                                       0.17-27                                    amd64        classical file transfer client
ii  fuse                                      2.9.0-1ubuntu2                             amd64        Filesystem in Userspace
ii  fuse-utils                                2.9.0-1ubuntu2                             all          Filesystem in Userspace (transitional package)
ii  g++                                       4:4.7.2-1ubuntu2                           amd64        GNU C++ compiler
ii  g++-4.5                                   4.5.4-1ubuntu2                             amd64        GNU C++ compiler
ii  g++-4.7                                   4.7.2-2ubuntu1                             amd64        GNU C++ compiler
ii  gamin                                     0.1.10-4ubuntu1                            amd64        File and directory monitoring system
ii  gcalctool                                 6.6.0-0ubuntu1                             amd64        GNOME desktop calculator
ii  gcc                                       4:4.7.2-1ubuntu2                           amd64        GNU C compiler
ii  gcc-4.5                                   4.5.4-1ubuntu2                             amd64        GNU C compiler
ii  gcc-4.5-base:amd64                        4.5.4-1ubuntu2                             amd64        GNU Compiler Collection (base package)
ii  gcc-4.6                                   4.6.3-10ubuntu1                            amd64        GNU C compiler
ii  gcc-4.6-base:amd64                        4.6.3-10ubuntu1                            amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.7                                   4.7.2-2ubuntu1                             amd64        GNU C compiler
ii  gcc-4.7-base:amd64                        4.7.2-2ubuntu1                             amd64        GCC, the GNU Compiler Collection (base package)
ii  gconf-service                             3.2.5-0ubuntu4                             amd64        GNOME configuration database system (D-Bus service)
ii  gconf-service-backend                     3.2.5-0ubuntu4                             amd64        GNOME configuration database system (D-Bus service)
ii  gconf2                                    3.2.5-0ubuntu4                             amd64        GNOME configuration database system (support tools)
ii  gconf2-common                             3.2.5-0ubuntu4                             all          GNOME configuration database system (common files)
ii  gcr                                       3.6.0-0ubuntu1                             amd64        GNOME crypto services (daemon and tools)
ii  gdb                                       7.5-0ubuntu2                               amd64        The GNU Debugger
ii  gdm                                       3.6.1-0ubuntu1                             amd64        Next generation GNOME Display Manager
ii  genisoimage                               9:1.1.11-2ubuntu3                          amd64        Creates ISO-9660 CD-ROM filesystem images
ii  geoclue                                   0.12.99-0ubuntu2                           amd64        Geographic information framework
ii  geoclue-ubuntu-geoip                      1.0.0-0ubuntu1                             amd64        Provide positioning for GeoClue via Ubuntu GeoIP services
ii  geoip-database                            20120609-1                                 all          IP lookup command line tools that use the GeoIP library (country database)
ii  gettext                                   0.18.1.1-9ubuntu1                          amd64        GNU Internationalization utilities
ii  gettext-base                              0.18.1.1-9ubuntu1                          amd64        GNU Internationalization utilities for the base system
ii  ghostscript                               9.06~dfsg-0ubuntu4                         amd64        interpreter for the PostScript language and for PDF
ii  ghostscript-cups                          9.06~dfsg-0ubuntu4                         amd64        interpreter for the PostScript language and for PDF - CUPS filters
ii  ghostscript-x                             9.06~dfsg-0ubuntu4                         amd64        interpreter for the PostScript language and for PDF - X11 support
ii  gigolo                                    0.4.1-3                                    amd64        frontend to manage connections to remote filesystems using GIO/GVfs
ii  gimp                                      2.8.2-1ubuntu1                             amd64        The GNU Image Manipulation Program
ii  gimp-data                                 2.8.2-1ubuntu1                             all          Data files for GIMP
ii  gimp-help-common                          2.6.1-1                                    all          Data files for the GIMP documentation
ii  gimp-help-en                              2.6.1-1                                    all          Documentation for the GIMP (English)
ii  gir1.2-accounts-1.0                       1.3-0ubuntu2                               amd64        typelib file for libaccounts-glib0
ii  gir1.2-appindicator-0.1                   12.10.0-0ubuntu1                           amd64        Typelib files for libappindicator1.
ii  gir1.2-appindicator3-0.1                  12.10.0-0ubuntu1                           amd64        Typelib files for libappindicator3-1.
ii  gir1.2-atk-1.0                            2.6.0-0ubuntu1                             amd64        ATK accessibility toolkit (GObject introspection)
ii  gir1.2-atspi-2.0                          2.6.0-0ubuntu1                             amd64        Assistive Technology Service Provider (GObject introspection)
ii  gir1.2-dbusmenu-glib-0.4                  12.10.2-0ubuntu1                           amd64        typelib file for libdbusmenu-glib4
ii  gir1.2-dbusmenu-gtk-0.4                   12.10.2-0ubuntu1                           amd64        typelib file for libdbusmenu-gtk4
ii  gir1.2-dee-0.5                            0.5.22-0ubuntu1                            amd64        GObject introspection data for the Dee library
ii  gir1.2-dee-1.0                            1.0.14-0ubuntu1                            amd64        GObject introspection data for the Dee library
ii  gir1.2-freedesktop                        1.33.14-1                                  amd64        Introspection data for some FreeDesktop components
ii  gir1.2-gdata-0.0                          0.13.2-0ubuntu1                            amd64        GObject introspection data for the GData webservices library
ii  gir1.2-gdkpixbuf-2.0                      2.26.4-0ubuntu1                            amd64        GDK Pixbuf library - GObject-Introspection
ii  gir1.2-glib-2.0                           1.33.14-1                                  amd64        Introspection data for GLib, GObject, Gio and GModule
ii  gir1.2-gmenu-3.0                          3.6.0-0ubuntu1                             amd64        GObject introspection data for the GNOME menu library
ii  gir1.2-goa-1.0                            3.6.0-0ubuntu1                             amd64        Introspection data for GNOME Online Accounts
ii  gir1.2-gst-plugins-base-0.10              0.10.36-1ubuntu1                           amd64        Description: GObject introspection data for the GStreamer Plugins Base library
ii  gir1.2-gstreamer-0.10                     0.10.36-1ubuntu2                           amd64        Description: GObject introspection data for the GStreamer library
ii  gir1.2-gtk-2.0                            2.24.13-0ubuntu2                           amd64        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtk-3.0                            3.6.0-0ubuntu3                             amd64        GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gudev-1.0                          175-0ubuntu13                              amd64        libgudev-1.0 introspection data
ii  gir1.2-indicate-0.7                       12.10.1-0ubuntu1                           amd64        Typelib file for libindicate5
ii  gir1.2-javascriptcoregtk-3.0              1.10.0-0ubuntu1                            amd64        GObject introspection data for the GTK+-based JavaScriptCore library
ii  gir1.2-notify-0.7                         0.7.5-1build1                              amd64        sends desktop notifications to a notification daemon (Introspection files)
ii  gir1.2-pango-1.0                          1.30.1-0ubuntu3                            amd64        Layout and rendering of internationalized text - gir bindings
ii  gir1.2-rb-3.0                             2.97-1ubuntu5                              amd64        GObject introspection data for the rhythmbox music player
ii  gir1.2-signon-1.0                         1.6-0ubuntu1                               amd64        GObject introspection data for the Signon library
ii  gir1.2-soup-2.4                           2.40.0-0ubuntu1                            amd64        GObject introspection data for the libsoup HTTP library
ii  gir1.2-syncmenu-0.1                       12.10.4-0ubuntu1                           amd64        indicator for synchronisation processes status - bindings
ii  gir1.2-ubuntuoneui-3.0                    4.0.0-0ubuntu1                             amd64        Ubuntu One widget library
ii  gir1.2-unity-4.0                          4.0.6-0ubuntu3                             amd64        GObject introspection data for the Unity library
ii  gir1.2-vte-2.90                           1:0.34.0-0ubuntu1                          amd64        GObject introspection data for the VTE library
ii  gir1.2-webkit-3.0                         1.10.0-0ubuntu1                            amd64        GObject introspection data for the WebKit library
ii  gir1.2-wnck-3.0                           3.4.3-0ubuntu1                             amd64        GObject introspection data for the WNCK library
ii  git                                       1:1.7.10.4-1ubuntu1                        amd64        fast, scalable, distributed revision control system
ii  git-man                                   1:1.7.10.4-1ubuntu1                        all          fast, scalable, distributed revision control system (manual pages)
ii  gksu                                      2.0.2-6ubuntu2                             amd64        graphical frontend to su
ii  glib-networking:amd64                     2.34.0-0ubuntu1                            amd64        network-related giomodules for GLib
ii  glib-networking-common                    2.34.0-0ubuntu1                            all          network-related giomodules for GLib - data files
ii  glib-networking-services                  2.34.0-0ubuntu1                            amd64        network-related giomodules for GLib - D-Bus services
ii  gnome-accessibility-themes                3.6.0.2-0ubuntu1                           all          accessibility themes for the GNOME desktop
ii  gnome-control-center                      1:3.4.2-0ubuntu19                          amd64        utilities to configure the GNOME desktop
ii  gnome-control-center-data                 1:3.4.2-0ubuntu19                          all          configuration applets for GNOME - data files
ii  gnome-control-center-signon               0.0.18-0ubuntu1                            amd64        GNOME Control Center extension for single signon
ii  gnome-desktop-data                        1:2.32.1-2ubuntu1                          all          Common files for GNOME desktop apps
ii  gnome-desktop3-data                       3.6.0.1-0ubuntu2                           all          Common files for GNOME desktop apps
ii  gnome-doc-utils                           0.20.10-1                                  all          collection of documentation utilities for the GNOME project
ii  gnome-games-common                        1:3.2.1-0ubuntu1                           all          data files for the GNOME games
ii  gnome-games-data                          1:3.6.0.2-0ubuntu1                         all          data files for the GNOME games
ii  gnome-icon-theme                          3.6.0-0ubuntu2                             all          GNOME Desktop icon theme (small subset)
ii  gnome-icon-theme-full                     3.6.0-0ubuntu2                             all          GNOME Desktop icon theme
ii  gnome-icon-theme-symbolic                 3.6.0-0ubuntu1                             all          GNOME desktop icon theme (symbolic icons)
ii  gnome-keyring                             3.6.0-0ubuntu1                             amd64        GNOME keyring services (daemon and tools)
ii  gnome-mahjongg                            1:3.6.0.2-0ubuntu1                         amd64        classic Eastern tile game for GNOME
ii  gnome-menus                               3.6.0-0ubuntu1                             amd64        GNOME implementation of the freedesktop menu specification
ii  gnome-online-accounts                     3.6.0-0ubuntu1                             amd64        GNOME Online Accounts
ii  gnome-session-bin                         3.6.0-0ubuntu1                             amd64        GNOME Session Manager - Minimal runtime
ii  gnome-settings-daemon                     3.4.2-0ubuntu14                            amd64        daemon handling the GNOME session settings
ii  gnome-sudoku                              1:3.6.0.2-0ubuntu1                         all          Sudoku puzzle game for GNOME
ii  gnome-system-tools                        3.0.0-2ubuntu1                             amd64        Cross-platform configuration utilities for GNOME
ii  gnome-time-admin                          3.0.0-2ubuntu1                             amd64        GNOME Time Administration Tool
ii  gnome-user-guide                          3.4.2-1                                    all          GNOME user's guide
ii  gnomine                                   1:3.6.0.2-0ubuntu1                         amd64        popular minesweeper puzzle game for GNOME
ii  gnumeric                                  1.10.17-1.1ubuntu1                         amd64        spreadsheet application for GNOME - main program
ii  gnumeric-common                           1.10.17-1.1ubuntu1                         all          spreadsheet application for GNOME - common files
ii  gnumeric-doc                              1.10.17-1.1ubuntu1                         all          spreadsheet application for GNOME - documentation
ii  gnupg                                     1.4.11-3ubuntu4                            amd64        GNU privacy guard - a free PGP replacement
ii  gpgv                                      1.4.11-3ubuntu4                            amd64        GNU privacy guard - signature verification tool
ii  grep                                      2.12-2                                     amd64        GNU grep, egrep and fgrep
ii  groff-base                                1.21-9                                     amd64        GNU troff text-formatting system (base system components)
ii  growisofs                                 7.1-10build1                               amd64        DVD+-RW/R recorder
ii  grub-common                               2.00-7ubuntu11                             amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                     0.6                                        amd64        GRUB gfxpayload blacklist
ii  grub-pc                                   2.00-7ubuntu11                             amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                               2.00-7ubuntu11                             amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                              2.00-7ubuntu11                             amd64        GRand Unified Bootloader (common files for version 2)
ii  gs-cjk-resource                           1.20100103-3                               all          Resource files for gs-cjk, ghostscript CJK-TrueType extension
ii  gsettings-desktop-schemas                 3.6.0-0ubuntu3                             all          GSettings deskop-wide schemas
ii  gsfonts                                   1:8.11+urwcyr1.0.7~pre44-4.2ubuntu1        all          Fonts for the Ghostscript interpreter(s)
ii  gsfonts-x11                               0.22                                       all          Make Ghostscript fonts available to X11
ii  gstreamer0.10-alsa:amd64                  0.10.36-1ubuntu1                           amd64        GStreamer plugin for ALSA
ii  gstreamer0.10-gnomevfs:amd64              0.10.36-1ubuntu1                           amd64        GStreamer plugin for GnomeVFS
ii  gstreamer0.10-nice:amd64                  0.1.2-1                                    amd64        ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad:amd64           0.10.23-7ubuntu1                           amd64        GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-base:amd64          0.10.36-1ubuntu1                           amd64        GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps           0.10.36-1ubuntu1                           amd64        GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good:amd64          0.10.31-3ubuntu1                           amd64        GStreamer plugins from the "good" set
ii  gstreamer0.10-pulseaudio:amd64            0.10.31-3ubuntu1                           amd64        GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                       0.10.36-1ubuntu2                           amd64        Tools for use with GStreamer
ii  gstreamer0.10-x:amd64                     0.10.36-1ubuntu1                           amd64        GStreamer plugins for X11 and Pango
ii  gthumb                                    3:3.0.2-0ubuntu2                           amd64        image viewer and browser
ii  gthumb-data                               3:3.0.2-0ubuntu2                           all          image viewer and browser - arch-independent files
ii  gtk2-engines:amd64                        1:2.20.2-2ubuntu1                          amd64        theme engines for GTK+ 2.x
ii  gtk2-engines-murrine:amd64                0.98.2-0ubuntu2                            amd64        cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf:amd64                 2.24.13-0ubuntu2                           amd64        pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-xfce                         3.0.0-1                                    amd64        GTK+-2.0 theme engine for Xfce
ii  gtk3-engines-unico                        1.0.2+r139-0ubuntu2                        amd64        Unico Gtk+ 3 theme engine
ii  gucharmap                                 1:3.5.99-0ubuntu1                          amd64        Unicode character picker and font browser
ii  guile-1.8-libs                            1.8.8+1-6ubuntu3                           amd64        Core Guile libraries
ii  gvfs:amd64                                1.14.0-0ubuntu6                            amd64        userspace virtual filesystem - GIO module
ii  gvfs-backends                             1.14.0-0ubuntu6                            amd64        userspace virtual filesystem - backends
ii  gvfs-bin                                  1.14.0-0ubuntu6                            amd64        userspace virtual filesystem - binaries
ii  gvfs-common                               1.14.0-0ubuntu6                            all          userspace virtual filesystem - common data files
ii  gvfs-daemons                              1.14.0-0ubuntu6                            amd64        userspace virtual filesystem - servers
ii  gvfs-fuse                                 1.14.0-0ubuntu6                            amd64        userspace virtual filesystem - fuse server
ii  gvfs-libs:amd64                           1.14.0-0ubuntu6                            amd64        userspace virtual filesystem - private libraries
ii  gzip                                      1.5-1.1ubuntu1                             amd64        GNU compression utilities
ii  hardening-includes                        2.2                                        all          Makefile for enabling compiler flags for security hardening
ii  hdparm                                    9.37-0ubuntu4                              amd64        tune hard disk parameters for high performance
ii  hicolor-icon-theme                        0.12-1ubuntu2                              all          default fallback theme for FreeDesktop.org icon themes
ii  hostname                                  3.11ubuntu1                                amd64        utility to set/show the host name or domain name
ii  hpijs                                     3.12.6-3ubuntu4                            all          transitional dummy package for hpijs printer driver
ii  hplip-cups                                3.12.6-3ubuntu4                            all          transitional dummy package for hpcups printer driver
ii  hplip-data                                3.12.6-3ubuntu4                            all          HP Linux Printing and Imaging - data files
ii  html2text                                 1.3.2a-15build1                            amd64        advanced HTML to text converter
ii  humanity-icon-theme                       0.6.1                                      all          Humanity Icon theme
ii  hunspell-en-ca                            1:3.3.0-2ubuntu3                           all          English_canadian dictionary for hunspell
ii  hunspell-en-us                            20070829-4ubuntu3                          all          English_american dictionary for hunspell
ii  hwdata                                    0.234-1                                    all          hardware identification / configuration data
ii  ibus                                      1.4.1-7ubuntu1                             amd64        Intelligent Input Bus - core
ii  ibus-gtk:amd64                            1.4.1-7ubuntu1                             amd64        Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3:amd64                           1.4.1-7ubuntu1                             amd64        Intelligent Input Bus - GTK+3 support
ii  ibus-pinyin                               1.4.0-1build1                              amd64        Pinyin engine for IBus
ii  ibus-pinyin-db-android                    1.4.0-1build1                              all          Pinyin engine for IBus - Android database
ii  ibus-table                                1.3.9.20110827-2                           all          table engine for IBus
ii  icedtea-7-jre-jamvm:amd64                 7u7-2.3.2a-1ubuntu1                        amd64        Alternative JVM for OpenJDK, using JamVM
ii  ifupdown                                  0.7.2ubuntu2                               amd64        high level tools to configure network interfaces
ii  im-switch                                 1.22ubuntu2                                all          Input method switch framework
ii  indicator-application                     12.10.0-0ubuntu2                           amd64        Application Indicators
ii  indicator-application-gtk2                12.10.0.1-0ubuntu1                         amd64        Application Indicators
ii  indicator-appmenu                         12.10.3-0ubuntu1                           amd64        Indicator for application menus.
ii  indicator-datetime                        12.10.2-0ubuntu3                           amd64        Simple clock
ii  indicator-messages                        12.10.4-0ubuntu1                           amd64        indicator that collects messages that need a response
ii  indicator-power                           12.10.2-0ubuntu1                           amd64        Indicator showing power state.
ii  indicator-session                         12.10.4-0ubuntu1                           amd64        indicator showing session management, status and user switching
ii  indicator-sound                           12.10.1-0ubuntu1                           amd64        System sound indicator.
ii  indicator-sound-gtk2                      12.10.0.1-0ubuntu1                         amd64        System sound indicator.
ii  info                                      4.13a.dfsg.1-10ubuntu2                     amd64        Standalone GNU Info documentation browser
ii  initramfs-tools                           0.103ubuntu0.2                             all          tools for generating an initramfs
ii  initramfs-tools-bin                       0.103ubuntu0.2                             amd64        binaries used by initramfs-tools
ii  initscripts                               2.88dsf-13.10ubuntu13                      amd64        scripts for initializing and shutting down the system
ii  inputattach                               1:1.4.3-1                                  amd64        utility to connect serial-attached peripherals to the input subsystem
ii  insserv                                   1.14.0-4ubuntu1                            amd64        boot sequence organizer using LSB init.d script dependency information
ii  install-info                              4.13a.dfsg.1-10ubuntu2                     amd64        Manage installed documentation in info format
ii  intel-gpu-tools                           1.3-0ubuntu2                               amd64        tools for debugging the Intel graphics driver
ii  intltool-debian                           0.35.0+20060710.1                          all          Help i18n of RFC822 compliant config files
ii  iproute                                   20120521-3ubuntu1                          amd64        networking and traffic control tools
ii  iptables                                  1.4.12-2ubuntu2                            amd64        administration tools for packet filtering and NAT
ii  iputils-arping                            3:20101006-3ubuntu1                        amd64        Tool to send ICMP echo requests to an ARP address
ii  iputils-ping                              3:20101006-3ubuntu1                        amd64        Tools to test the reachability of network hosts
ii  iputils-tracepath                         3:20101006-3ubuntu1                        amd64        Tools to trace the network path to a remote host
ii  irqbalance                                1.0.3-1ubuntu2                             amd64        Daemon to balance interrupts for SMP systems
ii  irssi                                     0.8.15-5ubuntu1                            amd64        terminal based IRC client
ii  isc-dhcp-client                           4.2.4-1ubuntu10                            amd64        ISC DHCP client
ii  isc-dhcp-common                           4.2.4-1ubuntu10                            amd64        common files used by all the isc-dhcp* packages
ii  isight-firmware-tools                     1.6-1                                      amd64        tools for dealing with Apple iSight firmware
ii  iso-codes                                 3.38-1                                     all          ISO language, territory, currency, script codes and their translations
ii  iw                                        3.4-1                                      amd64        tool for configuring Linux wireless devices
ii  java-common                               0.43ubuntu3                                all          Base of all Java packages
ii  jockey-common                             0.9.7-0ubuntu11                            all          user interface and desktop integration for driver management
ii  jockey-gtk                                0.9.7-0ubuntu11                            all          transitional package for driver management GUI
ii  kbd                                       1.15.3-9ubuntu1                            amd64        Linux console font and keytable utilities
ii  kerneloops-daemon                         0.12+git20090217-3ubuntu3                  amd64        kernel oops tracker
ii  keyboard-configuration                    1.70ubuntu6                                all          system-wide keyboard preferences
ii  klibc-utils                               2.0.1-1ubuntu2                             amd64        small utilities built with klibc for early boot
ii  krb5-locales                              1.10.1+dfsg-2                              all          Internationalization support for MIT Kerberos
ii  language-pack-en                          1:12.10+20121009                           all          translation updates for language English
ii  language-pack-en-base                     1:12.10+20121009                           all          translations for language English
ii  language-pack-gnome-en                    1:12.10+20121009                           all          GNOME translation updates for language English
ii  language-pack-gnome-en-base               1:12.10+20121009                           all          GNOME translations for language English
ii  language-selector-common                  0.90                                       all          Language selector for Ubuntu
ii  language-selector-gnome                   0.90                                       all          Language selector for Ubuntu
ii  language-support-en                       1:9.10+20090909                            all          metapackage for English language support
ii  language-support-writing-en               1:10.04+20100311                           all          Writing aids metapackage for English
ii  laptop-detect                             0.13.7ubuntu2                              amd64        attempt to detect a laptop
ii  launchpad-integration                     0.1.56.2                                   all          launchpad integration
ii  leafpad                                   0.8.18.1-3                                 amd64        GTK+ based simple text editor
ii  leds                                      2.120229-0extras12.04.1                    amd64        Calculate the resistance for LEDs
ii  less                                      444-4ubuntu1                               amd64        pager program similar to more
ii  lftp                                      4.3.8-1                                    amd64        Sophisticated command-line FTP/HTTP client programs
ii  libaa1:amd64                              1.4p5-40                                   amd64        ASCII art library
ii  libabiword-2.8                            2.8.6-0.3ubuntu2                           amd64        efficient, featureful word processor with collaboration -- shared library
ii  libabiword-2.9:amd64                      2.9.2+svn20120603-8                        amd64        efficient, featureful word processor with collaboration -- shared library
ii  libaccount-plugin-1.0-0                   0.0.18-0ubuntu1                            amd64        libaccount-plugin for GNOME Control Center
ii  libaccounts-glib0                         1.3-0ubuntu2                               amd64        library for single signon
ii  libaccounts-qt1                           1.2-0ubuntu2                               amd64        QT library for single sign on
ii  libaccountsservice0                       0.6.21-6ubuntu5                            amd64        query and manipulate user account information - shared libraries
ii  libacl1:amd64                             2.2.51-8ubuntu2                            amd64        Access control list shared library
ii  libaiksaurus-1.2-0c2a                     1.2.1+dev-0.12-6.1                         amd64        an English-language thesaurus (development)
ii  libaiksaurus-1.2-data                     1.2.1+dev-0.12-6.1                         all          an English-language thesaurus (data)
ii  libaiksaurusgtk-1.2-0c2a                  1.2.1+dev-0.12-6.1                         amd64        graphical interface to the Aiksaurus toolkit (library)
ii  libalgorithm-diff-perl                    1.19.02-2                                  all          module to find differences between files
ii  libalgorithm-diff-xs-perl                 0.04-2build3                               amd64        module to find differences between files (XS accelerated)
ii  libalgorithm-merge-perl                   0.08-2                                     all          Perl module for three-way merge of textual data
ii  libamd2.2.0                               1:3.4.0-2ubuntu3                           amd64        approximate minimum degree ordering library for sparse matrices
ii  libao-common                              1.1.0-1ubuntu3                             all          Cross Platform Audio Output Library (Common files)
ii  libao4:amd64                              1.1.0-1ubuntu3                             amd64        Cross Platform Audio Output Library
ii  libapparmor-perl                          2.8.0-0ubuntu5                             amd64        AppArmor library Perl bindings
ii  libapparmor1                              2.8.0-0ubuntu5                             amd64        changehat AppArmor library
ii  libappindicator1                          12.10.0-0ubuntu1                           amd64        Application Indicators
ii  libappindicator3-1                        12.10.0-0ubuntu1                           amd64        Application Indicators
ii  libapt-inst1.5:amd64                      0.9.7.5ubuntu5                             amd64        deb package format runtime library
ii  libapt-pkg-perl                           0.1.26                                     amd64        Perl interface to libapt-pkg
ii  libapt-pkg4.11                            0.8.16~exp5ubuntu13.3                      amd64        APT's package managment runtime library
ii  libapt-pkg4.12:amd64                      0.9.7.5ubuntu5                             amd64        package managment runtime library
ii  libarchive-zip-perl                       1.30-6                                     all          Perl module for manipulation of ZIP archives
ii  libarchive1                               2.8.4-1ubuntu0.11.10.1                     amd64        Single library to read/write tar, cpio, pax, zip, iso9660, etc.
ii  libarchive12:amd64                        3.0.4-2                                    amd64        Multi-format archive and compression library (shared library)
ii  libart-2.0-2:amd64                        2.3.21-2                                   amd64        Library of functions for 2D graphics - runtime files
ii  libasn1-8-heimdal:amd64                   1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - ASN.1 library
ii  libasound2:amd64                          1.0.25-3ubuntu3                            amd64        shared library for ALSA applications
ii  libasound2-plugins:amd64                  1.0.25-2ubuntu1                            amd64        ALSA library additional plugins
ii  libaspell15                               0.60.7~20110707-1build1                    amd64        GNU Aspell spell-checker runtime library
ii  libasprintf0c2:amd64                      0.18.1.1-9ubuntu1                          amd64        GNU library to use fprintf and friends in C++
ii  libass4:amd64                             0.10.0-3                                   amd64        library for SSA/*** subtitles rendering
ii  libasyncns0:amd64                         0.8-4build1                                amd64        Asynchronous name service query library
ii  libatasmart4:amd64                        0.19-1git1                                 amd64        ATA S.M.A.R.T. reading and parsing library
ii  libatk-bridge2.0-0:amd64                  2.6.0-0ubuntu1                             amd64        AT-SPI 2 toolkit bridge - shared library
ii  libatk-wrapper-java                       0.30.4-0ubuntu4                            all          An ATK implementation for Java using JNI
ii  libatk-wrapper-java-jni:amd64             0.30.4-0ubuntu4                            amd64        An ATK implementation for Java using JNI (jni bindings)
ii  libatk1.0-0:amd64                         2.6.0-0ubuntu1                             amd64        ATK accessibility toolkit
ii  libatk1.0-data                            2.6.0-0ubuntu1                             all          Common files for the ATK accessibility toolkit
ii  libatk1.0-dev                             2.6.0-0ubuntu1                             amd64        Development files for the ATK accessibility toolkit
ii  libatm1:amd64                             1:2.5.1-1.4                                amd64        shared library for ATM (Asynchronous Transfer Mode)
ii  libatspi1.0-0                             1.32.0-1ubuntu1                            amd64        C binding libraries of at-spi for GNOME Accessibility
ii  libatspi2.0-0:amd64                       2.6.0-0ubuntu1                             amd64        Assistive Technology Service Provider Interface - shared library
ii  libattr1:amd64                            1:2.4.46-8ubuntu1                          amd64        Extended attribute shared library
ii  libaudio-scrobbler-perl                   0.01-2.1                                   all          perl interface to audioscrobbler.com/last.fm
ii  libaudio2:amd64                           1.9.3-5                                    amd64        Network Audio System - shared libraries
ii  libaudit0                                 1.7.18-1ubuntu1                            amd64        Dynamic library for security auditing
ii  libav-tools                               6:0.8.3-6ubuntu2                           amd64        Multimedia player, server, encoder and transcoder
ii  libavahi-cil-dev                          0.6.19-4.2                                 all          CLI bindings for Avahi
ii  libavahi-client-dev                       0.6.31-1ubuntu2                            amd64        Development files for the Avahi client library
ii  libavahi-client3:amd64                    0.6.31-1ubuntu2                            amd64        Avahi client library
ii  libavahi-common-data:amd64                0.6.31-1ubuntu2                            amd64        Avahi common data files
ii  libavahi-common-dev                       0.6.31-1ubuntu2                            amd64        Development files for the Avahi common library
ii  libavahi-common3:amd64                    0.6.31-1ubuntu2                            amd64        Avahi common library
ii  libavahi-compat-libdnssd-dev              0.6.31-1ubuntu2                            amd64        Development headers for the Avahi Apple Bonjour compatibility library
ii  libavahi-compat-libdnssd1:amd64           0.6.31-1ubuntu2                            amd64        Avahi Apple Bonjour compatibility library
ii  libavahi-core-dev                         0.6.31-1ubuntu2                            amd64        Development files for Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-core7:amd64                      0.6.31-1ubuntu2                            amd64        Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-glib-dev                         0.6.31-1ubuntu2                            amd64        Development headers for the Avahi GLib integration library
ii  libavahi-glib1:amd64                      0.6.31-1ubuntu2                            amd64        Avahi GLib integration library
ii  libavahi-gobject-dev                      0.6.31-1ubuntu2                            amd64        Development headers for the Avahi GObject library
ii  libavahi-gobject0:amd64                   0.6.31-1ubuntu2                            amd64        Avahi GObject library
ii  libavahi-qt4-1:amd64                      0.6.31-1ubuntu2                            amd64        Avahi Qt 4 integration library
ii  libavahi-qt4-dev                          0.6.31-1ubuntu2                            amd64        Development headers for the Avahi Qt 4 integration library
ii  libavahi-ui-cil-dev                       0.6.19-4.2                                 all          CLI bindings for Avahi Ui
ii  libavahi-ui-dev                           0.6.31-1ubuntu2                            amd64        Development headers for the Avahi GTK+ User interface library
ii  libavahi-ui-gtk3-0:amd64                  0.6.31-1ubuntu2                            amd64        Avahi GTK+ User interface library for GTK3
ii  libavahi-ui0:amd64                        0.6.31-1ubuntu2                            amd64        Avahi GTK+ User interface library
ii  libavahi-ui0.0-cil                        0.6.19-4.2                                 all          CLI bindings for Avahi Ui
ii  libavahi1.0-cil                           0.6.19-4.2                                 all          CLI bindings for Avahi
ii  libavc1394-0:amd64                        0.5.4-1                                    amd64        control IEEE 1394 audio/video devices
ii  libavcodec53:amd64                        6:0.8.3-6ubuntu2                           amd64        Libav codec library
ii  libavdevice53:amd64                       6:0.8.3-6ubuntu2                           amd64        Libav device handling library
ii  libavfilter2:amd64                        6:0.8.3-6ubuntu2                           amd64        Libav video filtering library
ii  libavformat53:amd64                       6:0.8.3-6ubuntu2                           amd64        Libav file format library
ii  libavutil51:amd64                         6:0.8.3-6ubuntu2                           amd64        Libav utility library
ii  libbabl-0.0-0                             0.0.22-1.1                                 amd64        Dynamic, any to any, pixel format conversion library
ii  libbabl-0.1-0:amd64                       0.1.10-1ubuntu1                            amd64        Dynamic, any to any, pixel format conversion library
ii  libbamf3-0:amd64                          0.3.2-0ubuntu1                             amd64        Window matching library - shared library
ii  libbind9-60                               1:9.7.3.dfsg-1ubuntu4.1                    amd64        BIND9 Shared Library used by BIND
ii  libbind9-80                               1:9.8.1.dfsg.P1-4.2ubuntu3                 amd64        BIND9 Shared Library used by BIND
ii  libbison-dev:amd64                        1:2.5.dfsg-2.1build1                       amd64        YACC-compatible parser generator - development library
ii  libblas3                                  1.2.20110419-5                             amd64        Basic Linear Algebra Reference implementations, shared library
ii  libblas3gf                                1.2.20110419-5                             all          Transitional package for libblas
ii  libblkid1:amd64                           2.20.1-5.1ubuntu2                          amd64        block device id library
ii  libbluetooth3:amd64                       4.101-0ubuntu6                             amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libbonobo2-0:amd64                        2.32.1-0ubuntu2                            amd64        Bonobo CORBA interfaces library
ii  libbonobo2-common                         2.32.1-0ubuntu2                            all          Bonobo CORBA interfaces library -- support files
ii  libbonoboui2-0:amd64                      2.24.5-0ubuntu2                            amd64        The Bonobo UI library
ii  libbonoboui2-common                       2.24.5-0ubuntu2                            all          The Bonobo UI library -- common files
ii  libboost-iostreams1.49.0                  1.49.0-3.1ubuntu1                          amd64        Boost.Iostreams Library
ii  libbrasero-media3-1                       3.4.1-0ubuntu2                             amd64        CD/DVD burning library for GNOME - runtime
ii  libbrlapi0.5:amd64                        4.4-5ubuntu3                               amd64        braille display access via BRLTTY - shared library
ii  libbsd0:amd64                             0.4.2-1                                    amd64        utility functions from BSD systems - shared library
ii  libburn4                                  1.2.4-0ubuntu1                             amd64        library to provide CD/DVD writing functions
ii  libbz2-1.0:amd64                          1.0.6-4                                    amd64        high-quality block-sorting file compressor library - runtime
ii  libc-bin                                  2.15-0ubuntu20                             amd64        Embedded GNU C Library: Binaries
ii  libc-dev-bin                              2.15-0ubuntu20                             amd64        Embedded GNU C Library: Development binaries
ii  libc6:amd64                               2.15-0ubuntu20                             amd64        Embedded GNU C Library: Shared libraries
ii  libc6-dev:amd64                           2.15-0ubuntu20                             amd64        Embedded GNU C Library: Development Libraries and Header Files
ii  libcaca0:amd64                            0.99.beta18-1                              amd64        colour ASCII art library
ii  libcairo-gobject2:amd64                   1.12.2-1ubuntu2                            amd64        The Cairo 2D vector graphics library (GObject library)
ii  libcairo-perl                             1.100-0ubuntu1                             amd64        Perl interface to the Cairo graphics library
ii  libcairo-script-interpreter2:amd64        1.12.2-1ubuntu2                            amd64        The Cairo 2D vector graphics library (script interpreter)
ii  libcairo2:amd64                           1.12.2-1ubuntu2                            amd64        The Cairo 2D vector graphics library
ii  libcairo2-dev                             1.12.2-1ubuntu2                            amd64        Development files for the Cairo 2D graphics library
ii  libcamel-1.2-40                           3.6.0-0ubuntu2                             amd64        Evolution MIME message handling library
ii  libcanberra-gtk-module:amd64              0.29-0ubuntu2                              amd64        translates GTK+ widgets signals to event sounds
ii  libcanberra-gtk0:amd64                    0.29-0ubuntu2                              amd64        GTK+ helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-0:amd64                  0.29-0ubuntu2                              amd64        GTK+ 3.0 helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-module:amd64             0.29-0ubuntu2                              amd64        translates GTK3 widgets signals to event sounds
ii  libcanberra-pulse:amd64                   0.29-0ubuntu2                              amd64        PulseAudio backend for libcanberra
ii  libcanberra0:amd64                        0.29-0ubuntu2                              amd64        simple abstract interface for playing event sounds
ii  libcap-ng0                                0.6.6-2ubuntu1                             amd64        An alternate POSIX capabilities library
ii  libcap2:amd64                             1:2.22-1ubuntu4                            amd64        support for getting/setting POSIX.1e capabilities
ii  libcap2-bin                               1:2.22-1ubuntu4                            amd64        basic utility programs for using capabilities
ii  libcdaudio1                               0.99.12p2-12                               amd64        library for controlling a CD-ROM when playing audio CDs
ii  libcdio-cdda0                             0.81-4build1                               amd64        library to read and control digital audio CDs
ii  libcdio-cdda1                             0.83-4                                     amd64        library to read and control digital audio CDs
ii  libcdio-paranoia0                         0.81-4build1                               amd64        library to read digital audio CDs with error correction
ii  libcdio-paranoia1                         0.83-4                                     amd64        library to read digital audio CDs with error correction
ii  libcdio10                                 0.81-4build1                               amd64        library to read and control CD-ROM
ii  libcdio13                                 0.83-4                                     amd64        library to read and control CD-ROM
ii  libcdparanoia0:amd64                      3.10.2+debian-11                           amd64        audio extraction tool for sampling CDs (library)
ii  libcherokee-base0                         1.2.101-1                                  amd64        Cherokee web server - Base libraries
ii  libcherokee-server0                       1.2.101-1                                  amd64        Cherokee web server - Server libraries
ii  libck-connector0:amd64                    0.4.5-3                                    amd64        ConsoleKit libraries
ii  libclass-accessor-perl                    0.34-1                                     all          Perl module that automatically generates accessors
ii  libclass-factory-util-perl                1.7-2                                      all          Utility method for factory classes
ii  libclass-isa-perl                         0.36-3                                     all          report the search path for a class's ISA tree
ii  libclass-load-perl                        0.17-1                                     all          module for loading modules by name
ii  libclass-singleton-perl                   1.4-1                                      all          implementation of a "Singleton" class
ii  libclone-perl                             0.31-1build4                               amd64        recursively copy Perl datatypes
ii  libcloog-ppl0:amd64                       0.15.11-4build1                            amd64        Chunky Loop Generator (runtime library)
ii  libclutter-1.0-0:amd64                    1.12.0-0ubuntu1                            amd64        Open GL based interactive canvas library
ii  libclutter-1.0-common                     1.12.0-0ubuntu1                            all          Open GL based interactive canvas library (common files)
ii  libclutter-gtk-0.10-0                     0.10.8-1ubuntu1                            amd64        Open GL based interactive canvas library GTK+ widget
ii  libclutter-gtk-1.0-0:amd64                1.3.2-0ubuntu1                             amd64        Open GL based interactive canvas library GTK+ widget
ii  libcogl-common                            1.10.4-0ubuntu1                            all          Object oriented GL/GLES Abstraction/Utility Layer (common files)
ii  libcogl-pango0:amd64                      1.10.4-0ubuntu1                            amd64        Object oriented GL/GLES Abstraction/Utility Layer
ii  libcogl9:amd64                            1.10.4-0ubuntu1                            amd64        Object oriented GL/GLES Abstraction/Utility Layer
ii  libcolamd2.7.1                            1:3.4.0-2ubuntu3                           amd64        column approximate minimum degree ordering library for sparse matrices
ii  libcolord1:amd64                          0.1.21-1ubuntu2                            amd64        system service to manage device colour profiles -- runtime
ii  libcomerr2:amd64                          1.42.5-1ubuntu2                            amd64        common error description library
ii  libcompizconfig0                          1:0.9.8.4-0ubuntu2                         amd64        Settings library for plugins - OpenCompositing Project
ii  libconfig-inifiles-perl                   2.75-1                                     all          Read .ini-style configuration files
ii  libcrack2                                 2.8.19-1                                   amd64        pro-active password checker library
ii  libcrack2-dev                             2.8.19-1                                   amd64        pro-active password checker library - development files
ii  libcroco3:amd64                           0.6.6-1                                    amd64        Cascading Style Sheet (CSS) parsing and manipulation toolkit
ii  libcrypt-passwdmd5-perl                   1.3-10                                     all          interoperable MD5-based crypt() for perl
ii  libcups2:amd64                            1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - Core library
ii  libcupscgi1:amd64                         1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - CGI library
ii  libcupsdriver1:amd64                      1.5.3-0ubuntu4                             amd64        Common UNIX Printing System(tm) - Driver library
ii  libcupsfilters1:amd64                     1.0.24-2                                   amd64        OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64                       1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1:amd64                        1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:amd64                        1.6.1-0ubuntu11                            amd64        Common UNIX Printing System(tm) - PPD manipulation library
ii  libcurl3:amd64                            7.27.0-1ubuntu1                            amd64        easy-to-use client-side URL transfer library (OpenSSL flavour)
ii  libcurl3-gnutls:amd64                     7.27.0-1ubuntu1                            amd64        easy-to-use client-side URL transfer library (GnuTLS flavour)
ii  libcurl3-nss:amd64                        7.27.0-1ubuntu1                            amd64        easy-to-use client-side URL transfer library (NSS flavour)
ii  libcurses-perl                            1.28-1build2                               amd64        Curses interface for Perl
ii  libcurses-ui-perl                         0.9609-1                                   all          curses-based OO user interface framework for Perl
ii  libcwidget3                               0.5.16-3.4ubuntu1                          amd64        high-level terminal interface library for C++ (runtime files)
ii  libdaemon0                                0.14-2build1                               amd64        lightweight C library for daemons - runtime library
ii  libdata-optlist-perl                      0.107-1                                    all          module to parse and validate simple name/value option pairs
ii  libdatetime-format-builder-perl           0.8000-1                                   all          module to create DateTime parsers
ii  libdatetime-format-iso8601-perl           0.08-1                                     all          module to parse ISO8601 date and time formats
ii  libdatetime-format-strptime-perl          1.5000-1                                   all          Perl module to parse and format strp and strf time patterns
ii  libdatetime-locale-perl                   1:0.45-1                                   all          Perl extension providing localization support for DateTime
ii  libdatetime-perl                          2:0.7500-1                                 amd64        module for manipulating dates, times and timestamps
ii  libdatetime-timezone-perl                 1:1.46-1+2012c                             all          framework exposing the Olson time zone database to Perl
ii  libdatrie1:amd64                          0.2.5-3build1                              amd64        Double-array trie library
ii  libdb4.8:amd64                            4.8.30-11ubuntu1                           amd64        Berkeley v4.8 Database Libraries [runtime]
ii  libdb4.8-dev                              4.8.30-11ubuntu1                           amd64        Berkeley v4.8 Database Libraries [development]
ii  libdb5.1:amd64                            5.1.29-5ubuntu2                            amd64        Berkeley v5.1 Database Libraries [runtime]
ii  libdbus-1-3:amd64                         1.6.4-1ubuntu4                             amd64        simple interprocess messaging system (library)
ii  libdbus-1-dev                             1.6.4-1ubuntu4                             amd64        simple interprocess messaging system (development headers)
ii  libdbus-glib-1-2:amd64                    0.100-1                                    amd64        simple interprocess messaging system (GLib-based shared library)
ii  libdbusmenu-glib4:amd64                   12.10.2-0ubuntu1                           amd64        library for passing menus over DBus
ii  libdbusmenu-gtk3-4:amd64                  12.10.2-0ubuntu1                           amd64        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-gtk4:amd64                    12.10.2-0ubuntu1                           amd64        library for passing menus over DBus - GTK+ version
ii  libdbusmenu-qt2:amd64                     0.9.2-0ubuntu3                             amd64        Qt implementation of the DBusMenu protocol
ii  libdc1394-22:amd64                        2.2.0-2build1                              amd64        high level programming interface for IEEE1394 digital camera
ii  libdca0                                   0.0.5-5                                    amd64        decoding library for DTS Coherent Acoustics streams
ii  libdconf1:amd64                           0.14.0-0ubuntu2                            amd64        simple configuration storage system - runtime library
ii  libdecoration0                            1:0.9.8.4-0ubuntu2                         amd64        Compiz window decoration library
ii  libdee-1.0-1                              0.5.22-0ubuntu1                            amd64        model to synchronize mutiple instances over DBus - shared lib
ii  libdee-1.0-4                              1.0.14-0ubuntu1                            amd64        model to synchronize mutiple instances over DBus - shared lib
ii  libdevmapper-event1.02.1:amd64            2:1.02.74-4ubuntu1                         amd64        Linux Kernel Device Mapper event support library
ii  libdevmapper1.02.1:amd64                  2:1.02.74-4ubuntu1                         amd64        Linux Kernel Device Mapper userspace library
ii  libdigest-hmac-perl                       1.03+dfsg-1                                all          module for creating standard message integrity checks
ii  libdirac-encoder0:amd64                   1.0.2-6                                    amd64        open and royalty free high quality video codec - encoder library
ii  libdirectfb-1.2-9:amd64                   1.2.10.0-5                                 amd64        direct frame buffer graphics - shared libraries
ii  libdiscid0:amd64                          0.2.2-3build1                              amd64        Library for creating MusicBrainz DiscIDs
ii  libdjvulibre-text                         3.5.25.3-1ubuntu1                          all          Linguistic support files for libdjvulibre
ii  libdjvulibre21                            3.5.25.3-1ubuntu1                          amd64        Runtime support for the DjVu image format
ii  libdmapsharing-3.0-2                      2.9.15-1                                   amd64        DMAP client and server library - runtime
ii  libdns69                                  1:9.7.3.dfsg-1ubuntu4.1                    amd64        DNS Shared Library used by BIND
ii  libdns81                                  1:9.8.1.dfsg.P1-4.2ubuntu3                 amd64        DNS Shared Library used by BIND
ii  libdotconf1.0                             1.0.13-3build1                             amd64        Configuration file parser library - runtime files
ii  libdpkg-perl                              1.16.7ubuntu6                              all          Dpkg perl modules
ii  libdrm-dev                                2.4.39-0ubuntu1                            amd64        Userspace interface to kernel DRM services -- development files
ii  libdrm-intel1:amd64                       2.4.39-0ubuntu1                            amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a:amd64                    2.4.39-0ubuntu1                            amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:amd64                     2.4.39-0ubuntu1                            amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:amd64                      2.4.39-0ubuntu1                            amd64        Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2:amd64                             2.4.39-0ubuntu1                            amd64        Userspace interface to kernel DRM services -- runtime
ii  libdv4:amd64                              1.0.0-4                                    amd64        software library for DV format digital video (runtime lib)
ii  libdvdnav4                                4.2.0+20120524-2                           amd64        DVD navigation library
ii  libdvdread4                               4.2.0+20120521-2ubuntu1                    amd64        library for reading DVDs
ii  libebackend-1.2-5                         3.6.0-0ubuntu2                             amd64        Utility library for evolution data servers
ii  libebook-1.2-14                           3.6.0-0ubuntu2                             amd64        Client library for evolution address books
ii  libecal-1.2-15                            3.6.0-0ubuntu2                             amd64        Client library for evolution calendars
ii  libedata-book-1.2-15                      3.6.0-0ubuntu2                             amd64        Backend library for evolution address books
ii  libedata-cal-1.2-18                       3.6.0-0ubuntu2                             amd64        Backend library for evolution calendars
ii  libedataserver-1.2-17                     3.6.0-0ubuntu2                             amd64        Utility library for evolution data servers
ii  libedit2:amd64                            2.11-20080614-5                            amd64        BSD editline and history libraries
ii  libelf1:amd64                             0.153-1ubuntu1                             amd64        library to read and write ELF files
ii  libelfg0                                  0.8.13-3build1                             amd64        an ELF object file access library
ii  libemail-valid-perl                       0.190-1                                    all          Perl module for checking the validity of Internet email addresses
ii  libenca0                                  1.13-4build1                               amd64        Extremely Naive Charset Analyser - shared library files
ii  libenchant1c2a                            1.6.0-7build1                              amd64        Wrapper library for various spell checker engines (runtime libs)
ii  libencode-locale-perl                     1.03-1                                     all          utility to determine the locale encoding
ii  libept1                                   1.0.5build1                                amd64        High-level library for managing Debian package information
ii  libept1.4.12                              1.0.9                                      amd64        High-level library for managing Debian package information
ii  liberror-perl                             0.17-1                                     all          Perl module for error/exception handling in an OO-ish way
ii  libespeak1:amd64                          1.46.02-2ubuntu1                           amd64        Multi-lingual software speech synthesizer: shared library
ii  libevent-1.4-2                            1.4.14b-stable-0ubuntu1                    amd64        asynchronous event notification library
ii  libevent-2.0-5:amd64                      2.0.19-stable-3                            amd64        Asynchronous event notification library
ii  libexif12:amd64                           0.6.20-3                                   amd64        library to parse EXIF files
ii  libexiv2-12                               0.23-1                                     amd64        EXIF/IPTC metadata manipulation library
ii  libexo-1-0:amd64                          0.8.0-1                                    amd64        Library with extensions for Xfce
ii  libexo-common                             0.8.0-1                                    all          libexo common files
ii  libexo-helpers                            0.8.0-1                                    amd64        libexo helpers
ii  libexpat1:amd64                           2.1.0-1ubuntu1                             amd64        XML parsing C library - runtime library
ii  libexpat1-dev                             2.1.0-1ubuntu1                             amd64        XML parsing C library - development kit
ii  libfaad2:amd64                            2.7-8                                      amd64        freeware Advanced Audio Decoder - runtime files
ii  libfarstream-0.1-0:amd64                  0.1.2-1ubuntu1                             amd64        Audio/Video communications framework: core library
ii  libffi6:amd64                             3.0.11-2                                   amd64        Foreign Function Interface library runtime
ii  libfftw3-3:amd64                          3.3.2-3.1ubuntu1                           amd64        Library for computing Fast Fourier Transforms
ii  libfile-basedir-perl                      0.03-1fakesync1                            all          Perl module to use the freedesktop basedir specification
ii  libfile-copy-recursive-perl               0.38-1                                     all          Perl extension for recursively copying files and directories
ii  libfile-desktopentry-perl                 0.04-3                                     all          Perl module to handle freedesktop .desktop files
ii  libfile-fcntllock-perl                    0.14-2                                     amd64        Perl module for file locking with fcntl(2)
ii  libfile-listing-perl                      6.04-1                                     all          module to parse directory listings
ii  libfile-mimeinfo-perl                     0.16-1                                     all          Perl module to determine file types
ii  libfl-dev:amd64                           2.5.35-10.1ubuntu1                         amd64        static library for flex (a fast lexical analyzer generator).
ii  libflac8:amd64                            1.2.1-6build1                              amd64        Free Lossless Audio Codec - runtime C library
ii  libflite1:amd64                           1.4-release-6                              amd64        Small run-time speech synthesis engine - shared libraries
ii  libfont-afm-perl                          1.20-1                                     all          Font::AFM - Interface to Adobe Font Metrics files
ii  libfontconfig1:amd64                      2.10.1-0ubuntu3                            amd64        generic font configuration library - runtime
ii  libfontconfig1-dev                        2.10.1-0ubuntu3                            amd64        generic font configuration library - development
ii  libfontembed1:amd64                       1.0.24-2                                   amd64        OpenPrinting CUPS Filters - Font Embed Shared library
ii  libfontenc1:amd64                         1:1.1.1-1                                  amd64        X11 font encoding library
ii  libframe6:amd64                           2.2.4-0ubuntu1                             amd64        Touch Frame Library
ii  libfreerdp-plugins-standard               1.0.1-1ubuntu7                             amd64        RDP client for Windows Terminal Services (plugins)
ii  libfreerdp1                               1.0.1-1ubuntu7                             amd64        RDP client for Windows Terminal Services (library)
ii  libfreetype6:amd64                        2.4.10-0ubuntu1                            amd64        FreeType 2 font engine, shared library files
ii  libfreetype6-dev                          2.4.10-0ubuntu1                            amd64        FreeType 2 font engine, development files
ii  libfreezethaw-perl                        0.5001-1                                   all          module to serialize and deserialize Perl data structures
ii  libfribidi0:amd64                         0.19.2-3                                   amd64        Free Implementation of the Unicode BiDi algorithm
ii  libfs6:amd64                              2:1.0.4-1                                  amd64        X11 Font Services library
ii  libfuse2:amd64                            2.9.0-1ubuntu2                             amd64        Filesystem in Userspace (library)
ii  libgadu3                                  1:1.11.2-1                                 amd64        Gadu-Gadu protocol library - runtime files
ii  libgail-3-0:amd64                         3.6.0-0ubuntu3                             amd64        GNOME Accessibility Implementation Library -- shared libraries
ii  libgail18:amd64                           2.24.13-0ubuntu2                           amd64        GNOME Accessibility Implementation Library -- shared libraries
ii  libgamin0                                 0.1.10-4ubuntu1                            amd64        Client library for the gamin file and directory monitoring system
ii  libgarcon-1-0                             0.2.0-1                                    amd64        freedesktop.org compliant menu implementation for Xfce
ii  libgarcon-common                          0.2.0-1                                    all          common files for libgarcon menu implementation
ii  libgcc1:amd64                             1:4.7.2-2ubuntu1                           amd64        GCC support library
ii  libgck-1-0                                3.6.0-0ubuntu1                             amd64        Glib wrapper library for PKCS#11 - runtime
ii  libgconf-2-4:amd64                        3.2.5-0ubuntu4                             amd64        GNOME configuration database system (shared libraries)
ii  libgconf2-4:amd64                         3.2.5-0ubuntu4                             amd64        GNOME configuration database system (dummy package)
ii  libgcr-3-1                                3.6.0-0ubuntu1                             amd64        Library for Crypto UI related task - runtime
ii  libgcr-3-common                           3.6.0-0ubuntu1                             all          Library for Crypto UI related task - common files
ii  libgcrypt11:amd64                         1.5.0-3ubuntu1                             amd64        LGPL Crypto library - runtime library
ii  libgcrypt11-dev                           1.5.0-3ubuntu1                             amd64        LGPL Crypto library - development files
ii  libgd2-xpm:amd64                          2.0.36~rc1~dfsg-6ubuntu3                   amd64        GD Graphics Library version 2
ii  libgdata-common                           0.13.2-0ubuntu1                            all          Library for accessing GData webservices - common data files
ii  libgdata13                                0.13.2-0ubuntu1                            amd64        Library for accessing GData webservices - shared libraries
ii  libgdbm3:amd64                            1.8.3-11                                   amd64        GNU dbm database routines (runtime version)
ii  libgdiplus                                2.10-3ubuntu1                              amd64        interface library for System.Drawing of Mono
ii  libgdk-pixbuf2.0-0:amd64                  2.26.4-0ubuntu1                            amd64        GDK Pixbuf library
ii  libgdk-pixbuf2.0-common                   2.26.4-0ubuntu1                            all          GDK Pixbuf library - data files
ii  libgdk-pixbuf2.0-dev                      2.26.4-0ubuntu1                            amd64        GDK Pixbuf library (development files)
ii  libgdome2-0                               0.8.1+debian-4.1build1                     amd64        DOM level2 library for accessing XML files
ii  libgdome2-cpp-smart0c2a                   0.2.6-6build2                              amd64        C++ bindings for GDome2 DOM implementation
ii  libgdu0:amd64                             3.0.2-2ubuntu7                             amd64        GObject based Disk Utility Library
ii  libgee2:amd64                             0.6.4-2                                    amd64        GObject based collection library
ii  libgegl-0.0-0                             0.0.22-2ubuntu3                            amd64        Generic Graphics Library
ii  libgegl-0.2-0:amd64                       0.2.0-1ubuntu2                             amd64        Generic Graphics Library
ii  libgeis1:amd64                            2.2.12-0ubuntu2                            amd64        Gesture engine interface support
ii  libgeoclue0                               0.12.99-0ubuntu2                           amd64        C API for GeoClue
ii  libgeoip1:amd64                           1.4.8+dfsg-4                               amd64        non-DNS IP-to-country resolver library
ii  libgettextpo0:amd64                       0.18.1.1-9ubuntu1                          amd64        GNU Internationalization library
ii  libgif4:amd64                             4.1.6-9.1ubuntu1                           amd64        library for GIF images (library)
ii  libgimp2.0                                2.8.2-1ubuntu1                             amd64        Libraries for the GNU Image Manipulation Program
ii  libgirepository-1.0-1                     1.33.14-1                                  amd64        Library for handling GObject introspection data (runtime library)
ii  libgksu2-0                                2.0.13~pre1-5ubuntu3                       amd64        library providing su and sudo functionality
ii  libgl1-mesa-dev                           9.0-0ubuntu1                               amd64        free implementation of the OpenGL API -- GLX development files
ii  libgl1-mesa-dri:amd64                     9.0-0ubuntu1                               amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                     9.0-0ubuntu1                               amd64        free implementation of the OpenGL API -- GLX runtime
ii  libglade2-0:amd64                         1:2.6.4-1ubuntu2                           amd64        library to load .glade files at runtime
ii  libglapi-mesa:amd64                       9.0-0ubuntu1                               amd64        free implementation of the GL API -- shared library
ii  libglew1.8:amd64                          1.8.0-1ubuntu2                             amd64        OpenGL Extension Wrangler - runtime environment
ii  libglewmx1.8:amd64                        1.8.0-1ubuntu2                             amd64        OpenGL Extension Wrangler (Multiple Rendering Contexts)
ii  libglib-perl                              3:1.261-1                                  amd64        interface to the GLib and GObject libraries
ii  libglib2.0-0:amd64                        2.34.0-1ubuntu1                            amd64        GLib library of C routines
ii  libglib2.0-bin                            2.34.0-1ubuntu1                            amd64        Programs for the GLib library
ii  libglib2.0-cil                            2.12.10-4                                  amd64        CLI binding for the GLib utility library 2.12
ii  libglib2.0-cil-dev                        2.12.10-4                                  amd64        CLI binding for the GLib utility library 2.12
ii  libglib2.0-data                           2.34.0-1ubuntu1                            all          Common files for GLib library
ii  libglib2.0-dev                            2.34.0-1ubuntu1                            amd64        Development files for the GLib library
ii  libglibmm-2.4-1c2a:amd64                  2.33.13-0ubuntu2                           amd64        C++ wrapper for the GLib toolkit (shared libraries)
ii  libglu1-mesa:amd64                        9.0.0-0ubuntu1                             amd64        Mesa OpenGL utility library (GLU)
ii  libglu1-mesa-dev                          9.0.0-0ubuntu1                             amd64        Mesa OpenGL utility library -- development files
ii  libgme0                                   0.5.5-2                                    amd64        Playback library for video game music files - shared library
ii  libgmime-2.6-0                            2.6.10-1                                   amd64        MIME message parser and creator library - runtime
ii  libgmp10:amd64                            2:5.0.2+dfsg-2ubuntu2                      amd64        Multiprecision arithmetic library
ii  libgmp3c2                                 2:4.3.2+dfsg-2ubuntu1                      amd64        Multiprecision arithmetic library
ii  libgmpxx4ldbl:amd64                       2:5.0.2+dfsg-2ubuntu2                      amd64        Multiprecision arithmetic library (C++ bindings)
ii  libgnome-bluetooth11                      3.6.0-0ubuntu1                             amd64        GNOME Bluetooth tools - support library
ii  libgnome-bluetooth8                       3.2.2-0ubuntu5                             amd64        GNOME Bluetooth tools - support library
ii  libgnome-control-center1                  1:3.4.2-0ubuntu19                          amd64        utilities to configure the GNOME desktop
ii  libgnome-desktop-2-17                     1:2.32.1-2ubuntu1                          amd64        Utility library for loading .desktop files - runtime files
ii  libgnome-desktop-3-4                      3.6.0.1-0ubuntu2                           amd64        Utility library for loading .desktop files - runtime files
ii  libgnome-keyring-common                   3.6.0-0ubuntu1                             all          GNOME keyring services library - data files
ii  libgnome-keyring0:amd64                   3.6.0-0ubuntu1                             amd64        GNOME keyring services library
ii  libgnome-menu-3-0                         3.6.0-0ubuntu1                             amd64        GNOME implementation of the freedesktop menu specification
ii  libgnome-menu2                            3.0.1-0ubuntu8                             amd64        GNOME implementation of the freedesktop menu specification
ii  libgnome2-0:amd64                         2.32.1-2ubuntu3                            amd64        The GNOME library - runtime files
ii  libgnome2-bin                             2.32.1-2ubuntu3                            amd64        The GNOME library - binary files
ii  libgnome2-common                          2.32.1-2ubuntu3                            all          The GNOME library - common files
ii  libgnomecanvas2-0:amd64                   2.30.3-1ubuntu2                            amd64        powerful object-oriented display engine - runtime files
ii  libgnomecanvas2-common                    2.30.3-1ubuntu2                            all          powerful object-oriented display engine - common files
ii  libgnomekbd-common                        3.6.0-0ubuntu1                             all          GNOME library to manage keyboard configuration - common files
ii  libgnomekbd8                              3.6.0-0ubuntu1                             amd64        GNOME library to manage keyboard configuration - shared library
ii  libgnomeui-0:amd64                        2.24.5-2ubuntu3                            amd64        GNOME user interface library - runtime files
ii  libgnomeui-common                         2.24.5-2ubuntu3                            all          GNOME user interface library - common files
ii  libgnomevfs2-0:amd64                      1:2.24.4-1ubuntu3                          amd64        GNOME Virtual File System (runtime libraries)
ii  libgnomevfs2-common                       1:2.24.4-1ubuntu3                          amd64        GNOME Virtual File System (common files)
ii  libgnomevfs2-extra:amd64                  1:2.24.4-1ubuntu3                          amd64        GNOME Virtual File System (extra modules)
ii  libgnutls26:amd64                         2.12.14-5ubuntu4                           amd64        GNU TLS library - runtime library
ii  libgoa-1.0-0:amd64                        3.6.0-0ubuntu1                             amd64        library for GNOME Online Accounts
ii  libgoa-1.0-common                         3.6.0-0ubuntu1                             all          library for GNOME Online Accounts - common files
ii  libgoffice-0.8-8                          0.8.17-1.2ubuntu1                          amd64        Document centric objects library - runtime files
ii  libgoffice-0.8-8-common                   0.8.17-1.2ubuntu1                          all          Document centric objects library - common files
ii  libgomp1:amd64                            4.7.2-2ubuntu1                             amd64        GCC OpenMP (GOMP) support library
ii  libgpg-error-dev                          1.10-3.1ubuntu1                            amd64        library for common error values and messages in GnuPG components (development)
ii  libgpg-error0:amd64                       1.10-3.1ubuntu1                            amd64        library for common error values and messages in GnuPG components
ii  libgpgme11                                1.2.0-1.4ubuntu3                           amd64        GPGME - GnuPG Made Easy
ii  libgphoto2-2:amd64                        2.4.14-2                                   amd64        gphoto2 digital camera library
ii  libgphoto2-l10n                           2.4.14-2                                   all          gphoto2 digital camera library - localized messages
ii  libgphoto2-port0:amd64                    2.4.14-2                                   amd64        gphoto2 digital camera port library
ii  libgpm2:amd64                             1.20.4-6                                   amd64        General Purpose Mouse - shared library
ii  libgpod-common                            0.8.2-6build1                              amd64        common files for libgpod
ii  libgpod4:amd64                            0.8.2-6build1                              amd64        library to read and write songs and artwork to an iPod
ii  libgrail5                                 3.0.6-0ubuntu1                             amd64        Gesture Recognition And Instantiation Library
ii  libgs9                                    9.06~dfsg-0ubuntu4                         amd64        interpreter for the PostScript language and for PDF - Library
ii  libgs9-common                             9.06~dfsg-0ubuntu4                         all          interpreter for the PostScript language and for PDF - common files
ii  libgsasl7                                 1.8.0-2                                    amd64        GNU SASL library
ii  libgsf-1-114                              1.14.24-0ubuntu1                           amd64        Structured File Library - runtime version
ii  libgsf-1-common                           1.14.24-0ubuntu1                           all          Structured File Library - common files
ii  libgsm1:amd64                             1.0.13-4                                   amd64        Shared libraries for GSM speech compressor
ii  libgssapi-krb5-2:amd64                    1.10.1+dfsg-2                              amd64        MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
ii  libgssapi3-heimdal:amd64                  1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - GSSAPI support library
ii  libgssdp-1.0-2                            0.10.0-2                                   amd64        GObject-based library for SSDP
ii  libgssdp-1.0-3                            0.12.2.1-1ubuntu1                          amd64        GObject-based library for SSDP
ii  libgstreamer-perl                         0.17-1                                     amd64        Perl interface to the GStreamer media processing framework
ii  libgstreamer-plugins-bad0.10-0:amd64      0.10.23-7ubuntu1                           amd64        GStreamer shared libraries from the "bad" set
ii  libgstreamer-plugins-base0.10-0:amd64     0.10.36-1ubuntu1                           amd64        GStreamer libraries from the "base" set
ii  libgstreamer0.10-0:amd64                  0.10.36-1ubuntu2                           amd64        Core GStreamer libraries and elements
ii  libgtk-3-0:amd64                          3.6.0-0ubuntu3                             amd64        GTK+ graphical user interface library
ii  libgtk-3-bin                              3.6.0-0ubuntu3                             amd64        programs for the GTK+ graphical user interface library
ii  libgtk-3-common                           3.6.0-0ubuntu3                             all          common files for the GTK+ graphical user interface library
ii  libgtk-vnc-1.0-0                          0.5.1-1ubuntu2                             amd64        VNC viewer widget for GTK+2 (runtime libraries)
ii  libgtk-vnc-2.0-0                          0.5.1-1ubuntu2                             amd64        VNC viewer widget for GTK+3 (runtime libraries)
ii  libgtk2-notify-perl                       0.05-3build1                               amd64        Perl interface to libnotify
ii  libgtk2-perl                              2:1.244-1ubuntu1                           amd64        Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2-trayicon-perl                     0.06-1build2                               amd64        Perl interface to fill the system tray
ii  libgtk2.0-0:amd64                         2.24.13-0ubuntu2                           amd64        GTK+ graphical user interface library
ii  libgtk2.0-bin                             2.24.13-0ubuntu2                           amd64        programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                             2.12.10-4                                  amd64        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-cil-dev                         2.12.10-4                                  amd64        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                          2.24.13-0ubuntu2                           all          common files for the GTK+ graphical user interface library
ii  libgtk2.0-dev                             2.24.13-0ubuntu2                           amd64        development files for the GTK+ library
ii  libgtkmathview0c2a                        0.8.0-8                                    amd64        rendering engine for MathML documents
ii  libgtkspell0                              2.0.16-1ubuntu6                            amd64        a spell-checking addon for GTK's TextView widget
ii  libgtop2-7                                2.28.4-3                                   amd64        gtop system monitoring library (shared)
ii  libgtop2-common                           2.28.4-3                                   all          gtop system monitoring library (common)
ii  libgucharmap-2-90-7                       1:3.5.99-0ubuntu1                          amd64        Unicode browser widget library (shared library)
ii  libgucharmap7                             1:3.2.0-0ubuntu1                           amd64        Unicode browser widget library (shared library for GTK+ 2)
ii  libgudev-1.0-0:amd64                      1:175-0ubuntu13                            amd64        GObject-based wrapper library for libudev
ii  libgupnp-1.0-3                            0.16.1-1                                   amd64        GObject-based library for UPnP
ii  libgupnp-1.0-4                            0.18.4-0ubuntu1                            amd64        GObject-based library for UPnP
ii  libgupnp-igd-1.0-3                        0.1.11-1                                   amd64        library to handle UPnP IGD port mapping
ii  libgupnp-igd-1.0-4:amd64                  0.2.1-2build1                              amd64        library to handle UPnP IGD port mapping
ii  libgusb2                                  0.1.3-5                                    amd64        GLib wrapper around libusb1
ii  libgutenprint2                            5.2.9-1ubuntu1                             amd64        runtime for the Gutenprint printer driver library
ii  libgvnc-1.0-0                             0.5.1-1ubuntu2                             amd64        VNC gobject wrapper (runtime libraries)
ii  libgweather-3-1                           3.6.0-0ubuntu1                             amd64        GWeather shared library
ii  libgweather-common                        3.6.0-0ubuntu1                             all          GWeather common files
ii  libhcrypto4-heimdal:amd64                 1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - crypto library
ii  libheimbase1-heimdal:amd64                1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - Base library
ii  libheimntlm0-heimdal:amd64                1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - NTLM support library
ii  libhpmud0                                 3.12.6-3ubuntu4                            amd64        HP Multi-Point Transport Driver (hpmud) run-time libraries
ii  libhtml-form-perl                         6.03-1                                     all          module that represents an HTML form element
ii  libhtml-format-perl                       2.10-1                                     all          module for transforming HTML into various formats
ii  libhtml-parser-perl                       3.69-2                                     amd64        collection of modules that parse HTML text documents
ii  libhtml-tagset-perl                       3.20-2                                     all          Data tables pertaining to HTML
ii  libhtml-tree-perl                         5.02-1                                     all          Perl module to represent and create HTML syntax trees
ii  libhttp-cookies-perl                      6.00-2                                     all          HTTP cookie jars
ii  libhttp-daemon-perl                       6.01-1                                     all          simple http server class
ii  libhttp-date-perl                         6.02-1                                     all          module of date conversion routines
ii  libhttp-message-perl                      6.03-1                                     all          perl interface to HTTP style messages
ii  libhttp-negotiate-perl                    6.00-2                                     all          implementation of content negotiation
ii  libhunspell-1.2-0                         1.2.14-4                                   amd64        spell checker and morphological analyzer (shared library)
ii  libhunspell-1.3-0:amd64                   1.3.2-4build1                              amd64        spell checker and morphological analyzer (shared library)
ii  libhx509-5-heimdal:amd64                  1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - X509 support library
ii  libibus-1.0-0:amd64                       1.4.1-7ubuntu1                             amd64        Intelligent Input Bus - shared library
ii  libical0                                  0.48-2                                     amd64        iCalendar library implementation in C (runtime)
ii  libice-dev:amd64                          2:1.0.8-2                                  amd64        X11 Inter-Client Exchange library (development headers)
ii  libice6:amd64                             2:1.0.8-2                                  amd64        X11 Inter-Client Exchange library
ii  libicu44                                  4.4.2-2ubuntu0.11.10.1                     amd64        International Components for Unicode
ii  libicu48:amd64                            4.8.1.1-8                                  amd64        International Components for Unicode
ii  libid3tag0                                0.15.1b-10build3                           amd64        ID3 tag reading library from the MAD project
ii  libidl-common                             0.8.14-0.2ubuntu3                          all          library for parsing CORBA IDL files (common files)
ii  libidl0:amd64                             0.8.14-0.2ubuntu3                          amd64        library for parsing CORBA IDL files
ii  libidn11:amd64                            1.25-2                                     amd64        GNU Libidn library, implementation of IETF IDN specifications
ii  libido-0.1-0:amd64                        12.10.0.1-0ubuntu1                         amd64        Shared library providing extra gtk menu items for display in
ii  libido3-0.1-0:amd64                       12.10.2-0ubuntu1                           amd64        Shared library providing extra gtk menu items for display in
ii  libiec61883-0:amd64                       1.2.0-0.1ubuntu2                           amd64        an partial implementation of IEC 61883
ii  libieee1284-3:amd64                       0.2.11-10build2                            amd64        cross-platform library for parallel port access
ii  libijs-0.35                               0.35-8build1                               amd64        IJS raster image transport protocol: shared library
ii  libilmbase6                               1.0.1-4                                    amd64        several utility libraries from ILM used by OpenEXR
ii  libimobiledevice2                         1.1.1-4                                    amd64        Library for communicating with the iPhone and iPod Touch
ii  libimobiledevice3                         1.1.4-1ubuntu2                             amd64        Library for communicating with the iPhone and iPod Touch
ii  libindicate-gtk3                          12.10.1-0ubuntu1                           amd64        library for raising indicators via DBus - GTK+ bindings
ii  libindicate5                              12.10.1-0ubuntu1                           amd64        library for raising indicators via DBus
ii  libindicator3-7                           12.10.1-0ubuntu1                           amd64        panel indicator applet - shared library
ii  libindicator7                             12.10.1-0ubuntu1                           amd64        panel indicator applet - shared library
ii  libio-pty-perl                            1:1.08-1build3                             amd64        Perl module for pseudo tty IO
ii  libio-socket-inet6-perl                   2.69-2                                     all          object interface for AF_INET6 domain sockets
ii  libio-socket-ssl-perl                     1.76-1ubuntu1                              all          Perl module implementing object oriented interface to SSL sockets
ii  libio-string-perl                         1.08-2                                     all          Emulate IO::File interface for in-core strings
ii  libipc-run-perl                           0.91-1                                     all          Perl module for running processes
ii  libisc62                                  1:9.7.3.dfsg-1ubuntu4.1                    amd64        ISC Shared Library used by BIND
ii  libisc83                                  1:9.8.1.dfsg.P1-4.2ubuntu3                 amd64        ISC Shared Library used by BIND
ii  libisccc60                                1:9.7.3.dfsg-1ubuntu4.1                    amd64        Command Channel Library used by BIND
ii  libisccc80                                1:9.8.1.dfsg.P1-4.2ubuntu3                 amd64        Command Channel Library used by BIND
ii  libisccfg62                               1:9.7.3.dfsg-1ubuntu4.1                    amd64        Config File Handling Library used by BIND
ii  libisccfg82                               1:9.8.1.dfsg.P1-4.2ubuntu3                 amd64        Config File Handling Library used by BIND
ii  libisofs6                                 1.2.4-0ubuntu1                             amd64        library to create ISO9660 images
ii  libitm1:amd64                             4.7.2-2ubuntu1                             amd64        GNU Transactional Memory Library
ii  libiw30:amd64                             30~pre9-8ubuntu1                           amd64        Wireless tools - library
ii  libjack-jackd2-0:amd64                    1.9.8~dfsg.4+20120529git007cdc37-2ubuntu1  amd64        JACK Audio Connection Kit (libraries)
ii  libjasper1:amd64                          1.900.1-13build1                           amd64        JasPer JPEG-2000 runtime library
ii  libjavascriptcoregtk-1.0-0                1.10.0-0ubuntu1                            amd64        Javascript engine library for GTK+
ii  libjavascriptcoregtk-3.0-0                1.10.0-0ubuntu1                            amd64        Javascript engine library for GTK+
ii  libjbig0:amd64                            2.0-2ubuntu1                               amd64        JBIGkit libraries
ii  libjbig2dec0                              0.11-1ubuntu2                              amd64        JBIG2 decoder library - shared libraries
ii  libjpeg-progs                             8c-2ubuntu7                                amd64        Programs for manipulating JPEG files (dependency package)
ii  libjpeg-turbo-progs                       1.2.1-0ubuntu2                             amd64        Programs for manipulating JPEG files
ii  libjpeg-turbo8:amd64                      1.2.1-0ubuntu2                             amd64        IJG JPEG compliant runtime library.
ii  libjpeg62:amd64                           6b1-2ubuntu2                               amd64        Independent JPEG Group's JPEG runtime library (version 6.2)
ii  libjpeg8:amd64                            8c-2ubuntu7                                amd64        Independent JPEG Group's JPEG runtime library (dependency package)
ii  libjs-jquery                              1.7.2+debian-1ubuntu1                      all          JavaScript library for dynamic web applications
ii  libjson-glib-1.0-0:amd64                  0.15.2-0ubuntu1                            amd64        GLib JSON manipulation library
ii  libjson0:amd64                            0.10-1ubuntu1                              amd64        JSON manipulation library - shared library
ii  libjte1                                   1.19-1build1                               amd64        Jigdo Template Export - runtime library
ii  libk5crypto3:amd64                        1.10.1+dfsg-2                              amd64        MIT Kerberos runtime libraries - Crypto Library
ii  libkate1                                  0.4.1-1                                    amd64        Kate is a codec for karaoke and text encapsulation
ii  libkeybinder0                             0.2.2-4                                    amd64        registers global key bindings for applications
ii  libkeyutils1:amd64                        1.5.5-3                                    amd64        Linux Key Management Utilities (library)
ii  libklibc                                  2.0.1-1ubuntu2                             amd64        minimal libc subset for use with initramfs
ii  libkms1:amd64                             2.4.39-0ubuntu1                            amd64        Userspace interface to kernel DRM buffer management
ii  libkpathsea5                              2009-11ubuntu2                             amd64        TeX Live: path search library for TeX (runtime part)
ii  libkrb5-26-heimdal:amd64                  1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - libraries
ii  libkrb5-3:amd64                           1.10.1+dfsg-2                              amd64        MIT Kerberos runtime libraries
ii  libkrb5support0:amd64                     1.10.1+dfsg-2                              amd64        MIT Kerberos runtime libraries - Support library
ii  liblaunchpad-integration-common           0.1.56.2                                   all          library for launchpad integration common data
ii  liblaunchpad-integration1                 0.1.56.2                                   amd64        library for launchpad integration
ii  liblcms1:amd64                            1.19.dfsg-1.1ubuntu2                       amd64        Little CMS color management library
ii  liblcms2-2:amd64                          2.2+git20110628-2ubuntu4                   amd64        Little CMS 2 color management library
ii  libldap-2.4-2:amd64                       2.4.31-1ubuntu2                            amd64        OpenLDAP libraries
ii  liblightdm-gobject-1-0                    1.4.0-0ubuntu2                             amd64        LightDM GObject client library
ii  liblink-grammar4                          4.7.4-2                                    amd64        Carnegie Mellon University's link grammar parser (libraries)
ii  liblist-moreutils-perl                    0.33-1build2                               amd64        Perl module with additional list functions not found in List::Util
ii  libllvm3.1:amd64                          3.1-2ubuntu1                               amd64        Low-Level Virtual Machine (LLVM), runtime library
ii  liblocale-gettext-perl                    1.05-7build2                               amd64        module using libc functions for internationalization in Perl
ii  liblockfile-bin                           1.09-4                                     amd64        support binaries for and cli utilities based on liblockfile
ii  liblockfile1:amd64                        1.09-4                                     amd64        NFS-safe locking library
ii  libloudmouth1-0                           1.4.3-8                                    amd64        Lightweight C Jabber library
ii  libltdl7:amd64                            2.4.2-1ubuntu2                             amd64        A system independent dlopen wrapper for GNU libtool
ii  liblua5.1-0:amd64                         5.1.5-4                                    amd64        Shared library for the Lua interpreter version 5.1
ii  liblvm2app2.2:amd64                       2.02.95-4ubuntu1                           amd64        LVM2 application library
ii  liblwp-mediatypes-perl                    6.02-1                                     all          module to guess media type for a file or a URL
ii  liblwp-protocol-https-perl                6.03-1                                     all          HTTPS driver for LWP::UserAgent
ii  liblwres60                                1:9.7.3.dfsg-1ubuntu4.1                    amd64        Lightweight Resolver Library used by BIND
ii  liblwres80                                1:9.8.1.dfsg.P1-4.2ubuntu3                 amd64        Lightweight Resolver Library used by BIND
ii  liblzma2                                  5.0.0-2                                    amd64        XZ-format compression library
ii  liblzma5:amd64                            5.1.1alpha+20120614-1                      amd64        XZ-format compression library
ii  libmad0:amd64                             0.15.1b-7ubuntu1                           amd64        MPEG audio decoder library
ii  libmagic1:amd64                           5.11-2                                     amd64        File type determination library using "magic" numbers
ii  libmail-sendmail-perl                     0.79.16-1                                  all          Send email from a perl script
ii  libmailtools-perl                         2.09-1                                     all          Manipulate email in perl programs
ii  libmailutils4                             1:2.99.97-3                                amd64        GNU Mail abstraction library
ii  libmath-round-perl                        0.06-3                                     all          Perl extension for rounding numbers
ii  libmeanwhile1                             1.0.2-4ubuntu2                             amd64        open implementation of the Lotus Sametime Community Client protocol
ii  libmediainfo0:amd64                       0.7.59-1                                   amd64        library for reading metadata from media files -- shared library
ii  libmessaging-menu0                        12.10.4-0ubuntu1                           amd64        Messaging Menu - shared library
ii  libmetacity-private0a                     1:2.34.8-0ubuntu4                          amd64        library for the Metacity window manager
ii  libmhash2                                 0.9.9.9-1.1                                amd64        Library for cryptographic hashing and message authentication
ii  libmimic0                                 1.0.4-2.1build1                            amd64        A video codec for Mimic V2.x content
ii  libminiupnpc8                             1.6-3ubuntu2                               amd64        UPnP IGD client lightweight library
ii  libmldbm-perl                             2.04-1                                     all          module for storing multidimensional hash structures in perl tied hashes
ii  libmms0:amd64                             0.6.2-3                                    amd64        MMS stream protocol library - shared library
ii  libmng1:amd64                             1.0.10-3build1                             amd64        Multiple-image Network Graphics library
ii  libmodplug1                               1:0.8.8.4-3                                amd64        shared libraries for mod music based on ModPlug
ii  libmodule-implementation-perl             0.06-1                                     all          module for loading one of several alternate implementations of a module
ii  libmodule-runtime-perl                    0.013-1                                    all          Perl module for runtime module handling
ii  libmono-cairo4.0-cil                      2.10.8.1-5ubuntu1                          all          Mono Cairo library (for CLI 4.0)
ii  libmono-corlib4.0-cil                     2.10.8.1-5ubuntu1                          all          Mono core library (for CLI 4.0)
ii  libmono-i18n-west4.0-cil                  2.10.8.1-5ubuntu1                          all          Mono I18N.West library (for CLI 4.0)
ii  libmono-i18n4.0-cil                       2.10.8.1-5ubuntu1                          all          Mono I18N base library (for CLI 4.0)
ii  libmono-posix4.0-cil                      2.10.8.1-5ubuntu1                          all          Mono.Posix library (for CLI 4.0)
ii  libmono-security4.0-cil                   2.10.8.1-5ubuntu1                          all          Mono Security library (for CLI 4.0)
ii  libmono-system-configuration4.0-cil       2.10.8.1-5ubuntu1                          all          Mono System.Configuration library (for CLI 4.0)
ii  libmono-system-drawing4.0-cil             2.10.8.1-5ubuntu1                          all          Mono System.Drawing library (for CLI 4.0)
ii  libmono-system-security4.0-cil            2.10.8.1-5ubuntu1                          all          Mono System.Security library (for CLI 4.0)
ii  libmono-system-xml4.0-cil                 2.10.8.1-5ubuntu1                          all          Mono System.Xml library (for CLI 4.0)
ii  libmono-system4.0-cil                     2.10.8.1-5ubuntu1                          all          Mono System libraries (for CLI 4.0)
ii  libmount1:amd64                           2.20.1-5.1ubuntu2                          amd64        block device id library
ii  libmpc2:amd64                             0.9-4build1                                amd64        multiple precision complex floating-point library
ii  libmpcdec6                                2:0.1~r459-1ubuntu1                        amd64        MusePack decoder - library
ii  libmpfr4:amd64                            3.1.0-3ubuntu3                             amd64        multiple precision floating-point computation
ii  libmtdev1:amd64                           1.1.2-1ubuntu1                             amd64        Multitouch Protocol Translation Library - shared library
ii  libmtp-common                             1.1.4-1                                    all          Media Transfer Protocol (MTP) common files
ii  libmtp-runtime                            1.1.4-1                                    amd64        Media Transfer Protocol (MTP) runtime tools
ii  libmtp9:amd64                             1.1.4-1                                    amd64        Media Transfer Protocol (MTP) library
ii  libmusicbrainz5-0:amd64                   5.0.1-2                                    amd64        Library to access the MusicBrainz.org database
ii  libmysqlclient18:amd64                    5.5.27-0ubuntu2                            amd64        MySQL database client library
ii  libnatpmp1                                20110808-3ubuntu2                          amd64        portable and fully compliant implementation of NAT-PMP
ii  libnautilus-extension1                    1:3.2.1-0ubuntu4.2                         amd64        libraries for nautilus components - runtime version
ii  libnautilus-extension1a                   1:3.5.90.really.3.4.2-0ubuntu4             amd64        libraries for nautilus components - runtime version
ii  libncurses5:amd64                         5.9-10ubuntu1                              amd64        shared libraries for terminal handling
ii  libncursesw5:amd64                        5.9-10ubuntu1                              amd64        shared libraries for terminal handling (wide character support)
ii  libneon27-gnutls                          0.29.6-3                                   amd64        HTTP and WebDAV client library (GnuTLS enabled)
ii  libnet-dbus-perl                          1.0.0-1build1                              amd64        Extension for the DBus bindings
ii  libnet-dns-perl                           0.68-1.1                                   amd64        Perform DNS queries from a Perl script
ii  libnet-domain-tld-perl                    1.69-1                                     all          Perl module for retrieving a list of currently available TLDs
ii  libnet-http-perl                          6.03-2                                     all          module providing low-level HTTP connection client
ii  libnet-ip-perl                            1.25-3                                     all          Perl extension for manipulating IPv4/IPv6 addresses
ii  libnet-ssleay-perl                        1.48-1                                     amd64        Perl module for Secure Sockets Layer (SSL)
ii  libnetfilter-conntrack3:amd64             1.0.1-1                                    amd64        Netfilter netlink-conntrack library
ii  libnettle4:amd64                          2.4-2                                      amd64        low level cryptographic library (symmetric and one-way cryptos)
ii  libnewt0.52                               0.52.11-2ubuntu11                          amd64        Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libnfnetlink0                             1.0.0-1build1                              amd64        Netfilter netlink library
ii  libnice10:amd64                           0.1.2-1                                    amd64        ICE library (shared library)
ii  libnih-dbus1:amd64                        1.0.3-4ubuntu11                            amd64        NIH D-Bus Bindings Library
ii  libnih1:amd64                             1.0.3-4ubuntu11                            amd64        NIH Utility Library
ii  libnl-3-200:amd64                         3.2.7-4                                    amd64        library for dealing with netlink sockets
ii  libnl-genl-3-200:amd64                    3.2.7-4                                    amd64        library for dealing with netlink sockets - generic netlink
ii  libnl-route-3-200:amd64                   3.2.7-4                                    amd64        library for dealing with netlink sockets - route interface
ii  libnl1:amd64                              1.1-7                                      amd64        library for dealing with netlink sockets
ii  libnm-glib-vpn1                           0.9.6.0-0ubuntu7                           amd64        network management framework (GLib VPN shared library)
ii  libnm-glib4                               0.9.6.0-0ubuntu7                           amd64        network management framework (GLib shared library)
ii  libnm-gtk-common                          0.9.6.2-0ubuntu6                           all          network management framework (common files for wifi and mobile)
ii  libnm-gtk0                                0.9.6.2-0ubuntu6                           amd64        network management framework (GNOME dialogs for wifi and mobile)
ii  libnm-util2                               0.9.6.0-0ubuntu7                           amd64        network management framework (shared library)
ii  libnotify-bin                             0.7.5-1build1                              amd64        sends desktop notifications to a notification daemon (Utilities)
ii  libnotify4:amd64                          0.7.5-1build1                              amd64        sends desktop notifications to a notification daemon
ii  libnspr4:amd64                            4.8.9-1ubuntu3                             amd64        NetScape Portable Runtime Library
ii  libnss-mdns                               0.10-3.2build1                             amd64        NSS module for Multicast DNS name resolution
ii  libnss3:amd64                             3.13.1.with.ckbi.1.88-1ubuntu7             amd64        Network Security Service libraries
ii  libnss3-1d:amd64                          3.13.1.with.ckbi.1.88-1ubuntu7             amd64        Network Security Service libraries
ii  libntfs10                                 2.0.0-1ubuntu4                             amd64        library that provides common NTFS access functions
ii  libntlm0                                  1.2-1                                      amd64        NTLM authentication library
ii  libnuma1                                  2.0.8~rc4-1                                amd64        Libraries for controlling NUMA policy
ii  libnux-3.0-0                              3.8.0-0ubuntu1                             amd64        Visual rendering toolkit for real-time applications - shared lib
ii  libnux-3.0-common                         3.8.0-0ubuntu1                             all          Visual rendering toolkit for real-time applications - common files
ii  liboauth0:amd64                           0.9.7-0ubuntu1                             amd64        C library for implementing OAuth 1.0
ii  libofa0                                   0.9.3-5                                    amd64        Library for acoustic fingerprinting
ii  libogg0:amd64                             1.3.0-4                                    amd64        Ogg bitstream library
ii  liboobs-1-5                               3.0.0-1                                    amd64        GObject based interface to system-tools-backends - shared library
ii  libopenal-data                            1:1.14-4ubuntu1                            all          Software implementation of the OpenAL API (data files)
ii  libopenal1:amd64                          1:1.14-4ubuntu1                            amd64        Software implementation of the OpenAL API (shared library)
ii  libopencc1:amd64                          0.3.0-3                                    amd64        simplified-traditional chinese conversion library - runtime
ii  libopenexr6                               1.6.1-6                                    amd64        runtime files for the OpenEXR image library
ii  libopenjpeg2:amd64                        1.3+dfsg-4.5ubuntu1                        amd64        JPEG 2000 image compression/decompression library
ii  libopenobex1                              1.5-2build2                                amd64        OBEX protocol library
ii  libopts25                                 1:5.12-0.1ubuntu2                          amd64        automated option processing library based on autogen
ii  libopus0                                  1.0.1-0ubuntu1                             amd64        Opus codec runtime library
ii  liborbit2:amd64                           1:2.14.19-0.1ubuntu1                       amd64        libraries for ORBit2 - a CORBA ORB
ii  liborc-0.4-0:amd64                        1:0.4.16-2                                 amd64        Library of Optimized Inner Loops Runtime Compiler
ii  libotr2                                   3.2.1-1                                    amd64        Off-the-Record Messaging library
ii  libots0                                   0.5.0-2.1                                  amd64        Open Text Summarizer (library)
ii  libp11-kit0:amd64                         0.13-1                                     amd64        Library for loading and coordinating access to PKCS#11 modules - runtime
ii  libpackage-deprecationmanager-perl        0.13-1                                     all          module for managing deprecation warnings for Perl distributions
ii  libpackage-stash-perl                     0.33-1                                     all          module providing routines for manipulating stashes
ii  libpackage-stash-xs-perl                  0.24-1build2                               amd64        Perl module providing routines for manipulating stashes (XS version)
ii  libpackagekit-glib2-14:amd64              0.7.6-1                                    amd64        Library for accessing PackageKit using GLib
ii  libpam-ck-connector:amd64                 0.4.5-3                                    amd64        ConsoleKit PAM module
ii  libpam-gnome-keyring                      3.6.0-0ubuntu1                             amd64        PAM module to unlock the GNOME keyring upon login
ii  libpam-modules:amd64                      1.1.3-7ubuntu3                             amd64        Pluggable Authentication Modules for PAM
ii  libpam-modules-bin                        1.1.3-7ubuntu3                             amd64        Pluggable Authentication Modules for PAM - helper binaries
ii  libpam-runtime                            1.1.3-7ubuntu3                             all          Runtime support for the PAM library
ii  libpam0g:amd64                            1.1.3-7ubuntu3                             amd64        Pluggable Authentication Modules library
ii  libpango-perl                             1.223-0ubuntu1                             amd64        Perl module to layout and render international text
ii  libpango1.0-0:amd64                       1.30.1-0ubuntu3                            amd64        Layout and rendering of internationalized text
ii  libpango1.0-dev                           1.30.1-0ubuntu3                            amd64        Development files for the Pango
ii  libpaper-utils                            1.1.24+nmu2                                amd64        library for handling paper characteristics (utilities)
ii  libpaper1:amd64                           1.1.24+nmu2                                amd64        library for handling paper characteristics
ii  libparams-classify-perl                   0.013-4build1                              amd64        Perl module for argument type classification
ii  libparams-util-perl                       1.07-1                                     amd64        Perl extension for simple stand-alone param checking functions
ii  libparams-validate-perl                   1.06-1                                     amd64        Perl module to validate parameters to Perl method/function calls
ii  libparse-debianchangelog-perl             1.2.0-1ubuntu1                             all          parse Debian changelogs and output them in other formats
ii  libparted0debian1:amd64                   2.3-10ubuntu2                              amd64        disk partition manipulator - shared library
ii  libpcap0.8:amd64                          1.3.0-1                                    amd64        system interface for user-level packet capture
ii  libpci3:amd64                             1:3.1.9-5ubuntu4                           amd64        Linux PCI Utilities (shared library)
ii  libpciaccess0:amd64                       0.13.1-2                                   amd64        Generic PCI access library for X
ii  libpcre3:amd64                            1:8.30-5ubuntu1                            amd64        Perl 5 Compatible Regular Expression Library - runtime files
ii  libpcre3-dev                              1:8.30-5ubuntu1                            amd64        Perl 5 Compatible Regular Expression Library - development files
ii  libpcrecpp0:amd64                         1:8.30-5ubuntu1                            amd64        Perl 5 Compatible Regular Expression Library - C++ runtime files
ii  libpcsclite1:amd64                        1.8.5-1ubuntu1                             amd64        Middleware to access a smart card using PC/SC (library)
ii  libpeas-1.0-0                             1.4.0-2ubuntu3                             amd64        Application plugin library
ii  libpeas-common                            1.4.0-2ubuntu3                             all          Application plugin library (common files)
ii  libperl5.14                               5.14.2-13                                  amd64        shared Perl library
ii  libpipeline1:amd64                        1.2.2-1                                    amd64        pipeline manipulation library
ii  libpixman-1-0:amd64                       0.26.0-3                                   amd64        pixel-manipulation library for X and cairo
ii  libpixman-1-dev                           0.26.0-3                                   amd64        pixel-manipulation library for X and cairo (development files)
ii  libplist1                                 1.8-2                                      amd64        Library for handling Apple binary and XML property lists
ii  libplymouth2                              0.8.4-0ubuntu3                             amd64        graphical boot animation and logger - shared libraries
ii  libpng12-0:amd64                          1.2.49-1ubuntu1                            amd64        PNG library - runtime
ii  libpng12-dev                              1.2.49-1ubuntu1                            amd64        PNG library - development
ii  libpod-plainer-perl                       1.03-1                                     all          Perl extension for converting Pod to old-style Pod.
ii  libpolkit-agent-1-0:amd64                 0.104-2ubuntu1                             amd64        PolicyKit Authentication Agent API
ii  libpolkit-backend-1-0:amd64               0.104-2ubuntu1                             amd64        PolicyKit backend API
ii  libpolkit-gobject-1-0:amd64               0.104-2ubuntu1                             amd64        PolicyKit Authorization API
ii  libpolkit-gtk-1-0                         0.102-1ubuntu1                             amd64        PolicyKit GTK+ API
ii  libpoppler-glib6                          0.16.7-2ubuntu2                            amd64        PDF rendering library (GLib-based shared library)
ii  libpoppler-glib8:amd64                    0.20.4-0ubuntu1                            amd64        PDF rendering library (GLib-based shared library)
ii  libpoppler13                              0.16.7-2ubuntu2                            amd64        PDF rendering library
ii  libpoppler28:amd64                        0.20.4-0ubuntu1                            amd64        PDF rendering library
ii  libpopt0:amd64                            1.16-7ubuntu2                              amd64        lib for parsing cmdline parameters
ii  libportaudio2:amd64                       19+svn20111121-1build1                     amd64        Portable audio I/O - shared library
ii  libpostproc52:amd64                       6:0.8.3-6ubuntu2                           amd64        Libav video postprocessing library
ii  libppl-c4:amd64                           0.11.2-8ubuntu1                            amd64        Parma Polyhedra Library (C interface)
ii  libppl9:amd64                             0.11.2-8ubuntu1                            amd64        Parma Polyhedra Library (runtime library)
ii  libprocps0:amd64                          1:3.3.3-2ubuntu3                           amd64        library for accessing process information from /proc
ii  libprotobuf7                              2.4.1-3ubuntu1                             amd64        protocol buffers C++ library
ii  libproxy0                                 0.3.1-2ubuntu6                             amd64        automatic proxy configuration management library (shared)
ii  libproxy1:amd64                           0.4.7-0ubuntu6                             amd64        automatic proxy configuration management library (shared)
ii  libpth20                                  2.0.7-16ubuntu4                            amd64        The GNU Portable Threads
ii  libpthread-stubs0:amd64                   0.3-3                                      amd64        pthread stubs not provided by native libc
ii  libpthread-stubs0-dev:amd64               0.3-3                                      amd64        pthread stubs not provided by native libc, development files
ii  libpulse-mainloop-glib0:amd64             1:2.1-0ubuntu4                             amd64        PulseAudio client libraries (glib support)
ii  libpulse0:amd64                           1:2.1-0ubuntu4                             amd64        PulseAudio client libraries
ii  libpulsedsp:amd64                         1:2.1-0ubuntu4                             amd64        PulseAudio OSS pre-load library
ii  libpurple-bin                             1:2.10.6-0ubuntu2                          all          multi-protocol instant messaging library - extra utilities
ii  libpurple0                                1:2.10.6-0ubuntu2                          amd64        multi-protocol instant messaging library
ii  libpwl5:amd64                             0.11.2-8ubuntu1                            amd64        Parma Watchdog Library (Watchdog timers - runtime library)
ii  libpython2.7                              2.7.3-5ubuntu4                             amd64        Shared Python runtime library (version 2.7)
ii  libpython3.2                              3.2.3-6ubuntu3                             amd64        Shared Python runtime library (version 3.2)
ii  libqjson0:amd64                           0.7.1-6build1                              amd64        Qt-based library that maps JSON data to QVariant objects
ii  libqpdf8:amd64                            3.0.2-1                                    amd64        runtime library for PDF transformation/inspection software
ii  libqt4-dbus:amd64                         4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 D-Bus module
ii  libqt4-declarative:amd64                  4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 Declarative module
ii  libqt4-designer:amd64                     4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 designer module
ii  libqt4-dev                                4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 development files
ii  libqt4-dev-bin                            4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 development programs
ii  libqt4-help:amd64                         4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 help module
ii  libqt4-network:amd64                      4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 network module
ii  libqt4-opengl:amd64                       4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 OpenGL module
ii  libqt4-opengl-dev                         4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 OpenGL library development files
ii  libqt4-qt3support:amd64                   4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 3 compatibility library for Qt 4
ii  libqt4-script:amd64                       4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 script module
ii  libqt4-scripttools:amd64                  4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 script tools module
ii  libqt4-sql:amd64                          4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 SQL module
ii  libqt4-sql-mysql:amd64                    4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 MySQL database driver
ii  libqt4-sql-sqlite:amd64                   4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 SQLite 3 database driver
ii  libqt4-svg:amd64                          4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 SVG module
ii  libqt4-test:amd64                         4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 test module
ii  libqt4-xml:amd64                          4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 XML module
ii  libqt4-xmlpatterns:amd64                  4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 XML patterns module
ii  libqtcore4:amd64                          4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 core module
ii  libqtgui4:amd64                           4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 GUI module
ii  libqtwebkit-dev                           2.2.1-4ubuntu1                             amd64        Web content engine library for Qt - development files
ii  libqtwebkit4:amd64                        2.2.1-4ubuntu1                             amd64        Web content engine library for Qt
ii  libquadmath0:amd64                        4.7.2-2ubuntu1                             amd64        GCC Quad-Precision Math Library
ii  libquvi-scripts                           0.4.8-3                                    all          library for parsing video download links (Lua scripts)
ii  libquvi7:amd64                            0.4.1-1                                    amd64        library for parsing video download links (runtime libraries)
ii  libraptor2-0                              2.0.8-1                                    amd64        Raptor 2 RDF syntax library
ii  librarian0                                0.8.1-5build1                              amd64        Documentation meta-data library (library package)
ii  librasqal3                                0.9.29-1                                   amd64        Rasqal RDF query library
ii  libraw1394-11:amd64                       2.0.9-1                                    amd64        library for direct access to IEEE 1394 bus (aka FireWire)
ii  librdf0                                   1.0.15-1                                   amd64        Redland Resource Description Framework (RDF) library
ii  libreadline5:amd64                        5.2-12                                     amd64        GNU readline and history libraries, run-time libraries
ii  libreadline6:amd64                        6.2-9                                      amd64        GNU readline and history libraries, run-time libraries
ii  librest-0.7-0:amd64                       0.7.90-0ubuntu1                            amd64        REST service access library
ii  librhythmbox-core6                        2.97-1ubuntu5                              amd64        support library for the rhythmbox music player
ii  libroken18-heimdal:amd64                  1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - roken support library
ii  librpc-xml-perl                           0.76-3                                     all          Perl implementation of the XML-RPC protocol
ii  librsvg2-2:amd64                          2.36.3-0ubuntu1                            amd64        SAX-based renderer library for SVG files (runtime)
ii  librsvg2-common:amd64                     2.36.3-0ubuntu1                            amd64        SAX-based renderer library for SVG files (extra runtime)
ii  librtmp0:amd64                            2.4+20111222.git4e06e21-1                  amd64        toolkit for RTMP streams (shared library)
ii  libsamplerate0:amd64                      0.1.8-5                                    amd64        Audio sample rate conversion library
ii  libsane:amd64                             1.0.23-0ubuntu1                            amd64        API library for scanners
ii  libsane-common                            1.0.23-0ubuntu1                            amd64        API library for scanners -- documentation and support files
ii  libsane-hpaio                             3.12.6-3ubuntu4                            amd64        HP SANE backend for multi-function peripherals
ii  libsasl2-2:amd64                          2.1.25.dfsg1-5                             amd64        Cyrus SASL - authentication abstraction library
ii  libsasl2-modules:amd64                    2.1.25.dfsg1-5                             amd64        Cyrus SASL - pluggable authentication modules
ii  libschroedinger-1.0-0:amd64               1.0.11-2                                   amd64        library for encoding/decoding of Dirac video streams
ii  libsdl1.2debian:amd64                     1.2.15-5ubuntu1                            amd64        Simple DirectMedia Layer
ii  libsecret-1-0                             0.10-0ubuntu1                              amd64        Secret store
ii  libsecret-common                          0.10-0ubuntu1                              all          Secret store (common files)
ii  libselinux1:amd64                         2.1.9-5ubuntu1                             amd64        SELinux runtime shared libraries
ii  libsensors4:amd64                         1:3.3.1-2ubuntu2                           amd64        library to read temperature/voltage/fan sensors
ii  libsepol1:amd64                           2.1.4-3ubuntu2                             amd64        SELinux library for manipulating binary security policies
ii  libsexy2                                  0.1.11-2build3                             amd64        collection of additional GTK+ widgets - library
ii  libsgutils2-2                             1.33-1build1                               amd64        utilities for devices using the SCSI command set (shared libraries)
ii  libshout3:amd64                           2.3.1-1ubuntu2                             amd64        MP3/Ogg Vorbis broadcast streaming library
ii  libsigc++-2.0-0c2a:amd64                  2.2.10-0.2                                 amd64        type-safe Signal Framework for C++ - runtime
ii  libsignon-extension1                      8.43-0ubuntu1                              amd64        Single Sign On framework
ii  libsignon-glib1                           1.6-0ubuntu1                               amd64        library for signond
ii  libsignon-plugins-common1                 8.43-0ubuntu1                              amd64        Single Sign On framework
ii  libsignon-qt1                             8.43-0ubuntu1                              amd64        Single Sign On framework
ii  libsilc-1.1-2                             1.1.10-2build1                             amd64        SILC generic library
ii  libsilcclient-1.1-3                       1.1.10-2build1                             amd64        SILC client library
ii  libslang2:amd64                           2.2.4-15ubuntu1                            amd64        S-Lang programming library - runtime version
ii  libslp1                                   1.2.1-9                                    amd64        OpenSLP libraries
ii  libslv2-9                                 0.6.6+dfsg1-2                              amd64        library for simple use of LV2 plugins
ii  libsm-dev:amd64                           2:1.2.1-2                                  amd64        X11 Session Management library (development headers)
ii  libsm6:amd64                              2:1.2.1-2                                  amd64        X11 Session Management library
ii  libsmbclient:amd64                        2:3.6.6-3ubuntu5                           amd64        shared library for communication with SMB/CIFS servers
ii  libsndfile1:amd64                         1.0.25-5                                   amd64        Library for reading/writing audio files
ii  libsnmp-base                              5.4.3~dfsg-2.5ubuntu1                      all          SNMP (Simple Network Management Protocol) MIBs and documentation
ii  libsnmp15                                 5.4.3~dfsg-2.5ubuntu1                      amd64        SNMP (Simple Network Management Protocol) library
ii  libsocket6-perl                           0.23-1build3                               amd64        Perl extensions for IPv6
ii  libsonic0:amd64                           0.1.17-1.1build1                           amd64        Simple library to speed up or slow down speech
ii  libsoundtouch0:amd64                      1.6.0-3                                    amd64        Sound stretching library
ii  libsoup-gnome2.4-1:amd64                  2.40.0-0ubuntu1                            amd64        HTTP library implementation in C -- GNOME support library
ii  libsoup2.4-1:amd64                        2.40.0-0ubuntu1                            amd64        HTTP library implementation in C -- Shared library
ii  libspandsp2                               0.0.6~pre20-3ubuntu1                       amd64        Telephony signal processing library
ii  libspectre1:amd64                         0.2.7-2                                    amd64        Library for rendering PostScript documents
ii  libspeechd2:amd64                         0.7.1-6.1ubuntu2                           amd64        Speech Dispatcher: Shared libraries
ii  libspeex1:amd64                           1.2~rc1-6                                  amd64        The Speex codec runtime library
ii  libspeexdsp1:amd64                        1.2~rc1-6                                  amd64        The Speex extended runtime library
ii  libsqlite3-0:amd64                        3.7.13-1                                   amd64        SQLite 3 shared library
ii  libss2:amd64                              1.42.5-1ubuntu2                            amd64        command-line interface parsing library
ii  libssl-dev                                1.0.1c-3ubuntu2                            amd64        SSL development libraries, header files and documentation
ii  libssl-doc                                1.0.1c-3ubuntu2                            all          SSL development documentation documentation
ii  libssl0.9.8:amd64                         0.9.8o-7ubuntu3.1                          amd64        SSL shared libraries
ii  libssl1.0.0:amd64                         1.0.1c-3ubuntu2                            amd64        SSL shared libraries
ii  libstartup-notification0:amd64            0.12-1ubuntu2                              amd64        library for program launch feedback (shared library)
ii  libstdc++6:amd64                          4.7.2-2ubuntu1                             amd64        GNU Standard C++ Library v3
ii  libstdc++6-4.5-dev                        4.5.4-1ubuntu2                             amd64        GNU Standard C++ Library v3 (development files)
ii  libstdc++6-4.7-dev                        4.7.2-2ubuntu1                             amd64        GNU Standard C++ Library v3 (development files)
ii  libsub-install-perl                       0.926-1                                    all          module for installing subroutines into packages easily
ii  libsub-name-perl                          0.05-1build3                               amd64        module for assigning a new name to referenced sub
ii  libswitch-perl                            2.16-2                                     all          switch statement for Perl
ii  libswscale2:amd64                         6:0.8.3-6ubuntu2                           amd64        Libav video scaling library
ii  libsync-menu1:amd64                       12.10.4-0ubuntu1                           amd64        indicator for synchronisation processes status - libraries
ii  libsyncdaemon-1.0-1                       4.0.0-0ubuntu1                             amd64        Ubuntu One synchronization daemon library
ii  libsys-hostname-long-perl                 1.4-2                                      all          Figure out the long (fully-qualified) hostname
ii  libsysfs2:amd64                           2.1.0+repack-1.2                           amd64        interface library to sysfs
ii  libt1-5                                   5.1.2-3.5                                  amd64        Type 1 font rasterizer library - runtime
ii  libtag1-vanilla:amd64                     1.8-0ubuntu2                               amd64        audio meta-data library - vanilla flavour
ii  libtag1c2a:amd64                          1.8-0ubuntu2                               amd64        audio meta-data library
ii  libtagc0:amd64                            1.8-0ubuntu2                               amd64        audio meta-data library - C bindings
ii  libtalloc2:amd64                          2.0.7+git20120207-1                        amd64        hierarchical pool based memory allocator
ii  libtasn1-3:amd64                          2.13-2                                     amd64        Manage ASN.1 structures (runtime)
ii  libtdb1:amd64                             1.2.10-2                                   amd64        Trivial Database - shared library
ii  libtelepathy-glib0:amd64                  0.20.0-0ubuntu1                            amd64        Telepathy framework - GLib library
ii  libterm-readkey-perl                      2.30-4build4                               amd64        A perl module for simple terminal control
ii  libtext-charwidth-perl                    0.04-7build2                               amd64        get display widths of characters on the terminal
ii  libtext-iconv-perl                        1.7-5build1                                amd64        converts between character sets in Perl
ii  libtext-wrapi18n-perl                     0.06-7                                     all          internationalized substitute of Text::Wrap
ii  libthai-data                              0.1.18-1                                   all          Data files for Thai language support library
ii  libthai0:amd64                            0.1.18-1                                   amd64        Thai language support library
ii  libtheora0:amd64                          1.1.1+dfsg.1-3.1                           amd64        The Theora Video Compression Codec
ii  libthunarx-2-0                            1.4.0-1ubuntu2                             amd64        extension library for thunar
ii  libtidy-0.99-0                            20091223cvs-1.2                            amd64        HTML syntax checker and reformatter - library
ii  libtie-ixhash-perl                        1.21-2                                     all          ordered associative arrays for Perl
ii  libtiff4:amd64                            3.9.6-9ubuntu1                             amd64        Tag Image File Format (TIFF) library (old version)
ii  libtiff5:amd64                            4.0.2-1ubuntu2                             amd64        Tag Image File Format (TIFF) library
ii  libtimedate-perl                          1.2000-1                                   all          collection of modules to manipulate date/time information
ii  libtimezonemap1                           0.3.2build1                                amd64        GTK+3 timezone map widget
ii  libtinfo5:amd64                           5.9-10ubuntu1                              amd64        shared low-level terminfo library for terminal handling
ii  libtinyxml2-0.0.0:amd64                   0~git20120518.1.a2ae54e-1                  amd64        C++ XML parsing library
ii  libtotem-plparser17                       3.4.3-0ubuntu1                             amd64        Totem Playlist Parser library - runtime files
ii  libtry-tiny-perl                          0.11-1                                     all          module providing minimalistic try/catch
ii  libts-0.0-0:amd64                         1.0-11                                     amd64        touch screen library
ii  libtumbler-1-0                            0.1.25-1ubuntu1                            amd64        library for tumbler, a D-Bus thumbnailing service
ii  libtxc-dxtn-s2tc0:amd64                   0~git20110809-3                            amd64        Texture compression library for Mesa
ii  libubuntuoneui-3.0-1                      4.0.0-0ubuntu1                             amd64        Ubuntu One widget library
ii  libudev0:amd64                            175-0ubuntu13                              amd64        udev library
ii  libudisks2-0:amd64                        2.0.0-1                                    amd64        GObject based library to access udisks2
ii  libumfpack5.4.0                           1:3.4.0-2ubuntu3                           amd64        sparse LU factorization library
ii  libunique-1.0-0                           1.1.6-4build1                              amd64        Library for writing single instance applications - shared libraries
ii  libunistring0:amd64                       0.9.3-5build1                              amd64        Unicode string library for C
ii  libunity-core-6.0-5                       6.8.0-0ubuntu2                             amd64        Core library for the Unity interface.
ii  libunity-misc4                            4.0.4-0ubuntu3                             amd64        Miscellaneous functions for Unity - shared library
ii  libunity-protocol-private0:amd64          6.8.0-0ubuntu2                             amd64        binding to get places into the launcher - private library
ii  libunity-webapps0                         2.4.1-0ubuntu2                             amd64        Web Apps integration with the Unity desktop
ii  libunity6                                 4.0.6-0ubuntu3                             amd64        binding to get places into the launcher - shared library
ii  libunity9:amd64                           6.8.0-0ubuntu2                             amd64        binding to get places into the launcher - shared library
ii  libupower-glib1                           0.9.17-1build1                             amd64        abstraction for power management - shared library
ii  liburi-perl                               1.60-1                                     all          module to manipulate and access URI strings
ii  libusb-0.1-4:amd64                        2:0.1.12-23                                amd64        userspace USB programming library
ii  libusb-1.0-0:amd64                        2:1.0.12-2                                 amd64        userspace USB programming library
ii  libusbmuxd1                               1.0.7-2                                    amd64        USB multiplexor daemon for iPhone and iPod Touch devices - library
ii  libusbmuxd2                               1.0.8-1                                    amd64        USB multiplexor daemon for iPhone and iPod Touch devices - library
ii  libutempter0                              1.1.5-4build1                              amd64        A privileged helper for utmp/wtmp updates (runtime)
ii  libutouch-evemu1:amd64                    1.0.9-0ubuntu1                             amd64        KernelInput Event Device Emulation Library
ii  libutouch-frame1                          2.2.3-0ubuntu1                             amd64        Touch Frame Library
ii  libutouch-geis1:amd64                     2.2.9-0ubuntu3                             amd64        Gesture engine interface support
ii  libutouch-grail1                          3.0.5-0ubuntu1                             amd64        Gesture Recognition And Instantiation Library
ii  libuuid-perl                              0.02-4ubuntu2                              amd64        Perl extension for using UUID interfaces as defined in e2fsprogs
ii  libuuid1:amd64                            2.20.1-5.1ubuntu2                          amd64        Universally Unique ID library
ii  libv4l-0:amd64                            0.8.8-2ubuntu1                             amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                      0.8.8-2ubuntu1                             amd64        Video4linux frame format conversion library
ii  libva1:amd64                              1.0.15-4build1                             amd64        Video Acceleration (VA) API for Linux -- runtime
ii  libvisual-0.4-0:amd64                     0.4.0-5                                    amd64        Audio visualization framework
ii  libvisual-0.4-plugins:amd64               0.4.0.dfsg.1-7build1                       amd64        Audio visualization framework plugins
ii  libvo-aacenc0:amd64                       0.1.2-1                                    amd64        VisualOn AAC encoder library
ii  libvo-amrwbenc0:amd64                     0.1.2-1                                    amd64        VisualOn AMR-WB encoder library
ii  libvorbis0a:amd64                         1.3.2-1.3                                  amd64        The Vorbis General Audio Compression Codec (Decoder library)
ii  libvorbisenc2:amd64                       1.3.2-1.3                                  amd64        The Vorbis General Audio Compression Codec (Encoder library)
ii  libvorbisfile3:amd64                      1.3.2-1.3                                  amd64        The Vorbis General Audio Compression Codec (High Level API)
ii  libvpx1:amd64                             1.1.0-1                                    amd64        VP8 video codec (shared library)
ii  libvte-2.90-9                             1:0.34.0-0ubuntu1                          amd64        Terminal emulator widget for GTK+ 3.0 - runtime files
ii  libvte-2.90-common                        1:0.34.0-0ubuntu1                          all          Terminal emulator widget for GTK+ 3.0 - common files
ii  libvte-common                             1:0.28.2-5ubuntu1                          all          Terminal emulator widget for GTK+ 2.x - common files
ii  libvte9                                   1:0.28.2-5ubuntu1                          amd64        Terminal emulator widget for GTK+ 2.0 - runtime files
ii  libwacom-common                           0.6-0ubuntu1                               all          Wacom model feature query library (common files)
ii  libwacom2:amd64                           0.6-0ubuntu1                               amd64        Wacom model feature query library
ii  libwavpack1:amd64                         4.60.1-3                                   amd64        audio codec (lossy and lossless) - library
ii  libwbclient0:amd64                        2:3.6.6-3ubuntu5                           amd64        Samba winbind client library
ii  libwebkitgtk-1.0-0                        1.10.0-0ubuntu1                            amd64        Web content engine library for GTK+
ii  libwebkitgtk-1.0-common                   1.10.0-0ubuntu1                            all          Web content engine library for GTK+ - data files
ii  libwebkitgtk-3.0-0                        1.10.0-0ubuntu1                            amd64        Web content engine library for GTK+
ii  libwebkitgtk-3.0-common                   1.10.0-0ubuntu1                            all          Web content engine library for GTK+ - data files
ii  libwildmidi-config                        0.2.3.4-2.1                                all          software MIDI player configuration
ii  libwildmidi1:amd64                        0.2.3.4-2.1                                amd64        software MIDI player library
ii  libwind0-heimdal:amd64                    1.6~git20120403+dfsg1-2                    amd64        Heimdal Kerberos - stringprep implementation
ii  libwmf0.2-7                               0.2.8.4-10ubuntu2                          amd64        Windows metafile conversion library
ii  libwnck-3-0                               3.4.3-0ubuntu1                             amd64        Window Navigator Construction Kit - runtime files
ii  libwnck-3-common                          3.4.3-0ubuntu1                             all          Window Navigator Construction Kit - common files
ii  libwnck-common                            1:2.30.7-0ubuntu2                          all          Window Navigator Construction Kit - common files
ii  libwnck22                                 1:2.30.7-0ubuntu2                          amd64        Window Navigator Construction Kit - runtime files
ii  libwpd-0.9-9                              0.9.4-3                                    amd64        Library for handling WordPerfect documents (shared library)
ii  libwpg-0.2-2                              0.2.1-1build1                              amd64        WordPerfect graphics import/convert library (shared library)
ii  libwps-0.2-2                              0.2.7-1                                    amd64        Works text file format import filter library (shared library)
ii  libwrap0:amd64                            7.6.q-23                                   amd64        Wietse Venema's TCP wrappers library
ii  libwv-1.2-3                               1.2.4-2ubuntu3                             amd64        Library for accessing Microsoft Word documents
ii  libwv-1.2-4:amd64                         1.2.9-3                                    amd64        Library for accessing Microsoft Word documents
ii  libwww-perl                               6.04-1                                     all          simple and consistent interface to the world-wide web
ii  libwww-robotrules-perl                    6.01-1                                     all          database of robots.txt-derived permissions
ii  libwxbase2.8-0:amd64                      2.8.12.1-11ubuntu3                         amd64        wxBase library (runtime) - non-GUI support classes of wxWidgets toolkit
ii  libwxgtk2.8-0:amd64                       2.8.12.1-11ubuntu3                         amd64        wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  libx11-6:amd64                            2:1.5.0-1                                  amd64        X11 client-side library
ii  libx11-data                               2:1.5.0-1                                  all          X11 client-side library
ii  libx11-dev:amd64                          2:1.5.0-1                                  amd64        X11 client-side library (development headers)
ii  libx11-xcb-dev                            2:1.5.0-1                                  amd64        Xlib/XCB interface library (development headers)
ii  libx11-xcb1:amd64                         2:1.5.0-1                                  amd64        Xlib/XCB interface library
ii  libx86-1:amd64                            1.1+ds1-10                                 amd64        x86 real-mode library
ii  libxapian22                               1.2.12-1                                   amd64        Search engine library
ii  libxatracker1:amd64                       9.0-0ubuntu1                               amd64        X acceleration library -- runtime
ii  libxau-dev:amd64                          1:1.0.7-1                                  amd64        X11 authorisation library (development headers)
ii  libxau6:amd64                             1:1.0.7-1                                  amd64        X11 authorisation library
ii  libxaw7:amd64                             2:1.0.10-2                                 amd64        X11 Athena Widget library
ii  libxcb-dri2-0:amd64                       1.8.1-1ubuntu1                             amd64        X C Binding, dri2 extension
ii  libxcb-glx0:amd64                         1.8.1-1ubuntu1                             amd64        X C Binding, glx extension
ii  libxcb-glx0-dev:amd64                     1.8.1-1ubuntu1                             amd64        X C Binding, glx extension, development files
ii  libxcb-render0:amd64                      1.8.1-1ubuntu1                             amd64        X C Binding, render extension
ii  libxcb-render0-dev:amd64                  1.8.1-1ubuntu1                             amd64        X C Binding, render extension, development files
ii  libxcb-shape0:amd64                       1.8.1-1ubuntu1                             amd64        X C Binding, shape extension
ii  libxcb-shm0:amd64                         1.8.1-1ubuntu1                             amd64        X C Binding, shm extension
ii  libxcb-shm0-dev:amd64                     1.8.1-1ubuntu1                             amd64        X C Binding, shm extension, development files
ii  libxcb-util0:amd64                        0.3.8-2build1                              amd64        utility libraries for X C Binding -- atom, aux and event
ii  libxcb1:amd64                             1.8.1-1ubuntu1                             amd64        X C Binding
ii  libxcb1-dev:amd64                         1.8.1-1ubuntu1                             amd64        X C Binding, development files
ii  libxcomposite-dev                         1:0.4.3-2build2                            amd64        X11 Composite extension library (development headers)
ii  libxcomposite1:amd64                      1:0.4.3-2build2                            amd64        X11 Composite extension library
ii  libxcursor-dev:amd64                      1:1.1.13-1                                 amd64        X cursor management library (development files)
ii  libxcursor1:amd64                         1:1.1.13-1                                 amd64        X cursor management library
ii  libxdamage-dev                            1:1.1.3-2build2                            amd64        X11 damaged region extension library (development headers)
ii  libxdamage1:amd64                         1:1.1.3-2build2                            amd64        X11 damaged region extension library
ii  libxdmcp-dev:amd64                        1:1.1.1-1                                  amd64        X11 authorisation library (development headers)
ii  libxdmcp6:amd64                           1:1.1.1-1                                  amd64        X11 Display Manager Control Protocol library
ii  libxext-dev:amd64                         2:1.3.1-2                                  amd64        X11 miscellaneous extensions library (development headers)
ii  libxext6:amd64                            2:1.3.1-2                                  amd64        X11 miscellaneous extension library
ii  libxfce4ui-1-0                            4.10.0-1                                   amd64        widget library for Xfce
ii  libxfce4ui-utils                          4.10.0-1                                   amd64        Utility files for libxfce4ui
ii  libxfce4util-bin                          4.10.0-1                                   amd64        tools for libxfce4util
ii  libxfce4util-common                       4.10.0-1                                   all          common files for libxfce4util
ii  libxfce4util4                             4.8.2-1                                    amd64        Utility functions library for Xfce4
ii  libxfce4util6                             4.10.0-1                                   amd64        Utility functions library for Xfce4
ii  libxfcegui4-4                             4.10.0-1                                   amd64        Basic GUI C functions for Xfce4
ii  libxfconf-0-2                             4.10.0-1                                   amd64        Client library for Xfce4 configure interface
ii  libxfixes-dev                             1:5.0-4ubuntu5                             amd64        X11 miscellaneous 'fixes' extension library (development headers)
ii  libxfixes3:amd64                          1:5.0-4ubuntu5                             amd64        X11 miscellaneous 'fixes' extension library
ii  libxfont1                                 1:1.4.5-2                                  amd64        X11 font rasterisation library
ii  libxft-dev                                2.3.1-1                                    amd64        FreeType-based font drawing library for X (development files)
ii  libxft2:amd64                             2.3.1-1                                    amd64        FreeType-based font drawing library for X
ii  libxi-dev                                 2:1.6.1-1                                  amd64        X11 Input extension library (development headers)
ii  libxi6:amd64                              2:1.6.1-1                                  amd64        X11 Input extension library
ii  libxinerama-dev:amd64                     2:1.1.2-1                                  amd64        X11 Xinerama extension library (development headers)
ii  libxinerama1:amd64                        2:1.1.2-1                                  amd64        X11 Xinerama extension library
ii  libxkbfile1:amd64                         1:1.0.8-1                                  amd64        X11 keyboard file manipulation library
ii  libxklavier16                             5.2.1-1ubuntu2                             amd64        X Keyboard Extension high-level API
ii  libxml-parser-perl                        2.41-1build2                               amd64        Perl module for parsing XML files
ii  libxml-twig-perl                          1:3.39-1ubuntu1                            all          Perl module for processing huge XML documents in tree mode
ii  libxml-xpath-perl                         1.13-7                                     all          Perl module for processing XPath
ii  libxml2:amd64                             2.8.0+dfsg1-5ubuntu2                       amd64        GNOME XML library
ii  libxml2-utils                             2.8.0+dfsg1-5ubuntu2                       amd64        XML utilities
ii  libxmu6:amd64                             2:1.1.1-1                                  amd64        X11 miscellaneous utility library
ii  libxmuu1:amd64                            2:1.1.1-1                                  amd64        X11 miscellaneous micro-utility library
ii  libxp6:amd64                              1:1.0.1-2build1                            amd64        X Printing Extension (Xprint) client library
ii  libxpm4:amd64                             1:3.5.10-1                                 amd64        X11 pixmap library
ii  libxrandr-dev                             2:1.4.0-1                                  amd64        X11 RandR extension library (development headers)
ii  libxrandr2:amd64                          2:1.4.0-1                                  amd64        X11 RandR extension library
ii  libxrender-dev:amd64                      1:0.9.7-1                                  amd64        X Rendering Extension client library (development files)
ii  libxrender1:amd64                         1:0.9.7-1                                  amd64        X Rendering Extension client library
ii  libxres1:amd64                            2:1.0.6-1                                  amd64        X11 Resource extension library
ii  libxslt1.1:amd64                          1.1.26-14                                  amd64        XSLT 1.0 processing library - runtime library
ii  libxss1:amd64                             1:1.2.2-1                                  amd64        X11 Screen Saver extension library
ii  libxt6:amd64                              1:1.1.3-1                                  amd64        X11 toolkit intrinsics library
ii  libxtst6:amd64                            2:1.2.1-1                                  amd64        X11 Testing -- Record extension library
ii  libxv1:amd64                              2:1.0.7-1                                  amd64        X11 Video extension library
ii  libxvidcore4:amd64                        2:1.3.2-9                                  amd64        Open source MPEG-4 video codec (library)
ii  libxvmc1                                  2:1.0.7-1ubuntu1                           amd64        X11 Video extension library
ii  libxxf86dga1:amd64                        2:1.1.3-2                                  amd64        X11 Direct Graphics Access extension library
ii  libxxf86vm-dev                            1:1.1.2-1                                  amd64        X11 XFree86 video mode extension library (development headers)
ii  libxxf86vm1:amd64                         1:1.1.2-1                                  amd64        X11 XFree86 video mode extension library
ii  libyajl2                                  2.0.4-2                                    amd64        Yet Another JSON Library
ii  libyaml-tiny-perl                         1.51-1                                     all          Perl module for reading and writing YAML files
ii  libyelp0                                  3.6.0-0ubuntu1                             amd64        Library for the GNOME help browser
ii  libzbar0                                  0.10+doc-7build3                           amd64        bar code scanner and decoder (library)
ii  libzeitgeist-1.0-1                        0.3.18-1ubuntu1                            amd64        library to access Zeitgeist - shared library
ii  libzen0:amd64                             0.4.28-1                                   amd64        ZenLib C++ utility library -- runtime
ii  libzephyr4                                3.0.2-2                                    amd64        Project Athena's notification service - non-Kerberos libraries
ii  libzvbi-common                            0.2.33-6                                   all          Vertical Blanking Interval decoder (VBI) - common files
ii  libzvbi0:amd64                            0.2.33-6                                   amd64        Vertical Blanking Interval decoder (VBI) - runtime files
ii  lightdm                                   1.4.0-0ubuntu2                             amd64        Display Manager
ii  lightdm-gtk-greeter                       1.3.1-0ubuntu1                             amd64        LightDM GTK+ Greeter
ii  link-grammar-dictionaries-en              4.7.4-2                                    all          Carnegie Mellon University's link grammar parser (English dictionary)
ii  lintian                                   2.5.10.2ubuntu2                            all          Debian package checker
ii  linux-firmware                            1.95                                       all          Firmware for Linux kernel drivers
ii  linux-generic                             3.5.0.17.19                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.5.0-17                    3.5.0-17.28                                all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-17-generic            3.5.0-17.28                                amd64        Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
ii  linux-headers-generic                     3.5.0.17.19                                amd64        Generic Linux kernel headers
ii  linux-image-2.6.38-11-generic             2.6.38-11.50                               amd64        Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-3.0.0-12-generic              3.0.0-12.20                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-16-generic              3.0.0-16.29                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.5.0-17-generic              3.5.0-17.28                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-17-generic        3.5.0-17.28                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.5.0.17.19                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                      3.5.0-17.28                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                          1.0.25+dfsg-0ubuntu3                       all          base package for ALSA and OSS sound systems
ii  locales                                   2.13+git20120306-3                         all          common files for locale support
ii  lockfile-progs                            0.1.16build1                               amd64        Programs for locking and unlocking files and mailboxes
ii  login                                     1:4.1.4.2+svn3283-3ubuntu7                 amd64        system login tools
ii  logrotate                                 3.7.8-6ubuntu6                             amd64        Log rotation utility
ii  lp-solve                                  5.5.0.13-7                                 amd64        Solve (mixed integer) linear programming problems
ii  lsb-base                                  4.0-0ubuntu26                              all          Linux Standard Base 4.0 init script functionality
ii  lsb-release                               4.0-0ubuntu26                              all          Linux Standard Base version reporting utility
ii  lshw                                      02.16-1                                    amd64        information about hardware configuration
ii  lsof                                      4.86+dfsg-1ubuntu1                         amd64        Utility to list open files
ii  ltrace                                    0.5.3-2.1ubuntu3                           amd64        Tracks runtime library calls in dynamically linked programs
ii  lvm2                                      2.02.95-4ubuntu1                           amd64        Linux Logical Volume Manager
ii  lynx-cur                                  2.8.8dev.12-2                              amd64        Text-mode WWW Browser with NLS support (development version)
ii  lzma                                      9.22-2ubuntu2                              amd64        Compression and decompression in the LZMA format - command line utility
ii  m4                                        1.4.16-3                                   amd64        a macro processing language
ii  mailutils                                 1:2.99.97-3                                amd64        GNU mailutils utilities for handling mail
ii  mailutils-common                          1:2.99.97-3                                all          Common files for GNU mailutils
ii  make                                      3.81-8.2ubuntu2                            amd64        An utility for Directing compilation.
ii  makedev                                   2.3.1-91ubuntu2                            all          creates device files in /dev
ii  man-db                                    2.6.3-1                                    amd64        on-line manual pager
ii  manpages                                  3.40-0.1ubuntu3                            all          Manual pages about using a GNU/Linux system
ii  manpages-dev                              3.40-0.1ubuntu3                            all          Manual pages about using GNU/Linux for development
ii  mawk                                      1.3.3-17                                   amd64        a pattern scanning and text processing language
ii  media-player-info                         17-1                                       all          Media player identification files
ii  mediainfo                                 0.7.59-1                                   amd64        command-line utility for reading information from audio/video files
ii  memtest86+                                4.20-1.1ubuntu2                            amd64        thorough real-mode memory tester
ii  mesa-common-dev                           9.0-0ubuntu1                               amd64        Developer documentation for Mesa
ii  metacity                                  1:2.34.8-0ubuntu4                          amd64        lightweight GTK+ window manager
ii  metacity-common                           1:2.34.8-0ubuntu4                          all          shared files for the Metacity window manager
ii  mime-support                              3.52-1ubuntu1                              all          MIME files 'mime.types' & 'mailcap', and support programs
ii  min12xxw                                  0.0.9-6ubuntu2                             all          transitional dummy package for min12xxw printer driver
ii  miscfiles                                 1.4.2.dfsg.1-9                             all          Dictionaries and other interesting files
ii  mlocate                                   0.25-0ubuntu1                              amd64        quickly find files on the filesystem based on their name
ii  mobile-broadband-provider-info            20120708-1                                 all          database of mobile broadband service providers
ii  modemmanager                              0.6.0.0.really-0ubuntu1                    amd64        D-Bus service for managing modems
ii  module-init-tools                         3.16-1ubuntu6                              amd64        tools for managing Linux kernel modules
ii  mono-4.0-gac                              2.10.8.1-5ubuntu1                          all          Mono GAC tool (for CLI 4.0)
ii  mono-gac                                  2.10.8.1-5ubuntu1                          all          Mono GAC tool
ii  mono-runtime                              2.10.8.1-5ubuntu1                          amd64        Mono runtime
ii  mount                                     2.20.1-5.1ubuntu2                          amd64        Tools for mounting and manipulating filesystems
ii  mountall                                  2.42                                       amd64        filesystem mounting tool
ii  mousepad                                  0.2.16-6ubuntu1                            amd64        simple Xfce oriented text editor
ii  mousetweaks                               3.6.0-0ubuntu2                             amd64        mouse accessibility enhancements for the GNOME desktop
ii  mpg321                                    0.3.2-1.1                                  amd64        Simple and lightweight command line MP3 player
ii  mscompress                                0.3-3.1build1                              amd64        Microsoft "compress.exe/expand.exe" compatible (de)compressor
ii  mtools                                    4.0.17-1                                   amd64        Tools for manipulating MSDOS files
ii  mtr-tiny                                  0.82-3ubuntu1                              amd64        Full screen ncurses traceroute tool
ii  multiarch-support                         2.15-0ubuntu20                             amd64        Transitional package to ensure multiarch compatibility
ii  mupdf                                     0.9-2ubuntu1                               amd64        lightweight PDF viewer
ii  murrine-themes                            0.98.3ubuntu1                              all          themes for gtk2 murrine engine
ii  myspell-en-au                             2.1-5.3ubuntu1                             all          English_australian dictionary for myspell
ii  myspell-en-gb                             1:3.3.0-2ubuntu3                           all          English_british dictionary for myspell
ii  myspell-en-za                             1:3.3.0-2ubuntu3                           all          English_southafrican dictionary for myspell
ii  mysql-common                              5.5.27-0ubuntu2                            all          MySQL database common files, e.g. /etc/mysql/my.cnf
ii  nano                                      2.2.6-1ubuntu1                             amd64        small, friendly text editor inspired by Pico
ii  nautilus-data                             1:3.5.90.really.3.4.2-0ubuntu4             all          data files for nautilus
ii  nautilus-dropbox                          1.4.0-3                                    amd64        Dropbox integration for Nautilus
ii  ncurses-base                              5.9-10ubuntu1                              all          basic terminal type definitions
ii  ncurses-bin                               5.9-10ubuntu1                              amd64        terminal-related programs and man pages
ii  ncurses-term                              5.9-10ubuntu1                              all          additional terminal type definitions
ii  net-tools                                 1.60-24.1ubuntu3                           amd64        The NET-3 networking toolkit
ii  netbase                                   5.0ubuntu1                                 all          Basic TCP/IP networking system
ii  netcat-openbsd                            1.105-6ubuntu1                             amd64        TCP/IP swiss army knife
ii  network-manager                           0.9.6.0-0ubuntu7                           amd64        network management framework (daemon and userspace tools)
ii  network-manager-gnome                     0.9.6.2-0ubuntu6                           amd64        network management framework (GNOME frontend)
ii  network-manager-pptp                      0.9.6.0-0ubuntu1                           amd64        network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome                0.9.6.0-0ubuntu1                           amd64        network management framework (PPTP plugin GNOME GUI)
ii  ntfs-3g                                   1:2012.1.15AR.5-4ubuntu3                   amd64        read/write NTFS driver for FUSE
ii  ntp                                       1:4.2.6.p3+dfsg-1ubuntu5                   amd64        Network Time Protocol daemon and utility programs
ii  ntpdate                                   1:4.2.6.p3+dfsg-1ubuntu5                   amd64        client for setting system time from NTP servers
ii  nvidia-common                             1:0.2.71                                   amd64        transitional package for ubuntu-drivers-common
ii  obex-data-server                          0.4.6-0ubuntu2                             amd64        D-Bus service for OBEX client and server side functionality
ii  onboard                                   0.98.0-0ubuntu2                            amd64        Simple On-screen Keyboard
ii  oneconf                                   0.2.9.1                                    all          synchronize your configuration data over the network
ii  openjdk-7-jre:amd64                       7u7-2.3.2a-1ubuntu1                        amd64        OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-7-jre-headless:amd64              7u7-2.3.2a-1ubuntu1                        amd64        OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-7-jre-lib                         7u7-2.3.2a-1ubuntu1                        all          OpenJDK Java runtime (architecture independent libraries)
ii  openprinting-ppds                         20120823-0ubuntu4                          all          OpenPrinting printer support - PostScript PPD files
ii  openssh-client                            1:6.0p1-3ubuntu1                           amd64        secure shell (SSH) client, for secure access to remote machines
ii  openssh-server                            1:6.0p1-3ubuntu1                           amd64        secure shell (SSH) server, for secure access from remote machines
ii  openssl                                   1.0.1c-3ubuntu2                            amd64        Secure Socket Layer (SSL) binary and related cryptographic tools
ii  orage                                     4.8.3-2                                    amd64        Calendar for Xfce Desktop Environment
ii  os-prober                                 1.56ubuntu1                                amd64        utility to detect other OSes on a set of drives
ii  parted                                    2.3-10ubuntu2                              amd64        disk partition manipulator
ii  passwd                                    1:4.1.4.2+svn3283-3ubuntu7                 amd64        change and administer password and group data
ii  pastebinit                                1.3-2ubuntu3                               all          command-line pastebin client
ii  patch                                     2.6.1-3ubuntu1                             amd64        Apply a diff file to an original
ii  patchutils                                0.3.2-1.1build1                            amd64        Utilities to work with patches
ii  pciutils                                  1:3.1.9-5ubuntu4                           amd64        Linux PCI Utilities
ii  pcmciautils                               018-8                                      amd64        PCMCIA utilities for Linux 2.6
ii  perl                                      5.14.2-13                                  amd64        Larry Wall's Practical Extraction and Report Language
ii  perl-base                                 5.14.2-13                                  amd64        minimal Perl system
ii  perl-modules                              5.14.2-13                                  all          Core Perl modules
ii  pidgin                                    1:2.10.6-0ubuntu2                          amd64        graphical multi-protocol instant messaging client for X
ii  pidgin-data                               1:2.10.6-0ubuntu2                          all          multi-protocol instant messaging client - data files
ii  pidgin-libnotify                          0.14-4ubuntu11                             amd64        display notification bubbles in pidgin
ii  pidgin-microblog                          0.3.0-3                                    amd64        Microblogging plugins for Pidgin
ii  pkg-config                                0.26-1ubuntu2                              amd64        manage compile and link flags for libraries
ii  plymouth                                  0.8.4-0ubuntu3                             amd64        graphical boot animation and logger - main package
ii  plymouth-label                            0.8.4-0ubuntu3                             amd64        graphical boot animation and logger - label control
ii  plymouth-theme-ubuntu-text                0.8.4-0ubuntu3                             amd64        graphical boot animation and logger - ubuntu-logo theme
ii  plymouth-theme-xubuntu-logo               12.10.2                                    all          graphical boot animation and logger - xubuntu-logo theme
ii  plymouth-theme-xubuntu-text               12.10.2                                    all          graphical boot animation and logger - xubuntu-text theme
ii  pm-utils                                  1.4.1-9                                    all          utilities and scripts for power management
ii  pnm2ppa                                   1.13+nondbs-0ubuntu2                       all          transitional dummy package for pnm2ppa printer driver
ii  po-debconf                                1.0.16+nmu2ubuntu1                         all          tool for managing templates file translations with gettext
ii  policykit-1                               0.104-2ubuntu1                             amd64        framework for managing administrative policies and privileges
ii  policykit-1-gnome                         0.105-1ubuntu4                             amd64        GNOME authentication agent for PolicyKit-1
ii  policykit-desktop-privileges              0.12                                       all          run common desktop actions without password
ii  poppler-utils                             0.20.4-0ubuntu1                            amd64        PDF utilities (based on Poppler)
ii  popularity-contest                        1.53ubuntu1                                all          Vote for your favourite packages automatically
ii  postfix                                   2.9.3-2ubuntu2                             amd64        High-performance mail transport agent
ii  powermgmt-base                            1.31build1                                 amd64        Common utils and configs for power management
ii  ppp                                       2.4.5-5ubuntu2                             amd64        Point-to-Point Protocol (PPP) - daemon
ii  pppconfig                                 2.3.18+nmu3ubuntu1                         all          A text menu based utility for configuring ppp
ii  pppoeconf                                 1.20ubuntu1                                all          configures PPPoE/ADSL connections
ii  pptp-linux                                1.7.2-7                                    amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  printer-driver-c2esp                      25c-1ubuntu1                               amd64        printer driver for Kodak ESP AiO color inkjet Series
ii  printer-driver-foo2zjs                    20120510dfsg0-1ubuntu1                     amd64        printer driver for ZjStream-based printers
ii  printer-driver-gutenprint                 5.2.9-1ubuntu1                             amd64        printer drivers for CUPS
ii  printer-driver-hpcups                     3.12.6-3ubuntu4                            amd64        HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  printer-driver-hpijs                      3.12.6-3ubuntu4                            amd64        HP Linux Printing and Imaging - gs IJS driver (hpijs)
ii  printer-driver-min12xxw                   0.0.9-6ubuntu2                             amd64        printer driver for KonicaMinolta PagePro 1[234]xxW
ii  printer-driver-pnm2ppa                    1.13+nondbs-0ubuntu2                       amd64        printer driver for HP-GDI printers
ii  printer-driver-ptouch                     1.3-4ubuntu1                               amd64        printer driver Brother P-touch label printers
ii  printer-driver-pxljr                      1.3+repack0-2build1                        amd64        printer driver for HP Color LaserJet 35xx/36xx
ii  printer-driver-sag-gdi                    0.1-3                                      all          printer driver for Ricoh Aficio SP 1000s/SP 1100s
ii  printer-driver-splix                      2.0.0+svn306-2ubuntu1                      amd64        Driver for Samsung and Xerox SPL2 and SPLc laser printers
ii  procps                                    1:3.3.3-2ubuntu3                           amd64        /proc file system utilities
ii  psmisc                                    22.19-1ubuntu1                             amd64        utilities that use the proc file system
ii  psutils                                   1.17-32                                    amd64        PostScript document handling utilities
ii  ptouch-driver                             1.3-4ubuntu1                               all          transitional dummy package for ptouch printer driver
ii  pulseaudio                                1:2.1-0ubuntu4                             amd64        PulseAudio sound server
ii  pulseaudio-esound-compat                  1:2.1-0ubuntu4                             amd64        PulseAudio ESD compatibility layer
ii  pulseaudio-module-x11                     1:2.1-0ubuntu4                             amd64        X11 module for PulseAudio sound server
ii  pulseaudio-utils                          1:2.1-0ubuntu4                             amd64        Command line tools for the PulseAudio sound server
ii  pxljr                                     1.3+repack0-2build1                        all          transitional dummy package for pxljr printer driver
ii  python                                    2.7.3-0ubuntu7                             amd64        interactive high-level object-oriented language (default version)
ii  python-appindicator                       12.10.0-0ubuntu1                           amd64        Python bindings for libappindicator
ii  python-apport                             2.6.1-0ubuntu3                             all          Python library for Apport crash report handling
ii  python-apt                                0.8.7ubuntu4                               amd64        Python interface to libapt-pkg
ii  python-apt-common                         0.8.7ubuntu4                               all          Python interface to libapt-pkg (locales)
ii  python-aptdaemon                          0.45+bzr861-0ubuntu9.1                     all          Python 2 module for the server and client of aptdaemon
ii  python-aptdaemon-gtk                      0.45+bzr861-0ubuntu9.1                     all          Transitional dummy package
ii  python-aptdaemon.gtk3widgets              0.45+bzr861-0ubuntu9.1                     all          Python 2 GTK+ 3 widgets to run an aptdaemon client
ii  python-aptdaemon.gtkwidgets               0.45+bzr861-0ubuntu9.1                     all          Python GTK+ 2 widgets to run an aptdaemon client
ii  python-cairo                              1.8.8-1ubuntu4                             amd64        Python bindings for the Cairo vector graphics library
ii  python-central                            0.6.17ubuntu2                              all          register and build utility for Python packages
ii  python-chardet                            2.0.1-2build1                              all          universal character encoding detector
ii  python-configglue                         1.0-1build1                                all          Glues together optparse.OptionParser and ConfigParser.ConfigParser
ii  python-configobj                          4.7.2+ds-4                                 all          simple but powerful config file reader and writer for Python
ii  python-crypto                             2.6-2                                      amd64        cryptographic algorithms and protocols for Python
ii  python-cups                               1.9.62-0ubuntu1                            amd64        Python bindings for CUPS
ii  python-cupshelpers                        1.3.11+20120807-0ubuntu10                  all          Python modules for printer configuration with CUPS
ii  python-dbus                               1.1.1-1                                    amd64        simple interprocess messaging system (Python interface)
ii  python-dbus-dev                           1.1.1-1                                    all          main loop integration development files for python-dbus
ii  python-debian                             0.1.21+nmu2ubuntu1                         all          Python modules to work with Debian-related data formats
ii  python-debtagshw                          1.10.2                                     all          Match debtags hardware:: tags against the actual hardware
ii  python-defer                              1.0.6-2                                    all          Small framework for asynchronous programming (Python 2)
ii  python-dirspec                            4.0.0-0ubuntu1                             all          Python User Folders Specification Library
ii  python-gconf                              2.28.1+dfsg-1build1                        amd64        Python bindings for the GConf configuration database system
ii  python-gdbm                               2.7.3-1ubuntu2                             amd64        GNU dbm database support for Python
ii  python-gi                                 3.4.0-1                                    amd64        Python 2.x bindings for gobject-introspection libraries
ii  python-gi-cairo                           3.4.0-1                                    amd64        Python Cairo bindings for the GObject library
ii  python-glade2                             2.24.0-3build1                             amd64        GTK+ bindings: Glade support
ii  python-gmenu                              3.0.1-0ubuntu8                             amd64        GNOME implementation of the freedesktop menu specification
ii  python-gnomekeyring                       2.32.0+dfsg-2ubuntu1                       amd64        Python bindings for the GNOME keyring library
ii  python-gnupginterface                     0.3.2-9.1ubuntu3                           all          Python interface to GnuPG (GPG)
ii  python-gobject                            3.4.0-1                                    all          Python 2.x bindings for GObject - transitional package
ii  python-gobject-2                          2.28.6-10ubuntu2                           amd64        deprecated static Python bindings for the GObject library
ii  python-gpgme                              0.2-2                                      amd64        python wrapper for the GPGME library
ii  python-gst0.10                            0.10.22-3ubuntu1                           amd64        generic media-playing framework (Python bindings)
ii  python-gtk2                               2.24.0-3build1                             amd64        Python bindings for the GTK+ widget set
ii  python-httplib2                           0.7.4-2                                    all          comprehensive HTTP client library written for Python
ii  python-ibus                               1.4.1-7ubuntu1                             all          Intelligent Input Bus - Python support
ii  python-imaging                            1.1.7-4build1                              amd64        Python Imaging Library
ii  python-keyring                            0.9.2-1                                    all          store and access your passwords safely
ii  python-launchpad-integration              0.1.56.2                                   amd64        library for launchpad integration
ii  python-launchpadlib                       1.9.12-2                                   all          Launchpad web services client library
ii  python-lazr.restfulclient                 0.12.0-2                                   all          client for lazr.restful-based web services
ii  python-lazr.uri                           1.0.3-1                                    all          library for parsing, manipulating, and generating URIs
ii  python-libxml2                            2.8.0+dfsg1-5ubuntu2                       amd64        Python bindings for the GNOME XML library
ii  python-lxml                               2.3.5-1                                    amd64        pythonic binding for the libxml2 and libxslt libraries
ii  python-minimal                            2.7.3-0ubuntu7                             amd64        minimal subset of the Python language (default version)
ii  python-notify                             0.1.1-3build1                              amd64        Python bindings for libnotify
ii  python-oauth                              1.0.1-3build1                              all          Python library implementing of the OAuth protocol
ii  python-openssl                            0.13-2ubuntu1                              amd64        Python 2 wrapper around the OpenSSL library
ii  python-pam                                0.4.2-13ubuntu2                            amd64        Python interface to the PAM library
ii  python-pexpect                            2.4-1                                      all          Python module for automating interactive applications
ii  python-piston-mini-client                 0.7.2+bzr57-0ubuntu2                       all          library for writing clients for Django's Piston REST APIs
ii  python-pkg-resources                      0.6.28-1ubuntu2                            all          Package Discovery and Resource Access using pkg_resources
ii  python-problem-report                     2.6.1-0ubuntu3                             all          Python library to handle problem reports
ii  python-protobuf                           2.4.1-3ubuntu1                             amd64        Python bindings for protocol buffers
ii  python-pycurl                             7.19.0-5ubuntu1                            amd64        Python bindings to libcurl
ii  python-pyinotify                          0.9.3-1.1                                  all          simple Linux inotify Python bindings
ii  python-serial                             2.5-3                                      all          pyserial - module encapsulating access for the serial port
ii  python-simplejson                         2.6.1-1                                    amd64        simple, fast, extensible JSON encoder/decoder for Python
ii  python-six                                1.1.0-2                                    all          Python 2 and 3 compatibility library (Python 2 interface)
ii  python-smbc                               1.0.13-0ubuntu2                            amd64        Python bindings for Samba clients (libsmbclient)
ii  python-software-properties                0.92.9                                     all          manage the repositories that you install software from
ii  python-support                            1.0.15                                     all          automated rebuilding support for Python modules
ii  python-twisted-bin                        12.2.0-1                                   amd64        Event-based framework for internet applications
ii  python-twisted-core                       12.2.0-1                                   all          Event-based framework for internet applications
ii  python-twisted-names                      12.2.0-1                                   all          DNS protocol implementation with client and server
ii  python-twisted-web                        12.2.0-1                                   all          HTTP protocol implementation together with clients and servers
ii  python-ubuntu-sso-client                  4.0.0-0ubuntu1                             all          Ubuntu Single Sign-On client - Python library
ii  python-ubuntuone-client                   4.0.0-0ubuntu1                             all          Ubuntu One client Python libraries
ii  python-ubuntuone-storageprotocol          4.0.0-0ubuntu1                             all          Python library for Ubuntu One file storage and sharing service
ii  python-virtkey                            0.61.0-0ubuntu1                            amd64        Library to emulate keyboard keypresses.
ii  python-vte                                1:0.28.2-5ubuntu1                          amd64        Python bindings for the VTE widget set
ii  python-wadllib                            1.3.0-2                                    all          Python library for navigating WADL files
ii  python-webkit                             1.1.8-2ubuntu3                             amd64        WebKit/Gtk Python bindings
ii  python-wsgi-intercept                     0.5.1-0ubuntu1                             all          installs a WSGI application in place of a real URI for testing
ii  python-wxgtk2.8                           2.8.12.1-11ubuntu3                         amd64        wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
ii  python-wxversion                          2.8.12.1-11ubuntu3                         all          wxWidgets Cross-platform C++ GUI toolkit (wxPython version selector)
ii  python-xapian                             1.2.12-2                                   amd64        Xapian search engine interface for Python
ii  python-xdg                                0.20-0ubuntu1                              all          Python 2 library to access freedesktop.org standards
ii  python-xkit                               0.5.0                                      all          library for the manipulation of xorg.conf files (Python 2)
ii  python-zeitgeist                          0.9.5-0ubuntu1                             all          event logging framework - Python bindings
ii  python-zope.interface                     3.6.1-3                                    amd64        Interfaces for Python
ii  python2.7                                 2.7.3-5ubuntu4                             amd64        Interactive high-level object-oriented language (version 2.7)
ii  python2.7-minimal                         2.7.3-5ubuntu4                             amd64        Minimal subset of the Python language (version 2.7)
ii  python3                                   3.2.3-5ubuntu1                             all          interactive high-level object-oriented language (default python3 version)
ii  python3-apport                            2.6.1-0ubuntu3                             all          Python 3 library for Apport crash report handling
ii  python3-apt                               0.8.7ubuntu4                               amd64        Python 3 interface to libapt-pkg
ii  python3-aptdaemon                         0.45+bzr861-0ubuntu9.1                     all          Python 3 module for the server and client of aptdaemon
ii  python3-aptdaemon.gtk3widgets             0.45+bzr861-0ubuntu9.1                     all          Python 3 GTK+ 3 widgets to run an aptdaemon client
ii  python3-cairo                             1.10.0+dfsg-3~exp2                         amd64        Python 3 bindings for the Cairo vector graphics library
ii  python3-dbus                              1.1.1-1                                    amd64        simple interprocess messaging system (Python 3 interface)
ii  python3-defer                             1.0.6-2                                    all          Small framework for asynchronous programming (Python 3)
ii  python3-distupgrade                       1:0.190.1                                  all          manage release upgrades
ii  python3-gdbm                              3.3.0-1                                    amd64        GNU dbm database support for Python 3.x
ii  python3-gi                                3.4.0-1                                    amd64        Python 3 bindings for gobject-introspection libraries
ii  python3-gi-cairo                          3.4.0-1                                    amd64        Python 3 Cairo bindings for the GObject library
ii  python3-minimal                           3.2.3-5ubuntu1                             all          minimal subset of the Python language (default python3 version)
ii  python3-pkg-resources                     0.6.28-1ubuntu2                            all          Package Discovery and Resource Access using pkg_resources
ii  python3-problem-report                    2.6.1-0ubuntu3                             all          Python 3 library to handle problem reports
ii  python3-software-properties               0.92.9                                     all          manage the repositories that you install software from
ii  python3-update-manager                    1:0.174.3                                  all          python 3.x module for update-manager
ii  python3-virtkey                           0.61.0-0ubuntu1                            amd64        Library to emulate keyboard keypresses.
ii  python3-xkit                              0.5.0                                      all          library for the manipulation of xorg.conf files (Python 3)
ii  python3.2                                 3.2.3-6ubuntu3                             amd64        Interactive high-level object-oriented language (version 3.2)
ii  python3.2-minimal                         3.2.3-6ubuntu3                             amd64        Minimal subset of the Python language (version 3.2)
ii  qdbus                                     4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 D-Bus tool
ii  qt4-linguist-tools                        4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 Linguist tools
ii  qt4-qmake                                 4:4.8.3+dfsg-0ubuntu3                      amd64        Qt 4 qmake Makefile generator tool
ii  quadrapassel                              1:3.6.0.2-0ubuntu1                         amd64        popular Russian game, similar to Tetris
ii  radeontool                                1.6.2-1.1build1                            amd64        utility to control ATI Radeon backlight functions on laptops
ii  rarian-compat                             0.8.1-5build1                              amd64        Documentation meta-data library (compatibility tools)
ii  rastertosag-gdi                           0.1-3                                      all          transitional dummy package for rastertosag-gdi printer driver
ii  rdesktop                                  1.7.1-1ubuntu1                             amd64        RDP client for Windows NT/2000 Terminal Server and Windows Servers
ii  readline-common                           6.2-9                                      all          GNU readline and history libraries, common files
ii  resolvconf                                1.67ubuntu2                                all          name server information handler
ii  rfkill                                    0.4-1ubuntu3                               amd64        tool for enabling and disabling wireless devices
ii  ristretto                                 0.6.3-0ubuntu1                             amd64        lightweight picture-viewer for the Xfce desktop environment
ii  rsync                                     3.0.9-3ubuntu1                             amd64        fast, versatile, remote (and local) file-copying tool
ii  rsyslog                                   5.8.6-1ubuntu9                             amd64        reliable system and kernel logging daemon
ii  rtkit                                     0.10-2build1                               amd64        Realtime Policy and Watchdog Daemon
ii  samba                                     2:3.6.6-3ubuntu5                           amd64        SMB/CIFS file, print, and login server for Unix
ii  samba-common                              2:3.6.6-3ubuntu5                           all          common files used by both the Samba server and client
ii  samba-common-bin                          2:3.6.6-3ubuntu5                           amd64        common files used by both the Samba server and client
ii  screensaver-default-images                0.2-1                                      all          Wallpapers for image processing screensavers
ii  sed                                       4.2.1-10ubuntu1                            amd64        The GNU sed stream editor
ii  sensible-utils                            0.0.7ubuntu1                               all          Utilities for sensible alternative selection
ii  session-migration                         0.2                                        amd64        Tool to migrate in user session settings
ii  sessioninstaller                          0.20+bzr131-0ubuntu2                       all          APT based installer using PackageKit's session DBus API
ii  sgml-base                                 1.26+nmu3ubuntu1                           all          SGML infrastructure and SGML catalog file support
ii  sgml-data                                 2.0.8                                      all          common SGML and XML data
ii  shared-mime-info                          1.0-1ubuntu2                               amd64        FreeDesktop.org shared MIME database and spec
ii  shimmer-themes                            1.5.3-0ubuntu1                             all          Gtk+ themes from Shimmer Project
ii  signon-keyring-extension                  0.3-0ubuntu1                               amd64        GNOME keyring extension for signond
ii  signon-plugin-oauth2                      0.11-0ubuntu3                              amd64        Single Signon oauth2 plugin
ii  signon-ui                                 0.11-0ubuntu1                              amd64        Single Sign-on UI
ii  signond                                   8.43-0ubuntu1                              amd64        Single Sign On framework
ii  smbclient                                 2:3.6.6-3ubuntu5                           amd64        command-line SMB/CIFS clients for Unix
ii  software-center                           5.4.1.2                                    all          Utility for browsing, installing, and removing software
ii  software-center-aptdaemon-plugins         0.1.5                                      all          The aptdaemon plugins for software-center
ii  software-properties-common                0.92.9                                     all          manage the repositories that you install software from (common)
ii  software-properties-gtk                   0.92.9                                     all          manage the repositories that you install software from (gtk)
ii  sound-theme-freedesktop                   0.7.pristine-2                             all          freedesktop.org sound theme
ii  spawn-fcgi                                1.6.3-1                                    amd64        A fastcgi process spawner
ii  speech-dispatcher                         0.7.1-6.1ubuntu2                           amd64        Common interface to speech synthesizers
ii  splix                                     2.0.0+svn306-2ubuntu1                      all          transitional dummy package for splix printer driver
ii  ssh                                       1:6.0p1-3ubuntu1                           all          secure shell client and server (metapackage)
ii  ssh-import-id                             2.12-0ubuntu1                              all          securely retrieve an SSH public key and install it locally
ii  ssl-cert                                  1.0.32                                     all          simple debconf wrapper for OpenSSL
ii  strace                                    4.5.20-2.3ubuntu2                          amd64        A system call tracer
ii  sudo                                      1.8.5p2-1ubuntu1                           amd64        Provide limited super user privileges to specific users
ii  synaptic                                  0.75.12build1                              amd64        Graphical package manager
ii  syslinux                                  2:4.05+dfsg-6                              amd64        collection of boot loaders
ii  syslinux-common                           2:4.05+dfsg-6                              all          collection of boot loaders (common files)
ii  syslinux-legacy                           2:3.63+dfsg-2ubuntu5                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  system-config-printer-common              1.3.11+20120807-0ubuntu10                  all          Printer configuration GUI
ii  system-config-printer-gnome               1.3.11+20120807-0ubuntu10                  all          Printer configuration GUI
ii  system-config-printer-udev                1.3.11+20120807-0ubuntu10                  amd64        Printer auto-configuration facility based on udev
ii  system-tools-backends                     2.10.2-1ubuntu1                            amd64        System Tools to manage computer configuration -- scripts
ii  sysv-rc                                   2.88dsf-13.10ubuntu13                      all          System-V-like runlevel change mechanism
ii  sysv-rc-conf                              0.99-7                                     all          SysV init runlevel configuration tool for the terminal
ii  sysvinit-utils                            2.88dsf-13.10ubuntu13                      amd64        System-V-like utilities
ii  tango-icon-theme                          0.8.90-5                                   all          Tango icon theme
ii  tango-icon-theme-common                   0.7-0ubuntu2                               all          Tango Icon theme - common icons
ii  tar                                       1.26-4ubuntu1                              amd64        GNU version of the tar archiving utility
ii  tcl                                       8.5.0-2                                    all          The Tool Command Language (default version) - run-time files
ii  tcl8.4                                    8.4.19-4ubuntu4                            amd64        Tcl (the Tool Command Language) v8.4 - run-time files
ii  tcl8.5                                    8.5.11-2ubuntu1                            amd64        Tcl (the Tool Command Language) v8.5 - run-time files
ii  tcpd                                      7.6.q-23                                   amd64        Wietse Venema's TCP wrapper utilities
ii  tcpdump                                   4.3.0-1ubuntu1                             amd64        command-line network traffic analyzer
ii  tdb-tools                                 1.2.10-2                                   amd64        Trivial Database - bundled binaries
ii  telnet                                    0.17-36build2                              amd64        The telnet client
ii  thunar                                    1.4.0-1ubuntu2                             amd64        File Manager for Xfce
ii  thunar-archive-plugin                     0.3.0-4                                    amd64        Archive plugin for Thunar file manager
ii  thunar-data                               1.4.0-1ubuntu2                             all          Provides thunar documentation, icons and translations
ii  thunar-media-tags-plugin                  0.2.0-1                                    amd64        Media tags plugin for Thunar file manager
ii  thunar-volman                             0.8.0-1                                    amd64        Thunar extension for volumes management
ii  tightvncserver                            1.3.9-6.4                                  amd64        virtual network computing server software
ii  time                                      1.7-24                                     amd64        GNU time program for measuring CPU resource usage
ii  toshset                                   1.76-4                                     amd64        Access much of the Toshiba laptop hardware interface
ii  transmission-cli                          2.72-0ubuntu0.12.10.1                      amd64        lightweight BitTorrent client (command line programs)
ii  transmission-common                       2.72-0ubuntu0.12.10.1                      all          lightweight BitTorrent client (common files)
ii  transmission-daemon                       2.72-0ubuntu0.12.10.1                      amd64        lightweight BitTorrent client (daemon)
ii  tsconf                                    1.0-11                                     all          touch screen library common files
ii  ttf-dejavu-core                           2.33-2ubuntu1                              all          Vera font family derivate with additional characters
ii  ttf-dejavu-extra                          2.33-2ubuntu1                              all          Vera font family derivate with additional characters
ii  ttf-droid                                 20111207+git-1ubuntu1                      all          transitional dummy package
ii  ttf-freefont                              20120503-1                                 all          transitional dummy package
ii  ttf-indic-fonts-core                      1:0.5.11ubuntu1                            all          Core collection of free fonts for languages of India
ii  ttf-kacst-one                             5.0+svn11846-6                             all          transitional dummy package
ii  ttf-khmeros-core                          5.0-5ubuntu1                               all          transitional dummy package
ii  ttf-lao                                   0.0.20060226-8                             all          transitional dummy package
ii  ttf-liberation                            1.07.2-5                                   all          transitional dummy package
ii  ttf-lyx                                   2.0.3-3                                    all          transitional package
ii  ttf-opensymbol                            2:2.4.3+LibO3.4.4-0ubuntu1                 all          OpenSymbol TrueType font
ii  ttf-punjabi-fonts                         1:0.5.11ubuntu1                            all          Free TrueType fonts for the Punjabi language
ii  ttf-takao-pgothic                         003.02.01-5ubuntu1                         all          transitional dummy package
ii  ttf-thai-tlwg                             1:0.5.0-5                                  all          transitional dummy package
ii  ttf-ubuntu-font-family                    0.80-0ubuntu5                              all          Ubuntu Font Family, sans-serif typeface hinted for clarity
ii  ttf-unfonts-core                          1.0.3.is.1.0.2-080608-5ubuntu2             all          transitional dummy package
ii  ttf-wqy-microhei                          0.2.0-beta-1ubuntu1                        all          A droid derived Sans-Seri style CJK font
ii  tumbler                                   0.1.25-1ubuntu1                            amd64        D-Bus thumbnailing service
ii  tumbler-common                            0.1.25-1ubuntu1                            all          D-Bus thumbnailing service (common files)
ii  tzdata                                    2012e-0ubuntu2                             all          time zone and daylight-saving time data
ii  tzdata-java                               2012e-0ubuntu2                             all          time zone and daylight-saving time data for use by java runtimes
ii  ubufox                                    2.4.1-0ubuntu1                             all          transitional dummy package
ii  ubuntu-drivers-common                     1:0.2.71                                   amd64        Detect and install additional Ubuntu driver packages
ii  ubuntu-extras-keyring                     2010.09.27                                 all          GnuPG keys of the Ubuntu extras archive
ii  ubuntu-keyring                            2012.05.19                                 all          GnuPG keys of the Ubuntu archive
ii  ubuntu-minimal                            1.287                                      amd64        Minimal core of Ubuntu
ii  ubuntu-release-upgrader-core              1:0.190.1                                  all          manage release upgrades
ii  ubuntu-release-upgrader-gtk               1:0.190.1                                  all          manage release upgrades
ii  ubuntu-sso-client                         4.0.0-0ubuntu1                             all          Ubuntu Single Sign-On client
ii  ubuntu-standard                           1.287                                      amd64        The Ubuntu standard system
ii  ubuntu-system-service                     0.2.3                                      all          Dbus service to set various system-wide configurations
ii  ubuntuone-client                          4.0.0-0ubuntu1                             all          Ubuntu One client
ii  ucf                                       3.0025+nmu3                                all          Update Configuration File: preserve user changes to config files.
ii  udev                                      175-0ubuntu13                              amd64        rule-based device node and kernel event manager
ii  udisks                                    1.0.4-6                                    amd64        storage media interface
ii  udisks2                                   2.0.0-1                                    amd64        D-BUS service to access and manipulate storage devices
ii  ufw                                       0.33-0ubuntu2                              all          program for managing a Netfilter firewall
ii  unattended-upgrades                       0.79.3ubuntu4                              all          automatic installation of security upgrades
ii  unity-common                              6.8.0-0ubuntu2                             all          Common files for the Unity interface.
ii  unity-greeter                             12.10.4-0ubuntu5                           amd64        Unity Greeter
ii  unity-services                            6.8.0-0ubuntu2                             amd64        Services for the Unity interface
ii  unity-webapps-service                     2.4.1-0ubuntu2                             amd64        Service for Web Apps integration with the Unity desktop
ii  unzip                                     6.0-7ubuntu1                               amd64        De-archiver for .zip files
ii  update-inetd                              4.43                                       all          inetd configuration file updater
ii  update-manager                            1:0.174.3                                  all          GNOME application that manages apt updates
ii  update-manager-core                       1:0.174.3                                  all          manage release upgrades
ii  update-motd                               3.5-0ubuntu1                               all          superceded by pam_motd in libpam-modules
ii  update-notifier                           0.126                                      amd64        Daemon which notifies about package updates
ii  update-notifier-common                    0.126                                      all          Files shared between update-notifier and other packages
ii  upower                                    0.9.17-1build1                             amd64        abstraction for power management
ii  upstart                                   1.5-0ubuntu9                               amd64        event-based init daemon
ii  ureadahead                                0.100.0-12build1                           amd64        Read required files in advance
ii  usb-creator-common                        0.2.40ubuntu1                              amd64        create a startup disk using a CD or disc image (common files)
ii  usb-modeswitch                            1.2.3+repack0-1ubuntu3                     amd64        mode switching tool for controlling "flip flop" USB devices
ii  usb-modeswitch-data                       20120815-1                                 all          mode switching data for usb-modeswitch
ii  usbmuxd                                   1.0.8-1                                    amd64        USB multiplexor daemon for iPhone and iPod Touch devices
ii  usbutils                                  1:005-3                                    amd64        Linux USB utilities
ii  util-linux                                2.20.1-5.1ubuntu2                          amd64        Miscellaneous system utilities
ii  uuid-runtime                              2.20.1-5.1ubuntu2                          amd64        runtime components for the Universally Unique ID library
ii  vbetool                                   1.1-2ubuntu1                               amd64        run real-mode video BIOS code to alter hardware state
ii  vim                                       2:7.3.547-4ubuntu1                         amd64        Vi IMproved - enhanced vi editor
ii  vim-common                                2:7.3.547-4ubuntu1                         amd64        Vi IMproved - Common files
ii  vim-runtime                               2:7.3.547-4ubuntu1                         all          Vi IMproved - Runtime files
ii  vim-tiny                                  2:7.3.547-4ubuntu1                         amd64        Vi IMproved - enhanced vi editor - compact version
ii  vinagre                                   3.6.0-0ubuntu1                             amd64        remote desktop client for the GNOME Desktop
ii  wakeonlan                                 0.41-11                                    all          Sends 'magic packets' to wake-on-LAN enabled ethernet adapters
ii  wamerican                                 7.1-1                                      all          American English dictionary words for /usr/share/dict
ii  watershed                                 6build1                                    amd64        reduce superfluous executions of idempotent command
ii  wbritish                                  7.1-1                                      all          British English dictionary words for /usr/share/dict
ii  wdiff                                     1.1.2-1                                    amd64        Compares two files word by word
ii  wget                                      1.13.4-3ubuntu1                            amd64        retrieves files from the web
ii  whiptail                                  0.52.11-2ubuntu11                          amd64        Displays user-friendly dialog boxes from shell scripts
ii  wireless-crda                             1.16                                       amd64        Wireless Central Regulatory Domain Agent
ii  wireless-regdb                            2011.04.28-1ubuntu3                        all          wireless regulatory database
ii  wireless-tools                            30~pre9-8ubuntu1                           amd64        Tools for manipulating Linux Wireless Extensions
ii  wpasupplicant                             1.0-2ubuntu5                               amd64        client support for WPA and WPA2 (IEEE 802.11i)
ii  x-ttcidfont-conf                          32+nmu2                                    all          TrueType and CID fonts configuration for X
ii  x11-apps                                  7.7~2ubuntu1                               amd64        X applications
ii  x11-common                                1:7.7+1ubuntu4                             all          X Window System (X.Org) infrastructure
ii  x11-session-utils                         7.6+2build1                                amd64        X session utilities
ii  x11-utils                                 7.7~1ubuntu1                               amd64        X11 utilities
ii  x11-xfs-utils                             7.7~1                                      amd64        X font server utilities
ii  x11-xkb-utils                             7.7~1                                      amd64        X11 XKB utilities
ii  x11-xserver-utils                         7.7~3ubuntu1                               amd64        X server utilities
ii  x11proto-composite-dev                    1:0.4.2-2                                  all          X11 Composite extension wire protocol
ii  x11proto-core-dev                         7.0.23-1                                   all          X11 core wire protocol and auxiliary headers
ii  x11proto-damage-dev                       1:1.2.1-2                                  all          X11 Damage extension wire protocol
ii  x11proto-dri2-dev                         2.8-1                                      all          X11 DRI2 extension wire protocol
ii  x11proto-fixes-dev                        1:5.0-2ubuntu1                             all          X11 Fixes extension wire protocol
ii  x11proto-gl-dev                           1.4.16-1                                   all          X11 OpenGL extension wire protocol
ii  x11proto-input-dev                        2.2-1                                      all          X11 Input extension wire protocol
ii  x11proto-kb-dev                           1.0.6-2                                    all          X11 XKB extension wire protocol
ii  x11proto-randr-dev                        1.4.0+git20120101.is.really.1.4.0-0ubuntu1 all          X11 RandR extension wire protocol
ii  x11proto-render-dev                       2:0.11.1-2                                 all          X11 Render extension wire protocol
ii  x11proto-xext-dev                         7.2.1-1                                    all          X11 various extension wire protocol
ii  x11proto-xf86vidmode-dev                  2.3.1-2                                    all          X11 Video Mode extension wire protocol
ii  x11proto-xinerama-dev                     1.2.1-2                                    all          X11 Xinerama extension wire protocol
ii  xauth                                     1:1.0.7-1                                  amd64        X authentication utility
ii  xbitmaps                                  1.1.1-1                                    all          Base X bitmaps
ii  xbrlapi                                   4.4-5ubuntu3                               amd64        Access software for a blind person using a braille display - xbrlapi
ii  xchat                                     2.8.8-3ubuntu15                            amd64        IRC client for X similar to AmIRC
ii  xchat-common                              2.8.8-3ubuntu15                            all          Common files for X-Chat
ii  xcursor-themes                            1.0.3-1                                    all          Base X cursor themes
ii  xdg-user-dirs                             0.14-0ubuntu4                              amd64        tool to manage well known user directories
ii  xdg-user-dirs-gtk                         0.9-1ubuntu1                               amd64        tool to manage well known user directories (Gtk extension)
ii  xdg-utils                                 1.1.0~rc1-2ubuntu6                         all          desktop integration utilities from freedesktop.org
ii  xfburn                                    0.4.3-4ubuntu2                             amd64        CD-burner application for Xfce Desktop Environment
ii  xfce-keyboard-shortcuts                   4.10.0-1                                   all          xfce keyboard shortcuts configuration
ii  xfce4-appfinder                           4.10.0-1                                   amd64        Application finder for the Xfce4 Desktop Environment
ii  xfce4-cpugraph-plugin                     1.0.5-0ubuntu1                             amd64        CPU load graph plugin for the Xfce4 panel
ii  xfce4-dict                                0.6.0-5build2                              amd64        Dictionary plugin for Xfce4 panel
ii  xfce4-fsguard-plugin                      1.0.1-1                                    amd64        filesystem monitor plugin for the Xfce4 panel
ii  xfce4-indicator-plugin                    0.5.0-1ubuntu2                             amd64        plugin to display information from applications in the Xfce4 panel
ii  xfce4-mailwatch-plugin                    1.1.0-5build2                              amd64        mail watcher plugin for the Xfce4 panel
ii  xfce4-mixer                               1:4.8.0-3ubuntu2                           amd64        Xfce mixer application
ii  xfce4-mount-plugin                        0.6.4-1build1                              amd64        mount plugin for the Xfce4 panel
ii  xfce4-netload-plugin                      1.2.0-0ubuntu1                             amd64        network load monitor plugin for the Xfce4 panel
ii  xfce4-notes                               1.7.7-2ubuntu3                             amd64        Notes application for the Xfce4 desktop
ii  xfce4-notes-plugin                        1.7.7-2ubuntu3                             amd64        Notes plugin for the Xfce4 desktop
ii  xfce4-notifyd                             0.2.2-2ubuntu1                             amd64        simple, visually-appealing notification daemon for Xfce
ii  xfce4-panel                               4.10.0-1ubuntu2                            amd64        panel for Xfce4 desktop environment
ii  xfce4-places-plugin                       1.3.0-1ubuntu1                             amd64        quick access to folders, documents and removable media
ii  xfce4-power-manager                       1.2.0-1ubuntu1                             amd64        power manager for Xfce desktop
ii  xfce4-power-manager-data                  1.2.0-1ubuntu1                             all          power manager for Xfce desktop, arch-indep files
ii  xfce4-quicklauncher-plugin                1.9.4-9build2                              amd64        rapid launcher plugin for the Xfce4 panel
ii  xfce4-screenshooter                       1.8.1-1                                    amd64        screenshots utility for Xfce
ii  xfce4-session                             4.10.0-1ubuntu1                            amd64        Xfce4 Session Manager
ii  xfce4-settings                            4.10.0-1ubuntu2                            amd64        graphical application for managing Xfce settings
ii  xfce4-smartbookmark-plugin                0.4.4-1ubuntu3                             amd64        search the web via the Xfce4 panel
ii  xfce4-systemload-plugin                   1:1.1.1-1ubuntu1                           amd64        system load monitor plugin for the Xfce4 panel
ii  xfce4-taskmanager                         1.0.0-2                                    amd64        process manager for the Xfce4 Desktop Environment
ii  xfce4-terminal                            0.4.8-1ubuntu3                             amd64        Xfce terminal emulator
ii  xfce4-verve-plugin                        1.0.0-1build2                              amd64        Verve (command line) plugin for Xfce panel
ii  xfce4-volumed                             0.1.13-2ubuntu1                            amd64        volume keys daemon
ii  xfce4-weather-plugin                      0.8.1-0ubuntu1                             amd64        weather information plugin for the Xfce4 panel
ii  xfconf                                    4.10.0-1                                   amd64        utilities for managing settings in Xfce
ii  xfdesktop4                                4.10.0-1ubuntu1                            amd64        xfce desktop background, icons and root menu manager
ii  xfdesktop4-data                           4.10.0-1ubuntu1                            all          xfce desktop background, icons and root menu (common files)
ii  xfonts-base                               1:1.0.3                                    all          standard fonts for X
ii  xfonts-encodings                          1:1.0.4-1ubuntu1                           all          Encodings for X.Org fonts
ii  xfonts-scalable                           1:1.0.3-1                                  all          scalable fonts for X
ii  xfonts-utils                              1:7.7~1                                    amd64        X Window System font utility programs
ii  xfprint4                                  4.6.1-3ubuntu1                             amd64        Printer GUI for Xfce4
ii  xfwm4                                     4.10.0-2ubuntu1                            amd64        window manager of the Xfce project
ii  xfwm4-themes                              4.10.0-1                                   all          Theme files for xfwm4
ii  xinit                                     1.3.2-1                                    amd64        X server initialisation tool
ii  xinput                                    1.6.0-1                                    amd64        Runtime configuration and test of XInput devices
ii  xkb-data                                  2.5-1ubuntu7                               all          X Keyboard Extension (XKB) configuration data
ii  xml-core                                  0.13+nmu1                                  all          XML infrastructure and XML catalog file support
ii  xorg                                      1:7.7+1ubuntu4                             amd64        X.Org X Window System
ii  xorg-docs-core                            1:1.6-1ubuntu2                             all          Core documentation for the X.org X Window System
ii  xorg-sgml-doctools                        1:1.10-1                                   all          Common tools for building X.Org SGML documentation
ii  xscreensaver                              5.15-2ubuntu1                              amd64        Automatic screensaver for X
ii  xscreensaver-data                         5.15-2ubuntu1                              amd64        data files to be shared among screensaver frontends
ii  xscreensaver-gl                           5.15-2ubuntu1                              amd64        GL(Mesa) screen hacks for xscreensaver
ii  xserver-common                            2:1.13.0-0ubuntu6                          all          common files used by various X servers
ii  xserver-xorg                              1:7.7+1ubuntu4                             amd64        X.Org X server
ii  xserver-xorg-core                         2:1.13.0-0ubuntu6                          amd64        Xorg X server - core server
ii  xserver-xorg-input-all                    1:7.7+1ubuntu4                             amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                  1:2.7.3-0ubuntu2                           amd64        X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse                  1:1.7.2-2build1                            amd64        X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics              1.6.2-1ubuntu5                             amd64        Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse                1:12.9.0-0ubuntu3                          amd64        X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom                  1:0.17.0-0ubuntu2                          amd64        X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                    1:7.7+1ubuntu4                             amd64        X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati                    1:6.99.99~git20120913.8637f772-0ubuntu1    amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus                 1:1.5.1-0ubuntu2                           amd64        X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev                  1:0.4.3-0ubuntu1                           amd64        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-intel                  2:2.20.9-0ubuntu2                          amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64                 6.9.3-0ubuntu1                             amd64        X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                    1:1.6.2-0ubuntu1                           amd64        X.Org X server -- MGA display driver
ii  xserver-xorg-video-modesetting            0.5.0-0ubuntu1                             amd64        X.Org X server -- Generic modesetting driver
ii  xserver-xorg-video-neomagic               1:1.2.7-0ubuntu1                           amd64        X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau                1:1.0.2-0ubuntu3                           amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome             1:0.3.1-0ubuntu1                           amd64        X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                    0.1.0-0ubuntu1                             amd64        X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128                   6.9.1-0ubuntu1                             amd64        X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon                 1:6.99.99~git20120913.8637f772-0ubuntu1    amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                     1:0.6.5-0ubuntu1                           amd64        X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage                 1:2.3.6-0ubuntu1                           amd64        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion          1:1.7.7-0ubuntu1                           amd64        X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                    1:0.10.7-0ubuntu1                          amd64        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb                 1:0.9.6-0ubuntu1                           amd64        X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                   1:1.4.5-0ubuntu1                           amd64        X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident                1:1.3.6-0ubuntu2                           amd64        X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa                   1:2.3.2-0ubuntu1                           amd64        X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware                 1:12.0.2+git.e5ac80d8-0ubuntu1             amd64        X.Org X server -- VMware display driver
ii  xsltproc                                  1.1.26-14                                  amd64        XSLT 1.0 command line processor
ii  xterm                                     278-1ubuntu2                               amd64        X terminal emulator
ii  xtrans-dev                                1.2.7-1                                    all          X transport library (development files)
ii  xubuntu-artwork                           12.10.2                                    all          Xubuntu themes and artwork
ii  xubuntu-default-settings                  12.10.7                                    all          default settings for the Xubuntu desktop
ii  xubuntu-docs                              12.10.2                                    all          xubuntu documentation
ii  xubuntu-icon-theme                        12.10.2                                    all          Xubuntu icon theme
ii  xubuntu-wallpapers                        12.10.2                                    all          Xubuntu wallpapers
ii  xul-ext-ubufox                            2.4.1-0ubuntu1                             all          Ubuntu-specific configuration defaults and apt support for Firefox
ii  xz-utils                                  5.1.1alpha+20120614-1                      amd64        XZ-format compression utilities
ii  yelp                                      3.6.0-0ubuntu1                             amd64        Help browser for GNOME
ii  yelp-xsl                                  3.6.0-0ubuntu1                             all          XSL stylesheets for the yelp help browser
ii  zeitgeist-core                            0.9.5-0ubuntu1                             amd64        event logging framework - engine
ii  zenity                                    3.4.0-2                                    amd64        Display graphical dialog boxes from shell scripts
ii  zenity-common                             3.4.0-2                                    all          Display graphical dialog boxes from shell scripts (common files)
ii  zip                                       3.0-6                                      amd64        Archiver for .zip files
ii  zlib1g:amd64                              1:1.2.7.dfsg-13                            amd64        compression library - runtime
ii  zlib1g-dev:amd64                          1:1.2.7.dfsg-13                            amd64        compression library - development
```

Thanks,

r

---

### Post by 2F4U on 2012-10-27
What mirror are you using? However, it is also my experience that Xubuntu hasn't received many updates since it has been released.

---

### Post by PaulW2U on 2012-10-27
> **robothebobo said:**
> This might seem like a silly question, but since updating to xubuntu 12.10 from 12.04, I have had 0 updates required for more than a week.

A lot of the updates have been going into the proposed repository for testing. In due course they will be moved to the main repositories and be available for updating your installation. However, you should have had some security updates relating to java, Firefox and Thunderbird.

As 2F4U has asked, what mirror are you using? It may not be as up to date as it should be.

[http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/) is a useful site that tracks the updates for each release and which repositories they are initially uploaded to.

---

### Post by vasa1 on 2012-10-27
I don't know if this is an official site or not, but you could look here:
[http://www.ubuntuupdates.org](http://www.ubuntuupdates.org)

---

### Post by MadmanRB on 2012-10-27
Ubuntu 12.10 is still new so a lack of updates right now is no big shock, give it time and AI bet updates will be a plenty.

---

### Post by robothebobo on 2012-10-28
> **2F4U said:**
> What mirror are you using? However, it is also my experience that Xubuntu hasn't received many updates since it has been released.

Here is my /etc/apt/sources.list. It looks like it's pointing directly at Ubuntu's servers, not at any mirror? 

```

# deb cdrom:[Xubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
# deb http://archive.canonical.com/ lucid partner
# deb-src http://archive.canonical.com/ lucid partner
```

---

### Post by howefield on 2012-10-28
I installed (fresh) on the 26th and have updates waiting for firefox, I'd expect you would have at least those.

FWIW, my source.list looks like this.

```
# deb cdrom:[Xubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.1)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal universe
deb http://gb.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
```

---

### Post by robothebobo on 2012-10-28
> **howefield said:**
> I installed (fresh) on the 26th and have updates waiting for firefox, I'd expect you would have at least those.

FWIW, my source.list looks like this.



Woah! I think I see the problem, from comparing yours and mine. I have no *release***-updates** entries in my source.list!!

For example, for your Universe repository, you have:

```

deb http://gb.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal universe
deb http://gb.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ quantal-updates universe
```

and I have only:

```
deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
```


I bet that's the problem. My guess is that 'quantal' gives you the version that shipped with the first release of 12.10 and 'quantal-updates' gives incremental updates from that... is that correct?

Anyhow, I will go update this and see if it fixes the issue.

(the other question, though, is how on earth did I lose those entries? Bug in the distribution upgrade mechanism?)

-R

---

### Post by robothebobo on 2012-10-28
Success! I added the 'quantal-updates' entries to match howefield's, and discovered that I was also missing the entire 'security' block that he had (shown below) and lo and behold, I am getting updates!

I still am totally perplexed at how I lost this in the upgrade from 12.04 to 12.10 though...


This was the 'security' stuff that was also missing from mine:
```

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse
```


Thanks howefield for posting yours - I didn't have anything to compare to before.

---

### Post by howefield on 2012-10-28
> **robothebobo said:**
> Thanks howefield for posting yours - I didn't have anything to compare to before.

You're very welcome, glad you got it sussed out.

It's one reason why I prefer clean installs to upgrades.

---

