---
title: "TRying to install updates error"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by coubury on 2008-10-06
Using Ubuntu

when i trying to install updates i get this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I get it also when i try to open synaptic

---

### Post by tuxxy on 2008-10-06
Open a terminal and run this command, then try again

```
sudo dpkg --configure -a
```

---

### Post by coubury on 2008-10-06
It failed


me@me-laptop:~$ sudo dpkg --configure -a
[sudo] password for me: 
Setting up libc6 (2.7-10ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
me@me-laptop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [315kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6636B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [90.4kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [908B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [100kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [26.7kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [20.1kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [2795B]
Fetched 621kB in 2s (212kB/s)                       
Reading package lists... Done
me@me-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccfg30
The following packages will be upgraded:
  anacron app-install-data-commercial compiz-fusion-plugins-main
  deskbar-applet eject eog evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins firefox
  firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support gcalctool gdb
  gdm gnome-about gnome-cards-data gnome-desktop-data gnome-games
  gnome-games-data gnome-panel gnome-panel-data gnome-system-monitor
  gtk2-engines gtk2-engines-murrine gtk2-engines-ubuntulooks gtkhtml3.14 gvfs
  gvfs-backends gvfs-fuse hal iproute libcamel1.2-11 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3
  libfreetype6 libgdata-google1.2-1 libgdata1.2-1 libgksu2-0 libglib2.0-0
  libglibmm-2.4-1c2a libgnome-desktop-2 libgtkhtml3.14-19
  libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0
  libgweather-common libgweather1 libhal-storage1 libhal1 libisc32 libisccc30
  libldap-2.4-2 liblwres30 libnautilus-extension1 libnspr4-0d libnss3-1d
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpcre3
  libpoppler-glib2 libpoppler2 libpurple0 libsmbclient libsmbios1 libsoup2.4-1
  libtiff4 libwnck-common libwnck22 libxml2 libxml2-utils libxslt1.1
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
  linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic
  linux-restricted-modules-common nautilus nautilus-data nautilus-sendto
  pciutils pidgin pidgin-data poppler-utils procps python-gobject
  python-gtkhtml2 python-libxml2 rdesktop samba-common smbclient ssl-cert sudo
  tzdata ufw update-manager update-manager-core update-notifier
  update-notifier-common xserver-xorg-video-intel xsltproc xulrunner-1.9
  xulrunner-1.9-gnome-support yelp
115 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/129MB of archives.
After this operation, 971kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 95877 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.34 (using .../linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace tzdata 2008c-1ubuntu0.8.04 (using .../tzdata_2008e-1ubuntu0.8.04_all.deb) ...
Unpacking replacement tzdata ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
me@me-laptop:~$

---

### Post by love305k on 2008-12-30
i got the error while doing this...unable to install any updates
help me as soos as possible
maqsood@maqsood-desktop:~$ sudo dpkg --configure -a
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/status': Input/output error
maqsood@maqsood-desktop:~$

---

