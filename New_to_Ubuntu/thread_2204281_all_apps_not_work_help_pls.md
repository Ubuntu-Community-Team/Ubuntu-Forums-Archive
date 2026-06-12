---
title: "all apps not work help pls"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by alex150 on 2014-02-07
Hi guys, i have bought a ubuntu vps server.
installed with 
sudo apt-get install ubuntu-desktop 

and its work. but i need ubuntu to start firefox or other apps, i click trough the menu and try to start the applications no application works. 
its only load and nothing happend. wtf?!? 
terminal not work, and other apps not work. 
i can do nothing at the settings.. see:
 [IMG]http://www7.pic-upload.de/07.02.14/qxzauc1u75sa.png[/IMG]

[IMG]http://www7.pic-upload.de/07.02.14/zoju8f1zdmhw.png[/IMG]

---

### Post by tgalati4 on 2014-02-07
Sounds like you are missing some pieces.

Open a terminal and review:

```
apt-cache depends ubuntu-desktop
```

I've pasted a typical output (only the recommends, since the "depends" are presumably already loaded):

```
Recommends: acpi-support
  Recommends: activity-log-manager-control-center
  Recommends: aisleriot
  Recommends: app-install-data-partner
  Recommends: apport-gtk
  Recommends: avahi-autoipd
  Recommends: avahi-daemon
    avahi-daemon:i386
  Recommends: bluez
    bluez:i386
  Recommends: bluez-alsa
  Recommends: bluez-cups
  Recommends: bluez-gstreamer
  Recommends: branding-ubuntu
  Recommends: brasero
  Recommends: brltty
  Recommends: cups
    cups:i386
  Recommends: cups-bsd
    cups-bsd:i386
  Recommends: cups-client
    cups-client:i386
  Recommends: deja-dup
  Recommends: empathy
  Recommends: example-content
  Recommends: **firefox**
  Recommends: **firefox-gnome-support**
  Recommends: fonts-kacst-one
  Recommends: fonts-khmeros-core
  Recommends: fonts-lao
  Recommends: fonts-liberation
  Recommends: fonts-lklug-sinhala
  Recommends: fonts-nanum
  Recommends: fonts-sil-abyssinica
  Recommends: fonts-sil-padauk
  Recommends: fonts-takao-pgothic
  Recommends: fonts-thai-tlwg
  Recommends: fonts-tibetan-machine
  Recommends: gcc
  Recommends: gnome-accessibility-themes
  Recommends: gnome-bluetooth
  Recommends: gnome-disk-utility
  Recommends: gnome-mahjongg
  Recommends: gnome-orca
  Recommends: gnome-screensaver
  Recommends: gnome-sudoku
  Recommends: gnomine
  Recommends: gvfs-fuse
  Recommends: gwibber
  Recommends: hplip
  Recommends: ibus
    ibus:i386
  Recommends: ibus-gtk3
  Recommends: ibus-pinyin
  Recommends: ibus-pinyin-db-android
  Recommends: ibus-table
  Recommends: im-switch
    im-config
  Recommends: kerneloops-daemon
  Recommends: landscape-client-ui-install
  Recommends: laptop-detect
  Recommends: libgail-common
  Recommends: libnss-mdns
  Recommends: libpam-gnome-keyring
  Recommends: libproxy1-plugin-gsettings
  Recommends: libproxy1-plugin-networkmanager
  Recommends: libqt4-sql-sqlite
  Recommends: libreoffice-calc
  Recommends: libreoffice-gnome
  Recommends: libreoffice-help-en-us
  Recommends: libreoffice-impress
  Recommends: libreoffice-math
  Recommends: libreoffice-ogltrans
  Recommends: libreoffice-pdfimport
  Recommends: libreoffice-presentation-minimizer
  Recommends: libreoffice-presenter-console
  Recommends: libreoffice-style-human
  Recommends: libreoffice-writer
  Recommends: libwmf0.2-7-gtk
  Recommends: linux-headers-generic
  Recommends: make
  Recommends: mousetweaks
  Recommends: nautilus-share
  Recommends: network-manager-gnome
  Recommends: network-manager-pptp
  Recommends: network-manager-pptp-gnome
  Recommends: onboard
  Recommends: overlay-scrollbar
  Recommends: pcmciautils
  Recommends: plymouth-theme-ubuntu-logo
  Recommends: policykit-desktop-privileges
  Recommends: printer-driver-c2esp
  Recommends: printer-driver-foo2zjs
  Recommends: printer-driver-min12xxw
  Recommends: printer-driver-ptouch
  Recommends: printer-driver-pxljr
  Recommends: printer-driver-sag-gdi
  Recommends: printer-driver-splix
  Recommends: pulseaudio-module-bluetooth
  Recommends: pulseaudio-module-gconf
  Recommends: pulseaudio-module-x11
  Recommends: python3-aptdaemon.pkcompat
  Recommends: qt-at-spi
  Recommends: remmina
  Recommends: rhythmbox
  Recommends: rhythmbox-plugin-magnatune
  Recommends: rhythmbox-ubuntuone
  Recommends: shotwell
  Recommends: simple-scan
  Recommends: sni-qt
  Recommends: speech-dispatcher
  Recommends: telepathy-idle
  Recommends: thunderbird
  Recommends: thunderbird-gnome-support
  Recommends: totem
  Recommends: totem-mozilla
  Recommends: transmission-gtk
  Recommends: ttf-indic-fonts-core
  Recommends: ttf-punjabi-fonts
  Recommends: ttf-ubuntu-font-family
  Recommends: ttf-wqy-microhei
  Recommends: ubuntu-docs
  Recommends: ubuntuone-client-gnome
  Recommends: ubuntuone-control-panel-qt
  Recommends: unity-webapps-common
  Recommends: usb-creator-gtk
  Recommends: vino
  Recommends: whoopsie
  Recommends: xcursor-themes
  Recommends: xdg-utils
  **Recommends: xul-ext-ubufox**
 ** Recommends: xul-ext-unity**
```

