---
title: "Secure/private browser"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by cluelesswonder on 2012-02-26
Hihi!

I've been running linux mint for a while before installing ubuntu on my main computer but i'm still a total n00b.  I wanted to use a secure/private browser (or at least know how to do it) and am not really sure where to begin.  I downloaded Tor but I don't understand how to run it and just got a bunch of code when I opened what I thought would be the browser.
A quick search on this forum and on the web generally seems to mention Squid and Dansguardian.  I tried the: sudo apt-get install dansguardian squid
command that i read someone else recommending, but I ended up with this:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clamav clamav-base clamav-freshclam libclamav6 libtommath0 squid-common
  squid-langpack
Suggested packages:
  clamav-docs libclamunrar6 squidclient squid-cgi logcheck-database resolvconf
  winbind
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam dansguardian libclamav6 libtommath0
  squid squid-common squid-langpack
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.2 MB of archives.
After this operation, 55.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric/main squid-langpack all 20110707-1 [306 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric/main squid-common all 2.7.STABLE9-4ubuntu4 [267 kB]
Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric/main squid i386 2.7.STABLE9-4ubuntu4 [728 kB]
Get:4 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric/main libtommath0 i386 0.42.0-1 [47.5 kB]
Get:5 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates/main libclamav6 i386 0.97.3+dfsg-1ubuntu0.11.10.1 [4,009 kB]
Get:6 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates/main clamav-base all 0.97.3+dfsg-1ubuntu0.11.10.1 [31.1 MB]
Get:7 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates/main clamav-freshclam i386 0.97.3+dfsg-1ubuntu0.11.10.1 [114 kB]
Get:8 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates/main clamav i386 0.97.3+dfsg-1ubuntu0.11.10.1 [128 kB]
Get:9 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric/universe dansguardian i386 2.10.1.1-3ubuntu1 [487 kB]
Fetched 37.2 MB in 1min 58s (313 kB/s)                                         
Preconfiguring packages ...
Selecting previously deselected package squid-langpack.
(Reading database ... 166603 files and directories currently installed.)
Unpacking squid-langpack (from .../squid-langpack_20110707-1_all.deb) ...
Selecting previously deselected package squid-common.
Unpacking squid-common (from .../squid-common_2.7.STABLE9-4ubuntu4_all.deb) ...
Selecting previously deselected package squid.
Unpacking squid (from .../squid_2.7.STABLE9-4ubuntu4_i386.deb) ...
Selecting previously deselected package libtommath0.
Unpacking libtommath0 (from .../libtommath0_0.42.0-1_i386.deb) ...
Selecting previously deselected package libclamav6.
Unpacking libclamav6 (from .../libclamav6_0.97.3+dfsg-1ubuntu0.11.10.1_i386.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.97.3+dfsg-1ubuntu0.11.10.1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.97.3+dfsg-1ubuntu0.11.10.1_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.97.3+dfsg-1ubuntu0.11.10.1_i386.deb) ...
Selecting previously deselected package dansguardian.
Unpacking dansguardian (from .../dansguardian_2.10.1.1-3ubuntu1_i386.deb) ...
dpkg: error: version 'dansguardian_2.8.0.6-antivirus-6.4.4.1-4' has bad syntax: version number does not start with digit
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up squid-langpack (20110707-1) ...
Setting up squid-common (2.7.STABLE9-4ubuntu4) ...
Setting up squid (2.7.STABLE9-4ubuntu4) ...
Creating squid spool directory structure
2012/02/26 00:51:52| Creating Swap Directories
squid start/running, process 16524
Setting up libtommath0 (0.42.0-1) ...
Setting up libclamav6 (0.97.3+dfsg-1ubuntu0.11.10.1) ...
Setting up clamav-base (0.97.3+dfsg-1ubuntu0.11.10.1) ...
Setting up clamav-freshclam (0.97.3+dfsg-1ubuntu0.11.10.1) ...
 * Starting ClamAV virus database updater freshclam                      [ OK ] 
Setting up clamav (0.97.3+dfsg-1ubuntu0.11.10.1) ...
Setting up dansguardian (2.10.1.1-3ubuntu1) ...
Warning: The home directory /var/log/dansguardian you specified already exists.
Adding system user `dansguardian' (UID 115) ...
Adding new group `dansguardian' (GID 126) ...
Adding new user `dansguardian' (UID 115) with group `dansguardian' ...
The home directory `/var/log/dansguardian' already exists. Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/log/dansguardian' does not belong to the user that you are currently creating.

dpkg: error: version 'dansguardian_2.8.0.6-antivirus-6.4.4.1-4' has bad syntax: version number does not start with digit
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun
        this script.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place



little help?? :D

---

### Post by wildmanne39 on 2012-02-26
Hi, I believe most of your questions cab be answered by reading the stickies at the top of this forum.
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)
Thanks

---

### Post by Jake5 on 2012-02-26
This is only an example of what you need to do, not to be mistaken with the actual code you need to type, but its pretty close.


 Removal & Downgrade

Quote:

My preferred method is to simply disable the ppa in Software Sources and reinstall firefox:

Code:

sudo apt-get install --reinstall firefox

Alternatively, you can use ppa-purge. To uninstall a ppa and revert to the default version, run the following commands, changing the second line according to the ppa chosen:

Code:

sudo apt-get install ppa-purge sudo ppa-purge ppa:mozillateam/firefox-stable

---

