---
title: "ati script wont build hardy heron package issue.."
date: 2008-05-08
forum: New to Ubuntu
---

### Post by scondrel on 2008-05-08
This script does not work for me ([http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide).I](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide).I) get this error output no matter  how perfect i follow the script ..Can someone advise me on how or where do  i go from there ?..Heres my output terminal error:


scondrel@CHAOS:~$ cd ~/Desktop
scondrel@CHAOS:~/Desktop$ sudo apt-get update
[sudo] password for scondrel: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy Release.gpg
Ign [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:1 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy Release
Get:2 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates Release [51.2kB]
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main Packages
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/restricted Packages
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main Sources
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/restricted Sources
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/universe Packages
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/universe Sources
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/multiverse Sources
Get:3 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/main Packages [34.1kB]        
Get:4 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/restricted Packages [14B]     
Get:5 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/main Sources [7871B]          
Get:6 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/restricted Sources [14B]      
Get:7 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/universe Packages [7224B]     
Get:8 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/universe Sources [1131B]      
Get:9 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/multiverse Packages [14B]     
Get:10 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy-updates/multiverse Sources [14B]     
Fetched 102kB in 9s (10.6kB/s)                                                 
Reading package lists... Done
scondrel@CHAOS:~/Desktop$ sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debconf is already the newest version.
linux-headers-2.6.24-16-generic is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 gcc-3.3-base gettext html2text intltool-debian
  libc6-dev libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch
  po-debconf
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  cvs gettext-doc glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
Recommended packages:
  libmail-sendmail-perl libcompress-zlib-perl libmail-box-perl
The following NEW packages will be installed:
  build-essential debhelper dh-make dkms dpkg-dev fakeroot g++ g++-4.2
  gcc-3.3-base gettext html2text intltool-debian libc6-dev libstdc++5
  libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch po-debconf
0 upgraded, 19 newly installed, 0 to remove and 11 not upgraded.
Need to get 11.8MB of archives.
After this operation, 46.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main linux-libc-dev 2.6.24-16.30 [694kB]
Get:2 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [2538kB] 
Get:3 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1217kB]
Get:4 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [3035kB]  
Get:5 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main g++ 4:4.2.3-1ubuntu3 [1446B]     
Get:6 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:7 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main patch 2.5.9-4 [97.8kB]           
Get:8 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main dpkg-dev 1.14.16.6ubuntu3 [559kB]
Get:9 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7070B]
Get:10 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main html2text 1.3.2a-3build2 [91.3kB]
Get:11 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main gettext 0.17-2ubuntu1 [2067kB]  
Get:12 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:13 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main po-debconf 1.0.10 [232kB]       
Get:14 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main debhelper 6.0.4ubuntu1 [516kB]  
Get:15 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main dh-make 0.44ubuntu1 [37.0kB]    
Get:16 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/universe dkms 2.0.19-0ubuntu2 [51.5kB]
Get:17 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/main fakeroot 1.9ubuntu1 [116kB]     
Get:18 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/universe gcc-3.3-base 1:3.3.6-15ubuntu4 [151kB]
Get:19 [http://lc.archive.ubuntu.com](http://lc.archive.ubuntu.com) hardy/universe libstdc++5 1:3.3.6-15ubuntu4 [292kB]
Fetched 11.8MB in 3min56s (49.8kB/s)                                           
Selecting previously deselected package linux-libc-dev.
(Reading database ... 102627 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-16.30_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu3_all.deb) ...
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
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu4_amd64.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu4_amd64.deb) ...
Setting up linux-libc-dev (2.6.24-16.30) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu3) ...
Setting up html2text (1.3.2a-3build2) ...

Setting up gettext (0.17-2ubuntu1) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...

Setting up debhelper (6.0.4ubuntu1) ...
Setting up dh-make (0.44ubuntu1) ...
Setting up dkms (2.0.19-0ubuntu2) ...

Setting up fakeroot (1.9ubuntu1) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu4) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu4) ...

Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu3) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
scondrel@CHAOS:~/Desktop$ sudo rm /usr/src/fglrx-kernel*.deb
[sudo] password for scondrel: 
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory
scondrel@CHAOS:~/Desktop$ sudo sh ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu/hardy
Created directory fglrx-install.HA7645
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.476.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
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
dpkg-buildpackage: source version 2:8.476-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.SD7728/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.SD7728/debian/driver.$i > \
	      /tmp/fglrx.SD7728/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.SD7728/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.SD7728/debian/10fglrx.template > /tmp/fglrx.SD7728/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.SD7728/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.SD7728/debian/fglrx.default /tmp/fglrx.SD7728/debian/fglrx; \
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
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.SD7728/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.SD7728/debian/driver.$i > \
	      /tmp/fglrx.SD7728/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.SD7728/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.SD7728/debian/10fglrx.template > /tmp/fglrx.SD7728/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.SD7728/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.SD7728/debian/fglrx.default /tmp/fglrx.SD7728/debian/fglrx; \
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
		usr/src/fglrx-8.476
dh_install
# Driver package
/sbin/ldconfig -n usr/X11R6/lib/
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
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
echo "PACKAGE_VERSION=\"8.476\"" >> debian/dkms.conf
echo "CLEAN=\"rm -f *.*o\"" >> debian/dkms.conf
echo "BUILT_MODULE_NAME[0]=\"fglrx\"" >> debian/dkms.conf
echo "MAKE[0]=\"pushd \${dkms_tree}/fglrx/8.476/build; sh make.sh --nohints; popd\"" >> debian/dkms.conf
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
		usr/src/fglrx-8.476
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
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.HA7645

---

### Post by bebox on 2008-05-26
> **scondrel said:**
> This script does not work for me 
dpkg-shlibdeps: warning: symbol XauFileName used by debian/xorg-driver-fglrx/usr/sbin/atieventsd found in none of the libraries.
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd shouldn't be linked with libXrender.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libfglrx_gamma.so.1 needed by debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.HA7645

I HAVE THE SAME PROBLEM!!!...please help

---

