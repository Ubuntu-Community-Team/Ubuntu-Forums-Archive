---
title: "After updates gnome-shell lost panel and dash"
date: 2011-06-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-06-30
If that's what it's called :-)
Can't do anything from the desktop :-(

Unity boots ok though :-) I can use that!
In fact, I am using it.

---

### Post by dino99 on 2011-06-30
seems its your day :)

purge and reinstall gnome-shell & like

or gnome-shell --replace

---

### Post by Quackers on 2011-06-30
It does doesn't it :-)

No terminal, no ctrl+Alt+t and no Alt+F2 :-(

---

### Post by paul_in_london on 2011-06-30
> **Quackers said:**
> If that's what it's called :-)
Can't do anything from the desktop :-(

Unity boots ok though :-) I can use that!
In fact, I am using it.

@Quackers. It's worse than that for me!:lolflag:

All good yesterday, but now gnome-shell fails to load after login and when I try to load it manually:

```
paul@oneiric:~$ gnome-shell --replace &
paul@oneiric:~$ 
(gnome-shell:4468): Clutter-CRITICAL **: Unable to initialize Clutter: XServer appears to lack the required GLX support
Window manager error: Unable to initialize Clutter.
```

No difference if I disable the **ricotz** ppa.

Are you using the **xorg-edgers** ppa? Something in today's updates has broken things:

```
Aptitude 0.6.4: log report
Thu, Jun 30 2011 19:13:24 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 44 packages, and remove 3 packages.
68.7 MB of disk space will be freed
===============================================================================
[REMOVE, NOT USED] libaudit0
[REMOVE, NOT USED] libindicator3
[REMOVE, NOT USED] libtxc-dxtn0
[INSTALL, DEPENDENCIES] libgbm1
[INSTALL, DEPENDENCIES] libllvm2.9
[INSTALL, DEPENDENCIES] libopenvg1-mesa
[UPGRADE] apt 0.8.15ubuntu1 -> 0.8.15.1ubuntu1
[UPGRADE] apt-transport-https 0.8.15ubuntu1 -> 0.8.15.1ubuntu1
[UPGRADE] apt-utils 0.8.15ubuntu1 -> 0.8.15.1ubuntu1
[UPGRADE] chromium-browser 14.0.806.0~svn20110629r90908-0ubuntu1~ucd1~natty -> 14.0.807.0~svn20110630r91077-0ubuntu1~ucd1~natty
[UPGRADE] chromium-browser-l10n 14.0.806.0~svn20110629r90908-0ubuntu1~ucd1~natty -> 14.0.807.0~svn20110630r91077-0ubuntu1~ucd1~natty
[UPGRADE] chromium-codecs-ffmpeg 14.0.806.0~svn20110629r90908-0ubuntu1~ucd1~natty -> 14.0.807.0~svn20110630r91077-0ubuntu1~ucd1~natty
[UPGRADE] flashplugin-installer 10.3.181.26ubuntu1 -> 10.3.181.34ubuntu1
[UPGRADE] flashplugin-nonfree 10.3.181.26ubuntu1 -> 10.3.181.34ubuntu1
[UPGRADE] gdm 3.0.4-0ubuntu1~natty~build1 -> 3.0.4-0ubuntu2
[UPGRADE] gir1.2-gnomebluetooth-1.0 3.0.1-0ubuntu1 -> 3.0.1-0ubuntu2
[UPGRADE] gir1.2-gtk-2.0 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] gir1.2-mutter-3.0 3.0.2.1+git20110626.ec5fb2a4-0ubuntu1~11.10~ricotz0 -> 3.0.2.1+git20110629.d752096c-0ubuntu1~11.10~ricotz0
[UPGRADE] gnome-bluetooth 3.0.1-0ubuntu1 -> 3.0.1-0ubuntu2
[UPGRADE] gnome-control-center 1:3.0.2-1ubuntu6 -> 1:3.0.2-1ubuntu7
[UPGRADE] gnome-control-center-data 1:3.0.2-1ubuntu6 -> 1:3.0.2-1ubuntu7
[UPGRADE] gnome-shell 3.0.2+git20110628.ad314b36-0ubuntu1~11.10~ricotz0 -> 3.0.2+git20110629.6222796b-0ubuntu1~11.10~ricotz0
[UPGRADE] gtk2-engines-pixbuf 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] gtk3-engines-unico 0.1.0+r69-0ubuntu1 -> 0.1.0+r74-0ubuntu1
[UPGRADE] libegl1-mesa 7.11.0+git20110623.1e5cef96-0ubuntu0sarvatt -> 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt
[UPGRADE] libegl1-mesa-drivers 7.11.0+git20110623.1e5cef96-0ubuntu0sarvatt -> 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt
[UPGRADE] libgail18 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] libgl1-mesa-dri 7.11.0+git20110623.1e5cef96-0ubuntu0sarvatt -> 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt
[UPGRADE] libgl1-mesa-glx 7.11.0+git20110623.1e5cef96-0ubuntu0sarvatt -> 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt
[UPGRADE] libglapi-mesa 7.11.0+git20110623.1e5cef96-0ubuntu0sarvatt -> 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt
[UPGRADE] libglu1-mesa 7.11.0+git20110623.1e5cef96-0ubuntu0sarvatt -> 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt
[UPGRADE] libgnome-bluetooth8 3.0.1-0ubuntu1 -> 3.0.1-0ubuntu2
[UPGRADE] libgnome-control-center1 1:3.0.2-1ubuntu6 -> 1:3.0.2-1ubuntu7
[UPGRADE] libgtk2.0-0 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] libgtk2.0-bin 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] libgtk2.0-common 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] liblightdm-gobject-0-0 0.4.0-0ubuntu7 -> 0.4.1-0ubuntu1
[UPGRADE] libmutter0 3.0.2.1+git20110626.ec5fb2a4-0ubuntu1~11.10~ricotz0 -> 3.0.2.1+git20110629.d752096c-0ubuntu1~11.10~ricotz0
[UPGRADE] libunity-core-4.0-4 4.0.1-0ubuntu2 -> 4.0.1-0ubuntu3
[UPGRADE] light-themes 0.1.8.15 -> 0.1.8.16
[UPGRADE] lightdm 0.4.0-0ubuntu7 -> 0.4.1-0ubuntu1
[UPGRADE] lightdm-greeter-example-gtk 0.4.0-0ubuntu7 -> 0.4.1-0ubuntu1
[UPGRADE] mutter-common 3.0.2.1+git20110626.ec5fb2a4-0ubuntu1~11.10~ricotz0 -> 3.0.2.1+git20110629.d752096c-0ubuntu1~11.10~ricotz0
[UPGRADE] nautilus-dropbox 0.6.7-2 -> 0.6.8
[UPGRADE] unity 4.0.1-0ubuntu2 -> 4.0.1-0ubuntu3
[UPGRADE] unity-common 4.0.1-0ubuntu2 -> 4.0.1-0ubuntu3
[UPGRADE] unity-services 4.0.1-0ubuntu2 -> 4.0.1-0ubuntu3
===============================================================================

Log complete.
```

Btw, I'm also using the **gnome3-team** ppa (oneiric branch).

So at the moment I'm in "fallback" mode.

---

### Post by Quackers on 2011-06-30
No ricotz here, just gnome3team ppa.
It's getting better as I can see the panel now in gnome-shell :-)  I can even use the desktop - for about 10 seconds, then something crashes and I have to reboot. Still no Alt+F2 though.
I'll be back!

---

### Post by paul_in_london on 2011-06-30
> **Quackers said:**
> No ricotz here, just gnome3team ppa.
It's getting better as I can see the panel now in gnome-shell :-)  I can even use the desktop - for about 10 seconds, then something crashes and I have to reboot. Still no Alt+F2 though.
I'll be back!

Cheers - I suspect it's one of the **xorg-edgers** updates, but I don't feel inclined to purge that ppa...

---

### Post by Quackers on 2011-06-30
No xorg-edgers here now either, so it's not that.

---

### Post by paul_in_london on 2011-06-30
> **Quackers said:**
> No xorg-edgers here now either, so it's not that.

Hmm. Thanks. That's interesting. I assumed it was probably that and from what you say it's not something from the **gnome3-team** ppa either. I ran some updates when I finally got back from the pub after work last night. When I power up I very often boot into recovery mode first to apply any available updates and then reboot.

As far as I remember, it then booted into gnome-shell fine, but maybe I ran some other updates after that which screwed things up unbeknownst to me at the time. I'll see if I can spot anything else in the **aptitude** log.

---

### Post by Harry33 on 2011-06-30
Does some one of you use proprietary drivers?
If so, after updating/upgrading mesa, you have to reinstall graphics drivers.
Otherwise gnome-shell will not load.

---

### Post by Harry33 on 2011-06-30
> **Quackers said:**
> No ricotz here, just gnome3team ppa.
It's getting better as I can see the panel now in gnome-shell :-)  I can even use the desktop - for about 10 seconds, then something crashes and I have to reboot. Still no Alt+F2 though.
I'll be back!

