---
title: "Can't update or install new software:  package system is broken"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by dimitri6 on 2014-05-23
Hi all,

I'm experiencing an issue with my Ubuntu 14.04 64-bit system. I'm unable to install neither updates nor new software.  I get an error message:  "The package system is broken".  I tried pressing the "repair option" but the error persists. I was even instructed to run apt-get install -f in the terminal, again, to no avail.

I would appreciate any assistance to solve it.

Thank you in advance.

---

### Post by slickymaster on 2014-05-23
Can you please post back here, using the code tags for the effect, the output you get when in a terminal you run the following:```
sudo apt-get -f install
```and```
sudo dpkg --configure -a
```

---

### Post by dimitri6 on 2014-05-23
```
pa1067@Linux-Main:~$ sudo apt-get -f install
[sudo] password for pa1067: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  blt gstreamer0.10-gnonlin libamd2.2.0 libboost-filesystem1.53.0
  libboost-python1.53.0 libboost-regex1.53.0 libboost-signals1.53.0
  libboost-thread1.53.0 libdb5.1:i386 libdb5.1-java-jni libebml3 libfftw3-3
  libfftw3-long3 libgsoap3 libkdcraw22 liblavfile-2.0-0 liblavjpeg-2.0-0
  liblavplay-2.0-0 liblcms1:i386 libllvm3.3:i386 liblua5.1-0 libmarblewidget16
  libmatroska5 libmng1:i386 libmpeg2encpp-2.0-0 libmplex2-2.0-0 libplot2c2
  libpthread-stubs0 libtasn1-3:i386 libtcl8.5 libtk8.5 libumfpack5.4.0
  libwebp4 linux-headers-3.11.0-19 linux-headers-3.11.0-19-generic
  nvidia-settings-319 python-central python-xkit tcl8.5 tk8.5 wine-gecko1.4
  wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tzdata
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
1 not fully installed or removed.
Need to get 0 B/181 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 351200 files and directories currently installed.)
Preparing to unpack .../tzdata_2014c-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2014c-0ubuntu0.14.04) over (2014b-1) ...
dpkg: error processing archive /var/cache/apt/archives/tzdata_2014c-0ubuntu0.14.04_all.deb (--unpack):
 unable to make backup link of `./usr/share/zoneinfo/Australia/West' before installing new version: Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2014c-0ubuntu0.14.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
pa1067@Linux-Main:~$
```

---

### Post by dimitri6 on 2014-05-23
```
pa1067@Linux-Main:~$ sudo dpkg --configure -a
[sudo] password for pa1067: 
dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2014c-0ubuntu0.14.04); however:
  Version of tzdata on system is 2014b-1.

dpkg: error processing package tzdata-java (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata-java
pa1067@Linux-Main:~$
```

---

### Post by slickymaster on 2014-05-23
Try to run the following```
sudo dpkg-reconfigure tzdata --force
```and again post back the output you get.

---

### Post by dimitri6 on 2014-05-23
pa1067@Linux-Main:~$ sudo dpkg-reconfigure tzdata --force
[sudo] password for pa1067: 

Current default time zone: 'America/Montreal'
Local time is now:      Fri May 23 13:14:17 EDT 2014.
Universal Time is now:  Fri May 23 17:14:17 UTC 2014.

pa1067@Linux-Main:~$

---

### Post by slickymaster on 2014-05-23
Now try to run```
sudo apt-get update && sudo apt-get update
```Once again post the output you get.

---

### Post by dimitri6 on 2014-05-23
I ran sudo apt-get update && sudo apt-get update

But it still get "The package system is broken" when I try to update the system or attempt to install software.

---

### Post by slickymaster on 2014-05-23
Ok, let's try this:```
wget http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2014c-0ubuntu0.14.04_all.deb
```Then cd into the folder where you download it and run```
sudo dpkg -i tzdata_2014c-0ubuntu0.14.04_all.deb
```and afterwards```
sudo apt-get install -f
```Please post back the output you get.

---

### Post by dimitri6 on 2014-05-23
pa1067@Linux-Main:~$ sudo dpkg -i tzdata_2014c-0ubuntu0.14.04_all.deb
[sudo] password for pa1067: 
(Reading database ... 351200 files and directories currently installed.)
Preparing to unpack tzdata_2014c-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2014c-0ubuntu0.14.04) over (2014b-1) ...
dpkg: error processing archive tzdata_2014c-0ubuntu0.14.04_all.deb (--install):
 unable to make backup link of `./usr/share/zoneinfo/Australia/West' before installing new version: Operation not permitted
Errors were encountered while processing:
 tzdata_2014c-0ubuntu0.14.04_all.deb
pa1067@Linux-Main:~$

---

### Post by dimitri6 on 2014-05-23
pa1067@Linux-Main:~$ sudo apt-get install -f
[sudo] password for pa1067: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  blt gstreamer0.10-gnonlin libamd2.2.0 libboost-filesystem1.53.0
  libboost-python1.53.0 libboost-regex1.53.0 libboost-signals1.53.0
  libboost-thread1.53.0 libdb5.1:i386 libdb5.1-java-jni libebml3 libfftw3-3
  libfftw3-long3 libgsoap3 libkdcraw22 liblavfile-2.0-0 liblavjpeg-2.0-0
  liblavplay-2.0-0 liblcms1:i386 libllvm3.3:i386 liblua5.1-0 libmarblewidget16
  libmatroska5 libmng1:i386 libmpeg2encpp-2.0-0 libmplex2-2.0-0 libplot2c2
  libpthread-stubs0 libtasn1-3:i386 libtcl8.5 libtk8.5 libumfpack5.4.0
  libwebp4 linux-headers-3.11.0-19 linux-headers-3.11.0-19-generic
  nvidia-settings-319 python-central python-xkit tcl8.5 tk8.5 wine-gecko1.4
  wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tzdata
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
1 not fully installed or removed.
Need to get 0 B/181 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 351200 files and directories currently installed.)
Preparing to unpack .../tzdata_2014c-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2014c-0ubuntu0.14.04) over (2014b-1) ...
dpkg: error processing archive /var/cache/apt/archives/tzdata_2014c-0ubuntu0.14.04_all.deb (--unpack):
 unable to make backup link of `./usr/share/zoneinfo/Australia/West' before installing new version: Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2014c-0ubuntu0.14.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
pa1067@Linux-Main:~$

---

### Post by slickymaster on 2014-05-23
> **dimitri6 said:**
> ```
pa1067@Linux-Main:~$ sudo dpkg -i tzdata_2014c-0ubuntu0.14.04_all.deb
[sudo] password for pa1067: 
(Reading database ... 351200 files and directories currently installed.)
Preparing to unpack tzdata_2014c-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2014c-0ubuntu0.14.04) over (2014b-1) ...
dpkg: error processing archive tzdata_2014c-0ubuntu0.14.04_all.deb (--install):
 unable to make backup link of `**[COLOR=#ff0000]./usr/share/zoneinfo/Australia/West[/COLOR]**' before installing new version: Operation not permitted
Errors were encountered while processing:
 tzdata_2014c-0ubuntu0.14.04_all.deb
pa1067@Linux-Main:~$
```

