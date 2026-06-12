---
title: "Got the ECS LIVA micro PC, can't install any version of Linux"
date: 2014-09-27
forum: New to Ubuntu
---

### Post by dale8 on 2014-09-27
Hello, my first time here and new to Linux.  I purchased an ECS LIVA PC kit and put it together and downloaded Lubuntu, along with unetbootin and created a USB install drive.  When I boot from that drive I am greeted with a DOS-like screen with the following text:

```
GNU GRUB version 2.02~beta2-9ubuntu1
Minimal-BASH-like line editing is supported....[etc]

grub>
```

Everywhere I search for help, I find advice similar to the following: "Create boot disk, blah blah lots of instructions... Boot from disk and follow instructions to install..."  I've tried Lubuntu and Mint and both show the same screen with some minor variations to the first line and the stupid command prompt.

I realize I am jumping into a new OS environment and I will need to learn how it works, but right out of the box I get nothing.  Not pleased, but in all fairness I think it might just be a quirk of the ECS LIVA or my own lack of knowledge.  Will someone help me understand what I am doing wrong, or if I am on the right track, provide me with the next steps?  A GUI would really be nice.

---

### Post by QIII on 2014-09-27
Hello!

It would be very helpful if you posted the specs of your machine rather than assuming others will be familiar with it or look it up.

Thanks.

---

