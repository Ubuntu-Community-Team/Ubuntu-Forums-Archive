---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-12-10
forum: Philippine Team
---

### Post by neehs on 2010-12-10
Masters,

I always got this when make updating at terminal. Kindly advise. TIA

```
Setting up getdeb-repository (0.1-1~getdeb1) ...
--2010-12-10 14:35:00--  http://archive.getdeb.net/getdeb-archive.key
Resolving archive.getdeb.net... failed: Name or service not known.
wget: unable to resolve host address `archive.getdeb.net'
gpg: no valid OpenPGP data found.
dpkg: error processing getdeb-repository (--configure):
 subprocess installed post-installation script returned error exit status 2

```

---

### Post by sikander3786 on 2010-12-10
Please post the output of these commands.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

```
cat /etc/apt/sources.list
```

---

### Post by neehs on 2010-12-10
Hi sikander3786, Thank you for your response. However output below;

First command & second got this output:

```
sh@sh-desktop:~$ sudo dpkg --configure -a
Setting up getdeb-repository (0.1-1~getdeb1) ...
--2010-12-10 16:14:19--  http://archive.getdeb.net/getdeb-archive.key
Resolving archive.getdeb.net... failed: Name or service not known.
wget: unable to resolve host address `archive.getdeb.net'
gpg: no valid OpenPGP data found.
dpkg: error processing getdeb-repository (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 getdeb-repository


sh@sh-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglew1.5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up getdeb-repository (0.1-1~getdeb1) ...
--2010-12-10 16:16:13--  http://archive.getdeb.net/getdeb-archive.key
Resolving archive.getdeb.net... failed: Name or service not known.
wget: unable to resolve host address `archive.getdeb.net'
gpg: no valid OpenPGP data found.
dpkg: error processing getdeb-repository (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 getdeb-repository
E: Sub-process /usr/bin/dpkg returned an error code (1)
sh@sh-desktop:~$ 

```

---

### Post by sikander3786 on 2010-12-10
Try removing that package.

```
sudo apt-get remove --purge getdeb-repository
```

---

### Post by neehs on 2010-12-10
Thank you so much sikander3786. Its working ok.

---

### Post by sikander3786 on 2010-12-11
> **neehs said:**
> Thank you so much sikander3786. Its working ok.
You are Welcome :-)

Glad to know that it is fixed. You can now mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by zaid zh on 2011-10-08
plz hellp me the pc cant download any thing from ubuntu software center and if i update give me run apt apt-install-f
sudo apt-get install -f
[sudo] password for zaid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  mesa-utils unity-2d-panel libqtgconf1 wine1.3-gecko fortunes-min
  libdesktop-agnostic-cfg-gconf unity-2d-launcher linux-headers-2.6.38-8
  libunity-2d-private0 libnspr4-0d libqtbamf1 fortune-mod libqtdee2 librecode0
  libdesktop-agnostic-vfs-gio libdesktop-agnostic-fdo-glib unity-2d-spread
  linux-headers-2.6.38-8-generic unity-2d-places
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libogremain-1.7.3
Suggested packages:
  libogreproperty-1.7.3 libogrertshadersystem-1.7.3
The following NEW packages will be installed:
  libogremain-1.7.3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0 B/2,875 kB of archives.
After this operation, 8,249 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 242971 files and directories currently installed.)
Unpacking libogremain-1.7.3 (from .../libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb (--unpack):
 trying to overwrite '/etc/OGRE/plugins.cfg', which is also in package libogremain-1.6.4 1.6.4.dfsg1-1ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
zaid@zaidzh-HP-Compaq-6710b-GC045ES-ABV:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  mesa-utils unity-2d-panel libqtgconf1 wine1.3-gecko fortunes-min
  libdesktop-agnostic-cfg-gconf unity-2d-launcher linux-headers-2.6.38-8
  libunity-2d-private0 libnspr4-0d libqtbamf1 fortune-mod libqtdee2 librecode0
  libdesktop-agnostic-vfs-gio libdesktop-agnostic-fdo-glib unity-2d-spread
  linux-headers-2.6.38-8-generic unity-2d-places
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libogremain-1.7.3
Suggested packages:
  libogreproperty-1.7.3 libogrertshadersystem-1.7.3
The following NEW packages will be installed:
  libogremain-1.7.3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0 B/2,875 kB of archives.
After this operation, 8,249 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 242971 files and directories currently installed.)
Unpacking libogremain-1.7.3 (from .../libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb (--unpack):
 trying to overwrite '/etc/OGRE/plugins.cfg', which is also in package libogremain-1.6.4 1.6.4.dfsg1-1ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by matt_symes on 2011-10-08
Hi

Try this. Open a terminal and type
[FONT=monospace]
[/FONT]```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb
```

Then type 

```
sudo apt-get autoremove
```

Lastly type

```
sudo apt-get update
```

Kind regards

---

### Post by zaid zh on 2011-10-09
thanx its work thank you :P

---

### Post by kaio123 on 2012-02-16
hi guys i am getting a similar error while installing mythtv. i know its not a mythtv issue since i probably deleted something in mysql out of frustation. i tried all the methods mentioned on this thread. Can anyone help ?


=================================

start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mysql-server; however:
  Package mysql-server is not configured yet.
  Package mysql-server-5.1 which provides mysql-server is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                No apport report written because the error message indicates its a followup error from a previous failure.
                                Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
 mythtv

---

### Post by kaio123 on 2012-02-16
i have tried 
apt-get update
apt-get -f install mysql-server-5.1
apt-get clean
sudo apt-get remove --purge

---

### Post by DrZer0 on 2012-03-31
[SIZE=2][COLOR=Black]Hi , i had an error with nmap install package
```
drzero@drzero-pc:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of source-saintexploit:
 source-saintexploit depends on nmap; however:
  Package nmap is not installed.
dpkg: error processing source-saintexploit (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 source-saintexploit

``````
drzero@drzero-pc:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  nmap
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 345 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,620 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing /var/cache/apt/archives/nmap_5.61-bt1_i386.deb (--unpack):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/nmap_5.61-bt1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

``````

drzero@drzero-pc:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://jo.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://jo.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jo.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://jo.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://jo.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://jo.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://jo.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://jo.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://jo.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://jo.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://jo.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://jo.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://jo.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://jo.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

# BackTrack
deb http://all.repository.backtrack-linux.org revolution main microverse non-free testing
deb http://32.repository.backtrack-linux.org revolution main microverse non-free testing
deb http://source.repository.backtrack-linux.org revolution main microverse non-free testing

```[/COLOR][/SIZE]

---

### Post by DrZer0 on 2012-03-31
Fixed the problem detected in the package
apt-get autoremove

Done :)

---

### Post by von Papst on 2012-04-09
I'm getting the same error with postfix.
tried autoremove, update everything in this thread. Nothing helps for now. 

Below are results of dpkg and install -f commands. Any help appreciated.

madman@thor:/etc$ sudo dpkg --configure -a           
Setting up postfix (2.7.0-1ubuntu0.2) ...
setting synchronous mail queue updates: false
setting myorigin
setting destinations: mx.skydancers.org, thor.skydancers.local, localhost.skydancers.local, localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
/etc/aliases does not exist, creating it.
/var/lib/dpkg/info/postfix.postinst: 493: cannot create /etc/aliases: Directory nonexistent
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
madman@thor:/etc$ sudo apt-get install -f            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.7.0-1ubuntu0.2) ...
setting synchronous mail queue updates: false
setting myorigin
setting destinations: mx.skydancers.org, thor.skydancers.local, localhost.skydancers.local, localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
/etc/aliases does not exist, creating it.
/var/lib/dpkg/info/postfix.postinst: 493: cannot create /etc/aliases: Directory nonexistent
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by matt_symes on 2012-04-12
Hi
 
@von Papst
 
>  
/var/lib/dpkg/info/postfix.postinst: 493: cannot create /etc/aliases: Directory nonexistent
 

 
You could try creating the directory as that seems to be its problem
 
```
 
sudo mkdir /etc/aliases

```
 
If that does not work then you can try this to create asn empty file
 
```
sudo rmdir /etc/aliases
```
 
```
 
sudo touch /etc/aliases

```
 
And if that does not woirk the post the output of the postinst file.
 
```
 
cat /var/lib/dpkg/info/postfix.postinst

```
 
Kind regards

---

### Post by von Papst on 2012-04-12
Yeah just got it this morning. I overlooked that. It's working now.

---

### Post by gtstephenson on 2012-05-01
I have a similar issue. Pls see below. This caused by Adobe flash-plugin.

Suggestions?

Tom S.

root@toms-laptop:/# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 policykit sdparm libgda3-sqlite libpolkit-gnome0 linux-headers-2.6.32-24-generic libpolkit-dbus2 libdb4.6
  libpolkit-grant2 libpolkit2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 10.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 489143 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by matt_symes on 2012-05-02
Hi

> **gtstephenson said:**
> I have a similar issue. Pls see below. This caused by Adobe flash-plugin.

Suggestions?

Tom S.

```
root@toms-laptop:/# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 policykit sdparm libgda3-sqlite libpolkit-gnome0 linux-headers-2.6.32-24-generic libpolkit-dbus2 libdb4.6
  libpolkit-grant2 libpolkit2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 10.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 489143 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I assume this returns nothing  ?

```
update-alternatives --display iceape-flashplugin
```

Can you post the output of this command

```
cat /var/lib/dpkg/info/adobe-flashplugin.prerm
```

between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by gtstephenson on 2012-05-02
tstephenson@toms-laptop:~$ sudo update-alternatives --display iceape-flashplugin
update-alternatives: error: no alternatives for iceape-flashplugin.
tstephenson@toms-laptop:~$
tstephenson@toms-laptop:~$ cat /var/lib/dpkg/info/adobe-flashplugin.prerm
#!/bin/sh
# prerm script for adobe-flashplugin
#
# see: dh_installdeb(1)

set -e

# summary of how this script can be called:
#               * <prerm> `remove'
#               * <old-prerm> `upgrade' <new-version>
#               * <new-prerm> `failed-upgrade' <old-version>
#               * <conflictor's-prerm> `remove' `in-favour' <package> <new-version>
#               * <deconfigured's-prerm> `deconfigure' `in-favour'
#                 <package-being-installed> <version> `removing'
#                 <conflicting-package> <version>
# for details, see [http://www.debian.org/doc/debian-policy/](http://www.debian.org/doc/debian-policy/) or
# the debian-policy package

VARIANTS="iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons"

case "$1" in
        remove)
                for p in $VARIANTS; do
                        update-alternatives --remove "$p-flashplugin" /usr/lib/adobe-flashplugin/libflashplayer.so;
                done
                for p in $VARIANTS; do
                         [ `update-alternatives --list "$p-flashplugin" | wc -l` = 0 ]  && \
                                update-alternatives --remove-all "$p-flashplugin"
                done
                ;;
        upgrade|deconfigure)
                for p in $VARIANTS; do
                        update-alternatives --remove "$p-flashplugin" /usr/lib/adobe-flashplugin/libflashplayer.so;
                done
                for p in $VARIANTS; do
                         [ `update-alternatives --list "$p-flashplugin" | wc -l` = 0 ] && \
                                update-alternatives --remove-all "$p-flashplugin"
                done
                ;;
        failed-upgrade)
                for p in $VARIANTS; do
                        update-alternatives --remove "$p-flashplugin" /usr/lib/adobe-flashplugin/libflashplayer.so;
                done
                for p in $VARIANTS; do
                         [ `update-alternatives --list "$p-flashplugin" | wc -l` = 0 ] && \
                                update-alternatives --remove-all "$p-flashplugin"
                done
                ;;
        *)
                echo "prerm called with unknown argument \`$1'" >&2
                exit 1
        ;;
