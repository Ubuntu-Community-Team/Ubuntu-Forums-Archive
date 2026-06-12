---
title: "Ubuntu or Kubuntu"
date: 2009-06-13
forum: Recurring Discussions
---

### Post by DJNJ on 2009-06-13
Im kinda new with these open source operating systems.

I have been using ubuntu for about a year.
and i recently saw kubuntu with KDE.


Which one is the best ? Best as in faster and stable.

Ubuntu or Kubuntu?

---

### Post by jenkinbr on 2009-06-14
> **DJNJ said:**
> Im kinda new with these open source operating systems.

I have been using ubuntu for about a year.
and i recently saw kubuntu with KDE.


Which one is the best ? Best as in faster and stable.

Ubuntu or Kubuntu?
*Best* is a matter of opinion.

I use Ubuntu because I cannot for the life of me get kubuntu or KDE to run on my system at a respectable speed.

KDE4 has been around long enough now that it is rather stable.

I'm a GNOME guy, but that doesn't mean I'm going to cram GNOME down your throat - I have a few KDE apps installed because I like them and/or need them.

If you have the space, you can run both.  Kubuntu and Ubuntu will sit happily side by side on the same system.  If you are using ubuntu, try running```
sudo apt-get install kubuntu-desktop
``` and if you are running Kubuntu, try running ```
sudo apt-get install ubuntu-desktop
```

---

### Post by Chemical Imbalance on 2009-06-14
Just clarification: after you install kubuntu-desktop, you have to log out to the login screen.  Select "Session" in the lower corner and choose "KDE".  Then log back in and you should be in KDE4.

---

### Post by DJNJ on 2009-06-14
Thanks for the quick reply guys !!

---

### Post by jenkinbr on 2009-06-14
No problem.

---

### Post by boarder428 on 2009-08-01
So I'm currently running jaunty in the gnome desktop,  I'm still fairly new to whole Linux world but adapting rather well and very curious.  I'd like to try out the kde desktop but am a little confused.

If I try kde and experience problems is it easy to go back to gnome?

Also I don't understand the log in session thing.  Does that mean you have the choice of logging in to Kde desktop or Gnome desktop?

 I'm still adapting from windows and still have to use window very frequently and I like the desktop enhancements, widgets ect in vista and would like to learn how to make my ubuntu desktop look similar, any good tut's with some more explanation?

---

### Post by Tipped OuT on 2009-08-01
> **boarder428 said:**
> So I'm currently running jaunty in the gnome desktop,  I'm still fairly new to whole Linux world but adapting rather well and very curious.  I'd like to try out the kde desktop but am a little confused.

If I try kde and experience problems is it easy to go back to gnome?

Also I don't understand the log in session thing.  Does that mean you have the choice of logging in to Kde desktop or Gnome desktop?

 I'm still adapting from windows and still have to use window very frequently and I like the desktop enhancements, widgets ect in vista and would like to learn how to make my ubuntu desktop look similar, any good tut's with some more explanation?

Let me brake it down for you.

If you follow the directions to install KDE from **jenkinbr**'s post, then you'll be able to choose to use KDE, or GNOME, at your will.

How? You log out, and there's a text that says "Options" on the bottom left. Click on that, select Sessions and you should see KDE as an option, click on KDE. When you log in, you'll log into KDE.

When you want to log in back to GNOME, you do the same thing, you log out, select Options, then Sessions and choose GNOME, and log in.

If you don't like KDE, you can log into GNOME, and uninstall KDE with this command:

```
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde
```

---

### Post by XubuRoxMySox on 2009-08-01
> **boarder428 said:**
> ... I don't understand the log in session thing.  Does that mean you have the choice of logging in to Kde desktop or Gnome desktop?

Yup! You can have as many desktop environments installed as you have room for on your hard drive! Some are rich in eye candy and wicked-kewl effects, some are simpler, most have their own applications but can run the others with no problems.

The logout thing lets you choose which one you want to use for that session. After you install a new desktop environment
```

sudo apt-get install ubuntu-desktop
``` or ```
sudo apt-get install kubuntu-desktop
``` pr ```
sudo apt-get install xubuntu-desktop
``` or ```
sudo apt-get install lxde
```, then you log out.

When you go back to login screen, find the Options button (lower left). Click it, then choose your Session (KDE, Gnome, Xfce, LXDE, Enlightenment, etc).