Well Gnome3 Team PPA for Oneiric only contains an old cheese package.
And Gnome3 Team PPA for Natty may break Oneiric.

---

### Post by paul_in_london on 2011-06-30
> **Harry33 said:**
> Does some one of you use proprietary drivers?
If so, after updating/upgrading mesa, you have to reinstall graphics drivers.
Otherwise gnome-shell will not load.

Not using proprietary graphics drivers on this box. but one of my updates tonight was:

```
[UPGRADE] libgl1-mesa-dri **7.11.0+git20110623.1e5cef96-0ubuntu0sarvatt -> 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt**
```

so I'm wondering if it's something to do with this:

```
http://blog.mraw.org/2011/06/18/mesa_a_disturbance_in_the_Force/
```

```
paul@oneiric:~$ dpkg -s xserver-xorg-core
Package: xserver-xorg-core
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 4116
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: xorg-server
Version: 2:1.10.2+git20110616+server-1.10-branch.9551f504-0ubuntu0sarvatt
Provides: xorg-input-abi-12, xorg-video-abi-10
Depends: xserver-common (>= 2:1.10.2+git20110616+server-1.10-branch.9551f504-0ubuntu0sarvatt), keyboard-configuration, udev (>= 149), libc6 (>= 2.8), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.6), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
[COLOR="Red"]**Recommends**[/COLOR]: **[COLOR="Red"]libgl1-mesa-dri[/COLOR]** (>= 7.1~rc1)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Breaks: fglrx (<= 2:8.801-0ubuntu2), xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<< 0.7.8), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-8, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-dummy (<= 1:0.3.3-2build1), xserver-xorg-video-glamo (<= 0.0.0+20091108.git9918e082-1), xserver-xorg-video-glide (<= 1.0.3-2), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-newport (<= 1:0.2.1-4ubuntu1), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-psb (<= 0.2.1-1ubuntu3), xserver-xorg-video-radeonhd (<= 1.3.0-2), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-tga (<= 1:1.1.0-9ubuntu1), xserver-xorg-video-unichrome (<= 1:0.2.6.99-0ubuntu1), xserver-xorg-video-v4l (<< 1:0.2.0-4ubuntu1), xserver-xorg-video-vga (<= 1:4.1.0-8)
Description: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xserver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
paul@oneiric:~$
```

---

### Post by paul_in_london on 2011-06-30
> **Harry33 said:**
> Well Gnome3 Team PPA for Oneiric only contains an old cheese package.
And Gnome3 Team PPA for Natty may break Oneiric.