esac

# dh_installdeb will replace this with shell code automatically
# generated by other debhelper scripts.



exit 0

# vim: ts=2 sw=2
tstephenson@toms-laptop:~$
tstephenson@toms-laptop:~$ /var/lib/dpkg/info/adobe-flashplugin.prerm remove
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.

---

### Post by matt_symes on 2012-05-02
Hi
```

VARIANTS="iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons"

case "$1" in
        remove)
                for p in $VARIANTS; do
                        update-alternatives --remove "$p-flashplugin" /usr/lib/adobe-flashplugin/libflashplayer.so;
                done
                for p in $VARIANTS; do
                         [ `update-alternatives --list "$p-flashplugin" | wc -l` = 0 ]  && \
                                update-alternatives --remove-all "$p-flashplugin"
                done
                ;;
```This appears to be the problem. First let's check the state of the symlinks in the alternatives directory.

Open a terminal and type...

```
ls  -l /etc/alternatives/*flashplugin
```Small L after ls. Post back the results.

Also, from the terminal. please post back the output from the command below.

```
grep -H ^ /var/lib/dpkg/alternatives/*flashplugin
```One again i ask you to post in between code tags. It makes it easier for me to read.

Here's how you do it again. 

Post the output between code tags like this (this is how i do it)

[noparse]```
matthew@matthew-Aspire-7540 ~ % ls /etc/alternatives/*flashplugin
/etc/alternatives/mozilla-flashplugin
matthew@matthew-Aspire-7540 ~ %
```[/noparse]

to get output like this

```
matthew@matthew-Aspire-7540 ~ % ls /etc/alternatives/*flashplugin
/etc/alternatives/mozilla-flashplugin
matthew@matthew-Aspire-7540 ~ %
```Kind regards

---

### Post by gtstephenson on 2012-05-02
It appears the alternative doesn't exist.