Why not explore them all? Each is wonderful in it's own way. For older computers (let's say 512 of RAM or less), I recommend [LXDE]("http://lxde.org") *much* more than Xfce. I find it much lighter weight, with far fewer dependencies (it's designed to be "independent"), and very "newbie friendly."

-Robin

---

### Post by SuperSonic4 on 2009-08-01
> **Tipped OuT said:**
> Let me brake it down for you.

If you follow the directions to install KDE from **jenkinbr**'s post, then you'll be able to choose to use KDE, or GNOME, at your will.

How? You log out, and there's a text that says "Options" on the bottom left. Click on that, select Sessions and you should see KDE as an option, click on KDE. When you log in, you'll log into KDE.

When you want to log in back to GNOME, you do the same thing, you log out, select Options, then Sessions and choose GNOME, and log in.

If you don't like KDE, you can log into GNOME, and uninstall KDE with this command:

```
sudo apt-get remove kubuntu-desktop
```

That bottom bit is untrue - it will only remove the small metapackage. Instead one should paste ```
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde
```

Source: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by slakkie on 2009-08-01
do aptitude search tu-desktop, see what other desktops ubuntu provides :)

---

### Post by Tipped OuT on 2009-08-01
> **SuperSonic4 said:**
> That bottom bit is untrue - it will only remove the small metapackage. Instead one should paste ```
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde
```

Source: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Yeah, thank you for the correction.

---

### Post by ktechkio on 2009-08-02
> **Tipped OuT said:**
> Yeah, thank you for the correction.

What's the point. The simplest way is install with sudo aptitude install kubuntu-desktop

Remove with sudo aptitude remove kubuntu-desktop:popcorn:

---

### Post by slakkie on 2009-08-02
Like said, that will remove only the meta-package. And not the packages which are installed by that package.

---

### Post by ktechkio on 2009-08-02
> **slakkie said:**
> Like said, that will remove only the meta-package. And not the packages which are installed by that package.

Seems like you never tried!:KS 
If you do both install and remove with aptitude **NOT** apt-get it will remove the whole package set.

---

### Post by Regenweald on 2009-08-02
> **ktechkio said:**
> Seems like you never tried!:KS 
If you do both install and remove with aptitude **NOT** apt-get it will remove the whole package set.

Probably the one thing that puts aptitude over apt-get and why i use it, sensible handling of dependencies: it came in when i installed 'this' and so should it leave when i uninstall it. Sorry to de-rail.

---

### Post by Tipped OuT on 2009-08-02
> **ktechkio said:**
> Seems like you never tried!:KS 
If you do both install and remove with aptitude **NOT** apt-get it will remove the whole package set.

Which ever works best for you man.

---

### Post by kg84 on 2009-08-02
A couple of questions...

How much extra space is needed to install the KDE desktop alongside Ubuntu's Gnome?

If one likes KDE more than Gnome can this be made the default desktop environment that loads at start up?

Ta.

:)

---

### Post by slakkie on 2009-08-02
> **ktechkio said:**
> Seems like you never tried!:KS 
If you do both install and remove with aptitude **NOT** apt-get it will remove the whole package set.

Mmm, lemme show you:

```

8:46 pts/1 0 wesleys@eniac:/home/wesleys$ sudo aptitude  purge kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  k3b
The following packages will be REMOVED:
  kubuntu-desktop{p}
0 packages upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 45.1kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 162005 files and directories currently installed.)
Removing kubuntu-desktop ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
8:46 pts/1 0 wesleys@eniac:/home/wesleys$ which kwin
/usr/bin/kwin
8:46 pts/1 0 wesleys@eniac:/home/wesleys$                   

```


kwin is provided by kubuntu-desktop..

```

aptitude search tu-desktop
p   edubuntu-desktop                                                                 - edubuntu desktop system
p   edubuntu-desktop-kde                                                             - edubuntu desktop system with KDE desktop
p   gobuntu-desktop                                                                  - The Gobuntu desktop system
p   kubuntu-desktop                                                                  - Kubuntu desktop system
p   mythbuntu-desktop                                                                - The Mythbuntu standalone system
p   ubuntu-desktop                                                                   - The Ubuntu desktop system
p   xubuntu-desktop                                                                  - Xubuntu desktop system

```

Yet I have Gnome/KDE/Xfce etc etc installed.

---

### Post by tacantara on 2009-08-02
> **kg84 said:**
> A couple of questions...

How much extra space is needed to install the KDE desktop alongside Ubuntu's Gnome?

If one likes KDE more than Gnome can this be made the default desktop environment that loads at start up?

Ta.

:)