```
paul@oneiric:~$ sudo ppa-purge ppa:gnome3-team/gnome3
[sudo] password for paul: 
Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/lightdm-team/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/lightdm-team/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: gnome3-team gnome3
comm: file 2 is not in sorted order
Package revert list generated:
 accountsservice/oneiric brasero/oneiric brasero-cdrkit/oneiric 
brasero-common/oneiric dconf-gsettings-backend/oneiric dconf-tools/oneiric 
eog/oneiric evince/oneiric evince-common/oneiric evolution/oneiric 
evolution-data-server/oneiric evolution-data-server-common/oneiric 
file-roller/oneiric gconf2/oneiric gconf2-common/oneiric 
gconf-defaults-service/oneiric gconf-editor/oneiric gdm/oneiric gedit/oneiric 
gedit-common/oneiric gir1.2-clutter-1.0/oneiric gir1.2-freedesktop/oneiric 
gir1.2-gconf-2.0/oneiric gir1.2-gkbd-3.0/oneiric gir1.2-glib-2.0/oneiric 
gir1.2-gnomebluetooth-1.0/oneiric gir1.2-gtk-3.0/oneiric 
gir1.2-mutter-3.0/oneiric gir1.2-peas-1.0/oneiric gir1.2-polkit-1.0/oneiric 
gir1.2-soup-2.4/oneiric gir1.2-telepathyglib-0.12/oneiric 
gir1.2-telepathylogger-0.2/oneiric gjs/oneiric gnome-bluetooth/oneiric 
gnome-common/oneiric gnome-control-center/oneiric 
gnome-control-center-data/oneiric gnome-desktop3-data/oneiric 
gnome-disk-utility/oneiric gnome-doc-utils/oneiric gnome-icon-theme/oneiric 
gnome-icon-theme-symbolic/oneiric gnome-keyring/oneiric gnome-media/oneiric 
gnome-menus/oneiric gnome-power-manager/oneiric gnome-screensaver/oneiric 
gnome-session/oneiric gnome-session-bin/oneiric gnome-session-common/oneiric 
gnome-session-fallback/oneiric gnome-settings-daemon/oneiric 
gnome-shell/oneiric gnome-system-monitor/oneiric gnome-terminal/oneiric 
gnome-terminal-data/oneiric gnome-themes/oneiric gnome-themes-selected/oneiric 
gnome-themes-standard/oneiric gnome-tweak-tool/oneiric 
gsettings-desktop-schemas/oneiric gtk3-engines/oneiric 
gtk3-engines-unico/oneiric libaccountsservice0/oneiric libavahi-client3/oneiric 
libavahi-common3/oneiric libavahi-common-data/oneiric libavahi-glib1/oneiric 
libavahi-ui-gtk3-0/oneiric libbrasero-media3-1/oneiric libcanberra0/oneiric 
libcanberra-gtk0/oneiric libcanberra-gtk3-0/oneiric 
libcanberra-gtk3-module/oneiric libcanberra-gtk-module/oneiric 
libclutter-1.0-0/oneiric libclutter-1.0-common/oneiric libdconf0/oneiric 
libebackend-1.2-1/oneiric libecal1.2-8/oneiric libedataserver1.2-14/oneiric 
libedataserverui-3.0-0/oneiric libevince3-3/oneiric libgail-3-0/oneiric 
libgck0/oneiric libgconf2-4/oneiric libgcr-3-0/oneiric libgdata11/oneiric 
libgdata-common/oneiric libgdu0/oneiric libgdu-gtk0/oneiric 
libgirepository-1.0-1/oneiric libgjs0b/oneiric libgnome-bluetooth8/oneiric 
libgnome-control-center1/oneiric libgnomekbd7/oneiric 
libgnomekbd-common/oneiric libgnome-keyring0/oneiric 
libgnome-media-profiles-3.0-0/oneiric libgnome-menu2/oneiric libgtk-3-0/oneiric 
libgtk-3-bin/oneiric libgtk-3-common/oneiric libgtkhtml-4.0-0/oneiric 
libgtkhtml-editor-4.0-0/oneiric libgtkmm-3.0-1/oneiric 
libgtksourceview-3.0-0/oneiric libgtksourceview-3.0-common/oneiric 
libgucharmap-2-90-7/oneiric libgweather-3-0/oneiric libgweather-common/oneiric 
libmetacity-private0/oneiric libmutter0/oneiric libnautilus-extension1/oneiric 
libnotify4/oneiric libpam-gnome-keyring/oneiric libpeas-1.0-0/oneiric 
libpeas-common/oneiric libpolkit-agent-1-0/oneiric 
libpolkit-backend-1-0/oneiric libpolkit-gobject-1-0/oneiric libquvi0/oneiric 
librsvg2-2/oneiric librsvg2-common/oneiric libsoup2.4-1/oneiric 
libsoup-gnome2.4-1/oneiric libstartup-notification0/oneiric 
libtelepathy-glib0/oneiric libtelepathy-logger2/oneiric libtotem0/oneiric 
libtotem-plparser17/oneiric libunique-3.0-0/oneiric libwebkitgtk-1.0-0/oneiric 
libwebkitgtk-1.0-common/oneiric libwebkitgtk-3.0-0/oneiric 
libwebkitgtk-3.0-common/oneiric libwnck22/oneiric libwnck-3-0/oneiric 
libwnck-3-common/oneiric libwnck-common/oneiric libxklavier16/oneiric 
light-themes/oneiric metacity/oneiric metacity-common/oneiric 
mousetweaks/oneiric mutter-common/oneiric nautilus/oneiric 
nautilus-data/oneiric nautilus-open-terminal/oneiric policykit-1/oneiric 
policykit-1-gnome/oneiric python-gmenu/oneiric totem/oneiric 
ubuntu-artwork/oneiric yelp/oneiric yelp-xsl/oneiric zenity/oneiric 
zenity-common/oneiric

Disabling gnome3-team PPA from 
/etc/apt/sources.list.d/gnome3-team-gnome3-oneiric.list
Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/lightdm-team/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/lightdm-team/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release &#8216;oneiric&#8217; for &#8216;gtk3-engines&#8217; was not found
Unable to find an archive "oneiric" for the package "gtk3-engines"
Unable to find an archive "oneiric" for the package "gtk3-engines"
The following packages will be DOWNGRADED:
  gnome-keyring gnome-system-monitor gnome-themes gnome-themes-selected libgck0 libgcr-3-0 libgnome-media-profiles-3.0-0 libpam-gnome-keyring 
The following NEW packages will be installed:
  bogofilter{a} bogofilter-bdb{a} bogofilter-common{a} evolution evolution-common{a} evolution-plugins{a} evolution-webcal{a} gir1.2-totem-1.0{a} gir1.2-totem-plparser-1.0{a} libecal1.2-8 libevolution{a} 
  libgsl0ldbl{a} libgtkhtml-4.0-0 libgtkhtml-4.0-common{a} libgtkhtml-editor-4.0-0 libgtkmm-2.4-1c2a{a} liblircclient0{a} libtotem0 totem totem-common{a} totem-mozilla{a} totem-plugins{a} 
The following packages will be REMOVED:
  gtk3-engines{u} libgtkmm-3.0-1{u} 
0 packages upgraded, 22 newly installed, 8 downgraded, 2 to remove and 11 not upgraded.
Need to get 13.2 MB of archives. After unpacking 21.8 MB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://archive.ubuntu.com/ubuntu/ oneiric/main gnome-themes-selected all 2.32.1-0ubuntu1 [28.2 kB]
Get: 2 http://archive.ubuntu.com/ubuntu/ oneiric/universe gnome-themes all 2.32.1-0ubuntu1 [1,097 kB]
Get: 3 http://archive.ubuntu.com/ubuntu/ oneiric/main libgtkmm-2.4-1c2a i386 1:2.24.0-1 [1,019 kB]
Get: 4 http://archive.ubuntu.com/ubuntu/ oneiric/main gnome-system-monitor i386 2.28.2-0ubuntu1 [382 kB]
Get: 5 http://archive.ubuntu.com/ubuntu/ oneiric/main libgtkhtml-4.0-common all 4.1.2-0ubuntu1 [75.9 kB]
Get: 6 http://archive.ubuntu.com/ubuntu/ oneiric/main libgtkhtml-4.0-0 i386 4.1.2-0ubuntu1 [364 kB]
Get: 7 http://archive.ubuntu.com/ubuntu/ oneiric/main libgtkhtml-editor-4.0-0 i386 4.1.2-0ubuntu1 [83.6 kB]
Get: 8 http://archive.ubuntu.com/ubuntu/ oneiric/main libevolution i386 3.1.2-0ubuntu2 [2,426 kB]
Get: 9 http://archive.ubuntu.com/ubuntu/ oneiric/main evolution-common all 3.1.2-0ubuntu2 [2,855 kB]                                                                                                               
Get: 10 http://archive.ubuntu.com/ubuntu/ oneiric/main evolution i386 3.1.2-0ubuntu2 [187 kB]                                                                                                                      
Get: 11 http://archive.ubuntu.com/ubuntu/ oneiric/main bogofilter-common all 1.2.2-3ubuntu1 [186 kB]                                                                                                               
Get: 12 http://archive.ubuntu.com/ubuntu/ oneiric/main libgsl0ldbl i386 1.15+dfsg-1 [961 kB]                                                                                                                       
Get: 13 http://archive.ubuntu.com/ubuntu/ oneiric/main bogofilter-bdb i386 1.2.2-3ubuntu1 [260 kB]                                                                                                                 
Get: 14 http://archive.ubuntu.com/ubuntu/ oneiric/main bogofilter i386 1.2.2-3ubuntu1 [1,004 B]                                                                                                                    
Get: 15 http://archive.ubuntu.com/ubuntu/ oneiric/main evolution-plugins i386 3.1.2-0ubuntu2 [196 kB]                                                                                                              
Get: 16 http://archive.ubuntu.com/ubuntu/ oneiric/main evolution-webcal i386 2.32.0-1 [13.7 kB]                                                                                                                    
Get: 17 http://archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-totem-plparser-1.0 i386 2.32.5-2 [5,844 B]                                                                                                           
Get: 18 http://archive.ubuntu.com/ubuntu/ oneiric/main libtotem0 i386 3.0.1-0ubuntu2 [222 kB]                                                                                                                      
Get: 19 http://archive.ubuntu.com/ubuntu/ oneiric/main gir1.2-totem-1.0 i386 3.0.1-0ubuntu2 [7,092 B]                                                                                                              
Get: 20 http://archive.ubuntu.com/ubuntu/ oneiric/main libgck0 i386 3.0.3-1 [74.4 kB]                                                                                                                              
Get: 21 http://archive.ubuntu.com/ubuntu/ oneiric/main libgcr-3-0 i386 3.0.3-1 [140 kB]                                                                                                                            
Get: 22 http://archive.ubuntu.com/ubuntu/ oneiric/main gnome-keyring i386 3.0.3-1 [1,359 kB]                                                                                                                       
Get: 23 http://archive.ubuntu.com/ubuntu/ oneiric/main libecal1.2-8 i386 3.0.2.1-0ubuntu1 [119 kB]                                                                                                                 
Get: 24 http://archive.ubuntu.com/ubuntu/ oneiric/main libgnome-media-profiles-3.0-0 i386 2.91.2-4 [31.8 kB]                                                                                                       
Get: 25 http://archive.ubuntu.com/ubuntu/ oneiric/main libpam-gnome-keyring i386 3.0.3-1 [36.8 kB]                                                                                                                 
Get: 26 http://archive.ubuntu.com/ubuntu/ oneiric/main totem-common all 3.0.1-0ubuntu2 [227 kB]                                                                                                                    
Get: 27 http://archive.ubuntu.com/ubuntu/ oneiric/main totem i386 3.0.1-0ubuntu2 [424 kB]                                                                                                                          
Get: 28 http://archive.ubuntu.com/ubuntu/ oneiric/main totem-mozilla i386 3.0.1-0ubuntu2 [174 kB]                                                                                                                  
Get: 29 http://archive.ubuntu.com/ubuntu/ oneiric/main liblircclient0 i386 0.9.0-0ubuntu1 [16.0 kB]                                                                                                                
Get: 30 http://archive.ubuntu.com/ubuntu/ oneiric/main totem-plugins i386 3.0.1-0ubuntu2 [188 kB]                                                                                                                  
Fetched 13.2 MB in 13s (948 kB/s)                                                                                                                                                                                  
Preconfiguring packages ...
dpkg: warning: downgrading gnome-themes-selected from 3.0.0-0ubuntu1~build2 to 2.32.1-0ubuntu1.
(Reading database ... 267670 files and directories currently installed.)
Preparing to replace gnome-themes-selected 3.0.0-0ubuntu1~build2 (using .../gnome-themes-selected_2.32.1-0ubuntu1_all.deb) ...
Unpacking replacement gnome-themes-selected ...
dpkg: warning: downgrading gnome-themes from 3.0.0-0ubuntu1~build2 to 2.32.1-0ubuntu1.
Preparing to replace gnome-themes 3.0.0-0ubuntu1~build2 (using .../gnome-themes_2.32.1-0ubuntu1_all.deb) ...
Unpacking replacement gnome-themes ...
(Reading database ... 267579 files and directories currently installed.)
Removing gtk3-engines ...
Selecting previously deselected package libgtkmm-2.4-1c2a.
(Reading database ... 267469 files and directories currently installed.)
Unpacking libgtkmm-2.4-1c2a (from .../libgtkmm-2.4-1c2a_1%3a2.24.0-1_i386.deb) ...
dpkg: warning: downgrading gnome-system-monitor from 3.0.0-0ubuntu1~build1 to 2.28.2-0ubuntu1.
Preparing to replace gnome-system-monitor 3.0.0-0ubuntu1~build1 (using .../gnome-system-monitor_2.28.2-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-system-monitor ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0 ...
(Reading database ... 267376 files and directories currently installed.)
Removing libgtkmm-3.0-1 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libgtkhtml-4.0-common.
(Reading database ... 267366 files and directories currently installed.)
Unpacking libgtkhtml-4.0-common (from .../libgtkhtml-4.0-common_4.1.2-0ubuntu1_all.deb) ...
Selecting previously deselected package libgtkhtml-4.0-0.
Unpacking libgtkhtml-4.0-0 (from .../libgtkhtml-4.0-0_4.1.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtkhtml-editor-4.0-0.
Unpacking libgtkhtml-editor-4.0-0 (from .../libgtkhtml-editor-4.0-0_4.1.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libevolution.
Unpacking libevolution (from .../libevolution_3.1.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package evolution-common.
Unpacking evolution-common (from .../evolution-common_3.1.2-0ubuntu2_all.deb) ...
Selecting previously deselected package evolution.
Unpacking evolution (from .../evolution_3.1.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package bogofilter-common.
Unpacking bogofilter-common (from .../bogofilter-common_1.2.2-3ubuntu1_all.deb) ...
Selecting previously deselected package libgsl0ldbl.
Unpacking libgsl0ldbl (from .../libgsl0ldbl_1.15+dfsg-1_i386.deb) ...
Selecting previously deselected package bogofilter-bdb.
Unpacking bogofilter-bdb (from .../bogofilter-bdb_1.2.2-3ubuntu1_i386.deb) ...
Selecting previously deselected package bogofilter.
Unpacking bogofilter (from .../bogofilter_1.2.2-3ubuntu1_i386.deb) ...
Selecting previously deselected package evolution-plugins.
Unpacking evolution-plugins (from .../evolution-plugins_3.1.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package evolution-webcal.
Unpacking evolution-webcal (from .../evolution-webcal_2.32.0-1_i386.deb) ...
Selecting previously deselected package gir1.2-totem-plparser-1.0.
Unpacking gir1.2-totem-plparser-1.0 (from .../gir1.2-totem-plparser-1.0_2.32.5-2_i386.deb) ...
Selecting previously deselected package libtotem0.
Unpacking libtotem0 (from .../libtotem0_3.0.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package gir1.2-totem-1.0.
Unpacking gir1.2-totem-1.0 (from .../gir1.2-totem-1.0_3.0.1-0ubuntu2_i386.deb) ...
dpkg: warning: downgrading libgck0 from 3.0.3-2~natty1 to 3.0.3-1.
Preparing to replace libgck0 3.0.3-2~natty1 (using .../libgck0_3.0.3-1_i386.deb) ...
Unpacking replacement libgck0 ...
dpkg: warning: downgrading libgcr-3-0 from 3.0.3-2~natty1 to 3.0.3-1.
Preparing to replace libgcr-3-0 3.0.3-2~natty1 (using .../libgcr-3-0_3.0.3-1_i386.deb) ...
Unpacking replacement libgcr-3-0 ...
dpkg: warning: downgrading gnome-keyring from 3.0.3-2~natty1 to 3.0.3-1.
Preparing to replace gnome-keyring 3.0.3-2~natty1 (using .../gnome-keyring_3.0.3-1_i386.deb) ...
Unpacking replacement gnome-keyring ...
Selecting previously deselected package libecal1.2-8.
Unpacking libecal1.2-8 (from .../libecal1.2-8_3.0.2.1-0ubuntu1_i386.deb) ...
dpkg: warning: downgrading libgnome-media-profiles-3.0-0 from 3.0.0-0ubuntu1~build1 to 2.91.2-4.
Preparing to replace libgnome-media-profiles-3.0-0 3.0.0-0ubuntu1~build1 (using .../libgnome-media-profiles-3.0-0_2.91.2-4_i386.deb) ...
Unpacking replacement libgnome-media-profiles-3.0-0 ...
dpkg: warning: downgrading libpam-gnome-keyring from 3.0.3-2~natty1 to 3.0.3-1.
Preparing to replace libpam-gnome-keyring 3.0.3-2~natty1 (using .../libpam-gnome-keyring_3.0.3-1_i386.deb) ...
Unpacking replacement libpam-gnome-keyring ...
Selecting previously deselected package totem-common.
Unpacking totem-common (from .../totem-common_3.0.1-0ubuntu2_all.deb) ...
Selecting previously deselected package totem.
Unpacking totem (from .../totem_3.0.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package totem-mozilla.
Unpacking totem-mozilla (from .../totem-mozilla_3.0.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package liblircclient0.
Unpacking liblircclient0 (from .../liblircclient0_0.9.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package totem-plugins.
Unpacking totem-plugins (from .../totem-plugins_3.0.1-0ubuntu2_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0 ...
Setting up gnome-themes-selected (2.32.1-0ubuntu1) ...
Setting up gnome-themes (2.32.1-0ubuntu1) ...
Setting up libgtkmm-2.4-1c2a (1:2.24.0-1) ...
Setting up gnome-system-monitor (2.28.2-0ubuntu1) ...
Setting up libgtkhtml-4.0-common (4.1.2-0ubuntu1) ...
Setting up libgtkhtml-4.0-0 (4.1.2-0ubuntu1) ...
Setting up libgtkhtml-editor-4.0-0 (4.1.2-0ubuntu1) ...
Setting up libevolution (3.1.2-0ubuntu2) ...
Setting up evolution-common (3.1.2-0ubuntu2) ...
Setting up evolution (3.1.2-0ubuntu2) ...
Setting up bogofilter-common (1.2.2-3ubuntu1) ...
Setting up libgsl0ldbl (1.15+dfsg-1) ...
Setting up bogofilter-bdb (1.2.2-3ubuntu1) ...
Setting up bogofilter (1.2.2-3ubuntu1) ...
Setting up evolution-plugins (3.1.2-0ubuntu2) ...
Setting up evolution-webcal (2.32.0-1) ...
Setting up gir1.2-totem-plparser-1.0 (2.32.5-2) ...
Setting up libtotem0 (3.0.1-0ubuntu2) ...
Setting up gir1.2-totem-1.0 (3.0.1-0ubuntu2) ...
Setting up libgck0 (3.0.3-1) ...
Setting up libgcr-3-0 (3.0.3-1) ...
Setting up gnome-keyring (3.0.3-1) ...
Installing new version of config file /etc/xdg/autostart/gnome-keyring-pkcs11.desktop ...
Installing new version of config file /etc/xdg/autostart/gnome-keyring-secrets.desktop ...
Installing new version of config file /etc/xdg/autostart/gnome-keyring-gpg.desktop ...
Installing new version of config file /etc/xdg/autostart/gnome-keyring-ssh.desktop ...
Setting up libecal1.2-8 (3.0.2.1-0ubuntu1) ...
Setting up libgnome-media-profiles-3.0-0 (2.91.2-4) ...
Setting up libpam-gnome-keyring (3.0.3-1) ...
Setting up totem-common (3.0.1-0ubuntu2) ...
Setting up totem (3.0.1-0ubuntu2) ...
Setting up totem-mozilla (3.0.1-0ubuntu2) ...
Setting up liblircclient0 (0.9.0-0ubuntu1) ...
Setting up totem-plugins (3.0.1-0ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 1220 KiB
localepurge: Disk space freed in /usr/share/omf: 52 KiB

Total disk space freed by localepurge: 1272 KiB

                                         
Current status: 4410 new [-1].
PPA purged successfully using aptitude fallback
paul@oneiric:~$ 
```