That's the source of your problem. 
Australia West is in the file list for Trusy (see [http://packages.ubuntu.com/trusty/all/tzdata/filelist](http://packages.ubuntu.com/trusty/all/tzdata/filelist)), the problem is that your deb package somehow is referring to _./usr/share/zoneinfo/_ instead of **/usr/share/zoneinfo/ **and honestly I'm not seeing a possible workaround to fix that.

You could try to file a bug in Launchpad against that package in [https://bugs.launchpad.net/ubuntu/+source/tzdata](https://bugs.launchpad.net/ubuntu/+source/tzdata)

---

### Post by dimitri6 on 2014-05-23
Thanks for you time, it's appreciated!

But I don't quite understand.  The problem that I can't install updates or software is that because one file is referring to a different timezone?  And that, what it appears to me a 'detail'  is enough to halt the system? WOW!

What if I change my timezone to Australia West? Will I be able to install new software?

Regardless, I don't understand how the time zone settings are related to the system update module!

---

### Post by Eric_Damhuis on 2014-05-24
This feels like the same problem....

~$ sudo apt-get autoremove
[sudo] password for eric: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsmbclient : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 python-samba : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
 samba-common-bin : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.1) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by bapoumba on 2014-05-24
From post #4 :
```
dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2014c-0ubuntu0.14.04); however:
  Version of tzdata on system is 2014b-1.

```

Using any ppa or other repo ?

```
apt-cache policy tzdata
```

---

### Post by dimitri6 on 2014-05-24
pa1067@Linux-Main:~$ apt-cache policy tzdata
tzdata:
  Installed: 2014b-1
  Candidate: 2014c-0ubuntu0.14.04
  Version table:
     2014c-0ubuntu0.14.04 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
 *** 2014b-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
pa1067@Linux-Main:~$

---

### Post by dimitri6 on 2014-05-24
Could this be the probem?  (some time ago I patched the kernel with the latest one -- for no reason )

pa1067@Linux-Main:~$ uname -a
Linux Linux-Main 3.14.1-031401-generic #201404141220 SMP Mon Apr 14 16:21:48 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
pa1067@Linux-Main:~$

But I was able to update, I recall.

Anyway, as I'm typing these lines I'm backing up everything for a dban low-level format and bare-metal re-install.

---

### Post by bapoumba on 2014-05-24
In the mean time, please try 
```
sudo apt-get upgrade tzdata
```

Having backups is always a good idea :)

---

### Post by dimitri6 on 2014-05-24
pa1067@Linux-Main:~$ sudo apt-get upgrade tzdata
[sudo] password for pa1067: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 tzdata-java : Depends: tzdata (= 2014c-0ubuntu0.14.04) but 2014b-1 is installed
E: Unmet dependencies. Try using -f.
pa1067@Linux-Main:~$

---

### Post by bapoumba on 2014-05-24
One question I had previously : are you using any ppa or third party repo ? 
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

[s]Not sure where this 2014c package from Utopic is coming from ..[/s]
Edit: 2014c is the version I have. Scratch my last comment. Utopic is 2014c1

---

### Post by dimitri6 on 2014-05-24
When I enter cat /etc/apt/sources.list

the terminal will close.

pa1067@Linux-Main:~$ ls /etc/apt/sources.list.d
atareao-atareao-saucy.list                google-chrome.list.distUpgrade
atareao-atareao-saucy.list.distUpgrade    google-chrome.list.save
atareao-atareao-saucy.list.save           kernel-ppa-ppa-trusty.list
cinelerra-ppa-ppa-saucy.list              kernel-ppa-ppa-trusty.list.save
cinelerra-ppa-ppa-saucy.list.distUpgrade  mixxx-mixxx-saucy.list
cinelerra-ppa-ppa-saucy.list.save         mixxx-mixxx-saucy.list.distUpgrade
dlynch3-ppa-saucy.list                    mixxx-mixxx-saucy.list.save
dlynch3-ppa-saucy.list.distUpgrade        owncloud-client.list
dlynch3-ppa-saucy.list.save               owncloud-client.list.distUpgrade
getdeb.list                               owncloud-client.list.save
getdeb.list.distUpgrade                   yktooo-ppa-saucy.list
getdeb.list.save                          yktooo-ppa-saucy.list.distUpgrade
google-chrome.list                        yktooo-ppa-saucy.list.save
pa1067@Linux-Main:~$

---

### Post by bapoumba on 2014-05-24
> **dimitri6 said:**
> When I enter cat /etc/apt/sources.list

the terminal will close.
That is very strange.. No error ?

All of these ppa are for saucy. As you say you are running trusty, you should disable all of them. 
> **dimitri6 said:**
> 
pa1067@Linux-Main:~$ ls /etc/apt/sources.list.d
atareao-atareao-saucy.list                google-chrome.list.distUpgrade
atareao-atareao-saucy.list.distUpgrade    google-chrome.list.save
atareao-atareao-saucy.list.save           kernel-ppa-ppa-trusty.list
cinelerra-ppa-ppa-saucy.list              kernel-ppa-ppa-trusty.list.save
cinelerra-ppa-ppa-saucy.list.distUpgrade  mixxx-mixxx-saucy.list
cinelerra-ppa-ppa-saucy.list.save         mixxx-mixxx-saucy.list.distUpgrade
dlynch3-ppa-saucy.list                    mixxx-mixxx-saucy.list.save
dlynch3-ppa-saucy.list.distUpgrade        owncloud-client.list
dlynch3-ppa-saucy.list.save               owncloud-client.list.distUpgrade
getdeb.list                               owncloud-client.list.save
getdeb.list.distUpgrade                   yktooo-ppa-saucy.list
getdeb.list.save                          yktooo-ppa-saucy.list.distUpgrade
google-chrome.list                        yktooo-ppa-saucy.list.save
pa1067@Linux-Main:~$
The syntax in the ppa is the same as for the sources.list. To disable a repo, you need to comment out all the lines, ie place a # at the beginning of each line.

To edit the first file :
```
sudo nano /etc/apt/sources.list.d/atareao-atareao-saucy.list

```
nano is a small editor working from the terminal. Add # in front of each line, then save with ctrl-o (letter o) and exit with ctrl-x.
You need to do this for each ppa, unless your Software Sources is working and you can just untick them from there.

Then read again the sources.list and try to upgrade :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dimitri6 on 2014-05-24
All lines already have a # in front:

  GNU nano 2.2.6             File: /etc/apt/sources.list.d/atareao-atareao-saucy.list                                

# deb [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) trusty main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) saucy main
# deb-src [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) saucy main

---

### Post by bapoumba on 2014-05-25
And have you had a look at the other ppa ? All of them ? What is the result of the update/upgrade with all ppa disabled ?

---

### Post by dimitri6 on 2014-05-25
Thank you all for your help.  I finally wiped the Hard Drive (with dban) and re-installed from scratch.  When I updraded to 14.04 LTS from 13.10 it gave a bunch of errors, which I thaugh they were fixed.  It appears that there were many lefovers from 13.04 interfering.  Too complicated and time consuming to troubleshoot.

I backed up the home folder and I re-installed. Now it works like a champ.

Thanks all for your suggestions!

---

### Post by bapoumba on 2014-05-25
Hey, that is one way to do it :)

Next time you upgrade, please disable _all_ your ppas. Some play nice on upgrades, some do not. Even use ppa-purge to revert the packages you may have installed to the default ones.
[https://launchpad.net/ubuntu/+source/ppa-purge](https://launchpad.net/ubuntu/+source/ppa-purge)
[http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html)

---

