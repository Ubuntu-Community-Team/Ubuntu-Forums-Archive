---
title: "Download all packages in the repos"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-12-01
Is there a way I can download all the packages from the Ubuntu repositories using Synaptic?  A terminal utility perhaps?

Thanks in advance!

---

### Post by jakupl on 2008-12-01
```
sudo apt-get install -d *
``` maybe? not sure, haven't tested it ;)

EDIT: It should work. A user called choipd on [this thread]("http://www.beijinglug.org/en/index.php?option=com_fireboard&Itemid=66&func=view&catid=3&id=&id=3452&catid=3&lang=zh") claims that apt-get can manage wildcards.

EDIT 2: Just for clarification. This command will not install the packages, only download. That's what the "d" flag does ;)

---

### Post by halitech on 2008-12-01
in theory yes but my question is why?

---

### Post by kdardio2415 on 2008-12-01
Why not?

---

### Post by halitech on 2008-12-01
cause its a crapload of stuff and most will probably not be used? why not just grab the dvd iso's and burn them and point apt at it?

---

### Post by kdardio2415 on 2008-12-01
You, sir, are the screen door on my submarine.

---

### Post by Kinetic Being on 2008-12-01
You wouldn't want to install them all at the same time, but you could download them if you wanted them for storage or something...

---

### Post by pi.boy.travis on 2008-12-01
> **jakupl said:**
> ```
sudo apt-get install -d *
``` maybe? not sure, haven't tested it ;)

EDIT: It should work. A user called choipd on [this thread]("http://www.beijinglug.org/en/index.php?option=com_fireboard&Itemid=66&func=view&catid=3&id=&id=3452&catid=3&lang=zh") claims that apt-get can manage wildcards.

EDIT 2: Just for clarification. This command will not install the packages, only download. That's what the "d" flag does ;)

Excellent!  Just what I was looking for!

Any way I can use this for, say. . . the entire Main repo?

EDIT: I am doing this so that I can have the repositories on DVD's.  I do LOTS of installations, and not all of the computers have an internet connection.  I will use APTonCD to burn the disk.

Thanks!

---

### Post by jakupl on 2008-12-01
Well... don't be too happy, I just simulated it using:

```
sudo apt-get install -ds *
```

(the "s" flag means simulate)

Somehow it wants to install packages with the name of every file in your current directory. This is what I got, "I have a directory in /home called andreas"

```
jakup@bobby:~$ sudo apt-get install -ds *
[sudo] password for jakup: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package andreas
jakup@bobby:~$ 

```

soooo... but there is probably an easier way to do it.

---

