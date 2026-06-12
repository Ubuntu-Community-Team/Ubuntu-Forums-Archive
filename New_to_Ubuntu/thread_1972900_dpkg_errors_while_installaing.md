---
title: "dpkg errors while installaing"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by mnamutso on 2012-05-04
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
MEMORY: 2GiB
OS-TYPE: 32bit
COMPUTER-TYPE: DELL XPS M1330

```
:~$ sudo apt-get install samba4

[sudo] password for ******: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-folks-0.6 gir1.2-polkit-1.0 libcaribou0 gir1.2-gkbd-3.0 caribou gjs gir1.2-caribou-1.0 gir1.2-telepathylogger-0.2 gir1.2-wnck-3.0
  mixxx-data gir1.2-gnomebluetooth-1.0 cups-pk-helper gir1.2-upowerglib-1.0 libmozjs185-1.0 gir1.2-telepathyglib-0.12 gir1.2-gee-1.0
  libgjs0c
Use 'apt-get autoremove' to remove them.
Suggested packages:
  bind9 phpldapadmin samba-gtk swat2
Recommended packages:
  samba4-dsdb-modules
The following NEW packages will be installed:
  samba4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/1,609 kB of archives.
After this operation, 11.5 MB of additional disk space will be used.
yPreconfiguring packages ...
Selecting previously deselected package samba4.
(Reading database ... 389531 files and directories currently installed.)
Unpacking samba4 (from .../samba4_4.0.0~alpha17~git20110807.dfsg1-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up postfix (2.8.5-2~build1) ...
Adding system user `postfix' (UID 119) ...
Adding new user `postfix' (UID 119) with group `postfix' ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/spool/postfix -g postfix -s /bin/false -u 119 postfix' returned error code 1. Exiting.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3-common:
 nagios3-common depends on bsd-mailx | mailx; however:
  Package bsd-mailx is not configured yet.
  Package mailx is not installed.
  Package bsd-mailx which provides mailx is not configured yet.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                      dpkg: error processing nagios3-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3-cgi:
 nagios3-cgi depends on nagios3-common (= 3.2.3-3); however:
  Package nagios3-common is not configured yet.
dpkg: error processing nagios3-cgi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios3-core:
 nagios3-core depends on nagios3-common (= 3.2.3-3); however:
  Package nagios3-common is not configured yet.
dpkg: error processing nagios3-core (--configure):
 dependency problems - leaving unconfigured
Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Administrator password will be set randomly!
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
 nagios3-common
 nagios3-cgi
 nagios3-core
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$
```

NB: Anything i try to install somehow ends up with:-
Errors were encountered while processing:
 postfix
 bsd-mailx
 nagios3-common
 nagios3-cgi
 nagios3-core

---

### Post by strask on 2012-05-04
Try posting the output of ```

sudo dpkg --audit
```
That may help shed some light on the problem.

---

### Post by mnamutso on 2012-05-08
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 nagios3-common       support files for nagios3
 bsd-mailx            simple mail user agent
 nagios3-core         A host/service/network monitoring and management system c
 nagios3-cgi          cgi files for nagios3

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 samba4               SMB/CIFS file, NT domain and active directory server (ver
 postfix              High-performance mail transport agent

---

