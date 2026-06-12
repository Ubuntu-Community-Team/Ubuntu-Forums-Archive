---
title: "got issues with apt-get"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by chandramauli on 2013-07-04
hello,
I have ubuntu 10.04 VMWare player on windows 7. I find errors with apt-get install command as i want to install curl for AOSP.
Following is the command and result i got while performing it.
devi@ubuntu:~$ sudo apt-get install curl
[sudo] password for devi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  curl
1 upgraded, 0 newly installed, 0 to remove and 521 not upgraded.
Need to get 209kB of archives.
After this operation, 4,096B disk space will be freed.
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main curl 7.19.7-1ubuntu1.2
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main curl 7.19.7-1ubuntu1.2
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.19.7-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.19.7-1ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Help me, how to i resolve this problem?

---

### Post by claracc on 2013-07-04
Ubuntu 10.04 has reached its end of life support, for this reason, you cannot install software from the repositories.

The best recommendatios is that you upgrade your system to a supported ubuntu release (12.04,12.10, 13.04).

Anycase, you can install software from and EOL in this way: [http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

---

### Post by chandramauli on 2013-07-04
It is still not working..
I did exactly as in recommended link
and it resulted as below

```

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err [http://ppa.launchpad.net/ferramroberto/java/ubuntu/](http://ppa.launchpad.net/ferramroberto/java/ubuntu/) lucid/main Translation-en_US
  Could not resolve 'ppa.launchpad.net'
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                   
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US              
  Could not resolve 'archive.canonical.com'
Err [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) lucid Release.gpg
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com](http://us.old-releases.ubuntu.com) lucid-updates Release.gpg                
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://us.old-releases.ubuntu.com/ubuntu/](http://us.old-releases.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Could not resolve 'us.old-releases.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com/](http://archive.canonical.com/) natty/partner Translation-en_US
  Could not resolve 'archive.canonical.com'
Reading package lists... Done
W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.old-releases.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.old-releases.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'


W: Failed to fetch [http://archive.canonical.com/dists/lucid/Release.gpg](http://archive.canonical.com/dists/lucid/Release.gpg)  Could not resolve 'archive.canonical.com'


W: Failed to fetch [http://archive.canonical.com/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/dists/lucid/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'


W: Failed to fetch [http://archive.canonical.com/dists/natty/Release.gpg](http://archive.canonical.com/dists/natty/Release.gpg)  Could not resolve 'archive.canonical.com'


W: Failed to fetch [http://archive.canonical.com/dists/natty/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/dists/natty/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'


W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'


W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'


W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  firefox-locale-en linux-headers-2.6.32-48 linux-headers-2.6.32-48-generic
  linux-image-2.6.32-48-generic xul-ext-ubufox
The following packages will be upgraded:
  acpid apparmor apparmor-utils apport apport-gtk apt apt-transport-https
  apt-utils aptitude apturl apturl-common avahi-autoipd avahi-daemon
  avahi-utils base-files bind9-host binutils bogofilter bogofilter-bdb
  bogofilter-common bsdutils bzip2 ca-certificates compizconfig-backend-gconf
  cups cups-bsd cups-client cups-common curl dbus dbus-x11 dhcp3-client
  dhcp3-common dmsetup dnsutils dpkg empathy empathy-common evince
  evolution-data-server evolution-data-server-common firefox firefox-branding
  firefox-gnome-support foomatic-filters fuse-utils gdm gdm-guest-session
  ghostscript ghostscript-cups ghostscript-x gnome-utils gnupg gnupg-curl gpgv
  hpijs hplip hplip-data ifupdown imagemagick language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  lftp libapparmor-perl libapparmor1 libarchive1 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core6 libavahi-glib1
  libavahi-gobject0 libavahi-ui0 libbind9-60 libblkid1 libbz2-1.0
  libcamel1.2-14 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libdbus-1-3
  libdbus-glib-1-2 libdevmapper1.02.1 libdns64 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11
  libedataserverui1.2-8 libegroupwise1.2-13 libevdocument2 libevview2
  libexchange-storage1.2-3 libexif12 libexpat1 libfreetype6 libfuse2 libgc1c2
  libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata6 libgdict-1.0-6
  libgdiplus libgnutls26 libgs8 libgssapi-krb5-2 libgtk-vnc-1.0-0 libhpmud0
  libicu42 libisc60 libisccc60 libisccfg60 libjasper1 libjs-jquery
  libk5crypto3 libkpathsea5 libkrb5-3 libkrb5support0 liblcms1 libldap-2.4-2
  liblwres60 libmagickcore2 libmagickcore2-extra libmagickwand2
  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-runtime2.0-cil libmono-system-web2.0-cil
  libmono-system2.0-cil libmono2.0-cil libnm-glib2 libnm-util1 libnspr4-0d
  libnss3-1d libpam-modules libpam-runtime libpam0g libpango1.0-0
  libpango1.0-common libpcsclite1 libperl5.10 libpng12-0 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpoppler-glib4 libpoppler5
  libproxy0 libpurple-bin libpurple0 libpython2.6 libraptor1 librsvg2-2
  librsvg2-common libslp1 libsmbclient libsndfile1 libsnmp-base libsnmp15
  libsoup-gnome2.4-1 libsoup2.4-1 libssl0.9.8 libtasn1-3 libtiff4 libuuid1
  libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common libvte9 libwbclient0
  libwebkit-1.0-2 libwebkit-1.0-common libwww-perl libx11-6 libx11-data
  libx11-dev libxcb-render0 libxcb1 libxcb1-dev libxext6 libxfont1 libxi6
  libxml2 libxml2-utils libxrender1 libxslt1.1 libxt6 libxtst6 libxxf86vm1
  linux-firmware linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev login logrotate modemmanager mono-2.0-gac mono-gac
  mono-runtime mount mountall nautilus-sendto-empathy network-manager
  network-manager-gnome nvidia-173-modaliases nvidia-current-modaliases
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-style-human openoffice.org-writer openssl
  passwd perl perl-base perl-modules policykit-1 poppler-utils python-apport
  python-avahi python-crypto python-httplib2 python-libxml2 python-mako
  python-pam python-problem-report python-software-properties
  python-ubuntuone-client python-ubuntuone-storageprotocol python-uno
  python-vte python2.6 python2.6-minimal rdesktop rsync samba-common
  samba-common-bin smbclient software-properties-gtk sudo telepathy-gabble
  ttf-opensymbol ubufox ubuntuone-client ubuntuone-client-gnome uno-libs3
  update-manager update-manager-core update-notifier update-notifier-common
  ure usb-creator-common usb-creator-gtk util-linux uuid-runtime vino w3m wget
  x11-common x11-xserver-utils xorg xserver-common xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-all xsltproc
  xulrunner-1.9.2
294 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 292MB of archives.
After this operation, 213MB of additional disk space will be used.
Do you want to continue [Y/n]?
Y[Enter]

0.7-1ubuntu0.1_i386.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.0-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.0-2ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/x11-xserver-utils/x11-xserver-utils_7.5+1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/x11-xserver-utils/x11-xserver-utils_7.5+1ubuntu2.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.13_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.13_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/shadow/passwd_4.1.4.2-1ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/shadow/passwd_4.1.4.2-1ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/libuuid1_2.17.2-0ubuntu1.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/libuuid1_2.17.2-0ubuntu1.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/libblkid1_2.17.2-0ubuntu1.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/libblkid1_2.17.2-0ubuntu1.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-2ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-2ubuntu5.4_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.5-1ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.5-1ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.5-1ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.5-1ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.5-1ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.5-1ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.13_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.13_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/aptitude/aptitude_0.4.11.11-1ubuntu10lucid1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/aptitude/aptitude_0.4.11.11-1ubuntu10lucid1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.14_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.14_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/ca-certificates/ca-certificates_20090814ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/ca-certificates/ca-certificates_20090814ubuntu0.10.04.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.1.3-2ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.1.3-2ubuntu3.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.1.3-2ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.1.3-2ubuntu3.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.39-1ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.39-1ubuntu4.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/lvm2/dmsetup_1.02.39-1ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/lvm2/dmsetup_1.02.39-1ubuntu4.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gpgv_1.4.10-2ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gpgv_1.4.10-2ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.10-2ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.10-2ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.19.7-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.19.7-1ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg-curl_1.4.10-2ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg-curl_1.4.10-2ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/logrotate/logrotate_3.7.8-4ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/logrotate/logrotate_3.7.8-4ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.7.2p1-1ubuntu5.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.7.2p1-1ubuntu5.6_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.6.8ubuntu29.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.6.8ubuntu29.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.5.1-0ubuntu0.10.04.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.5.1-0ubuntu0.10.04.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.5.1-0ubuntu0.10.04.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.5.1-0ubuntu0.10.04.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.5.1-0ubuntu0.10.04.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.5.1-0ubuntu0.10.04.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.5.1-0ubuntu0.10.04.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.5.1-0ubuntu0.10.04.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns64_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns64_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.0.dfsg.P1-1ubuntu0.9_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.8.1-1.1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.8.1-1.1ubuntu3.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.8.1-1.1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.8.1-1.1ubuntu3.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgc/libgc1c2_6.8-1.2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgc/libgc1c2_6.8-1.2ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libw/libwww-perl/libwww-perl_5.834-1ubuntu0.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/libw/libwww-perl/libwww-perl_5.834-1ubuntu0.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_3.0.7-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_3.0.7-1ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/uuid-runtime_2.17.2-0ubuntu1.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/util-linux/uuid-runtime_2.17.2-0ubuntu1.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.2-2.1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/w/w3m/w3m_0.5.2-2.1ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/acpid/acpid_1.0.10-5ubuntu2.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/acpid/acpid_1.0.10-5ubuntu2.5_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_1.13.3-0ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_1.13.3-0ubuntu2.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_1.13.3-0ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_1.13.3-0ubuntu2.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apport/apport_1.13.3-0ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apport/apport_1.13.3-0ubuntu2.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_1.13.3-0ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_1.13.3-0ubuntu2.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.13_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.13_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apturl/apturl_0.4.1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apturl/apturl_0.4.1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apturl/apturl-common_0.4.1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apturl/apturl-common_0.4.1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.0-0ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.0-0ubuntu2.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.0-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.0-0ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.23.5-0ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vte/libvte-common_0.23.5-0ubuntu1.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.23.5-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vte/libvte9_0.23.5-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vte/python-vte_0.23.5-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vte/python-vte_0.23.5-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/software-properties/python-software-properties_0.75.10.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/software-properties/python-software-properties_0.75.10.3_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.75.10.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.75.10.3_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.25-1ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.25-1ubuntu6.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core6_0.6.25-1ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core6_0.6.25-1ubuntu6.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.25-1ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.25-1ubuntu6.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-utils_0.6.25-1ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-utils_0.6.25-1ubuntu6.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.20.1-3ubuntu7.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.20.1-3ubuntu7.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-common_1.2.1-0ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-common_1.2.1-0ubuntu1.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-bdb_1.2.1-0ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-bdb_1.2.1-0ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter_1.2.1-0ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter_1.2.1-0ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.19.7-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.19.7-1ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.19.7-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/curl_7.19.7-1ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-x11_1.2.16-2ubuntu4.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-x11_1.2.16-2ubuntu4.7_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.84-1ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.84-1ubuntu0.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.9.5-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.9.5-0ubuntu0.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.30.2-0ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.30.2-0ubuntu0.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-11_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-11_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.14.3-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.14.3-0ubuntu0.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-14_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-14_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util1_0.8-0ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util1_0.8-0ubuntu3.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8-0ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8-0ubuntu3.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu42_4.2.1-3ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu42_4.2.1-3ubuntu0.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.26-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.26-1ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-common_1.2.7-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-common_1.2.7-0ubuntu0.10.04.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.7-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.7-0ubuntu0.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.30.3-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.30.3-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.30.3-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.30.3-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.30.3-0ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.30.3-0ubuntu1.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument2_2.30.3-0ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument2_2.30.3-0ubuntu1.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evince/libevview2_2.30.3-0ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evince/libevview2_2.30.3-0ubuntu1.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea5_2009-5ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea5_2009-5ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.12.4-0ubuntu5.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.12.4-0ubuntu5.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.30.3-0ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.30.3-0ubuntu1.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.28.3.1-0ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.28.3.1-0ubuntu6.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_20.0+build1-0ubuntu0.10.04.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_20.0+build1-0ubuntu0.10.04.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_20.0+build1-0ubuntu0.10.04.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_20.0+build1-0ubuntu0.10.04.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_20.0+build1-0ubuntu0.10.04.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_20.0+build1-0ubuntu0.10.04.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_20.0+build1-0ubuntu0.10.04.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_20.0+build1-0ubuntu0.10.04.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.30.2.is.2.30.0-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.30.2.is.2.30.0-0ubuntu5.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gdm-guest-session/gdm-guest-session_0.15ubuntu0.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gdm-guest-session/gdm-guest-session_0.15ubuntu0.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_8.71.dfsg.1-0ubuntu5.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_8.71.dfsg.1-0ubuntu5.5_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.71.dfsg.1-0ubuntu5.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.71.dfsg.1-0ubuntu5.5_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnome-utils/libgdict-1.0-6_2.30.0-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnome-utils/libgdict-1.0-6_2.30.0-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnome-utils/gnome-utils_2.30.0-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnome-utils/gnome-utils_2.30.0-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-7ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-7ubuntu0.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2_6.5.7.8-1ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2_6.5.7.8-1ubuntu1.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand2_6.5.7.8-1ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand2_6.5.7.8-1ubuntu1.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.5.7.8-1ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.5.7.8-1ubuntu1.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/lftp/lftp_4.0.2-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/lftp/lftp_4.0.2-1ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/liba/libarchive/libarchive1_2.8.0-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/liba/libarchive/libarchive1_2.8.0-2ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.25-1ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.25-1ubuntu6.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-gobject0_0.6.25-1ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-gobject0_0.6.25-1ubuntu6.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-ui0_0.6.25-1ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-ui0_0.6.25-1ubuntu6.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.28.3.1-0ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.28.3.1-0ubuntu6.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libe/libexif/libexif12_0.6.19-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libe/libexif/libexif12_0.6.19-1ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgdata/libgdata-common_0.5.2-0ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgdata/libgdata-common_0.5.2-0ubuntu1.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-1ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup-gnome2.4-1_2.30.2-0ubuntu0.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup-gnome2.4-1_2.30.2-0ubuntu0.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgdata/libgdata6_0.5.2-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgdata/libgdata6_0.5.2-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgdiplus/libgdiplus_2.4.2-1ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgdiplus/libgdiplus_2.4.2-1ubuntu0.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gtk-vnc/libgtk-vnc-1.0-0_0.3.10-2ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gtk-vnc/libgtk-vnc-1.0-0_0.3.10-2ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/j/jquery/libjs-jquery_1.3.3-2ubuntu1.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/j/jquery/libjs-jquery_1.3.3-2ubuntu1.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2-extra_6.5.7.8-1ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2-extra_6.5.7.8-1ubuntu1.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_2.4.4~svn151842-1ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_2.4.4~svn151842-1ubuntu4.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-2.0-gac_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-2.0-gac_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-i18n-west2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-i18n-west2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-posix2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-posix2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip2.84-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip2.84-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-runtime2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-runtime2.0-cil_2.4.4~svn151842-1ubuntu4.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pcsc-lite/libpcsclite1_1.5.3-1ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pcsc-lite/libpcsclite1_1.5.3-1ubuntu4.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/policykit-1/libpolkit-agent-1-0_0.96-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/policykit-1/libpolkit-agent-1-0_0.96-2ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.6.6-1ubuntu4.6_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.6.6-1ubuntu4.6_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.6.6-1ubuntu4.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.6.6-1ubuntu4.6_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/raptor/libraptor1_1.4.21-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/raptor/libraptor1_1.4.21-1ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libr/librsvg/librsvg2-common_2.26.3-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libr/librsvg/librsvg2-common_2.26.3-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libr/librsvg/librsvg2-2_2.26.3-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libr/librsvg/librsvg2-2_2.26.3-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.7~dfsg-1ubuntu3.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.7~dfsg-1ubuntu3.10_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.7~dfsg-1ubuntu3.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.7~dfsg-1ubuntu3.10_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.2.3-3ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.2.3-3ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.2.3-3ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.2.3-3ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.21-2ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.21-2ubuntu0.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisfile3_1.2.3-3ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisfile3_1.2.3-3ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-render0_1.5-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-render0_1.5-2ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.4.1-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.4.1-1ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.6.dfsg-1ubuntu1.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.6.dfsg-1ubuntu1.8_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxtst/libxtst6_1.1.0-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxtst/libxtst6_1.1.0-2ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.34.14_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.34.14_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.48.55_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.48.55_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.48.55_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.48.55_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-48_2.6.32-48.110_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-48_2.6.32-48.110_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-48-generic_2.6.32-48.110_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-48-generic_2.6.32-48.110_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.48.55_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.48.55_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-48.110_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-48.110_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/modemmanager/modemmanager_0.3-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/modemmanager/modemmanager_0.3-0ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.134.11.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.134.11.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.134.11.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.134.11.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier_0.99.3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier_0.99.3ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier-common_0.99.3ubuntu0.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier-common_0.99.3ubuntu0.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8-0ubuntu3.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8-0ubuntu3.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8-0ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8-0ubuntu3.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-173/nvidia-173-modaliases_173.14.22-0ubuntu11.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers-173/nvidia-173-modaliases_173.14.22-0ubuntu11.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current-modaliases_195.36.24-0ubuntu1~10.04.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current-modaliases_195.36.24-0ubuntu1~10.04.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_3.2.0-7ubuntu4.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_3.2.0-7ubuntu4.4_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.2.0-7ubuntu4.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.2.0-7ubuntu4.4_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_3.2.0-7ubuntu4.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_3.2.0-7ubuntu4.4_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.2.0-7ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.2.0-7ubuntu4.4_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/avahi/python-avahi_0.6.25-1ubuntu6.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/avahi/python-avahi_0.6.25-1ubuntu6.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python-crypto/python-crypto_2.0.1+dfsg1-4ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-crypto/python-crypto_2.0.1+dfsg1-4ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python-httplib2/python-httplib2_0.7.2-1ubuntu2~0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-httplib2/python-httplib2_0.7.2-1ubuntu2~0.10.04.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.6.dfsg-1ubuntu1.8_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.6.dfsg-1ubuntu1.8_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mako/python-mako_0.2.5-2ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mako/python-mako_0.2.5-2ubuntu1.3_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python-pam/python-pam_0.4.2-12.1ubuntu1.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-pam/python-pam_0.4.2-12.1ubuntu1.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.2.2-0ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.2.2-0ubuntu2.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.2.2-0ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.2.2-0ubuntu2.3_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/ubuntuone-storage-protocol/python-ubuntuone-storageprotocol_1.2.0-0ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/ubuntuone-storage-protocol/python-ubuntuone-storageprotocol_1.2.0-0ubuntu1.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.2.2-0ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.2.2-0ubuntu2.3_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.6.0-2ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.6.0-2ubuntu3.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.7~dfsg-1ubuntu3.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.7~dfsg-1ubuntu3.10_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.4.7~dfsg-1ubuntu3.10_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.4.7~dfsg-1ubuntu3.10_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.7~dfsg-1ubuntu3.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.7~dfsg-1ubuntu3.10_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/telepathy-gabble/telepathy-gabble_0.8.12-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/telepathy-gabble/telepathy-gabble_0.8.12-0ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_2.6-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_2.6-0ubuntu0.10.04.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/ubufox/xul-ext-ubufox_2.6-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/ubufox/xul-ext-ubufox_2.6-0ubuntu0.10.04.1_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-gtk_0.2.22.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-gtk_0.2.22.3_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-common_0.2.22.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-common_0.2.22.3_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.28.2-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/v/vino/vino_2.28.2-0ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.12_all.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.12_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.12_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.12_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.5+5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.5+5ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.5+5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.5+5ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.5+5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.5+5ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xorg_7.5+5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg/xorg_7.5+5ubuntu1.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.26-1ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.26-1ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.28+build1+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.28+build1+nobinonly-0ubuntu0.10.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/compizconfig-backend-gconf/compizconfig-backend-gconf_0.8.4-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/compizconfig-backend-gconf/compizconfig-backend-gconf_0.8.4-0ubuntu2.1_i386.deb)  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by Dozy Van on 2013-07-04
[**[COLOR=#000000]chandramauli[/COLOR]**]("http://ubuntuforums.org/member.php?u=1836410")

The issue is that as this version of ubuntu is so old so few people use it. I would suggest you backup your important information download 12.04 and do a freshinstall.

---

### Post by chandramauli on 2013-07-04
Thank you.. :)

---

### Post by Irihapeti on 2013-07-04
Please put long listings between ```

``` tags. It takes up less room on the screen and is easier to read.

---

### Post by claracc on 2013-07-04
You have to remove the natty lines in sources.list, also disable the ppas (ferramrroberto is one of them), and point the security.com repositories to old-releases.ubuntu.com.

Here you have a more complete link: [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

Anycase, as I recommended before, your best bet is to update to a supported ubuntu release.

---