I have a 120 GB HD (small by today's standards) on my laptop, and I have both KDE and Gnome DEs installed.  I guess it depends on how much other stuff you have on your HD and remaining capacity.  In other words, I can't tell you how much space you need to install an extra DE (anyone out there have that info?).  When you have more than one DE installed, during the boot process, you can switch between DEs, and even select which one you want to use as your default DE.  I occasionally switch between Gnome and KDE just to make the overall user experience more interesting, and when I want to show my Windows-using friends and co-workers how customizable Ubuntu is.

---

### Post by kg84 on 2009-08-02
> **tacantara said:**
> I have a 120 GB HD (small by today's standards) on my laptop, and I have both KDE and Gnome DEs installed.  I guess it depends on how much other stuff you have on your HD and remaining capacity.  In other words, I can't tell you how much space you need to install an extra DE (anyone out there have that info?).  When you have more than one DE installed, during the boot process, you can switch between DEs, and even select which one you want to use as your default DE.  I occasionally switch between Gnome and KDE just to make the overall user experience more interesting, and when I want to show my Windows-using friends and co-workers how customizable Ubuntu is.

Thanks for the reply.

I currently have Ubu on a 50GB partition (machine dual boots with Vista) - its a pretty fresh install of Ubu, so most of this is free.

I would hazard a guess and say that this will be more than ample :)

Thanks for the info on switching / prioritising one E over the other. Am keen to give KDE a go as I used mandrake a long time ago and am feeling a tad nostalgic ;)

---

### Post by slakkie on 2009-08-02
If you run the simulation you could get an indication of how big it will be:

```

sudo aptitude -s install kubuntu-desktop

```

Then look for the lines:

```

Need to get 25.8kB of archives. After unpacking 53.2kB will be used.

```

For you it will be different, since I already have all the dependencies installed.

---

### Post by londonali1010 on 2009-08-02
I can't say for sure how big it is, but it definitely isn't huge.  I have an 8GB netbook and I ran gnome and KDE both for a while, and I still had ample space for other files.  Just using gnome I take up 6.5 GB, so it was probably significantly less than 1 GB for the DE install!

---

### Post by SuperSonic4 on 2009-08-02
I believe the DE install itself is much the same as a live cd - about 700mb.

As slakkie said you can pass the -s (simulate) flag to check what you need

---

### Post by kg84 on 2009-08-02
Nice one :)

Thanks for the info - I will have a look at KDE later this evening or tomorrow.

---

### Post by boarder428 on 2009-08-02
Great topic, lots of good info here!  Thanks to all, I think my question(s) have been answered for the moment!

---

### Post by boarder428 on 2009-08-06
So I seem to be running into an issue here, I set KDE as my default enviroment upon installng and when I boot up the computer I get the kde login screen but it boots into gnome and in order to get to kde I have to log out and choose kde.  does anyone have any suggestions?

---

### Post by MasterNetra on 2009-08-06
> **boarder428 said:**
> So I seem to be running into an issue here, I set KDE as my default enviroment upon installng and when I boot up the computer I get the kde login screen but it boots into gnome and in order to get to kde I have to log out and choose kde.  does anyone have any suggestions?

Make it KDE default it should ask you if you want to make KDE default for that account. Just make sure you select the session as KDE before you login. ^.^

---

### Post by boarder428 on 2009-08-06
> **MasterNetra said:**
> Make it KDE default it should ask you if you want to make KDE default for that account. Just make sure you select the session as KDE before you login. ^.^

I guess I don't quite understand. I did choose to make KDE default, I thought that would make kde the default if I did'nt choose a session, or does that just change the login screen? cause now when it boots it shows the kubuntu splash screen and then login screen has changed as well to what I assume is the kubutu log in screen?

If I wanted to change the default back to ubuntu how would I do so without uninstalling kubuntu?

---

### Post by Tipped OuT on 2009-08-07
> **boarder428 said:**
> I guess I don't quite understand. I did choose to make KDE default, I thought that would make kde the default if I did'nt choose a session, or does that just change the login screen? cause now when it boots it shows the kubuntu splash screen and then login screen has changed as well to what I assume is the kubutu log in screen?

If I wanted to change the default back to ubuntu how would I do so without uninstalling kubuntu?

You're using the KDM login screen that's why. 

Enter this:
```
sudo dpkg-reconfigure gdm
```

Then set GDM as your login.

---

### Post by boarder428 on 2009-08-07
> **Tipped OuT said:**
> You're using the KDM login screen that's why. 

Enter this:
```
sudo dpkg-reconfigure gdm
```

Then set GDM as your login.
Thanks for the reply although I was returned the following error
```
* Reloading GNOME Display Manager configuration... 
* Changes will take effect when all current X sessions have ended.                           
invoke-rc.d: initscript gdm, action "reload" failed.

```

