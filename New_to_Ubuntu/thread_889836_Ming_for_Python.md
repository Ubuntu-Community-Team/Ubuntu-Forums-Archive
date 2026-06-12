---
title: "Ming for Python"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by colink on 2008-08-14
Hello, 

I'm trying to get the Ming SWF library for Python installed on Ubuntu, but when I try importing ming in python I get this error:

>>> import ming
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/ming.py", line 2, in <module>
    import mingc
  File "/usr/lib/python2.5/site-packages/mingc.py", line 7, in <module>
    import _mingc
ImportError: libming.so.1: cannot open shared object file: No such file or directory


Any help would be appreciated, 
Colin

---

### Post by roquefilipe on 2008-08-14
well I did "sudo aptitude install python-ming" and then imported ming without problems. You might want to try to reinstall it.

Also, search for the libming library . run this "sudo updatedb; locate libming"

---

### Post by ConMan318 on 2008-08-14
Run this:
```

ls /usr/lib/python2.5/site-packages/

```

and look for 'ming.py' and 'mingc.py'.  My guess is that they don't exist, so obviously Python can't find them.  You said 'installed on Ubuntu', so maybe you think the module is pre-installed.  Nope.

Just checked the repos, you can install the module with 
```

sudo apt-get install python-ming

```

then run your program again.

---

### Post by colink on 2008-08-14
Just tried both suggestions with no luck. Here's the output:

%aptitude install python-ming

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  apache2-mpm-prefork libapache2-mod-perl2 libapache2-mod-php5 libnspr4 libnss3 libsvn1 linux-image-generic 
  linux-libc-dev linux-restricted-modules-common linux-restricted-modules-generic mysql-client-5.0 mysql-server-5.0 
  php5-cli php5-common 
The following packages have been kept back:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater apache2-utils 
  apache2.2-common app-install-data apport apport-qt bind9-host bsdutils bzip2 ca-certificates cupsys cupsys-bsd 
  cupsys-client cupsys-common dbus dnsutils e2fslibs e2fsprogs file firefox foo2zjs genisoimage gs-esp gs-esp-x 
  gtk-qt-engine hpijs hplip hplip-data hwdb-client-common hwdb-client-kde iptables kate kcontrol kdebase-bin 
  kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a kdepasswd kdeprint kdesktop kdm kexi kfind khelpcenter 
  kicker klipper kmenuedit koffice-data koffice-libs konqueror konqueror-nsplugins konsole ksmserver ksplash 
  ksysguard ksysguardd ktorrent kwin language-pack-en language-pack-kde-en libapache2-mod-perl2-dev 
  libapache2-mod-python libbind9-0 libblkid1 libbz2-1.0 libcairo2 libcomerr2 libcupsimage2 libcupsys2 libcurl3 
  libcurl3-gnutls libdbus-1-3 libdns22 libexif12 libflac++5c2 libflac7 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa 
  libgnutls13 libgs-esp8 libicu36 libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libjasper-runtime libkonq4 
  libkrb53 liblwres9 libmagic1 libmagick9 libmysqlclient15-dev libmysqlclient15off liboggflac3 libpcre3 libperl5.8 
  libpng12-0 libpoppler1 libpoppler1-qt libpq5 libpulse0 libqt3-mt libruby1.8 libsmbclient libsndfile1 libsnmp-base 
  libsnmp9 libspeex1 libss2 libssl-dev libssl0.9.8 libuuid1 libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 
  libxfont1 libxine1 libxml2 libxslt1.1 linux-generic linux-headers-generic mesa-utils mount mysql-common 
  mysql-server openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-impress openoffice.org-java-common openoffice.org-kde openoffice.org-math 
  openoffice.org-style-crystal openoffice.org-style-human openoffice.org-writer openssh-client openssh-server 
  openssl openvpn perl perl-base perl-modules perl-suid php-pear php5 php5-dev php5-mysql phpmyadmin poppler-utils 
  python python-apport python-launchpad-bugs python-minimal python-problem-report python-uno python2.5 
  python2.5-dev python2.5-minimal rsync ruby1.8 samba samba-common smbclient smbfs ssl-cert subversion tar tcpdump 
  ttf-opensymbol tzdata unattended-upgrades unzip update-manager-core util-linux util-linux-locales vim-common 
  vim-tiny vorbis-tools wodim xserver-xorg-core 
0 packages upgraded, 0 newly installed, 0 to remove and 204 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up python-ming (0.3.0-11ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/ming.py
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/ming.py
dpkg: error processing python-ming (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-ming
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-ming (0.3.0-11ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/ming.py
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/ming.py
dpkg: error processing python-ming (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-ming


%sudo apt-get install python-ming

Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-ming is already the newest version.
The following packages were automatically installed and are no longer required:
  libapache-mod-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 204 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python-ming (0.3.0-11ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/ming.py
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/ming.py
dpkg: error processing python-ming (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-ming
E: Sub-process /usr/bin/dpkg returned an error code (1)


The ming.py and mingc.py are in my packages folder for python. The problem is when mingc.py tries to import _mingc the error from the first post happens. 

Searching for libming brings up a long list of directories and files. Anything specific I should be looking for?

---

### Post by roquefilipe on 2008-08-14
you have many packages held back. Any reason for that? I would first resolve that since python is even in the list. 

To do that try "sudo aptitude update;sudo aptitude upgrade;sudo aptitude dist-upgrade"

---

