---
title: "(SOLVED) 12.10 broken after removing packages"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by bou3lam on 2013-03-29
hi
i wanted to remove some medibuntu packages and its seems has removed something else, this is the command i made :
```


PKGS=$(dpkg -l | awk '{print $2}' | grep -e aacgain -e aacplusenc -e acroread-fonts -e alsa-firmware -e app-install-data-medibuntu -e apport-hooks-medibuntu -e hot-babe -e ices -e libavcodec-extra-53 -e libavdevice-extra-53 -e libav-extra-dbg -e libavfilter-extra-2 -e libavformat-extra-53 -e libavutil-extra-51 -e libdvdcss2 -e libdvdcss-dev -e libpostproc-extra-52 -e libswscale-extra-2 -e medibuntu-keyring -e mencoder -e mplayer-dbg -e mplayer-doc -e mplayer-gui -e mplayer -e non-free-codecs -e rmconverter -e w32codecs -e w64codecs | tr '\n' ' '); sudo apt-get purge $PKGS


```
ubuntu load and take me to login screen but its doesnt accept my password, please someone help

---

### Post by ManamiVixen on 2013-03-29
If the mediabuntu was a seperate ppa, you could use the ppa-purge command provided by ppa-purge to remove uneeded ppa's and their packages at the same time.

---

### Post by bou3lam on 2013-03-30
no its seems that command deleted a lot of other things, the system is not working now, i have downloaded and burned ubuntu dektop 12.10 into a cd, can someone please help me how to repair my install without losing my data ? 
thanks in advance

---

