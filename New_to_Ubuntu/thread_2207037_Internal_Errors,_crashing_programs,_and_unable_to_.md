---
title: "Internal Errors, crashing programs, and unable to update or fix dependencies"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by DanHS on 2014-02-21
I had almost identical problems with 12.10 on this computer a while ago, if I recall correctly upgrading to 13 solved it for a while, or I reinstalled 12.10 and then upgraded, don't really remember. Either way, it worked fine until the other night programs suddenly began crashing, error messages began popping up en mass, and updates won't work. When I boot up the computer I get a slew of error messages, and trying to send error reports produces more error messages. I was even getting the little boxes that just said "permission denied"

I've got the little red circle with white line up in the status bar, that says "An error occured, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'. This usually means your installed packages have unmet dependencies"

Software Updater gives me the following message: "the package system is broken. Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"


If I run apt-get install -f I get all this:
```
redbone@redbone-MS-7695:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bluez-alsa:i386 glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386
  gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386 gtk2-engines-oxygen:i386
  gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ibus-gtk:i386 libaa1:i386 libaio1:i386 libao4:i386
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386
  libaudio2:i386 libaudiofile1:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libavc1394-0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386
  libcanberra-gtk0:i386 libcanberra0:i386 libcapi20-3:i386 libcdparanoia0:i386 libcroco3:i386 libcups2:i386
  libcupsfilters1:i386 libcupsimage2:i386 libcurl3:i386 libdatrie1:i386 libdbus-glib-1-2:i386 libdv4:i386
  libesd0:i386 libexif12:i386 libflac8:i386 libfluidsynth1:i386 libfontconfig1:i386 libfreetype6:i386
  libgail-common:i386 libgail18:i386 libgconf-2-4:i386 libgcrypt11:i386 libgd3:i386 libgdbm3:i386
  libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libglib2.0-0:i386 libglu1-mesa:i386 libgnutls26:i386
  libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-port10:i386 libgraphite2-3:i386 libgssapi-krb5-2:i386
  libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk2.0-0:i386
  libgudev-1.0-0:i386 libharfbuzz0a:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libibus-1.0-5:i386 libice6:i386 libicu48:i386
  libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjasper1:i386 libjbig0:i386
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386
  libmng1:i386 libmpg123-0:i386 libmysqlclient18:i386 libnspr4:i386 libnss3:i386 libodbc1:i386 libogg0:i386
  libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpango1.0-0:i386
  libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpangox-1.0-0:i386 libpangoxft-1.0-0:i386
  libpixman-1-0:i386 libproxy1:i386 libpulse-mainloop-glib0:i386 libpulse0:i386 libpulsedsp:i386
  libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386 libqt4-network:i386 libqt4-opengl:i386
  libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386
  libqtwebkit4:i386 libraw1394-11:i386 libreadline6:i386 libroken18-heimdal:i386 librsvg2-2:i386
  librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386
  libsdl1.2debian:i386 libsecret-1-0:i386 libshout3:i386 libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386
  libsoup2.4-1:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386
  libstdc++5:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtasn1-3:i386 libtdb1:i386 libthai0:i386
  libtheora0:i386 libtiff5:i386 libunistring0:i386 libusb-0.1-4:i386 libusb-1.0-0:i386 libv4l-0:i386
  libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvorbisfile3:i386 libvpx1:i386 libwavpack1:i386 libwebp4:i386 libwind0-heimdal:i386 libwrap0:i386
  libxaw7:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386 libxft2:i386
  libxi6:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386 libxpm4:i386 libxrandr2:i386
  libxrender1:i386 libxslt1.1:i386 libxss1:i386 libxt6:i386 libxtst6:i386 libxv1:i386 mysql-common odbcinst
  odbcinst1debian2 odbcinst1debian2:i386 openjdk-7-jre-lib xaw3dg:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.11.0-17 linux-headers-3.11.0-17-generic linux-image-3.11.0-17-generic
  linux-image-extra-3.11.0-17-generic
Suggested packages:
  fdutils linux-doc-3.11.0 linux-source-3.11.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.11.0-17 linux-headers-3.11.0-17-generic linux-image-3.11.0-17-generic
  linux-image-extra-3.11.0-17-generic
0 upgraded, 4 newly installed, 0 to remove and 13 not upgraded.
3 not fully installed or removed.
Need to get 0 B/62.0 MB of archives.
After this operation, 259 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Sub-process gzip returned an error code (1)
E: Prior errors apply to /var/cache/apt/archives/linux-headers-3.11.0-17-generic_3.11.0-17.31_amd64.deb
debconf: apt-extracttemplates failed: No such file or directory
(Reading database ... 224940 files and directories currently installed.)
Unpacking linux-image-3.11.0-17-generic (from .../linux-image-3.11.0-17-generic_3.11.0-17.31_amd64.deb) ...
Done.
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-image-3.11.0-17-generic_3.11.0-17.31_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.11.0-17-generic' to '/boot/vmlinuz-3.11.0-17-generic.dpkg-new': unexpected end of file or stream
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
Unpacking linux-image-extra-3.11.0-17-generic (from .../linux-image-extra-3.11.0-17-generic_3.11.0-17.31_amd64.deb) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-image-extra-3.11.0-17-generic_3.11.0-17.31_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
                                                                                         Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
Unpacking linux-headers-3.11.0-17 (from .../linux-headers-3.11.0-17_3.11.0-17.31_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.11.0-17_3.11.0-17.31_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: invalid literal/lengths set'
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
dpkg-deb: error: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-headers-3.11.0-17-generic_3.11.0-17.31_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.11.0-17-generic_3.11.0-17.31_amd64.deb
 /var/cache/apt/archives/linux-image-extra-3.11.0-17-generic_3.11.0-17.31_amd64.deb
 /var/cache/apt/archives/linux-headers-3.11.0-17_3.11.0-17.31_all.deb
 /var/cache/apt/archives/linux-headers-3.11.0-17-generic_3.11.0-17.31_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What do I need to do to get usable files to fix this? I'm not great with code, so walk me though everything please, if you have any ideas for a solution. Would I be better off just downloading a new 13.10 iso and reinstalling, again?

---

### Post by ian-weisser on 2014-02-21
I don't see any need to reinstall.
The error messages seem quite straightforward.

Your 3.11.0-17 kernel packages are corrupt, so they won't install.
>  /var/cache/apt/archives/linux-image-3.11.0-17-generic_3.11.0-17.31_amd64.deb
 /var/cache/apt/archives/linux-image-extra-3.11.0-17-generic_3.11.0-17.31_amd64.deb
 /var/cache/apt/archives/linux-headers-3.11.0-17_3.11.0-17.31_all.deb
 /var/cache/apt/archives/linux-headers-3.11.0-17-generic_3.11.0-17.31_amd64.deb
Delete them so the system is forced to re-download them.

A more important question would be *why are my kernel packages corrupt*?
Your description of your previous problems are not detailed enough to be useful for a diagnosis, but if you are having massive corruption regularly there are only three possible causes: Either you are doing something you shouldn't (user error), or you are installing something you shouldn't (software error), or your machine is broken (hardware error).

I don't see any sofware error here - indeed, the software is working very hard to tell you exactly what the problem is. Exactly what it is supposed to do.

If it happens again, please let us know early, before the system seems on the verge of collapse.


As an irrelevant aside, you seem to have a tremendous number of orphaned packages you should probably remove.
> The following packages were automatically installed and are no longer required:
      [huge list]
Use 'apt-get autoremove' to remove them.
Remember to use 'sudo' when you use autoremove.

---

