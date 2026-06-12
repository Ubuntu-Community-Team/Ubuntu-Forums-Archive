---
title: "Apparent dependency circle for ubuntu desktop?"
date: 2015-01-13
forum: New to Ubuntu
---

### Post by davycrockett on 2015-01-13
Hi,

I am trying to reinstall a lot of my system after stupidly deleting some python libraries and having some serious problems with representation of windows on ubuntu trusty 14.04.
It seems there is a dependency circle for update-notifier-common/ update-notifier/ update-manager/ ubuntu-release-upgrader-gtk/ ubuntu-desktop although as a complete beginner I'm not sure.
I have been playing around with removing some of these from dpkg but to no avail.
Any bright ideas?  Thanks.


TRYING TO INSTALL ubuntu desktop

```
sudo apt-get install ubuntu-desktop

  Package ubuntu-release-upgrader-gtk is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.


dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-notifier-common
 update-notifier
 update-manager
 ubuntu-release-upgrader-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

TRYING TO INSTALL update-notifier-common

dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ubuntu-release-upgrader-gtk; however:
  Package ubuntu-release-upgrader-gtk is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.


dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 update-notifier-common
 update-notifier
 update-manager
 ubuntu-release-upgrader-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)



TRYING TO INSTALL update-notifier

 e-upgrader-gtk; however:
  Package ubuntu-release-upgrader-gtk is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.


dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-notifier-common
 update-notifier
 update-manager
 ubuntu-release-upgrader-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


TRYING TO INSTALL update-manager

ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.


dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ubuntu-release-upgrader-gtk; however:
  Package ubuntu-release-upgrader-gtk is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.


dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-notifier-common
 update-notifier
 update-manager
 ubuntu-release-upgrader-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)



TRYING TO INSTALL ubuntu-release-upgrader-gtk

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-notifier-common
 update-notifier
 update-manager
 ubuntu-release-upgrader-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by sandyd on 2015-01-13
What does
```

