---
title: "snort &amp; installing packages"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by mike22 on 2008-09-21
Everytime I try to install a package from synaptic or install it from a terminal I get a snort error. Snort I'm pretty sure is the program I tried to install a few days ago. Here is the snort error that I receive.


```
michael@ubuntu:~$ sudo apt-get install vsftpd
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  texlive-base texlive texlive-fonts-recommended texlive-common tofrodos
  texlive-base-bin tetex-bin tidy libtidy-0.99-0 texlive-latex-recommended
  texlive-latex-base winbind texlive-doc-base tex-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  vsftpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 96.8kB of archives.
After this operation, 401kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/main vsftpd 2.0.6-1ubuntu1 [96.8kB]
Fetched 96.8kB in 1s (51.3kB/s)
Selecting previously deselected package vsftpd.
(Reading database ... 135753 files and directories currently installed.)
Unpacking vsftpd (from .../vsftpd_2.0.6-1ubuntu1_i386.deb) ...
Setting up snort (2.7.0-14) ...
 * Stopping Network Intrusion Detection System  snort                            * No running snort instance found
 * Starting Network Intrusion Detection System  snort                            * /etc/snort/db-pending-config file found
 * Snort will not start as its database is not yet configured.
 * Please configure the database as described in
 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 6
Setting up vsftpd (2.0.6-1ubuntu1) ...
Adding system user `ftp' (UID 120) ...
Adding new user `ftp' (UID 120) with group `nogroup' ...
Not creating home directory `/home/ftp'.
 * Starting FTP server: vsftpd                                           [ OK ] 

Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@ubuntu:~$ 

```

---

### Post by Tatty on 2008-09-21
It seems to be struggling to install snort for some reason.

These lines:

```
 * Snort will not start as its database is not yet configured.
 * Please configure the database as described in
 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config

```

make me think that you may need to do the above before going back to finish the installation.  Once you have configured the database run
```
sudo apt-get install -f
```
To try to get the install to finish.


Did you install this from the repos?  If so then there is a bug report for this issue here [https://bugs.launchpad.net/ubuntu/+source/snort/+bug/222091](https://bugs.launchpad.net/ubuntu/+source/snort/+bug/222091)  It may be worth you subscribing to this to let the devs know this issue is still occouring.

---

### Post by mike22 on 2008-09-21
When I attempt to install snort, I get a snort "configure error."

```
michael@ubuntu:~$ sudo apt-get install -f
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  texlive-base texlive texlive-fonts-recommended texlive-common tofrodos
  texlive-base-bin tetex-bin tidy libtidy-0.99-0 texlive-latex-recommended
  texlive-latex-base winbind texlive-doc-base tex-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up snort (2.7.0-14) ...
 * Stopping Network Intrusion Detection System  snort                            * No running snort instance found
 * Starting Network Intrusion Detection System  snort                            * /etc/snort/db-pending-config file found
 * Snort will not start as its database is not yet configured.
 * Please configure the database as described in
 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@ubuntu:~$ 
 
```

---

### Post by oldos2er on 2008-09-21
I think you need to do what Tatty suggested, and do what the error message is telling you to do:

* Please configure the database as described in
* /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config

---

### Post by mike22 on 2008-09-21
> **oldos2er said:**
> I think you need to do what Tatty suggested, and do what the error message is telling you to do:

* Please configure the database as described in
* /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config

Didn't notice that sorry.

---

### Post by srinu.mca5 on 2011-03-04
when i start my snort with /etc/init.d/snort start is gives the following errors..what should i do....Please reply to me...

 Please configure the database as described in
* /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config

---

