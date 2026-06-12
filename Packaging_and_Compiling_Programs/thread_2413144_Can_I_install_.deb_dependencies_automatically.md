---
title: "Can I install .deb dependencies automatically?"
date: 2019-02-21
forum: Packaging and Compiling Programs
---

### Post by harrylad on 2019-02-21
I have created a simple deb package based on this tutorial [https://blog.heckel.xyz/2015/10/18/how-to-create-debian-package-and-debian-repository/](https://blog.heckel.xyz/2015/10/18/how-to-create-debian-package-and-debian-repository/)

This package depends on curl and jq.

When I install the package like so:
 
    > 
**sudo apt install netutils** 
   Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    netutils is already the newest version (1.3.0).
    You might want to run 'apt-get -f install' to correct these:
    [B]The following packages have unmet dependencies:
     netutils : Depends: curl
                   Depends: jq[/B]
    E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


  Then when I run the following I am able to install the dependencies:
  >  
 **sudo apt-get -f install**
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Correcting dependencies... Done
    The following packages were automatically installed and are no longer required:
    blah blah
    x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev
    blah blah
    Use 'sudo apt autoremove' to remove them.
    The following additional packages will be installed:
    curl jq
    The following NEW packages will be installed:
    curl jq
blah blah
**Setting up curl (7.47.0-1ubuntu2.12) ...**
**Setting up jq (1.5+dfsg-1ubuntu0.1) ...**
Setting up netutils (1.3.0) ...


How can I create/modify this package to that the depenencies curl, jq (Or whatever dependencies) are installed automatically?
Can I even do this? Or is there a different package I need to use to do this?

---

### Post by again? on 2019-02-21
Put depends in the control file.
eg this is the control file from a deb I made some time ago.
```
Package: conkytimer
Version: 0.1-3
Architecture: amd64
Maintainer: xxxxxxxx
Installed-Size: 686
[COLOR="#FF0000"]Depends: sox, conky-all[/COLOR]
Section: utils
Priority: optional
Description: Countdown timer for the unity launcher.
 Conkytimer uses a unity quicklist to select preset countdown
 durations and displays the output to the unity panel using conky.
```

---

### Post by harrylad on 2019-02-22
Sorry i did not mention that this is already in the control file as per the example:

> 
Source: netutils
Section: unknown
Priority: optional
Maintainer: unknown <info@test.com>
Build-Depends: debhelper (>=9)
Standards-Version: 3.9.6
Homepage: <insert the upstream URL, if relevant>
#Vcs-Git: git://anonscm.debian.org/collab-maint/netutils.git
#Vcs-Browser: [https://anonscm.debian.org/cgit/collab-maint/netutils.git](https://anonscm.debian.org/cgit/collab-maint/netutils.git)


Package: netutils
Architecture: any
**Depends: ${shlibs:Depends}, ${misc:Depends}, curl, jq**
Description: Network management tools




Because I have included these in the Depends entry I get the message:

> [COLOR=#000000]*The following additional packages will be installed:*[/COLOR]
[B]sudo apt install netutils 
Reading package lists... Done
Building dependency tree
Reading state information... Done
netutils is already the newest version (1.3.0).
You might want to run 'apt-get -f install' to correct these:
[B]The following packages have unmet dependencies:
netutils : Depends: curl
Depends: jq
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/B][/B]

And then i NEED to run [B]apt-get -f install.

[/B]**My question is can I install these automatically without having to run ****apt-get -f install?**

---

### Post by again? on 2019-02-22
Not really an expert at deb packaging.
I fumbled my way through creating a ppa and building a couple of personal debs a number of years ago.
Perhaps compress your deb as a .tar.gz file and attach for others to check.

---

### Post by again? on 2019-02-22
[COLOR="#006400"][/COLOR][COLOR="#006400"][/COLOR][COLOR="#006400"][/COLOR]****Followed the blog and apt pulls in dependencies for me.
Updated the **control** file
```
Source: netutils
Section: unknown
Priority: optional
Maintainer: Glen <phil@example.com>
Build-Depends: debhelper (>= 10)
Standards-Version: 4.1.2
Homepage: <insert the upstream URL, if relevant>
#Vcs-Git: https://anonscm.debian.org/git/collab-maint/netutils.git
#Vcs-Browser: https://anonscm.debian.org/cgit/collab-maint/netutils.git

Package: netutils
Architecture: any
[COLOR="#FF0000"]Depends: ${shlibs:Depends}, ${misc:Depends}, curl, jq[/COLOR]
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>
```

 and **changelog** file
```
[COLOR="#FF0000"]netutils (1.2.0) unstable; urgency=medium

  * Added curl jq depends

 -- Glen <phil@example.com>  Sat, 23 Feb 2019 07:33:28 +0800[/COLOR]

netutils (1.1.0) unstable; urgency=medium

  * Added 'ipaddr' script

 -- Glen <phil@example.com>  Sat, 23 Feb 2019 07:27:28 +0800

netutils (1.0.0) unstable; urgency=medium

  * Initial Release.

 -- Glen <phil@example.com>  Fri, 22 Feb 2019 11:57:09 +0800
```


Looking again at your first post it appears you haven't specified the updated deb to install. (sudo apt install netutils)
The only netutils version apt knows about is what is already installed unless you followed the guide all the way through
and also created a local repository.

Try purging netutils curl and jq.
Then install with apt using the complete path to your updated deb.
eg
```
**[COLOR="#006400"]glen@Bionic:~/Debian/netutils$[/COLOR]** sudo apt purge netutils curl jq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjq1 libonig4
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  curl* jq* netutils*
0 to upgrade, 0 to newly install, 3 to remove and 0 not to upgrade.
After this operation, 498 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 285644 files and directories currently installed.)
Removing netutils (1.2.0) ...
Removing curl (7.58.0-2ubuntu3.6) ...
Removing jq (1.5+dfsg-2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
```

***Note** use [COLOR="#FF0000"]full path to your latest deb version[/COLOR]. 
In the blog he used dpkg to install. Then used apt-get to fix dependencies.
Being from 2015, it was probably before you were able to install local debs with apt.
You only need to use apt to install using the full path to your latest deb. (apt will resolve dependencies... "dpkg -i" will not)
```
**[COLOR="#006400"]glen@Bionic:~/Debian/netutils$[/COLOR]** sudo apt install [COLOR="#FF0000"]$HOME/Debian/netutils_1.2.0_amd64.deb[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'netutils' instead of '/home/glen/Debian/netutils_1.2.0_amd64.deb'
The following additional packages will be installed:
  curl jq
The following NEW packages will be installed
  curl jq netutils
0 to upgrade, 3 to newly install, 0 to remove and 0 not to upgrade.
Need to get 204 kB/207 kB of archives.
After this operation, 498 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 /home/glen/Debian/netutils_1.2.0_amd64.deb netutils amd64 1.2.0 [2,296 B]
Get:2 http://ftp.iinet.net.au/pub/ubuntu bionic-updates/main amd64 curl amd64 7.58.0-2ubuntu3.6 [159 kB]
Get:3 http://ftp.iinet.net.au/pub/ubuntu bionic/universe amd64 jq amd64 1.5+dfsg-2 [45.6 kB]
Fetched 204 kB in 1s (289 kB/s)
debconf: unable to initialise frontend: Dialog
debconf: (Dialogue frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously unselected package curl.
(Reading database ... 285627 files and directories currently installed.)
Preparing to unpack .../curl_7.58.0-2ubuntu3.6_amd64.deb ...
Unpacking curl (7.58.0-2ubuntu3.6) ...
Selecting previously unselected package jq.
Preparing to unpack .../jq_1.5+dfsg-2_amd64.deb ...
Unpacking jq (1.5+dfsg-2) ...
Selecting previously unselected package netutils.
Preparing to unpack .../netutils_1.2.0_amd64.deb ...
Unpacking netutils (1.2.0) ...
Setting up jq (1.5+dfsg-2) ...
Setting up curl (7.58.0-2ubuntu3.6) ...
Setting up netutils (1.2.0) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...

**[COLOR="#006400"]glen@Bionic:~/Debian/netutils$[/COLOR] dpkg -L netutils**
/.
/usr
/usr/bin
/usr/bin/ipaddr
/usr/share
/usr/share/doc
/usr/share/doc/netutils
/usr/share/doc/netutils/README.Debian
/usr/share/doc/netutils/changelog.gz
/usr/share/doc/netutils/copyright

**[COLOR="#006400"]glen@Bionic:~/Debian/netutils$[/COLOR]** ipaddr
106.68.[COLOR="#696969"]xxx.xxx[/COLOR]
```

Check install version and listed dependencies.
If it shows "Status: install ok **unpacked**", it is installed but unconfigured due to dependencies not installed.
```
**[COLOR="#006400"]glen@Bionic:~/Debian/netutils$[/COLOR] apt show netutils**
Package: netutils
Version: 1.2.0
Status: install ok installed
Priority: optional
Section: unknown
Maintainer: Glen <phil@example.com>
Installed-Size: 12.3 kB
Depends: curl, jq
Homepage: <insert the upstream URL, if relevant>
Download-Size: unknown
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>
```

It's not necessary to create a local repository (section 3.4) unless you want your new local netutil deb versions
to be updated automatically when you run system updates.

Still not working, try downloading and installing my attached deb.

```
sudo apt purge netutils curl jq
cd ~/Downloads
tar xvzf netutils.tar.gz
sudo apt install ~/Downloads/netutils/netutils_1.2.0_amd64.deb
```

---