[code]
 ls  -l /etc/alternatives/*flashplugin
ls: cannot access /etc/alternatives/*flashplugin: No such file or directory

[code]
grep -H ^ /var/lib/dpkg/alternatives/*flashplugin
grep: /var/lib/dpkg/alternatives/*flashplugin: No such file or directory

---

### Post by gtstephenson on 2012-05-02
> **matt_symes said:**
> Hi
```

VARIANTS="iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons"

case "$1" in
        remove)
                for p in $VARIANTS; do
                        update-alternatives --remove "$p-flashplugin" /usr/lib/adobe-flashplugin/libflashplayer.so;
                done
                for p in $VARIANTS; do
                         [ `update-alternatives --list "$p-flashplugin" | wc -l` = 0 ]  && \
                                update-alternatives --remove-all "$p-flashplugin"
                done
                ;;
```This appears to be the problem. First let's check the state of the symlinks in the alternatives directory.

Open a terminal and type...

```
ls  -l /etc/alternatives/*flashplugin
```Small L after ls. Post back the results.

Also, from the terminal. please post back the output from the command below.

```
grep -H ^ /var/lib/dpkg/alternatives/*flashplugin
```One again i ask you to post in between code tags. It makes it easier for me to read.

Here's how you do it again. 

Post the output between code tags like this (this is how i do it)

[noparse]```
matthew@matthew-Aspire-7540 ~ % ls /etc/alternatives/*flashplugin
/etc/alternatives/mozilla-flashplugin
matthew@matthew-Aspire-7540 ~ %
```[/noparse]

to get output like this

```
matthew@matthew-Aspire-7540 ~ % ls /etc/alternatives/*flashplugin
/etc/alternatives/mozilla-flashplugin
matthew@matthew-Aspire-7540 ~ %
```Kind regards


OK, I find the alternatives/*flashplugin doesn't exist.
perhaps this is easier to read.

[code]ls  -l /etc/alternatives/*flashplugin
ls: cannot access /etc/alternatives/*flashplugin: No such file or directory[code]

So obviously the grep will fail since there are no files that meet the criteria.
:-(

---

### Post by matt_symes on 2012-05-02
Hi

> **gtstephenson said:**
> OK, I find the alternatives/*flashplugin doesn't exist.
perhaps this is easier to read.

```
ls -l /etc/alternatives/*flashplugin
ls: cannot access /etc/alternatives/*flashplugin: No such file or directory[code]

So obviously the grep will fail since there are no files that meet the criteria.


That's not a problem. We can fix your system. I just wanted to check there would be nothing left hanging about.

Open a terminal and copy and paste these commands.

[CODE]sudo cp /var/lib/dpkg/info/adobe-flashplugin.prerm{,.old}
``````
echo 'exit 0;' | sudo tee /var/lib/dpkg/info/adobe-flashplugin.prerm
``````

sudo apt-get -f install
``````
sudo apt-get update
```Then try to install something

```
sudo apt-get install htop
```If that all has gone well then type....

```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm.old
```... otherwise post back any errors.

Just one last thing. it needs to be 

[noparse]```
...[ >>> / <<<< code][/noparse]

I.E 

[noparse][code]...
```[/noparse]

You missed the forward slash.

If you edit your last post and put the forward slash in you will see how it works and next time help save my eyesight :)

Kind regards

---

### Post by gtstephenson on 2012-05-03
Did not have good success.

```

tstephenson@toms-laptop:~$ sudo cp /var/lib/dpkg/info/adobe-flashplugin.prerm{,.old}
tstephenson@toms-laptop:~$ echo 'exit 0;' | sudo tee /var/lib/dpkg/info/adobe-flashplugin.prerm
exit 0;
tstephenson@toms-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24 policykit sdparm libgda3-sqlite libpolkit-gnome0 linux-headers-2.6.32-24-generic libpolkit-dbus2 libdb4.6
  libpolkit-grant2 libpolkit2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up adobe-flashplugin (10.0.12.36-1hardy1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-flashplugin) in auto mode.
update-alternatives: error: unable to make /usr/lib/firefox/plugins/flashplugin-alternative.so.dpkg-tmp a symlink to /etc/alternatives/firefox-flashplugin: No such file or directory
dpkg: error processing adobe-flashplugin (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
tstephenson@toms-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/ precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/ precise/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com lucid Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Get:2 http://us.archive.ubuntu.com lucid Release [57.2kB]
Get:3 http://us.archive.ubuntu.com lucid/main Packages [1,386kB]
Get:4 http://us.archive.ubuntu.com lucid/restricted Packages [6,208B]
Get:5 http://us.archive.ubuntu.com lucid/main Sources [659kB]
Get:6 http://us.archive.ubuntu.com lucid/restricted Sources [3,775B]
Fetched 2,112kB in 23s (89.6kB/s)
Reading package lists... Done
tstephenson@toms-laptop:~$ sudo apt-get install htop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package htop

```

Seems dpkg still returns an error.

Tom Stephenson

---

### Post by matt_symes on 2012-05-03
Hi

> 
The following packages will be **REMOVED**:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 10.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 489143 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):> 
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
**Setting up** adobe-flashplugin (**10.0.12.36-1hardy1**) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-flashplugin) in auto mode.
update-alternatives: error: unable to make /usr/lib/firefox/plugins/flashplugin-alternative.so.dpkg-tmp a symlink to /etc/alternatives/firefox-flashplugin: No such file or directory
dpkg: error processing adobe-flashplugin (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:These are actually different errors. 

The first one from your first post was trying to remove flash. 

The second one is trying to install it. This second error would have caused the first.

Another thing to note is:  10.0.12.36-1hardy1. 

What version of Ubuntu are you using ? Do you have hardy sources in your source file ?

```
cat /etc/apt/sources.list
```Kind regards

---

### Post by matt_symes on 2012-05-03
Hi

> 
The following packages will be **REMOVED**:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.

> 
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up adobe-flashplugin (**10.0.12.36-1hardy1**) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-flashplugin) in auto mode.
update-alternatives: error: unable to make /usr/lib/firefox/plugins/flashplugin-alternative.so.dpkg-tmp a symlink to /etc/alternatives/firefox-flashplugin: No such file or directory
dpkg: error processing adobe-flashplugin (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:

These are actually different errors. 

The first one from your first post was trying to remove flash. 

The second one is trying to install it. This second error would have caused the first.

Another thing to note is:  10.0.12.36-1hardy1. 

What version of Ubuntu are you using ? Do you have hardy sources in your source file ?

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by gtstephenson on 2012-05-03
```

tstephenson@toms-laptop:~$ cat /etc/apt/sources.list /etc/apt/sources.list.d/*
deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse
deb http://security.ubuntu.com/ubuntu/ natty-security restricted main multiverse
deb-src http://security.ubuntu.com/ubuntu/ natty-security restricted main multiverse
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.

```

I have just done upgrade(s) to get to 11.10 - But the OS announced that my crappy old Dell can't run unity. 1.8Gbz Pentium M and 512M RAM.

That's OK cause this is not my office system, just a piece of lab equipment. I have never upgraded till today. Was hoping the upgrade process would realize the database is wrong, that the adobe-flashplugin isn't required. But alas, the system still complains.

I'm going to remove the 12.04 CD from the list since the hardware won't support it.

Tom S

---

### Post by matt_symes on 2012-05-05
Hi

Let's try to remove the abode  install as opposed to fixing it.
[FONT=monospace]
[/FONT]```
echo 'exit 0;' | sudo tee /var/lib/dpkg/info/adobe-flashplugin.prerm
```

```
sudo apt-get remove --purge adobe-flashplugin
```

Post back any errors.

Kind regards

---

### Post by caveman978 on 2012-05-07
```

username@ubuntu:~$ echo 'exit 0;' | sudo tee /var/lib/dpkg/info/adobe-flashplugin.prerm
exit 0;

username@ubuntu:~$ sudo apt-get remove --purge adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  adobe-flashplugin*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 10.4 MB disk space will be freed.
Do you want to continue [Y/n]? 

(Reading database ... 217597 files and directories currently installed.)
Removing adobe-flashplugin ...
dpkg (subprocess): unable to execute installed pre-removal script (/var/lib/dpkg/info/adobe-flashplugin.prerm): Exec format error
dpkg: error processing adobe-flashplugin (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by caveman978 on 2012-05-07
I solved this by downloading the latest adobe-flashplugin and installing it.
I think I might be missing a partner PPA statement in my apt sources.

found here:
[http://www.ubuntuupdates.org/package/canonical_partner/oneiric/partner/base/adobe-flashplugin](http://www.ubuntuupdates.org/package/canonical_partner/oneiric/partner/base/adobe-flashplugin)


```

username@ubuntu:/tmp$ wget http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233-0oneiric1_i386.deb

--2012-05-07 11:41:40--  http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.233-0oneiric1_i386.deb
Resolving archive.canonical.com... 91.189.92.150, 91.189.92.191
Connecting to archive.canonical.com|91.189.92.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6591218 (6.3M) [application/x-debian-package]
Saving to: `adobe-flashplugin_11.2.202.233-0oneiric1_i386.deb'

100%[======================================>] 6,591,218    130K/s   in 48s     

2012-05-07 11:42:28 (135 KB/s) - `adobe-flashplugin_11.2.202.233-0oneiric1_i386.deb' saved [6591218/6591218]

username@ubuntu:/tmp$ sudo dpkg -i adobe-flashplugin_11.2.202.233-0oneiric1_i386.deb 

Selecting previously deselected package adobe-flashplugin.
(Reading database ... 217599 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.32.18-1 (using adobe-flashplugin_11.2.202.233-0oneiric1_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script (/var/lib/dpkg/info/adobe-flashplugin.prerm): Exec format error
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Unpacking replacement adobe-flashplugin ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode.
Processing triggers for hicolor-icon-theme ...

```

---

### Post by gtstephenson on 2012-05-07
Yes, that does solve the issue.

Thanks very much.

Tom Stephenson

---

### Post by howdous on 2012-05-28
With sudo apt-get install php5-gd I get the following error and for that matter whatever I try and install yields this same error:
---------------------------------------------
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  nginx-full: Depends: nginx-common (= 1.0.14-1ubuntu1ppa5~lucid) but it is not                                                                                                                                                              going to be installed
  php5-gd: Depends: libt1-5 (>= 5.1.0) but it is not going to be installed
           Depends: php5-common (= 5.3.2-1ubuntu4.15) but 5.3.2-1ubuntu4.14 is t                                                                                                                                                             o be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s                                                                                                                                                             olution).
---------------------------------------------

I then try the suggested 'apt-get -f install' and that yields the following:
---------------------------------------------
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-40-server linux-headers-2.6.32-40
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nginx-common
The following NEW packages will be installed:
  nginx-common
0 upgraded, 1 newly installed, 0 to remove and 32 not upgraded.
2 not fully installed or removed.
Need to get 0B/63.2kB of archives.
After this operation, 250kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 114660 files and directories currently installed.)
Unpacking nginx-common (from .../nginx-common_1.0.14-1ubuntu1ppa5~lucid_all.deb)                                                                                                                                                              ...
dpkg: error processing /var/cache/apt/archives/nginx-common_1.0.14-1ubuntu1ppa5~                                                                                                                                                             lucid_all.deb (--unpack):
 trying to overwrite '/etc/ufw/applications.d/nginx', which is also in package n                                                                                                                                                             ginx 0:1.0.14-1ubuntu1ppa5~lucid
Processing triggers for ufw ...
Errors were encountered while processing:
 /var/cache/apt/archives/nginx-common_1.0.14-1ubuntu1ppa5~lucid_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
---------------------------------------------------

I then try sudo dpkg --configure -a and that yields the following:

---------------------------------------------------
dpkg: dependency problems prevent configuration of nginx-full:
 nginx-full depends on nginx-common (= 1.0.14-1ubuntu1ppa5~lucid); however:
  Package nginx-common is not installed.
dpkg: error processing nginx-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nginx:
 nginx depends on nginx-full; however:
  Package nginx-full is not configured yet.
dpkg: error processing nginx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nginx-full
 nginx
---------------------------------------------------

With the following command I revealed my sources list - cat /etc/apt/sources.list

---------------------------------------------------

#
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ l                                                                                                                                                             ucid main restricted

# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ l                                                                                                                                                             ucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted unive                                                                                                                                                             rse multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted u                                                                                                                                                             niverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://software.virtualmin.com/gpl/ubuntu/](http://software.virtualmin.com/gpl/ubuntu/) virtualmin-lucid main
deb [http://software.virtualmin.com/gpl/ubuntu/](http://software.virtualmin.com/gpl/ubuntu/) virtualmin-universal main
deb [http://nginx.org/packages/ubuntu/](http://nginx.org/packages/ubuntu/) lucid nginx
deb-src [http://nginx.org/packages/ubuntu/](http://nginx.org/packages/ubuntu/) lucid nginx
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main
--------------------------------------------

I would really appreciate if someone could assist seeing that I cannot install anything on my server with this error and it's driving me up the wall.

---

### Post by matt_symes on 2012-05-28
Hi
 
If you are happy the file is the version you want then use the force overwrite switch.
 
I cannot remember the exact syntax but it's something along the lines of
 
```
 
sudo dpkg -i --force-overwrite /var/cache/apt/archives/nginx-common_1.0.14-1ubuntu1ppa5~ lucid_all.deb 

```
 
Kind regards

---

### Post by howdous on 2012-06-01
You are an absolute star. There was one space in your string that gave me trouble but fortunately I picked it up and now I am back in business again.:guitar:

My server is now happy and I can install & update again.

Thanks):P

> **matt_symes said:**
> Hi
 
If you are happy the file is the version you want then use the force overwrite switch.
 
I cannot remember the exact syntax but it's something along the lines of
 
```
 
sudo dpkg -i --force-overwrite /var/cache/apt/archives/nginx-common_1.0.14-1ubuntu1ppa5~ lucid_all.deb 

```
 
Kind regards

---

### Post by matt_symes on 2012-06-01
Hi

 > There was one space in your string that gave me trouble but fortunately I picked it

You've got to hate typo's :P. I'm glad it's sorted for you.

One thing i would like to point out is that one should look at the old file and the new file in the deb package - the one that the deb is trying to overwrite - just to make sure there will be no problems when overwriting the file.

You can use this to extract the deb file.

```
mkdir ~/temp_deb && cd $_ && dpkg-deb -x </path/to/packgae_name> .
```

and then use diff to compare them.

```
man diff /path/to/old-file /path/to/new/file
```

In many cases it may be OK to overwrite the file without checking but it never hurts to check, especially on a production machine.

Kind regards

---

### Post by bokas2012 on 2012-06-07
Hello, 

I have similar issue, but still i can't find  the decision. Please help.

```

120607 18:55:58  InnoDB: Shutdown completed; log sequence number 1595675
AppArmor parser error for /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/usr.sbin.mysqld at line 9: Could not open 'abstractions/mysql'
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by matt_symes on 2012-06-07
Hi

Open a terminal and type

```
ls -l /etc/apparmor.d/abstractions/mysql
```

Post the results back here.

Kind regards

---

### Post by bokas2012 on 2012-06-07
```

root@Ubuntu-1204-precise-32-minimal ~ # ls -l /etc/apparmor.d/abstractions/mysql
ls: cannot access /etc/apparmor.d/abstractions/mysql: No such file or directory


```

---

### Post by matt_symes on 2012-06-07
Hi

> **bokas2012 said:**
> ```

root@Ubuntu-1204-precise-32-minimal ~ # ls -l /etc/apparmor.d/abstractions/mysql
ls: cannot access /etc/apparmor.d/abstractions/mysql: No such file or directory


```

You're missing that file. You could try renstalling apparmor. It will be one of these packages; maybe the profiles package but i'm not sure. I don't know AppArmor well enough

```
 % apt-cache search apparmor               
apparmor - User-space parser utility for AppArmor
apparmor-docs - Documentation for AppArmor
apparmor-notify - AppArmor notification system
apparmor-profiles - Profiles for AppArmor Security policies
apparmor-utils - Utilities for controlling AppArmor
<snip>
```

The file should look silimar to this.

```
matthew@matthew-Aspire-7540 ~/my_virtual_machines/kernel_sources_general/linux-3.1-rc4
 % cat /etc/apparmor.d/abstractions/mysql                   
# ------------------------------------------------------------------
#
#    Copyright (C) 2002-2006 Novell/SUSE
#
#    This program is free software; you can redistribute it and/or
#    modify it under the terms of version 2 of the GNU General Public
#    License published by the Free Software Foundation.
#
# ------------------------------------------------------------------

   /var/lib/mysql/mysql.sock rw,
   /usr/share/mysql/charsets/ r,
   /usr/share/mysql/charsets/*.xml r,
matthew@matthew-Aspire-7540 ~/my_virtual_machines/kernel_sources_general/linux-3.1-rc4
 % 
```

and have permissions the same as this.

```
matthew@matthew-Aspire-7540 ~/my_virtual_machines/kernel_sources_general/linux-3.1-rc4
 % ls -l /etc/apparmor.d/abstractions/mysql
-rw-r--r-- 1 root root 483 Nov 15  2011 /etc/apparmor.d/abstractions/mysql
matthew@matthew-Aspire-7540 ~/my_virtual_machines/kernel_sources_general/linux-3.1-rc4
 % 
```

Kind regards

---

### Post by bokas2012 on 2012-06-08
```


root@Ubuntu-1204-precise-32-minimal ~ # ls -l /etc/apparmor.d/abstractions/mysql           
-rw-r--r-- 1 root root 483 Jun  8 11:24 /etc/apparmor.d/abstractions/mysql



```but  still 

```

root@Ubuntu-1204-precise-32-minimal ~ # apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mysql-server-5.5 (5.5.22-0ubuntu1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by matt_symes on 2012-06-09
Hi

At least that is the apparmor gone.

Try reinstalling the mysql-server package.

```
sudo apt-get install --reinstall  mysql-server
```

Kind regards

---

### Post by bokas2012 on 2012-06-09
The same :-(
```

root@Ubuntu-1204-precise-32-minimal ~ # sudo apt-get install --reinstall  mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.5 (5.5.22-0ubuntu1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Ubuntu-1204-precise-32-minimal ~ # 


```

---

### Post by matt_symes on 2012-06-09
Hi

> root@Ubuntu-1204-precise-32-minimal

I've just noticed your running a minimal install. 

I have never installed mysql-server on a minimal install but i can tell you it does install on Ubuntu 12.04 desktop so i think it may be due to the minimal install environment.

I think the next thing i would check would be to ensure all the dependencies are installed correctly.

[http://packages.ubuntu.com/precise/mysql-server-5.5](http://packages.ubuntu.com/precise/mysql-server-5.5)

I suspect that is why the mysql server apparmor profile was not installed either.

Do you get any feedback if you attempt to start the job from the command line ?

```
sudo /etc/init.d/mysql start
```

...or using upstart ?

```
sudo service mysql start
```

Kind regards

---

### Post by lovevn on 2012-06-12
hi everyone, I'm a new member. I have a problem:
When I type
```
sudo apt-get install
```, it appearence:
[IMG]http://www.freeimagehosting.net/newuploads/pj478.png[/IMG]
```

root@dell-Inspiron-N4050:~# sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
how must I do to fix this error?
please help me.

---

### Post by matt_symes on 2012-06-12
Hi

Welcome to the forums lovevn :)

First thing to try is to reboot your PC. Do you still get the same error after a reboot ?

Kind regards

---

### Post by marinoszak on 2012-06-12
Hello!,

i typed the command below
sudo apt-get remove --purge  tv-maxe

and after that when i try to use for example  apt-get autoremove it shows:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up setserial (2.17-46) ...
update-rc.d: warning: etc-setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: /etc/rcS.d: no such directory
dpkg: error processing setserial (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lirc:
 lirc depends on setserial; however:
  Package setserial is not configured yet.
dpkg: error processing lirc (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
             Errors were encountered while processing:
 setserial
 lirc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```sudo dpkg --configure -a
```
Setting up setserial (2.17-46) ...
update-rc.d: warning: etc-setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: /etc/rcS.d: no such directory
dpkg: error processing setserial (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lirc:
 lirc depends on setserial; however:
  Package setserial is not configured yet.
dpkg: error processing lirc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 setserial
 lirc
```sudo apt-get install -f
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up setserial (2.17-46) ...
update-rc.d: warning: etc-setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: /etc/rcS.d: no such directory
dpkg: error processing setserial (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of lirc:
 lirc depends on setserial; however:
  Package setserial is not configured yet.
dpkg: error processing lirc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 setserial
 lirc
```

EDIT:  I'm a new member TOO!

---

### Post by matt_symes on 2012-06-13
Hi

Welcome to the forums marinoszak :)

The problem package seems to be setserial.

> update-rc.d: warning: etc-setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: /etc/rcS.d: no such directory
dpkg: error processing setserial (--configure):

You really have no /etc/rcS.d directory ? Can we check this ?

Open a terminal and post the output of these two commands.

```
ls -d /etc/rc*
```

```
ls /etc/rcS.d/
```

Kind regards

---

### Post by marinoszak on 2012-06-13
Thank you for your respnse.
The outputs are below:

```
marinos@zak:~$ ls -d /etc/rc*
/etc/rc0.d  /etc/rc2.d  /etc/rc4.d  /etc/rc6.d
/etc/rc1.d  /etc/rc3.d  /etc/rc5.d  /etc/rc.local

```

```
marinos@zak:~$ sudo ls /etc/rcS.d/
ls: cannot access /etc/rcS.d/: No such file or directory
```

---

### Post by marinoszak on 2012-06-13
Is there any way to recreate /etc/rcS.d directory?
EDIT: Can i copy them form live cd instead?

---

### Post by matt_symes on 2012-06-13
Hi

> marinos@zak:~$ sudo ls /etc/rcS.d/
ls: cannot access /etc/rcS.d/: No such file or directory

That looks like a problem there. Here's mine.

```
matthew@matthew-Aspire-7540 ~ % ls -d /etc/rc*                 
**/etc/rcS.d** /etc/rc0.d  /etc/rc1.d  /etc/rc2.d  /etc/rc3.d  /etc/rc4.d  /etc/rc5.d  /etc/rc6.d  /etc/rc.local  
matthew@matthew-Aspire-7540 ~ % 

