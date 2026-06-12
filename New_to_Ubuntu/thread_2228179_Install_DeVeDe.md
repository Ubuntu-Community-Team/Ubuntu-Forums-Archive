---
title: "Install DeVeDe"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by mlempenau on 2014-06-06
I have installed 14.04 and all the updates.  I have also install other s/w packages.  I have installed ubuntu restricted extras.  When I try to install DeVeDe it tells me that two packages must be removed.  Libav codec library and movie player for unix like systems.  Then it gives me the option of installing anyway???  How should I proceed?

---

### Post by rahul4557 on 2014-06-06
First run command
> sudo apt-get autoremove
This will remove any packages that are no more required (which were automatically installed to satisfy dependencies for some packages)

Than try installing DeVeDe..
Good Luck..

---

### Post by coffeecat on 2014-06-06
The dependency list for the version of devede in the Ubuntu 14.04 repositories suggests that you should not be prompted to uninstall packages. Which suggests that you have enabled and installed things from 3rd party repositories which are causing conflicts.

Please post the complete output of this terminal command:

```
sudo apt-get -s install devede
```

This will not install anything, but simply simulate installing devede. The output will help identify which packages and which versions of these packages are causing problems. Highlight the terminal output with your mouse and right-click to copy. Then paste into your post enclosing the output between [noparse]```
 and 
```[/noparse] tags.

Also - do you have any PPA or other 3rd party repositories enabled? If so, which ones?

---

### Post by mlempenau on 2014-06-06
```
mlempenau@mlempenau1404:~$ sudo apt-get -s install devede
[sudo] password for mlempenau: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb kde-l10n-th linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-headers-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
  linux-image-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dvdauthor imagemagick imagemagick-common libav-tools libavcodec-extra-54
  libavdevice53 libavfilter3 libbs2b0 liblqr-1-0 libmagickcore5
  libmagickcore5-extra libmagickwand5 libnetpbm10 libquvi-scripts libquvi7
  mplayer2 netpbm
Suggested packages:
  imagemagick-doc autotrace curl enscript ffmpeg gnuplot grads hp2xx html2ps
  libwmf-bin povray radiance texlive-base-bin transfig ufraw-batch
  frei0r-plugins
The following packages will be REMOVED:
  libavcodec54 mplayer
The following NEW packages will be installed:
  devede dvdauthor imagemagick imagemagick-common libav-tools
  libavcodec-extra-54 libavdevice53 libavfilter3 libbs2b0 liblqr-1-0
  libmagickcore5 libmagickcore5-extra libmagickwand5 libnetpbm10
  libquvi-scripts libquvi7 mplayer2 netpbm
0 upgraded, 18 newly installed, 2 to remove and 9 not upgraded.
Remv mplayer [2:1.1+dfsg1-0ubuntu3] [mencoder:i386 ]
Inst mplayer2 (2.0-701-gd4c5b7f-2ubuntu2 Ubuntu:14.04/trusty [i386]) []
Remv libavcodec54 [6:9.13-0ubuntu0.14.04.1] [mencoder:i386 libchromaprint0:i386 libopencv-highgui2.4:i386 handbrake:i386 gstreamer1.0-libav:i386 libavformat54:i386 vlc-nox:i386 ]
Inst libavcodec-extra-54 (6:9.13-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386]) []
Inst libbs2b0 (3.1.0+dfsg-2ubuntu2 Ubuntu:14.04/trusty [i386]) []
Inst libquvi-scripts (0.4.21-1 Ubuntu:14.04/trusty [all]) []
Inst libquvi7 (0.4.1-1ubuntu3 Ubuntu:14.04/trusty [i386])
Inst imagemagick-common (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [all])
Inst libavdevice53 (6:9.13-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst libavfilter3 (6:9.13-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst libav-tools (6:9.13-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Inst liblqr-1-0 (0.4.1-2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst libmagickcore5 (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [i386])
Inst libmagickwand5 (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [i386])
Inst libmagickcore5-extra (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [i386])
Inst dvdauthor (0.7.0-1.2ubuntu1 Ubuntu:14.04/trusty [i386])
Inst imagemagick (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [i386])
Inst devede (3.23.0~ds1-5ubuntu1 Ubuntu:14.04/trusty [all])
Inst libnetpbm10 (2:10.0-15ubuntu2 Ubuntu:14.04/trusty [i386])
Inst netpbm (2:10.0-15ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libavcodec-extra-54 (6:9.13-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libbs2b0 (3.1.0+dfsg-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf libquvi-scripts (0.4.21-1 Ubuntu:14.04/trusty [all])
Conf libquvi7 (0.4.1-1ubuntu3 Ubuntu:14.04/trusty [i386])
Conf mplayer2 (2.0-701-gd4c5b7f-2ubuntu2 Ubuntu:14.04/trusty [i386])
Conf imagemagick-common (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [all])
Conf libavdevice53 (6:9.13-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libavfilter3 (6:9.13-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf libav-tools (6:9.13-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [i386])
Conf liblqr-1-0 (0.4.1-2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf libmagickcore5 (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [i386])
Conf libmagickwand5 (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [i386])
Conf libmagickcore5-extra (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [i386])
Conf dvdauthor (0.7.0-1.2ubuntu1 Ubuntu:14.04/trusty [i386])
Conf imagemagick (8:6.7.7.10-6ubuntu3 Ubuntu:14.04/trusty [i386])
Conf devede (3.23.0~ds1-5ubuntu1 Ubuntu:14.04/trusty [all])
Conf libnetpbm10 (2:10.0-15ubuntu2 Ubuntu:14.04/trusty [i386])
Conf netpbm (2:10.0-15ubuntu2 Ubuntu:14.04/trusty [i386])
mlempenau@mlempenau1404:~$
```

---

### Post by mlempenau on 2014-06-06
I only have cononical and independent checked in software sources.  Thanks

---

### Post by mc4man on 2014-06-07
You can go ahead & install
As far as libavcodec54 it's just replacing with the extra version which is fine
The maintainer has decided to replace the  mplayer dep  with mplayer2 or mpv
(- the 14.04 mpv build is terrible so you're better off with mplayer2

If you happened to have an mplayer install you wanted to hold on to the you could try installing mpv first, then devede,  possibly it then wouldn't remove mplayer

---

### Post by mlempenau on 2014-06-07
I just finished installing.  Install went well and DeVeDe seems to be working.  Thanks so much for the help.

---

