---
title: "Following recommendation from 'sudo apt-get install apt-show-versions' breaks skype"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by desconocido on 2014-02-02
I have just installed Ubuntu 12.04 (amd64 version) after using 9.10 and have installed gnome-shell and removed unity.
I downloaded skype from 
[http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/)
and chose the option 'Ubunti 12.04 (Multiarch)'
This produced file skype-ubuntu-precise_4.2.0.13-1_i386.deb
I installed this with gdebi and skype worked fine.

I decided to install apt-show-versions thus:

```
$ sudo apt-get install apt-show-versions
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**The following packages were automatically installed and are no longer required:**
  libkrb5-3:i386 libk5crypto3:i386 libstdc++6:i386 liblcms1:i386 libwrap0:i386 libsamplerate0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libqt4-script:i386 libqt4-network:i386 libqt4-dbus:i386 libjack-jackd2-0:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libglib2.0-0:i386
  libmysqlclient18:i386 libexpat1:i386 libqt4-xmlpatterns:i386 libavahi-common-data:i386 libjson0:i386 libxcb1:i386 libp11-kit0:i386 libxau6:i386
  libcups2:i386 libqtcore4:i386 libkrb5support0:i386 libice6:i386 libspeexdsp1:i386 libxdmcp6:i386 libgcrypt11:i386 libxml2:i386 libkeyutils1:i386
  libqt4-sql:i386 libasound2:i386 libflac8:i386 libxrender1:i386 liborc-0.4-0:i386 libvorbisenc2:i386 libqt4-xml:i386 libasyncns0:i386 libxss1:i386
  libtiff4:i386 libgstreamer-plugins-base0.10-0:i386 libavahi-client3:i386 libx11-6:i386 libsm6:i386 libpulse0:i386 libqt4-sql-mysql:i386
  libgssapi-krb5-2:i386 libxi6:i386 libvorbis0a:i386 libgstreamer0.10-0:i386 libaudio2:i386 libxt6:i386 libxv1:i386 libxext6:i386
  libavahi-common3:i386 mysql-common libsndfile1:i386 libsqlite3-0:i386 libmng1:i386 libasound2-plugins:i386 libgpg-error0:i386 libogg0:i386
**Use 'apt-get autoremove' to remove them.**
The following extra packages will be installed:
  libapt-pkg-perl
The following NEW packages will be installed
  apt-show-versions libapt-pkg-perl
0 upgraded, 2 newly installed, 0 to remove and 120 not upgraded.
Need to get 116 kB of archives.
After this operation, 444 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://es.archive.ubuntu.com/ubuntu/ precise/main libapt-pkg-perl amd64 0.1.25build2 [82.9 kB]
Get:2 http://es.archive.ubuntu.com/ubuntu/ precise/universe apt-show-versions all 0.17 [32.9 kB]
Fetched 116 kB in 0s (135 kB/s)              
Selecting previously unselected package libapt-pkg-perl.
(Reading database ... 164425 files and directories currently installed.)
Unpacking libapt-pkg-perl (from .../libapt-pkg-perl_0.1.25build2_amd64.deb) ...
Selecting previously unselected package apt-show-versions.
Unpacking apt-show-versions (from .../apt-show-versions_0.17_all.deb) ...
Processing triggers for man-db ...
Setting up libapt-pkg-perl (0.1.25build2) ...
Setting up apt-show-versions (0.17) ...
** initializing cache. This may take a while **
```

So I took the advice:

```
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libaudio2:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libcups2:i386 libexpat1:i386 libflac8:i386 libfreetype6:i386 libgcrypt11:i386 libglib2.0-0:i386 libgnutls26:i386 libgpg-error0:i386
  libgssapi-krb5-2:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libice6:i386 libjack-jackd2-0:i386 libjpeg-turbo8:i386
  libjpeg8:i386 libjson0:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386 libmng1:i386
  libmysqlclient18:i386 libogg0:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpulse0:i386 libqt4-dbus:i386 libqt4-network:i386 libqt4-script:i386
  libqt4-sql:i386 libqt4-sql-mysql:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libsamplerate0:i386 libsm6:i386 libsndfile1:i386
  libspeexdsp1:i386 libsqlite3-0:i386 libstdc++6:i386 libtasn1-3:i386 libtiff4:i386 libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 libx11-6:i386
  libxau6:i386 libxcb1:i386 libxdmcp6:i386 libxext6:i386 libxi6:i386 libxml2:i386 libxrender1:i386 libxss1:i386 libxt6:i386 libxv1:i386 mysql-common
0 upgraded, 0 newly installed, 65 to remove and 120 not upgraded.
After this operation, 54.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 164467 files and directories currently installed.)
Removing libasound2-plugins:i386 ...
Removing libasound2:i386 ...
Removing libpulse0:i386 ...
Removing libasyncns0:i386 ...
Removing libaudio2:i386 ...
Removing libcups2:i386 ...
Removing libavahi-client3:i386 ...
Removing libavahi-common3:i386 ...
Removing libavahi-common-data:i386 ...
Removing libexpat1:i386 ...
Removing libsndfile1:i386 ...
Removing libflac8:i386 ...
Removing libfreetype6:i386 ...
Removing libgnutls26:i386 ...
Removing libgcrypt11:i386 ...
Removing libqt4-xmlpatterns:i386 ...
Removing libqt4-script:i386 ...
Removing libqt4-network:i386 ...
Removing libqt4-dbus:i386 ...
Removing libqt4-xml:i386 ...
Removing libqt4-sql-mysql:i386 ...
Removing libqt4-sql:i386 ...
Removing libqtcore4:i386 ...
Removing libgstreamer-plugins-base0.10-0:i386 ...
Removing libgstreamer0.10-0:i386 ...
Removing libglib2.0-0:i386 ...
Removing libgpg-error0:i386 ...
Removing libgssapi-krb5-2:i386 ...
Removing libxt6:i386 ...
Removing libsm6:i386 ...
Removing libice6:i386 ...
Removing libjack-jackd2-0:i386 ...
Removing libtiff4:i386 ...
Removing libmng1:i386 ...
Removing libjpeg8:i386 ...
Removing libjpeg-turbo8:i386 ...
Removing libjson0:i386 ...
Removing libkrb5-3:i386 ...
Removing libk5crypto3:i386 ...
Removing libkeyutils1:i386 ...
Removing libkrb5support0:i386 ...
Removing liblcms1:i386 ...
Removing libmysqlclient18:i386 ...
Removing libvorbisenc2:i386 ...
Removing libvorbis0a:i386 ...
Removing libogg0:i386 ...
Removing liborc-0.4-0:i386 ...
Removing libp11-kit0:i386 ...
Removing libsamplerate0:i386 ...
Removing libspeexdsp1:i386 ...
Removing libsqlite3-0:i386 ...
Removing libstdc++6:i386 ...
Removing libtasn1-3:i386 ...
Removing libwrap0:i386 ...
Removing libxi6:i386 ...
Removing libxv1:i386 ...
Removing libxrender1:i386 ...
Removing libxss1:i386 ...
Removing libxext6:i386 ...
Removing libx11-6:i386 ...
Removing libxcb1:i386 ...
Removing libxau6:i386 ...
Removing libxdmcp6:i386 ...
Removing libxml2:i386 ...
Removing mysql-common ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
```



However this broke skype and it vanished:

```
$ dpkg -l skype
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
un  skype                           <none>                          (no description available)

```

Trying to reinstall it did not work:

```
$ sudo dpkg -i skype-ubuntu-precise_4.2.0.13-1_i386.deb 
[sudo] password for : 
Selecting previously unselected package skype:i386.
(Reading database ... 164214 files and directories currently installed.)
Unpacking skype:i386 (from skype-ubuntu-precise_4.2.0.13-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:i386:
 skype:i386 depends on libasound2 (>= 1.0.23); however:
  Package libasound2:i386 is not installed.
 skype:i386 depends on libqt4-dbus (>= 4:4.5.3); however:
  Package libqt4-dbus:i386 is not installed.
 skype:i386 depends on libqt4-network (>= 4:4.8.0); however:
  Package libqt4-network:i386 is not installed.
 skype:i386 depends on libqt4-xml (>= 4:4.5.3); however:
  Package libqt4-xml:i386 is not installed.
 skype:i386 depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Package libqtcore4:i386 is not installed.
 skype:i386 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:i386 is not installed.
 skype:i386 depends on libqtwebkit4 (>= 2.2~2011week36); however:
  Package libqtwebkit4:i386 is not installed.
 skype:i386 depends on libstdc++6 (>= 4.6); however:
  Package libstdc++6:i386 is not installed.
 skype:i386 depends on libx11-6; however:
  Package libx11-6:i386 is not installed.
 skype:i386 depends on libxext6; however:
  Package libxext6:i386 is not installed.
 skype:i386 depends on libxss1; however:
  Package libxss1:i386 is not installed.
 skype:i386 depends on libxv1; however:
  Package libxv1:i386 is not installed.
 skype:i386 depends on libasound2-plugins; however:
  Package libasound2-plugins:i386 is not installed.
dpkg: error processing skype:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 skype:i386
```


Trying to re-install the libraries did not work:

```
$ sudo apt-get install libkrb5-3:i386 libk5crypto3:i386 libstdc++6:i386 liblcms1:i386 libwrap0:i386 libsamplerate0:i386 libjpeg-turbo8:i386 libjpeg8:i386  libqt4-script:i386 libqt4-network:i386 libqt4-dbus:i386 libjack-jackd2-0:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libglib2.0-0:i386  libmysqlclient18:i386 libexpat1:i386 libqt4-xmlpatterns:i386 libavahi-common-data:i386 libjson0:i386 libxcb1:i386 libp11-kit0:i386 libxau6:i386  libcups2:i386 libqtcore4:i386 libkrb5support0:i386 libice6:i386 libspeexdsp1:i386 libxdmcp6:i386 libgcrypt11:i386 libxml2:i386 libkeyutils1:i386  libqt4-sql:i386 libasound2:i386 libflac8:i386 libxrender1:i386 liborc-0.4-0:i386 libvorbisenc2:i386 libqt4-xml:i386 libasyncns0:i386 libxss1:i386  libtiff4:i386 libgstreamer-plugins-base0.10-0:i386 libavahi-client3:i386 libx11-6:i386 libsm6:i386 libpulse0:i386 libqt4-sql-mysql:i386  libgssapi-krb5-2:i386 libxi6:i386 libvorbis0a:i386 libgstreamer0.10-0:i386 libaudio2:i386 libxt6:i386 libxv1:i386 libxext6:i386  libavahi-common3:i386 mysql-common libsndfile1:i386 libsqlite3-0:i386 libmng1:i386 libasound2-plugins:i386 libgpg-error0:i386 libogg0:i386
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libasound2 : Breaks: libasound2:i386 (!= 1.0.25-1ubuntu10.2) but 1.0.25-1ubuntu10 is to be installed
 libasound2:i386 : Breaks: libasound2 (!= 1.0.25-1ubuntu10)
 libavahi-client3 : Breaks: libavahi-client3:i386 (!= 0.6.30-5ubuntu2.1) but 0.6.30-5ubuntu2 is to be installed
 libavahi-client3:i386 : Breaks: libavahi-client3 (!= 0.6.30-5ubuntu2) but 0.6.30-5ubuntu2.1 is to be installed
 libavahi-common-data : Breaks: libavahi-common-data:i386 (!= 0.6.30-5ubuntu2.1) but 0.6.30-5ubuntu2 is to be installed
 libavahi-common-data:i386 : Breaks: libavahi-common-data (!= 0.6.30-5ubuntu2) but 0.6.30-5ubuntu2.1 is to be installed
 libavahi-common3 : Breaks: libavahi-common3:i386 (!= 0.6.30-5ubuntu2.1) but 0.6.30-5ubuntu2 is to be installed
 libavahi-common3:i386 : Breaks: libavahi-common3 (!= 0.6.30-5ubuntu2) but 0.6.30-5ubuntu2.1 is to be installed
 libcups2 : Breaks: libcups2:i386 (!= 1.5.3-0ubuntu8) but 1.5.3-0ubuntu5.1 is to be installed
 libcups2:i386 : Breaks: libcups2 (!= 1.5.3-0ubuntu5.1) but 1.5.3-0ubuntu8 is to be installed
 libglib2.0-0 : Breaks: libglib2.0-0:i386 (!= 2.32.4-0ubuntu1) but 2.32.1-0ubuntu2 is to be installed
 libglib2.0-0:i386 : Depends: libelf1:i386 (>= 0.131) but it is not going to be installed
                     Breaks: libglib2.0-0 (!= 2.32.1-0ubuntu2) but 2.32.4-0ubuntu1 is to be installed
 libgnutls26 : Breaks: libgnutls26:i386 (!= 2.12.14-5ubuntu3.5) but 2.12.14-5ubuntu3.4 is to be installed
 libgnutls26:i386 : Breaks: libgnutls26 (!= 2.12.14-5ubuntu3.4) but 2.12.14-5ubuntu3.5 is to be installed
 libgstreamer-plugins-base0.10-0 : Breaks: libgstreamer-plugins-base0.10-0:i386 (!= 0.10.36-1ubuntu0.1) but 0.10.36-1 is to be installed
 libgstreamer-plugins-base0.10-0:i386 : Breaks: libgstreamer-plugins-base0.10-0 (!= 0.10.36-1) but 0.10.36-1ubuntu0.1 is to be installed
 libjack-jackd2-0 : Breaks: libjack-jackd2-0:i386 (!= 1.9.8~dfsg.1-1ubuntu2) but 1.9.8~dfsg.1-1ubuntu1 is to be installed
 libjack-jackd2-0:i386 : Breaks: libjack-jackd2-0 (!= 1.9.8~dfsg.1-1ubuntu1) but 1.9.8~dfsg.1-1ubuntu2 is to be installed
 libpulse0 : Breaks: libpulse0:i386 (!= 1:1.1-0ubuntu15.4) but 1:1.1-0ubuntu15 is to be installed
 libpulse0:i386 : Breaks: libpulse0 (!= 1:1.1-0ubuntu15) but 1:1.1-0ubuntu15.4 is to be installed
 libqt4-dbus : Breaks: libqt4-dbus:i386 (!= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu4.5 is to be installed
 libqt4-dbus:i386 : Recommends: qdbus:i386 (= 4:4.8.1-0ubuntu4.5)
                    Breaks: libqt4-dbus (!= 4:4.8.1-0ubuntu4.5) but 4:4.8.1-0ubuntu4.6 is to be installed
 libqt4-network : Breaks: libqt4-network:i386 (!= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu4.5 is to be installed
 libqt4-network:i386 : Breaks: libqt4-network (!= 4:4.8.1-0ubuntu4.5) but 4:4.8.1-0ubuntu4.6 is to be installed
 libqt4-script : Breaks: libqt4-script:i386 (!= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu4.5 is to be installed
 libqt4-script:i386 : Breaks: libqt4-script (!= 4:4.8.1-0ubuntu4.5) but 4:4.8.1-0ubuntu4.6 is to be installed
 libqt4-sql : Breaks: libqt4-sql:i386 (!= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu4.5 is to be installed
 libqt4-sql:i386 : Breaks: libqt4-sql (!= 4:4.8.1-0ubuntu4.5) but 4:4.8.1-0ubuntu4.6 is to be installed
 libqt4-xml : Breaks: libqt4-xml:i386 (!= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu4.5 is to be installed
 libqt4-xml:i386 : Breaks: libqt4-xml (!= 4:4.8.1-0ubuntu4.5) but 4:4.8.1-0ubuntu4.6 is to be installed
 libqt4-xmlpatterns : Breaks: libqt4-xmlpatterns:i386 (!= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu4.5 is to be installed
 libqt4-xmlpatterns:i386 : Breaks: libqt4-xmlpatterns (!= 4:4.8.1-0ubuntu4.5) but 4:4.8.1-0ubuntu4.6 is to be installed
 libqtcore4 : Breaks: libqtcore4:i386 (!= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu4.5 is to be installed
 libqtcore4:i386 : Breaks: libqtcore4 (!= 4:4.8.1-0ubuntu4.5) but 4:4.8.1-0ubuntu4.6 is to be installed
 libsqlite3-0 : Breaks: libsqlite3-0:i386 (!= 3.7.9-2ubuntu1.1) but 3.7.9-2ubuntu1 is to be installed
 libsqlite3-0:i386 : Breaks: libsqlite3-0 (!= 3.7.9-2ubuntu1) but 3.7.9-2ubuntu1.1 is to be installed
 libx11-6 : Breaks: libx11-6:i386 (!= 2:1.4.99.1-0ubuntu2.2) but 2:1.4.99.1-0ubuntu2.1 is to be installed
 libx11-6:i386 : Breaks: libx11-6 (!= 2:1.4.99.1-0ubuntu2.1) but 2:1.4.99.1-0ubuntu2.2 is to be installed
 libxi6 : Breaks: libxi6:i386 (!= 2:1.7.1.901-1ubuntu1~precise1) but 2:1.6.0-0ubuntu2.1 is to be installed
 libxi6:i386 : Breaks: libxi6 (!= 2:1.6.0-0ubuntu2.1) but 2:1.7.1.901-1ubuntu1~precise1 is to be installed
 skype:i386 : Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
              Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
              Recommends: sni-qt:i386 but it is not going to be installed
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free amd64 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry http://deb.opera.com/opera/ stable/non-free i386 Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. **Try 'apt-get -f install' with no packages** (or specify a solution).

```

