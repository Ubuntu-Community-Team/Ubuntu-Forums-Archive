---
title: "What package(s) make System Settings work?"
date: 2011-08-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-08-19
I'm using gnome-shell and a week or so ago system settings from the drop down menu at the user name stopped starting. System settings is not in the Applications menu either. It seems to have disappeared :(
Does anyone know what package(s) need to be installed for it to run?

Are others having the same problem?

Thanks.

---

### Post by cariboo on 2011-08-19
Have you tried:

```
gnome-control-center --overview
```

---

### Post by Quackers on 2011-08-19
Cariboo907, that gives this ```
ocelot2@ocelot2-VGN-AR51SU:~$ gnome-control-center --overview
/usr/bin/python: can't find '__main__' module in '/usr/share/command-not-found'

```

---

### Post by cariboo on 2011-08-19
I don't know if this will help, but this is what I get when I run locate gnome-control-center:

```
locate gnome-control-center
/home/cariboo/.cache/gnome-control-center
/home/cariboo/.cache/gnome-control-center/backgrounds
/home/cariboo/.cache/gnome-control-center/backgrounds/6ada0bcecaa67dc6c7c14de193e83560b9dee06160e1afe6c866def014390a74
/home/cariboo/.config/gnome-control-center
/home/cariboo/.config/gnome-control-center/backgrounds
/home/cariboo/.config/gnome-control-center/backgrounds/last-edited.xml
/usr/bin/gnome-control-center
/usr/lib/libgnome-control-center.so.1
/usr/lib/libgnome-control-center.so.1.0.0
/usr/share/gnome-control-center
/usr/share/applications/gnome-control-center.desktop
/usr/share/doc/gnome-control-center
/usr/share/doc/gnome-control-center-data
/usr/share/doc/libgnome-control-center1
/usr/share/doc/gnome-control-center/AUTHORS
/usr/share/doc/gnome-control-center/NEWS.gz
/usr/share/doc/gnome-control-center/README
/usr/share/doc/gnome-control-center/TODO
/usr/share/doc/gnome-control-center/changelog.Debian.gz
/usr/share/doc/gnome-control-center/copyright
/usr/share/doc/gnome-control-center-data/AUTHORS
/usr/share/doc/gnome-control-center-data/NEWS.gz
/usr/share/doc/gnome-control-center-data/README
/usr/share/doc/gnome-control-center-data/TODO
/usr/share/doc/gnome-control-center-data/changelog.Debian.gz
/usr/share/doc/gnome-control-center-data/copyright
/usr/share/doc/libgnome-control-center1/AUTHORS
/usr/share/doc/libgnome-control-center1/NEWS.gz
/usr/share/doc/libgnome-control-center1/README
/usr/share/doc/libgnome-control-center1/TODO
/usr/share/doc/libgnome-control-center1/changelog.Debian.gz
/usr/share/doc/libgnome-control-center1/copyright
/usr/share/gnome-control-center/datetime
/usr/share/gnome-control-center/default-apps
/usr/share/gnome-control-center/icons
/usr/share/gnome-control-center/keybindings
/usr/share/gnome-control-center/pixmaps
/usr/share/gnome-control-center/sounds
/usr/share/gnome-control-center/ui
/usr/share/gnome-control-center/datetime/backward
/usr/share/gnome-control-center/default-apps/chromium-browser.xml
/usr/share/gnome-control-center/icons/hicolor
/usr/share/gnome-control-center/icons/hicolor/16x16
/usr/share/gnome-control-center/icons/hicolor/22x22
/usr/share/gnome-control-center/icons/hicolor/24x24
/usr/share/gnome-control-center/icons/hicolor/32x32
/usr/share/gnome-control-center/icons/hicolor/48x48
/usr/share/gnome-control-center/icons/hicolor/16x16/devices
/usr/share/gnome-control-center/icons/hicolor/16x16/status
/usr/share/gnome-control-center/icons/hicolor/16x16/devices/audio-headset.svg
/usr/share/gnome-control-center/icons/hicolor/16x16/status/audio-input-microphone-high.png
/usr/share/gnome-control-center/icons/hicolor/16x16/status/audio-input-microphone-low.png
/usr/share/gnome-control-center/icons/hicolor/16x16/status/audio-input-microphone-medium.png
/usr/share/gnome-control-center/icons/hicolor/16x16/status/audio-input-microphone-muted.png
/usr/share/gnome-control-center/icons/hicolor/22x22/status
/usr/share/gnome-control-center/icons/hicolor/22x22/status/audio-input-microphone-high.png
/usr/share/gnome-control-center/icons/hicolor/22x22/status/audio-input-microphone-low.png
/usr/share/gnome-control-center/icons/hicolor/22x22/status/audio-input-microphone-medium.png
/usr/share/gnome-control-center/icons/hicolor/22x22/status/audio-input-microphone-muted.png
/usr/share/gnome-control-center/icons/hicolor/24x24/devices
/usr/share/gnome-control-center/icons/hicolor/24x24/status
/usr/share/gnome-control-center/icons/hicolor/24x24/devices/audio-headset.svg
/usr/share/gnome-control-center/icons/hicolor/24x24/status/audio-input-microphone-high.png
/usr/share/gnome-control-center/icons/hicolor/24x24/status/audio-input-microphone-low.png
/usr/share/gnome-control-center/icons/hicolor/24x24/status/audio-input-microphone-medium.png
/usr/share/gnome-control-center/icons/hicolor/24x24/status/audio-input-microphone-muted.png
/usr/share/gnome-control-center/icons/hicolor/32x32/devices
/usr/share/gnome-control-center/icons/hicolor/32x32/status
/usr/share/gnome-control-center/icons/hicolor/32x32/devices/audio-headset.svg
/usr/share/gnome-control-center/icons/hicolor/32x32/status/audio-input-microphone-high.png
/usr/share/gnome-control-center/icons/hicolor/32x32/status/audio-input-microphone-low.png
/usr/share/gnome-control-center/icons/hicolor/32x32/status/audio-input-microphone-medium.png
/usr/share/gnome-control-center/icons/hicolor/32x32/status/audio-input-microphone-muted.png
/usr/share/gnome-control-center/icons/hicolor/48x48/devices
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-center-back-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-center-back.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-center-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-center.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-left-back-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-left-back.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-left-side-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-left-side.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-left-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-left.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-right-back-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-right-back.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-right-side-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-right-side.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-right-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-speaker-right.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-subwoofer-testing.svg
/usr/share/gnome-control-center/icons/hicolor/48x48/devices/audio-subwoofer.svg
/usr/share/gnome-control-center/keybindings/00-multimedia.xml
/usr/share/gnome-control-center/keybindings/01-launchers.xml
/usr/share/gnome-control-center/keybindings/01-system.xml
/usr/share/gnome-control-center/keybindings/50-accessibility.xml
/usr/share/gnome-control-center/keybindings/50-metacity-launchers.xml
/usr/share/gnome-control-center/keybindings/50-metacity-navigation.xml
/usr/share/gnome-control-center/keybindings/50-metacity-screenshot.xml
/usr/share/gnome-control-center/keybindings/50-metacity-system.xml
/usr/share/gnome-control-center/keybindings/50-metacity-windows.xml
/usr/share/gnome-control-center/pixmaps/double-click-maybe.png
/usr/share/gnome-control-center/pixmaps/double-click-off.png
/usr/share/gnome-control-center/pixmaps/double-click-on.png
/usr/share/gnome-control-center/pixmaps/gnome-about-me-lock-open.png
/usr/share/gnome-control-center/pixmaps/gnome-about-me-lock.png
/usr/share/gnome-control-center/pixmaps/left-index-finger.png
/usr/share/gnome-control-center/pixmaps/left-index-finger.svg
/usr/share/gnome-control-center/pixmaps/left-little-finger.png
/usr/share/gnome-control-center/pixmaps/left-little-finger.svg
/usr/share/gnome-control-center/pixmaps/left-middle-finger.png
/usr/share/gnome-control-center/pixmaps/left-middle-finger.svg
/usr/share/gnome-control-center/pixmaps/left-ring-finger.png
/usr/share/gnome-control-center/pixmaps/left-ring-finger.svg
/usr/share/gnome-control-center/pixmaps/left-thumb.png
/usr/share/gnome-control-center/pixmaps/left-thumb.svg
/usr/share/gnome-control-center/pixmaps/print_error.png
/usr/share/gnome-control-center/pixmaps/print_error.svg
/usr/share/gnome-control-center/pixmaps/print_ok.png
/usr/share/gnome-control-center/pixmaps/print_ok.svg
/usr/share/gnome-control-center/pixmaps/right-index-finger.png
/usr/share/gnome-control-center/pixmaps/right-index-finger.svg
/usr/share/gnome-control-center/pixmaps/right-little-finger.png
/usr/share/gnome-control-center/pixmaps/right-little-finger.svg
/usr/share/gnome-control-center/pixmaps/right-middle-finger.png
/usr/share/gnome-control-center/pixmaps/right-middle-finger.svg
/usr/share/gnome-control-center/pixmaps/right-ring-finger.png
/usr/share/gnome-control-center/pixmaps/right-ring-finger.svg
/usr/share/gnome-control-center/pixmaps/right-thumb.png
/usr/share/gnome-control-center/pixmaps/right-thumb.svg
/usr/share/gnome-control-center/sounds/gnome-sounds-default.xml
/usr/share/gnome-control-center/ui/GnomeLogoVerticalMedium.svg
/usr/share/gnome-control-center/ui/background
/usr/share/gnome-control-center/ui/datetime
/usr/share/gnome-control-center/ui/display-capplet.ui
/usr/share/gnome-control-center/ui/gnome-keyboard-panel.ui
/usr/share/gnome-control-center/ui/gnome-media-properties.ui
/usr/share/gnome-control-center/ui/gnome-mouse-properties.ui
/usr/share/gnome-control-center/ui/gnome-region-panel-layout-chooser.ui
/usr/share/gnome-control-center/ui/gnome-region-panel-options-dialog.ui
/usr/share/gnome-control-center/ui/gnome-region-panel.ui
/usr/share/gnome-control-center/ui/info.ui
/usr/share/gnome-control-center/ui/network.ui
/usr/share/gnome-control-center/ui/online-accounts.ui
/usr/share/gnome-control-center/ui/power.ui
/usr/share/gnome-control-center/ui/printers
/usr/share/gnome-control-center/ui/screen.ui
/usr/share/gnome-control-center/ui/shell.ui
/usr/share/gnome-control-center/ui/uap.ui
/usr/share/gnome-control-center/ui/user-accounts
/usr/share/gnome-control-center/ui/background/background.ui
/usr/share/gnome-control-center/ui/background/display-base.png
/usr/share/gnome-control-center/ui/background/display-overlay.png
/usr/share/gnome-control-center/ui/datetime/bg.png
/usr/share/gnome-control-center/ui/datetime/cc.png
/usr/share/gnome-control-center/ui/datetime/datetime.ui
/usr/share/gnome-control-center/ui/datetime/pin.png
/usr/share/gnome-control-center/ui/datetime/timezone_-1.png
/usr/share/gnome-control-center/ui/datetime/timezone_-10.png
/usr/share/gnome-control-center/ui/datetime/timezone_-11.png
/usr/share/gnome-control-center/ui/datetime/timezone_-2.png
/usr/share/gnome-control-center/ui/datetime/timezone_-3.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_-3.png
/usr/share/gnome-control-center/ui/datetime/timezone_-4.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_-4.png
/usr/share/gnome-control-center/ui/datetime/timezone_-5.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_-5.png
/usr/share/gnome-control-center/ui/datetime/timezone_-6.png
/usr/share/gnome-control-center/ui/datetime/timezone_-7.png
/usr/share/gnome-control-center/ui/datetime/timezone_-8.png
/usr/share/gnome-control-center/ui/datetime/timezone_-9.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_-9.png
/usr/share/gnome-control-center/ui/datetime/timezone_0.png
/usr/share/gnome-control-center/ui/datetime/timezone_1.png
/usr/share/gnome-control-center/ui/datetime/timezone_10.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_10.png
/usr/share/gnome-control-center/ui/datetime/timezone_11.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_11.png
/usr/share/gnome-control-center/ui/datetime/timezone_12.75.png
/usr/share/gnome-control-center/ui/datetime/timezone_12.png
/usr/share/gnome-control-center/ui/datetime/timezone_13.png
/usr/share/gnome-control-center/ui/datetime/timezone_14.png
/usr/share/gnome-control-center/ui/datetime/timezone_2.png
/usr/share/gnome-control-center/ui/datetime/timezone_3.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_3.png
/usr/share/gnome-control-center/ui/datetime/timezone_4.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_4.png
/usr/share/gnome-control-center/ui/datetime/timezone_5.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_5.75.png
/usr/share/gnome-control-center/ui/datetime/timezone_5.png
/usr/share/gnome-control-center/ui/datetime/timezone_6.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_6.png
/usr/share/gnome-control-center/ui/datetime/timezone_7.png
/usr/share/gnome-control-center/ui/datetime/timezone_8.75.png
/usr/share/gnome-control-center/ui/datetime/timezone_8.png
/usr/share/gnome-control-center/ui/datetime/timezone_9.5.png
/usr/share/gnome-control-center/ui/datetime/timezone_9.png
/usr/share/gnome-control-center/ui/printers/new-printer-dialog.ui
/usr/share/gnome-control-center/ui/printers/printers.ui
/usr/share/gnome-control-center/ui/user-accounts/account-dialog.ui
/usr/share/gnome-control-center/ui/user-accounts/account-fingerprint.ui
/usr/share/gnome-control-center/ui/user-accounts/language-chooser.ui
/usr/share/gnome-control-center/ui/user-accounts/password-dialog.ui
/usr/share/gnome-control-center/ui/user-accounts/photo-dialog.ui
/usr/share/gnome-control-center/ui/user-accounts/user-accounts-dialog.ui
/usr/share/icons/Humanity/categories/16/gnome-control-center.svg
/usr/share/icons/Humanity/categories/24/gnome-control-center.svg
/usr/share/icons/Humanity/categories/32/gnome-control-center.svg
/usr/share/icons/Humanity/categories/48/gnome-control-center.svg
/usr/share/icons/gnome/16x16/categories/gnome-control-center.png
/usr/share/icons/gnome/22x22/categories/gnome-control-center.png
/usr/share/icons/gnome/24x24/categories/gnome-control-center.png
/usr/share/icons/gnome/32x32/categories/gnome-control-center.png
/usr/share/icons/gnome/48x48/categories/gnome-control-center.png
/usr/share/indicators/session/applications/gnome-control-center.desktop
/usr/share/locale-langpack/en/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/locale-langpack/en@shaw/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/man/man1/gnome-control-center.1.gz
/usr/share/menu/gnome-control-center
/var/lib/dpkg/info/gnome-control-center-data.conffiles
/var/lib/dpkg/info/gnome-control-center-data.list
/var/lib/dpkg/info/gnome-control-center-data.md5sums
/var/lib/dpkg/info/gnome-control-center-data.postinst
/var/lib/dpkg/info/gnome-control-center.list
/var/lib/dpkg/info/gnome-control-center.md5sums
/var/lib/dpkg/info/gnome-control-center.postinst
/var/lib/dpkg/info/gnome-control-center.postrm
/var/lib/dpkg/info/libgnome-control-center1.list
/var/lib/dpkg/info/libgnome-control-center1.md5sums
/var/lib/dpkg/info/libgnome-control-center1.postinst
/var/lib/dpkg/info/libgnome-control-center1.postrm
/var/lib/dpkg/info/libgnome-control-center1.shlibs
/var/lib/dpkg/info/libgnome-control-center1.symbols
```

