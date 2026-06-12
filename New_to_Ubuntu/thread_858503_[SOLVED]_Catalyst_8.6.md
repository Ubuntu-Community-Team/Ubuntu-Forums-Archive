---
title: "[SOLVED] Catalyst 8.6"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-13
Hi everybody.
I am trying to install catalyst 8.6 through this method([http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)).
The problem is while i went through the steps i got this error:
> diastopher@diastopher-desktop:~$ sh ati-driver-installer-8-6-x86.x86_64.run --buildpkg Ubuntu/hardy
Created directory fglrx-install.jN7775
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.501..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/hardy
Package build failed!
Package build utility output:
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.501-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.TP7895/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.TP7895/debian/driver.$i > \
	      /tmp/fglrx.TP7895/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.TP7895/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.TP7895/debian/10fglrx.template > /tmp/fglrx.TP7895/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.TP7895/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.TP7895/debian/fglrx.default /tmp/fglrx.TP7895/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 fakeroot debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.TP7895/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.TP7895/debian/driver.$i > \
	      /tmp/fglrx.TP7895/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.TP7895/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.TP7895/debian/10fglrx.template > /tmp/fglrx.TP7895/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.TP7895/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.TP7895/debian/fglrx.default /tmp/fglrx.TP7895/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
		usr/lib \
		usr/sbin \
		usr/lib \
		usr/lib/xorg/modules \
		usr/lib/xorg/modules/drivers \
		usr/lib/xorg/modules/linux \
		etc/acpi \
		etc/acpi/events \
		etc/default \
		etc/X11/Xsession.d \

# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
		usr/lib32 \
		usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
		usr/bin \
		usr/sbin \
		usr/share \
		usr/share/applnk \
		usr/share/gnome \
		usr/share/gnome/apps \
		usr/share/icons \
		usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
		usr/include \
		usr/lib
dh_installdirs -pfglrx-kernel-source \
		usr/src/fglrx-8.501
