---
title: "G++ invoking problems..."
date: 2013-04-14
forum: New to Ubuntu
---

### Post by mna0307 on 2013-04-14
i have installed ubuntu 12.10 for windows 8 64 bit ... , g++ is not installed,,,isnot it supposed to be by defualt insalled when i m using ubuntu 12.10 as virtual os on windows 8 using vmware as i ws unable to install on windows 8....when i check g++ --version, it says.....

The program 'g++' can be found in the following packages:
* g++
* pentium-builder
Try: sudo apt-get install <selected package>

when i try to install it using sudo apt-get install g++......the output it gives is as under:---------------
Code:

```
libpaper1 is already the newest version.python-gobject is already the newest version.libsigc++-2.0-0c2a is already the newest version.libnm-gtk0 is already the newest version.gvfs is already the newest version.libglib2.0-bin is already the newest version.libglibmm-2.4-1c2a is already the newest version.printer-driver-sag-gdi is already the newest version.gnomine is already the newest version.libgnutls26 is already the newest version.xserver-xorg-video-mga is already the newest version.libgpm2 is already the newest version.gzip is already the newest version.dpkg is already the newest version.grub-pc is already the newest version.pkg-config is already the newest version.appmenu-gtk is already the newest version.gir1.2-launchpad-integration-3.0 is already the newest version.ginn is already the newest version.firefox-gnome-support is already the newest version.liblocale-gettext-perl is already the newest version.launchpad-integration is already the newest version.ubuntu-keyring is already the newest version.glib-networking-common is already the newest version.libcanberra-gtk0 is already the newest version.gir1.2-freedesktop is already the newest version.python-gst0.10 is already the newest version.linux-generic-pae is already the newest version.gksu is already the newest version.software-center-aptdaemon-plugins is already the newest version.gstreamer0.10-pulseaudio is already the newest version.gnome-online-accounts is already the newest version.libcap-ng0 is already the newest version.gir1.2-wnck-3.0 is already the newest version.libproxy1-plugin-gsettings is already the newest version.totem-plugins is already the newest version.gnome-user-share is already the newest version.gir1.2-glib-2.0 is already the newest version.gcc is already the newest version.ghostscript is already the newest version.python-xdg is already the newest version.gnome-games-data is already the newest version.xserver-xorg-video-s3 is already the newest version.lightdm is already the newest version.appmenu-gtk3 is already the newest version.iputils-ping is already the newest version.python-ubuntuone-storageprotocol is already the newest version.gir1.2-gtk-2.0 is already the newest version.xserver-xorg-video-trident is already the newest version.libgssapi3-heimdal is already the newest version.python-zeitgeist is already the newest version.libwmf0.2-7-gtk is already the newest version.xserver-xorg-video-intel is already the newest version.perl is already the newest version.gir1.2-gstreamer-0.10 is already the newest version.indicator-messages is already the newest version.system-config-printer-common is already the newest version.fonts-thai-tlwg is already the newest version.xserver-xorg-video-mach64 is already the newest version.libnm-glib4 is already the newest version.network-manager is already the newest version.libcupscgi1 is already the newest version.libgtkmm-3.0-1 is already the newest version.gwibber-service-twitter is already the newest version.gnome-desktop3-data is already the newest version.language-pack-gnome-en is already the newest version.libzeitgeist-1.0-1 is already the newest version.gnome-screensaver is already the newest version.libgtkspell-3-0 is already the newest version.gir1.2-unity-5.0 is already the newest version.fonts-tlwg-norasi is already the newest version.libtag1c2a is already the newest version.libjbig2dec0 is already the newest version.libgphoto2-2 is already the newest version.gstreamer0.10-gconf is already the newest version.python-imaging is already the newest version.libutouch-grail1 is already the newest version.rhythmbox-plugin-magnatune is already the newest version.python-debtagshw is already the newest version.libgupnp-1.0-4 is already the newest version.gconf2 is already the newest version.fonts-takao-pgothic is already the newest version.guile-1.8-libs is already the newest version.libgoa-1.0-common is already the newest version.gstreamer0.10-plugins-base is already the newest version.libgphoto2-l10n is already the newest version.libdbusmenu-gtk4 is already the newest version.libpackagekit-glib2-14 is already the newest version.libgnome-keyring0 is already the newest version.xserver-xorg-input-all is already the newest version.network-manager-pptp-gnome is already the newest version.fontconfig-config is already the newest version.libwpg-0.2-2 is already the newest version.dconf-gsettings-backend is already the newest version.gir1.2-gdkpixbuf-2.0 is already the newest version.xserver-xorg-input-mouse is already the newest version.remmina-plugin-rdp is already the newest version.light-themes is already the newest version.libfreerdp-plugins-standard is already the newest version.libgtk2.0-bin is already the newest version.firefox is already the newest version.libreoffice-gtk is already the newest version.fonts-tlwg-sawasdee is already the newest version.liblaunchpad-integration-3.0-1 is already the newest version.gcc-4.6-base is already the newest version.libglewmx1.6 is already the newest version.libc6 is already the newest version.language-selector-common is already the newest version.ghostscript-cups is already the newest version.gir1.2-dbusmenu-glib-0.4 is already the newest version.rhythmbox-plugin-zeitgeist is already the newest version.gvfs-daemons is already the newest version.gir1.2-gnomekeyring-1.0 is already the newest version.compizconfig-backend-gconf is already the newest version.grub2-common is already the newest version.zeitgeist-datahub is already the newest version.gstreamer0.10-plugins-good is already the newest version.libnm-glib-vpn1 is already the newest version.libpng12-0 is already the newest version.gir1.2-gtk-3.0 is already the newest version.xserver-xorg-video-geode is already the newest version.gwibber-service is already the newest version.compiz-gnome is already the newest version.libgee2 is already the newest version.libgmp10 is already the newest version.gir1.2-vte-2.90 is already the newest version.xdiagnose is already the newest version.update-manager is already the newest version.rhythmbox-plugin-cdrecorder is already the newest version.gstreamer0.10-x is already the newest version.libgucharmap-2-90-7 is already the newest version.rsyslog is already the newest version.libglew1.6 is already the newest version.powermgmt-base is already the newest version.network-manager-gnome is already the newest version.libvisual-0.4-plugins is already the newest version.iputils-arping is already the newest version.pulseaudio is already the newest version.gvfs-fuse is already the newest version.xorg-docs-core is already the newest version.libgnome-bluetooth8 is already the newest version.xserver-xorg-video-ati is already the newest version.xserver-xorg-video-siliconmotion is already the newest version.gir1.2-appindicator3-0.1 is already the newest version.gstreamer0.10-alsa is already the newest version.python-gconf is already the newest version.gstreamer0.10-tools is already the newest version.libgphoto2-port0 is already the newest version.libglib2.0-0 is already the newest version.gir1.2-peas-1.0 is already the newest version.python-configglue is already the newest version.gnome-session-bin is already the newest version.libgomp1 is already the newest version.usb-creator-gtk is already the newest version.libgnome-desktop-3-2 is already the newest version.software-properties-gtk is already the newest version.libcupsimage2 is already the newest version.growisofs is already the newest version.gnome-power-manager is already the newest version.0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
it does not instal, rather says about so many packages that these are newest version,,but at the end says 0 installed, 0 upgraded....
```.what to do???how to install g++...i need it to compile and run c++ programs..plz help

---

### Post by wildmanne39 on 2013-04-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use normal fonts.
Thanks

---

### Post by wickedpuppy on 2013-04-14
strange , the same thing done on my machine returns different result. Nothing about libpaper1 .. can you do a screenshot and put it on imagebin?

---

### Post by prshah on 2013-04-14
> **mna0307 said:**
> i have installed ubuntu 12.10 for windows 8 64 bit ... , g++ is not installed<snip>
what to do???how to install g++...i need it to compile and run c++ programs..plz help

Please install build-essential to install a complete development environment, including gcc/g++.

```
sudo apt-get update && sudo apt-get install build-essential
```

---