Ok so I still can't start gnome-shell for the same reason as before:

```
paul@oneiric:~$ gnome-shell --replace &
[1] 3240
paul@oneiric:~$ 
(gnome-shell:3240): Clutter-CRITICAL **: Unable to initialize Clutter: XServer appears to lack the required GLX support
Window manager error: Unable to initialize Clutter.
```

---

### Post by paul_in_london on 2011-06-30
> **Quackers said:**
> No xorg-edgers here now either, so it's not that.

Well on my box it **was** that! Disabled **xorg-edgers** (sod it!):

```
paul@oneiric:~$ sudo ppa-purge ppa:xorg-edgers/ppa
Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/lightdm-team/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/lightdm-team/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: xorg-edgers ppa
Package revert list generated:
 libdrm2/oneiric libdrm-intel1/oneiric libdrm-nouveau1a/oneiric 
libdrm-radeon1/oneiric libegl1-mesa/oneiric libegl1-mesa-drivers/oneiric 
libgbm1/oneiric libgl1-mesa-dri/oneiric libgl1-mesa-glx/oneiric 
libglapi-mesa/oneiric libglu1-mesa/oneiric libopenvg1-mesa/oneiric 
xserver-common/oneiric xserver-xorg-core/oneiric 
xserver-xorg-input-mouse/oneiric xserver-xorg-input-vmmouse/oneiric 
xserver-xorg-video-apm/oneiric xserver-xorg-video-ark/oneiric 
xserver-xorg-video-ati/oneiric xserver-xorg-video-chips/oneiric 
xserver-xorg-video-cirrus/oneiric xserver-xorg-video-fbdev/oneiric 
xserver-xorg-video-i128/oneiric xserver-xorg-video-i740/oneiric 
xserver-xorg-video-intel/oneiric xserver-xorg-video-mach64/oneiric 
xserver-xorg-video-mga/oneiric xserver-xorg-video-neomagic/oneiric 
xserver-xorg-video-nouveau/oneiric xserver-xorg-video-r128/oneiric 
xserver-xorg-video-radeon/oneiric xserver-xorg-video-rendition/oneiric 
xserver-xorg-video-s3/oneiric xserver-xorg-video-s3virge/oneiric 
xserver-xorg-video-savage/oneiric xserver-xorg-video-siliconmotion/oneiric 
xserver-xorg-video-sis/oneiric xserver-xorg-video-sisusb/oneiric 
xserver-xorg-video-tdfx/oneiric xserver-xorg-video-trident/oneiric 
xserver-xorg-video-tseng/oneiric xserver-xorg-video-vesa/oneiric 
xserver-xorg-video-vmware/oneiric xserver-xorg-video-voodoo/oneiric

Disabling xorg-edgers PPA from 
/etc/apt/sources.list.d/xorg-edgers-ppa-oneiric.list
Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/lightdm-team/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/lightdm-team/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-mga is already the newest version.
xserver-xorg-video-mga set to manually installed.
Selected version '2.4.25-2ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libdrm2'
Selected version '2.4.25-2ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libdrm-intel1'
Selected version '2.4.25-2ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libdrm-nouveau1a'
Selected version '2.4.25-2ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libdrm-radeon1'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libegl1-mesa'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libegl1-mesa-drivers'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libglapi-mesa' because of 'libegl1-mesa-drivers'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libgbm1'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libgl1-mesa-dri'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libgl1-mesa-glx'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libglapi-mesa'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libglu1-mesa'
Selected version '7.11~1-0ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'libopenvg1-mesa'
Selected version '2:1.10.2-1ubuntu1' (Ubuntu:11.10/oneiric [all]) for 'xserver-common'
Selected version '2:1.10.2-1ubuntu1' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-core'
Selected version '1:1.7.0-4' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-input-mouse'
Selected version '1:12.7.0-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-input-vmmouse'
Selected version '1:1.2.3-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-apm'
Selected version '1:0.7.3-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-ark'
Selected version '1:6.14.2-1ubuntu1' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-ati'
Selected version '1:1.2.4-1' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-chips'
Selected version '1:1.3.2-2ubuntu7' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-cirrus'
Selected version '1:0.4.2-3ubuntu6' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-fbdev'
Selected version '1:1.3.4-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-i128'
Selected version '1:1.3.2-4' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-i740'
Selected version '2:2.15.0-3ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-intel'
Selected version '6.9.0-1' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-mach64'
Selected version '1:1.4.13.dfsg-3build1' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-mga'
Selected version '1:1.2.5-1ubuntu3' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-neomagic'
Selected version '1:0.0.16+git20110411+8378443-1' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-nouveau'
Selected version '6.8.1-5' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-r128'
Selected version '1:6.14.2-1ubuntu1' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-radeon'
Selected version '1:4.2.4-0ubuntu5' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-rendition'
Selected version '1:0.6.3-4' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-s3'
Selected version '1:1.10.4-4' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-s3virge'
Selected version '1:2.3.2-3ubuntu2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-savage'
Selected version '1:1.7.4-0ubuntu7' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-siliconmotion'
Selected version '1:0.10.3-3' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-sis'
Selected version '1:0.9.4-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-sisusb'
Selected version '1:1.4.3-4' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-tdfx'
Selected version '1:1.3.4-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-trident'
Selected version '1:1.2.4-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-tseng'
Selected version '1:2.3.0-7' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-vesa'
Selected version '1:11.0.3-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-vmware'
Selected version '1:1.2.4-2' (Ubuntu:11.10/oneiric [i386]) for 'xserver-xorg-video-voodoo'
Suggested packages:
  libglide3 xfonts-100dpi xfonts-75dpi firmware-linux
The following packages will be DOWNGRADED:
  libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libegl1-mesa libegl1-mesa-drivers libgbm1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa libopenvg1-mesa xserver-common xserver-xorg-core
  xserver-xorg-input-mouse xserver-xorg-input-vmmouse xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 0 newly installed, 43 downgraded, 0 to remove and 11 not upgraded.
Need to get 8,493 kB of archives.
After this operation, 684 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric/main libdrm2 i386 2.4.25-2ubuntu2 [26.6 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ oneiric/main libdrm-intel1 i386 2.4.25-2ubuntu2 [25.1 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ oneiric/main libdrm-nouveau1a i386 2.4.25-2ubuntu2 [14.2 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ oneiric/main libdrm-radeon1 i386 2.4.25-2ubuntu2 [14.7 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ oneiric/main libgbm1 i386 7.11~1-0ubuntu2 [15.1 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ oneiric/main libgl1-mesa-dri i386 7.11~1-0ubuntu2 [2,807 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ oneiric/main libgl1-mesa-glx i386 7.11~1-0ubuntu2 [99.0 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ oneiric/main libegl1-mesa-drivers i386 7.11~1-0ubuntu2 [1,602 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ oneiric/main libglapi-mesa i386 7.11~1-0ubuntu2 [23.0 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ oneiric/main libopenvg1-mesa i386 7.11~1-0ubuntu2 [16.0 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ oneiric/main libegl1-mesa i386 7.11~1-0ubuntu2 [44.2 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ oneiric/main libglu1-mesa i386 7.11~1-0ubuntu2 [167 kB]
Get:13 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-core i386 2:1.10.2-1ubuntu1 [1,640 kB]                                                                                                         
Get:14 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-common all 2:1.10.2-1ubuntu1 [33.3 kB]                                                                                                              
Get:15 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-input-mouse i386 1:1.7.0-4 [39.8 kB]                                                                                                           
Get:16 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-input-vmmouse i386 1:12.7.0-2 [15.3 kB]                                                                                                        
Get:17 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-apm i386 1:1.2.3-2 [59.9 kB]                                                                                                             
Get:18 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-ark i386 1:0.7.3-2 [12.9 kB]                                                                                                             
Get:19 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-r128 i386 6.8.1-5 [54.9 kB]                                                                                                              
Get:20 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-mach64 i386 6.9.0-1 [90.2 kB]                                                                                                            
Get:21 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-radeon i386 1:6.14.2-1ubuntu1 [441 kB]                                                                                                   
Get:22 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-ati i386 1:6.14.2-1ubuntu1 [6,666 B]                                                                                                     
Get:23 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-chips i386 1:1.2.4-1 [73.4 kB]                                                                                                           
Get:24 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-cirrus i386 1:1.3.2-2ubuntu7 [37.5 kB]                                                                                                   
Get:25 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-fbdev i386 1:0.4.2-3ubuntu6 [12.7 kB]                                                                                                    
Get:26 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-i128 i386 1:1.3.4-2 [29.7 kB]                                                                                                            
Get:27 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-i740 i386 1:1.3.2-4 [27.8 kB]                                                                                                            
Get:28 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-intel i386 2:2.15.0-3ubuntu2 [165 kB]                                                                                                    
Get:29 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-neomagic i386 1:1.2.5-1ubuntu3 [35.3 kB]                                                                                                 
Get:30 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-nouveau i386 1:0.0.16+git20110411+8378443-1 [108 kB]                                                                                     
Get:31 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-rendition i386 1:4.2.4-0ubuntu5 [22.6 kB]                                                                                                
Get:32 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-s3 i386 1:0.6.3-4 [36.1 kB]                                                                                                              
Get:33 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-s3virge i386 1:1.10.4-4 [40.8 kB]                                                                                                        
Get:34 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-savage i386 1:2.3.2-3ubuntu2 [69.3 kB]                                                                                                   
Get:35 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-siliconmotion i386 1:1.7.4-0ubuntu7 [54.4 kB]                                                                                            
Get:36 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-sis i386 1:0.10.3-3 [280 kB]                                                                                                             
Get:37 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-sisusb i386 1:0.9.4-2 [43.0 kB]                                                                                                          
Get:38 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-tdfx i386 1:1.4.3-4 [37.9 kB]                                                                                                            
Get:39 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-trident i386 1:1.3.4-2 [73.3 kB]                                                                                                         
Get:40 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-tseng i386 1:1.2.4-2 [27.0 kB]                                                                                                           
Get:41 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-vesa i386 1:2.3.0-7 [16.7 kB]                                                                                                            
Get:42 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-vmware i386 1:11.0.3-2 [33.8 kB]                                                                                                         
Get:43 http://archive.ubuntu.com/ubuntu/ oneiric/main xserver-xorg-video-voodoo i386 1:1.2.4-2 [19.1 kB]                                                                                                          
Fetched 8,493 kB in 12s (691 kB/s)                                                                                                                                                                                
Extract templates from packages: 100%
dpkg: warning: downgrading libdrm2 from 2.4.26+git20110604.6dd804c5-0ubuntu0sarvatt to 2.4.25-2ubuntu2.
(Reading database ... 269835 files and directories currently installed.)
Preparing to replace libdrm2 2.4.26+git20110604.6dd804c5-0ubuntu0sarvatt (using .../libdrm2_2.4.25-2ubuntu2_i386.deb) ...
Unpacking replacement libdrm2 ...
dpkg: warning: downgrading libdrm-intel1 from 2.4.26+git20110604.6dd804c5-0ubuntu0sarvatt to 2.4.25-2ubuntu2.
Preparing to replace libdrm-intel1 2.4.26+git20110604.6dd804c5-0ubuntu0sarvatt (using .../libdrm-intel1_2.4.25-2ubuntu2_i386.deb) ...
Unpacking replacement libdrm-intel1 ...
dpkg: warning: downgrading libdrm-nouveau1a from 2.4.26+git20110604.6dd804c5-0ubuntu0sarvatt to 2.4.25-2ubuntu2.
Preparing to replace libdrm-nouveau1a 2.4.26+git20110604.6dd804c5-0ubuntu0sarvatt (using .../libdrm-nouveau1a_2.4.25-2ubuntu2_i386.deb) ...
Unpacking replacement libdrm-nouveau1a ...
dpkg: warning: downgrading libdrm-radeon1 from 2.4.26+git20110604.6dd804c5-0ubuntu0sarvatt to 2.4.25-2ubuntu2.
Preparing to replace libdrm-radeon1 2.4.26+git20110604.6dd804c5-0ubuntu0sarvatt (using .../libdrm-radeon1_2.4.25-2ubuntu2_i386.deb) ...
Unpacking replacement libdrm-radeon1 ...
dpkg: warning: downgrading libgbm1 from 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt to 7.11~1-0ubuntu2.
Preparing to replace libgbm1 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt (using .../libgbm1_7.11~1-0ubuntu2_i386.deb) ...
Unpacking replacement libgbm1 ...
dpkg: warning: downgrading libgl1-mesa-dri from 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt to 7.11~1-0ubuntu2.
Preparing to replace libgl1-mesa-dri 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt (using .../libgl1-mesa-dri_7.11~1-0ubuntu2_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
dpkg: warning: downgrading libgl1-mesa-glx from 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt to 7.11~1-0ubuntu2.
Preparing to replace libgl1-mesa-glx 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt (using .../libgl1-mesa-glx_7.11~1-0ubuntu2_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
dpkg: warning: downgrading libegl1-mesa-drivers from 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt to 7.11~1-0ubuntu2.
Preparing to replace libegl1-mesa-drivers 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt (using .../libegl1-mesa-drivers_7.11~1-0ubuntu2_i386.deb) ...
Unpacking replacement libegl1-mesa-drivers ...
dpkg: warning: downgrading libglapi-mesa from 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt to 7.11~1-0ubuntu2.
Preparing to replace libglapi-mesa 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt (using .../libglapi-mesa_7.11~1-0ubuntu2_i386.deb) ...
Unpacking replacement libglapi-mesa ...
dpkg: warning: downgrading libopenvg1-mesa from 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt to 7.11~1-0ubuntu2.
Preparing to replace libopenvg1-mesa 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt (using .../libopenvg1-mesa_7.11~1-0ubuntu2_i386.deb) ...
Unpacking replacement libopenvg1-mesa ...
dpkg: warning: downgrading libegl1-mesa from 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt to 7.11~1-0ubuntu2.
Preparing to replace libegl1-mesa 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt (using .../libegl1-mesa_7.11~1-0ubuntu2_i386.deb) ...
Unpacking replacement libegl1-mesa ...
dpkg: warning: downgrading libglu1-mesa from 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt to 7.11~1-0ubuntu2.
Preparing to replace libglu1-mesa 7.12.0~git20110630.0edb40cb-0ubuntu0sarvatt (using .../libglu1-mesa_7.11~1-0ubuntu2_i386.deb) ...
Unpacking replacement libglu1-mesa ...
dpkg: warning: downgrading xserver-xorg-core from 2:1.10.2+git20110616+server-1.10-branch.9551f504-0ubuntu0sarvatt to 2:1.10.2-1ubuntu1.
Preparing to replace xserver-xorg-core 2:1.10.2+git20110616+server-1.10-branch.9551f504-0ubuntu0sarvatt (using .../xserver-xorg-core_2%3a1.10.2-1ubuntu1_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
dpkg: warning: downgrading xserver-common from 2:1.10.2+git20110616+server-1.10-branch.9551f504-0ubuntu0sarvatt to 2:1.10.2-1ubuntu1.
Preparing to replace xserver-common 2:1.10.2+git20110616+server-1.10-branch.9551f504-0ubuntu0sarvatt (using .../xserver-common_2%3a1.10.2-1ubuntu1_all.deb) ...
Unpacking replacement xserver-common ...
dpkg: warning: downgrading xserver-xorg-input-mouse from 1:1.7.0+git20110628.b12fa0d5-0ubuntu0sarvatt to 1:1.7.0-4.
Preparing to replace xserver-xorg-input-mouse 1:1.7.0+git20110628.b12fa0d5-0ubuntu0sarvatt (using .../xserver-xorg-input-mouse_1%3a1.7.0-4_i386.deb) ...
Unpacking replacement xserver-xorg-input-mouse ...
dpkg: warning: downgrading xserver-xorg-input-vmmouse from 1:12.7.0+git20110624.fd140bfb-0ubuntu0sarvatt to 1:12.7.0-2.
Preparing to replace xserver-xorg-input-vmmouse 1:12.7.0+git20110624.fd140bfb-0ubuntu0sarvatt (using .../xserver-xorg-input-vmmouse_1%3a12.7.0-2_i386.deb) ...
Unpacking replacement xserver-xorg-input-vmmouse ...
dpkg: warning: downgrading xserver-xorg-video-apm from 1:1.2.3+git20110526.6f8a776f-0ubuntu0sarvatt to 1:1.2.3-2.
Preparing to replace xserver-xorg-video-apm 1:1.2.3+git20110526.6f8a776f-0ubuntu0sarvatt (using .../xserver-xorg-video-apm_1%3a1.2.3-2_i386.deb) ...
Unpacking replacement xserver-xorg-video-apm ...
dpkg: warning: downgrading xserver-xorg-video-ark from 1:0.7.3+git20110526.9d3769be-0ubuntu0sarvatt to 1:0.7.3-2.
Preparing to replace xserver-xorg-video-ark 1:0.7.3+git20110526.9d3769be-0ubuntu0sarvatt (using .../xserver-xorg-video-ark_1%3a0.7.3-2_i386.deb) ...
Unpacking replacement xserver-xorg-video-ark ...
dpkg: warning: downgrading xserver-xorg-video-r128 from 6.8.1+git20110526.3de85360-0ubuntu0sarvatt to 6.8.1-5.
Preparing to replace xserver-xorg-video-r128 6.8.1+git20110526.3de85360-0ubuntu0sarvatt (using .../xserver-xorg-video-r128_6.8.1-5_i386.deb) ...
Unpacking replacement xserver-xorg-video-r128 ...
dpkg: warning: downgrading xserver-xorg-video-mach64 from 6.9.0+git20110526.ef55d1f1-0ubuntu0sarvatt to 6.9.0-1.
Preparing to replace xserver-xorg-video-mach64 6.9.0+git20110526.ef55d1f1-0ubuntu0sarvatt (using .../xserver-xorg-video-mach64_6.9.0-1_i386.deb) ...
Unpacking replacement xserver-xorg-video-mach64 ...
dpkg: warning: downgrading xserver-xorg-video-radeon from 1:6.14.99+git20110623.9bb31158-0ubuntu0sarvatt to 1:6.14.2-1ubuntu1.
Preparing to replace xserver-xorg-video-radeon 1:6.14.99+git20110623.9bb31158-0ubuntu0sarvatt (using .../xserver-xorg-video-radeon_1%3a6.14.2-1ubuntu1_i386.deb) ...
Unpacking replacement xserver-xorg-video-radeon ...
dpkg: warning: downgrading xserver-xorg-video-ati from 1:6.14.99+git20110623.9bb31158-0ubuntu0sarvatt to 1:6.14.2-1ubuntu1.
Preparing to replace xserver-xorg-video-ati 1:6.14.99+git20110623.9bb31158-0ubuntu0sarvatt (using .../xserver-xorg-video-ati_1%3a6.14.2-1ubuntu1_i386.deb) ...
Unpacking replacement xserver-xorg-video-ati ...
dpkg: warning: downgrading xserver-xorg-video-chips from 1:1.2.4+git20110526.e4bd8648-0ubuntu0sarvatt to 1:1.2.4-1.
Preparing to replace xserver-xorg-video-chips 1:1.2.4+git20110526.e4bd8648-0ubuntu0sarvatt (using .../xserver-xorg-video-chips_1%3a1.2.4-1_i386.deb) ...
Unpacking replacement xserver-xorg-video-chips ...
dpkg: warning: downgrading xserver-xorg-video-cirrus from 1:1.3.2+git20110526.e4f80ffd-0ubuntu0sarvatt to 1:1.3.2-2ubuntu7.
Preparing to replace xserver-xorg-video-cirrus 1:1.3.2+git20110526.e4f80ffd-0ubuntu0sarvatt (using .../xserver-xorg-video-cirrus_1%3a1.3.2-2ubuntu7_i386.deb) ...
Unpacking replacement xserver-xorg-video-cirrus ...
dpkg: warning: downgrading xserver-xorg-video-fbdev from 1:0.4.2+git20110526.a8721393-0ubuntu0sarvatt to 1:0.4.2-3ubuntu6.
Preparing to replace xserver-xorg-video-fbdev 1:0.4.2+git20110526.a8721393-0ubuntu0sarvatt (using .../xserver-xorg-video-fbdev_1%3a0.4.2-3ubuntu6_i386.deb) ...
Unpacking replacement xserver-xorg-video-fbdev ...
dpkg: warning: downgrading xserver-xorg-video-i128 from 1:1.3.4+git20110526.b9e0edbd-0ubuntu0sarvatt to 1:1.3.4-2.
Preparing to replace xserver-xorg-video-i128 1:1.3.4+git20110526.b9e0edbd-0ubuntu0sarvatt (using .../xserver-xorg-video-i128_1%3a1.3.4-2_i386.deb) ...
Unpacking replacement xserver-xorg-video-i128 ...
dpkg: warning: downgrading xserver-xorg-video-i740 from 1:1.3.2+git20110526.87da594b-0ubuntu0sarvatt to 1:1.3.2-4.
Preparing to replace xserver-xorg-video-i740 1:1.3.2+git20110526.87da594b-0ubuntu0sarvatt (using .../xserver-xorg-video-i740_1%3a1.3.2-4_i386.deb) ...
Unpacking replacement xserver-xorg-video-i740 ...
dpkg: warning: downgrading xserver-xorg-video-intel from 2:2.15.0+git20110628.95866bd6-0ubuntu0sarvatt to 2:2.15.0-3ubuntu2.
Preparing to replace xserver-xorg-video-intel 2:2.15.0+git20110628.95866bd6-0ubuntu0sarvatt (using .../xserver-xorg-video-intel_2%3a2.15.0-3ubuntu2_i386.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
dpkg: warning: downgrading xserver-xorg-video-neomagic from 1:1.2.5+git20110526.a9d69f6d-0ubuntu0sarvatt to 1:1.2.5-1ubuntu3.
Preparing to replace xserver-xorg-video-neomagic 1:1.2.5+git20110526.a9d69f6d-0ubuntu0sarvatt (using .../xserver-xorg-video-neomagic_1%3a1.2.5-1ubuntu3_i386.deb) ...
Unpacking replacement xserver-xorg-video-neomagic ...
dpkg: warning: downgrading xserver-xorg-video-nouveau from 1:0.0.16+git20110623.ab89aa02-0ubuntu0sarvatt to 1:0.0.16+git20110411+8378443-1.
Preparing to replace xserver-xorg-video-nouveau 1:0.0.16+git20110623.ab89aa02-0ubuntu0sarvatt (using .../xserver-xorg-video-nouveau_1%3a0.0.16+git20110411+8378443-1_i386.deb) ...
Unpacking replacement xserver-xorg-video-nouveau ...
dpkg: warning: downgrading xserver-xorg-video-rendition from 1:4.2.4+git20110526.541d1193-0ubuntu0sarvatt to 1:4.2.4-0ubuntu5.
Preparing to replace xserver-xorg-video-rendition 1:4.2.4+git20110526.541d1193-0ubuntu0sarvatt (using .../xserver-xorg-video-rendition_1%3a4.2.4-0ubuntu5_i386.deb) ...
Unpacking replacement xserver-xorg-video-rendition ...
dpkg: warning: downgrading xserver-xorg-video-s3 from 1:0.6.3+git20110526.381ace93-0ubuntu0sarvatt to 1:0.6.3-4.
Preparing to replace xserver-xorg-video-s3 1:0.6.3+git20110526.381ace93-0ubuntu0sarvatt (using .../xserver-xorg-video-s3_1%3a0.6.3-4_i386.deb) ...
Unpacking replacement xserver-xorg-video-s3 ...
dpkg: warning: downgrading xserver-xorg-video-s3virge from 1:1.10.4+git20110526.a568407e-0ubuntu0sarvatt to 1:1.10.4-4.
Preparing to replace xserver-xorg-video-s3virge 1:1.10.4+git20110526.a568407e-0ubuntu0sarvatt (using .../xserver-xorg-video-s3virge_1%3a1.10.4-4_i386.deb) ...
Unpacking replacement xserver-xorg-video-s3virge ...
dpkg: warning: downgrading xserver-xorg-video-savage from 1:2.3.2+git20110526.d177ae0b-0ubuntu0sarvatt to 1:2.3.2-3ubuntu2.
Preparing to replace xserver-xorg-video-savage 1:2.3.2+git20110526.d177ae0b-0ubuntu0sarvatt (using .../xserver-xorg-video-savage_1%3a2.3.2-3ubuntu2_i386.deb) ...
Unpacking replacement xserver-xorg-video-savage ...
dpkg: warning: downgrading xserver-xorg-video-siliconmotion from 1:1.7.5+git20110526.087226bf-0ubuntu0sarvatt to 1:1.7.4-0ubuntu7.
Preparing to replace xserver-xorg-video-siliconmotion 1:1.7.5+git20110526.087226bf-0ubuntu0sarvatt (using .../xserver-xorg-video-siliconmotion_1%3a1.7.4-0ubuntu7_i386.deb) ...
Unpacking replacement xserver-xorg-video-siliconmotion ...
dpkg: warning: downgrading xserver-xorg-video-sis from 1:0.10.3+git20110608.94f23a56-0ubuntu0sarvatt to 1:0.10.3-3.
Preparing to replace xserver-xorg-video-sis 1:0.10.3+git20110608.94f23a56-0ubuntu0sarvatt (using .../xserver-xorg-video-sis_1%3a0.10.3-3_i386.deb) ...
Unpacking replacement xserver-xorg-video-sis ...
dpkg: warning: downgrading xserver-xorg-video-sisusb from 1:0.9.4+git20110608.241dd519-0ubuntu0sarvatt to 1:0.9.4-2.
Preparing to replace xserver-xorg-video-sisusb 1:0.9.4+git20110608.241dd519-0ubuntu0sarvatt (using .../xserver-xorg-video-sisusb_1%3a0.9.4-2_i386.deb) ...
Unpacking replacement xserver-xorg-video-sisusb ...
dpkg: warning: downgrading xserver-xorg-video-tdfx from 1:1.4.3+git20110526.0c4ffbec-0ubuntu0sarvatt to 1:1.4.3-4.
Preparing to replace xserver-xorg-video-tdfx 1:1.4.3+git20110526.0c4ffbec-0ubuntu0sarvatt (using .../xserver-xorg-video-tdfx_1%3a1.4.3-4_i386.deb) ...
Unpacking replacement xserver-xorg-video-tdfx ...
dpkg: warning: downgrading xserver-xorg-video-trident from 1:1.3.4+git20110526.de79bbea-0ubuntu0sarvatt to 1:1.3.4-2.
Preparing to replace xserver-xorg-video-trident 1:1.3.4+git20110526.de79bbea-0ubuntu0sarvatt (using .../xserver-xorg-video-trident_1%3a1.3.4-2_i386.deb) ...
Unpacking replacement xserver-xorg-video-trident ...
dpkg: warning: downgrading xserver-xorg-video-tseng from 1:1.2.4+git20110613.542e65de-0ubuntu0sarvatt to 1:1.2.4-2.
Preparing to replace xserver-xorg-video-tseng 1:1.2.4+git20110613.542e65de-0ubuntu0sarvatt (using .../xserver-xorg-video-tseng_1%3a1.2.4-2_i386.deb) ...
Unpacking replacement xserver-xorg-video-tseng ...
dpkg: warning: downgrading xserver-xorg-video-vesa from 1:2.3.0+git20110526.0b02c685-0ubuntu0sarvatt to 1:2.3.0-7.
Preparing to replace xserver-xorg-video-vesa 1:2.3.0+git20110526.0b02c685-0ubuntu0sarvatt (using .../xserver-xorg-video-vesa_1%3a2.3.0-7_i386.deb) ...
Unpacking replacement xserver-xorg-video-vesa ...
dpkg: warning: downgrading xserver-xorg-video-vmware from 1:11.0.3+git20110526.0142bb8d-0ubuntu0sarvatt to 1:11.0.3-2.
Preparing to replace xserver-xorg-video-vmware 1:11.0.3+git20110526.0142bb8d-0ubuntu0sarvatt (using .../xserver-xorg-video-vmware_1%3a11.0.3-2_i386.deb) ...
Unpacking replacement xserver-xorg-video-vmware ...
dpkg: warning: downgrading xserver-xorg-video-voodoo from 1:1.2.4+git20110526.614ccdf6-0ubuntu0sarvatt to 1:1.2.4-2.
Preparing to replace xserver-xorg-video-voodoo 1:1.2.4+git20110526.614ccdf6-0ubuntu0sarvatt (using .../xserver-xorg-video-voodoo_1%3a1.2.4-2_i386.deb) ...
Unpacking replacement xserver-xorg-video-voodoo ...
Processing triggers for man-db ...
Setting up libdrm2 (2.4.25-2ubuntu2) ...
Setting up libdrm-intel1 (2.4.25-2ubuntu2) ...
Setting up libdrm-nouveau1a (2.4.25-2ubuntu2) ...
Setting up libdrm-radeon1 (2.4.25-2ubuntu2) ...
Setting up libgbm1 (7.11~1-0ubuntu2) ...
Setting up libgl1-mesa-dri (7.11~1-0ubuntu2) ...
Setting up libglapi-mesa (7.11~1-0ubuntu2) ...
Setting up libgl1-mesa-glx (7.11~1-0ubuntu2) ...
Setting up libegl1-mesa (7.11~1-0ubuntu2) ...
Setting up libopenvg1-mesa (7.11~1-0ubuntu2) ...
Setting up libegl1-mesa-drivers (7.11~1-0ubuntu2) ...
Setting up libglu1-mesa (7.11~1-0ubuntu2) ...
Setting up xserver-common (2:1.10.2-1ubuntu1) ...
Setting up xserver-xorg-core (2:1.10.2-1ubuntu1) ...
Setting up xserver-xorg-input-mouse (1:1.7.0-4) ...
Setting up xserver-xorg-input-vmmouse (1:12.7.0-2) ...
Setting up xserver-xorg-video-apm (1:1.2.3-2) ...
Setting up xserver-xorg-video-ark (1:0.7.3-2) ...
Setting up xserver-xorg-video-r128 (6.8.1-5) ...
Setting up xserver-xorg-video-mach64 (6.9.0-1) ...
Setting up xserver-xorg-video-radeon (1:6.14.2-1ubuntu1) ...
Setting up xserver-xorg-video-ati (1:6.14.2-1ubuntu1) ...
Setting up xserver-xorg-video-chips (1:1.2.4-1) ...
Setting up xserver-xorg-video-cirrus (1:1.3.2-2ubuntu7) ...
Setting up xserver-xorg-video-fbdev (1:0.4.2-3ubuntu6) ...
Setting up xserver-xorg-video-i128 (1:1.3.4-2) ...
Setting up xserver-xorg-video-i740 (1:1.3.2-4) ...
Setting up xserver-xorg-video-intel (2:2.15.0-3ubuntu2) ...
Setting up xserver-xorg-video-neomagic (1:1.2.5-1ubuntu3) ...
Setting up xserver-xorg-video-nouveau (1:0.0.16+git20110411+8378443-1) ...
Setting up xserver-xorg-video-rendition (1:4.2.4-0ubuntu5) ...
Setting up xserver-xorg-video-s3 (1:0.6.3-4) ...
Setting up xserver-xorg-video-s3virge (1:1.10.4-4) ...
Setting up xserver-xorg-video-savage (1:2.3.2-3ubuntu2) ...
Setting up xserver-xorg-video-siliconmotion (1:1.7.4-0ubuntu7) ...
Setting up xserver-xorg-video-sis (1:0.10.3-3) ...
Setting up xserver-xorg-video-sisusb (1:0.9.4-2) ...
Setting up xserver-xorg-video-tdfx (1:1.4.3-4) ...
Setting up xserver-xorg-video-trident (1:1.3.4-2) ...
Setting up xserver-xorg-video-tseng (1:1.2.4-2) ...
Setting up xserver-xorg-video-vesa (1:2.3.0-7) ...
Setting up xserver-xorg-video-vmware (1:11.0.3-2) ...
Setting up xserver-xorg-video-voodoo (1:1.2.4-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

PPA purged successfully
paul@oneiric:~$ 
```

