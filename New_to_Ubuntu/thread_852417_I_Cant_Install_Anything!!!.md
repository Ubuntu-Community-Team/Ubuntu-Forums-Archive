---
title: "I Cant Install Anything!!!"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by utfan2012 on 2008-07-07
paul@laptop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdeartwork-emoticons-kde4 parley-data-kde4 libwildmidi0 texlive-base-bin-doc
  smartpm-core lilypond-doc python-pexpect lilypond-data kdebase-data-kde4
  texlive-base kdeartwork-theme-window-kde4 texlive texlive-fonts-recommended
  libsoundtouch1c2 libcfitsio3 texlive-pstricks-doc lmodern python-pycurl
  libmono-zeroconf1.0-cil ttf-dustin libtagc0 kdeartwork-misc-kde4
  texlive-common kdegames-mahjongg-data-kde4 libopenspc0 libvncserver0
  klettres-data-kde4 libchm1 kdeedu-data mysql-common kde-icons-oxygen
  texlive-pstricks kalzium-data texlive-base-bin kdewallpapers-kde4
  libmysqlclient15off dvipdfmx tetex-bin kgeography-data-kde4 marble-data-kde4
  prosper blt tipa texlive-latex-recommended-doc python-tk
  texlive-latex-base-doc ttf-sjfonts python-rpm kdelibs5-data kstars-data-kde4
  libtaglib2.0-cil ksysguardd-kde4 libcaptury0 icedax freepats kstars-data
  edict pgf libboo2.0-cil kamefu-data kalzium-data-kde4
  texlive-latex-recommended libkarma0 libzip1 texlive-generic-recommended
  kanjidic libcdaudio1 kdebase-workspace-data qt3-doc texlive-latex-base
  texlive-fonts-recommended-doc libsidplay1 libavahi1.0-cil
  kdeartwork-theme-icon-kde4 libkonq5-templates perl-tk libcapseo0
  latex-beamer pmount libraptor1 libgmyth0 indi indi-kde4 latex-xcolor
  texlive-doc-base raptor-utils kdegames-card-data-kde4 libnova-0.12-1
  libid3-3.8.3c2a tex-common kdepimlibs-data libboost-python1.34.1 libmms0
  libiptcdata0 texinfo libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavcodec1d libavformat1d libavutil1d libgsm1 libmad0 libmodplug0c2
  libmpcdec3 libpostproc1d vlc-nox vlc-plugin-pulse
Recommended packages:
  videolan-doc
The following packages will be REMOVED:
  kio-umountwrapper
The following NEW packages will be installed:
  libavcodec1d libavformat1d libavutil1d libgsm1 libmad0 libmodplug0c2
  libmpcdec3 libpostproc1d mozilla-plugin-vlc vlc vlc-nox vlc-plugin-esd
  vlc-plugin-pulse
0 upgraded, 13 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 8189kB of archives.
After this operation, 22.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libavutil1d 3:0.cvs20070307-5ubuntu7 [39.0kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libgsm1 1.0.12-1 [27.2kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libavcodec1d 3:0.cvs20070307-5ubuntu7 [1602kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libavformat1d 3:0.cvs20070307-5ubuntu7 [287kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libmad0 0.15.1b-2.1ubuntu1 [76.4kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libmodplug0c2 1:0.7-7 [122kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libmpcdec3 1.2.2-1build1 [27.4kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libpostproc1d 3:0.cvs20070307-5ubuntu7 [73.3kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse vlc-nox 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3 [4745kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse vlc-plugin-pulse 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3 [6954B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse vlc 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3 [1140kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse mozilla-plugin-vlc 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3 [37.9kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse vlc-plugin-esd 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3 [4884B]
Fetched 8189kB in 9s (898kB/s)                                                 
(Reading database ... 225123 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

Help PLEASE

---

### Post by phidia on 2008-07-07
You can read [this]("http://www.debian-administration.org/articles/251") for subprocess post removal script errors, and probably [this]("http://lycos.dropcode.net/gregarius/feed.php?channel=183&y=2008&m=05&d=11&iid=258079") too.

---

### Post by utfan2012 on 2008-07-07
Im really not good at this, the websites still were above my head...

---

