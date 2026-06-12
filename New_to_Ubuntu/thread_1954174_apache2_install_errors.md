---
title: "apache2 install errors"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by neil_1 on 2012-04-07
i'm trying to install mysql packages but i get these errors..
could someone tell me what i'm doing wrong?

i did
> sudo apt-get install apache2 
sudo apt-get install php5 libapache2-mod-php5 
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql but when i enter any, i get the same errors.

> neil@crunchbang:~$ sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-auth-mysql is already the newest version.
mysql-server is already the newest version.
php5-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.1 (5.1.61-0+squeeze1) ...
Stopping MySQL database server: mysqld.
120407 13:05:21 [Note] Plugin 'FEDERATED' is disabled.
120407 13:05:21  InnoDB: Initializing buffer pool, size = 8.0M
120407 13:05:21  InnoDB: Completed initialization of buffer pool
120407 13:05:21  InnoDB: Started; log sequence number 0 44233
120407 13:05:21  InnoDB: Starting shutdown...
120407 13:05:26  InnoDB: Shutdown completed; log sequence number 0 44233
insserv: warning: script 'K01vmware' missing LSB tags and overrides
insserv: warning: script 'K08vmware-USBArbitrator' missing LSB tags and overrides
insserv: warning: script 'vmware' missing LSB tags and overrides
insserv: warning: script 'vmware-USBArbitrator' missing LSB tags and overrides
insserv: There is a loop between service rmnologin and checkroot if started
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service hdparm at depth 2
insserv:  loop involving service hwclock at depth 6
insserv:  loop involving service keyboard-setup at depth 4
insserv:  loop involving service checkfs at depth 6
insserv:  loop involving service ifupdown-clean at depth 6
insserv:  loop involving service mtab at depth 6
insserv: There is a loop between service rmnologin and checkroot if started
insserv: There is a loop between service rmnologin and udev if started
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service vmware-USBArbitrator if started
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service bootlogs at depth 2
insserv:  loop involving service mountdevsubfs at depth 3
insserv:  loop involving service mountkernfs at depth 1
insserv:  loop involving service vmware-USBArbitrator at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apache2.2-common (2.2.16-6+squeeze6) ...
configured to not write apport reports
                                      insserv: warning: script 'K01vmware' missing LSB tags and overrides
insserv: warning: script 'K08vmware-USBArbitrator' missing LSB tags and overrides
insserv: warning: script 'vmware' missing LSB tags and overrides
insserv: warning: script 'vmware-USBArbitrator' missing LSB tags and overrides
insserv: There is a loop between service rmnologin and checkroot if started
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service hdparm at depth 2
insserv:  loop involving service hwclock at depth 6
insserv:  loop involving service keyboard-setup at depth 4
insserv:  loop involving service checkfs at depth 6
insserv:  loop involving service ifupdown-clean at depth 6
insserv:  loop involving service mtab at depth 6
insserv: There is a loop between service rmnologin and checkroot if started
insserv: There is a loop between service rmnologin and udev if started
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service vmware-USBArbitrator if started
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends oconfigured to not write apport reports
                                                                                      n rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmconfigured to not write apport reports
                                                          configured to not write apport reports
     configured to not write apport reports
                                           configured to not write apport reports
                                                                                 configured to not write apport reports
                            ware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service bootlogs at depth 2
insserv:  loop involving service mountdevsubfs at depth 3
insserv:  loop involving service mountkernfs at depth 1
insserv:  loop involving service vmware-USBArbitrator at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing apache2.2-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.16-6+squeeze6); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (= 2.2.16-6+squeeze6) | apache2-mpm-prefork (= 2.2.16-6+squeeze6) | apache2-mpm-event (= 2.2.16-6+squeeze6) | apache2-mpm-itk (= 2.2.16-6+squeeze6); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
  Package apache2-mpm-itk is not installed.
 apache2 depends on apache2.2-common (= 2.2.16-6+squeeze6); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-auth-mysql:
 libapache2-mod-auth-mysql depends on apache2.2-common (>= 2.2.3-3); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing libapache2-mod-auth-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-itk is not installed.
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not configured yet.
dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.1
 apache2.2-common
 apache2-mpm-prefork
 apache2
 libapache2-mod-auth-mysql
 libapache2-mod-php5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
