---
title: "Accidentally uninstalled Ubuntu 13.04 (all of it)"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by robsalamo on 2013-09-16
Funny story, and I'm curious what the trigger was. I decided yesterday to try Ubuntu 13.04. Steam was the first app I installed. I ended up with the same error as fruitz:[http://ubuntuforums.org/showthread.php?t=2116667](http://ubuntuforums.org/showthread.php?t=2116667).

After skimming that thread I just decided to run an apt-get remove on all relevant packages, and it uninstalled all of Ubuntu which, obviously, caught me by surprise.

I used 'sudo apt-get remove' to delete libgl1-mesa-dri, steam, libgl1-mesa-glx, libglapi-mesa, and libdrm2.

After reboot all that was left was the bootloader. I haven't tried to reproduce it.

I work in Red Hat, but I'm completely new to Ubuntu and dpkg/apt. Are there any big red flags in that apt-get line that I should have noticed?

---

### Post by fireflower on 2013-09-17
1) Running 64 bit Steam on 64 bit Ubuntu shouldn't be a problem. (Anecdote: That was my experience in 12.04.) The thread you referred to appears to be about a mismatch of 32 bit Steam with 64 bit Ubuntu.

2) The last time I posted here (10.04) there were rules about posting dangerous code. I realize this case is an exception to those rules. It just freaks me out, seeing something that could brick my computer. I agree that obviously there is a problem; you shouldn't be able to do this kind of thing accidentally.

---

### Post by coffeecat on 2013-09-17
> **robsalamo said:**
> Are there any big red flags in that apt-get line that I should have noticed?

None in the actual line that I could see, but there would have been a huge red flag together with wailing siren in the terminal output. I don't have steam installed, but the two packages in the remove list either side of steam come in a default installation, so I ran this command on my 13.04 system confident that I could back out at the last minute:

```
sudo apt-get remove libgl1-mesa-dri libgl1-mesa-glx
```

