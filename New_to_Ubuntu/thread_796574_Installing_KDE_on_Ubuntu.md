---
title: "Installing KDE on Ubuntu"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by bornem4nn on 2008-05-16
I have Ubuntu on my laptop and am currently using Gnome.  I am attempting to switch between Gnome and KDE.  I was told to go in the terminal and type "sudo apt-get install kubuntu-desktop" although it said that it can't find the package.   



ryan@ryan-laptop:~$ sudo apt-get install kubuntu-desktop
[sudo] password for ryan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop
ryan@ryan-laptop:~$ 



So please if anyone has an idea please let me know. Thanx.

---

### Post by forestpixie on 2008-05-16
Open software sources in system - admin. Check universe,muliverse and restricted, close and reload. Then have another go

---

### Post by bornem4nn on 2008-05-19
ahhh ic. Thank you, I appreciate your help. its up and running

---

### Post by forestpixie on 2008-05-19
Glad I could help, can you mark thread solved please

---

### Post by Mr. Svinlesha on 2008-05-19
Quick question: I just followed the instructions here and installed KDE as well.  Very nice.  But is there a way to get past the login screen during start-up -- that is, to log in automatically?  I did this in Gnome through System > Administration > Login Window, but that doesn't seem to work in KDE.

---

### Post by forestpixie on 2008-05-19
> In Feisty Fawn >System>Administration>Login Window>Click "Security Tab" then check "Enable Automatic Login" and then choose your user name from the drop down arrow. You should be good to go at next boot.

Found this - might work with hardy but not sure as I don't use it. If it doesn't work maybe do a thread.

---

### Post by Mr. Svinlesha on 2008-05-20
Yeah -- that's what I tried.  It didn't work, which is why I posted the question.

Thanks anyway, though.

---

### Post by zvacet on 2008-05-20
> I just followed the instructions here and installed KDE as well. Very nice. But is there a way to get past the login screen during start-up -- that is, to log in automatically?

Do you mean login automaticlly in KDE? If that is yes then in login window at bottom left you will see sessions and select KDE to be default.

---

### Post by Mr. Svinlesha on 2008-05-20
That's exactly what I meant and thanks again, **zvacet**.

Second time you've helped me out in the space of two minutes.

:)

---

### Post by T-Virus on 2008-05-20
Why not freshly install Kubuntu?

---

### Post by Mr. Svinlesha on 2008-05-20
Okay, slightly embarressing question, but... what if I want to log in to Gnome as default?

---

### Post by forestpixie on 2008-05-20
Do the same as before - at the login window choose session - gnome then when it asks make it default

---

### Post by Mr. Svinlesha on 2008-05-20
I tried that but it doesn't ask.  In fact, I'm not sure how I succeeded in making KDE my default desktop.  Instead, I get a context menu with a list: Default, Gnome, KDE, and a couple of others.  I have to select one to log in.

?

---

### Post by forestpixie on 2008-05-20
Do that - select Gnome and then it should ask the question - before you get to enter usrname

---

### Post by Mr. Svinlesha on 2008-05-20
Hmmmm... in the version I'm using, my username is already automatically selected when the login window pops up.  I've tried several variations of your instructions now, but nothing seems to work.

How do I uninstall KDE?

---

### Post by forestpixie on 2008-05-20
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

I know when I have mine set to login automatically - to get back to the session change/login window I have to logout of gnome - then I get the login/username page - at the bottom left - sessions or something like that - change session - choose which you want - then you login I think and get the do you want this just for this session or as default dialogue.

If you're not getting those options perhaps you could let us know what is actually happening :)

Anyway to get rid I used the psychocats page.

Good luck

---

### Post by Mr. Svinlesha on 2008-05-20
Well, there's something different, anyway... I don't have anything in the lower left-hand side of the screen, only a little icon at the bottom right of the login window, which opens a context menu...

KDE is nice, but I realized after I got installed that I have already installed a bunch of gizmos and so forth in Gnome that don't carry over...and let's face it, Gnome is pretty nice too.

Anyway, thanks again for the help.

---

### Post by zvacet on 2008-05-20
> I get a context menu with a list: Default, Gnome, KDE, and a couple of others. I have to select one to log in.

As** forestpixie** said do that and you should be able to choose which one to use.Do you maybe have problems with that because you put yourself to automatic login?If that is the case logout and you will see login window with sessions in bottom left.Select Gnome and that´s it.if you want to remove KDE 

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools
```

---