```

```
matthew@matthew-Aspire-7540 ~ % ls /etc/rcS.d 
README  S25brltty  S37apparmor  S47lm-sensors  S55urandom  S70x11-common  S75schroot
matthew@matthew-Aspire-7540 ~ %
```

I have no idea why you have no rcS.d directory in /etc. I have not come across this before :confused:

In the first instance let's try this.

Open a terminal and type

```
sudo mkdir /etc/rcS.d/
```

Then type

```
sudo apt-get install -f
```

Post back any errors.

Kind regards

---

### Post by marinoszak on 2012-06-13
Thank you very much for your effort.
As i mentioned before i tried to copy this directory from a live CD.
I can not say that this is the right choice but all previously errors just disappeared after that change.

> Another question:
is there any useful documentation i can read so that i can easily interpret errors that i may come across in the future? 

---

### Post by matt_symes on 2012-06-13
Hi

> **marinoszak said:**
> Thank you very much for your effort.
As i mentioned before i tried to copy this directory from a live CD.
I can not say that this is the right choice but all previously errors just disappeared after that change.

I'm glad it's fixed.

Recreating rcS.d was important for fixing your setserial error and so fixing apt. 

Copying the symlinks from the liveCD should create the default startup symlinks for you as the LiveCD should mirror your installed file system layout when you first installed Ubuntu.

You can double check by checking the symlinks point to valid startup files if you want.

```
ls -l /etc/rcS.d
```

You only problem you *may* have is if you have installed software since you installed Ubuntu that created links in /etc/rcS.d.

On my system i have two such files

```
lrwxrwxrwx 1 root root  20 Mar 12 21:07 S47lm-sensors -> ../init.d/lm-sensors
lrwxrwxrwx 1 root root  17 Jan  5 17:10 S75schroot -> ../init.d/schroot
```

This may or may not give you problem. 

You can try to determine if you have missed any with this.

```
grep "update-rc.d" /var/lib/dpkg/info/* | grep start | grep S
```

Case is important here and S is not the same as s.

To give you a heads up, here are mine...

```
matthew@matthew-Aspire-7540 ~ % grep "update-rc.d" /var/lib/dpkg/info/* | grep start | grep S
/var/lib/dpkg/info/apparmor.postinst:           update-rc.d apparmor start 37 S . >/dev/null
/var/lib/dpkg/info/brltty.postinst:             update-rc.d brltty start 25 S . >/dev/null
/var/lib/dpkg/info/initscripts.postinst:#update-rc.d bootlogd               start 05 S . >/dev/null || exit $?
/var/lib/dpkg/info/initscripts.postinst:update-rc.d urandom                start 55 S . start 30 0 6 . >/dev/null || exit $?
/var/lib/dpkg/info/initscripts.postinst:#update-rc.d stop-bootlogd-single   start 99 S . >/dev/null || exit $?
/var/lib/dpkg/info/lm-sensors.postinst: update-rc.d lm-sensors start 47 S . >/dev/null || exit $?
/var/lib/dpkg/info/module-init-tools.postinst:          update-rc.d module-init-tools start 15 S . >/dev/null
/var/lib/dpkg/info/x11-common.postinst:         update-rc.d x11-common start 70 S . >/dev/null
matthew@matthew-Aspire-7540 ~ % ls /etc/rcS.d 
README  S25brltty  S37apparmor  S47lm-sensors  S55urandom  S70x11-common  S75schroot
matthew@matthew-Aspire-7540 ~ %
```

As you can see, they don't totally match up but it can give you a heads up. (i.e bootlogd  {boot logging} is disabled on my system)

If you do notice any issues then you can just recreate the symlinks or reinstall the software depending on what you feel most comfortable with.

> Another question:
is there any useful documentation i can read so that i can easily interpret errors that i may come across in the future?

Many errors are pretty self explanatory. For all others there is Google or my preferred search engine duckduckgo :D.

Kind regards

---

### Post by marinoszak on 2012-06-14
```

marinos@zak:~$ grep "update-rc.d" /var/lib/dpkg/info/* | grep start | grep S
/var/lib/dpkg/info/apparmor.postinst:        update-rc.d apparmor start 37 S . >/dev/null
/var/lib/dpkg/info/brltty.postinst:        update-rc.d brltty start 25 S . >/dev/null
/var/lib/dpkg/info/initscripts.postinst:#update-rc.d bootlogd               start 05 S . >/dev/null || exit $?
/var/lib/dpkg/info/initscripts.postinst:update-rc.d urandom                start 55 S . start 30 0 6 . >/dev/null || exit $?
/var/lib/dpkg/info/initscripts.postinst:#update-rc.d stop-bootlogd-single   start 99 S . >/dev/null || exit $?
/var/lib/dpkg/info/x11-common.postinst:        update-rc.d x11-common start 70 S . >/dev/null

```There is no such difference with yours except from the sensors.
If there is any problem to any of my installed packages i will re-install them.

Now concerning the  search engine duckduckg, i think it worths a try regarding that is has less spam and more privacy as opposed with Google!

Thank you a lot!

---

### Post by sergiolop on 2012-08-08
Hi guys,

I would like some help if possible. Everythign was working fine untill I ran this
```
[FONT=Times New Roman]sudo aptitude install lsb[/FONT]
```
after that My computer kept on getting stuck and wasn't able to run startx. 
when startx was ran it would give me this error.
```

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.

 ddxSigGiveUp: Closing log

```
I tried to reinstall xorg by running
sudo apt-get install --reinstall xorg and I would get 
```

root@server:~# sudo apt-get install --reinstall xorg
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2,714 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 314193 files and directories currently installed.)
Preparing to replace xorg 1:7.6+12ubuntu1 (using .../xorg_1%3a7.6+12ubuntu1_i386                                                                                                                     .deb) ...
Unpacking replacement xorg ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Global parameter passdb backend found in service section!
Global parameter obey pam restrictions found in service section!
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Global parameter passwd chat found in service section!
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
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Global parameter passdb backend found in service section!
Global parameter obey pam restrictions found in service section!
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Global parameter passwd chat found in service section!
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
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr                                                                                                                     /share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              Setting up xorg (1                                                                                                                     :7.6+12ubuntu1) ...
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

IF someone could help me this would be great. Appreciate it thank you all.

---

### Post by saboteurkid on 2012-08-11
```
saboteurkid@KingOfJustice:~$ sudo apt-get install php5 php5-gd php5-mysql php5-curl php5-cli php5-cgi php5-dev
[sudo] password for saboteurkid: 
Sorry, try again.
[sudo] password for saboteurkid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5 is already the newest version.
php5-cgi is already the newest version.
php5-cgi set to manually installed.
php5-cli is already the newest version.
php5-curl is already the newest version.
php5-dev is already the newest version.
php5-gd is already the newest version.
php5-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Help me!!!

---

### Post by Halfsight on 2012-08-24
Ok, here is my ordeal. I noticed this thread has been getting results.

Original error:

```
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up fglrx-updates (2:8.960-0ubuntu1.1) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
Removing old fglrx-updates-8.960 DKMS files...

-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 8.960
Kernel:  3.2.0-27-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-27-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 8.960
Kernel:  3.2.0-29-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod............(bad exit status: 135)

DKMS: uninstall completed.

------------------------------
Deleting module version: 8.960
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-updates-8.960 DKMS files...
Building for 3.2.0-27-generic and 3.2.0-29-generic
Building for architecture x86_64
Building initial module for 3.2.0-27-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-27-generic/updates/dkms/

depmod....

DKMS: install completed.
Building initial module for 3.2.0-29-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-29-generic/updates/dkms/

depmod............(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 8.960
Kernel:  3.2.0-29-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-29-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod............(bad exit status: 135)

DKMS: uninstall completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing fglrx-updates (--configure):
 subprocess installed post-installation script returned error exit status 6
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle-updates:
 fglrx-amdcccle-updates depends on fglrx-updates; however:
  Package fglrx-updates is not configured yet.
dpkg: error processing fglrx-amdcccle-updates (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic
Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 fglrx-updates
 linux-image-generic
 fglrx-amdcccle-updates
 linux-generic
```

Removed all ATI Software

Now I am down to:

```
sudo dpkg --configure -a
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic

```

Please help.  ):P

---

### Post by matt_symes on 2012-08-25
Hi

@[Halfsight]("http://ubuntuforums.org/member.php?u=1723322"). Welcome to the forums.

> 
Running depmod. 
Failed to run depmodYou look to have a module problem and, hence, depmod is not working correctly.

Please post the output of

```
depmod -n
``````
apt-cache policy fglrx
```

If it is a lot of output the please just post the section around where it errors.

The post 

```
dpkg -l | grep fglrx
```That is a small L after dpkg

I am wondering if the ATI driver did not uninstall correctly and that is what is giving you the problems.

Couold you please pos the commands you used to uninstall that video driver.

Kind regards

---

### Post by matt_symes on 2012-08-25
Hi

@[sergiolop]("http://ubuntuforums.org/member.php?u=1717451") and @[saboteurkid]("http://ubuntuforums.org/member.php?u=1654241"). 

Do you both still need help ? I was away from the forums for a couple of weeks.

Kind regards

---

### Post by pmac95 on 2012-08-26
Thanks to both of you, your resolution really helped me to solve a similar, nagging problem

---

### Post by ganeshkanawade on 2012-08-29
I got the following error while installing the application.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package getdeb-repository
ganesh@ganesh-HP-xw6400-Workstation:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  default-jre-headless
Suggested packages:
  default-jre
The following NEW packages will be installed:
  default-jre-headless
0 upgraded, 1 newly installed, 0 to remove and 1109 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,328 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 129603 files and directories currently installed.)
Unpacking default-jre-headless (from .../default-jre-headless_1%3a1.6-43ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/default-jre-headless_1%3a1.6-43ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/lib/jvm/java-1.6.0-openjdk', which is also in package openjdk-6-jre-headless 6b24-1.11.3-1ubuntu0.11.10.1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/default-jre-headless_1%3a1.6-43ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help me to sort out this issue.

---

### Post by matt_symes on 2012-08-31
Hi

> **ganeshkanawade said:**
> I got the following error while installing the application.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package getdeb-repository
ganesh@ganesh-HP-xw6400-Workstation:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  default-jre-headless
Suggested packages:
  default-jre
The following NEW packages will be installed:
  default-jre-headless
0 upgraded, 1 newly installed, 0 to remove and 1109 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,328 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 129603 files and directories currently installed.)
Unpacking default-jre-headless (from .../default-jre-headless_1%3a1.6-43ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/default-jre-headless_1%3a1.6-43ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/lib/jvm/java-1.6.0-openjdk', which is also in package openjdk-6-jre-headless 6b24-1.11.3-1ubuntu0.11.10.1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/default-jre-headless_1%3a1.6-43ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help me to sort out this issue.

@ganeshkanawade. Welcome to the forums. 

The problem you are having is that the package you are trying to install has a file contained in it that has also been installed by a different package on your system. The package management system will not overwrite the file unless you explicitly instruct it to.

This is a safety precaution built into the package management system.

Open a terminal and type

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/default-jre-headless_1%3a1.6-43ubuntu2_i386.deb'
```

Enter your password. It will not be echoed to the screen. This is normal.

This will overwrite the old file with the new one.

Then type

```
sudo apt-get -f installReading package
```

This procedure is usually safe but you may want to take a look at the new conflicted files to ensure it is not going to cause you any problems with the old file.

If you have any problems then please post back.

Kind regards

---

### Post by jah2007 on 2012-11-09
Hi 
I need help with error message!


joel@Joel-PC:~$ sudo apt-get install -f
[sudo] password for joel: 
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Korrigerar beroenden.... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  kde-l10n-sv language-pack-kde-sv-base language-pack-kde-zh-hans-base
  calligra-l10n-engb calligra-l10n-sv calligra-l10n-zhcn language-pack-kde-en
  kde-l10n-engb language-pack-kde-sv language-pack-zh-hans-base kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans language-pack-kde-en-base
Använd "apt-get autoremove" för att ta bort dem.
Följande ytterligare paket kommer att installeras:
  libqt4-xmlpatterns
Följande paket kommer att uppgraderas:
  libqt4-xmlpatterns
1 att uppgradera, 0 att nyinstallera, 0 att ta bort och 22 att inte uppgradera.
15 är inte helt installerade eller borttagna.
Behöver hämta 0 B/1 033 kB arkiv.
Efter denna åtgärd kommer ytterligare 0 B utrymme användas på disken.
Vill du fortsätta [J/n]? J
dpkg: fel vid hantering av libqt4-xmlpatterns (--configure):
 libqt4-xmlpatterns:amd64 4:4.8.1-0ubuntu4.2 cannot be configured because libqt4-xmlpatterns:i386 is in a different version (4:4.8.1-0ubuntu4.3)
dpkg: fel vid hantering av libqt4-xmlpatterns:i386 (--configure):
 libqt4-xmlpatterns:i386 4:4.8.1-0ubuntu4.3 cannot be configured because libqt4-xmlpatterns:amd64 is in a different version (4:4.8.1-0ubuntu4.2)
dpkg: beroendeproblem förhindrar konfigurering av libqt4-declarative:i386:
 libqt4-declarative:i386 är beroende av libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-xmlpatterns:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-declarative:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-declarative:
 libqt4-declarative är beroende av libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.3), men:
  Versionen av libqt4-xmlpatterns på systemet är 4:4.8.1-0ubuntu4.2.
dpkg: fel vid hantering av libqt4-declarative (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqtgui4:i386:
 libqtgui4:i386 är beroende av libqt4-declarative (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-declarative:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqtgui4:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar koIngen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                                                              Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                         Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
    Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                               Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
          Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                                     nfigurering av libqtgui4:
 libqtgui4 är beroende av libqt4-declarative (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-declarative har inte konfigurerats ännu.
dpkg: fel vid hantering av libqtgui4 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-designer:
 libqt4-designer är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-designer (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-designer:i386:
 libqt4-designer:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-designer:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-opengl:
 libqt4-opengl är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-opengl (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-opengl:i386:
 libqt4-opengl:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-opengl:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-qt3support:
 libqt4-qt3support är beroende av libqt4-designer (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-designer har inte konfigurerats ännu.
 libqt4-qt3support är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-qt3support (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-qt3support:i386:
 libqt4-qt3support:i386 är beroende av libqt4-designer (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqt4-designer:i386 har inte konfigurerats ännu.
 libqt4-qt3support:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-qt3support:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-scripttools:i386:
 libqt4-scripttools:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-scripttools:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-svg:
 libqt4-svg är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-svg (--configure):
 beroendeproblem - lämnar okonfigurerad
dpkg: beroendeproblem förhindrar konfigurering av libqt4-svg:i386:
 libqt4-svg:i386 är beroende av libqtgui4 (= 4:4.8.1-0ubuntu4.3), men:
  Paketet libqtgui4:i386 har inte konfigurerats ännu.
dpkg: fel vid hantering av libqt4-svg:i386 (--configure):
 beroendeproblem - lämnar okonfigurerad
Fel uppstod vid hantering:
 libqt4-xmlpatterns
 libqt4-xmlpatterns:i386
 libqt4-declarative:i386
 libqt4-declarative
 libqtgui4:i386
 libqtgui4
 libqt4-designer
 libqt4-designer:i386
 libqt4-opengl
 libqt4-opengl:i386
 libqt4-qt3support
 libqt4-qt3support:i386
 libqt4-scripttools:i386
 libqt4-svg
 libqt4-svg:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any suggestions?

---

### Post by Mo3taz on 2013-02-25
i have This Problem Please any one help me 

> Setting up postfix (2.7.1-1+squeeze1) ...
insserv: warning: script 'K01nova-agent' missing LSB tags and overrides
insserv: warning: script 'nova-agent' missing LSB tags and overrides

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 178.239.177.109
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 178.239.177.109
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of postfix-mysql:
 postfix-mysql depends on postfix (= 2.7.1-1+squeeze1); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-mysql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 postfix-mysql
root@trial-server:~# apt-get install -f
Reading package lists... 25%
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up postfix (2.7.1-1+squeeze1) ...
insserv: warning: script 'K01nova-agent' missing LSB tags and overrides
insserv: warning: script 'nova-agent' missing LSB tags and overrides

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 178.239.177.109
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 178.239.177.109
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of postfix-mysql:
 postfix-mysql depends on postfix (= 2.7.1-1+squeeze1); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-mysql (--configure):
 dependency problems - leaving unconfigured
configured to not write apport reports
                                      configured to not write apport reports
                                                                            Errors were encountered while processing:
 postfix
 postfix-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by matt_symes on 2013-02-25
Hi

and welcome to the forums.

please post the out of

```
gedit /etc/postfix/main.cf
```

into your next post.

Kind regards

---

### Post by Mo3taz on 2013-02-25
This is File 

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = 178.239.177.109
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = debian, 178.239.177.109, localhost.239.177.109, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
html_directory = /usr/share/doc/postfix/html


Sorry for lating

---

### Post by matt_symes on 2013-02-25
Hi

Accorrding to this

[http://www.postfix.org/BASIC_CONFIGURATION_README.html#myhostname](http://www.postfix.org/BASIC_CONFIGURATION_README.html#myhostname)

> The [myhostname]("http://www.postfix.org/postconf.5.html#myhostname") parameter specifies the fully-qualified domain name of the machine running the Postfix system.   $[myhostname]("http://www.postfix.org/postconf.5.html#myhostname") appears as the default value in many other Postfix configuration parameters. 

> By default, [myhostname]("http://www.postfix.org/postconf.5.html#myhostname") is set to the local machine name.  If your local machine name is not in fully-qualified domain name form, or if you run Postfix on a virtual interface, you will have to specify the fully-qualified domain name that the mail system should use.

This is in your main.cfg file and it does not seem to like it.

> myhostname = 178.239.177.109

```
sudo nano /etc/postfix/main.cf
```

change the host name to your actual host name.

Press ctrl + o to save and ctrl + x to exit.

then type

```
sudo apt-get -f install
```

Kind regards

---

### Post by Mo3taz on 2013-02-25
It's Working Now Thank you

---

### Post by Mo3taz on 2013-02-27
This Problem Has Been come Again any one help me :)  when i Get  sudo apt-get install -f

It's Tell me 


> insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.locaconfigured to not write apport reports
 configured to not write apport reports
                                       configured to not write apport reports
                                                                             l and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service webmin and rc.local if started
insserv:  loop involving service rc.local at depth 23
insserv:  loop involving service webmin at depth 1
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing apache2.2-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.16-6+squeeze10); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker (= 2.2.16-6+squeeze10) | apache2-mpm-prefork (= 2.2.16-6+squeeze10) | apache2-mpm-event (= 2.2.16-6+squeeze10) | apache2-mpm-itk (= 2.2.16-6+squeeze10); however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-event is not installed.
  Package apache2-mpm-itk is not installed.
 apache2 depends on apache2.2-common (= 2.2.16-6+squeeze10); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
Setting up dbus (1.2.24-4+squeeze2) ...
insserv: warning: script 'K01nova-agent' missing LSB tags and overrides
insserv: warning: script 'S98webmin' missing LSB tags and overrides
insserv: warning: script 'webmin' missing LSB tags and overrides
insserv: warning: script 'nova-agent' missing LSB tags and overrides
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service webmin and rc.local if started
insserv:  loop involving service rc.local at depth 23
insserv:  loop involving service webmin at depth 1
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf2-common:
 gconf2-common depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing gconf2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2-4:
 libgconf2-4 depends on gconf2-common (>= 2.28); however:
  Package gconf2-common is not configured yet.
 libgconf2-4 depends on gconf2-common (<< 2.29); however:
  Package gconf2-common is not configured yet.
dpkg: error processing libgconf2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of configured to not write apport reports
         configured to not write apport reports
                                               configured to not write apport reports
     configured to not write apport reports
                                           configured to not write apport reports
 gconf2:
 gconf2 depends on libgconf2-4 (>= 2.27.0); however:
  Package libgconf2-4 is not configured yet.
 gconf2 depends on gconf2-common (>= 2.28); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on gconf2-common (<< 2.29); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
Setting up x11-common (1:7.5+8+squeeze1) ...
insserv: warning: script 'K01nova-agent' missing LSB tags and overrides
insserv: warning: script 'S98webmin' missing LSB tags and overrides
insserv: warning: script 'webmin' missing LSB tags and overrides
insserv: warning: script 'nova-agent' missing LSB tags and overrides
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service webmin and rc.local if started
insserv:  loop involving service rc.local at depth 23
insserv:  loop involving service webmin at depth 1
insserv: Starting webmin depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing x11-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libice6:
 libice6 depends on x11-common; however:
  Package x11-common is not configured yet.
dpkg: error processing libice6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsm6:
 libsm6 depends on libice6 (>= 1:1.0.0); however:
  Package libice6 is not configured yet.
dpkg: error processing libsm6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwxgtk2.8-0:
 libwxgtk2.8-0 depends on libsm6; however:
  Package libsm6 is not configured yet.
dpkg: error processing libwxgtk2.8-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnuplot-x11:
 gnuplot-x11 depends on libwxgtk2.8-0 (>= 2.8.10.1); however:
  Package libwxgtk2.8-0 is not confconfigured to not write apport reports
                                                                         configured to not write apport reports
                               configured to not write apport reports
                                                                     configured to not write apport reports
                           configured to not write apport reports
                                                                 configured to not write apport reports
                       configured to not write apport reports
                                                             igured yet.
dpkg: error processing gnuplot-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnuplot:
 gnuplot depends on gnuplot-x11 (>= 4.4.0-1.1); however:
  Package gnuplot-x11 is not configured yet.
dpkg: error processing gnuplot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.12.1-1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initscripts
 apache2.2-common
 apache2-mpm-prefork
 apache2
 dbus
 dbus-x11
 gconf2-common
 libgconf2-4
 gconf2
 x11-common
 libice6
 libsm6
 libwxgtk2.8-0
 gnuplot-x11
 gnuplot
 libgnomevfs2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by matt_symes on 2013-02-27
Hi

and welcome back :D

> apache2 depends on apache2.2-common (= 2.2.16-6+squeeze10); ?

A debian source. Are you using debian ?

Please post the output of

```
grep -v "^#" /etc/apt/sources.list /etc/apt/sources.list.d/*
```I want to have a look at your sources before even looking at your main problem.

Kind regards

---

### Post by Mo3taz on 2013-02-27
Iam use debian 

> # deb [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) squeeze main

deb [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) squeeze main
deb-src [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) squeeze main

deb [http://security.debian.org/](http://security.debian.org/) squeeze/updates main
deb-src [http://security.debian.org/](http://security.debian.org/) squeeze/updates main

# squeeze-updates, previously known as 'volatile'
deb [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) squeeze-updates main
deb-src [http://ftp.it.debian.org/debian/](http://ftp.it.debian.org/debian/) squeeze-updates main


---

### Post by matt_symes on 2013-02-27
Hi

Please post the output of your rc.local file.

On Ubuntu it's at

/etc/rc.local

but i am not sure where it is under debian

Kind regards

---

### Post by phantom74 on 2013-07-04
Hi guys, been having the same problem after trying to install a specific kernel to work with qemu/gns3 and juniper emulation.
now when i try to updgrade kernel and software i get the same error as previously stated. ran sudo apt-get -f update and sudo apt-get upgrade and i still get the error.

Tried a sudo apt-get autoremove and this is what i get:

phantom@dalila:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic : Depends: linux-headers-generic (= 3.2.0.45.54) but 3.2.0.48.58 is installed
 linux-image-generic : Depends: linux-image-3.2.0-45-generic but it is not installed
E: Unmet dependencies. Try using -f.
phantom@dalila:~$ sudo apt-get autoremove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic linux-image-3.2.0-48-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-48-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 1 newly installed, 0 to remove and 77 not upgraded.
9 not fully installed or removed.
Need to get 0 B/38.5 MB of archives.
After this operation, 150 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 486780 files and directories currently installed.)
Unpacking linux-image-3.2.0-48-generic (from .../linux-image-3.2.0-48-generic_3.2.0-48.74_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-48-generic_3.2.0-48.74_amd64.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/System.map-3.2.0-48-generic': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-48-generic /boot/vmlinuz-3.2.0-48-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-48-generic /boot/vmlinuz-3.2.0-48-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-44-generic...
P: Writing config for /boot/vmlinuz-3.2.0-41-generic...
P: Writing config for /boot/vmlinuz-3.2.0-40-generic...
P: Writing config for /boot/vmlinuz-3.2.0-39-generic...
P: Writing config for /boot/vmlinuz-3.2.0-38-generic...
P: Writing config for /boot/vmlinuz-3.2.0-37-generic...
P: Writing config for /boot/vmlinuz-3.2.0-36-generic...
P: Writing config for /boot/vmlinuz-3.2.0-35-generic...
P: Writing config for /boot/vmlinuz-3.2.0-34-generic...
P: Writing config for /boot/vmlinuz-3.2.0-33-generic...
P: Writing config for /boot/vmlinuz-3.2.0-32-generic...
P: Writing config for /boot/vmlinuz-3.2.0-31-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Writing config for Windows 7 (loader) on /dev/sda1...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-48-generic /boot/vmlinuz-3.2.0-48-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-48-generic_3.2.0-48.74_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
phantom@dalila:~$ 

Also noticed that /boot has now 0 bytes free space. can you help me out updating to the right kernel please.

~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        11G  4.4G  5.3G  46% /
udev            2.0G   12K  2.0G   1% /dev
tmpfs           791M  928K  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   84K  2.0G   1% /run/shm
/dev/sda7       5.7G  194M  5.3G   4% /tmp
/dev/sda5       388M  383M     0 100% /boot
/dev/sda8        15G  6.6G  7.4G  48% /usr
/dev/sda9        11G  4.3G  5.4G  45% /opt
/dev/sda11      686G  270G  382G  42% /home

thank you

---

### Post by Bimal_Gaudel on 2013-08-18
IS somebody watching?? Please help:





bimal@QUANTUM:~$ sudo dpkg --configure -a
[sudo] password for bimal: 
bimal@QUANTUM:~$ 
bimal@QUANTUM:~$ 
bimal@QUANTUM:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2013-08-19 02:04:32--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 202.166.193.8, 202.166.193.6
Connecting to download.oracle.com (download.oracle.com)|202.166.193.8|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) [following]
--2013-08-19 02:04:32--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.35.54.140
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.35.54.140|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2013-08-19 02:04:33--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|202.166.193.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'


     0K .....                                                 100% 1.13M=0.004s


2013-08-19 02:04:33 (1.13 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]


Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
bimal@QUANTUM:~$ 
bimal@QUANTUM:~$ 
bimal@QUANTUM:~$ 
bimal@QUANTUM:~$ 
bimal@QUANTUM:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/


# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise universe
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
bimal@QUANTUM:~$ 
bimal@QUANTUM:~$

---

### Post by matt_symes on 2013-08-21
Hi

@Bimal.

Do you still need help with this ?

If you do then try purging the oracle installer package.

Copy and paste this into the terminal.

```
sudo dpkg -P oracle-java7-installer
``` 

Also have you added any ppas ?

Please post the output of this command.

Copy and past it to insure there is no typos.

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Copy and paste the output from the terminal into your next post.

Once we have removed java we can look at installing it correctly.

In future, please start a new thread as this thread is getting old now. 

It's far more likely to be looked at by others if you start a new one.

Kind regards

---

### Post by usman2 on 2013-10-08
Hey guys,
Sorry for bumping into an old thread.. but I'm so tired of these stupid errors now - I really need someone's help to sort this out.

Please read this [http://askubuntu.com/questions/355277/ubuntu-12-04-installed-on-usb-but-i-cant-try-it-before-installing](http://askubuntu.com/questions/355277/ubuntu-12-04-installed-on-usb-but-i-cant-try-it-before-installing)

to know where I'm coming from.. I made it work after hours of research then I faced 'Unable to locate Error' finally solved and now this.. point is my 1tb ext. hdd got into RAW format and I want to recover the data/reapir the partition through Testdisk. It has some really important data and I can't just let it go.. but I keep recieving such error messages one after another.

Please know that I don't know how to use ubuntu, so guide like you would guide a newbie or a beginner.. 

> 
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
testdisk is already the newest version.
The following package was automatically installed and is no longer required:
  thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.99ubuntu13.2) ...
update-initramfs: deferring update (trigger activated)
lzma: (stdin): Cannot allocate memory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thank You.

---

### Post by matt_symes on 2013-10-11
Hi

Are you still having trouble ?

> [COLOR=#000000]*lzma: (stdin): Cannot allocate memory*[/COLOR]

What are the specs of your machine ? It looks like you may be running out of memory.

Anyway, testdisk is already installed by the looks of it.

> [COLOR=#000000]*testdisk is already the newest version.*[/COLOR]

Please post the output of

```
dpkg -C
```

That is a capital C above. It may return no output. Also post the output of the below.

```
sudo apt-get check
```

and finally...

```
dpkg -l initramfs-tools
```

Kind regards

---

### Post by diodeszener on 2013-11-11
> **matt_symes said:**
> Hi

Try this. Open a terminal and type
[FONT=monospace]
[/FONT]```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb
```


Kind regards

Thanks so much. It's work with me.

---