After the password prompt, this is what I saw:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  aften audacity-data bluez-alsa:i386 cdparanoia clamav clamav-base
  clamav-freshclam dkms dvdisaster dvdisaster-doc dvdstyler-data faac
  glib-networking:i386 gstreamer0.10-plugins-base:i386
  gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386
  gtk2-engines-murrine:i386 gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386
  ibus-gtk:i386 k3b-data lib32gcc1 libaa1:i386 libaccounts-qt5-1 libaio1:i386
  libao4:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libaudio2:i386 libaudiofile1:i386 libavc1394-0:i386
  libbit-vector-perl libboost-filesystem1.49.0 libboost-regex1.49.0
  libboost-system1.49.0 libcaca0:i386 libcairo-gobject2:i386
  libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386
  libcapi20-3:i386 libcarp-clan-perl libcdparanoia0:i386 libclamav6
  libcupsfilters1:i386 libcupsimage2:i386 libcurl3:i386 libdate-calc-perl
  libdate-calc-xs-perl libdbus-glib-1-2:i386 libdbus-glib1.0-cil
  libdbus1.0-cil libdee-qt5-3 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdv4:i386 libesd0:i386 libexif12:i386 libflac++6
  libflac8:i386 libgail-common:i386 libgail18:i386 libgconf-2-4:i386
  libgconf2.0-cil libgd2-xpm:i386 libgdata2.1-cil libgdbm3:i386
  libgettextpo0:i386 libgexiv2-2 libgkeyfile1.0-cil libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386
  libgnome-keyring0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libgtk-sharp-beans-cil libgudev-1.0-0:i386
  libgudev1.0-cil libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libibus-1.0-0:i386
  libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libk3b6
  libkcddb4 libkrb5-26-heimdal:i386 liblcms1:i386 libldap-2.4-2:i386
  libllvm3.2:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386 libmng1:i386
  libmono-data-tds4.0-cil libmono-system-data4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-runtime-serialization4.0-cil
  libmono-system-transactions4.0-cil libmono-system-xml-linq4.0-cil
  libmono-zeroconf1.0-cil libmpg123-0:i386 libmysqlclient18:i386
  libnewtonsoft-json4.5-cil libnotify0.4-cil libnspr4:i386 libnss3:i386
  libodbc1:i386 libogg0:i386 liboggz2 libogmrip1 libopenal1:i386
  liborc-0.4-0:i386 libpciaccess0:i386 libportsmf0 libproxy1:i386
  libpulse-mainloop-glib0:i386 libpulse0:i386 libpulsedsp:i386
  libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386
  libqt4-network:i386 libqt4-opengl:i386 libqt4-qt3support:i386
  libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386
  libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386
  libqt4-xmlpatterns:i386 libqt5graphicaleffects5 libqt5network5 libqt5qml5
  libqt5v8-5 libqt5xml5 libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386
  libraw1394-11:i386 libroken18-heimdal:i386 librtmp0:i386 libsamplerate0:i386
  libsane:i386 libsasl2-2:i386 libsasl2-modules:i386 libsbsms10
  libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386
  libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libshout3:i386 libsignon-qt5-1
  libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libsoxr0
  libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386
  libssl1.0.0:i386 libstdc++5:i386 libtag1-vanilla:i386 libtag1c2a:i386
  libtaglib2.1-cil libtdb1:i386 libtheora0:i386 libtommath0
  libtxc-dxtn-s2tc0:i386 libunistring0:i386 libusb-0.1-4:i386
  libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386 libvamp-hostsdk3
  libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386
  libvorbisenc2:i386 libvorbisfile3:i386 libwavpack1:i386 libwebp4:i386
  libwind0-heimdal:i386 libwrap0:i386 libwxbase2.8-0 libx11-xcb1:i386
  libxaw7:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxmu6:i386 libxp6:i386
  libxpm4:i386 libxslt1.1:i386 libxss1:i386 libxtst6:i386 libxv1:i386
  libxxf86vm1:i386 linux-headers-3.8.0-19 linux-headers-3.8.0-19-generic
  linux-headers-3.8.0-25 linux-headers-3.8.0-25-generic
  linux-image-3.8.0-19-generic linux-image-3.8.0-25-generic
  linux-image-extra-3.8.0-19-generic linux-image-extra-3.8.0-25-generic
  linux-image-generic mkvtoolnix mysql-common odbcinst1debian2:i386 oggz-tools
  ogmrip-dirac ogmrip-doc ogmrip-oggz qtdeclarative5-friends-plugin
  ubuntu-ui-toolkit-theme xaw3dg:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-generic-oauth account-plugin-google account-plugin-identica
  account-plugin-jabber account-plugin-salut account-plugin-twitter
  account-plugin-windows-live account-plugin-yahoo acidrip apturl audacity
  banshee banshee-extension-soundmenu brasero clamtk compiz compiz-gnome
  compiz-plugins-default deja-dup-backend-gvfs devede dvdstyler empathy
  evolution-data-server friends-facebook friends-identica friends-twitter gimp
  gir1.2-gdata-0.0 gir1.2-goa-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-3.0 gnome-contacts gnome-control-center
  gnome-control-center-signon gnome-control-center-unity gnome-session
  gnome-session-bin gnome-user-guide google-earth-stable gpac
  gpac-modules-base gstreamer1.0-clutter gstreamer1.0-plugins-bad gvfs
  gvfs:i386 gvfs-backends gvfs-daemons gvfs-fuse gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter handbrake-gtk hplip-gui
  ia32-libs ia32-libs-multiarch:i386 indicator-datetime indicator-power k3b
  kcharselect kde-runtime kdelibs5-plugins kubuntu-debug-installer
  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcogl-pango12
  libcogl12 libedata-book-1.2-15 libegl1-mesa libegl1-mesa-drivers
  libfolks-eds25 libgbm1 libgdata13 libgl1-mesa-dri libgl1-mesa-glx libglew1.8
  libglewmx1.8 libglu1-mesa libgoa-1.0-0 libgpac2 libkactivities-bin
  libkactivities-models1 libkactivities6 libkdewebkit5 libnux-4.0-0
  libokularcore2abi1 libplasma3 libqt4-opengl libqt5gui5 libqt5quick5
  libqt5svg5 libqt5widgets5 libqtwebkit4 libreoffice-ogltrans
  librhythmbox-core6 libtotem0 libunity-core-6.0-5 libvisual-0.4-plugins
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwxgtk2.8-0 libwxsvg0 libxatracker1
  libxine2-x libyelp0 lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure mcp-account-manager-uoa mencoder
  mesa-utils mplayer nautilus nautilus-sendto nautilus-sendto-empathy
  nautilus-share nux-tools ogmrip ogmrip-ac3 ogmrip-mpeg ogmrip-profiles
  ogmrip-video-copy okular phonon phonon-backend-gstreamer
  plasma-scriptengine-javascript python-qt4 qapt-batch
  qtdeclarative5-accounts-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin rhythmbox rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone shotwell
  signon-plugin-oauth2 signon-ui smplayer smplayer-themes
  smplayer-translations software-center totem totem-mozilla totem-plugins
  ubuntu-desktop ubuntu-docs ubuntu-release-upgrader-gtk ubuntu-sso-client-qt
  ubuntuone-control-panel-qt unity unity-lens-photos unity-scope-gdrive
  unity-scope-musicstores update-manager update-notifier vlc
  webaccounts-extension-common x11-utils xine-ui xorg xserver-xorg-video-all
  xserver-xorg-video-vmware xul-ext-webaccounts yelp zenity