### Post by dale8 on 2014-09-27
Sure I can - 
ECS LIVA link: [www.ecs.com.tw/LIVA](www.ecs.com.tw/LIVA) & [http://www.newegg.com/Product/Product.aspx?Item=N82E16856501007](http://www.newegg.com/Product/Product.aspx?Item=N82E16856501007)
Intel Bay Trail-M SoC N2807 1.58 GHz ([http://ark.intel.com/products/81072/Intel-Celeron-Processor-N2807-1M-Cache-up-to-2_16-GHz](http://ark.intel.com/products/81072/Intel-Celeron-Processor-N2807-1M-Cache-up-to-2_16-GHz))
2GB Ram
32GB eMCC storage
It supports only Windows 8.1 and Linux, according to what I've read (due to drivers I think).

---

### Post by dale8 on 2014-09-28
If owners of this device want to install Linux instead of Windows, they have to download the drivers package at [http://www.ecs.com.tw/LIVA/support.html](http://www.ecs.com.tw/LIVA/support.html)

Inside the package is a Word document written by an Intel engineer documenting their work on getting their Bay Trail SOCs to work with Linux.  My trouble came from not formatting the USB stick with "GPT partition scheme for UEFI computer."  I also used Rufus instead of Unetboot, which had an option for specific types of formatting.

I've attached the document to this post.  I think the DOS-like menu I kept seeing was some kind of debug menu - surely someone here knows what it is (I described it in my initial post).  Simply pointing that out would have been a huge help, as I thought it was the installer.

---

### Post by sligett on 2014-10-24
Hi dale8 - I'm happy I stumbled upon your question. The Intel doc you pointed to helped me install Ubuntu 14.04 on the ECS Liva. If you do want to find out more about what you originally saw, google "grub prompt". (I don't know anything about grub, really.) 

thanks

---

### Post by JKyleOKC on 2014-10-24
> **dale8 said:**
>  I think the DOS-like menu I kept seeing was some kind of debug menu - surely someone here knows what it is (I described it in my initial post).  Simply pointing that out would have been a huge help, as I thought it was the installer.You're correct that it's a debug menu, part of "grub" which is the "**GR**and **U**nified **B**ootloader" program that does for many Linux distributions what the "iosys.sys" program did for older versions of Windows -- controls loading of the actual system into RAM, starting from power up when absolutely nothing is in memory.

The giveaway is that "grub>" prompt you got. This means that the program could not do its job and is asking for guidance from you, which of course is almost impossible when you encounter it as you did!

I'm not at all familiar with your hardware but apparently it requires some tricky handling. I'm glad that Sligett jumped in and added some meaningful comments. Hope you get it all working!

---

### Post by VanillaXtract on 2014-12-31
I also purchased one of these. I have been able to install Trusty-desktop with no issues. But I would rather install server. However, at the partitioning step, it does not seem to recognize the internal storage. All I see is what is in the screen shot. Any ideas for what is causing the issue?
[IMG]http://s8.postimg.org/j85kxdct1/unnamed.jpg[/IMG]

---

### Post by vijayan2 on 2015-01-02
I also have the same the issue - Ubuntu 14.04.1 Server  installation [COLOR=#000000]does not seem to recognize the internal storage[/COLOR] . 

I did a workaround to get Ubuntu 14.04.1 Server on ECS Liva micro PC:
[LIST=1]
[*]Install Ubuntu 14.04.1 Desktop .
[*]Convert Ubuntu 14.04.1 Desktop to Ubuntu 14.04.1 Server.
[/LIST]

**Convert Ubuntu 14.04.1 Desktop to Ubuntu 14.04.1 Server**
[LIST=1]
[*]Switch to the Terminal Mode.
[*]Execute the following commands:
[/LIST]
[INDENT]sudo apt-get install tasksel[/INDENT]
[INDENT]sudo tasksel remove ubuntu-desktop[/INDENT]
[INDENT]sudo tasksel install server[/INDENT]
[INDENT]sudo apt-get update[/INDENT]
[INDENT]sudo apt-get install linux-server linux-image-server[/INDENT]
[INDENT]sudo apt-get purge lightdm[/INDENT]


Also, the system will freeze when restarting ubuntu. I followed the info provided at the following link:

[http://michalorman.com/2013/10/fix-ubuntu-freeze-during-restart/](http://michalorman.com/2013/10/fix-ubuntu-freeze-during-restart/)

---

### Post by VanillaXtract on 2015-01-05
Thank you for your help. My ultimate goal is to have a minimal install for Kodi (xbmc). While this doesn't quite get me down to the ~2GB a minimal install does, it does get rid of the desktop, which definitely helps.

---

### Post by vital-0 on 2015-05-06
> **vijayan2 said:**
> I also have the same the issue - Ubuntu 14.04.1 Server  installation [COLOR=#000000]does not seem to recognize the internal storage[/COLOR] . 

I did a workaround to get Ubuntu 14.04.1 Server on ECS Liva micro PC:
[LIST=1]
[*]Install Ubuntu 14.04.1 Desktop . 
[*]Convert Ubuntu 14.04.1 Desktop to Ubuntu 14.04.1 Server. 
[/LIST]

Thank you for the workaround, it works!

To further remove desktop packages I made a quick and dirty comparison of installed package lists (*dpkg --get-selections | grep -v deinstall*) with a Ubuntu Server 14.04.2. 
I'd like to share it in case someone wants to free up 2 GiB of disk space and decrease the attack surface.[INDENT]**Warning:** run it from console not over ssh as it will drop your network connection when uninstalling network-manager package.
Editing */etc/network/interfaces* by adding the following may help if using DHCP address:
```
auto eth0
iface eth0 inet dhcp

```
[/INDENT]
Cleaning up:
```
sudo aptitude install python-newt
sudo aptitude purge acl acpi-support alsa-base alsa-utils anacron app-install-data app-install-data-partner apport-gtk aptdaemon aptdaemon-data aspell aspell-en at-spi2-core avahi-autoipd avahi-daemon avahi-utils binutils bluez bluez-alsa:amd64 bluez-cups brasero-common brltty colord cpp cpp-4.8 cups cups-browsed cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers cups-ppdc cups-server-common dbus-x11 dc dconf-gsettings-backend:amd64 dconf-service desktop-file-utils dialog dictionaries-common diffstat dmz-cursor-theme dnsmasq-base doc-base dvd+rw-tools enchant espeak-data:amd64 ethtool evince evince-common file-roller firefox firefox-locale-en fontconfig fontconfig-config fonts-dejavu-core fonts-droid fonts-freefont-ttf fonts-kacst fonts-kacst-one fonts-khmeros-core fonts-lao fonts-liberation fonts-lklug-sinhala fonts-opensymbol fonts-sil-abyssinica fonts-sil-padauk fonts-takao-pgothic fonts-thai-tlwg fonts-tibetan-machine fonts-tlwg-garuda fonts-tlwg-kinnari fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree foomatic-db-compressed-ppds gcc gcc-4.8 gconf-service gconf-service-backend gconf2 gconf2-common gcr gdb gdisk gedit gedit-common genisoimage gettext ghostscript ghostscript-x gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-gmenu-3.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-soup-2.4 gir1.2-totem-plparser-1.0 gir1.2-udisks-2.0 gir1.2-unity-5.0:amd64 gir1.2-vte-2.90 gir1.2-wnck-3.0 glib-networking:amd64 glib-networking-common glib-networking-services gnome-accessibility-themes gnome-calculator gnome-icon-theme gnome-icon-theme-symbolic gnome-keyring gnome-menus gnome-orca growisofs gsettings-desktop-schemas gsettings-ubuntu-schemas gsfonts gstreamer0.10-plugins-base-apps gstreamer0.10-tools gtk2-engines-murrine:amd64 gucharmap gvfs:amd64 gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs:amd64 hardening-includes hicolor-icon-theme hplip hplip-data humanity-icon-theme hunspell-en-us hyphen-en-us im-config indicator-application indicator-messages inputattach intltool-debian iputils-arping kerneloops-daemon language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base language-selector-gnome libaa1:amd64 libaccounts-glib0:amd64 libappindicator3-1 libapt-pkg-perl libarchive-zip-perl libarchive13:amd64 libart-2.0-2:amd64 libasan0:amd64 libasound2:amd64 libasound2-data libaspell15 libasprintf-dev:amd64 libassuan0:amd64 libatasmart4:amd64 libatk-adaptor:amd64 libatk-bridge2.0-0:amd64 libatk1.0-0:amd64 libatk1.0-data libatkmm-1.6-1:amd64 libatomic1:amd64 libatspi2.0-0:amd64 libauthen-sasl-perl libautodie-perl libavahi-client3:amd64 libavahi-common-data:amd64 libavahi-common3:amd64 libavahi-core7:amd64 libavahi-glib1:amd64 libavahi-gobject0:amd64 libbluetooth3:amd64 libbrlapi0.6:amd64 libburn4 libc-dev-bin libc6-dbg:amd64 libc6-dev:amd64 libcaca0:amd64 libcairo-gobject2:amd64 libcairo2:amd64 libcairomm-1.0-1:amd64 libcdparanoia0:amd64 libclone-perl libcloog-isl4:amd64 libclutter-1.0-0:amd64 libclutter-1.0-common libclutter-gtk-1.0-0:amd64 libcogl-common libcogl-pango15:amd64 libcogl15:amd64 libcolord1:amd64 libcolorhug1:amd64 libcroco3:amd64 libcrypt-passwdmd5-perl libcups2:amd64 libcupscgi1:amd64 libcupsfilters1:amd64 libcupsimage2:amd64 libcupsmime1:amd64 libcupsppdc1:amd64 libdaemon0 libdatrie1:amd64 libdbusmenu-glib4:amd64 libdbusmenu-gtk3-4:amd64 libdbusmenu-gtk4:amd64 libdconf1:amd64 libdee-1.0-4:amd64 libdigest-hmac-perl libdjvulibre-text libdjvulibre21:amd64 libdotconf0:amd64 libdpkg-perl libdrm-nouveau2:amd64 libdv4:amd64 libegl1-mesa-drivers-lts-utopic:amd64 libegl1-mesa-lts-utopic:amd64 libelfg0:amd64 libemail-valid-perl libenchant1c2a:amd64 libepoxy0 libevdev2 libevdocument3-4 libevview3-3 libexif12:amd64 libexiv2-12 libfftw3-single3:amd64 libfile-basedir-perl libfile-copy-recursive-perl libfile-desktopentry-perl libfile-fcntllock-perl libfile-mimeinfo-perl libfontconfig1:amd64 libfontembed1:amd64 libfontenc1:amd64 libframe6:amd64 libfreerdp1:amd64 libfs6:amd64 libgail-3-0:amd64 libgail-common:amd64 libgail18:amd64 libgbm1:amd64 libgbm1-lts-utopic:amd64 libgcc-4.8-dev:amd64 libgconf-2-4:amd64 libgcr-ui-3-1:amd64 libgd3:amd64 libgdk-pixbuf2.0-0:amd64 libgdk-pixbuf2.0-common libgee-0.8-2:amd64 libgeis1:amd64 libgeoclue0:amd64 libgettextpo-dev:amd64 libgettextpo0:amd64 libgexiv2-2:amd64 libgl1-mesa-dri-lts-utopic:amd64 libgl1-mesa-glx-lts-utopic:amd64 libglapi-mesa-lts-utopic:amd64 libgles1-mesa-lts-utopic:amd64 libgles2-mesa-lts-utopic:amd64 libglib2.0-bin libglibmm-2.4-1c2a:amd64 libglu1-mesa:amd64 libgmime-2.6-0:amd64 libgnome-bluetooth11 libgnome-keyring-common libgnome-keyring0:amd64 libgnome-menu-3-0 libgomp1:amd64 libgpgme11:amd64 libgphoto2-6:amd64 libgphoto2-l10n libgphoto2-port10:amd64 libgrail6 libgraphite2-3:amd64 libgrip0 libgs9 libgs9-common libgstreamer0.10-0:amd64 libgstreamer1.0-0:amd64 libgtk-3-0:amd64 libgtk-3-bin libgtk-3-common libgtk2.0-0:amd64 libgtk2.0-bin libgtk2.0-common libgtkmm-3.0-1:amd64 libgtksourceview-3.0-1:amd64 libgtksourceview-3.0-common libgucharmap-2-90-7 libgudev-1.0-0:amd64 libgusb2:amd64 libgutenprint2 libgxps2:amd64 libharfbuzz-icu0:amd64 libharfbuzz0b:amd64 libhpmud0 libhunspell-1.3-0:amd64 libical1 libice6:amd64 libicu52:amd64 libido3-0.1-0:amd64 libieee1284-3:amd64 libijs-0.35 libimobiledevice4:amd64 libindicator3-7 libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl libipc-run-perl libipc-system-simple-perl libisl10:amd64 libisofs6 libitm1:amd64 libjasper1:amd64 libjavascriptcoregtk-3.0-0:amd64 libjbig0:amd64 libjbig2dec0 libjpeg-turbo8:amd64 libjpeg8:amd64 libjson-glib-1.0-0:amd64 libjson-glib-1.0-common libjte1 libkpathsea6 liblcms2-2:amd64 libldb1:amd64 liblightdm-gobject-1-0 liblircclient0 liblist-moreutils-perl libllvm3.5:amd64 liblouis-data liblouis2:amd64 liblzo2-2:amd64 libmailtools-perl libmbim-glib0:amd64 libmessaging-menu0 libminiupnpc8 libmm-glib0:amd64 libmpc3:amd64 libmpfr4:amd64 libmtdev1:amd64 libmtp-common libmtp-runtime libmtp9:amd64 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-dns-perl libnet-domain-tld-perl libnet-ip-perl libnet-libidn-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnettle4:amd64 libnl-route-3-200:amd64 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4:amd64 libnspr4:amd64 libnss-mdns:amd64 libnss3:amd64 libnss3-nssdb libntdb1:amd64 libopenobex1 libopenvg1-mesa-lts-utopic:amd64 libp11-kit-gnome-keyring:amd64 libpackagekit-glib2-16:amd64 libpam-gnome-keyring:amd64 libpango-1.0-0:amd64 libpango1.0-0:amd64 libpangocairo-1.0-0:amd64 libpangoft2-1.0-0:amd64 libpangomm-1.4-1:amd64 libpangox-1.0-0:amd64 libpangoxft-1.0-0:amd64 libpaper-utils libpaper1:amd64 libpeas-1.0-0 libpeas-common libperl5.18 libperlio-gzip-perl libpixman-1-0:amd64 libplist1:amd64 libpoppler-glib8:amd64 libpoppler44:amd64 libproxy1:amd64 libpython3.4:amd64 libqmi-glib0:amd64 libqpdf13:amd64 libquadmath0:amd64 libraw9:amd64 librest-0.7-0:amd64 librsvg2-2:amd64 librsvg2-common:amd64 libsamplerate0:amd64 libsane:amd64 libsane-common libsane-hpaio libsecret-1-0:amd64 libsecret-common libsensors4:amd64 libsignon-glib1 libsm6:amd64 libsmbclient:amd64 libsnmp-base libsnmp30:amd64 libsocket6-perl libsonic0:amd64 libsoup-gnome2.4-1:amd64 libsoup2.4-1:amd64 libspectre1:amd64 libspeechd2:amd64 libspeexdsp1:amd64 libstartup-notification0:amd64 libsub-identify-perl libt1-5 libtag1-vanilla:amd64 libtag1c2a:amd64 libtalloc2:amd64 libtcl8.6:amd64 libtdb1:amd64 libtelepathy-glib0:amd64 libtevent0:amd64 libtext-levenshtein-perl libthai-data libthai0:amd64 libtiff5:amd64 libtk8.6:amd64 libtotem-plparser18 libtsan0:amd64 libtxc-dxtn-s2tc0:amd64 libudisks2-0:amd64 libunistring0:amd64 libunity-protocol-private0:amd64 libunity-scopes-json-def-desktop libunity9:amd64 libupower-glib1:amd64 liburi-perl liburl-dispatcher1:amd64 libusbmuxd2 libutempter0 libuuid-perl libv4l-0:amd64 libv4lconvert0:amd64 libvisual-0.4-0:amd64 libvisual-0.4-plugins:amd64 libvpx1:amd64 libvte-2.90-9 libvte-2.90-common libwavpack1:amd64 libwayland-client0:amd64 libwayland-cursor0:amd64 libwayland-egl1-mesa-lts-utopic:amd64 libwayland-server0:amd64 libwbclient0:amd64 libwebkitgtk-3.0-common libwebp5:amd64 libwebpmux1:amd64 libwnck-3-0:amd64 libwnck-3-common libwnck-common libwnck22 libx11-xcb1:amd64 libxatracker2-lts-utopic:amd64 libxaw7:amd64 libxcb-dri2-0:amd64 libxcb-dri3-0:amd64 libxcb-glx0:amd64 libxcb-keysyms1:amd64 libxcb-present0:amd64 libxcb-render0:amd64 libxcb-shape0:amd64 libxcb-shm0:amd64 libxcb-sync1:amd64 libxcb-util0:amd64 libxcb-xfixes0:amd64 libxcomposite1:amd64 libxcursor1:amd64 libxdamage1:amd64 libxfixes3:amd64 libxfont1:amd64 libxft2:amd64 libxi6:amd64 libxinerama1:amd64 libxkbcommon0:amd64 libxkbfile1:amd64 libxklavier16 libxmu6:amd64 libxp6:amd64 libxpm4:amd64 libxrandr2:amd64 libxrender1:amd64 libxres1:amd64 libxshmfence1:amd64 libxslt1.1:amd64 libxss1:amd64 libxt6:amd64 libxtst6:amd64 libxv1:amd64 libxvmc1:amd64 libxxf86dga1:amd64 libxxf86vm1:amd64 libyaml-tiny-perl libzeitgeist-2.0-0:amd64 lintian linux-libc-dev:amd64 linux-signed-generic-lts-utopic linux-signed-image-3.16.0-36-generic linux-signed-image-generic-lts-utopic linux-sound-base make manpages-dev mobile-broadband-provider-info modemmanager mscompress mtools myspell-en-au myspell-en-gb myspell-en-za nautilus-data network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome obex-data-server oneconf oneconf-common openoffice.org-hyphenation openprinting-ppds p11-kit p11-kit-modules:amd64 patchutils pcmciautils pkg-config plymouth-label policykit-1-gnome policykit-desktop-privileges poppler-data poppler-utils pptp-linux printer-driver-c2esp printer-driver-foo2zjs printer-driver-foo2zjs-common printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi printer-driver-splix python-aptdaemon python-aptdaemon.gtk3widgets python-cairo python-commandnotfound python-cups python-cupshelpers python-debtagshw python-defer python-dirspec python-gconf python-gi-cairo python-gnomekeyring python-gobject python-gobject-2 python-gtk2 python-imaging python-ldb python-libxml2 python-lxml python-notify python-ntdb python-oauthlib python-oneconf python-pexpect python-pil python-piston-mini-client python-renderpm python-reportlab python-reportlab-accel python-samba python-smbc python-talloc python-tdb python-twisted-web python-ubuntu-sso-client python-xdg python-zeitgeist python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-brlapi python3-cairo python3-chardet python3-crypto python3-debian python3-defer python3-gi-cairo python3-httplib2 python3-louis python3-newt python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-pyatspi python3-pycurl python3-six python3-software-properties python3-speechd python3-xdg python3-xkit qpdf rfkill rtkit samba-common samba-common-bin samba-libs:amd64 sane-utils sessioninstaller shim shim-signed shotwell-common simple-scan smbclient software-center-aptdaemon-plugins software-properties-common software-properties-gtk sound-theme-freedesktop ssh-askpass-gnome syslinux syslinux-common syslinux-legacy system-config-printer-common system-config-printer-gnome system-config-printer-udev t1utils tcl tcl8.6 tk tk8.6 toshset totem-common transmission-common transmission-gtk ttf-indic-fonts-core ttf-punjabi-fonts ttf-ubuntu-font-family ubuntu-drivers-common ubuntu-extras-keyring ubuntu-settings ubuntu-sso-client udisks2 update-inetd upower usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd wbritish wodim x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xcursor-themes xdg-user-dirs xdg-utils xfonts-base xfonts-encodings xfonts-scalable xfonts-utils xinit xinput xorg xorg-docs-core xserver-common xserver-xorg-core-lts-utopic xserver-xorg-input-all-lts-utopic xserver-xorg-input-evdev-lts-utopic xserver-xorg-input-mouse-lts-utopic xserver-xorg-input-synaptics-lts-utopic xserver-xorg-input-vmmouse-lts-utopic xserver-xorg-input-wacom-lts-utopic xserver-xorg-lts-utopic xserver-xorg-video-all-lts-utopic xserver-xorg-video-ati-lts-utopic xserver-xorg-video-cirrus-lts-utopic xserver-xorg-video-fbdev-lts-utopic xserver-xorg-video-intel-lts-utopic xserver-xorg-video-mach64-lts-utopic xserver-xorg-video-mga-lts-utopic xserver-xorg-video-modesetting-lts-utopic xserver-xorg-video-neomagic-lts-utopic xserver-xorg-video-nouveau-lts-utopic xserver-xorg-video-openchrome-lts-utopic xserver-xorg-video-r128-lts-utopic xserver-xorg-video-radeon-lts-utopic xserver-xorg-video-savage-lts-utopic xserver-xorg-video-siliconmotion-lts-utopic xserver-xorg-video-sisusb-lts-utopic xserver-xorg-video-tdfx-lts-utopic xserver-xorg-video-trident-lts-utopic xserver-xorg-video-vesa-lts-utopic xserver-xorg-video-vmware-lts-utopic xterm xul-ext-ubufox yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity-common zip 

```
The package list may vary with later updates but hopefully can serve as a base. I'm not sure if bind9 package is installed out of the box on Ubuntu Server (I had it installed but the server was not a fresh install), you can add it to the list if needed.
> **vijayan2 said:**
> Also, the system will freeze when restarting ubuntu. I followed the info provided at the following link:

[http://michalorman.com/2013/10/fix-ubuntu-freeze-during-restart/](http://michalorman.com/2013/10/fix-ubuntu-freeze-during-restart/)
The link suggests adding "reboot=pci" but "reboot=efi" worked better for me as it doesn't switch the system off for half a minute during reboot.

---

