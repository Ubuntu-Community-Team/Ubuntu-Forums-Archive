---
title: "kubuntu uninstall?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by bmann11 on 2008-04-25
I've been running 7.10 for a couple weeks and digging it.  I installed kubuntu overtop of ubuntu to check it out but am now sufficiently satisfied to stick with gnome.

How do I uninstall kubuntu?

Thanks.

---

### Post by sam_delta on 2008-04-25
try 

```
sudo apt-get remove kubuntu-desktop
```

---

### Post by bmann11 on 2008-04-25
didn't work, any other ideas

---

### Post by sam_delta on 2008-04-25
found it at 
[http://www.psychocats.net/ubuntu/puregnomegutsy](http://www.psychocats.net/ubuntu/puregnomegutsy)

NOTE: this command will remove any kde related programs installed during installation of kubuntu desktop,please review the packages so, you do not delete something you want to keep

in ubuntu 7.10 gutsy type:

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop
```

heres another link pointed at the same/very similar solution
[http://ubuntuforums.org/showthread.php?t=96048](http://ubuntuforums.org/showthread.php?t=96048)

tell us how it goes

sam

---

### Post by Paqman on 2008-04-25
> **sam_delta said:**
> try 

```
sudo apt-get remove kubuntu-desktop
```

kubuntu-desktop is a meta-package (just like it's ubuntu and xubuntu friends). That means it doesn't contain any actual software. It's just a list of dependencies. The idea is that if you  install the desktop package, it pulls in all the required components for that DE.

Hence, removing it does nothing.

---

### Post by sam_delta on 2008-04-25
> **Paqman said:**
> kubuntu-desktop is a meta-package (just like it's ubuntu and xubuntu friends). That means it doesn't contain any actual software. It's just a list of dependencies. The idea is that if you  install the desktop package, it pulls in all the required components for that DE.

Hence, removing it does nothing.

yeah, thanks for the info, i just putted a command which removes all the components of kde above.

thanks again for pointing into the right direction

sam

---

### Post by bmann11 on 2008-04-25
so how do I get kubuntu to go away?

When I start up I see kubuntu instead of ubuntu, but then it usually opens of ubuntu.  

Now it seems like I have an older kubuntu firefox browser, my file folders have mysterioulsy changed and a few tool bar buttons seem a bit different as well.

Is there a way to get back to before I tried out kubunto?  Thanks

---

### Post by Paqman on 2008-04-25
> **bmann11 said:**
> 
When I start up I see kubuntu instead of ubuntu, but then it usually opens of ubuntu.  

You mean it says Kubuntu on the splash screen it shows while booting? But then when you log in it goes to a Gnome desktop? That's just a matter of changing the splash screen.

[Click to install gnome-splashscreen-manager](apt:gnome-splashscreen-manager), which will let you put anything you want up there.

---

### Post by bmann11 on 2008-04-25
just rebooted and hit the select session under options on the login screen.  Clicked on gnome and I'm back to my original desktop.

Is there even a point to 'deactivating kubuntu'?

---

### Post by Paqman on 2008-04-25
> **bmann11 said:**
> 
Is there even a point to 'deactivating kubuntu'?

Not really. It frees up some space on your drive, I guess.

---

### Post by bmann11 on 2008-04-25
Yes, it shows kubuntu on the splash screen while booting.  But firefox also opens up to a kubuntu page when I open FF up, so I assume there is still some residual kubuntu stuff going on.

I installed splash screen manager, but there's nothing I can click on within that program.

Thanks.

---

### Post by bmann11 on 2008-04-25
Yes, it shows kubuntu on the splash screen while booting.  But firefox also opens up to a kubuntu page when I open FF up, so I assume there is still some residual kubuntu stuff going on.

I installed splash screen manager, but there's nothing I can click on within that program.

Thanks.

---