0 upgraded, 0 newly installed, 172 to remove and 0 not upgraded.
After this operation, 643 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

``` 

The "The following packages were automatically installed and are no longer required:" part is only a FYI message and may have distracted you, but it is followed by a clear "The following packages will be REMOVED" announcement. My list will include packages that you may not have had installed, but looking at those which would have been common to both of our installations, I think you've hosed the GUI rather than the whole operating system.

**EDIT**: in case you used apt-get autoremove instead of apt-get remove, it gets even more alarming. Running...

```
sudo apt-get autoremove libgl1-mesa-dri libgl1-mesa-glx
```

Gives me:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-generic-oauth account-plugin-google account-plugin-identica
  account-plugin-jabber account-plugin-salut account-plugin-twitter
  account-plugin-windows-live account-plugin-yahoo acidrip aften apturl
  audacity audacity-data banshee banshee-extension-soundmenu bluez-alsa:i386
  brasero cdparanoia clamav clamav-base clamav-freshclam clamtk compiz
  compiz-gnome compiz-plugins-default deja-dup-backend-gvfs devede dkms
  dvdisaster dvdisaster-doc dvdstyler dvdstyler-data empathy
  evolution-data-server faac friends-facebook friends-identica friends-twitter
  gimp gir1.2-gdata-0.0 gir1.2-goa-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-3.0 glib-networking:i386 gnome-contacts gnome-control-center
  gnome-control-center-signon gnome-control-center-unity gnome-session
  gnome-session-bin gnome-user-guide google-earth-stable gpac
  gpac-modules-base gstreamer0.10-plugins-base:i386
  gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gstreamer1.0-clutter
  gstreamer1.0-plugins-bad gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs gvfs:i386
  gvfs-backends gvfs-daemons gvfs-fuse gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter handbrake-gtk hplip-gui
  ia32-libs ia32-libs-multiarch:i386 ibus-gtk:i386 indicator-datetime
  indicator-power k3b k3b-data kcharselect kde-runtime kdelibs5-plugins
  kubuntu-debug-installer lib32gcc1 libaa1:i386 libaccounts-qt5-1 libaio1:i386
  libao4:i386 libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libaudio2:i386 libaudiofile1:i386 libavc1394-0:i386
  libbit-vector-perl libboost-filesystem1.49.0 libboost-regex1.49.0
  libboost-system1.49.0 libcaca0:i386 libcairo-gobject2:i386
  libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386
  libcapi20-3:i386 libcarp-clan-perl libcdparanoia0:i386 libclamav6
  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcogl-pango12
  libcogl12 libcupsfilters1:i386 libcupsimage2:i386 libcurl3:i386
  libdate-calc-perl libdate-calc-xs-perl libdbus-glib-1-2:i386
  libdbus-glib1.0-cil libdbus1.0-cil libdee-qt5-3 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdv4:i386 libedata-book-1.2-15
  libegl1-mesa libegl1-mesa-drivers libesd0:i386 libexif12:i386 libflac++6
  libflac8:i386 libfolks-eds25 libgail-common:i386 libgail18:i386 libgbm1
  libgconf-2-4:i386 libgconf2.0-cil libgd2-xpm:i386 libgdata13 libgdata2.1-cil
  libgdbm3:i386 libgettextpo0:i386 libgexiv2-2 libgkeyfile1.0-cil
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa:i386 libglew1.8 libglewmx1.8 libglu1-mesa libglu1-mesa:i386
  libgnome-keyring0:i386 libgoa-1.0-0 libgpac2 libgphoto2-2:i386
  libgphoto2-port0:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libgtk-sharp-beans-cil libgudev-1.0-0:i386 libgudev1.0-cil
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhx509-5-heimdal:i386 libibus-1.0-0:i386 libiec61883-0:i386
  libieee1284-3:i386 libjack-jackd2-0:i386 libk3b6 libkactivities-bin
  libkactivities-models1 libkactivities6 libkcddb4 libkdewebkit5
  libkrb5-26-heimdal:i386 liblcms1:i386 libldap-2.4-2:i386 libllvm3.2:i386
  libltdl7:i386 libmad0:i386 libmikmod2:i386 libmng1:i386
  libmono-data-tds4.0-cil libmono-system-data4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-runtime-serialization4.0-cil
  libmono-system-transactions4.0-cil libmono-system-xml-linq4.0-cil
  libmono-zeroconf1.0-cil libmpg123-0:i386 libmysqlclient18:i386
  libnewtonsoft-json4.5-cil libnotify0.4-cil libnspr4:i386 libnss3:i386
  libnux-4.0-0 libodbc1:i386 libogg0:i386 liboggz2 libogmrip1
  libokularcore2abi1 libopenal1:i386 liborc-0.4-0:i386 libpciaccess0:i386
  libplasma3 libportsmf0 libproxy1:i386 libpulse-mainloop-glib0:i386
  libpulse0:i386 libpulsedsp:i386 libqt4-dbus:i386 libqt4-declarative:i386
  libqt4-designer:i386 libqt4-network:i386 libqt4-opengl libqt4-opengl:i386
  libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386
  libqt4-sql:i386 libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqt5graphicaleffects5 libqt5gui5
  libqt5network5 libqt5qml5 libqt5quick5 libqt5svg5 libqt5v8-5 libqt5widgets5
  libqt5xml5 libqtcore4:i386 libqtgui4:i386 libqtwebkit4 libqtwebkit4:i386
  libraw1394-11:i386 libreoffice-ogltrans librhythmbox-core6
  libroken18-heimdal:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386
  libsasl2-2:i386 libsasl2-modules:i386 libsbsms10 libsdl-image1.2:i386
  libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386
  libsdl1.2debian:i386 libshout3:i386 libsignon-qt5-1 libsndfile1:i386
  libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libsoxr0 libspeex1:i386
  libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386
  libstdc++5:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtaglib2.1-cil
  libtdb1:i386 libtheora0:i386 libtommath0 libtotem0 libtxc-dxtn-s2tc0:i386
  libunistring0:i386 libunity-core-6.0-5 libusb-0.1-4:i386 libusb-1.0-0:i386
  libv4l-0:i386 libv4lconvert0:i386 libvamp-hostsdk3 libvisual-0.4-0:i386
  libvisual-0.4-plugins libvisual-0.4-plugins:i386 libvorbis0a:i386
  libvorbisenc2:i386 libvorbisfile3:i386 libwavpack1:i386 libwebkitgtk-1.0-0
  libwebkitgtk-3.0-0 libwebp4:i386 libwind0-heimdal:i386 libwrap0:i386
  libwxbase2.8-0 libwxgtk2.8-0 libwxsvg0 libx11-xcb1:i386 libxatracker1
  libxaw7:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxine2-x libxmu6:i386
  libxp6:i386 libxpm4:i386 libxslt1.1:i386 libxss1:i386 libxtst6:i386
  libxv1:i386 libxxf86vm1:i386 libyelp0 lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure linux-headers-3.8.0-19
  linux-headers-3.8.0-19-generic linux-headers-3.8.0-25
  linux-headers-3.8.0-25-generic linux-image-3.8.0-19-generic
  linux-image-3.8.0-25-generic linux-image-extra-3.8.0-19-generic
  linux-image-extra-3.8.0-25-generic linux-image-generic
  mcp-account-manager-uoa mencoder mesa-utils mkvtoolnix mplayer mysql-common
  nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share nux-tools
  odbcinst1debian2:i386 oggz-tools ogmrip ogmrip-ac3 ogmrip-dirac ogmrip-doc
  ogmrip-mpeg ogmrip-oggz ogmrip-profiles ogmrip-video-copy okular phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript python-qt4
  qapt-batch qtdeclarative5-accounts-plugin qtdeclarative5-friends-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-ui-toolkit-plugin
  rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone shotwell signon-plugin-oauth2 signon-ui smplayer
  smplayer-themes smplayer-translations software-center totem totem-mozilla
  totem-plugins ubuntu-desktop ubuntu-docs ubuntu-release-upgrader-gtk
  ubuntu-sso-client-qt ubuntu-ui-toolkit-theme ubuntuone-control-panel-qt
  unity unity-lens-photos unity-scope-gdrive unity-scope-musicstores
  update-manager update-notifier vlc webaccounts-extension-common x11-utils
  xaw3dg:i386 xine-ui xorg xserver-xorg-video-all xserver-xorg-video-vmware
  xul-ext-webaccounts yelp zenity
0 upgraded, 0 newly installed, 403 to remove and 0 not upgraded.
After this operation, 1,426 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```

