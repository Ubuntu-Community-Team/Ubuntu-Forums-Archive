---
title: "meta package"
date: 2008-05-05
forum: Packaging and Compiling Programs
---

### Post by songshu on 2008-05-05
dear all,

i'm trying to build some meta packages but get some erors if i install more then one.

i basically did the following

```
mkdir laoshu-desktop_8.04.1_i386
mkdir laoshu-desktop_8.04.1_i386/DEBIAN
nano laoshu-desktop_8.04.1_i386/DEBIAN/control
```

```
Package: laoshu-desktop
Source: laoshu-meta
Version: 1.0
Architecture: i386
Maintainer: randall <randall@songshu.org>
Installed-Size: 40
Depends: acpi, acpi-support, acpid, alsa-base, alsa-utils, anacron, mozilla-plugin-vlc, apmd, avahi-daemon, bc, ca-certificates, cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gutenprint, dbus, dc, doc-base, foomatic-db, foomatic-db-engine, foomatic-filters, gdebi, gdm, genisoimage, ghostscript-x, gnome-app-install, gnome-mount, gnome-system-tools, gtk2-engines, gtk2-engines-murrine, gtk2-engines-pixbuf, gtk2-engines-ubuntulooks, gtk2-engines-xfce, hal, hotkey-setup, language-selector, lftp, libgl1-mesa-glx, libglib2.0-data, libglut3, libsasl2-modules, libxp6, openprinting-ppds, pnm2ppa, powermanagement-interface, readahead, screen, scrollkeeper, smbclient, software-properties-gtk, synaptic, tango-icon-theme, tango-icon-theme-common, thunar, thunar-archive-plugin, thunar-media-tags-plugin, thunar-thumbnailers, thunar-volman, ttf-bitstream-vera, ttf-dejavu-core, ttf-freefont, ubuntu-artwork, unzip, update-manager, usplash, vim-runtime, x-ttcidfont-conf, xfce4-mcs-plugins, xfce4-mcs-plugins-extra, xfce4-mixer, xfce4-panel, xfce4-session, xfce4-terminal, xfce4-utils, xfdesktop4, xfwm4, xfwm4-themes, xkb-data, xorg, xterm, zenity, zip, app-install-data-commercial, apport-gtk, avahi-autoipd, bluez-cups, bluez-utils, bogofilter, brasero, cdparanoia, cups-pdf, displayconfig-gtk, dvd+rw-tools,  file-roller, firefox, foo2zjs, foomatic-db-hpijs, fortune-mod, gcalctool, gcc, gimp, gnome-accessibility-themes, gnome-games, gnome-power-manager, gnome-screensaver, gnome-system-monitor, gucharmap, hal-cups-utils, hplip, jockey-gtk, laptop-detect, libgl1-mesa-dri, libgnome2-perl, libgoffice-gtk-0-6, libnss-mdns, linux-headers-generic, make, min12xxw, mousepad, mozilla-thunderbird, network-manager-gnome, notification-daemon, onboard, orage, pidgin, pidgin-otr, powernowd, pxljr, python-exo, gthumb, scim, scim-gtk2-immodule, scim-tables-additional, screensaver-default-images, splix, system-config-printer-gnome, transmission-gtk, ttf-arabeyes, ttf-arphic-uming, ttf-indic-fonts-core, ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts, ttf-thai-tlwg, ttf-unfonts-core, ubufox, update-notifier, wodim, wvdial, xcursor-themes, xdg-utils, xfce4-appfinder, xfce4-battery-plugin, xfce4-clipman-plugin, xfce4-cpugraph-plugin, xfce4-dict-plugin, xfce4-fsguard-plugin, xfce4-governor-plugin, xfce4-mailwatch-plugin, xfce4-mount-plugin, xfce4-netload-plugin, xfce4-notes-plugin, xfce4-places-plugin, xfce4-quicklauncher-plugin, xfce4-screenshooter-plugin, xfce4-smartbookmark-plugin, xfce4-systemload-plugin, xfce4-verve-plugin, xfce4-weather-plugin, xfce4-xkb-plugin, xfprint4, xscreensaver-data, xscreensaver-gl, openoffice.org, openoffice.org-gtk, openoffice.org-style-tango, lightning-extension, ekiga, inkscape, gftp, exaile, catfish
Section: metapackages
Priority: optional
Description: LaoShu desktop system
 This package depends on all of the packages in the LaoShu desktop system
 .
 It is safe to remove this package if some of the desktop system packages are
 not desired.

```

```
dpkg -b laoshu-desktop_8.04.1_i386
```

this installs just fine, but if i create another one like this i get the following error on install

```
dpkg: error processing /var/cache/apt/laoshu-restricted-extras_1.0_i386.deb (--unpack):
trying to overwrite '/.deb', which is also in package laoshu-desktop

```



i get the slight feeling that i miss something in the directory structure, but no clue what it could be.

p.s.

i noticed the mention of equivs in some older posts, but the package itself says its depreciated.

thanks

---