### Post by schragge on 2013-03-30
The *grep -e ices* stanza would select anything that contains substring *ices* in it like *glib-networking-serv[COLOR=red]ices[/COLOR]*, *php-serv[COLOR=red]ices[/COLOR]-json*, *lib[COLOR=#ff0000]ices[/COLOR]sl34*, and so on. You should have resticted it with *^ices$*. The same is true for all other strings you grepped. E.g. *grep -e mplayer* would select all the packages listed below
```

gnome-mplayer - GTK+ interface for MPlayer
gnome-mplayer-dbg - GTK+ interface for MPlayer (debugging symbols)
mplayerthumbs - video thumbnail generator using mplayer
kmplayer - media player for KDE
mplayer-dbg - debugging symbols for MPlayer
mplayer-gui - movie player for Unix-like systems
mplayer-skin-blue - blue skin for mplayer
mplayer2-dbg - Debugging symbols for mplayer2
remuco-mplayer - duplex remote control for media players - MPlayer adapter
smplayer - complete front-end for MPlayer and MPlayer2
smplayer-translations - complete front-end for MPlayer and MPlayer2 - translation files
smplayer-themes - complete front-end for MPlayer - icon themes
[COLOR=#ff0000]python-templayer - layered template library for Python[/COLOR]
vdr-plugin-mplayer - MPlayer playback plugin for VDR
mplayer - Ultimate Movie Player For Linux.
mplayer-doc - Documentation for mplayer.
mplayer-nogui - Ultimate Movie Player For Linux.
mplayer2 - Advanced general-purpose video player.
smplayer2 - Front-end for Mplayer2.
smplayer2-common - Front-end for Mplayer2 (common data files).

``` Note that [COLOR=red]python-templayer[/COLOR] has nothing to do with Mplayer.

[highlight]Update[/highlight]
Please have a look at the output of
```
awk '$3=="remove"' /var/log/dpkg.log
```

To get the list of packages you may want to re-install, try
```
awk '$1=="2013-03-30" && $3=="remove" {print $4}' /var/lib/dpkg.log
```

---

### Post by bou3lam on 2013-03-30
i understood this really late, now i need just to repair the broken things with the burned cd without losing my data, is that possible ?

---

### Post by schragge on 2013-03-30
Certainly, I've updated my previous post. Can you still log in on the text console, say **Ctrl**+**Alt**+**F1**?

---

### Post by bou3lam on 2013-03-30
yes i can still use the console, ctrl+f2 i can even login with my username and password, and get root with su, but through the gnome classic or ubuntu default login screens i cant logi in, im doing a home backup now, please kindly allow some 30 minutes and i will put the results

---

### Post by ManamiVixen on 2013-03-30
Do in a terminal 
'sudo apt-get update && sudo apt-get install --fix-policy' and see where that will get you.

---

### Post by bou3lam on 2013-03-30
here the results, seems that damned command removed everything :(

awk '$3=="remove"' /var/log/dpkg.log :```
awk '$3=="remove"' /var/log/dpkg.log
2013-03-12 00:20:11 remove libmsn0.3:amd64 4.2.1-0ubuntu2 <none>
2013-03-12 00:20:12 remove libnspr4:i386 4.9.4-0ubuntu0.12.10.1 <none>
2013-03-12 00:20:13 remove libnss3:i386 3.14.1-0ckbi1.93ubuntu.0.12.10.1 <none>
2013-03-12 00:20:14 remove libodbc1:i386 2.2.14p2-5ubuntu4 <none>
2013-03-12 00:20:15 remove libortp8:amd64 3.5.2-10 <none>
2013-03-12 00:20:16 remove libpango1.0-0:i386 1.30.1-0ubuntu3 <none>
2013-03-12 00:20:17 remove libphysfs1:amd64 2.0.2-6 <none>
2013-03-12 00:20:18 remove libpixman-1-0:i386 0.26.0-3 <none>
2013-03-12 00:20:19 remove libportsmf0:amd64 0.1~svn20101010-3 <none>
2013-03-12 00:20:20 remove libproxy1:i386 0.4.7-0ubuntu6 <none>
2013-03-12 00:20:21 remove libpst4:amd64 0.6.54-4 <none>
2013-03-12 00:20:22 remove libpulse-mainloop-glib0:i386 1:2.1-0ubuntu4 <none>
2013-03-12 00:20:23 remove libqt4-opengl:i386 4:4.8.3+dfsg-0ubuntu3.1 <none>
2013-03-12 00:20:24 remove libqt4-svg:i386 4:4.8.3+dfsg-0ubuntu3.1 <none>
2013-03-12 00:20:25 remove libraw1394-11:i386 2.0.9-1 <none>
2013-03-12 00:20:26 remove libroken18-heimdal:i386 1.6~git20120403+dfsg1-2 <none>
2013-03-12 00:20:27 remove librsvg2-2:i386 2.36.3-0ubuntu1 <none>
2013-03-12 00:20:28 remove librtmp0:i386 2.4+20111222.git4e06e21-1 <none>
2013-03-12 00:20:29 remove libsane:i386 1.0.23-0ubuntu1 <none>
2013-03-12 00:20:30 remove libsasl2-2:i386 2.1.25.dfsg1-5 <none>
2013-03-12 00:20:31 remove libsbsms10:amd64 2.0.1-1 <none>
2013-03-12 00:20:32 remove libsdl-image1.2:i386 1.2.12-3~exp1ubuntu1 <none>
2013-03-12 00:20:33 remove libsdl-mixer1.2:i386 1.2.12-3 <none>
2013-03-12 00:20:34 remove libsdl-net1.2:i386 1.2.8-2 <none>
2013-03-12 00:20:35 remove libsdl-ttf2.0-0:i386 2.0.11-2 <none>
2013-03-12 00:20:36 remove libsdl1.2debian:i386 1.2.15-5ubuntu1 <none>
2013-03-12 00:20:37 remove libshout3:i386 2.3.1-1ubuntu2 <none>
2013-03-12 00:20:39 remove libsoup-gnome2.4-1:i386 2.40.0-0ubuntu1 <none>
2013-03-12 00:20:40 remove libsoup2.4-1:i386 2.40.0-0ubuntu1 <none>
2013-03-12 00:20:41 remove libspeex1:i386 1.2~rc1-6 <none>
2013-03-12 00:20:42 remove libsqlite0:amd64 2.8.17-7fakesync1build1 <none>
2013-03-12 00:20:43 remove libsrtp0:amd64 1.4.4+20100615~dfsg-1build1 <none>
2013-03-12 00:20:44 remove libssl0.9.8:i386 0.9.8o-7ubuntu3.1 <none>
2013-03-12 00:20:45 remove libstdc++5:amd64 1:3.3.6-25ubuntu1 <none>
2013-03-12 00:20:46 remove libstdc++5:i386 1:3.3.6-25ubuntu1 <none>
2013-03-12 00:20:47 remove libsvga1:amd64 1:1.4.3-33 <none>
2013-03-12 00:20:48 remove libtag1-vanilla:i386 1.8-0ubuntu2 <none>
2013-03-12 00:20:49 remove libtdb1:i386 1.2.10-2 <none>
2013-03-12 00:20:50 remove libtinyxml2.6.2:amd64 2.6.2-1build1 <none>
2013-03-12 00:20:51 remove libunistring0:i386 0.9.3-5build1 <none>
2013-03-12 00:20:52 remove libusb-0.1-4:i386 2:0.1.12-23 <none>
2013-03-12 00:20:53 remove libusb-1.0-0:i386 2:1.0.12-2 <none>
2013-03-12 00:20:54 remove libv4l-0:i386 0.8.8-2ubuntu1 <none>
2013-03-12 00:20:55 remove libv4lconvert0:i386 0.8.8-2ubuntu1 <none>
2013-03-12 00:20:56 remove libvamp-hostsdk3:amd64 2.1-1 <none>
2013-03-12 00:20:57 remove libvorbisfile3:i386 1.3.2-1.3 <none>
2013-03-12 00:20:58 remove libwavpack1:i386 4.60.1-3 <none>
2013-03-12 00:20:59 remove libwebp2:i386 0.1.3-3 <none>
2013-03-12 00:21:00 remove libwind0-heimdal:i386 1.6~git20120403+dfsg1-2 <none>
2013-03-12 00:21:01 remove libxaw7:i386 2:1.0.10-2 <none>
2013-03-12 00:21:02 remove libxcb-render0:i386 1.8.1-1ubuntu1 <none>
2013-03-12 00:21:03 remove libxcb-shm0:i386 1.8.1-1ubuntu1 <none>
2013-03-12 00:21:05 remove libxcomposite1:i386 1:0.4.3-2build2 <none>
2013-03-12 00:21:06 remove libxcursor1:i386 1:1.1.13-1 <none>
2013-03-12 00:21:07 remove libxft2:i386 2.3.1-1 <none>
2013-03-12 00:21:08 remove libxinerama1:i386 2:1.1.2-1 <none>
2013-03-12 00:21:09 remove libxmu6:i386 2:1.1.1-1 <none>
2013-03-12 00:21:10 remove libxp6:i386 1:1.0.1-2build1 <none>
2013-03-12 00:21:11 remove libxpm4:i386 1:3.5.10-1 <none>
2013-03-12 00:21:12 remove libxrandr2:i386 2:1.4.0-1 <none>
2013-03-12 00:21:13 remove libxslt1.1:i386 1.1.26-14 <none>
2013-03-12 00:21:14 remove libxtst6:i386 2:1.2.1-1 <none>
2013-03-12 00:21:15 remove libytnef0:amd64 1.5-4build1 <none>
2013-03-12 00:21:16 remove menu-xdg:all 0.5 <none>
2013-03-12 00:21:18 remove odbcinst1debian2:i386 2.2.14p2-5ubuntu4 <none>
2013-03-12 00:21:19 remove plasma-containments-addons:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-12 00:21:20 remove python-central:all 0.6.17ubuntu2 <none>
2013-03-12 00:21:21 remove quadrapassel:amd64 1:3.6.0.2-0ubuntu1.2 <none>
2013-03-12 00:21:22 remove sound-juicer:amd64 3.4.0-3 <none>
2013-03-12 00:21:23 remove swell-foop:amd64 1:3.6.0.2-0ubuntu1.2 <none>
2013-03-12 00:21:24 remove timidity:amd64 2.13.2-40build2 <none>
2013-03-12 00:21:26 remove timidity-daemon:all 2.13.2-40build2 <none>
2013-03-12 00:21:27 remove xaw3dg:i386 1.5+E-18.2 <none>
2013-03-12 21:14:49 remove gufw:all 12.10.0-0ubuntu2 <none>
2013-03-13 15:34:06 remove pcsx2:i386 1.0.0+svn5409+dfsg-0.1~precise1 <none>
2013-03-13 15:40:10 remove libwxgtk2.8-0:i386 2.8.12.1-11ubuntu3.1 <none>
2013-03-13 15:40:12 remove libgtk2.0-0:i386 2.24.13-0ubuntu2 <none>
2013-03-13 15:40:12 remove libatk1.0-0:i386 2.6.0-0ubuntu1 <none>
2013-03-13 15:40:13 remove libsdl1.2debian:i386 1.2.15-5ubuntu1 <none>
2013-03-13 15:40:13 remove libcaca0:i386 0.99.beta18-1 <none>
2013-03-13 15:40:14 remove libpango1.0-0:i386 1.30.1-0ubuntu3 <none>
2013-03-13 15:40:14 remove libcairo2:i386 1.12.2-1ubuntu2.2 <none>
2013-03-13 15:40:15 remove libcggl:i386 3.1.0013-1 <none>
2013-03-13 15:40:16 remove libcg:i386 3.1.0013-1 <none>
2013-03-13 15:40:16 remove libgdk-pixbuf2.0-0:i386 2.26.4-0ubuntu1 <none>
2013-03-13 15:40:17 remove libglew1.8:i386 1.8.0-1ubuntu2 <none>
2013-03-13 15:40:17 remove libjasper1:i386 1.900.1-13build1 <none>
2013-03-13 15:40:18 remove libpixman-1-0:i386 0.26.0-3 <none>
2013-03-13 15:40:18 remove libportaudio2:i386 19+svn20111121-1build1 <none>
2013-03-13 15:40:19 remove libsoundtouch0:i386 1.6.0-3 <none>
2013-03-13 15:40:20 remove libwxbase2.8-0:i386 2.8.12.1-11ubuntu3.1 <none>
2013-03-13 15:40:20 remove libxcb-render0:i386 1.8.1-1ubuntu1 <none>
2013-03-13 15:40:21 remove libxcb-shm0:i386 1.8.1-1ubuntu1 <none>
2013-03-13 15:40:21 remove libxcomposite1:i386 1:0.4.3-2build2 <none>
2013-03-13 15:40:22 remove libxcursor1:i386 1:1.1.13-1 <none>
2013-03-13 15:40:22 remove libxft2:i386 2.3.1-1 <none>
2013-03-13 15:40:23 remove libxinerama1:i386 2:1.1.2-1 <none>
2013-03-13 15:40:23 remove libxrandr2:i386 2:1.4.0-1 <none>
2013-03-13 15:41:11 remove libatk1.0-0:i386 2.6.0-0ubuntu1 <none>
2013-03-13 15:41:12 remove libcaca0:i386 0.99.beta18-1 <none>
2013-03-13 15:41:13 remove libcairo2:i386 1.12.2-1ubuntu2.2 <none>
2013-03-13 15:41:14 remove libcg:i386 3.1.0013-1 <none>
2013-03-13 15:41:15 remove libcggl:i386 3.1.0013-1 <none>
2013-03-13 15:41:17 remove libgdk-pixbuf2.0-0:i386 2.26.4-0ubuntu1 <none>
2013-03-13 15:41:23 remove libglew1.8:i386 1.8.0-1ubuntu2 <none>
2013-03-13 15:41:30 remove libgtk2.0-0:i386 2.24.13-0ubuntu2 <none>
2013-03-13 15:41:34 remove libjasper1:i386 1.900.1-13build1 <none>
2013-03-13 15:41:38 remove libpango1.0-0:i386 1.30.1-0ubuntu3 <none>
2013-03-13 15:41:42 remove libpixman-1-0:i386 0.26.0-3 <none>
2013-03-13 15:41:46 remove libportaudio2:i386 19+svn20111121-1build1 <none>
2013-03-13 15:41:49 remove libsdl1.2debian:i386 1.2.15-5ubuntu1 <none>
2013-03-13 15:41:53 remove libsoundtouch0:i386 1.6.0-3 <none>
2013-03-13 15:41:56 remove libwxbase2.8-0:i386 2.8.12.1-11ubuntu3.1 <none>
2013-03-13 15:41:59 remove libwxgtk2.8-0:i386 2.8.12.1-11ubuntu3.1 <none>
2013-03-13 15:42:01 remove libxcb-render0:i386 1.8.1-1ubuntu1 <none>
2013-03-13 15:42:02 remove libxcb-shm0:i386 1.8.1-1ubuntu1 <none>
2013-03-13 15:42:03 remove libxcomposite1:i386 1:0.4.3-2build2 <none>
2013-03-13 15:42:05 remove libxcursor1:i386 1:1.1.13-1 <none>
2013-03-13 15:42:06 remove libxft2:i386 2.3.1-1 <none>
2013-03-13 15:42:07 remove libxinerama1:i386 2:1.1.2-1 <none>
2013-03-13 15:42:08 remove libxrandr2:i386 2:1.4.0-1 <none>
2013-03-13 15:42:09 remove pcsx2:i386 1.0.0+svn5409+dfsg-0.1~precise1 <none>
2013-03-13 19:03:41 remove unix-runescape-client:all 3.2-2 <none>
2013-03-13 19:04:02 remove runescape:all 201302280552~git-master~quantal1 <none>
2013-03-13 19:04:03 remove libwx-perl:amd64 1:0.9909-1 <none>
2013-03-13 19:04:04 remove libalien-wxwidgets-perl:amd64 0.59+dfsg-1 <none>
2013-03-13 19:04:05 remove libwxgtk2.8-dev:amd64 2.8.12.1-11ubuntu3.1 <none>
2013-03-13 19:04:05 remove libwxbase2.8-dev:amd64 2.8.12.1-11ubuntu3.1 <none>
2013-03-13 19:04:06 remove wx-common:amd64 2.8.12.1-11ubuntu3.1 <none>
2013-03-13 19:04:07 remove wx2.8-headers:amd64 2.8.12.1-11ubuntu3.1 <none>
2013-03-17 13:38:29 remove stellarium:amd64 0.11.3-1 <none>
2013-03-17 13:38:31 remove stellarium-data:all 0.11.3-1 <none>
2013-03-19 20:03:08 remove pidgin-libnotify:amd64 0.14-4ubuntu11 <none>
2013-03-19 20:03:09 remove pidgin:amd64 1:2.10.6-0ubuntu2.2 <none>
2013-03-19 21:58:33 remove emesene:all 2.12.5+dfsg-1ubuntu2 <none>
2013-03-19 21:58:36 remove python-dnspython:all 1.10.0-1 <none>
2013-03-19 21:58:37 remove python-gupnp-igd:amd64 0.2.1-2build1 <none>
2013-03-19 21:58:37 remove python-indicate:amd64 12.10.1-0ubuntu1 <none>
2013-03-19 21:58:38 remove python-webkit:amd64 1.1.8-2ubuntu3 <none>
2013-03-19 21:59:02 remove pidgin-ppa:all 0.0.7 <none>
2013-03-19 21:59:03 remove pidgin-libnotify:amd64 0.14-4ubuntu11 <none>
2013-03-19 21:59:04 remove pidgin:amd64 1:2.10.6-0ubuntu2.2 <none>
2013-03-19 22:27:52 remove emesene:all 2.12.5+dfsg-1ubuntu2 <none>
2013-03-19 22:27:54 remove python-dnspython:all 1.10.0-1 <none>
2013-03-19 22:27:55 remove python-gupnp-igd:amd64 0.2.1-2build1 <none>
2013-03-19 22:27:55 remove python-indicate:amd64 12.10.1-0ubuntu1 <none>
2013-03-19 22:27:56 remove python-webkit:amd64 1.1.8-2ubuntu3 <none>
2013-03-20 19:17:24 remove account-plugin-aim:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-20 19:17:25 remove account-plugin-jabber:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-20 19:17:26 remove account-plugin-salut:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-20 19:17:27 remove account-plugin-yahoo:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-20 19:17:27 remove nautilus-sendto-empathy:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-20 19:17:28 remove mcp-account-manager-uoa:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-20 19:17:29 remove empathy:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-20 19:52:31 remove bcmwl-kernel-source:amd64 6.20.155.1+bdcom-0ubuntu0.0.1 <none>
2013-03-21 19:02:21 remove b43-fwcutter:amd64 1:015-14 <none>
2013-03-21 19:03:37 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-21 21:37:59 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 10:31:13 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 10:34:37 remove firmware-b43-installer:all 1:015-14 <none>
2013-03-22 10:34:37 remove firmware-b43legacy-installer:all 1:015-14 <none>
2013-03-22 10:53:44 remove b43-fwcutter:amd64 1:015-14 <none>
2013-03-22 10:58:44 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 11:14:03 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 11:19:02 remove broadcom-sta-common:all 5.100.82.112-7 <none>
2013-03-22 11:19:02 remove broadcom-sta-source:all 5.100.82.112-7 <none>
2013-03-22 11:35:57 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 11:58:19 remove firmware-b43-installer:all 1:015-14 <none>
2013-03-22 11:58:20 remove b43-fwcutter:amd64 1:015-14 <none>
2013-03-22 13:56:41 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 14:04:18 remove broadcom-sta-source:all 5.100.82.112-7 <none>
2013-03-22 14:08:09 remove broadcom-sta-common:all 5.100.82.112-7 <none>
2013-03-22 14:23:06 remove broadcom-sta-dkms:all 5.100.82.112-7 <none>
2013-03-22 15:37:56 remove fglrx:amd64 2:9.000-0ubuntu3 <none>
2013-03-22 15:45:31 remove linux-image-extra-3.8.0-030800-generic:amd64 3.8.0-030800.201302181935 <none>
2013-03-22 15:45:53 remove linux-image-3.8.0-030800-generic:amd64 3.8.0-030800.201302181935 <none>
2013-03-22 15:51:06 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 15:52:49 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 16:18:37 remove bcmwl-kernel-source:amd64 5.100.82.38+bdcom-0ubuntu6 <none>
2013-03-22 16:19:30 remove bcmwl-kernel-source:amd64 5.100.82.38+bdcom-0ubuntu6 <none>
2013-03-22 19:00:40 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 19:19:48 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 19:55:01 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-22 20:30:07 remove linux-image-extra-3.6.0-030600-generic:amd64 3.6.0-030600.201209302035 <none>
2013-03-22 20:30:26 remove linux-image-3.6.0-030600-generic:amd64 3.6.0-030600.201209302035 <none>
2013-03-22 20:33:25 remove bcmwl-kernel-source:amd64 5.100.82.38+bdcom-0ubuntu6 <none>
2013-03-22 20:59:38 remove bcmwl-kernel-source:amd64 5.100.82.38+bdcom-0ubuntu6 <none>
2013-03-22 23:02:19 remove firmware-b43legacy-installer:all 1:015-14 <none>
2013-03-22 23:02:19 remove firmware-b43-installer:all 1:015-14 <none>
2013-03-22 23:02:20 remove b43-fwcutter:amd64 1:015-14 <none>
2013-03-22 23:02:21 remove broadcom-sta-common:all 5.100.82.112-7 <none>
2013-03-22 23:02:21 remove broadcom-sta-source:all 5.100.82.112-7 <none>
2013-03-23 13:18:27 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-23 14:30:05 remove b43-fwcutter:amd64 1:015-14 <none>
2013-03-23 14:30:46 remove bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-28 15:36:51 remove account-plugin-icons:all 0.8-0ubuntu2 <none>
2013-03-28 15:36:52 remove account-plugin-windows-live:amd64 0.8-0ubuntu2 <none>
2013-03-28 15:36:53 remove finch:amd64 1:2.10.6-0ubuntu2.2 <none>
2013-03-28 15:36:54 remove module-assistant:all 0.11.4 <none>
2013-03-28 15:36:54 remove signon-plugin-password:amd64 8.43-0ubuntu1 <none>
2013-03-29 13:19:16 remove alacarte:all 3.5.5-0ubuntu1.1 <none>
2013-03-29 13:23:36 remove gnome-shell:amd64 3.6.2-0ubuntu0.2 <none>
2013-03-29 14:44:45 remove kwrite:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:44:46 remove libkopete4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:44:47 remove kubuntu-debug-installer:amd64 11.10ubuntu1 <none>
2013-03-29 14:44:47 remove qapt-batch:amd64 1.4.1-0ubuntu2 <none>
2013-03-29 14:44:49 remove polkit-kde-1:amd64 0.99.0-3ubuntu7 <none>
2013-03-29 14:44:59 remove libkolab0:amd64 0.2.1-0ubuntu2 <none>
2013-03-29 14:45:00 remove libkolabxml0:amd64 0.7.0-0ubuntu3 <none>
2013-03-29 14:45:00 remove libboost-thread1.49.0:amd64 1.49.0-3.1ubuntu1.2 <none>
2013-03-29 14:45:02 remove libxerces-c3.1:amd64 3.1.1-3 <none>
2013-03-29 14:45:03 remove kdepim-runtime:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:04 remove kde-runtime:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:05 remove libakonadi-contact4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:06 remove libakonadi-kabc4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:07 remove libakonadi-kcal4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:07 remove libmailtransport4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:08 remove libakonadi-kmime4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:08 remove libprison0:amd64 1.0+dfsg-1 <none>
2013-03-29 14:45:09 remove libdmtx0a:amd64 0.7.2-2ubuntu1 <none>
2013-03-29 14:45:10 remove libkcal4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:10 remove libkcalutils4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:11 remove libmicroblog4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:12 remove nepomuk-core:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:13 remove libnepomuksync4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:14 remove libnepomukcore4abi1:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:14 remove libqrencode3:amd64 3.3.0-2 <none>
2013-03-29 14:45:15 remove nepomuk-core-data:all 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:16 remove libkgapi0:amd64 0.4.2-0ubuntu1 <none>
2013-03-29 14:45:17 remove libkabc4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:45:17 remove libkresources4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 14:56:30 remove unity-2d:all 6.12.0-0ubuntu0.2 <none>
2013-03-29 14:56:54 remove unity-webapps-gmail:all 2.4.7 <none>
2013-03-29 14:56:55 remove unity-webapps-common:all 2.4.10-0ubuntu1 <none>
2013-03-29 14:57:33 remove libunity-2d-private0:all 6.12.0-0ubuntu0.2 <none>
2013-03-29 14:57:34 remove lightdm-remote-session-uccsconfigure:amd64 1.1-0ubuntu2 <none>
2013-03-29 14:57:34 remove ubuntu-desktop:amd64 1.287 <none>
2013-03-29 14:57:35 remove unity-2d-spread:all 6.12.0-0ubuntu0.2 <none>
2013-03-29 14:57:36 remove unity-2d-shell:all 6.12.0-0ubuntu0.2 <none>
2013-03-29 14:57:37 remove unity-2d-panel:all 6.12.0-0ubuntu0.2 <none>
2013-03-29 14:57:37 remove unity-2d-common:all 6.12.0-0ubuntu0.2 <none>
2013-03-29 14:57:38 remove unity:amd64 6.12.0-0ubuntu0.2 <none>
2013-03-29 14:58:08 remove unity-scope-video-remote:all 0.3.10-0ubuntu1 <none>
2013-03-29 14:58:09 remove unity-lens-video:all 0.3.14-0ubuntu1 <none>
2013-03-29 14:58:25 remove unity-scope-gdocs:all 0.7-0ubuntu1 <none>
2013-03-29 14:58:34 remove unity-lens-photos:all 0.9-0ubuntu1 <none>
2013-03-29 14:58:35 remove gir1.2-gdata-0.0:amd64 0.13.2-0ubuntu1 <none>
2013-03-29 14:58:35 remove gir1.2-goa-1.0:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 14:58:36 remove python3-oauthlib:all 0.3.0-0ubuntu1 <none>
2013-03-29 14:58:37 remove python3-crypto:amd64 2.6-2 <none>
2013-03-29 14:58:38 remove python3-httplib2:all 0.7.4-2 <none>
2013-03-29 14:59:38 remove gwibber:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 14:59:39 remove libgwibber-gtk3:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 15:12:34 remove linux-headers-3.5.0-25-generic:amd64 3.5.0-25.39 <none>
2013-03-29 15:12:45 remove linux-headers-3.5.0-25:all 3.5.0-25.39 <none>
2013-03-29 15:12:49 remove linux-headers-3.5.0-26-generic:amd64 3.5.0-26.42 <none>
2013-03-29 15:12:53 remove linux-headers-3.5.0-26:all 3.5.0-26.42 <none>
2013-03-29 15:12:58 remove linux-image-extra-3.5.0-25-generic:amd64 3.5.0-25.39 <none>
2013-03-29 15:13:15 remove linux-image-3.5.0-25-generic:amd64 3.5.0-25.39 <none>
2013-03-29 15:13:28 remove linux-image-extra-3.5.0-26-generic:amd64 3.5.0-26.42 <none>
2013-03-29 15:13:42 remove linux-image-3.5.0-26-generic:amd64 3.5.0-26.42 <none>
2013-03-29 15:14:06 remove account-plugin-salut:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-29 15:14:07 remove account-plugin-windows-live:amd64 0.8-0ubuntu2 <none>
2013-03-29 15:14:09 remove broadcom-sta-common:all 5.100.82.112-7 <none>
2013-03-29 15:14:10 remove broadcom-sta-dkms:all 5.100.82.112-7 <none>
2013-03-29 15:14:11 remove emesene:all 2.12.5+dfsg-1ubuntu2 <none>
2013-03-29 15:14:14 remove empathy:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-29 15:14:15 remove finch:amd64 1:2.10.6-0ubuntu2.2 <none>
2013-03-29 15:14:16 remove firmware-b43-installer:all 1:015-14 <none>
2013-03-29 15:14:18 remove firmware-b43legacy-installer:all 1:015-14 <none>
2013-03-29 15:14:18 remove gwibber:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 15:14:20 remove kde-runtime:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:21 remove kdepim-runtime:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:22 remove libakonadi-contact4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:23 remove libakonadi-kabc4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:24 remove libakonadi-kcal4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:25 remove libakonadi-kmime4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:29 remove libboost-thread1.49.0:amd64 1.49.0-3.1ubuntu1.2 <none>
2013-03-29 15:14:30 remove libdmtx0a:amd64 0.7.2-2ubuntu1 <none>
2013-03-29 15:14:31 remove libgwibber-gtk3:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 15:14:32 remove libkabc4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:34 remove libkcal4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:35 remove libkcalutils4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:36 remove libkgapi0:amd64 0.4.2-0ubuntu1 <none>
2013-03-29 15:14:37 remove libkolab0:amd64 0.2.1-0ubuntu2 <none>
2013-03-29 15:14:38 remove libkolabxml0:amd64 0.7.0-0ubuntu3 <none>
2013-03-29 15:14:39 remove libkopete4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:41 remove libkresources4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:42 remove libmailtransport4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:43 remove libmicroblog4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:44 remove libnepomukcore4abi1:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:46 remove libnepomuksync4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:14:47 remove libprison0:amd64 1.0+dfsg-1 <none>
2013-03-29 15:14:48 remove libqrencode3:amd64 3.3.0-2 <none>
2013-03-29 15:14:49 remove libxerces-c3.1:amd64 3.1.1-3 <none>
2013-03-29 15:14:50 remove lightdm-remote-session-uccsconfigure:amd64 1.1-0ubuntu2 <none>
2013-03-29 15:14:51 remove mcp-account-manager-uoa:amd64 3.6.0.3-0ubuntu1 <none>
2013-03-29 15:14:53 remove module-assistant:all 0.11.4 <none>
2013-03-29 15:14:54 remove pidgin-ppa:all 0.0.7 <none>
2013-03-29 15:14:56 remove stellarium:amd64 0.11.3-1 <none>
2013-03-29 15:14:58 remove unity-webapps-common:all 2.4.10-0ubuntu1 <none>
2013-03-29 15:14:59 remove unity-webapps-gmail:all 2.4.7 <none>
2013-03-29 15:15:04 remove finger:amd64 0.17-15 <none>
2013-03-29 15:15:05 remove gdm:amd64 3.6.1-0ubuntu1 <none>
2013-03-29 15:15:08 remove gir1.2-caribou-1.0:amd64 0.4.4-0ubuntu1 <none>
2013-03-29 15:15:08 remove gir1.2-mutter-3.0:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 15:15:09 remove gir1.2-clutter-1.0:amd64 1.12.0-0ubuntu1 <none>
2013-03-29 15:15:10 remove gir1.2-coglpango-1.0:amd64 1.10.4-0ubuntu1 <none>
2013-03-29 15:15:10 remove gir1.2-cogl-1.0:amd64 1.10.4-0ubuntu1 <none>
2013-03-29 15:15:11 remove gir1.2-gcr-3:amd64 3.6.0-0ubuntu1 <none>
2013-03-29 15:15:12 remove gir1.2-gck-1:amd64 3.6.0-0ubuntu1 <none>
2013-03-29 15:15:13 remove gir1.2-gdesktopenums-3.0:amd64 3.6.0-0ubuntu3 <none>
2013-03-29 15:15:13 remove gir1.2-gkbd-3.0:amd64 3.6.0-0ubuntu1 <none>
2013-03-29 15:15:14 remove gir1.2-ibus-1.0:amd64 1.4.1-7ubuntu1 <none>
2013-03-29 15:15:18 remove gir1.2-json-1.0:amd64 0.15.2-0ubuntu1 <none>
2013-03-29 15:15:19 remove gir1.2-telepathylogger-0.2:amd64 0.4.0-2~ubuntu12.10.0 <none>
2013-03-29 15:15:20 remove gir1.2-upowerglib-1.0:amd64 0.9.17-1build1 <none>
2013-03-29 15:15:20 remove gir1.2-xkl-1.0:amd64 5.2.1-1ubuntu2 <none>
2013-03-29 15:15:21 remove gjs:amd64 1.34.0-0ubuntu1 <none>
2013-03-29 15:15:22 remove gnome-contacts:amd64 3.6.0-0ubuntu2 <none>
2013-03-29 15:15:23 remove gstreamer1.0-plugins-base:amd64 1.0.1-1 <none>
2013-03-29 15:15:24 remove icoutils:amd64 0.30.0-1 <none>
2013-03-29 15:15:25 remove kde-runtime-data:all 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:15:27 remove libaudit0:amd64 1.7.18-1ubuntu1 <none>
2013-03-29 15:15:27 remove libcaribou0:amd64 0.4.4-0ubuntu1 <none>
2013-03-29 15:15:28 remove libcaribou-common:all 0.4.4-0ubuntu1 <none>
2013-03-29 15:15:29 remove libgjs0c:amd64 1.34.0-0ubuntu1 <none>
2013-03-29 15:15:29 remove libgstreamer-plugins-base1.0-0:amd64 1.0.1-1 <none>
2013-03-29 15:15:30 remove libgstreamer1.0-0:amd64 1.0.1-1 <none>
2013-03-29 15:15:30 remove libkdesu5:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:15:31 remove libkidletime4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:15:32 remove libkmediaplayer4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:15:32 remove libknotifyconfig4:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:15:33 remove libmozjs185-1.0:amd64 1.8.5-1.0.0-0ubuntu8 <none>
2013-03-29 15:15:33 remove libmutter0:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 15:15:34 remove libntrack-qt4-1:amd64 016-1.1 <none>
2013-03-29 15:15:35 remove libqapt-runtime:amd64 1.4.1-0ubuntu2 <none>
2013-03-29 15:15:35 remove libqapt1:amd64 1.4.1-0ubuntu2 <none>
2013-03-29 15:15:36 remove mutter-common:all 3.6.2-0ubuntu0.1 <none>
2013-03-29 15:15:37 remove oxygen-icon-theme:all 4:4.9.2-0ubuntu1 <none>
2013-03-29 15:15:38 remove plasma-scriptengine-javascript:amd64 4:4.9.5-0ubuntu0.1 <none>
2013-03-29 15:15:39 remove shared-desktop-ontologies:all 0.10.0-1 <none>
2013-03-29 15:15:40 remove libntrack0:amd64 016-1.1 <none>
2013-03-29 15:15:41 remove ntrack-module-libnl-0:amd64 016-1.1 <none>
2013-03-29 15:22:26 remove htop:amd64 1.0.1-4 <none>
2013-03-29 19:50:20 remove nautilus-share:amd64 0.7.3-1ubuntu3 <none>
2013-03-29 19:50:20 remove apturl:amd64 0.5.1ubuntu6 <none>
2013-03-29 19:50:22 remove unity-2d:all 6.12.0-0ubuntu0.2 <none>
2013-03-29 19:50:22 remove unity:amd64 6.12.0-0ubuntu0.2 <none>
2013-03-29 19:50:23 remove indicator-appmenu:amd64 12.10.3-0ubuntu2.1 <none>
2013-03-29 19:50:25 remove libbamf3-0:amd64 0.3.6-0ubuntu2 <none>
2013-03-29 19:50:26 remove ginn:amd64 0.2.6-0ubuntu1 <none>
2013-03-29 19:50:27 remove libbamf0:amd64 0.3.6-0ubuntu2 <none>
2013-03-29 19:50:28 remove libqtbamf1:amd64 0.2.4-0ubuntu2 <none>
2013-03-29 19:50:29 remove bamfdaemon:amd64 0.3.6-0ubuntu2 <none>
2013-03-29 19:50:30 remove brasero:amd64 3.4.1-0ubuntu3.1 <none>
2013-03-29 19:50:31 remove brasero-cdrkit:amd64 3.4.1-0ubuntu3.1 <none>
2013-03-29 19:50:32 remove clamtk:all 4.41-1 <none>
2013-03-29 19:50:33 remove epiphany-extensions:amd64 3.6.0-0ubuntu2 <none>
2013-03-29 19:50:35 remove epiphany-browser:amd64 3.6.1-0ubuntu1 <none>
2013-03-29 19:50:37 remove libfolks-eds25:amd64 0.7.4.1-0ubuntu1 <none>
2013-03-29 19:50:38 remove evolution-data-server:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 19:50:39 remove xul-ext-unity:all 2.4.4-0ubuntu0.1 <none>
2013-03-29 19:50:40 remove xul-ext-websites-integration:all 2.3.5-0ubuntu1 <none>
2013-03-29 19:50:41 remove indicator-datetime:amd64 12.10.2-0ubuntu3.1 <none>
2013-03-29 19:50:42 remove gimp:amd64 2.8.2-1ubuntu1.1 <none>
2013-03-29 19:50:44 remove unity-lens-photos:all 0.9-0ubuntu1 <none>
2013-03-29 19:50:45 remove gir1.2-gdata-0.0:amd64 0.13.2-0ubuntu1 <none>
2013-03-29 19:50:45 remove gir1.2-goa-1.0:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 19:50:46 remove rhythmbox-plugins:amd64 2.97-1ubuntu6.1 <none>
2013-03-29 19:50:47 remove rhythmbox-plugin-zeitgeist:all 2.97-1ubuntu6.1 <none>
2013-03-29 19:50:48 remove rhythmbox-plugin-magnatune:amd64 2.97-1ubuntu6.1 <none>
2013-03-29 19:50:49 remove rhythmbox-plugin-cdrecorder:amd64 2.97-1ubuntu6.1 <none>
2013-03-29 19:50:49 remove unity-scope-musicstores:amd64 6.8.1-0ubuntu1 <none>
2013-03-29 19:50:50 remove rhythmbox-ubuntuone:all 4.0.0-0ubuntu1 <none>
2013-03-29 19:50:51 remove rhythmbox:amd64 2.97-1ubuntu6.1 <none>
2013-03-29 19:50:52 remove gir1.2-rb-3.0:amd64 2.97-1ubuntu6.1 <none>
2013-03-29 19:50:53 remove ubuntu-tweak:all 0.8.3-1~quantal1 <none>
2013-03-29 19:50:55 remove software-center:all 5.4.1.4 <none>
2013-03-29 19:50:57 remove gir1.2-webkit-3.0:amd64 1.10.2-0ubuntu0.12.10.1 <none>
2013-03-29 19:50:58 remove unity-scope-video-remote:all 0.3.10-0ubuntu1 <none>
2013-03-29 19:50:58 remove ubuntuone-control-panel-qt:all 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:00 remove ubuntu-sso-client-qt:all 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:01 remove ubuntuone-control-panel:all 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:01 remove ubuntuone-client-gnome:amd64 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:02 remove gir1.2-ubuntuoneui-3.0:amd64 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:03 remove libubuntuoneui-3.0-1:amd64 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:04 remove libsyncdaemon-1.0-1:amd64 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:06 remove ubuntuone-client:all 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:07 remove oneconf:all 0.2.9.1 <none>
2013-03-29 19:51:08 remove ubuntu-sso-client:all 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:09 remove python-ubuntuone-control-panel:all 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:10 remove python-ubuntu-sso-client:all 4.0.0-0ubuntu1 <none>
2013-03-29 19:51:11 remove gir1.2-soup-2.4:amd64 2.40.0-0ubuntu1 <none>
2013-03-29 19:51:12 remove totem-plugins:amd64 3.4.3-0ubuntu5 <none>
2013-03-29 19:51:12 remove gir1.2-totem-1.0:amd64 3.4.3-0ubuntu5 <none>
2013-03-29 19:51:13 remove gir1.2-totem-plparser-1.0:amd64 3.4.3-0ubuntu1 <none>
2013-03-29 19:51:14 remove shotwell:amd64 0.13.1-0ubuntu1 <none>
2013-03-29 19:51:15 remove librhythmbox-core6:amd64 2.97-1ubuntu6.1 <none>
2013-03-29 19:51:16 remove libedata-book-1.2-15:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 19:51:17 remove gnome-online-accounts:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 19:51:18 remove gnome-control-center-signon:amd64 0.0.18-0ubuntu1.1 <none>
2013-03-29 19:51:19 remove indicator-power:amd64 12.10.2-0ubuntu1 <none>
2013-03-29 19:51:20 remove gnome-control-center:amd64 1:3.4.2-0ubuntu19.1 <none>
2013-03-29 19:51:21 remove libgdata13:amd64 0.13.2-0ubuntu1 <none>
2013-03-29 19:51:22 remove libgoa-1.0-0:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 19:51:23 remove gnome-session-fallback:all 3.6.0-0ubuntu1.1 <none>
2013-03-29 19:51:24 remove metacity:amd64 1:2.34.8-0ubuntu4 <none>
2013-03-29 19:51:25 remove lightdm-remote-session-freerdp:amd64 1.0-0ubuntu2 <none>
2013-03-29 19:51:26 remove zenity:amd64 3.4.0-2 <none>
2013-03-29 19:51:27 remove ubuntu-docs:all 12.10.3 <none>
2013-03-29 19:51:40 remove gnome-user-guide:all 3.4.2-1 <none>
2013-03-29 19:51:44 remove yelp:amd64 3.6.0-0ubuntu1 <none>
2013-03-29 19:51:46 remove libyelp0:amd64 3.6.0-0ubuntu1 <none>
2013-03-29 19:51:47 remove libwebkitgtk-3.0-0:amd64 1.10.2-0ubuntu0.12.10.1 <none>
2013-03-29 19:51:48 remove libwebkitgtk-1.0-0:amd64 1.10.2-0ubuntu0.12.10.1 <none>
2013-03-29 19:51:49 remove gvfs-backends:amd64 1.14.2-0ubuntu0.1 <none>
2013-03-29 19:51:50 remove vino:amd64 3.6.0-0ubuntu1.1 <none>
2013-03-29 19:51:51 remove seahorse:amd64 3.6.2-0ubuntu1 <none>
2013-03-29 19:51:53 remove remote-login-service:amd64 1.0.0-0ubuntu1.1 <none>
2013-03-29 19:51:54 remove thunderbird-gnome-support:amd64 17.0.4+build1-0ubuntu0.12.10.1 <none>
2013-03-29 19:51:55 remove libedata-cal-1.2-18:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 19:51:56 remove gnome-applets:amd64 3.5.92-0ubuntu1 <none>
2013-03-29 19:51:57 remove gnome-panel:amd64 1:3.6.0-0ubuntu2 <none>
2013-03-29 19:51:58 remove libecal-1.2-15:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 19:51:59 remove nautilus-sendto:amd64 3.6.0-0ubuntu1 <none>
2013-03-29 19:52:00 remove libebook-1.2-14:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 19:52:01 remove libebackend-1.2-5:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 19:52:02 remove libedataserver-1.2-17:amd64 3.6.2-0ubuntu0.1 <none>
2013-03-29 19:52:03 remove totem-mozilla:amd64 3.4.3-0ubuntu5 <none>
2013-03-29 19:52:04 remove totem:amd64 3.4.3-0ubuntu5 <none>
2013-03-29 19:52:05 remove pidgin-libnotify:amd64 0.14-4ubuntu11 <none>
2013-03-29 19:52:06 remove pidgin:amd64 1:2.10.6-0ubuntu2.2 <none>
2013-03-29 19:52:07 remove telepathy-haze:amd64 0.6.0-1 <none>
2013-03-29 19:52:08 remove libpurple0:amd64 1:2.10.6-0ubuntu2.2 <none>
2013-03-29 19:52:09 remove libtelepathy-farstream2:amd64 0.4.0-3 <none>
2013-03-29 19:52:10 remove libfarstream-0.1-0:amd64 0.1.2-1ubuntu1 <none>
2013-03-29 19:52:11 remove gnome-media:amd64 3.4.0-0ubuntu4 <none>
2013-03-29 19:52:15 remove gstreamer0.10-plugins-good:amd64 0.10.31-3ubuntu1.2 <none>
2013-03-29 19:52:16 remove hardinfo:amd64 0.5.1-1.1ubuntu5 <none>
2013-03-29 19:52:18 remove unity-lens-shopping:amd64 6.8.0-0ubuntu1 <none>
2013-03-29 19:52:18 remove telepathy-salut:amd64 0.8.0-2 <none>
2013-03-29 19:52:19 remove telepathy-gabble:amd64 0.16.1-2 <none>
2013-03-29 19:52:20 remove network-manager-gnome:amd64 0.9.6.2-0ubuntu6 <none>
2013-03-29 19:52:21 remove network-manager:amd64 0.9.6.0-0ubuntu7 <none>
2013-03-29 19:52:28 remove libbrasero-media3-1:amd64 3.4.1-0ubuntu3.1 <none>
2013-03-29 19:52:29 remove libtotem0:amd64 3.4.3-0ubuntu5 <none>
2013-03-29 19:52:30 remove libtotem-plparser17:amd64 3.4.3-0ubuntu1 <none>
2013-03-29 19:52:31 remove librest-0.7-0:amd64 0.7.90-0ubuntu1 <none>
2013-03-29 19:52:32 remove libgweather-3-1:amd64 3.6.0-0ubuntu1 <none>
2013-03-29 19:52:33 remove libsoup-gnome2.4-1:amd64 2.40.0-0ubuntu1 <none>
2013-03-29 19:52:34 remove gstreamer0.10-nice:amd64 0.1.2-1 <none>
2013-03-29 19:52:35 remove libnice10:amd64 0.1.2-1 <none>
2013-03-29 19:52:36 remove libgupnp-igd-1.0-4:amd64 0.2.1-2build1 <none>
2013-03-29 19:52:37 remove libgupnp-1.0-4:amd64 0.18.4-0ubuntu1 <none>
2013-03-29 19:52:38 remove libgssdp-1.0-3:amd64 0.12.2.1-1ubuntu1 <none>
2013-03-29 19:52:39 remove libdmapsharing-3.0-2:amd64 2.9.15-1 <none>
2013-03-29 19:52:42 remove libunity-webapps0:amd64 2.4.1-0ubuntu3.2 <none>
2013-03-29 19:52:44 remove unity-webapps-service:amd64 2.4.1-0ubuntu3.2 <none>
2013-03-29 19:52:47 remove geoclue-ubuntu-geoip:amd64 1.0.0-0ubuntu1 <none>
2013-03-29 19:52:48 remove libsoup2.4-1:amd64 2.40.0-0ubuntu1 <none>
2013-03-29 19:52:49 remove glib-networking:amd64 2.34.0-0ubuntu1 <none>
2013-03-29 19:52:50 remove glib-networking-services:amd64 2.34.0-0ubuntu1 <none>
2013-03-29 19:52:51 remove libavutil-extra-51:amd64 6:0.8.5ubuntu0.12.10.1 <none>

```for the : awk '$1=="2013-03-30" && $3=="remove" {print $4}' /var/lib/dpkg.log


				
simo@Simo:~$ awk '$1=="2013-03-30" && $3=="remove" {print $4}' /var/lib/dpkg.log
awk: fatal: cannot open file `/var/lib/dpkg.log' for reading (No such file or directory)


the command : sudo apt-get update && sudo apt-get install --fix-policy  wont do nothing since i cant get connected

im able to log in only via ctrl+alt+f2 at the login screen , after login and password startx take me to the desktop, i cant get connected , no wifi there :

simo@Simo:~$ iwconfig
wwan0     no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


lo        no wireless extensions.

---

### Post by stinkeye on 2013-03-30
The command has a typo...
```
awk '$1=="2013-03-30" && $3=="remove" {print $4}' /var/[COLOR="#FF0000"]lib[/COLOR]/dpkg.log
```

Should be...
```
awk '$1=="2013-03-[COLOR="#0000FF"]30[/COLOR]" && $3=="remove" {print $4}' /var/[COLOR="#FF0000"]log[/COLOR]/dpkg.log
```

and should probably use 2013-03-[COLOR="#0000FF"]29[/COLOR] for the removal date.

Could try(once network is up) 
```
sudo apt-get install [COLOR="#FF0000"]-s[/COLOR] ubuntu-desktop
```

The ubuntu-desktop package depends on all of the packages in the Ubuntu desktop system and can be 
used to reinstall default packages.
The [COLOR="#FF0000"]-s[/COLOR] option simulates the action without installing anything.

Remove the [COLOR="#FF0000"]-s[/COLOR] option to install the packages.

---

### Post by schragge on 2013-03-30
> **bou3lam said:**
> simo@Simo:~$ awk '$1=="2013-03-30" && $3=="remove" {print $4}' /var/lib/dpkg.log
awk: fatal: cannot open file `/var/lib/dpkg.log' for reading (No such file or directory)
Sorry, my fault. This should have been
```
awk '$1=="2013-03-29" &&$2~/^19:/&&$3=="remove" {print $4}' /var/[COLOR=#ff0000]log[/COLOR]/dpkg.log
```

Download the file below:
[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.6.0-0ubuntu7_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.6.0-0ubuntu7_amd64.deb)
Copy it onto your Ubuntu machine (I presume you can mount a USB stick), and install with
```
sudo dpkg -i network-manager_0.9.6.0-0ubuntu7_amd64.deb
``` Hopefully, you will be able to start your network then.

---

### Post by bou3lam on 2013-03-30
here the output :

```

simo@Simo:~$ awk '$1=="2013-03-29" && $3=="remove" {print $4}' /var/log/dpkg.log
alacarte:all
gnome-shell:amd64
kwrite:amd64
libkopete4:amd64
kubuntu-debug-installer:amd64
qapt-batch:amd64
polkit-kde-1:amd64
libkolab0:amd64
libkolabxml0:amd64
libboost-thread1.49.0:amd64
libxerces-c3.1:amd64
kdepim-runtime:amd64
kde-runtime:amd64
libakonadi-contact4:amd64
libakonadi-kabc4:amd64
libakonadi-kcal4:amd64
libmailtransport4:amd64
libakonadi-kmime4:amd64
libprison0:amd64
libdmtx0a:amd64
libkcal4:amd64
libkcalutils4:amd64
libmicroblog4:amd64
nepomuk-core:amd64
libnepomuksync4:amd64
libnepomukcore4abi1:amd64
libqrencode3:amd64
nepomuk-core-data:all
libkgapi0:amd64
libkabc4:amd64
libkresources4:amd64
unity-2d:all
unity-webapps-gmail:all
unity-webapps-common:all
libunity-2d-private0:all
lightdm-remote-session-uccsconfigure:amd64
ubuntu-desktop:amd64
unity-2d-spread:all
unity-2d-shell:all
unity-2d-panel:all
unity-2d-common:all
unity:amd64
unity-scope-video-remote:all
unity-lens-video:all
unity-scope-gdocs:all
unity-lens-photos:all
gir1.2-gdata-0.0:amd64
gir1.2-goa-1.0:amd64
python3-oauthlib:all
python3-crypto:amd64
python3-httplib2:all
gwibber:amd64
libgwibber-gtk3:amd64
linux-headers-3.5.0-25-generic:amd64
linux-headers-3.5.0-25:all
linux-headers-3.5.0-26-generic:amd64
linux-headers-3.5.0-26:all
linux-image-extra-3.5.0-25-generic:amd64
linux-image-3.5.0-25-generic:amd64
linux-image-extra-3.5.0-26-generic:amd64
linux-image-3.5.0-26-generic:amd64
account-plugin-salut:amd64
account-plugin-windows-live:amd64
broadcom-sta-common:all
broadcom-sta-dkms:all
emesene:all
empathy:amd64
finch:amd64
firmware-b43-installer:all
firmware-b43legacy-installer:all
gwibber:amd64
kde-runtime:amd64
kdepim-runtime:amd64
libakonadi-contact4:amd64
libakonadi-kabc4:amd64
libakonadi-kcal4:amd64
libakonadi-kmime4:amd64
libboost-thread1.49.0:amd64
libdmtx0a:amd64
libgwibber-gtk3:amd64
libkabc4:amd64
libkcal4:amd64
libkcalutils4:amd64
libkgapi0:amd64
libkolab0:amd64
libkolabxml0:amd64
libkopete4:amd64
libkresources4:amd64
libmailtransport4:amd64
libmicroblog4:amd64
libnepomukcore4abi1:amd64
libnepomuksync4:amd64
libprison0:amd64
libqrencode3:amd64
libxerces-c3.1:amd64
lightdm-remote-session-uccsconfigure:amd64
mcp-account-manager-uoa:amd64
module-assistant:all
pidgin-ppa:all
stellarium:amd64
unity-webapps-common:all
unity-webapps-gmail:all
finger:amd64
gdm:amd64
gir1.2-caribou-1.0:amd64
gir1.2-mutter-3.0:amd64
gir1.2-clutter-1.0:amd64
gir1.2-coglpango-1.0:amd64
gir1.2-cogl-1.0:amd64
gir1.2-gcr-3:amd64
gir1.2-gck-1:amd64
gir1.2-gdesktopenums-3.0:amd64
gir1.2-gkbd-3.0:amd64
gir1.2-ibus-1.0:amd64
gir1.2-json-1.0:amd64
gir1.2-telepathylogger-0.2:amd64
gir1.2-upowerglib-1.0:amd64
gir1.2-xkl-1.0:amd64
gjs:amd64
gnome-contacts:amd64
gstreamer1.0-plugins-base:amd64
icoutils:amd64
kde-runtime-data:all
libaudit0:amd64
libcaribou0:amd64
libcaribou-common:all
libgjs0c:amd64
libgstreamer-plugins-base1.0-0:amd64
libgstreamer1.0-0:amd64
libkdesu5:amd64
libkidletime4:amd64
libkmediaplayer4:amd64
libknotifyconfig4:amd64
libmozjs185-1.0:amd64
libmutter0:amd64
libntrack-qt4-1:amd64
libqapt-runtime:amd64
libqapt1:amd64
mutter-common:all
oxygen-icon-theme:all
plasma-scriptengine-javascript:amd64
shared-desktop-ontologies:all
libntrack0:amd64
ntrack-module-libnl-0:amd64
htop:amd64
nautilus-share:amd64
apturl:amd64
unity-2d:all
unity:amd64
indicator-appmenu:amd64
libbamf3-0:amd64
ginn:amd64
libbamf0:amd64
libqtbamf1:amd64
bamfdaemon:amd64
brasero:amd64
brasero-cdrkit:amd64
clamtk:all
epiphany-extensions:amd64
epiphany-browser:amd64
libfolks-eds25:amd64
evolution-data-server:amd64
xul-ext-unity:all
xul-ext-websites-integration:all
indicator-datetime:amd64
gimp:amd64
unity-lens-photos:all
gir1.2-gdata-0.0:amd64
gir1.2-goa-1.0:amd64
rhythmbox-plugins:amd64
rhythmbox-plugin-zeitgeist:all
rhythmbox-plugin-magnatune:amd64
rhythmbox-plugin-cdrecorder:amd64
unity-scope-musicstores:amd64
rhythmbox-ubuntuone:all
rhythmbox:amd64
gir1.2-rb-3.0:amd64
ubuntu-tweak:all
software-center:all
gir1.2-webkit-3.0:amd64
unity-scope-video-remote:all
ubuntuone-control-panel-qt:all
ubuntu-sso-client-qt:all
ubuntuone-control-panel:all
ubuntuone-client-gnome:amd64
gir1.2-ubuntuoneui-3.0:amd64
libubuntuoneui-3.0-1:amd64
libsyncdaemon-1.0-1:amd64
ubuntuone-client:all
oneconf:all
ubuntu-sso-client:all
python-ubuntuone-control-panel:all
python-ubuntu-sso-client:all
gir1.2-soup-2.4:amd64
totem-plugins:amd64
gir1.2-totem-1.0:amd64
gir1.2-totem-plparser-1.0:amd64
shotwell:amd64
librhythmbox-core6:amd64
libedata-book-1.2-15:amd64
gnome-online-accounts:amd64
gnome-control-center-signon:amd64
indicator-power:amd64
gnome-control-center:amd64
libgdata13:amd64
libgoa-1.0-0:amd64
gnome-session-fallback:all
metacity:amd64
lightdm-remote-session-freerdp:amd64
zenity:amd64
ubuntu-docs:all
gnome-user-guide:all
yelp:amd64
libyelp0:amd64
libwebkitgtk-3.0-0:amd64
libwebkitgtk-1.0-0:amd64
gvfs-backends:amd64
vino:amd64
seahorse:amd64
remote-login-service:amd64
thunderbird-gnome-support:amd64
libedata-cal-1.2-18:amd64
gnome-applets:amd64
gnome-panel:amd64
libecal-1.2-15:amd64
nautilus-sendto:amd64
libebook-1.2-14:amd64
libebackend-1.2-5:amd64
libedataserver-1.2-17:amd64
totem-mozilla:amd64
totem:amd64
pidgin-libnotify:amd64
pidgin:amd64
telepathy-haze:amd64
libpurple0:amd64
libtelepathy-farstream2:amd64
libfarstream-0.1-0:amd64
gnome-media:amd64
gstreamer0.10-plugins-good:amd64
hardinfo:amd64
unity-lens-shopping:amd64
telepathy-salut:amd64
telepathy-gabble:amd64
network-manager-gnome:amd64
network-manager:amd64
libbrasero-media3-1:amd64
libtotem0:amd64
libtotem-plparser17:amd64
librest-0.7-0:amd64
libgweather-3-1:amd64
libsoup-gnome2.4-1:amd64
gstreamer0.10-nice:amd64
libnice10:amd64
libgupnp-igd-1.0-4:amd64
libgupnp-1.0-4:amd64
libgssdp-1.0-3:amd64
libdmapsharing-3.0-2:amd64
libunity-webapps0:amd64
unity-webapps-service:amd64
geoclue-ubuntu-geoip:amd64
libsoup2.4-1:amd64
glib-networking:amd64
glib-networking-services:amd64
libavutil-extra-51:amd64



```

i will now install the network manager

---

### Post by schragge on 2013-03-30
You also will need libsoup2.4 for network-manager to work:
[http://archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.40.0-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.40.0-0ubuntu1_amd64.deb)

---

### Post by bou3lam on 2013-03-30
cant install network manager :
```
 simo@Simo:~/Desktop$ sudo dpkg -i network-manager_0.9.6.0-0ubuntu7_amd64.deb[sudo] password for simo: 
Selecting previously unselected package network-manager.
(Reading database ... 230166 files and directories currently installed.)
Unpacking network-manager (from network-manager_0.9.6.0-0ubuntu7_amd64.deb) ...
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on libsoup2.4-1 (>= 2.26.1); however:
  Package libsoup2.4-1 is not installed.


dpkg: error processing network-manager (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 network-manager



```

[COLOR=#000000]You also will need libsoup2.4 for network-manager to work:[/COLOR]
[http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb]("http://archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.40.0-0ubuntu1_amd64.deb")

install it the same way as network manager ?

---

### Post by schragge on 2013-03-30
Yep.

---

### Post by bou3lam on 2013-03-30
[COLOR=#000000]libsoup2.4 require glib-networking [/COLOR]2.32.0 , i cant find it, i hope glib networking wont require other things :confused:
i installed glib-networking-services_2.34.0-0ubuntu1_amd64 and when i tried libsoup its asked for [COLOR=#000000]glib-networking [/COLOR]2.32.0 and didnt install

---

### Post by schragge on 2013-03-30
*glib-networking* requires *glib-networking-services* which also has been removed. Remember that [COLOR=#FF0000]*ices*[/COLOR] part?
[http://archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking-services_2.34.0-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking-services_2.34.0-0ubuntu1_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking_2.34.0-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glib-networking/glib-networking_2.34.0-0ubuntu1_amd64.deb)

---

### Post by bou3lam on 2013-03-30
im connected now via the broken install, what to now please ? many thanks for your help

---

### Post by bou3lam on 2013-03-30
> **stinkeye said:**
> 

Could try(once network is up) 
```
sudo apt-get install [COLOR=#FF0000]-s[/COLOR] ubuntu-desktop
```



Remove the [COLOR=#FF0000]-s[/COLOR] option to install the packages.


thanks alot guys all [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] system up and runing good again [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] after the ```
sudo apt-get install ubuntu-desktop
``` i had some login failure, solved it by reading other forum posts,just installing gnome shell solved it, and the whole problem was solved by sudo apt-get install ubuntu-desktop after the network manager install , thanks all again [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

---

### Post by schragge on 2013-04-01
> **ManamiVixen said:**
> If the mediabuntu was a seperate ppa, you could use the ppa-purge command provided by ppa-purge to remove uneeded ppa's and their packages at the same time.Yes, [ppa-purge]("http://manpages.ubuntu.com/manpages/precise/en/man1/ppa-purge.1.html") is the best way to remove all packages installed from a PPA. Unfortunately, [medibuntu]("http://www.medibuntu.org/") is not a PPA and cannot be, for legal reasons.

The most straightforward way to purge everything installed from medibuntu is using [synaptic]("http://manpages.ubuntu.com/manpages/precise/en/man8/synaptic.8.html"). You can filter packages in Synaptic by origin, so it's basically matter of clicking on **Origin** in the category selector pane on the left and selecting medibuntu repository, then sorting packages by their status (first field in the package selector pane), installed first, and marking all installed packages for complete removal (click on the first package, Shift+click on the last, right click and select **Mark for complete removal**). You also may define a custom filter either from inside Synaptic (Settings>Filters, click on the **New** button) or write it in a text file:
```

filter "Medibuntu" {
  status::flags 0x401;
  pattern::patterns {Origin; "medibuntu"; false;};
};

```
Save it as *medibuntu.filter* to your home folder, then start Synaptic with
```
gksudo synaptic -f ~/medibuntu.filter -iMedibuntu
```

Doing the same from the command line is relatively easy as long as you don't mix packages for different architectures (e.g. 32-bit and 64-bit packages, see [Multiarch]("http://wiki.debian.org/Multiarch")). 

The command below will do it only for the native architecture:
```
sudo apt-get purge `sed -n s/^Package://p /var/lib/apt/lists/*.medibuntu.*_Packages`
```

In the multiarch environment, the following commands won't purge packages that have siblings from a foreign architecture installed:
```

sed -nr 's/^Package:\s*(.*)/\1 purge/p' /var/lib/apt/lists/*.medibuntu.*_Packages|
sudo dpkg --set-selections 2>/dev/null
sudo dpkg -Pa

```
To include those packages, the sed expression gets rather unwieldly:
```

sed -n '
        /^Package:\s*/,/^$/{
                //{s///;h};/^Architecture:\s*/{s///;H;g;s/[ \t]*\n/:/;s/$/ purge/p}
}' /var/lib/apt/lists/packages.medibuntu.org_*_Packages

```
And awk is not much better:
```

awk -F':[ \t]*' '/^Package:/,/^$/{
        if(/^Package:/){p=$2;a=""}
        if(/^Architecture:/)a=":"$2
        if(/^$/)print p a
}' /var/lib/apt/lists/packages.medibuntu.org_*_Packages

```
Starting from *quantal*, installing [aptitude]("http://manpages.ubuntu.com/manpages/precise/en/man8/aptitude.8.html") will help. The following aptitude command will purge all packages from medibuntu repository:
```
sudo aptitude purge ~OMedibuntu
```
Hopefully this also works the same way in *precise*, but I'm not quite sure as aptitude got the full multiarch support after *precise* was released. 

In *precise*, the best command line tool I could come up with for this task (or rather a set of tools) are [dctrl-tools]("http://packages.ubuntu.com/quantal/dctrl-tools"), particularly [grep-dctrl]("http://manpages.ubuntu.com/manpages/precise/en/man1/grep-dctrl.1.html") and [tbl-dctrl]("http://manpages.ubuntu.com/manpages/precise/en/man1/tbl-dctrl.1.html")
```

sudo apt-get purge `grep-dctrl -sPackage,Architecture '' /var/lib/apt/lists/*.medibuntu.*Packages|tbl-dctrl -Hd:`

```
Alternatively, do it the *ppa-purge* way:
```

sed -n s/^Package://p /var/lib/apt/lists/*.medibuntu.*Packages|sort -u|xargs -r dpkg-query -W 2>/dev/null|awk '$2,$0=$1" purge"'|
sudo dpkg --set-selections
sudo dpkg -Pa

```
In the case of Medibuntu, there is a workaround that may not work with other 3rd party repositories. Maintainer of all packages but one in Medibuntu is *Medibuntu Packaging Team*, so it's possible to select just packages maintained by them:
```

dpkg-query -Wf'${binary:Package}${Maintainer;9}\n'|sed -n 's/Medibuntu$/ purge/p'|sudo dpkg --set-selections
sudo dpkg -Pa

```
The only package in Medibuntu repsitory that has another maintainer is *medibuntu-keyring*. To include it, run
```

sudo apt-get purge medibuntu-keyring `dpkg-query -Wf'${binary:Package}${Maintainer;9}\n'|sed -n 's/Medibuntu$//p'`

```

---

### Post by stinkeye on 2013-04-02
> **bou3lam said:**
> thanks alot guys all [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] system up and runing good again [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] after the ```
sudo apt-get install ubuntu-desktop
``` i had some login failure, solved it by reading other forum posts,just installing gnome shell solved it, and the whole problem was solved by sudo apt-get install ubuntu-desktop after the network manager install , thanks all again [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]
As you installed gnome-shell you probably set gdm as your login manager.
lightdm should now be installed as it's a dependency of ubuntu-desktop and if you like you can switch back by running...
```
sudo dpkg-reconfigure gdm
```

---

