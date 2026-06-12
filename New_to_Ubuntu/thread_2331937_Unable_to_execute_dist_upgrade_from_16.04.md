---
title: "Unable to execute dist upgrade from 16.04"
date: 2016-07-27
forum: New to Ubuntu
---

### Post by nisarg1184 on 2016-07-27
Hi

I have upgraded my machine to 16.04 from 15.10 and it was successful. However, I am unable to execute dist-upgrade or upgrade from my machine and it results in following error:

**sudo apt-get update && time sudo apt-get dist-upgrade **gives following output:  

```
Ign:1 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 InRelease                                                                              
Hit:2 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 Release                                                                                
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                               
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                                                         
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                                                          
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]                                         
Hit:10 [http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu](http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu) xenial InRelease
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]
Hit:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
Fetched 190 kB in 4s (41.9 kB/s)
Reading package lists... Done
W: [http://www.scootersoftware.com/dists/bcompare4/Release.gpg:](http://www.scootersoftware.com/dists/bcompare4/Release.gpg:) Signature by key C9467A8216C570CDFBAC3AFD331D6DDE7F8840CE uses weak digest algorithm (SHA1)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  checkbox-ng gstreamer1.0-clutter libasm3-java libbind9-90 libcamel-1.2-52 libclamav6 libcolamd2.8.0 libdns100 libebook-contacts-1.2-1 libecal-1.2-18
  libedata-cal-1.2-27 libedataserver-1.2-20 libglew1.10 libglewmx1.10 libgps21 libgtop2-10 libimobiledevice4 libisc95 libisccc90 libisccfg90 libisl13
  libjackrabbit-java libjna-java libjna-jni libjna-platform-java libjs-prototype libjs-scriptaculous libjsch-agent-proxy-java libkf5activities5
  libkf5calendarevents5 libkf5plasmaquick5 libllvm3.5v5 liblouis2 liblwres90 libmaven-scm-java libmono-web4.0-cil libpoppler52 libpth20 libqpdf13v5
  libqt5extserialport1 libquazip-qt5-1 libraw10 libsisu-guice-java libusbmuxd2 libwlocate0 libx264-146 libx265-59 libxcb-composite0 libxcb-damage0
  plasma-framework python-characteristic python3-cffi python3-checkbox-ng python3-ply python3-pycparser qml-module-org-kde-kquickcontrols
  qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-people qml-module-qtquick-controls qml-module-qtquick-dialogs qml-module-qtquick-localstorage
  qml-module-qtquick-privatewidgets qtdeclarative5-localstorage-plugin telepathy-indicator unity-scope-audacious unity-scope-clementine
  unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque unity-scope-musique
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  checkbox-ng-service gnome-control-center-shared-data libcdr-0.1-1v5 libcheese-gtk23 libcheese7 libgnome-desktop-3-10 libhunspell-1.3-0v5
  libmarblewidget-qt5-22 libmetacity-private3 libmono-corlib4.0-cil libmwaw-0.3-3v5 libodfgen-0.1-1v5 libplank0 libpresage1 libpython3.4
  libpython3.4-minimal libpython3.4-stdlib libvoikko1v5 openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless python3.4 python3.4-minimal tzdata-java
  unity-scope-musicstores xserver-xorg-input-mouse
The following NEW packages will be installed
  a11y-profile-manager-indicator appstream autotools-dev ca-certificates-mono checkbox-converged default-jre-headless dh-strip-nondeterminism dirmngr
  distro-info-data efibootmgr fonts-lato fonts-noto-cjk fonts-symbola fonts-tlwg-garuda-ttf fonts-tlwg-kinnari-ttf fonts-tlwg-laksaman-ttf
  fonts-tlwg-loma-ttf fonts-tlwg-mono-ttf fonts-tlwg-norasi-ttf fonts-tlwg-purisa-ttf fonts-tlwg-sawasdee-ttf fonts-tlwg-typewriter-ttf
  fonts-tlwg-typist-ttf fonts-tlwg-typo-ttf fonts-tlwg-umpush-ttf fonts-tlwg-waree-ttf fwupd fwupdate fwupdate-signed gcc-6-base
  gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 gnome-calendar gnome-software gnome-software-common gnupg2 gstreamer1.0-clutter-3.0 iio-sensor-proxy
  imagemagick imagemagick-6.q16 imagemagick-common initramfs-tools-core ktexteditor-data ktexteditor-katepart liba11y-profile-manager-0.1-0
  liba11y-profile-manager-data libao-common libao4 libappstream-glib8 libappstream3 libbind9-140 libcamel-1.2-54 libcdr-0.1-1 libcglib-java libcheese-gtk25
  libcheese8 libclamav7 libcolamd2.9.1 libcommons-lang3-java libcommons-net-java libdata-alias-perl libdfu1 libdns-export162 libdns162
  libebook-contacts-1.2-2 libecal-1.2-19 libedata-cal-1.2-28 libedataserver-1.2-21 libefivar0 libfftw3-double3 libfile-stripnondeterminism-perl
  libfilezilla0 libfwup0 libfwupd1 libgcab-1.0-0 libgeonames0 libgif7 libglew1.13 libglewmx1.13 libgnome-desktop-3-12 libgps22 libgtkspell3-3-0
  libgtop-2.0-10 libilmbase12 libimobiledevice6 libisc-export160 libisc160 libisccc140 libisccfg140 libisl15 libjavascriptcoregtk-4.0-18
  libkf5calendarevents5 libkf5gpgmepp5 libkf5service-bin libkf5texteditor5 libkf5texteditor5-libjs-underscore libksba8 libllvm3.8 liblouis9
  liblouisutdml-bin liblouisutdml-data liblouisutdml6 liblqr-1-0 liblvm2app2.2 liblwres141 libmagickcore-6.q16-2 libmagickcore-6.q16-2-extra
  libmagickwand-6.q16-2 libmarblewidget-qt5-23 libmetacity-private3a libmono-accessibility4.0-cil libmono-ldap4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil libmono-system-design4.0-cil libmono-system-ldap4.0-cil libmono-system-numerics4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-servicemodel-internals0.0-cil libmono-system-windows-forms4.0-cil libmono-webbrowser4.0-cil
  libmwaw-0.3-3 libnetpbm10 libnma-common libnma0 libnpth0 libodfgen-0.1-1 libopenexr22 libpeas-1.0-0-python3loader libplank1
  libplexus-component-annotations-java libplexus-component-metadata-java libplexus-container-default1.5-java libpoppler58 libpresage1v5 libprocps4
  libqdox2-java libqpdf17 libraw15 libreoffice-style-breeze libsnappy1v5 libsuitesparseconfig4.4.6 libusbmuxd4 libvoikko1 libvpx3 libwebkit2gtk-4.0-37
  libwebkit2gtk-4.0-37-gtk2 libx264-148 libx265-79 libxapian-1.3-5 libxtables11 libyaml-libyaml-perl linux-base mesa-vdpau-drivers netpbm
  openjdk-8-jre-headless overlay-scrollbar-gtk2 pyotherside python-attr python-ptyprocess python3-guacamole python3-padme python3-ptyprocess python3-systemd
  python3-xapian1.3 qml-module-io-thp-pyotherside qmlscene qtdeclarative5-dev-tools qtdeclarative5-test-plugin ruby2.3 sbsigntool secureboot-db
  session-shortcuts snapd squashfs-tools ubuntu-core-launcher ubuntu-software ubuntu-wallpapers-xenial unity-accessibility-profiles
  unity-control-center-faces vdpau-driver-all xserver-xorg-video-amdgpu
The following packages will be upgraded:
  account-plugin-aim account-plugin-jabber account-plugin-salut account-plugin-yahoo alsa-utils apport apt-transport-https apt-xapian-index apturl
  apturl-common baloo-kf5 bamfdaemon base-files bash bash-completion bind9-host binutils bluez-obexd checkbox-gui checkbox-ng cheese cheese-common clamav
  clamav-base clamav-freshclam command-not-found command-not-found-data compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  compiz-plugins-extra compizconfig-settings-manager console-setup console-setup-linux cpp cpp-5 cups-browsed cups-filters cups-filters-core-drivers
  debhelper dnsutils dolphin dolphin-plugins empathy empathy-common eog evolution-data-server evolution-data-server-common
  evolution-data-server-online-accounts fcitx-modules filezilla filezilla-common findutils folks-common fonts-tlwg-garuda fonts-tlwg-kinnari
  fonts-tlwg-laksaman fonts-tlwg-loma fonts-tlwg-mono fonts-tlwg-norasi fonts-tlwg-purisa fonts-tlwg-sawasdee fonts-tlwg-typewriter fonts-tlwg-typist
  fonts-tlwg-typo fonts-tlwg-umpush fonts-tlwg-waree fuse g++ g++-5 gcc gcc-5 gcc-5-base gdb gdbserver gedit gedit-common gir1.2-gmenu-3.0
  gir1.2-gnomedesktop-3.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-3.0 gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-unity-5.0 gnome-contacts
  gnome-font-viewer gnome-menus gnome-screensaver gnome-session-bin gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-system-monitor gnupg-agent google-chrome-stable grub-common grub-pc grub-pc-bin grub2-common gstreamer1.0-alsa gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good gstreamer1.0-pulseaudio gstreamer1.0-tools gstreamer1.0-x gtk2-engines-murrine gvfs gvfs-backends
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hplip hplip-data ifupdown indicator-appmenu indicator-datetime indicator-keyboard initramfs-tools
  initramfs-tools-bin initscripts iproute2 iptables isc-dhcp-client isc-dhcp-common kde-config-telepathy-accounts kde-telepathy-approver
  kde-telepathy-contact-list kde-telepathy-desktop-applets kde-telepathy-text-ui kde-thumbnailer-deb keyboard-configuration kinit kio klibc-utils
  language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base libasan2 libastro1 libatomic1 libavcodec-ffmpeg56 libbamf3-2
  libboost-date-time1.58.0 libboost-filesystem1.58.0 libboost-iostreams1.58.0 libboost-system1.58.0 libcc1-0 libcilkrts5 libcompizconfig0
  libdbus-glib2.0-cil libdbus2.0-cil libdecoration0 libebackend-1.2-10 libebook-1.2-16 libedata-book-1.2-25 libedataserverui-1.2-1 libegl1-mesa
  libfolks-eds25 libfolks-telepathy25 libfolks25 libfuse2 libgail-3-0 libgcc-5-dev libgcc1 libgd3 libgdiplus libgksu2-0 libgl1-mesa-dri libglib2.0-cil
  libgnome-menu-3-0 libgnutls-openssl27 libgnutls30 libgomp1 libgpgme11 libgpod-common libgpod4 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-cil libhpmud0 libhunspell-1.3-0 libitm1 libkf5baloo5
  libkf5balooengine5 libkf5emoticons-data libkf5emoticons5 libkf5kcmutils-data libkf5kcmutils5 libkf5kdelibs4support-data libkf5kdelibs4support5
  libkf5kiocore5 libkf5kiowidgets5 libkf5newstuff-data libkf5newstuff5 libkf5parts-data libkf5parts5 libkf5people-data libkf5people5 libkf5peoplebackend5
  libkf5peoplewidgets5 libkf5plasma5 libkf5plasmaquick5 libkf5runner5 libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5webkit5 libklibc libktpcommoninternals9 libktplogger9 libktpwidgets9
  libkwalletbackend5-5 liblightdm-gobject-1-0 liblsan0 libmaven3-core-java libmono-addins0.2-cil libmono-cairo4.0-cil libmono-corlib4.5-cil
  libmono-data-tds4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-sqlite4.0-cil libmono-system-configuration4.0-cil libmono-system-core4.0-cil libmono-system-data4.0-cil libmono-system-drawing4.0-cil
  libmono-system-enterpriseservices4.0-cil libmono-system-runtime-serialization-formatters-soap4.0-cil libmono-system-security4.0-cil
  libmono-system-transactions4.0-cil libmono-system-web-applicationservices4.0-cil libmono-system-web-services4.0-cil libmono-system-web4.0-cil
  libmono-system-xml-linq4.0-cil libmono-system-xml4.0-cil libmono-system4.0-cil libmpx0 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2
  libnm0 libnotify0.4-cil libnux-4.0-0 libnux-4.0-common libpam-systemd libplank-common libplexus-containers1.5-java libpoppler-glib8 libpoppler-qt5-1
  libpresage-data libpython2.7 libpython2.7-minimal libpython2.7-stdlib libpython3-stdlib libqapt3 libqapt3-runtime libquadmath0
  libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport libreoffice-style-galaxy
  libreoffice-style-human libreoffice-style-sifr libreoffice-writer librhythmbox-core9 libsane-hpaio libsisu-guice-java libstdc++-5-dev libstdc++6
  libsystemd0 libtotem0 libtsan0 libubsan0 libudev1 libunity-control-center1 libunity-core-6.0-9 libunity-protocol-private0 libunity-scopes-json-def-desktop
  libunity-settings-daemon1 libunity9 libupower-glib3 libvdpau1 libwagon2-java libwayland-egl1-mesa libwhoopsie0 libwnck-common libwnck22 libxatracker2
  libyelp0 light-themes lightdm lintian linux-firmware lp-solve lsb-base lsb-release lshw lvm2 marble marble-plugins maven mcp-account-manager-uoa
  metacity-common mono-4.0-gac mono-gac mono-runtime mono-runtime-common mono-runtime-sgen nautilus nautilus-data network-manager network-manager-gnome
  network-manager-pptp network-manager-pptp-gnome nodejs nodejs-dev nux-tools onboard plainbox-provider-checkbox plainbox-secure-policy plank
  plasma-framework poppler-utils ppp presage printer-driver-brlaser printer-driver-hpcups printer-driver-postscript-hp procps python-apt python-compizconfig
  python-pexpect python-service-identity python-software-properties python2.7 python2.7-minimal python3 python3-apt python3-brlapi python3-cairo
  python3-cffi python3-cffi-backend python3-checkbox-ng python3-commandnotfound python3-cryptography python3-cups python3-dbus python3-gdbm python3-gi
  python3-gi-cairo python3-louis python3-lxml python3-markupsafe python3-minimal python3-pexpect python3-pil python3-plainbox python3-pycurl
  python3-renderpm python3-reportlab python3-reportlab-accel python3-smbc python3-software-properties python3-uno qml-module-org-kde-telepathy qpdf
  rhythmbox rhythmbox-data rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins ruby seahorse shotwell
  shotwell-common software-center software-properties-common software-properties-gtk sonnet-plugins speech-dispatcher speech-dispatcher-audio-plugins
  suru-icon-theme systemd systemd-sysv totem totem-common totem-plugins ttf-ancient-fonts-symbola tzdata ubuntu-artwork ubuntu-desktop ubuntu-docs
  ubuntu-mobile-icons ubuntu-mono ubuntu-session ubuntu-wallpapers udev unity unity-control-center unity-lens-applications unity-lens-music unity-schemas
  unity-scopes-runner unity-services unity-settings-daemon update-notifier update-notifier-common upower usbmuxd whoopsie xorg xserver-xorg
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware yelp zenity zenity-common
472 to upgrade, 181 to newly install, 26 to remove and 0 not to upgrade.
Need to get 736 kB/529 MB of archives.
After this operation, 412 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 bash amd64 4.3-14ubuntu1.1                                                                  
  Connection failed
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 bash-completion all 1:2.1-4.2ubuntu1.1
  Connection failed
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 bash-completion all 1:2.1-4.2ubuntu1.1
  Connection failed
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bash/bash_4.3-14ubuntu1.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bash/bash_4.3-14ubuntu1.1_amd64.deb) Connection failed


E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bash-completion/bash-completion_2.1-4.2ubuntu1.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bash-completion/bash-completion_2.1-4.2ubuntu1.1_all.deb) Connection failed


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```


