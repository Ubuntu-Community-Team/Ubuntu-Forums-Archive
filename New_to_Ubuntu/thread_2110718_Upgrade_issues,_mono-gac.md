---
title: "Upgrade issues, mono-gac"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by inTrouble on 2013-01-31
Hello everybody,

I was afraid to upgrade my system for the longest time and finally decided now or never. Not a good idea. I wanted to upgrade from 10.10 to 12.10, taking one upgrade at the time. Things went wrong right away with a package not being installed correctly which was mono-gac. The machine didn't boot up into the new desktop. When I finally got it there, i started the next upgrade to 11.10 and then 12.04. Every time the system complained that mono-gac wasn't installed correctly because of dependency issues. I tried to reinstall mono with synaptic manager but that didn't work either. Anybody here to help?
Thanks.

---

### Post by inTrouble on 2013-02-04
Bump

---

### Post by omeomi on 2013-02-04
Could you provide a bit more information? What is the precise error you get? Which dependecies are missing? Have you tried reinstalling those dependencies?

---

### Post by inTrouble on 2013-02-06
Hello omeoni,
here is the error I get when trying to install packages.
I tried installing the mono packages from the Synaptics Package Manager but it fails.
And something else is strange: when I install programs from the Ubuntu Software Center, I get the message that the install failed. But when I check, the programs are installed and working.


installArchives() failed: 
Extracting templates from packages: 90% 
Extracting templates from packages: 100% 

Extracting templates from packages: 90% 
Extracting templates from packages: 100% 

Extracting templates from packages: 90% 
Extracting templates from packages: 100% 

Extracting templates from packages: 90% 
Extracting templates from packages: 100% 
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 66200 package 'virtualbox-3.0': 
 error in Version string '3.0.14-58977_Ubuntu_jaunty': invalid character in revision number 