Was then able to boot directly into gnome-shell and all appears normal again so it does seem to be something to do with this:

```
http://blog.mraw.org/2011/06/18/mesa_a_disturbance_in_the_Force/
```

> Things aren’t exactly going as smoothly as expected. Here are some explanations.

First collateral damage: non-free fglrx and nvidia drivers.

We have to admit we didn’t think of those when we moved libGL.so.1 (and friends) from /usr/lib to /usr/lib/<triplet> (that’s the move we call “adding multiarch support”). In the mesa 7.10.3-2 upload, some Breaks statements were added to prevent users from installing new mesa packages if they still have old (without multiarch support) fglrx or nvidia packages.

Solution: Sticking to the mesa packages in testing is the way to go until fixed fglrx and nvidia packages are uploaded.

Second collateral damage: xserver-xorg-core in testing.

The plan was to rebuild the server in unstable against the new mesa libraries, so that it would look into the new /usr/lib/<triplet> directory for mesa drivers. Since no source changes were needed, we went for a binNMU as explained in the previous blog post.

That’s the usual way to deal with libraries, and does the job very nicely. But that failed in this special case, for the following reasons:

    The server only has libgl1-mesa-dri in Recommends, so there’s no hard dependency here.
    Usually, rebuilding a package against a new library means getting a dependency on the new library (typically because the binary compatibility has been broken, so the SONAME got bumped, meaning one depends on libfoo42 instead of libfoo41). And that means going in testing at the same time as the new library.