real    10m3.656s
user    0m0.928s
sys    0m0.120s

---

### Post by nisarg1184 on 2016-07-27
I even tried **--fix-missing **and that too results in the same error!

**sudo apt-get update **works absolutely fine though...

---

### Post by cariboo on 2016-07-27
Try a different miror. Go to System Settings->Software & Updates and change Download from.

---

### Post by gordintoronto on 2016-07-27
16.04 is the current version, so there is no available dist upgrade.

Did you run the autoremove? You might also want to: sudo apt-get clean

And how many kernels do you have installed?

---

### Post by nikefalcon on 2016-07-29
If none of the above woks then delete everything from **/var/lib/apt/lists/ **and **/var/lib/apt/lists/partial**, do  **apt-get update** and try again.

> **gordintoronto said:**
> 16.04 is the current version, so there is no available dist upgrade.
**apt-get dist upgrade **is not the same as getting a new release(**do-release-upgrade**); it is possible to run a dist upgrade on a slightly dated 16.04 system like mine.

---

### Post by deadflowr on 2016-07-29
Hmm, what was the method used to upgrade from 15.10 to 16.04?
Because all of the clean up should have been done at that time, and not post upgrade.

---

### Post by tsjswimmer on 2016-08-14
Maybe Canonical's servers are having issues. I would wait a few days and try again. Or, as Cariboo has suggested, you can try using software-properties-gtk or software-properties-kde to switch mirrors.

---

