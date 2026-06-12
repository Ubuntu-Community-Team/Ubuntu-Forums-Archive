---
title: "gftp apt-get doesn't work..."
date: 2005-03-25
forum: Repositories &amp; Backports
---

### Post by CrustyDOD on 2005-03-25
Hey

Like topic says: sudo apt-get install gftp
doesn't work, error is: 

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.17-6) but it is not going to be installed
        Depends: gftp-text (= 2.0.17-6) but it is not going to be installed
E: Broken packages

Now i find these topic: [http://ubuntuforums.org/archive/index.php/t-15929.html](http://ubuntuforums.org/archive/index.php/t-15929.html)
updated list and it still doesn't work, same error!

my source.list:

##deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted


what's the problem here? what i am missing?


EDIT: just tryed to install apache and mysql and i get the same errors:

**Apache:** - sudo apt-get install apache2

The following packages have unmet dependencies:
  apache2: Depends: apache2-mpm-worker but it is not going to be installed or
                    apache2-mpm-prefork but it is not going to be installed or
                    apache2-mpm-perchild but it is not going to be installed
E: Broken packages


**MySql:** - sudo apt-get install mysql-server

The following packages have unmet dependencies:
  mysql-server: Depends: mysql-client (>= 4.0.20-2ubuntu1.4) but it is not going to be installed
                Depends: libdbi-perl but it is not going to be installed
E: Broken packages

---

### Post by az on 2005-03-25
Does apt-get -f install bring anything in?

What have you installed from the backports?  That may be a package that conflicts with others.  (Backports are great, but they have been known to screw up your dependancies.)

---