### Post by pi.boy.travis on 2008-12-01
```
travis@travis-laptop:~$ sudo apt-get install -d kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adept akregator amarok amarok-common amarok-engine-xine apport-qt ark
  dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent
  gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui
  ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data
  kaddressbook kamera kate kde-icons-oxygen kde-printer-applet
  kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins
  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data
  kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins
  kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons
  kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor
  khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror
  konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation
  kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog
  ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager
  language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libavahi-qt3-1
  libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2
  libexiv2-4 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4
  libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates
  libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4
  libmodplug0c2 libnjb5 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3
  libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant
  libqt4-core libqt4-help libqt4-opengl libqt4-test libqt4-webkit
  libqt4-xmlpatterns libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0
  libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0
  libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x libxvmc1 libzip1 mediamanager network-manager-kde okular
  okular-extra-backends openoffice.org-kde openoffice.org-style-crystal
  oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine
  pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3
  python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4
  raptor-utils redland-utils ruby ruby1.8 software-properties-kde
  soprano-daemon speedcrunch strigi-client strigi-daemon
  system-config-printer-kde systemsettings ttf-dustin update-manager-kde
  update-notifier-kde
Suggested packages:
  amarok-engines moodbar libqt0-ruby1.8 libvisual-0.4-plugins ncompress zoo
  p7zip-full k3b-i18n normalize-audio toolame sox movixmaker-2 vcdimager
  kdebase-kio-plugins kcontrol libk3b3-extracodecs transcode kdebase perl-suid
  egroupware procmail clamav f-prot-installer knewsticker kweather gnokii
  kitchensync knode libsoap-lite-perl kdeartwork-emoticons khelpcenter
  php5-cli ktorrent-dbg akonadi-server libarts1-akode geoip-bin
  libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqca2-plugin-pkcs11
  libvncserver0-dbg gxine xine-ui libxine1-doc libxine-doc libxine1-ffmpeg
  kde-icons-crystal crystalcursors phonon-backend-vlc phonon-backend-mplayer
  pinentry-doc python-kde4-dbg libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql
  python-qt3-doc python-qt3-gl python-qt4-dbg python-egenix-mxtexttools
  python-reportlab-doc ruby1.8-examples rdoc1.8 ri1.8 strigi-plugins
Recommended packages:
  python-renderpm
The following NEW packages will be installed:
  adept akregator amarok amarok-common amarok-engine-xine apport-qt ark
  dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent
  gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui
  ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data
  kaddressbook kamera kate kde-icons-oxygen kde-printer-applet
  kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins
  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data
  kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins
  kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons
  kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor
  khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror
  konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation
  kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog
  ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd
  kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0
  libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3
  libdbus-qt-1-1c2 libexiv2-4 libgeoip1 libifp4 libk3b3 libkcddb4
  libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4
  libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50
  liblualib50 libmimelib4 libmodplug0c2 libnjb5 libokularcore1 libphonon4
  libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl
  libqimageblitz4 libqt4-assistant libqt4-core libqt4-help libqt4-opengl
  libqt4-test libqt4-webkit libqt4-xmlpatterns libraptor1 librasqal0 librdf0
  libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0
  libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager
  network-manager-kde okular okular-extra-backends openoffice.org-kde
  openoffice.org-style-crystal oxygen-cursor-theme phonon
  phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4
  plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common
  python-qt4-dbus python-reportlab python-sip4 raptor-utils redland-utils ruby
  ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client
  strigi-daemon system-config-printer-kde systemsettings ttf-dustin
  update-manager-kde update-notifier-kde
0 upgraded, 195 newly installed, 0 to remove and 0 not upgraded.
Need to get 168MB of archives.
After this operation, 595MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

OK, so if I continue, all the packages in the meta-package kubuntu-desktop will be downloaded to my apt-cache, but not installed, correct?

---

### Post by starcannon on 2008-12-01
Unless your setting up a mirror... I see this to actually be possibly harmful. Keep in mind bandwidth costs somebody money... so "just because" is pretty callous I think...

[http://www.ubuntu.com/node/69](http://www.ubuntu.com/node/69)

Have fun and GL

---

### Post by halitech on 2008-12-01
looks to me like it will actually be installing them.
```
0 upgraded, 195 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by jakupl on 2008-12-01
> **pi.boy.travis said:**
> ```
travis@travis-laptop:~$ sudo apt-get install -d kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adept akregator amarok amarok-common amarok-engine-xine apport-qt ark
  dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent
  gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui
  ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data
  kaddressbook kamera kate kde-icons-oxygen kde-printer-applet
  kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins
  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data
  kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins
  kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons
  kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor
  khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror
  konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation
  kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog
  ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager
  language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libavahi-qt3-1
  libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2
  libexiv2-4 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4
  libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates
  libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4
  libmodplug0c2 libnjb5 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3
  libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant
  libqt4-core libqt4-help libqt4-opengl libqt4-test libqt4-webkit
  libqt4-xmlpatterns libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0
  libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0
  libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins
  libxine1-x libxvmc1 libzip1 mediamanager network-manager-kde okular
  okular-extra-backends openoffice.org-kde openoffice.org-style-crystal
  oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine
  pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3
  python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4
  raptor-utils redland-utils ruby ruby1.8 software-properties-kde
  soprano-daemon speedcrunch strigi-client strigi-daemon
  system-config-printer-kde systemsettings ttf-dustin update-manager-kde
  update-notifier-kde
Suggested packages:
  amarok-engines moodbar libqt0-ruby1.8 libvisual-0.4-plugins ncompress zoo
  p7zip-full k3b-i18n normalize-audio toolame sox movixmaker-2 vcdimager
  kdebase-kio-plugins kcontrol libk3b3-extracodecs transcode kdebase perl-suid
  egroupware procmail clamav f-prot-installer knewsticker kweather gnokii
  kitchensync knode libsoap-lite-perl kdeartwork-emoticons khelpcenter
  php5-cli ktorrent-dbg akonadi-server libarts1-akode geoip-bin
  libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqca2-plugin-pkcs11
  libvncserver0-dbg gxine xine-ui libxine1-doc libxine-doc libxine1-ffmpeg
  kde-icons-crystal crystalcursors phonon-backend-vlc phonon-backend-mplayer
  pinentry-doc python-kde4-dbg libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql
  python-qt3-doc python-qt3-gl python-qt4-dbg python-egenix-mxtexttools
  python-reportlab-doc ruby1.8-examples rdoc1.8 ri1.8 strigi-plugins
Recommended packages:
  python-renderpm
The following NEW packages will be installed:
  adept akregator amarok amarok-common amarok-engine-xine apport-qt ark
  dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent
  gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui
  ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data
  kaddressbook kamera kate kde-icons-oxygen kde-printer-applet
  kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins
  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data
  kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins
  kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons
  kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor
  khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror
  konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation
  kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog
  ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings
  kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd
  kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0
  libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3
  libdbus-qt-1-1c2 libexiv2-4 libgeoip1 libifp4 libk3b3 libkcddb4
  libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4
  libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50
  liblualib50 libmimelib4 libmodplug0c2 libnjb5 libokularcore1 libphonon4
  libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl
  libqimageblitz4 libqt4-assistant libqt4-core libqt4-help libqt4-opengl
  libqt4-test libqt4-webkit libqt4-xmlpatterns libraptor1 librasqal0 librdf0
  libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0
  libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager
  network-manager-kde okular okular-extra-backends openoffice.org-kde
  openoffice.org-style-crystal oxygen-cursor-theme phonon
  phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4
  plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common
  python-qt4-dbus python-reportlab python-sip4 raptor-utils redland-utils ruby
  ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client
  strigi-daemon system-config-printer-kde systemsettings ttf-dustin
  update-manager-kde update-notifier-kde
0 upgraded, 195 newly installed, 0 to remove and 0 not upgraded.
Need to get 168MB of archives.
After this operation, 595MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

OK, so if I continue, all the packages in the meta-package kubuntu-desktop will be downloaded to my apt-cache, but not installed, correct?

correct. Have fun.

EDIT: WAIT.... noo., could this be the simulation option that's playing with us?

---

### Post by pi.boy.travis on 2008-12-01
> **starcannon said:**
> Unless your setting up a mirror... I see this to actually be possibly harmful. Keep in mind bandwidth costs somebody money... so "just because" is pretty callous I think...

[http://www.ubuntu.com/node/69](http://www.ubuntu.com/node/69)

Have fun and GL

I have a cable connection, so bandwidth is no object!

Just wanted to confirm.  I don't want to accidentally install all of those packages!

EDIT: I though that this would work:
```
travis@travis-laptop:~$ sudo apt-cache add ubuntu-desktop
E: Unimplemented