Selecting previously unselected package libaacs0. 
(Reading database ... 
(Reading database ... 5% 
(Reading database ... 10% 
(Reading database ... 15% 
(Reading database ... 20% 
(Reading database ... 25% 
(Reading database ... 30% 
(Reading database ... 35% 
(Reading database ... 40% 
(Reading database ... 45% 
(Reading database ... 50% 
(Reading database ... 55% 
(Reading database ... 60% 
(Reading database ... 65% 
(Reading database ... 70% 
(Reading database ... 75% 
(Reading database ... 80% 
(Reading database ... 85% 
(Reading database ... 90% 
(Reading database ... 95% 
(Reading database ... 100% 
(Reading database ... 322283 files and directories currently installed.) 
Unpacking libaacs0 (from .../libaacs0_0.3.0-4_i386.deb) ... 
Selecting previously unselected package libbluray1. 
Unpacking libbluray1 (from .../libbluray1_1%3a0.2.1+git20111208.63e308d-3_i386.deb) ... 
Selecting previously unselected package libebml3. 
Unpacking libebml3 (from .../libebml3_1.2.2-2_i386.deb) ... 
Selecting previously unselected package libsdl-image1.2. 
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.10-3_i386.deb) ... 
Selecting previously unselected package libva-x11-1. 
Unpacking libva-x11-1 (from .../libva-x11-1_1.0.15-4_i386.deb) ... 
Selecting previously unselected package libxcb-composite0. 
Unpacking libxcb-composite0 (from .../libxcb-composite0_1.8.1-1ubuntu0.1_i386.deb) ... 
Selecting previously unselected package libxcb-randr0. 
Unpacking libxcb-randr0 (from .../libxcb-randr0_1.8.1-1ubuntu0.1_i386.deb) ... 
Selecting previously unselected package libxcb-xv0. 
Unpacking libxcb-xv0 (from .../libxcb-xv0_1.8.1-1ubuntu0.1_i386.deb) ... 
Selecting previously unselected package libass4. 
Unpacking libass4 (from .../libass4_0.10.0-3_i386.deb) ... 
Selecting previously unselected package libcddb2. 
Unpacking libcddb2 (from .../libcddb2_1.3.2-3fakesync1_i386.deb) ... 
Selecting previously unselected package libcrystalhd3. 
Unpacking libcrystalhd3 (from .../libcrystalhd3_1%3a0.0~git20110715.fdd2f19-4.1_i386.deb) ... 
Selecting previously unselected package libdirectfb-1.2-9. 
Unpacking libdirectfb-1.2-9 (from .../libdirectfb-1.2-9_1.2.10.0-4.3ubuntu1_i386.deb) ... 
Selecting previously unselected package libdvbpsi7. 
Unpacking libdvbpsi7 (from .../libdvbpsi7_0.2.2-1_i386.deb) ... 
Selecting previously unselected package libiso9660-8. 
Unpacking libiso9660-8 (from .../libiso9660-8_0.83-1_i386.deb) ... 
Selecting previously unselected package libmatroska5. 
Unpacking libmatroska5 (from .../libmatroska5_1.3.0-1_i386.deb) ... 
Selecting previously unselected package libmodplug1. 
Unpacking libmodplug1 (from .../libmodplug1_1%3a0.8.8.4-1_i386.deb) ... 
Selecting previously unselected package libmpcdec6. 
Unpacking libmpcdec6 (from .../libmpcdec6_2%3a0.1~r459-1ubuntu1_i386.deb) ... 
Selecting previously unselected package libresid-builder0c2a. 
Unpacking libresid-builder0c2a (from .../libresid-builder0c2a_2.1.1-12_i386.deb) ... 
Selecting previously unselected package libsidplay2. 
Unpacking libsidplay2 (from .../libsidplay2_2.1.1-12_i386.deb) ... 
Selecting previously unselected package libtar0. 
Unpacking libtar0 (from .../libtar0_1.2.11-8_i386.deb) ... 
Selecting previously unselected package libvcdinfo0. 
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-4.1ubuntu1_i386.deb) ... 
Selecting previously unselected package vlc-data. 
Unpacking vlc-data (from .../vlc-data_2.0.5-0ubuntu0.12.04.1_all.deb) ... 
dpkg: warning: unable to delete old directory '/etc/vlc/http': Directory not empty 
Selecting previously unselected package libvlccore5. 
Unpacking libvlccore5 (from .../libvlccore5_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Selecting previously unselected package libvlc5. 
Unpacking libvlc5 (from .../libvlc5_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Selecting previously unselected package libzvbi-common. 
Unpacking libzvbi-common (from .../libzvbi-common_0.2.33-4_all.deb) ... 
Selecting previously unselected package libzvbi0. 
Unpacking libzvbi0 (from .../libzvbi0_0.2.33-4_i386.deb) ... 
Selecting previously unselected package libdca0. 
Unpacking libdca0 (from .../libdca0_0.0.5-5_i386.deb) ... 
Selecting previously unselected package libupnp3. 
Unpacking libupnp3 (from .../libupnp3_1%3a1.6.6-5.1_i386.deb) ... 
Selecting previously unselected package vlc-nox. 
Unpacking vlc-nox (from .../vlc-nox_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Selecting previously unselected package libxcb-keysyms1. 
Unpacking libxcb-keysyms1 (from .../libxcb-keysyms1_0.3.8-1build1_i386.deb) ... 
Selecting previously unselected package vlc. 
Unpacking vlc (from .../vlc_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Selecting previously unselected package vlc-plugin-notify. 
Unpacking vlc-plugin-notify (from .../vlc-plugin-notify_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Selecting previously unselected package vlc-plugin-pulse. 
Unpacking vlc-plugin-pulse (from .../vlc-plugin-pulse_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for menu ... 
Setting up mono-gac (2.10.8.1-1ubuntu2.2) ... 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.atk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gdk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.10.glade-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.10.glib-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gtk-dotnet.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gtk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.pango-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.atk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gdk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.4.glade-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.4.glib-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gtk-dotnet.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gtk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.pango-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.atk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gdk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.6.glade-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.6.glib-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.pango-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.atk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gdk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.8.glade-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.8.glib-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gtk-dotnet.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gtk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.pango-sharp.dll does not exist 
dpkg: error processing mono-gac (--configure): 
 subprocess installed post-installation script returned error exit status 3 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of mono-runtime: 
 mono-runtime depends on mono-gac (= 2.10.8.1-1ubuntu2.2); however: 
  Package mono-gac is not configured yet. 
dpkg: error processing mono-runtime (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-corlib2.0-cil: 
 libmono-corlib2.0-cil depends on mono-runtime (>= 2.10.8.1); however:No apport report written because MaxReports is reached already 

  Package mono-runtime is not configured yet. 
 libmono-corlib2.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-corlib2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-cairo2.0-cil: 
 libmono-cairo2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
No apport report written because MaxReports is reached already 
  Package libmono-corlib2.0-cil is not configured yet. 
dpkg: error processing libmono-cairo2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-posix2.0-cil: 
 libmono-posix2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-posix2.0-cil depends on mono-runtime (>= 2.10.1); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-posix2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-system2.0-cil: 
 libmono-system2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-system2.0-cil depends on libmono-posix2.0-cil (>= 2.4); however: 
  Package libmono-posix2.0-cil is not configured yet. 
 libmono-system2.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
 libmono-system2.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-system2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-security2.0-cil: 
 libmono-security2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however:No apport report written because MaxReports is reached already 

  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-security2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-security2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-data-tds2.0-cil: 
 libmono-data-tds2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-data-tds2.0-cil depends on libmono-security2.0-cil (>= 2.6.7); however: 
  Package libmono-security2.0-cil is not configured yet. 
 libmono-data-tds2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-data-tds2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-i18n-west2.0-cil: 
No apport report written because MaxReports is reached already 
 libmono-i18n-west2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
dpkg: error processing libmono-i18n-west2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-i18n4.0-cil: 
 libmono-i18n4.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
No apport report written because MaxReports is reached already 
 libmono-i18n4.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-i18n4.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-i18n-west4.0-cil: 
 libmono-i18n-west4.0-cil depends on libmono-i18n4.0-cil (>= 1.0); however: 
  Package libmono-i18n4.0-cil is not configured yet. 
dpkg: error processing libmono-i18n-west4.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-i18n2.0-cil: 
 libmono-i18n2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-i18n2.0-cil depends on libmono-i18n-west2.0-cil (>= 1.0); however: 
  Package libmono-i18n-west2.0-cil is not configured yet. 
 libmono-i18n2.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
 libmono-i18n2.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-i18n2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-messaging2.0-cil: 
 libmono-messaging2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-messaging2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-messaging2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-sharpzip2.84-cil: 
 libmono-sharpzip2.84-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-sharpzip2.84-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-sharpzip2.84-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-system-data2.0-cil: 
 libmono-system-data2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-system-data2.0-cil depends on libmono-data-tds2.0-cil (>= 1.0); however: 
  Package libmono-data-tds2.0-cil is not configured yet. 
 libmono-system-data2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-system-data2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-sqlite2.0-cil: 
 libmono-sqlite2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-sqlite2.0-cil depends on libmono-system-data2.0-cil (>= 2.6.3); however: 
  Package libmono-system-data2.0-cil is not configured yet. 
 libmono-sqlite2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-sqlite2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-system-messaging2.0-cil: 
 libmono-system-messaging2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-system-messaging2.0-cil depends on libmono-messaging2.0-cil (>= 1.0); however: 
  Package libmono-messaging2.0-cil is not configured yet. 
 libmono-system-messaging2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-system-messaging2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-system-data-linq2.0-cil: 
No apport report written because MaxReports is reached already 
 libmono-system-data-linq2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-system-data-linq2.0-cil depends on libmono-system-data2.0-cil (>= 2.6.3); however: 
  Package libmono-system-data2.0-cil is not configured yet. 
 libmono-system-data-linq2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-system-data-linq2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono2.0-cil: 
 libmono2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono2.0-cil depends on libmono-security2.0-cil (>= 2.6.7); however: 
  Package libmono-security2.0-cil is not configured yet. 
 libmono2.0-cil depends on libmono-sharpzip2.84-cil (>= 1.0); however: 
  Package libmono-sharpzip2.84-cil is not configured yet. 
 libmono2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-system-web2.0-cil: 
 libmono-system-web2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-system-web2.0-cil depends on libmono-sqlite2.0-cil (>= 2.10.7); however: 
  Package libmono-sqlite2.0-cil is not configured yet. 
 libmono-system-web2.0-cil depends on libmono-system-data-linq2.0-cil (>= 1.0); however: 
  Package libmono-system-data-linq2.0-cil is not configured yet. 
 libmono-system-web2.0-cil depends on libmono-system-data2.0-cil (>= 2.6.3); however: 
  Package libmono-system-data2.0-cil is not configured yet. 
 libmono-system-web2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
 libmono-system-web2.0-cil depends on libmono2.0-cil (>= 2.6.3); however: 
  Package libmono2.0-cil is not configured yet. 
 libmono-system-web2.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
 libmono-system-web2.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-system-web2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of libmono-wcf3.0-cil: 
 libmono-wcf3.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-wcf3.0-cil depends on libmono-security2.0-cil (>= 2.6.7); however: 
  Package libmono-security2.0-cil is not configured yet. 
 libmono-wcf3.0-cil depends on libmono-system-messaging2.0-cil (>= 2.6.3); however: 
  Package libmono-system-messaging2.0-cil is not configured yet. 
 libmono-wcf3.0-cil depends on libmono-system-web2.0-cil (>= 2.10.3); however: 
  Package libmono-system-web2.0-cil is not configured yet. 
 libmono-wcf3.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-wcf3.0-cil (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already 
dpkg: dependency problems prevent configuration of mono-2.0-gac: 
 mono-2.0-gac depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 mono-2.0-gac depends on libmono-security2.0-cil (>= 2.6.7); however: 
  Package libmono-security2.0-cil is not configured yet. 
dpkg: error processing mono-2.0-gac (--configure): 
 dependency problems - leaving unconfigured 
Setting up libaacs0 (0.3.0-4) ... 
No apport report written because MaxReports is reached already 
Setting up libbluray1 (1:0.2.1+git20111208.63e308d-3) ... 
Setting up libebml3 (1.2.2-2) ... 
Setting up libsdl-image1.2 (1.2.10-3) ... 
Setting up libva-x11-1 (1.0.15-4) ... 
Setting up libxcb-composite0 (1.8.1-1ubuntu0.1) ... 
Setting up libxcb-randr0 (1.8.1-1ubuntu0.1) ... 
Setting up libxcb-xv0 (1.8.1-1ubuntu0.1) ... 
Setting up libass4 (0.10.0-3) ... 
Setting up libcddb2 (1.3.2-3fakesync1) ... 
Setting up libcrystalhd3 (1:0.0~git20110715.fdd2f19-4.1) ... 
Setting up libdirectfb-1.2-9 (1.2.10.0-4.3ubuntu1) ... 
Setting up libdvbpsi7 (0.2.2-1) ... 
Setting up libiso9660-8 (0.83-1) ... 
Setting up libmatroska5 (1.3.0-1) ... 
Setting up libmodplug1 (1:0.8.8.4-1) ... 
Setting up libmpcdec6 (2:0.1~r459-1ubuntu1) ... 
Setting up libresid-builder0c2a (2.1.1-12) ... 
Setting up libsidplay2 (2.1.1-12) ... 
Setting up libtar0 (1.2.11-8) ... 
Setting up libvcdinfo0 (0.7.23-4.1ubuntu1) ... 
Setting up vlc-data (2.0.5-0ubuntu0.12.04.1) ... 
Setting up libvlccore5 (2.0.5-0ubuntu0.12.04.1) ... 
Setting up libvlc5 (2.0.5-0ubuntu0.12.04.1) ... 
Setting up libzvbi-common (0.2.33-4) ... 
Setting up libzvbi0 (0.2.33-4) ... 
Setting up libdca0 (0.0.5-5) ... 
Setting up libupnp3 (1:1.6.6-5.1) ... 
Setting up vlc-nox (2.0.5-0ubuntu0.12.04.1) ... 
Setting up libxcb-keysyms1 (0.3.8-1build1) ... 
Setting up vlc (2.0.5-0ubuntu0.12.04.1) ... 
Setting up vlc-plugin-notify (2.0.5-0ubuntu0.12.04.1) ... 
Setting up vlc-plugin-pulse (2.0.5-0ubuntu0.12.04.1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Errors were encountered while processing: 
 mono-gac 
 mono-runtime 
 libmono-corlib2.0-cil 
 libmono-cairo2.0-cil 
 libmono-posix2.0-cil 
 libmono-system2.0-cil 
 libmono-security2.0-cil 
 libmono-data-tds2.0-cil 
 libmono-i18n-west2.0-cil 
 libmono-i18n4.0-cil 
 libmono-i18n-west4.0-cil 
 libmono-i18n2.0-cil 
 libmono-messaging2.0-cil 
 libmono-sharpzip2.84-cil 
 libmono-system-data2.0-cil 
 libmono-sqlite2.0-cil 
 libmono-system-messaging2.0-cil 
 libmono-system-data-linq2.0-cil 
 libmono2.0-cil 
 libmono-system-web2.0-cil 
 libmono-wcf3.0-cil 
 mono-2.0-gac 
Error in function: 
Setting up mono-gac (2.10.8.1-1ubuntu2.2) ... 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.atk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gdk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.10.glade-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.10.glib-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gtk-dotnet.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.gtk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.10.pango-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.atk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gdk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.4.glade-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.4.glib-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gtk-dotnet.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.gtk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.4.pango-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.atk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gdk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.6.glade-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.6.glib-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.pango-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.atk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gdk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglade2.0-cil/policy.2.8.glade-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libglib2.0-cil/policy.2.8.glib-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gtk-dotnet.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.gtk-sharp.dll does not exist 
! Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.8.pango-sharp.dll does not exist 
dpkg: error processing mono-gac (--configure): 
 subprocess installed post-installation script returned error exit status 3 
dpkg: dependency problems prevent configuration of mono-runtime: 
 mono-runtime depends on mono-gac (= 2.10.8.1-1ubuntu2.2); however: 
  Package mono-gac is not configured yet. 
dpkg: error processing mono-runtime (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-posix2.0-cil: 
 libmono-posix2.0-cil depends on mono-runtime (>= 2.10.1); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-posix2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-i18n4.0-cil: 
 libmono-i18n4.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
 libmono-i18n4.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-i18n4.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-i18n-west4.0-cil: 
 libmono-i18n-west4.0-cil depends on libmono-i18n4.0-cil (>= 1.0); however: 
  Package libmono-i18n4.0-cil is not configured yet. 
dpkg: error processing libmono-i18n-west4.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-system-web2.0-cil: 
 libmono-system-web2.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
 libmono-system-web2.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-system-web2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-i18n2.0-cil: 
 libmono-i18n2.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
 libmono-i18n2.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-i18n2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-system2.0-cil: 
 libmono-system2.0-cil depends on libmono-posix2.0-cil (>= 2.4); however: 
  Package libmono-posix2.0-cil is not configured yet. 
 libmono-system2.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
 libmono-system2.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-system2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-corlib2.0-cil: 
 libmono-corlib2.0-cil depends on mono-runtime (>= 2.10.8.1); however: 
  Package mono-runtime is not configured yet. 
 libmono-corlib2.0-cil depends on mono-runtime (<< 2.10.8.2); however: 
  Package mono-runtime is not configured yet. 
dpkg: error processing libmono-corlib2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-system-data-linq2.0-cil: 
 libmono-system-data-linq2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-system-data-linq2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-system-data-linq2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-sqlite2.0-cil: 
 libmono-sqlite2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
 libmono-sqlite2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however: 
  Package libmono-system2.0-cil is not configured yet. 
dpkg: error processing libmono-sqlite2.0-cil (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mono-2.0-gac: 
 mono-2.0-gac depends on libmono-corlib2.0-cil (>= 2.6.3); however: 
  Package libmono-corlib2.0-cil is not configured yet. 
dpkg: error processing mono-2.0-gac (--configure): 
 dependency problems - leaving unconfigured 


Any ideas?
Thanks,

inTrouble

---

### Post by inTrouble on 2013-02-11
I marked this solved because I did a fresh install of Ubuntu 12.10. Thanks for all the help.

---

