---
title: "Converting from Xubuntu to Kubuntu?"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by maria5 on 2014-06-06
I have an old Vista laptop (Compaq Presario C770ED) on which I want to install Kubuntu on one partition. Here is the problem though; I don't have any USB/CD/DVD with more than 1GB, which is required for writing the Kubuntu .iso image. (I have a microSD-card with 2GB, but my old Presario has no SD-card-slot...)

So, I was wondering... can I install Xubuntu (its .iso image fits just barely on my USB, but it's there!) on one partition of the laptop and then use
```
[COLOR=#141414][FONT=Georgia]sudo apt-get install kubuntu-desktop[/FONT][/COLOR]
``` to install Kubuntu on that partition, and then use ```
[COLOR=#141414][FONT=Georgia]sudo apt-get purge xubuntu-desktop[/FONT][/COLOR]
``` to delete everything unnecessary from Xubuntu?

By the way, I got the idea after reading this article:
[http://www.linux.org/threads/converting-between-the-ubuntus.5079/](http://www.linux.org/threads/converting-between-the-ubuntus.5079/)

Because, personally, I (= casual user of Windows computers) have no idea what exactly I'd be doing...

Thanks in advance!

---

### Post by Elfy on 2014-06-06
You can do that - but you'll just remove the xubuntu-desktop package itself.

You could use the mini.iso - but that's a bit more complicated.

You could also just try Xubuntu ;)

You could install kubuntu-desktop - then pick that at the login window - you'd still have Xubuntu installed, but you would be running Kubuntu at that point.

Assuming that you're intending to install 14.04 the depends and recommends for xubuntu-desktop are as follows, you'd want to remove all of these and install kubuntu-desktop

Depends

```
alsa-base, alsa-utils, anacron, bc, ca-certificates, dmz-cursor-theme, doc-base, fonts-dejavu-core, fonts-freefont-ttf, foomatic-db-compressed-ppds, genisoimage, ghostscript-x, gtk2-engines-pixbuf, inputattach, language-selector-gnome, libasound2-plugins, libpam-systemd, libsasl2-modules, libxp6, lightdm, lightdm-gtk-greeter, memtest86+, openprinting-ppds, pm-utils, printer-driver-pnm2ppa, rfkill, software-properties-gtk, thunar, thunar-volman, tumbler, ubuntu-drivers-common, ubuntu-extras-keyring, unzip, update-manager, wireless-tools, wpasupplicant, xdg-user-dirs, xdg-user-dirs-gtk, xfce4-appfinder, xfce4-notifyd, xfce4-panel, xfce4-session, xfce4-settings, xfdesktop4, xfwm4, xkb-data, xorg, xterm, xubuntu-artwork, xubuntu-default-settings, zenity, zip
```
Recommends
```

abiword, abiword-plugin-grammar, abiword-plugin-mathview, acpi-support, app-install-data-partner, apport-gtk, apt-offline, avahi-autoipd, avahi-daemon, blueman, bluez, bluez-alsa, bluez-cups, brltty, brltty-x11, catfish, cups, cups-bsd, cups-client, cups-filters, desktop-file-utils, espeak, evince, file-roller, firefox, fonts-droid, fonts-kacst-one, fonts-khmeros-core, fonts-lao, fonts-liberation, fonts-lklug-sinhala, fonts-nanum, fonts-opensymbol, fonts-sil-abyssinica, fonts-sil-padauk, fonts-takao-pgothic, fonts-thai-tlwg, fonts-tibetan-machine, gcc, gigolo, gimp, gmusicbrowser, gnome-accessibility-themes, gnome-calculator, gnome-sudoku, gnome-system-tools, gnomine, gnumeric, gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio, gtk-theme-config, gucharmap, gvfs-backends, gvfs-fuse, hplip, im-config, indicator-application, indicator-messages, indicator-power, indicator-sound, kerneloops-daemon, laptop-detect, libnotify-bin, libnss-mdns, libpam-gnome-keyring, libxfce4ui-utils, light-locker, light-locker-settings, make, menulibre, mousepad, mugshot, network-manager-gnome, network-manager-pptp, network-manager-pptp-gnome, onboard, orage, parole, pastebinit, pavucontrol, pcmciautils, pidgin, pidgin-otr, policykit-desktop-privileges, printer-driver-c2esp, printer-driver-foo2zjs, printer-driver-min12xxw, printer-driver-ptouch, printer-driver-pxljr, printer-driver-sag-gdi, printer-driver-splix, ristretto, simple-scan, software-center, speech-dispatcher, system-config-printer-gnome, thunar-archive-plugin, thunar-media-tags-plugin, thunderbird, transmission-gtk, ttf-indic-fonts-core, ttf-punjabi-fonts, ttf-ubuntu-font-family, update-notifier, whoopsie, xchat, xcursor-themes, xdg-utils, xfburn, xfce4-cpugraph-plugin, xfce4-dict, xfce4-indicator-plugin, xfce4-mailwatch-plugin, xfce4-netload-plugin, xfce4-notes-plugin, xfce4-places-plugin, xfce4-power-manager, xfce4-quicklauncher-plugin, xfce4-screenshooter, xfce4-systemload-plugin, xfce4-taskmanager, xfce4-terminal, xfce4-verve-plugin, xfce4-volumed, xfce4-weather-plugin, xfce4-whiskermenu-plugin, xfce4-xkb-plugin, xubuntu-community-wallpapers, xubuntu-docs, xul-ext-ubufox
```

---

### Post by Rob Sayer on 2014-06-07
I think it'd be better at this point to keep things as simple as possible if you're a linux novice.  As mentioned, perhaps you should just try xubuntu first.

That stuff in that link you posted isn't as straightforward (especially autoremove) as he makes it sound.  I wouldn't bother with that either.  Or the mini or minimal install iso.

Are you *sure* you can't get your hands on a 2Gb USB stick?  Or try burning the Kubuntu live CD to a 1Gb one?  Because if you want to 'try' one or the other you should do it that way first.

USB is way better to try live mode than CD because it's so much faster.  You can get a reasonable feel for the DE without installing.  This is what's recommended by linux people here much more knowledgeable than I and it's much better than installing multiple DEs or playing with autoremove if you're not experienced.  That stuff can cause problems.

I'd also try the Lubuntu live CD on an old computer.  I use Kubuntu 12.04 on my laptop that I use at home which has 4Gb and an i3 CPU.  I've tried it on my 1Gb netbook and it was slow.  I don't think I'd use KDE with less than 2Gb, even if you tweak it for speed, which you definitely can.

This 1Gb netbook is running Xubuntu 14.04 but I'm considering installing Lubuntu on it again ... previously it had lubuntu 13.10.  LXDE is much faster and not much uglier.

Actually I'm starting to like the idea of running a DE that looks like 90's Windows but works a lot like a Mac ...

---

### Post by LastDino on 2014-06-07
Hmm I suspect you might not have system config for kubuntu (judging by lack of everything yoe mentioned, but I could be wrong)

If you've a smart phone which enables you to use ''data mode'', you can very much use that 2GB SD card to install Xubuntu on your PC.

---