At this point I have no idea how to proceed! Any advice?

---

### Post by deadflowr on 2014-02-02
Did you try running an upgrade?
You have/had 120 packages not upgraded.
```
sudo apt-get dist-upgrade
```
should do the trick for that.
when that's done, you can see about fixing the 32-bit packages needed to run skype.

---

### Post by desconocido on 2014-02-03
> **deadflowr said:**
> apt-get dist-upgrade

Well, I may not be understanding what that command does, but I do want to remain with Ubuntu 12.04 LTS rather than upgrade to a new version.

---

### Post by Bucky Ball on 2014-02-03
You will remain with 12.04. It will only upgrade the packages, software, etc., NOT the entire release. I advise you start at the beginning as you should update before the upgrade. Try these three.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then try installing skype. Report any errors, either with the updates or skype install.

---

### Post by deadflowr on 2014-02-03
^^^^
Exactly.
Me for forgets to explain it doesn't change versions.
It only upgrades the packages for the existing version.

If you wanted to upgrade to a newer release then you would run
```
do-release-upgrade
```
or something to that effect.

---

### Post by desconocido on 2014-02-03
> **Bucky Ball said:**
> Try these three.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then try installing skype. Report any errors, either with the updates or skype install.

Here goes:

```
$ sudo apt-get update
[sudo] password for : 
Hit http://ppa.launchpad.net precise Release.gpg
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                                                              
Hit http://ppa.launchpad.net precise Release                                                                           
Hit http://es.archive.ubuntu.com precise Release.gpg                                                                   
Hit http://security.ubuntu.com precise-security Release.gpg                                                            
Hit http://extras.ubuntu.com precise Release                                                                           
Hit http://dl.google.com stable Release.gpg                                                                            
Hit http://deb.opera.com stable Release.gpg                                                                            
Hit http://security.ubuntu.com precise-security Release                                     
Hit http://dl.google.com stable Release                                                                           
Hit http://ppa.launchpad.net precise/main Sources                                                                      
Hit http://extras.ubuntu.com precise/main Sources                                                                      
Hit http://deb.opera.com stable Release                                                                          
Hit http://security.ubuntu.com precise-security/main Sources                                                           
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                               
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                             
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                               
Hit http://extras.ubuntu.com precise/main i386 Packages                                                          
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                       
Hit http://security.ubuntu.com precise-security/restricted Sources                                               
Hit http://security.ubuntu.com precise-security/universe Sources                                                 
Hit http://security.ubuntu.com precise-security/multiverse Sources                                               
Hit http://security.ubuntu.com precise-security/main amd64 Packages                                                    
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                                              
Hit http://dl.google.com stable/main amd64 Packages                                                                    
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                                                
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                                        
Hit http://security.ubuntu.com precise-security/main i386 Packages                                               
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                                         
Hit http://security.ubuntu.com precise-security/universe i386 Packages                                                 
Hit http://deb.opera.com stable/non-free amd64 Packages                                                                
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                                               
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                            
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                      
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                      
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                        
Hit http://dl.google.com stable/main i386 Packages                                                               
Ign http://dl.google.com stable/main TranslationIndex                                                                  
Hit http://security.ubuntu.com precise-security/main Translation-en                                                    
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                        
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                              
Hit http://deb.opera.com stable/non-free i386 Packages                                                                 
Ign http://deb.opera.com stable/non-free TranslationIndex                                                        
Hit http://security.ubuntu.com precise-security/universe Translation-en                                          
Ign http://ppa.launchpad.net precise/main Translation-en_GB                                                      
Ign http://extras.ubuntu.com precise/main Translation-en_GB                                                      
Ign http://ppa.launchpad.net precise/main Translation-en                                   
Ign http://extras.ubuntu.com precise/main Translation-en                                   
Ign http://dl.google.com stable/main Translation-en_GB                                     
Ign http://dl.google.com stable/main Translation-en                  
Hit http://es.archive.ubuntu.com precise Release
Ign http://deb.opera.com stable/non-free Translation-en_GB
Ign http://deb.opera.com stable/non-free Translation-en
Hit http://es.archive.ubuntu.com precise/main Sources
Hit http://es.archive.ubuntu.com precise/restricted Sources                                                            
Hit http://es.archive.ubuntu.com precise/universe Sources                                                              
Hit http://es.archive.ubuntu.com precise/multiverse Sources                                                            
Hit http://es.archive.ubuntu.com precise/main amd64 Packages                                                           
Hit http://es.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://es.archive.ubuntu.com precise/universe amd64 Packages
Hit http://es.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://es.archive.ubuntu.com precise/main i386 Packages
Hit http://es.archive.ubuntu.com precise/restricted i386 Packages
Hit http://es.archive.ubuntu.com precise/universe i386 Packages
Hit http://es.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://es.archive.ubuntu.com precise/main TranslationIndex
Hit http://es.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://es.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://es.archive.ubuntu.com precise/universe TranslationIndex
Hit http://es.archive.ubuntu.com precise/main Translation-en_GB
Hit http://es.archive.ubuntu.com precise/main Translation-en
Hit http://es.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://es.archive.ubuntu.com precise/multiverse Translation-en
Hit http://es.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://es.archive.ubuntu.com precise/restricted Translation-en
Hit http://es.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://es.archive.ubuntu.com precise/universe Translation-en
Fetched 72 B in 1min 7s (1 B/s)
Reading package lists... Done

```