i even get it when trying to use synaptic
> neil@crunchbang:~$ sudo apt-get install guake
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  guake
0 upgraded, 1 newly installed, 0 to remove and 32 not upgraded.
7 not fully installed or removed.
Need to get 164 kB of archives.
After this operation, 1,098 kB of additional disk space will be used.
Get:1 [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) squeeze/main guake amd64 0.4.2-3 [164 kB]
Fetched 164 kB in 1s (120 kB/s) 
Selecting previously deselected package guake.
(Reading database ... 125902 files and directories currently installed.)
Unpacking guake (from .../guake_0.4.2-3_amd64.deb) ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up mysql-server-5.1 (5.1.61-0+squeeze1) ...
Stopping MySQL database server: mysqld.
insserv: warning: script 'K01vmware' missing LSB tags and overrides
insserv: warning: script 'K08vmware-USBArbitrator' missing LSB tags and overrides
insserv: warning: script 'vmware' missing LSB tags and overrides
insserv: warning: script 'vmware-USBArbitrator' missing LSB tags and overrides
insserv: There is a loop between service rmnologin and checkroot if started
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service hdparm at depth 2
insserv:  loop involving service hwclock at depth 6
insserv:  loop involving service keyboard-setup at depth 4
insserv:  loop involving service checkfs at depth 6
insserv:  loop involving service ifupdown-clean at depth 6
insserv:  loop involving service mtab at depth 6
insserv: There is a loop between service rmnologin and checkroot if started
insserv: There is a loop between service rmnologin and udev if started
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service vmware-USBArbitrator if started
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service bootlogs at depth 2
insserv:  loop involving service mountdevsubfs at depth 3
insserv:  loop involving service mountkernfs at depth 1
insserv:  loop involving service vmware-USBArbitrator at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apache2.2-common (2.2.16-6+squeeze6) ...
configured to not write apport reports
                                      insserv: warning: script 'K01vmware' missing LSB tags and overrides
insserv: warning: script 'K08vmware-USBArbitrator' missing LSB tags and overrides
insserv: warning: script 'vmware' missing LSB tags and overrides
insserv: warning: script 'vmware-USBArbitrator' missing LSB tags and overrides
insserv: There is a loop between service rmnologin and checkroot if started
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service hdparm at depth 2
insserv:  loop involving service hwclock at depth 6
insserv:  loop involving service keyboard-setup at depth 4
insserv:  loop involving service checkfs at depth 6
insserv:  loop involving service ifupdown-clean at depth 6
insserv:  loop involving service mtab at depth 6
insserv: There is a loop between service rmnologin and checkroot if started
insserv: There is a loop between service rmnologin and udev if started
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service vmware-USBArbitrator if started
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facilityconfigured to not write apport reports
                                        `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Starting vmware-USBArbitrator depends on rmnologin and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service bootlogs at depth 2
insserv:  loop involving service mountdevsubfs at depth 3
insserv:  loop involving service mountkernfs at depth 1
insserv:  loop involving service vmware-USBArbitrator at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing apache2.2-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.16-6+squeeze6); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-auth-mysql:
 libapache2-mod-auth-mysql depends on apache2.2-common (>= 2.2.3-3); however:
  Package apache2.2-common is not configured yet.
configured to not write apport reports
                                      dpkg: error processing libapache2-mod-auth-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-itk is not installed.
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not configured yet.
configured to not write apport reports
                                      configured to not write apport reports
                                                                            dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on libapache2-mod-php5 | php5-cgi | php5; however:
  Package libapache2-mod-php5 is not configured yet.
  Package php5-cgi is not installed.
  Package php5 is not installed.
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Setting up guake (0.4.2-3) ...
configured to not write apport reports
                                      Processing triggers for python-central ...
Errors were encountered while processing:
 mysql-server-5.1
 apache2.2-common
 apache2-mpm-prefork
 libapache2-mod-auth-mysql
 libapache2-mod-php5
 mysql-server
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

i cant install anything now !
same errors!
did i break something ?

---

### Post by d4m1r on 2012-04-07
So I take it you are trying to install mysql on a Ubuntu Virtual Container (being run in a VMware box)?

mysqld = MySQL

Apache comes preinstalled with all versions of Ubuntu Server (package name is apache2 specifically) as far as I know..

---

### Post by CharlesA on 2012-04-07
Apache is only installed by default if you select it to be installed on a server install.

---

### Post by neil_1 on 2012-04-07
> **d4m1r said:**
> So I take it you are trying to install mysql on a Ubuntu Virtual Container (being run in a VMware box)?

mysqld = MySQL

Apache comes preinstalled with all versions of Ubuntu Server (package name is apache2 specifically) as far as I know..
no.
i'm installing it no my host (desktop)

> **CharlesA said:**
> Apache is only installed by default if you select it to be installed on a server install.
its a desktop :/

---

### Post by neil_1 on 2012-04-07
Solved (partially)

Vmware caused the conflict for some reason.
I uninstalled it, installed what i wanted and re-installed vmware :)

---

### Post by neil_1 on 2012-07-03
btw theres a fix for this one
```

Probably a cleaner way to approach this is to use /etc/insserv/overrides. Do the following:

 

Create /etc/insserv/overrides/vmware with the following:

 
### BEGIN INIT INFO
# Provides:          vmware
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 5
# Default-Stop:      2 3 5
# Short-Description: VMware VMX service for virtual machines
# Description:       Allows running of VMware virtual machines.                                    
### END INIT INFO

 

Create /etc/insserv/overrides/vmware-USBArbitrator with the following:

 

### BEGIN INIT INFO

# Provides:          vmware-USBArbitrator

# Required-Start:    $remote_fs $syslog vmware

# Required-Stop:     $remote_fs $syslog vmware

# Default-Start:     2 3 5

# Default-Stop:      2 3 5

# Short-Description: Start daemon when vmware starts

# Description:       Enable service provided by daemon.

### END INIT INFO

 

Then run 'chmod +x /etc/insserv/overrides/vmware*

 

This prevents the fix from being broken with an update to the shipped init.d script and my fix your USB problem. Since I don't use USB in a VM, I can't test it.

 

```

---