Stuff in Bold is probably needed for Firefox to run correctly.

---

### Post by alex150 on 2014-02-07
```
 Depends: alsa-base  Depends: alsa-utils
    alsa-utils:i386
  Depends: anacron
  Depends: at-spi2-core
    at-spi2-core:i386
  Depends: baobab
  Depends: bc
  Depends: ca-certificates
  Depends: checkbox-qt
  Depends: dmz-cursor-theme
  Depends: doc-base
  Depends: eog
  Depends: evince
  Depends: file-roller
  Depends: fonts-freefont-ttf
  Depends: foomatic-db-compressed-ppds
  Depends: foomatic-filters
  Depends: gcalctool
  Depends: gedit
  Depends: genisoimage
  Depends: ghostscript-x
  Depends: gnome-control-center
  Depends: gnome-font-viewer
  Depends: gnome-media
  Depends: gnome-menus
  Depends: gnome-power-manager
  Depends: gnome-screenshot
  Depends: gnome-session
  Depends: gnome-session-canberra
  Depends: gnome-system-log
  Depends: gnome-system-monitor
  Depends: gnome-terminal
  Depends: gstreamer0.10-alsa
  Depends: gstreamer0.10-plugins-base-apps
  Depends: gstreamer0.10-pulseaudio
  Depends: gucharmap
  Depends: gvfs-bin
    gvfs-bin:i386
  Depends: inputattach
  Depends: language-selector-gnome
  Depends: libatk-adaptor
  Depends: libgd2-xpm
  Depends: libnotify-bin
  Depends: libpam-ck-connector
  Depends: libpam-xdg-support
  Depends: libsasl2-modules
  Depends: libxp6
  Depends: lightdm
  Depends: nautilus
  Depends: nautilus-sendto
  Depends: notify-osd
  Depends: openprinting-ppds
  Depends: printer-driver-pnm2ppa
  Depends: pulseaudio
    pulseaudio:i386
  Depends: rfkill
  Depends: seahorse
  Depends: software-center
  Depends: software-properties-gtk
  Depends: ssh-askpass-gnome
  Depends: system-config-printer-gnome
  Depends: ttf-dejavu-core
  Depends: ubuntu-artwork
  Depends: ubuntu-drivers-common
  Depends: ubuntu-extras-keyring
  Depends: ubuntu-release-upgrader-gtk
  Depends: ubuntu-settings
  Depends: ubuntu-sounds
  Depends: unity
  Depends: unity-greeter
  Depends: unzip
    unzip:i386
  Depends: update-manager
  Depends: update-notifier
  Depends: wireless-tools
    wireless-tools:i386
  Depends: wpasupplicant
    wpasupplicant:i386
  Depends: xdg-user-dirs
  Depends: xdg-user-dirs-gtk
  Depends: xdiagnose
  Depends: xkb-data
  Depends: xorg
  Depends: xterm
    xterm:i386
  Depends: yelp
  Depends: zenity
    zenity:i386
  Depends: zip
    zip:i386
  Recommends: acpi-support
  Recommends: activity-log-manager-control-center
  Recommends: aisleriot
  Recommends: app-install-data-partner
  Recommends: apport-gtk
  Recommends: avahi-autoipd
  Recommends: avahi-daemon
    avahi-daemon:i386
  Recommends: bluez
    bluez:i386
  Recommends: bluez-alsa
  Recommends: bluez-cups
  Recommends: bluez-gstreamer
  Recommends: branding-ubuntu
  Recommends: brasero
  Recommends: brltty
  Recommends: cups
    cups:i386
  Recommends: cups-bsd
    cups-bsd:i386
  Recommends: cups-client
    cups-client:i386
  Recommends: deja-dup
  Recommends: empathy
  Recommends: example-content
  Recommends: firefox
  Recommends: firefox-gnome-support
  Recommends: fonts-kacst-one
  Recommends: fonts-khmeros-core
  Recommends: fonts-lao
  Recommends: fonts-liberation
  Recommends: fonts-lklug-sinhala
  Recommends: fonts-nanum
  Recommends: fonts-sil-abyssinica
  Recommends: fonts-sil-padauk
  Recommends: fonts-takao-pgothic
  Recommends: fonts-thai-tlwg
  Recommends: fonts-tibetan-machine
  Recommends: gcc
  Recommends: gnome-accessibility-themes
  Recommends: gnome-bluetooth
  Recommends: gnome-disk-utility
  Recommends: gnome-mahjongg
  Recommends: gnome-orca
  Recommends: gnome-screensaver
  Recommends: gnome-sudoku
  Recommends: gnomine
  Recommends: gvfs-fuse
  Recommends: gwibber
  Recommends: hplip
  Recommends: ibus
    ibus:i386
  Recommends: ibus-gtk3
  Recommends: ibus-pinyin
  Recommends: ibus-pinyin-db-android
  Recommends: ibus-table
  Recommends: im-switch
    im-config
  Recommends: kerneloops-daemon
  Recommends: landscape-client-ui-install
  Recommends: laptop-detect
  Recommends: libgail-common
  Recommends: libnss-mdns
  Recommends: libpam-gnome-keyring
  Recommends: libproxy1-plugin-gsettings
  Recommends: libproxy1-plugin-networkmanager
  Recommends: libqt4-sql-sqlite
  Recommends: libreoffice-calc
  Recommends: libreoffice-gnome
  Recommends: libreoffice-help-en-us
  Recommends: libreoffice-impress
  Recommends: libreoffice-math
  Recommends: libreoffice-ogltrans
  Recommends: libreoffice-pdfimport
  Recommends: libreoffice-presentation-minimizer
  Recommends: libreoffice-presenter-console
  Recommends: libreoffice-style-human
  Recommends: libreoffice-writer
  Recommends: libwmf0.2-7-gtk
  Recommends: linux-headers-generic
  Recommends: make
  Recommends: mousetweaks
  Recommends: nautilus-share
  Recommends: network-manager-gnome
  Recommends: network-manager-pptp
  Recommends: network-manager-pptp-gnome
  Recommends: onboard
  Recommends: overlay-scrollbar
  Recommends: pcmciautils
  Recommends: plymouth-theme-ubuntu-logo
  Recommends: policykit-desktop-privileges
  Recommends: printer-driver-c2esp
  Recommends: printer-driver-foo2zjs
  Recommends: printer-driver-min12xxw
  Recommends: printer-driver-ptouch
  Recommends: printer-driver-pxljr
  Recommends: printer-driver-sag-gdi
  Recommends: printer-driver-splix
  Recommends: pulseaudio-module-bluetooth
  Recommends: pulseaudio-module-gconf
  Recommends: pulseaudio-module-x11
  Recommends: python3-aptdaemon.pkcompat
  Recommends: qt-at-spi
  Recommends: remmina
  Recommends: rhythmbox
  Recommends: rhythmbox-plugin-magnatune
  Recommends: rhythmbox-ubuntuone
  Recommends: shotwell
  Recommends: simple-scan
  Recommends: sni-qt
  Recommends: speech-dispatcher
  Recommends: telepathy-idle
  Recommends: thunderbird
  Recommends: thunderbird-gnome-support
  Recommends: totem
  Recommends: totem-mozilla
  Recommends: transmission-gtk
  Recommends: ttf-indic-fonts-core
  Recommends: ttf-punjabi-fonts
  Recommends: ttf-ubuntu-font-family
  Recommends: ttf-wqy-microhei
  Recommends: ubuntu-docs
  Recommends: ubuntuone-client-gnome
  Recommends: ubuntuone-control-panel-qt
  Recommends: unity-webapps-common
  Recommends: usb-creator-gtk
  Recommends: vino
  Recommends: whoopsie
  Recommends: xcursor-themes
  Recommends: xdg-utils
  Recommends: xul-ext-ubufox
  Recommends: xul-ext-unity
  Conflicts: ubuntu-desktop:i386



```