**[COLOR="Red"]But in this case, rebuilding against the new library just means having a different search path somewhere in libglx.so.[/COLOR]** So the rebuilt package (2:1.10.2-1+b1) happily reached testing, which still contains the old mesa packages, which ship their files in the old /usr/lib path!

Solution: Stick to 2:1.10.2-1 packages (snapshot.debian.org to the rescue), or wait a bit and get fixed packages.

To get fixed packages, two things were needed:

    Getting the server package fixed in unstable: that means adding Breaks against old (pre-multiarch) mesa packages, as seen in 2:1.10.2-2. This will ensure that new server package built against new mesa will not be co-installable with old mesa packages, and both mesa and the server should migrate together to testing.
    Getting the server built again within testing, so that it gets built against old mesa, so that both mesa and the server in testing remains without multiarch until the packages in unstable are ready to migrate together.

While taking care of that second step, it was discovered that many buildds are still lacking a testing chroot, so there might be some delay until the server is rebuilt in testing (as 2:1.10.2-1+wheezy1). Eager users can use the time travel machine mentioned above to get stuff working again sooner.

(As far as I can tell, the last problematic combination which would remain would be 2:1.10.2-1+wheezy1 server with new mesa, but we’ll make sure we update the Breaks in the new mesa to make sure that it can’t happen. Since it’s not as urgent as getting the server in testing fixed, it’s only queued for mesa 7.10.3-3 for now.)

