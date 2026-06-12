---
title: "Fixing Broken Packages"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by lanetherif on 2012-09-03
Hi,

in order to fix a broken package, I used an earlier thread where it was advised to use "autoremove". I did it, yet it suspiciously looks like more than necessary packages are removed. I didn't restart my PC, yet. Do you think what happened is right? Here is the list of files removed:

> acroread-common advancecomp aisleriot avogadro-data baobab
  browser-plugin-gnash calligrawords-data cheese cheese-common ekiga espeak
  espeak-data file-roller firefox-locale-zh-hans fonts-dustin gcalctool gdebi
  gdebi-core gdm gedit gedit-common gedit-plugins gir1.2-gdmgreeter-1.0
  gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gtksource-3.0
  gir1.2-gucharmap-2.90 gir1.2-ubuntuoneui-3.0 glchess glines gnash
  gnash-common gnect gnibbles gnobots2 gnome-backgrounds gnome-core
  gnome-dictionary gnome-disk-utility gnome-font-viewer gnome-games
  gnome-games-data gnome-games-extra-data gnome-icon-theme-extras
  gnome-nettool gnome-screenshot gnome-search-tool gnome-sudoku
  gnome-system-log gnome-video-effects gnomine gnote gnotravex gnotski
  gnuchess gnuchess-book gnugo gtali gucharmap guile-1.8-libs guile-2.0-libs
  hamster-applet iagno kalzium-data kdeartwork-emoticons kdeedu-kvtml-data
  kdegames-data kdegames-mahjongg-data kdewallpapers kgeography-data
  klettres-data kstars-data ktouch-data lib32stdc++6 lib32z1 libapr1
  libaprutil1 libavogadro1 libbabl-0.0-0 libboost-graph1.46.1
  libboost-iostreams1.46.1 libboost-program-options1.46.1
  libboost-python1.46.1 libboost-thread1.46.1 libc6-dbg libcapi20-3
  libcfitsio3 libcheese-gtk21 libcheese3 libdb4.8 libdbus-glib1.0-cil
  libdbus1.0-cil libdmapsharing-3.0-2 libdotconf1.0 libespeak1 libgconf2.0-cil
  libgdict-1.0-6 libgdict-common libgdmgreeter1 libgdmsimplegreeter1
  libgdu-gtk0 libgegl-0.0-0 libgexiv2-1 libglew1.5 libgmime2.6-cil
  libgrantlee-gui0 libgtkglext1 libgtksourceview-3.0-0
  libgtksourceview-3.0-common libgtkspell-3-0 libindi-data libindi0
  libjpeg-progs libjpeg-turbo-progs libjpeg62 libjs-underscore libkdcraw-data
  libkdeedu-data libksane-data libkwinactivenvidiahack4
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmusicbrainz4-3
  libmusicbrainz5-0 libnova-0.12-2 liboil0.3 libopal3.10.2 libopenbabel4
  libpcrecpp0 libpt2.10.2 libqhull5 libraw5 libsonic0 libspnav0 libsvn1
  libubuntuoneui-3.0-1 libudisks2-0 lightsoff mahjongg marble-data
  media-player-info nepomuk-core-data nspluginviewer:i386 nspluginwrapper
  optipng palapeli-data parley-data plasma-active-data
  plasma-desktopthemes-artwork poxml python-egenix-mxdatetime
  python-egenix-mxtools python-enchant python-gdata python-iniparse
  python-levenshtein python-libproxy python-mako python-markupsafe
  python-pyexiv2 python-pyexiv2-doc python-vobject python-wnck qhull-bin
  qt4-linguist-tools qt4-qmake quadrapassel seahorse share-like-connect-data
  simple-scan sound-juicer speech-dispatcher subversion swell-foop
  translate-toolkit transmission-common transmission-gtk ttf-dustin udisks2
  valgrind vorbis-tools xdg-user-dirs-gtk xplanet-images xscreensaver-data
  xscreensaver-gl xsltproc

I am using Unity. I also use transmission and gedit or cheese...

Any ideas?

---

### Post by bigken on 2012-09-03
being a long since i was last here i used synaptic package manager in the past to repair broken packages

---

### Post by lanetherif on 2012-09-03
> **bigken said:**
> being a long since i was last here i used synaptic package manager in the past to repair broken packages

And?

---

### Post by timcredible on 2012-09-03
the dreaded broken packages is a pain.  synaptic has menu option to repair broken packages, but doesn't work sometimes.  the one time i ran into this, i ended up having to install packages by hand, and then just reinstalled.  luckily, unlike when windows registry gets hosed, reinstalling ubuntu is much easier than recovering windows

---

### Post by NikTh on 2012-09-03
Hello  , 

can you give the results of below command 

```
find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
``` 

Thanks

---

### Post by lanetherif on 2012-09-03
> **NikTh said:**
> Hello  , 

