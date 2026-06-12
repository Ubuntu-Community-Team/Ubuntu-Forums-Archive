---
title: "How to update via terminal when updates are marked not upgraded...?"
date: 2022-09-07
forum: New to Ubuntu
---

### Post by yatski on 2022-09-07
Is there possibility to update packages that are marked "not upgraded" in terminal? 

I suspect they are from kernel updating that went awry(see [https://ubuntuforums.org/showthread.php?t=2478651](https://ubuntuforums.org/showthread.php?t=2478651))

I use 22.04 LTS and my computer is Sony Vaio.

---

### Post by ActionParsnip on 2022-09-07
What is the output of:
```

sudo apt update
sudo apt -y upgrade

```

---

### Post by yatski on 2022-09-07
```
[heta@heta-vaio:~$ sudo apt update
sudo apt -y upgrade
[sudo] password for heta: 
Hit:1 http://fi.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://fi.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:3 http://fi.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Get:4 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Hit:5 https://deb.opera.com/opera-stable stable InRelease                      
Fetched 110 kB in 1s (102 kB/s)                          
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode fonts-dejavu fonts-inter g++-7 g++-9 gir1.2-clutter-1.0
  gir1.2-clutter-gst-3.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-gtkclutter-1.0 icoutils intel-microcode iucode-tool kde-style-breeze
  kded5 libaio1 libamtk-5-0 libamtk-5-common libaom0 libaom0:i386 libaom3:i386
  libasn1-8-heimdal:i386 libasync-mergepoint-perl libavcodec58:i386
  libavutil56:i386 libbasicusageenvironment1 libboost-date-time1.71.0
  libboost-filesystem1.71.0 libboost-iostreams1.71.0 libboost-locale1.71.0
  libbrlapi0.7 libcbor0.6 libcdio18 libcodec2-0.9 libcodec2-0.9:i386
  libcodec2-1.0:i386 libcrystalhd3 libcurl3-gnutls:i386 libdav1d5:i386
  libdc1394-22 libdlrestrictions1 libdns-export1109 libdvdread7 libebml4v5
  libextutils-pkgconfig-perl libffi7:i386 libfuture-perl libfwupdplugin1
  libgdbm-compat4:i386 libgdbm6:i386 libgdk-pixbuf-xlib-2.0-0:i386
  libgdk-pixbuf2.0-0:i386 libgfortran4 libgl1-mesa-glx:i386 libglu1-mesa:i386
  libgomp1:i386 libgroupsock8 libgssapi3-heimdal:i386 libgupnp-1.2-0
  libhandy-0.0-0 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhfstospell11 libhogweed5 libhogweed5:i386
  libhx509-5-heimdal:i386 libicu66:i386 libieee1284-3:i386 libigdgmm11
  libigdgmm11:i386 libilmbase24 libio-async-loop-epoll-perl libio-async-perl
  libjson-c4 libjuh-java libjurt-java libkf5archive5 libkf5attica5 libkf5auth5
  libkf5bookmarks-data libkf5bookmarks5 libkf5completion-data
  libkf5completion5 libkf5crash5 libkf5doctools5 libkf5globalaccel-bin
  libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5
  libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5
  libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data
  libkf5jobwidgets5 libkf5kdelibs4support-data libkf5kiocore5
  libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5
  libkf5parts-data libkf5solid5 libkf5solid5-data libkf5style5
  libkf5textwidgets-data libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5
  libkrb5-26-heimdal:i386 libldap-2.4-2:i386 liblibreoffice-java
  liblinux-epoll-perl liblivemedia77 libllvm10 libllvm10:i386 libllvm11
  libllvm11:i386 libllvm12 libllvm12:i386 libllvm7 libllvm8 libllvm9
  libllvm9:i386 libmalcontent-0-0 libmatroska6v5 libmetrics-any-perl
  libmozjs-68-0 libmusicbrainz5cc2v5 libmysqlclient21 libmysqlclient21:i386
  libncurses5:i386 libnettle7 libnettle7:i386 libnspr4:i386 libnss3:i386
  libntfs-3g883 libnuma1:i386 libofa0 libopenexr24 libopengl0:i386
  libopenjp2-7:i386 liborcus-0.15-0 libpango-perl libpangox-1.0-0 libpci3:i386
  libperl5.34:i386 libpgm-5.2-0 libphonon4qt5-4 libphonon4qt5-data libplacebo7
  libpoppler-glib8:i386 libpoppler118:i386 libprotobuf-lite17
  libpython2-stdlib libpython3.8 libpython3.8-minimal libpython3.8-stdlib
  libqpdf26 libqt5printsupport5 libqt5script5 libqt5test5 libraw19
  libreadonly-perl libref-util-perl libref-util-xs-perl libridl-java
  libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 libsane
  libsane:i386 libsane1:i386 libsereal-perl libshine3:i386 libsnappy1v5:i386
  libsnmp40:i386 libsoxr0:i386 libspeexdsp1:i386 libsrt1 libssl1.1:i386
  libstdc++-7-dev libstdc++-9-dev libstruct-dumb-perl libswresample3:i386
  libtag-extras1 libtepl-4-0 libtest-fatal-perl libtest-metrics-any-perl
  libtest-refcount-perl libtinfo5:i386 libtracker-control-2.0-0
  libtracker-miner-2.0-0 libtype-tiny-perl libtype-tiny-xs-perl
  libunoloader-java libusageenvironment3 libutempter0 libva-drm2:i386
  libva-x11-2:i386 libvdpau1:i386 libvoikko1 libvpx6 libvpx6:i386
  libwebp6:i386 libwebpmux3:i386 libwind0-heimdal:i386 libwrap0:i386
  libx264-155 libx264-155:i386 libx264-163:i386 libx265-179 libx265-179:i386
  libx265-199:i386 libxml-writer-perl libxmlb1 libxvidcore4:i386 libzvbi0:i386
  lz4 mesa-vdpau-drivers:i386 mysql-common oxygen-icon-theme
  phonon-backend-gstreamer-common phonon4qt5-backend-vlc pkg-config
  python-cairo python-gobject-2 python2 python2-minimal python2.7
  python2.7-minimal python3-entrypoints python3.8 python3.8-minimal qtchooser
  shim thermald ure-java vdpau-driver-all:i386
  xserver-xorg-input-all-hwe-18.04 xserver-xorg-input-libinput-hwe-18.04
  xserver-xorg-input-wacom-hwe-18.04 xserver-xorg-legacy-hwe-18.04
  xserver-xorg-video-intel-hwe-18.04 xserver-xorg-video-nouveau-hwe-18.04
  xserver-xorg-video-radeon-hwe-18.04 xserver-xorg-video-vmware-hwe-18.04
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  dmidecode gcc-10-base gcc-10-base:i386
The following packages will be upgraded:
  gnome-remote-desktop
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 126 kB of archives.
After this operation, 4&#8239;096 B of additional disk space will be used.
Get:1 http://fi.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gnome-remote-desktop amd64 42.4-0ubuntu1 [126 kB]
Fetched 126 kB in 0s (472 kB/s)            
(Reading database ... 296569 files and directories currently installed.)
Preparing to unpack .../gnome-remote-desktop_42.4-0ubuntu1_amd64.deb ...
Unpacking gnome-remote-desktop (42.4-0ubuntu1) over (42.3-0ubuntu1) ...
Setting up gnome-remote-desktop (42.4-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.72.1-1) ...
Processing triggers for libglib2.0-0:amd64 (2.72.1-1) ...

```

---

### Post by Bashing-om on 2022-09-07
yatski; Hey hey ---

Your output just 'looks' frightening. Not overly concerning :D

For the info about "held packages" please see:
[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)
Generally known as "phased updates".

Currently for 22.04 there are dmidecode and compiz in this stater of release.
[http://people.canonical.com/~ubuntu-archive/phased-updates.html](http://people.canonical.com/~ubuntu-archive/phased-updates.html).

Now how about we take the package manager's advise and remove the obsolete packages:
```

sudo apt update
sudo apt autoremove

```

After that what shows:
```

sudo apt update
sudo apt upgrade

```

Just to make sure that the package manager is in a consistent state; not requiting further attention.

[INDENT]it's all in the process
[/INDENT]

---

### Post by yatski on 2022-09-08
I removed obsolete packages.
However, as code below shows, it doesn't mention "linux-image-generic" anywhere.


```
heta@heta-vaio:~$ sudo apt update
sudo apt upgrade
Hit:1 http://fi.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://fi.archive.ubuntu.com/ubuntu jammy-updates InRelease   
Hit:3 http://fi.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Hit:4 https://deb.opera.com/opera-stable stable InRelease                      
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease      
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  dmidecode gcc-10-base gcc-10-base:i386
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

---

### Post by Impavidus on 2022-09-08
> **yatski said:**
> 
However, as code below shows, it doesn't mention "linux-image-generic" anywhere.


Why should it? As mentioned above, those are phased updates. This applies to all updates, not just new kernels. They will be installed eventually (unless they get frozen when a serious problem is detected).

If you wish, you can force the updates anyway. Maybe this update is particularly important to you or you know you'll not be in a position to install updates in the following weeks. Use```
sudo apt upgrade packagename
```

---

### Post by ajgreeny on 2022-09-08
So what happens if you try to install **linux-image-generic** now and what kernel are you running?
You can find the current kernel with command ***uname -a***

---

### Post by yatski on 2022-09-08
My kernel is 5.15.0-47-generic.

```
heta@heta-vaio:~$ sudo apt upgrade linux-image-generic
[sudo] password for heta: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  amd64-microcode intel-microcode iucode-tool linux-image-generic
  linux-modules-extra-5.15.0-47-generic thermald
The following packages have been kept back:
  dmidecode gcc-10-base gcc-10-base:i386
0 upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 4&#8239;114 kB/68,3 MB of archives.
After this operation, 359 MB of additional disk space will be used.
Do you want to continue? [Y/n] y   
Get:1 http://fi.archive.ubuntu.com/ubuntu jammy/main amd64 iucode-tool amd64 2.3.1-1build1 [46,9 kB]
Get:2 http://fi.archive.ubuntu.com/ubuntu jammy-updates/main amd64 intel-microcode amd64 3.20220510.0ubuntu0.22.04.1 [4&#8239;032 kB]
Get:3 http://fi.archive.ubuntu.com/ubuntu jammy/main amd64 amd64-microcode amd64 3.20191218.1ubuntu2 [32,5 kB]
Get:4 http://fi.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-image-generic amd64 5.15.0.47.47 [2&#8239;576 B]
Fetched 4&#8239;114 kB in 2s (2&#8239;504 kB/s)         
Selecting previously unselected package iucode-tool.
(Reading database ... 280517 files and directories currently installed.)
Preparing to unpack .../0-iucode-tool_2.3.1-1build1_amd64.deb ...
Unpacking iucode-tool (2.3.1-1build1) ...
Selecting previously unselected package linux-modules-extra-5.15.0-47-generic.
Preparing to unpack .../1-linux-modules-extra-5.15.0-47-generic_5.15.0-47.51_amd
64.deb ...
Unpacking linux-modules-extra-5.15.0-47-generic (5.15.0-47.51) ...
dpkg: error processing archive /tmp/apt-dpkg-install-66Mu3p/1-linux-modules-extr
a-5.15.0-47-generic_5.15.0-47.51_amd64.deb (--unpack):
 unable to open '/lib/modules/5.15.0-47-generic/kernel/sound/soc/codecs/snd-soc-
wsa881x.ko.dpkg-new': Operation not permitted
Selecting previously unselected package intel-microcode.
Preparing to unpack .../2-intel-microcode_3.20220510.0ubuntu0.22.04.1_amd64.deb 
...
Unpacking intel-microcode (3.20220510.0ubuntu0.22.04.1) ...
Selecting previously unselected package amd64-microcode.
Preparing to unpack .../3-amd64-microcode_3.20191218.1ubuntu2_amd64.deb ...
Unpacking amd64-microcode (3.20191218.1ubuntu2) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../4-linux-image-generic_5.15.0.47.47_amd64.deb ...
Unpacking linux-image-generic (5.15.0.47.47) ...
Selecting previously unselected package thermald.
Preparing to unpack .../5-thermald_2.4.9-1ubuntu0.1_amd64.deb ...
Unpacking thermald (2.4.9-1ubuntu0.1) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-66Mu3p/1-linux-modules-extra-5.15.0-47-generic_5.15.0-47.
51_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I Googled error code([https://itsfoss.com/dpkg-returned-an-error-code-1/](https://itsfoss.com/dpkg-returned-an-error-code-1/)) and ran 

```
 sudo apt-get install -f
[sudo] password for heta: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-modules-extra-5.15.0-47-generic
The following NEW packages will be installed:
  linux-modules-extra-5.15.0-47-generic
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
5 not fully installed or removed.
Need to get 0 B/64,0 MB of archives.
After this operation, 353 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 280664 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.15.0-47-generic_5.15.0-47.51_amd64.deb ...
Unpacking linux-modules-extra-5.15.0-47-generic (5.15.0-47.51) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.15.0-47-generic_5.15.0-47.51_amd64.deb (--unpack):
 unable to open '/lib/modules/5.15.0-47-generic/kernel/drivers/net/wireless/intersil/orinoco/orinoco_plx.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.15.0-47-generic_5.15.0-47.51_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
heta@heta-vaio:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-modules-extra-5.15.0-47-generic; however:
  Package linux-modules-extra-5.15.0-47-generic is not installed.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up iucode-tool (2.3.1-1build1) ...
Setting up intel-microcode (3.20220510.0ubuntu0.22.04.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Setting up amd64-microcode (3.20191218.1ubuntu2) ...
update-initramfs: deferring update (trigger activated)
amd64-microcode: microcode will be updated at next boot
Setting up thermald (2.4.9-1ubuntu0.1) ...
Processing triggers for dbus (1.12.20-2ubuntu4) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for initramfs-tools (0.140ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-47-generic
Errors were encountered while processing:
 linux-image-generic
```

[https://ibb.co/YywKKC2]("https://ibb.co/YywKKC2")(view of Software Updater)
Therefore, we return back to same problem I had in another topic.
"The package system is broken.
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

linux-image-generic: Depends: linux-modules-extra-5.15.0-47-generic but it is not installed"

---

### Post by Bashing-om on 2022-09-08
yatski; Well !

> 
linux-image-generic: Depends: linux-modules-extra-5.15.0-47-generic but it is not installed

Curious as to why it is not installed - but fixable :D
-bk-

As you say:
> 
Therefore, we return back to same problem [color=red]I had in another topic.[/color]

 Link back to that thread and I will meet you there to continue to investigate the failure of  linux-modules-extra- to install. We strive to keep the forum tidy.

[INDENT]gots to be a reason[/INDENT]

---

### Post by yatski on 2022-09-09
> **Bashing-om said:**
> 

As you say:

 Link back to that thread and I will meet you there to continue to investigate the failure of  linux-modules-extra- to install. We strive to keep the forum tidy.

[INDENT]gots to be a reason[/INDENT]

Thread is in this link: [https://ubuntuforums.org/showthread.php?t=2478651](https://ubuntuforums.org/showthread.php?t=2478651)

But for some reason Software Updater doesn't show any new updates today, compared to yesterday.. (Don't take me wrong. Its perfectly fine for me. I just fear the 'snowball effect' of not installing one update...)

---

### Post by Bashing-om on 2022-09-09
yatski; Hey 

> 
But for some reason Software Updater doesn't show any new updates today, compared to yesterday.. (Don't take me wrong. Its perfectly fine for me. I just fear the 'snowball effect' of not installing one update...)


Could well be now that all is indeed well :D

However, I have met you in the original kernel thread, there we verify that all is in good stead, or what.

[INDENT]goods things can happen
[/INDENT]

---