sudo apt-get install ubuntu-desktop ubuntu-release-upgrader-gtk update-manager update-notifier-common update-notifier
```
output?

---

### Post by davycrockett on 2015-01-15
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
ubuntu-release-upgrader-gtk is already the newest version.
update-manager is already the newest version.
update-notifier is already the newest version.

update-notifier-common is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 

Setting up update-notifier-common (0.154.1ubuntu1) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
  File "/usr/lib/python2.7/dist-packages/debian/deb822.py", line 37, in <module>
    import chardet
ImportError: No module named chardet
dpkg: error processing package update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.154.1ubuntu1); however:
  Package update-notifier-common is not configured yet.


dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-notifier; however:
  Package update-notifier is not configured yet.


dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.


dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ubuntu-releasNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                    No apport report written because the error message indicates it's a follow-up error from a previous failure.
                No apport report written because MaxReports has already been reached
    No apport report written because MaxReports has already been reached
                                                                        e-upgrader-gtk; however:
  Package ubuntu-release-upgrader-gtk is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.


dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-notifier-common
 update-notifier
 update-manager
 ubuntu-release-upgrader-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It's complaining about a lack of chardet module for python even though I've already done pip install chardet.

---

### Post by davycrockett on 2015-01-15
btw the path that dkpg is looking at 

```
/usr/lib/python2.7/dist-packages/debian/
```

is different to the .bashrc PYTHONPATH (where chardet lives) which is 

```
/home/username/Enthought/Canopy_64bit/User/lib/python2.7/site-packages
```

but copying over the chardet directory doesn't help.

---

### Post by mc4man on 2015-01-15
Do you have this installed?  (not whatever you've done in home dir., get rid of it..
```
apt-cache policy python-chardet
```

If not installed then try installing, if already installed then try re-installing
```
sudo apt-get --reinstall install python-chardet
```

---

### Post by davycrockett on 2015-02-10
Thanks a lot that worked now there are only issues with window representation and no toolbars appearing on the left or top of the screen(left for applications running, top for search). Only google-chrome shows a top border to drag windows around and no applications (eg libreoffice calc) have menu bars (file, edit etc.). Any ideas?

Thanks for your help again.

EDIT - Maybe this should be in desktop representations?

---

### Post by ptn107 on 2015-02-11
A Ubuntu 14.04.2 LTS system has the following python packages installed by default.  You have all of these?
```
dh-python
libpython-stdlib:amd64
libpython2.7:amd64
libpython2.7-minimal:amd64
libpython2.7-stdlib:amd64
libpython3-stdlib:amd64
libpython3.4:amd64
libpython3.4-minimal:amd64
libpython3.4-stdlib:amd64
python
python-apt
python-apt-common
python-aptdaemon
python-aptdaemon.gtk3widgets
python-cairo
python-chardet
python-commandnotfound
python-crypto
python-cups
python-cupshelpers
python-dbus
python-dbus-dev
python-debian
python-debtagshw
python-defer
python-dirspec
python-gconf
python-gdbm
python-gi
python-gi-cairo
python-gnomekeyring
python-gobject
python-gobject-2
python-gtk2
python-httplib2
python-ibus
python-imaging
python-ldb
python-libxml2
python-lockfile
python-lxml
python-minimal
python-notify
python-ntdb
python-oauthlib
python-oneconf
python-openssl
python-pam
python-pexpect
python-pil
python-piston-mini-client
python-pkg-resources
python-qt4
python-qt4-dbus
python-renderpm
python-reportlab
python-reportlab-accel
python-requests
python-samba
python-serial
python-sip
python-six
python-smbc
python-talloc
python-tdb
python-twisted-bin
python-twisted-core
python-twisted-web
python-ubuntu-sso-client
python-urllib3
python-xapian
python-xdg
python-zeitgeist
python-zope.interface
python2.7
python2.7-minimal
python3
python3-apport
python3-apt
python3-aptdaemon
python3-aptdaemon.gtk3widgets
python3-aptdaemon.pkcompat
python3-brlapi
python3-cairo
python3-chardet
python3-checkbox-ng
python3-checkbox-support
python3-commandnotfound
python3-crypto
python3-dbus
python3-debian
python3-defer
python3-distupgrade
python3-feedparser
python3-gdbm:amd64
python3-gi
python3-gi-cairo
python3-httplib2
python3-louis
python3-lxml
python3-mako
python3-markupsafe
python3-minimal
python3-oauthlib
python3-oneconf
python3-piston-mini-client
python3-pkg-resources
python3-plainbox
python3-problem-report
python3-pyatspi
python3-pycurl
python3-pyparsing
python3-requests
python3-six
python3-software-properties
python3-speechd
python3-uno
python3-update-manager
python3-urllib3
python3-xdg
python3-xkit
python3.4
python3.4-minimal
```

---

### Post by vishal131 on 2015-08-05
Hi,

I am struck at this issue since past one month but unable to solve. Apparently tried every solution available on this thread as well as other related threads. replying on this thread because this list my issue exactly. Please help, if you have any other solution/workaround in your mind :( 

The above solution also didn't helped and getting the same error again.

One thing I tried is, in python console, I tried "import deb.822". It executed without any error. But when I do "python package-data-downloader" from the directory /usr/lib/update-notifier/, I get import error. unable to understand why. Please help.

---

### Post by bapoumba on 2015-08-07
@vishal131 : could you please post your exact error messages ? Thanks.

---

### Post by vishal131 on 2015-08-08
This is the error message that I get when ever I install a new package or sudo apt-get upgarde:

```
Setting up update-notifier-common (0.154.1ubuntu1) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
ImportError: No module named debian.deb822
dpkg: error processing package update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.154.1ubuntu1); however:
  Package update-notifier-common is not configured yet.

dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-notifier; however:
  Package update-notifier is not configured yet.

dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ubuntu-releasNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        e-upgrader-gtk; however:
  Package ubuntu-release-upgrader-gtk is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-desktop depends on update-notifier; however:
  Package update-notifier is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-notifier-common
 update-notifier
 update-manager
 ubuntu-release-upgrader-gtk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by bapoumba on 2015-08-08
OK, can you please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by mc4man on 2015-08-08
For starters try - 
```
sudo apt-get install python-debian
```
(and make sure python-chardet package is installed

---

### Post by vishal131 on 2015-08-09
@bapoumba: following is the output

```
:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://in.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://in.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://in.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://in.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb http://archive.canonical.com/ precise partner
    57    # deb-src http://archive.canonical.com/ precise partner
    58    deb-src http://extras.ubuntu.com/ubuntu trusty main
```

```
:~$ ls -la /etc/apt/sources.list.d
total 24
drwxr-xr-x 2 root root 4096 Jul 14 02:33 .
drwxr-xr-x 6 root root 4096 Jun  4 23:24 ..
-rw-r--r-- 1 root root  176 Feb 19 00:09 google-chrome.list
-rw-r--r-- 1 root root  176 Feb 19 00:09 google-chrome.list.save
-rw-r--r-- 1 root root   86 Jul 14 02:33 ia32-libs-raring.list
-rw-r--r-- 1 root root   61 Jun  4 23:25 mono-xamarin.list
```

```
:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/ia32-libs-raring.list <==
deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse

==> /etc/apt/sources.list.d/mono-xamarin.list <==
deb http://download.mono-project.com/repo/debian wheezy main
```

---

### Post by vishal131 on 2015-08-09
@mc4man: I am getting the same error again :(

---