```

but no avail. . .

---

### Post by karlr42 on 2008-12-01
The server you're downloading from will suffer.

---

### Post by starcannon on 2008-12-01
> **pi.boy.travis said:**
> I have a cable connection, so bandwidth is no object!

Just wanted to confirm.  I don't want to accidentally install all of those packages!

EDIT: I though that this would work:
```
travis@travis-laptop:~$ sudo apt-cache add ubuntu-desktop
E: Unimplemented

```but no avail. . .
I'm not concerned with your bandwidth; my concern would be the bandwidth of the person or organization kind enough to donate the bandwidth for the mirror you'll be grabbing from.

GL and have fun

---

### Post by pi.boy.travis on 2008-12-01
OK, 

suco apt-get install -d

doesn't work for packages I already have installed. . . 

Something with apt-cache maybe?

---

### Post by cariboo on 2008-12-01
If you want to download all of the repositories without messing up your installation (which it will) use apt-mirror and create your own mirror of the repositories. Apt-mirror is in the repositories.

Jim

---

### Post by mc4man on 2008-12-01
You could read thru here

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

---

### Post by pi.boy.travis on 2008-12-01
OK, so the repos are WAY bigger than I (naively) thought. . . 

So what I need now is a way to download packages from the repos into my apt-cache.

apt-cache add

gave me:

E:Unimplemented

any other way to go about doing this?

EDIT: Preferably, this would satisfy dependencies as well.

Thanks in advance!

Also thanks to starcannon for the link to the page with instructions creating an Ubuntu mirror.  Definitely something I would like to look into.

---

### Post by bulldurham3293 on 2008-12-10
this is a completely different question. i am in to linux and i have wine for doing windows emulation but when i go to install it says software-properties-kde program is not running try to install it. so i install it and it still says the same thing can some tell me how to get it to run.

---

### Post by mwero001 on 2009-03-16
Hi all?

I've been trying to configure gnokii in my machine.
It's working well & I can send mesaages via the terminal. The challenge comes in here, I need to get my phone to read & write the texts from/to the mysql database.
I've unsuccessfully tried to connect my nokia 6233 to the mysql db unsuccessfully.

I'm working on web based sms project & that's why I need to my phone reading from the mysql db.

Any assistance pleeeeaase!!??

---

### Post by wannadumpwindows on 2009-03-16
> **bulldurham3293 said:**
> this is a completely different question. i am in to linux and i have wine for doing windows emulation but when i go to install it says software-properties-kde program is not running try to install it. so i install it and it still says the same thing can some tell me how to get it to run.

> Hi all?

I've been trying to configure gnokii in my machine.
It's working well & I can send mesaages via the terminal. The challenge comes in here, I need to get my phone to read & write the texts from/to the mysql database.
I've unsuccessfully tried to connect my nokia 6233 to the mysql db unsuccessfully.

I'm working on web based sms project & that's why I need to my phone reading from the mysql db.

Any assistance pleeeeaase!!??

If it's a completely different question, you need to do the courteous thing and start your own thread.

You're much more likely to get an answer that way.

---