allright? or there a error file?

---

### Post by alex150 on 2014-02-07
please help :X

---

### Post by Iowan on 2014-02-07
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
>     Do not bump your thread more than once in any 24 hour period. Consider waiting longer than that before bumping - this may help to catch the attention of users outside of your timezone.

---

### Post by alex150 on 2014-02-07
cool & and sorry.

---

### Post by alex150 on 2014-02-14
please help bump

---

### Post by whatthefunk on 2014-02-14
> **alex150 said:**
> ```
 Depends: alsa-base  Depends: alsa-utils
    alsa-utils:i386
  Depends: anacron
  Depends: at-spi2-core
    at-spi2-core:i386
  Depends: baobab
  Depends: bc
  Depends: ca-certificates
  Depends: checkbox-qt
  Depends: dmz-cursor-theme
  Depends: doc-base
  Depends: eog
  Depends: evince
  Depends: file-roller
  Depends: fonts-freefont-ttf
  Depends: foomatic-db-compressed-ppds
  Depends: foomatic-filters
  Depends: gcalctool
  Depends: gedit
  Depends: genisoimage
  Depends: ghostscript-x
  Depends: gnome-control-center
  Depends: gnome-font-viewer
  Depends: gnome-media
  Depends: gnome-menus
  Depends: gnome-power-manager
  Depends: gnome-screenshot
  Depends: gnome-session
  Depends: gnome-session-canberra
  Depends: gnome-system-log
  Depends: gnome-system-monitor
  Depends: gnome-terminal
  Depends: gstreamer0.10-alsa
  Depends: gstreamer0.10-plugins-base-apps
  Depends: gstreamer0.10-pulseaudio
  Depends: gucharmap
  Depends: gvfs-bin
    gvfs-bin:i386
  Depends: inputattach
  Depends: language-selector-gnome
  Depends: libatk-adaptor
  Depends: libgd2-xpm
  Depends: libnotify-bin
  Depends: libpam-ck-connector
  Depends: libpam-xdg-support
  Depends: libsasl2-modules
  Depends: libxp6
  Depends: lightdm
  Depends: nautilus
  Depends: nautilus-sendto
  Depends: notify-osd
  Depends: openprinting-ppds
  Depends: printer-driver-pnm2ppa
  Depends: pulseaudio
    pulseaudio:i386
  Depends: rfkill
  Depends: seahorse
  Depends: software-center
  Depends: software-properties-gtk
  Depends: ssh-askpass-gnome
  Depends: system-config-printer-gnome
  Depends: ttf-dejavu-core
  Depends: ubuntu-artwork
  Depends: ubuntu-drivers-common
  Depends: ubuntu-extras-keyring
  Depends: ubuntu-release-upgrader-gtk
  Depends: ubuntu-settings
  Depends: ubuntu-sounds
  Depends: unity
  Depends: unity-greeter
  Depends: unzip
    unzip:i386
  Depends: update-manager
  Depends: update-notifier
  Depends: wireless-tools
    wireless-tools:i386
  Depends: wpasupplicant
    wpasupplicant:i386
  Depends: xdg-user-dirs
  Depends: xdg-user-dirs-gtk
  Depends: xdiagnose
  Depends: xkb-data
  Depends: xorg
  Depends: xterm
    xterm:i386
  Depends: yelp
  Depends: zenity
    zenity:i386
  Depends: zip
    zip:i386
  Recommends: acpi-support
  Recommends: activity-log-manager-control-center
  Recommends: aisleriot
  Recommends: app-install-data-partner
  Recommends: apport-gtk
  Recommends: avahi-autoipd
  Recommends: avahi-daemon
    avahi-daemon:i386
  Recommends: bluez
    bluez:i386
  Recommends: bluez-alsa
  Recommends: bluez-cups
  Recommends: bluez-gstreamer
  Recommends: branding-ubuntu
  Recommends: brasero
  Recommends: brltty
  Recommends: cups
    cups:i386
  Recommends: cups-bsd
    cups-bsd:i386
  Recommends: cups-client
    cups-client:i386
  Recommends: deja-dup
  Recommends: empathy
  Recommends: example-content
  Recommends: firefox
  Recommends: firefox-gnome-support
  Recommends: fonts-kacst-one
  Recommends: fonts-khmeros-core
  Recommends: fonts-lao
  Recommends: fonts-liberation
  Recommends: fonts-lklug-sinhala
  Recommends: fonts-nanum
  Recommends: fonts-sil-abyssinica
  Recommends: fonts-sil-padauk
  Recommends: fonts-takao-pgothic
  Recommends: fonts-thai-tlwg
  Recommends: fonts-tibetan-machine
  Recommends: gcc
  Recommends: gnome-accessibility-themes
  Recommends: gnome-bluetooth
  Recommends: gnome-disk-utility
  Recommends: gnome-mahjongg
  Recommends: gnome-orca
  Recommends: gnome-screensaver
  Recommends: gnome-sudoku
  Recommends: gnomine
  Recommends: gvfs-fuse
  Recommends: gwibber
  Recommends: hplip
  Recommends: ibus
    ibus:i386
  Recommends: ibus-gtk3
  Recommends: ibus-pinyin
  Recommends: ibus-pinyin-db-android
  Recommends: ibus-table
  Recommends: im-switch
    im-config
  Recommends: kerneloops-daemon
  Recommends: landscape-client-ui-install
  Recommends: laptop-detect
  Recommends: libgail-common
  Recommends: libnss-mdns
  Recommends: libpam-gnome-keyring
  Recommends: libproxy1-plugin-gsettings
  Recommends: libproxy1-plugin-networkmanager
  Recommends: libqt4-sql-sqlite
  Recommends: libreoffice-calc
  Recommends: libreoffice-gnome
  Recommends: libreoffice-help-en-us
  Recommends: libreoffice-impress
  Recommends: libreoffice-math
  Recommends: libreoffice-ogltrans
  Recommends: libreoffice-pdfimport
  Recommends: libreoffice-presentation-minimizer
  Recommends: libreoffice-presenter-console
  Recommends: libreoffice-style-human
  Recommends: libreoffice-writer
  Recommends: libwmf0.2-7-gtk
  Recommends: linux-headers-generic
  Recommends: make
  Recommends: mousetweaks
  Recommends: nautilus-share
  Recommends: network-manager-gnome
  Recommends: network-manager-pptp
  Recommends: network-manager-pptp-gnome
  Recommends: onboard
  Recommends: overlay-scrollbar
  Recommends: pcmciautils
  Recommends: plymouth-theme-ubuntu-logo
  Recommends: policykit-desktop-privileges
  Recommends: printer-driver-c2esp
  Recommends: printer-driver-foo2zjs
  Recommends: printer-driver-min12xxw
  Recommends: printer-driver-ptouch
  Recommends: printer-driver-pxljr
  Recommends: printer-driver-sag-gdi
  Recommends: printer-driver-splix
  Recommends: pulseaudio-module-bluetooth
  Recommends: pulseaudio-module-gconf
  Recommends: pulseaudio-module-x11
  Recommends: python3-aptdaemon.pkcompat
  Recommends: qt-at-spi
  Recommends: remmina
  Recommends: rhythmbox
  Recommends: rhythmbox-plugin-magnatune
  Recommends: rhythmbox-ubuntuone
  Recommends: shotwell
  Recommends: simple-scan
  Recommends: sni-qt
  Recommends: speech-dispatcher
  Recommends: telepathy-idle
  Recommends: thunderbird
  Recommends: thunderbird-gnome-support
  Recommends: totem
  Recommends: totem-mozilla
  Recommends: transmission-gtk
  Recommends: ttf-indic-fonts-core
  Recommends: ttf-punjabi-fonts
  Recommends: ttf-ubuntu-font-family
  Recommends: ttf-wqy-microhei
  Recommends: ubuntu-docs
  Recommends: ubuntuone-client-gnome
  Recommends: ubuntuone-control-panel-qt
  Recommends: unity-webapps-common
  Recommends: usb-creator-gtk
  Recommends: vino
  Recommends: whoopsie
  Recommends: xcursor-themes
  Recommends: xdg-utils
  Recommends: xul-ext-ubufox
  Recommends: xul-ext-unity
  Conflicts: ubuntu-desktop:i386



```

allright? or there a error file?

This is just a list of programs you need to have installed in order for things to work properly.  Do you have them all installed?

---

