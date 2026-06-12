---
title: "how to uninstall kde. would having both kde and gnome cause slowdown and freezing?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-15
i originally installed kubuntu, had some issues with it and now i realized that its just not for me, although i love the way it looks. Im pretty used to GNOME, and I installed it and everything works for me better. 

so how would i uninstall kde? would it cause any errors? is having two desktop environments bad? it seems like when using gnome, things slow down a bit and things freeze and error and i think its because of the programs using all those dependancies or something? I dont know. All I know is that when I had ubuntu installed with a wubi partition almost everything worked immediately with out any hassle, and now that I have an actual partition for it ive really had to work at everything.

hopefully i dont have to uninstall everything and start over, but if i have to i will.

---

### Post by t0p on 2008-08-15
There's no reason to uninstall kde (or kubuntu-desktop, as it's known in the ubuntu world).  Having both kde and gnome installed isn't going to cause any problems - after all, you're not very likely to run both at the same time!!

I've got gnome, kde *and* xfce on my computer.  And you can have more if you want!  I'm thinking of installing fluxbox... :)

**EDIT:** I just noticed you said something about having an actual partition for gnome.  Do you mean hyou installed kubuntu on 1 partition, and ubuntu on another?  If so, you might want to reformat the kubuntu partition, just to free up some disk space.

---

### Post by Paqman on 2008-08-15
> **WinterMadness said:**
> 
so how would i uninstall kde?

By plugging this command into a terminal:
```

sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop

```

---

### Post by WinterMadness on 2008-08-15
> **t0p said:**
> There's no reason to uninstall kde (or kubuntu-desktop, as it's known in the ubuntu world).  Having both kde and gnome installed isn't going to cause any problems - after all, you're not very likely to run both at the same time!!

I've got gnome, kde *and* xfce on my computer.  And you can have more if you want!  I'm thinking of installing fluxbox... :)

**EDIT:** I just noticed you said something about having an actual partition for gnome.  Do you mean hyou installed kubuntu on 1 partition, and ubuntu on another?  If so, you might want to reformat the kubuntu partition, just to free up some disk space.



i made a kubuntu partition and downloaded the gnome desktop through the terminal. only one partition for linux

---

### Post by LowSky on 2008-08-15
```
sudo apt-get remove kubuntu-desktop*
```
dont forget the "*"

that should take care of everything

---

### Post by Paqman on 2008-08-15
> **LowSky said:**
> ```
sudo apt-get remove kubuntu-desktop*
```
dont forget the "*"

that should take care of everything

Removing kubuntu-desktop with apt-get won't remove the dependencies though. It's just a meta-package.

---

### Post by xXZeroXx on 2008-08-15
> **Paqman said:**
> By plugging this command into a terminal:
```

sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop

```
Thanks man, you really helped me, I had a lot of garbage in my menu.

---

