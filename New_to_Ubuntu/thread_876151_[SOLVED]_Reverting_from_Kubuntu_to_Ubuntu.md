---
title: "[SOLVED] Reverting from Kubuntu to Ubuntu"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by ILessThan3Sarah on 2008-07-31
I installed Kubuntu over Ubuntu a few days back... I've had a chance to try it out, and I've decided that i prefer Ubuntu.  Is there an easy way to do this, or do I have to format the entire partition, and do a clean install? 
thanks.

---

### Post by LittleLORDevil on 2008-07-31
I believe you can change your desktop manager from Kubuntu to GNOME through the package manager.  Then remove the KDE dependent software as well. I am no expert so maybe someone can continue and buff up my post.

---

### Post by sisco311 on 2008-07-31
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by LowSky on 2008-07-31
```
sudo aptitude remove kubuntu-desktop
```
or
```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
```

---

### Post by candtalan on 2008-07-31
there is no need to uninstall kubuntu or whatever to change to another desktop such as ubuntu.

if you currently have kubuntu, then you can use adept package manager, or synaptic package manager, or the command line such as apt-get install, to install the ubuntu. this is done simply by installing the package
ubuntu-desktop
using, say, adept or whatever means.

the kubuntu you currently use is in fact from a package called
kubuntu-desktop
and if you had started with ubuntu you could have installed that package to get kubuntu.

please note:
after the package installation/s, when you log in, you then choose which 'session' to use, either gnome (ubuntu) or kde (kubuntu)

simple as that.

the login screen will probably look like kubuntu in your case, this is the 'log in manager' and can be changed by other means.

if you have both packages installed, kubuntu-desktop and ubuntu-dektop, then you can uninstall the one you are not using, easily, using the same facilities as mentioned above.

incidentally, the xubuntu-desktop is also available and is favoured for low resource machines. 

If you have the disk space, you can keep all three installed and use them as choices when you log in.

hth

---