dh_install
# Driver package
/sbin/ldconfig -n usr/X11R6/lib/
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/atiodcli" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/atiode" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "etc/ati"                   "etc"
dh_install -pxorg-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
dh_install -pxorg-driver-fglrx "debian/fglrx-powermode.sh" "etc/acpi"
dh_install -pxorg-driver-fglrx "debian/fglrx-*-aticonfig"  "etc/acpi/events"
dh_install -pxorg-driver-fglrx "debian/fglrx"              "etc/default"
dh_installinit -pxorg-driver-fglrx --name="atieventsd"
# Driver dev package
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
#Create dkms.conf
echo "PACKAGE_NAME=\"fglrx\"" > debian/dkms.conf
echo "PACKAGE_VERSION=\"8.501\"" >> debian/dkms.conf
echo "CLEAN=\"rm -f *.*o\"" >> debian/dkms.conf
echo "BUILT_MODULE_NAME[0]=\"fglrx\"" >> debian/dkms.conf
echo "MAKE[0]=\"pushd \${dkms_tree}/fglrx/8.501/build; sh make.sh --nohints; popd\"" >> debian/dkms.conf
echo "DEST_MODULE_LOCATION[0]=\"/kernel/drivers/char/drm\"" >> debian/dkms.conf
echo "AUTOINSTALL=\"yes\"" >> debian/dkms.conf
# Kernel source package
dh_install -pfglrx-kernel-source \
		lib/modules/fglrx/build_mod/*.c            \
		lib/modules/fglrx/build_mod/*.h            \
		lib/modules/fglrx/build_mod/*.sh           \
		lib/modules/fglrx/build_mod/lib*           \
		lib/modules/fglrx/build_mod/2.6.x/Makefile \
		debian/dkms.conf			   \
		usr/src/fglrx-8.501
# control panel package
dh_install -A -pfglrx-amdcccle "usr/X11R6/bin/amdcccle"				"usr/bin"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"				"usr/share/icons"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"				"usr/share/pixmaps"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.desktop"			"usr/share/applications"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.kdelnk"				"usr/share/applnk"
dh_install -A -pfglrx-amdcccle "usr/share/ati"					"usr/share"
dh_desktop    -pfglrx-amdcccle
# start the install
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_installdeb
dh_makeshlibs
dh_shlibdeps
dpkg-shlibdeps: warning: symbol XauFileName used by debian/xorg-driver-fglrx/usr/sbin/atieventsd found in none of the libraries.
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd shouldn't be linked with libXrender.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libfglrx_gamma.so.1 needed by debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.jN7775
diastopher@diastopher-desktop:~$ 


Thanks for your time.

---

### Post by cristo-father on 2008-07-13
bump

---

### Post by cristo-father on 2008-07-13
bump

---

### Post by markbuntu on 2008-07-13
There is a specific fix for the error you encountered in the instructions you were following.

---

### Post by cristo-father on 2008-07-14
> **markbuntu said:**
> There is a specific fix for the error you encountered in the instructions you were following.

Your right, but it still gives me a problem after i do the "Finishing the Install: Configuration" part.
The problem consists of rebooting every time i start ubuntu...i cannot even get my username inserted i just see a orange wallpaper and the cursor of the mouse loading and then it restarts(i have tried running ubuntu several times and it always  happens.) 
Any suggestions?

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by sdowney717 on 2008-07-14
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
have you tried it this way?

---

### Post by cristo-father on 2008-07-14
> **sdowney717 said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
have you tried it this way?

If you pay attention to the first post you will notice that is the link i was following.Thanks anyway.:)

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by LowSky on 2008-07-14
have you used an ATI card before?
have you you've used fglrx previously?
 
you might have to edit your xorg.conf file

---

### Post by cristo-father on 2008-07-14
> **LowSky said:**
> have you used an ATI card before?
no

> **LowSky said:**
> 
have you you've used fglrx previously?
i do not know what that is...

> **LowSky said:**
> 
you might have to edit your xorg.conf file
Editing is the problem. That is why i cannot even run ubuntu...

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by LowSky on 2008-07-14
boot ubuntu in recovery mode from grub
It should come up with a screen asking if you wan to fix xorg or do something else.

if it doesn't and come up to a termial screen type this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and why do you have 3 threads about the same issue?

---

### Post by cristo-father on 2008-07-14
> **LowSky said:**
> boot ubuntu in recovery mode from grub
It should come up with a screen asking if you wan to fix xorg or do something else.

if it doesn't and come up to a termial screen type this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and why do you have 3 threads about the same issue?
I do not have 3 threads about the same issue.
One asks of ways to install drivers, the second asks about how to install catalyst and the last one asks about how to install and where to get open-source drivers.
Three very different questions.

---

### Post by Xerp on 2008-07-14
Have you tried Envy? Works great for me!

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install from Synaptic and away you go...

---

### Post by Zero Prime on 2008-07-14
Envy doesn't install the 8.6 drivers.  It installs the 8.47.3 drivers.

---

### Post by sdowney717 on 2008-07-14
when will envy update the driver install?
Is there an issue with 8.6?

---

### Post by markbuntu on 2008-07-14
You are installing the 64 bit version. It is critical that you follow the special directions for 64 bit install.

Try again, and be sure to follow the direction and use the --force-overwrite command and other 64 bit instructions.

---

### Post by cristo-father on 2008-07-14
Ok. Here is everything i did while installing catalyst.
> HTTP request sent, awaiting response... 200 OK
Length: 60,476,860 (58M) [application/octet-stream]

100%[=================================================================================================================>] 60,476,860     1.42M/s    ETA 00:00

01:52:26 (1.30 MB/s) - `ati-driver-installer-8-6-x86.x86_64.run' saved [60476860/60476860]

diastopher@diastopher-desktop:~$ sudo apt-get install ia32-libs
[sudo] password for diastopher: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386
Suggested packages:
  libasound2-plugins
Recommended packages:
  lib32nss-mdns
The following NEW packages will be installed:
  ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.5MB of archives.
After this operation, 113MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libc6-i386 2.7-10ubuntu3 [3699kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main lib32asound2 1.0.15-3ubuntu4 [317kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main lib32gcc1 1:4.2.3-2ubuntu7 [23.3kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main lib32ncurses5 5.6+20071124-1ubuntu2 [179kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main lib32stdc++6 4.2.3-2ubuntu7 [332kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main lib32z1 1:1.2.3.3.dfsg-7ubuntu1 [74.3kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe ia32-libs 2.2ubuntu11 [20.9MB]
Fetched 25.5MB in 26s (973kB/s)                                                                                                                             
Selecting previously deselected package libc6-i386.
(Reading database ... 95139 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.7-10ubuntu3_amd64.deb) ...
Selecting previously deselected package lib32asound2.
Unpacking lib32asound2 (from .../lib32asound2_1.0.15-3ubuntu4_amd64.deb) ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package lib32ncurses5.
Unpacking lib32ncurses5 (from .../lib32ncurses5_5.6+20071124-1ubuntu2_amd64.deb) ...
Selecting previously deselected package lib32stdc++6.
Unpacking lib32stdc++6 (from .../lib32stdc++6_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package lib32z1.
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3.3.dfsg-7ubuntu1_amd64.deb) ...
Selecting previously deselected package ia32-libs.
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu11_amd64.deb) ...
Setting up libc6-i386 (2.7-10ubuntu3) ...

Setting up lib32asound2 (1.0.15-3ubuntu4) ...

Setting up lib32gcc1 (1:4.2.3-2ubuntu7) ...

Setting up lib32ncurses5 (5.6+20071124-1ubuntu2) ...

Setting up lib32stdc++6 (4.2.3-2ubuntu7) ...

Setting up lib32z1 (1:1.2.3.3.dfsg-7ubuntu1) ...

Setting up ia32-libs (2.2ubuntu11) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
diastopher@diastopher-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
diastopher@diastopher-desktop:~$ sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debconf is already the newest version.
linux-headers-2.6.24-19-generic is already the newest version.
linux-headers-2.6.24-19-generic set to manually installed.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 gcc-3.3-base gettext html2text intltool-debian libc6-dev libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch po-debconf
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg cvs gettext-doc glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
Recommended packages:
  libmail-sendmail-perl libcompress-zlib-perl libmail-box-perl
The following NEW packages will be installed:
  build-essential debhelper dh-make dkms dpkg-dev fakeroot g++ g++-4.2 gcc-3.3-base gettext html2text intltool-debian libc6-dev libstdc++5
  libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch po-debconf
0 upgraded, 19 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.8MB of archives.
After this operation, 46.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-19.34 [695kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [2538kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1217kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [3035kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1450B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]                                                                               
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main patch 2.5.9-4 [97.8kB]                                                                                           
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]                                                                        
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7070B]                                                                              
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main html2text 1.3.2a-3build2 [91.3kB]                                                                               
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main gettext 0.17-2ubuntu1 [2067kB]                                                                                  
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main intltool-debian 0.35.0+20060710.1 [31.6kB]                                                                      
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main po-debconf 1.0.10 [232kB]                                                                                       
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main debhelper 6.0.4ubuntu1 [516kB]                                                                                  
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main dh-make 0.44ubuntu1 [37.0kB]                                                                                    
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe dkms 2.0.19-0ubuntu2 [51.5kB]                                                                               
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main fakeroot 1.9ubuntu1 [116kB]                                                                                     
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe gcc-3.3-base 1:3.3.6-15ubuntu6 [151kB]                                                              
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe libstdc++5 1:3.3.6-15ubuntu6 [292kB]                                                                
Fetched 11.8MB in 8s (1309kB/s)                                                                                                                             
Selecting previously deselected package linux-libc-dev.
(Reading database ... 96409 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.34_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_amd64.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build2_amd64.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-2ubuntu1_amd64.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../dh-make_0.44ubuntu1_all.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.0.19-0ubuntu2_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.9ubuntu1_amd64.deb) ...
Selecting previously deselected package gcc-3.3-base.
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu6_amd64.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu6_amd64.deb) ...
Setting up linux-libc-dev (2.6.24-19.34) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up html2text (1.3.2a-3build2) ...

Setting up gettext (0.17-2ubuntu1) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...

Setting up debhelper (6.0.4ubuntu1) ...
Setting up dh-make (0.44ubuntu1) ...
Setting up dkms (2.0.19-0ubuntu2) ...

Setting up fakeroot (1.9ubuntu1) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu6) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu6) ...

Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
diastopher@diastopher-desktop:~$ sh ati-driver-installer-8-6-x86.x86_64.run --buildpkg Ubuntu/hardy
Created directory fglrx-install.bz8498
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.501..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/hardy
Package build failed!
Package build utility output:
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.501-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.lz8618/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.lz8618/debian/driver.$i > \
	      /tmp/fglrx.lz8618/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.lz8618/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.lz8618/debian/10fglrx.template > /tmp/fglrx.lz8618/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.lz8618/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.lz8618/debian/fglrx.default /tmp/fglrx.lz8618/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 fakeroot debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.lz8618/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.lz8618/debian/driver.$i > \
	      /tmp/fglrx.lz8618/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.lz8618/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.lz8618/debian/10fglrx.template > /tmp/fglrx.lz8618/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.lz8618/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.lz8618/debian/fglrx.default /tmp/fglrx.lz8618/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
		usr/lib \
		usr/sbin \
		usr/lib \
		usr/lib/xorg/modules \
		usr/lib/xorg/modules/drivers \
		usr/lib/xorg/modules/linux \
		etc/acpi \
		etc/acpi/events \
		etc/default \
		etc/X11/Xsession.d \

# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
		usr/lib32 \
		usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
		usr/bin \
		usr/sbin \
		usr/share \
		usr/share/applnk \
		usr/share/gnome \
		usr/share/gnome/apps \
		usr/share/icons \
		usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
		usr/include \
		usr/lib
dh_installdirs -pfglrx-kernel-source \
		usr/src/fglrx-8.501
dh_install
# Driver package
/sbin/ldconfig -n usr/X11R6/lib/
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/atiodcli" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/atiode" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "etc/ati"                   "etc"
dh_install -pxorg-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
dh_install -pxorg-driver-fglrx "debian/fglrx-powermode.sh" "etc/acpi"
dh_install -pxorg-driver-fglrx "debian/fglrx-*-aticonfig"  "etc/acpi/events"
dh_install -pxorg-driver-fglrx "debian/fglrx"              "etc/default"
dh_installinit -pxorg-driver-fglrx --name="atieventsd"
# Driver dev package
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
#Create dkms.conf
echo "PACKAGE_NAME=\"fglrx\"" > debian/dkms.conf
echo "PACKAGE_VERSION=\"8.501\"" >> debian/dkms.conf
echo "CLEAN=\"rm -f *.*o\"" >> debian/dkms.conf
echo "BUILT_MODULE_NAME[0]=\"fglrx\"" >> debian/dkms.conf
echo "MAKE[0]=\"pushd \${dkms_tree}/fglrx/8.501/build; sh make.sh --nohints; popd\"" >> debian/dkms.conf
echo "DEST_MODULE_LOCATION[0]=\"/kernel/drivers/char/drm\"" >> debian/dkms.conf
echo "AUTOINSTALL=\"yes\"" >> debian/dkms.conf
# Kernel source package
dh_install -pfglrx-kernel-source \
		lib/modules/fglrx/build_mod/*.c            \
		lib/modules/fglrx/build_mod/*.h            \
		lib/modules/fglrx/build_mod/*.sh           \
		lib/modules/fglrx/build_mod/lib*           \
		lib/modules/fglrx/build_mod/2.6.x/Makefile \
		debian/dkms.conf			   \
		usr/src/fglrx-8.501
# control panel package
dh_install -A -pfglrx-amdcccle "usr/X11R6/bin/amdcccle"					"usr/bin"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"					"usr/share/icons"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"					"usr/share/pixmaps"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.desktop"				"usr/share/applications"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.kdelnk"					"usr/share/applnk"
dh_install -A -pfglrx-amdcccle "usr/share/ati"							"usr/share"
dh_desktop    -pfglrx-amdcccle
# start the install
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_installdeb
dh_makeshlibs
dh_shlibdeps
dpkg-shlibdeps: warning: symbol XauFileName used by debian/xorg-driver-fglrx/usr/sbin/atieventsd found in none of the libraries.
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd shouldn't be linked with libXrender.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libfglrx_gamma.so.1 needed by debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.bz8498
diastopher@diastopher-desktop:~$ sudo sh ati-driver-installer-8-6-x86.x86_64.run --extract driver
Creating directory driver
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.501..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
diastopher@diastopher-desktop:~$ cd driver/arch/x86_64/usr/X11R6/lib64
diastopher@diastopher-desktop:~/driver/arch/x86_64/usr/X11R6/lib64$ sudo ln -s libfglrx_gamma.so.1.0 libfglrx_gamma.so.1
diastopher@diastopher-desktop:~/driver/arch/x86_64/usr/X11R6/lib64$ cd ../../../../../
diastopher@diastopher-desktop:~/driver$ sudo sh ati-installer.sh -- --buildpkg Ubuntu/hardy
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/hardy
Package /home/diastopher/xorg-driver-fglrx_8.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/diastopher/xorg-driver-fglrx-dev_8.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/diastopher/fglrx-kernel-source_8.501-0ubuntu1_amd64.deb has been successfully generated
Package /home/diastopher/fglrx-amdcccle_8.501-0ubuntu1_amd64.deb has been successfully generated
diastopher@diastopher-desktop:~/driver$ cd
diastopher@diastopher-desktop:~$ sudo gedit /etc/default/linux-restricted-modules-common
diastopher@diastopher-desktop:~$ sudo gedit /etc/default/linux-restricted-modules-common
diastopher@diastopher-desktop:~$ sudo gedit /etc/default/linux-restricted-modules-common
diastopher@diastopher-desktop:~$ sudo gedit /etc/modprobe.d/blacklist-restricted
diastopher@diastopher-desktop:~$ sudo gedit /etc/modprobe.d/blacklist-local
diastopher@diastopher-desktop:~$ sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 99008 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.501-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.501-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.501-0ubuntu1_amd64.deb) ...
Setting up xorg-driver-fglrx (2:8.501-0ubuntu1) ...
 * Starting atieventsd                                                                                                                                [ OK ] 

Setting up fglrx-kernel-source (2:8.501-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up fglrx-amdcccle (2:8.501-0ubuntu1) ...

diastopher@diastopher-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
diastopher@diastopher-desktop:~$ sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.501*.deb fglrx-kernel-source_8.501-0*.deb fglrx-amdcccle_8.501-0*.deb
(Reading database ... 99169 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 2:8.501-0ubuntu1 (using xorg-driver-fglrx_8.501-0ubuntu1_amd64.deb) ...
 * Stopping atieventsd                                                                                                                                [ OK ] 
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace fglrx-kernel-source 2:8.501-0ubuntu1 (using fglrx-kernel-source_8.501-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-amdcccle 2:8.501-0ubuntu1 (using fglrx-amdcccle_8.501-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Setting up xorg-driver-fglrx (2:8.501-0ubuntu1) ...
 * Starting atieventsd                                                                                                                                [ OK ] 

Setting up fglrx-kernel-source (2:8.501-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up fglrx-amdcccle (2:8.501-0ubuntu1) ...

diastopher@diastopher-desktop:~$ sudo gedit /etc/X11/xorg.conf
No protocol specified
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.
diastopher@diastopher-desktop:~$ gksudo gedit /etc/X11/xorg.conf
No protocol specified

(gksudo:26329): Gtk-WARNING **: cannot open display: :0.0
diastopher@diastopher-desktop:~$ 

After this i logout because i cannot open gedit.
I logon and the restricted driver icon pops up and says: Device driver ati. Enabled not ticked .Status not in use.
So lets contine.

> 
diastopher@diastopher-desktop:~$ sudo gedit /etc/X11/xorg.conf
diastopher@diastopher-desktop:~$ sudo aticonfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
diastopher@diastopher-desktop:~$ sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
Warning: Option 'UseFastTLS' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
diastopher@diastopher-desktop:~$ 


After this i reboot just like instructed that is when if i boot normally i cannot enter ubuntu.
To solve this i go into recovery mode --> recovery menu --> xfix --> cancel.
After i do this i noticed two intresting consequences.
1.Restricted drivers status chages to in use.
2.xorg.conf does not have the line i typed in anymore.

> 
diastopher@diastopher-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)


I do not understand the second chance for removing mesa, but having in mind the first and the third i conclude none of them apply.
My output is 2.6.24 when inserting uname -r and i do not have xserver-xgl installed so i cannot remove it.
I am really lost....Help me....

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-15
bump

---

### Post by cristo-father on 2008-07-15
bump

---

### Post by cristo-father on 2008-07-15
bump

---

### Post by cristo-father on 2008-07-15
bump

---

### Post by cristo-father on 2008-07-15
bump

---

### Post by Canis familiaris on 2008-07-15
(1) Passed the commands
```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r` 
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```
(2) Make sure the the drivers are installed. Preferably reinstall it.
(3) Set it up.
```
sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768
```

Another thing: Do not BUMP your thread so many times, some moderator may catch that and give you an infraction. At least do not bump before 12 hours of your last post. In fact you should not bump the thread till 24 hours of your last post.

---

### Post by cristo-father on 2008-07-15
> **Anurag_panda said:**
> (1) Passed the commands
```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r` 
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```
(2) Make sure the the drivers are installed. Preferably reinstall it.
(3) Set it up.
```
sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768
```

Another thing: Do not BUMP your thread so many times, some moderator may catch that and give you an infraction. At least do not bump before 12 hours of your last post. In fact you should not bump the thread till 24 hours of your last post.

Here is what i did. Please keep in mind that it is not the first time i did this.

```
diastopher@diastopher-desktop:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r` 
[sudo] password for diastopher: 
diastopher@diastopher-desktop:~$ sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: error inserting '/lib/modules/2.6.24-19-generic/volatile/fglrx.ko': -1 File exists
diastopher@diastopher-desktop:~$ sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768
Found fglrx primary device section
error at set screen resolution : screen0 does not exist
aticonfig: parsing the command-line failed.
diastopher@diastopher-desktop:~$ 
```

After that i restarted and the following message appeared.

```
Ubuntu is running in low-graphics mode.

Your screen and graphics card could not be detected correctly.
To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself.
```

I pressed continue and noticed some changes.

1. Resolution is crappy.
2.Enabled is now ticked in the hardware drivers in administration.
3.xorg.conf now looks like this:
```
Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection
```
4.```
diastopher@diastopher-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

diastopher@diastopher-desktop:~$ 

```
5.```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="fglrx"
```

I am really lost...

---

### Post by Canis familiaris on 2008-07-15
WHich graphics card do you use?

If you dont know exactly post the o/p of:
```
lspci | grep VGA
```

---

### Post by cristo-father on 2008-07-15
Hd4850

---

### Post by Canis familiaris on 2008-07-15
At Ubuntu Wiki I noticed
> Make sure fglrx is not disabled in the DISABLED_MODULES part: kdesu kate /etc/default/linux-restricted-modules-common.

I suggest you remove that **DISABLED_MODULES="fglrx"** in that last file. Just comment it out by #.

Generate a new set of module dependencies so the fglrx driver starts properly. 

```
sudo depmod -a
```

Configure your ATi:
```
sudo aticonfig --initial
```
```
sudo aticonfig --overlay-type=Xv
```

Hope this helps.

---

### Post by cristo-father on 2008-07-15
> **Anurag_panda said:**
> At Ubuntu Wiki I noticed


I suggest you remove that **DISABLED_MODULES="fglrx"** in that last file. Just comment it out by #.

Generate a new set of module dependencies so the fglrx driver starts properly. 

```
sudo depmod -a
```

Configure your ATi:
```
sudo aticonfig --initial
```
```
sudo aticonfig --overlay-type=Xv
```

Hope this helps.

Here is the file without that line.
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

```

And this is the what the terminal says:
```
diastopher@diastopher-desktop:~$ sudo depmod -a
[sudo] password for diastopher: 
diastopher@diastopher-desktop:~$ sudo aticonfig --initial
Found fglrx primary device section
Using xorg.conf
Saved back-up to xorg.conf.fglrx-1
diastopher@diastopher-desktop:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using xorg.conf
Saved back-up to xorg.conf.fglrx-2
diastopher@diastopher-desktop:~$ 

```

I am gonna restart(my pc)...wish me luck.

After restarting....

I do not see any difference...

---

### Post by Canis familiaris on 2008-07-15
Can you change to a higher resolution:
System->Preferences->Screen Resolution

---

### Post by cristo-father on 2008-07-15
> **Anurag_panda said:**
> Can you change to a higher resolution:
System->Preferences->Screen Resolution
Max is 800x600.

---

### Post by Canis familiaris on 2008-07-15
Does fglrx still gives you Mesa as renderer?

Try this command again:
```
sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768
```

---

### Post by cristo-father on 2008-07-15
> **Anurag_panda said:**
> Does fglrx still gives you Mesa as renderer?

Try this command again:
```
sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768
```

Here are the results.
```
diastopher@diastopher-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

diastopher@diastopher-desktop:~$ sudo aticonfig --initial --input=/etc/X11/xorg.conf --resolution=0,1024x768
Found fglrx primary device section
error at set screen resolution : screen0 does not exist
aticonfig: parsing the command-line failed.
diastopher@diastopher-desktop:~$ 

```

---

### Post by Canis familiaris on 2008-07-15
Sorry! I have run out of ideas. :(

Perhaps try reinstalling Ubuntu and trying that guide again? Or try another distro.

---

### Post by cristo-father on 2008-07-15
> **Anurag_panda said:**
> Sorry! I have run out of ideas. :(

Perhaps try reinstalling Ubuntu and trying that guide again? Or try another distro.

Thanks for trying. What distro do you recommend?

---

### Post by Canis familiaris on 2008-07-15
> **cristo-father said:**
> Thanks for trying. What distro do you recommend?
I think installer of ATi can be run by double clicking in SuSE. I am not very sure. But try SuSE. It is more bloated and resource intensive but conversely has lots of features.

---

### Post by cristo-father on 2008-07-15
> **Anurag_panda said:**
> I think installer of ATi can be run by double clicking in SuSE. I am not very sure. But try SuSE. It is more bloated and resource intensive but conversely has lots of features.

Well...i guess it is good bye ubuntu and welcome opensuse 11.
Thanks everybody.

---

### Post by Canis familiaris on 2008-07-15
> **cristo-father said:**
> Well...i guess it is good bye ubuntu and welcome opensuse 11.
Thanks everybody.
Try Ubuntu again when its next version come out in October. i.e. Intrepid Ibex.

---

### Post by cristo-father on 2008-07-15
> **Anurag_panda said:**
> Try Ubuntu again when its next version come out in October. i.e. Intrepid Ibex.

Lol it is my birthmonth(if you know what i mean) present.
I already have tried opensuse, but i prefer ubuntu for two main reasons apt-get and the community.

---

### Post by markbuntu on 2008-07-15
I had a lot of trouble with mesa and my ati cards when I first unstalled Ubuntu. Eventually, after weeks of trying everything, the only way I could solve the problem was to do a new clean Ubuntu install and immediately get the ATI driver and install it.
Since then it has worked great on both my 32 bit and 64 bit installs.

I asked how to remove mesa without removing all its debs but never got an answer because when you go to remove mesa it wants to remove almost every graphical program on the system due to dependency issues. A clean install just seemed far easier.

---

### Post by cristo-father on 2008-07-15
> **markbuntu said:**
> 
I asked how to remove mesa without removing all its debs but never got an answer because when you go to remove mesa it wants to remove almost every graphical program on the system due to dependency issues.

How do i remove mesa(do not care if the debs come along:lolflag:)?

---

### Post by cristo-father on 2008-07-26
8.7 works.

---

