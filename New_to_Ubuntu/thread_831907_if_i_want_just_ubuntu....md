---
title: "if i want just ubuntu..."
date: 2008-06-17
forum: New to Ubuntu
---

### Post by XTR0RDiNAiRE on 2008-06-17
if i want to restore ubuntu back to zero
how do i do that, 

or lets say i have kubuntu and i just want to go back to ubuntu

---

### Post by ukripper on 2008-06-17
> **XTR0RDiNAiRE said:**
> if i want to restore ubuntu back to zero
how do i do that, 

or lets say i have kubuntu and i just want to go back to ubuntu

In terminal:
```
sudo apt-get install ubuntu-desktop
```

this will install gnome for you and you can logoff and select at login screen.

---

### Post by Daedal Dementia on 2008-06-17
boot nuke your drive.

put in your ubuntu CD

---

### Post by XTR0RDiNAiRE on 2008-06-17
> **ukripper said:**
> In terminal:
```
sudo apt-get install ubuntu-desktop
```

this will install gnome for you and you can logoff and select at login screen.

i did that and it still has kubuntu log in options

---

### Post by XTR0RDiNAiRE on 2008-06-17
> **Daedal Dementia said:**
> boot nuke your drive.

put in your ubuntu CD

what is that?
how do i boot nuke a drive

---

### Post by ukripper on 2008-06-17
> **XTR0RDiNAiRE said:**
> i did that and it still has kubuntu log in options

logout and then

at login prompt select > options-->select session-->gnome

---

### Post by _sphinx_ on 2008-06-17
Actually I have use kubuntu but I think you should get gnome session under session menu at the time of login.

---

### Post by XTR0RDiNAiRE on 2008-06-17
im tryin to just have ubuntu, cause i have a feeling that 
its the reason im having problems
with compiz and all that stuff
i still havent been able to launch awn
it says composite extension not available

---

### Post by Captain_Riker on 2008-06-17
Hello,

The simplest way of "getting back":

Wipe your HDD, and reinstall a fresh Ubuntu from an ubuntu install media.

I'd suggest to simply boot from an ubuntu install media and reinstall. If you still have your Data on the HDD, i hope it's on another patition. So just re-format the partitions for /boot (if seperate) and "/". And then add your existing "data" partition to your fstab(as far as I re,eber this can also be done with the installer, just give it a mountpoint). Just take care that only "/" (and /boot) will be formatted.

Otherwise you'd have to install and remove tons of packages. And afterwards you'll never be sure weather there is still "some KDE around" or not. ;-)

---

### Post by ChameleonDave on 2008-06-17
> **XTR0RDiNAiRE said:**
> if i want to restore ubuntu back to zero
how do i do that, 

or lets say i have kubuntu and i just want to go back to ubuntu

In other words, you want to use GNOME rather than KDE.

Install GNOME (the ubuntu-desktop package) and make it your default.

Deleting KDE is trickier, because it is a collection of hundreds of packages, and some of them may still be of use to you.  Just delete the packages on a case-by-case basis.  For example, if you prefer to use Brasero rather than K3B for burning CDs, then delete K3B.

Or, yes, you could reinstall the operating system from scratch.

---

### Post by Troll_the_Great on 2008-06-17
If you want to go back to "pure gnome" use this command:

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
```

This will remove all the components of Kubuntu.See this link for further help:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ChameleonDave on 2008-06-17
> **Troll_the_Great said:**
> If you want to go back to "pure gnome" use this command:

Except that that will remove a lot of useful programs like K3B and vorbis-tools, which he might want to keep even if he uses GNOME.

---

### Post by Duck2006 on 2008-06-17
> **ChameleonDave said:**
> Except that that will remove a lot of useful programs like K3B and vorbis-tools, which he might want to keep even if he uses GNOME.

You can reinstall them from your Synaptic Package Manager, or Add/Remove.

---

### Post by MasterSander on 2008-06-17
Or remove them from the command line. If he would want to amarok he'd just remove amarok-xine from 
```
 sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop 
```

---

