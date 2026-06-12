---
title: "Cannot install webgui"
date: 2010-11-08
forum: Repositories &amp; Backports
---

### Post by boondocks on 2010-11-08
I am using synaptic to install webgui.
As soon as I select and mark this package, the following appears:
> webgui:
 Depends: libpoe-component-client-http-perl ( >=0.88 ) but it is not installable
What should I do?

---

### Post by godspeedmav on 2010-11-08
Which version of Ubuntu are you using?

Even in launchpad: [https://launchpad.net/ubuntu/+source/libpoe-component-client-http-perl](https://launchpad.net/ubuntu/+source/libpoe-component-client-http-perl) till Karmic Koala, the version is at 0.88-1

According to the Maverick repos, it has libpoe-component-client-http-perl at version 0.895-1

Or you could download the .deb file from here: [http://ftp.debian.org/debian/pool/main/libp/libpoe-component-client-http-perl/](http://ftp.debian.org/debian/pool/main/libp/libpoe-component-client-http-perl/)

---

### Post by boondocks on 2010-11-08
I am running "Ubuntu 10.04.1 LTS".

---

### Post by pdc124 on 2010-12-05
Im trying to install this as well - Im no that familiar with ubuntu/dpkg , having come from gentoo .
is there an easy solution to this , or do i just have to chase down all the dependencies it lists.
> nine@nine:/tmp$ sudo dpkg -i libpoe-component-client-http-perl_0.895-1_all.deb 
Selecting previously deselected package libpoe-component-client-http-perl.
(Reading database ... 167588 files and directories currently installed.)
Unpacking libpoe-component-client-http-perl (from libpoe-component-client-http-perl_0.895-1_all.deb) ...
dpkg: dependency problems prevent configuration of libpoe-component-client-http-perl:
 libpoe-component-client-http-perl depends on libpoe-perl (>= 2:1.2800); however:
  Package libpoe-perl is not installed.
 libpoe-component-client-http-perl depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 libpoe-component-client-http-perl depends on libpoe-component-client-keepalive-perl (>= 0.2610); however:
  Package libpoe-component-client-keepalive-perl is not installed.
dpkg: error processing libpoe-component-client-http-perl (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 libpoe-component-client-http-perl
nine@nine:/tmp$ sudo aptitude
nine@nine:/tmp$ sudo apt-get install  libnet-ssleay-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  libpoe-component-client-http-perl: Depends: libpoe-perl (>= 2:1.2800) but it is not going to be installed
                                     Depends: libpoe-component-client-keepalive-perl (>= 0.2610) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
nine@nine:/tmp$ sudo apt-get install  libpoe-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  libpoe-component-client-http-perl: Depends: libnet-ssleay-perl but it is not going to be installed
                                     Depends: libpoe-component-client-keepalive-perl (>= 0.2610) but it is not installable
  libpoe-perl: Depends: libfilter-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


---