can you give the results of below command 

```
find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
```Thanks

Here it is:

> /etc/apt/sources.list.d/webupd8team-gnome3-precise.list

     1    deb [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu) precise main

/etc/apt/sources.list.d/diesch-testing-precise.list

     1    deb [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) precise main

/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_lordofultima_ubuntu.list

     1    # deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/lordofultima/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/lordofultima/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf

/etc/apt/sources.list.d/bisigi-ppa-precise.list

     1    # deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) precise main

/etc/apt/sources.list.d/mendeleydesktop.list

     1    # This file lists the repositories for Mendeley Desktop.
     2    #
     3    # These repositories should work with most recent Debian/Ubuntu-based Linux
     4    # distributions.
     5    #
     6    # If you have any problems with Mendeley's Debian/Ubuntu repositories,
     7    # you can let us know at [http://feedback.mendeley.com](http://feedback.mendeley.com)
     8    
     9    deb [http://www.mendeley.com/repositories/ubuntu/stable](http://www.mendeley.com/repositories/ubuntu/stable) /

/etc/apt/sources.list.d/google-talkplugin.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

/etc/apt/sources.list.d/tista-gdm-testing-precise.list

     1    deb [http://ppa.launchpad.net/tista/gdm-testing/ubuntu](http://ppa.launchpad.net/tista/gdm-testing/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/tista/gdm-testing/ubuntu](http://ppa.launchpad.net/tista/gdm-testing/ubuntu) precise main

/etc/apt/sources.list.d/webupd8team-themes-precise.list

     1    deb [http://ppa.launchpad.net/webupd8team/themes/ubuntu](http://ppa.launchpad.net/webupd8team/themes/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/webupd8team/themes/ubuntu](http://ppa.launchpad.net/webupd8team/themes/ubuntu) precise main

/etc/apt/sources.list.d/scopes-packagers-ppa-precise.list

     1    deb [http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu](http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu](http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu) precise main

/etc/apt/sources.list.d/ferramroberto-sopcast-precise.list

     1    deb [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu) precise main

/etc/apt/sources.list.d/jd-team-jdownloader-precise.list

     1    deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) precise main
     2    deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) precise main

/etc/apt/sources.list.d/venerix-blug-precise.list

     1    deb [http://ppa.launchpad.net/venerix/blug/ubuntu](http://ppa.launchpad.net/venerix/blug/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/venerix/blug/ubuntu](http://ppa.launchpad.net/venerix/blug/ubuntu) precise main

/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_swordandsworcery_ubuntu.list

     1    # deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/swordandsworcery/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/swordandsworcery/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf

/etc/apt/sources.list.d/webapps-preview-precise.list

     1    # deb [http://ppa.launchpad.net/webapps/preview/ubuntu](http://ppa.launchpad.net/webapps/preview/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/webapps/preview/ubuntu](http://ppa.launchpad.net/webapps/preview/ubuntu) precise main

/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list

     1    deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main
     2    deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main

/etc/apt/sources.list.d/gloobus-dev-covergloobus-precise.list

     1    # deb [http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu](http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu](http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu) precise main

/etc/apt/sources.list.d/kubuntu-ppa-ppa-precise.list

     1    # deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) precise main

/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list

     1    deb [http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu](http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu](http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu) precise main

/etc/apt/sources.list.d/noobslab-themes-precise.list

     1    deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) precise main

/etc/apt/sources.list.d/kubuntu-ppa-backports-precise.list

     1    # deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) precise main

/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_amnesia_ubuntu.list

     1    # deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/amnesia/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/amnesia/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf

/etc/apt/sources.list.d/fioan89-slidewall-precise.list

     1    deb [http://ppa.launchpad.net/fioan89/slidewall/ubuntu](http://ppa.launchpad.net/fioan89/slidewall/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/fioan89/slidewall/ubuntu](http://ppa.launchpad.net/fioan89/slidewall/ubuntu) precise main

/etc/apt/sources.list.d/ian-berke-ppa-drawers-precise.list

     1    deb [http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu](http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu](http://ppa.launchpad.net/ian-berke/ppa-drawers/ubuntu) precise main

/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list

     1    deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main

/etc/apt/sources.list.d/dropbox.list

     1    deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main

/etc/apt/sources.list.d/ubun-tor-ppa-precise.list

     1    # deb [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu) precise main

/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-59_ubuntu.list

     1    # deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-59/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-59/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf

/etc/apt/sources.list.d/recoll-backports-recoll-1_15-on-precise.list

     1    # deb [http://ppa.launchpad.net/recoll-backports/recoll-1.15-on/ubuntu](http://ppa.launchpad.net/recoll-backports/recoll-1.15-on/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/recoll-backports/recoll-1.15-on/ubuntu](http://ppa.launchpad.net/recoll-backports/recoll-1.15-on/ubuntu) precise main

/etc/apt/sources.list.d/kubuntu-ppa-beta-precise.list

     1    # deb [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu) precise main

/etc/apt/sources.list.d/marlin-devs-marlin-daily-precise.list

     1    deb [http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu](http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu](http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu) precise main

/etc/apt/sources.list.d/kokoto-java-omgubuntu-stuff-precise.list

     1    deb [http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu](http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu) precise main
     2    deb-src [http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu](http://ppa.launchpad.net/kokoto-java/omgubuntu-stuff/ubuntu) precise main

/etc/apt/sources.list.d/kroq-gar78-ppa-precise.list

     1    deb [http://ppa.launchpad.net/kroq-gar78/ppa/ubuntu](http://ppa.launchpad.net/kroq-gar78/ppa/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/kroq-gar78/ppa/ubuntu](http://ppa.launchpad.net/kroq-gar78/ppa/ubuntu) precise main

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
     5    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted #Added by software-properties
     6    
     7    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     8    # newer versions of the distribution.
     9    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise main restricted
    10    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise restricted main multiverse universe #Added by software-properties
    11    
    12    ## Major bug fix updates produced after the final release of the
    13    ## distribution.
    14    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    15    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates restricted main multiverse universe #Added by software-properties
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    18    ## team. Also, please note that software in universe WILL NOT receive any
    19    ## review or updates from the Ubuntu security team.
    20    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise universe
    21    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates universe
    22    
    23    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24    ## team, and may not be under a free licence. Please satisfy yourself as to 
    25    ## your rights to use the software. Also, please note that software in 
    26    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27    ## security team.
    28    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise multiverse
    29    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    37    deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse #Added by software-properties
    38    
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    42    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    43    
    44    ## Uncomment the following two lines to add software from Canonical's
    45    ## 'partner' repository.
    46    ## This software is not part of Ubuntu, but is offered by Canonical and the
    47    ## respective vendors as a service to Ubuntu users.
    48    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    49    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    50    
    51    ## This software is not part of Ubuntu, but is offered by third-party
    52    ## developers who want to ship their latest software.
    53    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    54    # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    55    deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) precise-proposed restricted main multiverse universe


By the way, due to bad luck PC restarted and it is working, also I've reinstalled transmission and gedit.

---

### Post by cortman on 2012-09-03
Looks like reverse dependency... hades.

Meta packages like "ubuntu-desktop" or "gnome-desktop-environment" can become fractured if any single component is uninstalled. Because the meta package "depends" on the removed package, the OS thinks that the package is defunct and should be removed. In reality, the meta package is just a convenient way to install multiple programs and packages, and doesn't "break" like a real software package.
The fix I've finally come to for this is to mark all the packages it suggests for autoremove as manually installed. The downside to this is obviously that those packages will no longer be autoremoved when it IS appropriate.
You can do this with apt-mark-

```
sudo apt-mark manual package_name
```

In your case, I would reinstall all the removed packages (shouldn't be tough, since you have the list of them right there, just very time and/or bandwidth consuming), then marking them all as manually installed with apt-mark.

---

### Post by lanetherif on 2012-09-03
> **cortman said:**
> Looks like reverse dependency... hades.

Meta packages like "ubuntu-desktop" or "gnome-desktop-environment" can become fractured if any single component is uninstalled. Because the meta package "depends" on the removed package, the OS thinks that the package is defunct and should be removed. In reality, the meta package is just a convenient way to install multiple programs and packages, and doesn't "break" like a real software package.
The fix I've finally come to for this is to mark all the packages it suggests for autoremove as manually installed. The downside to this is obviously that those packages will no longer be autoremoved when it IS appropriate.
You can do this with apt-mark-

```
sudo apt-mark manual package_name
```In your case, I would reinstall all the removed packages (shouldn't be tough, since you have the list of them right there, just very time and/or bandwidth consuming), then marking them all as manually installed with apt-mark.

I am cherry picking the programs I would want through the auto removed files and installing them through synaptics. Would it cause a problem (again)?

Edit: In fact it has ended very quickly. Acrobat Reader, Gedit, Transmission, Cheese...

---

### Post by NikTh on 2012-09-03
Hello, 

First of all I must say that I agree with @cortman's explanation of the situation you faced. 

My opinion is that the problem caused by the multiple external PPA's  have been added in your sources list , at past. 
Some of these PPA's caused the upgrade of some packages to a newer version. Then as I can see from the results of command either you removed them of disabled those PPA's. Usually when you remove or disable a PPA , packages that accompanying it, also will removed. 
An example of such PPA (that upgrades already installed programs) is 
> /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list

     1    deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
     2    # deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise mainI don't know if I am right or wrong , but thats my opinion. 

More experienced users will give a more clarifying answer. 

Thanks

---