I tried running the command within gnome and kde with the same return

I seem to have figured it out.  I booted to recovery mode>netroot and ran the command from there, it gave me the same return but the changes took effect this time upon rebooting!
Thanks!

---

### Post by AlmaTlust on 2009-08-24
Just clarifying a little bit:
kdm and gdm are display managers (programs that manage how your graphical system is started and stuff - xdm is another one). You can use either one depending on what you like better, both display managers can start any desktop environment.

kde and gnome (and xfce and others) are desktop environments. These sets of programs control how your desktop looks like, and they come with a set of programs that are designed to run with the desktop environment. But you are not restricted to those. You can run Gnome programs under KDE and vice versa.

When started the display manager (kdm or gdm at your like), you can choose which desktop environment to start. Normally it will remember your choice and start into the same DE until you change again.

One more info (although you probably noticed): Your documents and stuff are the same in all DEs, you have access to the same files etc., so you can switch as you like...

All DEs have their sets of programs for different tasks (like email, web, messaging, etc). Some arre better in one DE, some are better in the other. It depends on what you want to do.
I for example use KDE generally, because the PIM suite is better for me, but I have a bunch of Gnome programs that I use (like GIMP for graphics and Inkscape for vector graphics) because KDE hasn't any equals (yet)

My general impressions on DE's:
KDE: Big, many options, much to play around. Tends to be a little more resource intensive, depending on your system
Gnome: Big, less options, less to play around (still a lot to play around, though). A little less resource intensive than KDE
XFCE (xubuntu-desktop): A smaller system fitted well for lower-end computers or older systems. 
Hope that clarifies things...

---

### Post by nomnomnom on 2009-08-24
This is pretty weird for me to say but..... *Kubuntu*. 

I have grown to like it more than I thought I would.... :(

---

### Post by Benzaa on 2009-08-24
Ubuntu

The layout in kde in quite weird, it doest feel right.

---

### Post by bodhi.zazen on 2009-08-24
Xubuntu FTW !!!!

---

### Post by Perfect Storm on 2009-08-24
> **bodhi.zazen said:**
> Kubuntu FTW !!!!

Fixed it for ya! :popcorn:

---

### Post by RabbitWho on 2009-08-24
Kubuntu keeps causing my computer to crash and general errors. Not to mention how long it took to get the internet to connect where it only takes about 30 seconds on ubuntu and the others. I can't even switch users without the whole screen going black and refusing to let me do anything till i restart. I love kubuntu it's beautiful but if it doesn't work then what good is it. You're not even supposed to be aware of what operating system you're using most of the time and it makes me painfully aware at every opportunity by trying to make my life hell.

---

### Post by macogw on 2009-08-24
I think my Kubuntu avatar answers this.

---

### Post by Mike3 on 2009-08-24
I personally like Ubuntu slightly better. The GUI (GNOME) is more sleek, and it's slightly easier to migrate to from Windows.

---

### Post by mdsmedia on 2009-08-25
I started with Gnome (Ubuntu), tried Kubuntu-desktop but couldn't get to like it. I always had it installed alongside Ubuntu and always went back to Ubuntu.

I tried Xubuntu for a while and really liked it, but went back to Ubuntu.

I've had a fair bit more experience now and tried Debian (felt a lot like Xubuntu) and Mandriva (KDE).

When I installed Arch I put Xfce on as my DE.

Ubuntu is still my main OS/Distro/DE but i could grow to like Arch and Xfce or another DE.

I just couldn't get to like Kubuntu and Mandriva, with KDE, didn't grow on me either.

---

### Post by dandis on 2009-08-25
Ubuntu. I can't stand KDE.

---

### Post by Chemical Imbalance on 2009-08-25
> **dandis said:**
> Ubuntu. I can't stand KDE.

+1

KDE is too 'form over function' for me.  Simpler is better, but to only to an extent.  FLuxbox ,etc. can be a pain.  Gnome sits perfectly with me.

---

### Post by macogw on 2009-08-25
> **Chemical Imbalance said:**
> +1

KDE is too 'form over function' for me.  Simpler is better, but to only to an extent.  FLuxbox ,etc. can be a pain.  Gnome sits perfectly with me.

/me looks at options available in KDE
/me looks at options available in GNOME

Huh?  KDE's got way more functions.

---

### Post by Chemical Imbalance on 2009-08-25
> **macogw said:**
> /me looks at options available in KDE
/me looks at options available in GNOME

Huh?  KDE's got way more functions.

Bugs don't count as functions. :lolflag:

---