---

### Post by Quackers on 2011-07-01
Thanks Harry33. Gnome-shell now loads but when I try to do anything (like open Applications menu) it just crashes. This is a fresh install from alpha1 and I had the "graphics drivers are activated but not in use" error in respect of both Nvidia 173 and nvidia-current.
I removed them via terminal, rebooted and installed nvidia-current via terminal. Now desktop effects work and gnome-shell boots to a desktop - complete with top panel :-)
Sadly, it's just not usable :-(

Should the gnome3 team ppa now be disabled?

---

### Post by mc4man on 2011-07-01
You could try something like this
```
sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu
```
Could be related to this bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/798951](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/798951)

(an alternative would be to 
sudo mv /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

---

### Post by Quackers on 2011-07-01
> **mc4man said:**
> You could try something like this
```
sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu
```
Could be related to this bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/798951](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/798951)

(an alternative would be to 
sudo mv /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

Well that's done that! Perfect now :-) Everything works as it should (or so it appears for the moment).
Thanks mc4man! :D:D

Using terminal I am getting a dodgy looking message, but it doesn't appear to affect anything
```
ocelot2@ocelot2-VGN-AR51SU:~$ gksu gedit /usr/share/themes/Adwaita/metacity-1/metacity-theme-3.xml
glibtop: Non-standard uts for running kernel:
release 3.0-2-generic=3.0.0 gives version code 196608
```
System is fully updated.
Any clues there?

---

### Post by mc4man on 2011-07-01
> 
Using terminal I am getting a dodgy looking message, but it doesn't appear to affect anything
I'd think that would be fairly common atm when using gksu(do) from a terminal,, no apparent consequence

(myself usually use the run dialog or nautilus-actions for such stuff, it either works or doesn't. The terminal is sometimes useful if it doesn't.

edit: on this install I'm using an older kernel (2.6.38-9) and gksu comes up clean

---

### Post by Quackers on 2011-07-01
Ok thanks. It certainly doesn't seem to affect anything, as you say.

---

### Post by paul_in_london on 2011-07-01
> **Quackers said:**
> Thanks Harry33. Gnome-shell now loads but when I try to do anything (like open Applications menu) it just crashes. This is a fresh install from alpha1 and I had the "graphics drivers are activated but not in use" error in respect of both Nvidia 173 and nvidia-current.
I removed them via terminal, rebooted and installed nvidia-current via terminal. Now desktop effects work and gnome-shell boots to a desktop - complete with top panel :-)
Sadly, it's just not usable :-(

Should the gnome3 team ppa now be disabled?

nvidia-current is in use on my other (working) box @home, but I haven't updated that one for a few days so I'll see what happens there when I get a chance.

A bit off-topic I know, but yesterday's updates also screwed up OO + gnome-shell on my Virtualbox 4.08 VM (**Win XP host**) @work. It was previously fine. Apparently the same issue I've already posted about.

Btw, so far OO + gnome-shell has never been usable for me in VirtualBox with an **OO host**. gnome-shell typically loads initially, but crashes randomly especially if I try and click on anything! I gather 4.10 doesn't necessarily fix this.

---

### Post by paul_in_london on 2011-07-01
After today's updates (and with the **xorg-edgers** and **ricotz** ppas re-enabled), I can boot straight into a working gnome-shell again. :)

Haven't tried on the other box yet with nvidia though...

---

