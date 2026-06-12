---
title: "[SOLVED] Im an idiot..."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-10-03
I recently updated to Ubuntu intepid ibex alpha 5 (yes I know _alpha's_ a bit of a hint...) and then ran the pure gnome command from psychocats...[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
```

to remove kde4 but not realising that its only for ubuntu hardy heron until it was too late...and now ubuntu wont work is there anyway to reverse this?

---

### Post by Ryadt on 2008-10-03
No you can't reverse. You will have to do a fresh install of hardy.

---

### Post by Sef on 2008-10-03
> and now ubuntu wont work is there anyway to reverse this?

Could you please be more specific about what won't work.  


>  Im an idiot...

Mistakes are for learning.  If you never made a mistake, you would learn nothing.

---

### Post by kamitsukai on 2008-10-03
> **Ryadt said:**
> No you can't reverse. You will have to do a fresh install of hardy.

oh well...:D its kinda what I expected...serves me right really

---

### Post by Joeb454 on 2008-10-03
You could try dist-upgrading to the beta of Intrepid if you really want to run it, that may work (if you can get to a terminal).

If you can't boot up properly, but recovery mode works (and you have net access) you could run ```
apt-get update
apt-get dist-upgrade
```

---

### Post by kamitsukai on 2008-10-03
> **Sef said:**
> Could you please be more specific about what won't work.  




Mistakes are for learning.  If you never made a mistake, you would learn nothing.

well it will boot up but then i get an error..hang on ill take a pic and post the error

---

### Post by hyper_ch on 2008-10-03
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by Bucky Ball on 2008-10-03
You could go into software sources, enable your cd then drag them back somehow that way; but I'm guessing 'apt-get' is not going to work at this point. If you could download that package and manually make it then you could put the code from your first post into a terminal and replace 'remove' with 'install'

sudo apt-get **install** all_the_removed_packages

... except for the kde ones. :)

---

### Post by kamitsukai on 2008-10-03
well just tried to boot again and noticed that i didnt get an error but i just got to a text based login? and no gui...

also "apt-get dist upgrade" didnt work

---

### Post by Joeb454 on 2008-10-03
What does the screen say?

---

### Post by kamitsukai on 2008-10-03
> **Joeb454 said:**
> What does the screen say?

doesen't just asks me to log in:confused: ill probably just reinstall allot simpler

also is it possible to create a separate home partition from the graphical install on the hardy live cd?

---

### Post by Joeb454 on 2008-10-03
> **kamitsukai said:**
> doesen't just asks me to log in:confused: ill probably just reinstall allot simpler

also is it possible to create a separate home partition from the graphical install on the hardy live cd?

1) That's up to you :)

2) Yes you can, when the installer asks you to do your partitions - though if you have a dual boot - be careful of how you modify them, else you may overwrite your Windows partition (I've done it before...luckily I didn't mind :))

---

### Post by Sef on 2008-10-03
If it goes to the terminal, try this code:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by kamitsukai on 2008-10-03
Thanks for everyones help but ive just started reinstalling hardy now :) but ive learnt a valuable lesson dont just copy and paste things into the terminal unless youve tripple checked what your doing :P

---