---

### Post by Quackers on 2011-08-19
Thanks cariboo907, I get what's below. There are many differences that I can look into. I'll start now :-)
```
ocelot2@ocelot2-VGN-AR51SU:~$ locate gnome-control-center
/home/ocelot2/.config/gnome-control-center
/home/ocelot2/.config/gnome-control-center/backgrounds
/home/ocelot2/.config/gnome-control-center/backgrounds/last-edited.xml
/usr/lib/libgnome-control-center.so.1
/usr/lib/libgnome-control-center.so.1.0.0
/usr/share/gnome-control-center
/usr/share/doc/libgnome-control-center1
/usr/share/doc/libgnome-control-center1/AUTHORS
/usr/share/doc/libgnome-control-center1/NEWS.gz
/usr/share/doc/libgnome-control-center1/README
/usr/share/doc/libgnome-control-center1/TODO
/usr/share/doc/libgnome-control-center1/changelog.Debian.gz
/usr/share/doc/libgnome-control-center1/copyright
/usr/share/gnome-control-center/keybindings
/usr/share/gnome-control-center/keybindings/50-metacity-launchers.xml
/usr/share/gnome-control-center/keybindings/50-metacity-navigation.xml
/usr/share/gnome-control-center/keybindings/50-metacity-screenshot.xml
/usr/share/gnome-control-center/keybindings/50-metacity-system.xml
/usr/share/gnome-control-center/keybindings/50-metacity-windows.xml
/usr/share/icons/Humanity/categories/16/gnome-control-center.svg
/usr/share/icons/Humanity/categories/24/gnome-control-center.svg
/usr/share/icons/Humanity/categories/32/gnome-control-center.svg
/usr/share/icons/Humanity/categories/48/gnome-control-center.svg
/usr/share/icons/gnome/16x16/categories/gnome-control-center.png
/usr/share/icons/gnome/22x22/categories/gnome-control-center.png
/usr/share/icons/gnome/24x24/categories/gnome-control-center.png
/usr/share/icons/gnome/32x32/categories/gnome-control-center.png
/usr/share/icons/gnome/48x48/categories/gnome-control-center.png
/usr/share/locale-langpack/en/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/locale-langpack/en@shaw/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/gnome-control-center-2.0.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/gnome-control-center-2.0.mo
/var/lib/dpkg/info/gnome-control-center-data.list
/var/lib/dpkg/info/gnome-control-center.list
/var/lib/dpkg/info/gnome-control-center.postrm
/var/lib/dpkg/info/libgnome-control-center1.list
/var/lib/dpkg/info/libgnome-control-center1.md5sums
/var/lib/dpkg/info/libgnome-control-center1.postinst
/var/lib/dpkg/info/libgnome-control-center1.postrm
/var/lib/dpkg/info/libgnome-control-center1.shlibs
/var/lib/dpkg/info/libgnome-control-center1.symbols

```

---

### Post by Quackers on 2011-08-19
Mr Cariboo, it seems that the package gnome-control-center-data was missing! This package drags in 3 other packages, one of which is gnome-control-center.
System settings now works fine.
Thank you sir :-)

---

### Post by cariboo on 2011-08-19
I'm glad you got it sorted, and you're welcome.

---