```
$ sudo apt-get upgrade
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 skype:i386 : Depends: libasound2:i386 (>= 1.0.23) but it is not installed
              Depends: libqt4-dbus:i386 (>= 4:4.5.3) but it is not installed
              Depends: libqt4-network:i386 (>= 4:4.8.0) but it is not installed
              Depends: libqt4-xml:i386 (>= 4:4.5.3) but it is not installed
              Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not installed
              Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not installed
              Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not installed
              Depends: libstdc++6:i386 (>= 4.6) but it is not installed
              Depends: libx11-6:i386 but it is not installed
              Depends: libxext6:i386 but it is not installed
              Depends: libxss1:i386 but it is not installed
              Depends: libxv1:i386 but it is not installed
              Depends: libasound2-plugins:i386 but it is not installed
              Recommends: sni-qt:i386 but it is not installed
E: Unmet dependencies. Try using -f.

```

```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 skype:i386 : Depends: libasound2:i386 (>= 1.0.23) but it is not installed
              Depends: libqt4-dbus:i386 (>= 4:4.5.3) but it is not installed
              Depends: libqt4-network:i386 (>= 4:4.8.0) but it is not installed
              Depends: libqt4-xml:i386 (>= 4:4.5.3) but it is not installed
              Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not installed
              Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not installed
              Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not installed
              Depends: libstdc++6:i386 (>= 4.6) but it is not installed
              Depends: libx11-6:i386 but it is not installed
              Depends: libxext6:i386 but it is not installed
              Depends: libxss1:i386 but it is not installed
              Depends: libxv1:i386 but it is not installed
              Depends: libasound2-plugins:i386 but it is not installed
              Recommends: sni-qt:i386 but it is not installed
E: Unmet dependencies. Try using -f.

```

