---
title: "HELP! I've done something, and it came out horribly wrong!"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by valke on 2008-05-09
Hi all, last night, I wanted to try KDE, so I used this command in terminal:

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

But when I was done trying it out I wanted to get back to a pure Gnome, so I used this command:

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
```

Which can be found here: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

However, now I cannot apt-get or aptitude, or even run Update Manager. Update Manager told me "Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first." So I did, and this is what happens:

```
downdrift@dell-desktop:~$ sudo apt-get install -f
[sudo] password for downdrift: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libwildmidi0 libdc1394-13 libxvidcore4 network-manager-pptp
  libsoundtouch1c2 mplayer-skins vcdimager libwxgtk2.6-0 libsvga1 ttf-dustin
  libjack0 python-pyxattr libopenspc0 libapr1 python-pyogg mysql-common
  pinentry-curses libdvbpsi4 pptp-linux libxosd2 libmysqlclient15off procmail
  python-pyvorbis libx264-57 libvlc0 network-manager-vpnc libenca0
  python-mutagen libggi2 python-cddb libmikmod2 libgii1 libwxbase2.6-0 ocrad
  videolan-doc libgii1-target-x libdvdnav4 vpnc libiso9660-5 libcdaudio1
  python-pylibacl libsidplay1 zoo mpg123 libid3tag0 pmount libgmyth0
  resolvconf libtar openvpn python-eyed3 libvcdinfo0 libebml0 libmatroska0
  network-manager-openvpn libmpeg2-4 libmms0 libiptcdata0 gtk2-engines-qtcurve
  libfaac0 libfaad0 liba52-0.7.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131644 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tacutu on 2008-05-09
yes, there is some sort of weird dependency with kio-umountwrapper. Install dolphin, remove kio-umountwrapper and then remove dolphin again. Should work.

edit: rereading your post... oh... you can't install anything, can you... bummer!
edit 2: here, try this: [http://ubuntuforums.org/showpost.php?p=4786808&postcount=3](http://ubuntuforums.org/showpost.php?p=4786808&postcount=3)

---

### Post by valke on 2008-05-09
thanks a million! That other thread seemed to work!

---

### Post by jpmorelli on 2008-06-03
Work&#347; like a charm, thanks a lot !!! :KS

---

