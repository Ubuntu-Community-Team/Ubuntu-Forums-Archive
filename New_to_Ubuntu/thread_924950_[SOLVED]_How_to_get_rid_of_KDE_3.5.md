---
title: "[SOLVED] How to get rid of KDE 3.5"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-20
Hi, all:

I have KDE 4.1.1.  I also have KDE 3.5 on my system; I seem to have it installed accidentally.  I think that the combination of both is slowing my system down.  How can I get rid of 3.5 and still keep 4.1.1?  I posted to another thread here on the forums, and the OP recommended that I start a new thread for this particular topic.  What do you all think?  CAN I get rid of 3.5?

---

### Post by doorknob60 on 2008-09-20
In Hardy:
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools
```

Put that command in a terminal: Kmenu > Applications > System > Terminal (Konsole)

Note that it will remove everything KDE3 related, possibly stuff you don't want removed. You can either adjust the command or just reinstall the stuff later.

---

### Post by tarahmarie on 2008-09-22
I'm having another issue with kio that I think may be related to this.  Why do I still have 3.5.9 stuff on my machine?  How do I get rid of it?  Here's some sample output:

~ : Yes, Supreme Empress? $ locate 3.5.9
/var/cache/apt/archives/kate_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/kcontrol_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/kdebase-bin-kde3_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/kdebase-bin_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/kdebase-data_4%3a3.5.9-0ubuntu7.3_all.deb
/var/cache/apt/archives/kdebase-kio-plugins_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/kdesktop_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/khelpcenter_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/kicker_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/konsole_4%3a3.5.9-0ubuntu7.3_i386.deb
/var/cache/apt/archives/libkjsembed1_4%3a3.5.9-0ubuntu1_i386.deb
/var/cache/apt/archives/libkonq4_4%3a3.5.9-0ubuntu7.3_i386.deb

There are background processes eating up my RAM.  I do NOT like this.

---