```
$ sudo dpkg -i skype-ubuntu-precise_4.2.0.13-1_i386.deb 
(Reading database ... 164362 files and directories currently installed.)
Preparing to replace skype:i386 4.2.0.13-1 (using skype-ubuntu-precise_4.2.0.13-1_i386.deb) ...
Unpacking replacement skype:i386 ...
dpkg: dependency problems prevent configuration of skype:i386:
 skype:i386 depends on libasound2 (>= 1.0.23); however:
  Package libasound2:i386 is not installed.
 skype:i386 depends on libqt4-dbus (>= 4:4.5.3); however:
  Package libqt4-dbus:i386 is not installed.
 skype:i386 depends on libqt4-network (>= 4:4.8.0); however:
  Package libqt4-network:i386 is not installed.
 skype:i386 depends on libqt4-xml (>= 4:4.5.3); however:
  Package libqt4-xml:i386 is not installed.
 skype:i386 depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Package libqtcore4:i386 is not installed.
 skype:i386 depends on libqtgui4 (>= 4:4.8.0); however:
  Package libqtgui4:i386 is not installed.
 skype:i386 depends on libqtwebkit4 (>= 2.2~2011week36); however:
  Package libqtwebkit4:i386 is not installed.
 skype:i386 depends on libstdc++6 (>= 4.6); however:
  Package libstdc++6:i386 is not installed.
 skype:i386 depends on libx11-6; however:
  Package libx11-6:i386 is not installed.
 skype:i386 depends on libxext6; however:
  Package libxext6:i386 is not installed.
 skype:i386 depends on libxss1; however:
  Package libxss1:i386 is not installed.
 skype:i386 depends on libxv1; however:
  Package libxv1:i386 is not installed.
 skype:i386 depends on libasound2-plugins; however:
  Package libasound2-plugins:i386 is not installed.
dpkg: error processing skype:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 skype:i386

```

---