Either way, you are given advance warning.

---

### Post by Impavidus on 2013-09-17
As to the solution: Reinstall your system. Any personal files should still be present and can be accessed using a live disk.

---

### Post by buzzingrobot on 2013-09-17
> **coffeecat said:**
> ...you are given advance warning.

This is a bit OT, but...

Yes, a warning was displayed. The warning, though, was buried in a lengthy stream of package names that scrolled by in a second. That warning was off the top of the screen in an instant.

Would be nice if apt-get would page its output, per the dimensions of the terminal it's in, and format those "Here's what I'm gonna remove..." warnings to draw attentionn. (All caps? Bolded?)

For the OP:

Sad to say, I expect reinstalling is the fastest way to repair this. If /home is not backed up, you can preserve it by selecting "Something Else" in the installer's partitioning phase (that's manual partitioning), then highlight each existing partition name, select "Change", set the filesystem to Ext4, and check the format box. BUT, for /home, do not check the format box.

---

### Post by coffeecat on 2013-09-17
> **buzzingrobot said:**
> This is a bit OT, but...

Yes, a warning was displayed. The warning, though, was buried in a lengthy stream of package names that scrolled by in a second. That warning was off the top of the screen in an instant.

Not necessarily OT because this is about a warning not being enough to prevent a user from severely damaging their system. You have a good point. I wouldn't presume to suggest I know the thinking of the apt-get devs/maintainers, but I'd guess they assume that someone able to use apt-get in the terminal is experienced enough to check what's about to be removed before OK-ing it. Whether that's a reasonable assumption is a matter of opinion, of course.

More worrying, because this might affect beginners, is what you see when you try to remove libgl1-mesa-dri using Software Centre.

[ATTACH=CONFIG]246302[/ATTACH]

You and I and many forum members would know that it is not really a good idea to remove Xorg as well (deliberate ironic understatement!), but a lot of beginners might not. How would the devs implement a "if you proceed you risk borking your system" message? I don't know, but it's an interesting situation.

---

### Post by robsalamo on 2013-09-17
Thanks, all. It was unintentionally a malicious code post. I apologize for that, and I'll break it up just so it isn't prominent in the OP.

And you're all correct. I agreed to the removal without really paying attention to the package list (dumb). I would like to claim ignorance because I'm a yum user, but yum would have done the same thing (big, scrolled list of packages to remove followed by a simple y\N prompt). In short - pay attention when removing packages.

I wasn't concerned about the recovery process. I do have /home split off into another partition, but it was also blank. This was a clean install on an old, blank laptop.

Thanks for the responses!

---

### Post by buzzingrobot on 2013-09-17
Yes, I've run into the same thing with yum.

This is really a dependency issue across Linux.  I.e. how they are created and why we run into those seemingly exponential explosions of dependency chains.

---