### Post by deadflowr on 2014-02-03
Run the
```
sudo apt-get -f install
```
command that was reported to you.
That should fix the broken packages.
(Well, it's suppose to anyway)

Added: Run the command as is, don't add anything to it.
(I state this because sometimes poeple think you run it like a normal install command so they run it with the package like
```
sudo apt-get -f install libc6
```
don't do that.

---

### Post by monkeybrain20122 on 2014-02-04
Skype is in the Partners repo. Instead of trying to reinstall those i386 libs I would just try to install Skype with synaptic. In Precise you should install ia32 for 32 bit program in 64 bit platform.

To find out what is going on you may try to install one of the "not going to be installed" packages in the terminal and see the output errors. Usually it will give you some clues about what the conflict is. I think your sources.list is probably kind of messed up.

---

### Post by desconocido on 2014-02-05
> **deadflowr said:**
> Run the
```
sudo apt-get -f install
```
command that was reported to you.
That should fix the broken packages.
(Well, it's suppose to anyway).

Well, I tried that earlier but chickened out at the stage where it asks > Do you want to continue [Y/n]? I got nervous because:
```
$ sudo apt-get -f install
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-notify-0.7 libopencc1 syslinux gedit-common gir1.2-rb-3.0 gir1.2-gstreamer-0.10 libgtksourceview-3.0-0
  libdmapsharing-3.0-2 rhythmbox-data intel-gpu-tools libilmbase6 stellarium-data libdiscid0 gir1.2-indicate-0.7
  libgpod-common ibus-gtk3 gir1.2-gnomekeyring-1.0 liblouis-data syslinux-legacy libcrypt-passwdmd5-perl ibus-gtk
  ubuntu-extras-keyring syslinux-common librhythmbox-core5 libgpod4 gir1.2-totem-1.0 gir1.2-appindicator3-0.1
  libbabl-0.0-0 libgegl-0.0-0 libindicator7 command-not-found-data gir1.2-totem-plparser-1.0 liblouis2
  gir1.2-gtksource-3.0 libgtksourceview-3.0-common libopenexr6 gir1.2-gst-plugins-base-0.10 libgtkspell-3-0
  gir1.2-atspi-2.0 gimp-help-common ibus-pinyin-db-android im-switch gir1.2-gudev-1.0 gimp-help-en libgimp2.0
  libappindicator1 gir1.2-wnck-3.0 python-gdbm app-install-data thunderbird-globalmenu media-player-info
  gir1.2-launchpad-integration-3.0 protobuf-compiler libmusicbrainz3-6 gimp-data libprotoc7 librsync1
  activity-log-manager-common libstdc++6:i386 libmusicbrainz5-0 librhythmbox-core6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  accountsservice gir1.2-totem-1.0 libaccountsservice0 libclutter-gst-1.0-0 libclutter-gtk-1.0-0
  libclutter-imcontext-0.1-0 libcluttergesture-0.0.2-0 libhpmud0 libmusicbrainz5-0 libmx-1.0-2 libnss3 libnss3-1d
  libpython2.7 librhythmbox-core6 libstdc++6:i386 libtotem0 printer-driver-hpijs python2.7 python2.7-minimal
  thunderbird thunderbird-globalmenu thunderbird-gnome-support totem totem-common totem-mozilla
Suggested packages:
  hpijs-ppds hplip-doc python2.7-doc binfmt-support ttf-lyx
The following packages will be REMOVED
  activity-log-manager-control-center alacarte appmenu-qt apport apport-gtk apt-xapian-index aptdaemon apturl
  apturl-common bluez bluez-alsa bluez-gstreamer checkbox checkbox-qt command-not-found deja-dup duplicity
  epson-inkjet-printer-nx420 fglrx-amdcccle-experimental-13 fglrx-experimental-13 firefox firefox-gnome-support gdb
  gdebi gdebi-core gedit gimp gnome-applets gnome-applets-data gnome-bluetooth gnome-control-center gnome-orca
  gnome-shell gnome-sudoku gnome-tweak-tool gnome-user-share google-earth-stable:i386 gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter hplip ibus ibus-pinyin ibus-table
  indicator-datetime indicator-power jockey-common jockey-gtk landscape-client-ui-install language-selector-common
  language-selector-gnome launchpad-integration libdbusmenu-qt2 libdconf-qt0 libgwibber-gtk2 libgwibber2 libpurple-bin
  libqt4-dbus libqt4-declarative libqt4-designer libqt4-gui libqt4-network libqt4-opengl libqt4-script libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1 libqtgui4
  libreoffice-emailmerge libsyncdaemon-1.0-1 libunity-2d-private0 lsb lsb-core lsb-cxx lsb-desktop lsb-graphics
  lsb-printing lsb-release nautilus-share nvidia-common onboard oneconf printer-driver-postscript-hp
  python-appindicator python-apport python-apt python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-brlapi python-cairo python-chardet python-configglue python-crypto python-cups python-dateutil python-dbus
  python-debian python-debtagshw python-defer python-dirspec python-egenix-mxdatetime python-egenix-mxtools python-gi
  python-gi-cairo python-gmenu python-gnupginterface python-gobject python-gobject-2 python-gst0.10 python-gtk2
  python-httplib2 python-ibus python-imaging python-keyring python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-libproxy python-libxml2 python-louis python-mako python-markupsafe python-notify python-oauth
  python-openssl python-packagekit python-pam python-pexpect python-piston-mini-client python-problem-report
  python-protobuf python-pyatspi2 python-pycurl python-pyinotify python-renderpm python-reportlab
  python-reportlab-accel python-serial python-simplejson python-software-properties python-speechd python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno python-virtkey python-wadllib
  python-xapian python-xdg python-xkit python-zeitgeist python-zope.interface qdbus qt-at-spi rhythmbox
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist
  rhythmbox-plugins sessioninstaller skype:i386 sni-qt software-center software-center-aptdaemon-plugins
  software-properties-common software-properties-gtk stellarium totem-plugins ubuntu-minimal ubuntu-sso-client
  ubuntu-sso-client-gtk ubuntu-standard ubuntu-system-service ubuntuone-client ubuntuone-client-gnome
  ubuntuone-control-panel ubuntuone-couch ubuntuone-installer ufw unattended-upgrades unity-2d-panel update-manager
  update-manager-core update-notifier update-notifier-common usb-creator-common usb-creator-gtk vlc xdiagnose
  xul-ext-ubufox zeitgeist zeitgeist-core zeitgeist-datahub
The following NEW packages will be installed
  libclutter-gst-1.0-0 libclutter-gtk-1.0-0 libclutter-imcontext-0.1-0 libcluttergesture-0.0.2-0 libmusicbrainz5-0
  libmx-1.0-2 librhythmbox-core6 libstdc++6:i386
The following packages will be upgraded:
  accountsservice gir1.2-totem-1.0 libaccountsservice0 libhpmud0 libnss3 libnss3-1d libpython2.7 libtotem0
  printer-driver-hpijs python2.7 python2.7-minimal thunderbird thunderbird-globalmenu thunderbird-gnome-support totem
  totem-common totem-mozilla
17 upgraded, 8 newly installed, 208 to remove and 76 not upgraded.
1 not fully installed or removed.
Need to get 43.1 MB/43.4 MB of archives.
After this operation, 735 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

I couldn't believe that my missing packages problem could be solved by removing another 208, some of which I am sure I need!?

---

### Post by desconocido on 2014-02-05
> **monkeybrain20122 said:**
> 
To find out what is going on you may try to install one of the "not going to be installed" packages in the terminal and see the output errors. Usually it will give you some clues about what the conflict is.

```
$ sudo apt-get install libqtcore4:i386
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libqtcore4 : Breaks: libqtcore4:i386 (!= 4:4.8.1-0ubuntu4.6) but 4:4.8.1-0ubuntu4.5 is to be installed
 libqtcore4:i386 : Depends: libglib2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                   Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
                   Breaks: libqtcore4 (!= 4:4.8.1-0ubuntu4.5) but 4:4.8.1-0ubuntu4.6 is to be installed

```

---

### Post by desconocido on 2014-02-05
> **monkeybrain20122 said:**
> Skype is in the Partners repo. Instead of trying to reinstall those i386 libs I would just try to install Skype with synaptic.

I don't seem to be able to install synaptic either:

```
$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

And if I try Ubuntu Software Centre, I get the following two dialogue boxes:

---

### Post by desconocido on 2014-02-05
> **monkeybrain20122 said:**
> I think your sources.list is probably kind of messed up.

Here is /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://es.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://es.archive.ubuntu.com/ubuntu/ precise universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ precise multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

## Others added by BK
# deb http://deb.opera.com/opera/ stable non-free
```

---

### Post by desconocido on 2014-02-10
Well, I guess there was no way forward from there.

I have split my disk in two, moved /home to the new partition and re-installed Ubuntu 12.04.3 onto the original partition. It seems to be working again OK.

It looks like the advice from apt-get "The following packages were automatically installed and are no longer required" is broken. See also
[http://ubuntuforums.org/archive/index.php/t-1203065.html](http://ubuntuforums.org/archive/index.php/t-1203065.html)
[http://ubuntuforums.org/archive/index.php/t-1132579.html](http://ubuntuforums.org/archive/index.php/t-1132579.html)

I should be able to get Skype working again, but I'm still going to have problems with third party applications like Google-Earth and Freewrl which seem to have impossible dependency problems.
And I haven't even started on Wine and LAMP yet.

---

### Post by monkeybrain20122 on 2014-02-11
I suspect you may have some ppa's installed. Look into the directory /etc/sources.list.d and list the entries there. These are not in the main sources.list.

---

### Post by Bucky Ball on 2014-02-11
Install Skype from Software Centre or Synaptic. Shouldn't be a problem.

---

### Post by deadflowr on 2014-02-11
> **monkeybrain20122 said:**
> I suspect you may have some ppa's installed. Look into the directory /etc/sources.list.d and list the entries there. These are not in the main sources.list.

Does the skype.deb do that like google-chrome.deb does it, and add a ppa for further updating?

---

### Post by desconocido on 2014-02-11
> **monkeybrain20122 said:**
> I suspect you may have some ppa's installed. Look into the directory /etc/sources.list.d and list the entries there. These are not in the main sources.list.

The directory does not exist, perhaps because I have re-installed Ubuntu.

---

