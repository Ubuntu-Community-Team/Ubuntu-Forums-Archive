---
title: "want to install kaffeine_0.8.8-0.deb"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by ahmed772007 on 2012-10-11
can you help me to solve this problem 
 i want to install kaffeine_0.8.8-0.deb to use sharing tv ... i use  ubuntu 12.04 lts ..... this is my problem look at the picture[http://sphotos-e.ak.fbcdn.net/hphotos-ak-prn1/65350_122966331187269_1123624156_n.jpg](http://sphotos-e.ak.fbcdn.net/hphotos-ak-prn1/65350_122966331187269_1123624156_n.jpg)

and when i instaal the kdelibs-data_3.5.9-0ubuntu1_all this error appear
[http://s7.postimage.org/6r1dx6ym3/snapshot2.jpg](http://s7.postimage.org/6r1dx6ym3/snapshot2.jpg)

 help me please

---

### Post by rburkartjo on 2012-10-11
it is available in the ubuntu software center why not try installing from there worked for me

---

### Post by ahmed772007 on 2012-10-11
thanks for help ...ya i know ...  but i want this version because the last version of it don't work in the sharing
hen i install it from the ubuntu software center the last version is installed but i need this version

---

### Post by ahmed772007 on 2012-10-11
thanks for help ...ya i know ...  but i want this version because the last version of it don't work in the sharing

when i install it from the ubuntu software center the last version is installed but i need this version

---

### Post by NikTh on 2012-10-11
Hi , 

you must know that is not easy to revert back a package version. (at least not in Ubuntu). 
Especially when this package is from KDE and you have NOT KDE. 

You said you have Ubuntu (not Kubuntu). So I assume a lot of dependencies (for KDE) missing. 

When you download a standalone .deb package you must also download and ALL of the dependencies. 

The message is clear. You need the kdelibs4c2a **> =** 4:3.5.9 . You tried to install kdelibs5-data. This is NOT the same package as kdelibs4c2a. 

Here is the package of libs that you want : [http://packages.debian.org/sid/kdelibs4c2a](http://packages.debian.org/sid/kdelibs4c2a)
BUT look ALL the dependencies that ONLY this package requires. If you have them its OK , but if not ? 

What I want to say is that is hard (sometimes not all the times) to revert back or to install a newest package from a standalone .deb 

If this kdenlive is a newer package then maybe you have luck and some guy with a PPA has already packed it for you and you can search for the PPA add it to your sources and Done. 

Sometimes , package managers as apt-get can resolve such situations easy (when the dependencies are reachable) 

So first try ```
sudo apt-get install -f
```and give the results back here. 

Thanks

---

### Post by ahmed772007 on 2012-10-11
very very very thanks to you for this information .....
.now i need any prog to use it ii in my cart  like vdr or kaffeine but must support the ACamd 0.618 or  WinCSC to use the sharing .. my satellite cart is tvii dvbs-2 464 .. are there any prog to this ?

---

### Post by ahmed772007 on 2012-10-11
i do this code      sudo apt-get install -f

and this is the result 

mohamed@mohamed:~$ sudo apt-get install -f
[sudo] password for mohamed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 386 not upgraded.
mohamed@mohamed:~$

---

### Post by ahmed772007 on 2012-10-11
i do this code           sudo apt-get install -f

and this is the result 

mohamed@mohamed:~$ sudo apt-get install -f
[sudo] password for mohamed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 386 not upgraded.
mohamed@mohamed:~$

---

### Post by NikTh on 2012-10-11
Try ```
sudo apt-get update
sudo apt-get dist-upgrade
``` 

Please put the result between the brackets **[noparse]```
Here
```[/noparse]** so the results can be readable. 

Thanks

---

### Post by ahmed772007 on 2012-10-11
Installation this code is Ok and this is the result 

```
mohamed@mohamed:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libxine-dev
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mohamed@mohamed:~$ 

```

---

### Post by NikTh on 2012-10-12
Ok , you system now is full updated(almost)> **ahmed772007 said:**
> ```

0 upgraded, 0 newly installed, 0 to remove **and 1 not upgraded.**
mohamed@mohamed:~$ 

```

Because before wasn't.
> **ahmed772007 said:**
> ```

0 upgraded, 0 newly installed, 0 to remove and **386 not upgraded.**
mohamed@mohamed:~$
```

Now try again to install the .deb package with ```
sudo dpkg -i <nameofthepackage>.deb
``` 

and give the results back here.

Thanks

---

### Post by ahmed772007 on 2012-10-12
**[SIZE=4]this is result for  sudo dpkg -i kdelibs-data.deb[/SIZE]**

```
mohamed@mohamed:~$ sudo dpkg -i kdelibs-data.deb
[sudo] password for mohamed: 
dpkg: error processing kdelibs-data.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kdelibs-data.deb
mohamed@mohamed:~$ 

```

**[SIZE=4]and this si the result when i istall the bakage with Gdbi[/SIZE]**


[IMG]http://s17.postimage.org/bzzmmorof/image.jpg[/IMG]

---

### Post by NikTh on 2012-10-12
You did it wrong , but its OK. 

Where is the package kafeine ? In Downloads ? From the first pictures (firs post) I can see a folder.. "kaffeine full" if is there then you must first connect in this folder and the run the command. And do not try to install the libraries.. try to install the package in your title.

```
cd kaffeine\ full 
sudo dpkg -i *.deb
``` 

This command "dpkg -i *.deb" means that dpkg will attempt to install ALL the .deb packages inside this folder (kaffeine full). IF you have other .deb packages in this folder that **are not relevant** with kaffeine , move them. 

Give the full results here. 

Thanks

---

### Post by ahmed772007 on 2012-10-12
**[SIZE=3]alot of thanks  my dear ... this is the result of code [/SIZE]**


```
mohamed@mohamed:~$ cd kaffeine\ full 
mohamed@mohamed:~/kaffeine full$ sudo dpkg -i *.deb
[sudo] password for mohamed: 
dpkg: warning: downgrading kaffeine from 1.2.2-1ubuntu3.12.04.1 to 0.8.8-0ubuntu1~mtron2.
(Reading database ... 275572 files and directories currently installed.)
Preparing to replace kaffeine 1.2.2-1ubuntu3.12.04.1 (using kaffeine_0.8.8-0.deb) ...
Unpacking replacement kaffeine ...
Selecting previously unselected package kaffeine-gstreamer.
Unpacking kaffeine-gstreamer (from kaffeine-gstreamer_0.8.8-0.deb) ...
Selecting previously unselected package kaffeine-sc-plugin-0.4.2-svn.
Unpacking kaffeine-sc-plugin-0.4.2-svn (from kaffeine-sc-plugin-0.4.2-svn_0.4.2-SVN-1_i386.deb) ...
dpkg: dependency problems prevent configuration of kaffeine:
 kaffeine depends on kdelibs4c2a (>= 4:3.5.9); however:
  Package kdelibs4c2a is not installed.
 kaffeine depends on libcdio-cdda0; however:
  Package libcdio-cdda0 is not installed.
 kaffeine depends on libcdio-paranoia0; however:
  Package libcdio-paranoia0 is not installed.
 kaffeine depends on libxine1-all-plugins; however:
  Package libxine1-all-plugins is not installed.
dpkg: error processing kaffeine (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine-gstreamer:
 kaffeine-gstreamer depends on kdelibs4c2a (>= 4:3.5.9); however:
  Package kdelibs4c2a is not installed.
 kaffeine-gstreamer depends on kaffeine; however:
  Package kaffeine is not configured yet.
dpkg: error processing kaffeine-gstreamer (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine-sc-plugin-0.4.2-svn:
 kaffeine-sc-plugin-0.4.2-svn depends on kaffeine; however:
  Package kaffeine is not configured yet.
dpkg: error processing kaffeine-sc-plugin-0.4.2-svn (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Errors were encountered while processing:
 kaffeine
 kaffeine-gstreamer
 kaffeine-sc-plugin-0.4.2-svn
mohamed@mohamed:~/kaffeine full$ 

```

**[SIZE=3]the prog appear in the [SIZE=3]applications[/SIZE] but not work [/SIZE]**:(

---

### Post by ahmed772007 on 2012-10-12
[B][SIZE=3]if the kaffeine doesn't work .... what about vdr ?

i want anything working to my cart and support the sharing tv.... because i know you tired to me ..... really thanks to you [/SIZE][/B]

---

### Post by NikTh on 2012-10-12
OK , 
try now 
```
sudo apt-get install -f 
sudo dpkg --configure -a
``` 

Thanks

---

### Post by ahmed772007 on 2012-10-12
[B][SIZE=3]this is the result of code

[/SIZE][/B]
```
mohamed@mohamed:~$ sudo apt-get install -f 
[sudo] password for mohamed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnepomukdatamanagement4 libmarblewidget13 libkexiv2-10 boot-sav-nonfree
  libkipi8 linux-headers-3.2.0-30 linux-headers-3.2.0-30-generic-pae
  libktpcommoninternalsprivate0 mencoder plasma-widget-telepathy-contact
  libkdecorations4 libkwinglutils1 libkworkspace4abi1 liblzo2-2
  libkwineffects1abi3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kaffeine
Suggested packages:
  libdvdcss2
The following packages will be upgraded:
  kaffeine
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
Need to get 0 B/460 kB of archives.
After this operation, 4,796 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of kaffeine:
 kaffeine depends on kdelibs4c2a (>= 4:3.5.9); however:
  Package kdelibs4c2a is not installed.
 kaffeine depends on libcdio-cdda0; however:
  Package libcdio-cdda0 is not installed.
 kaffeine depends on libcdio-paranoia0; however:
  Package libcdio-paranoia0 is not installed.
 kaffeine depends on libxine1-all-plugins; however:
  Package libxine1-all-plugins is not installed.
dpkg: error processing kaffeine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine-sc-plugin-0.4.2-svn:
 kaffeine-sc-plugin-0.4.2-svn depends on kaffeine; however:
  Package kaffeine is not configured yet.No apport report written because the error message indicates its a followup error from a previous failure.

dpkg: error processing kaffeine-sc-plugin-0.4.2-svn (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 kaffeine
 kaffeine-sc-plugin-0.4.2-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)
mohamed@mohamed:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of kaffeine:
 kaffeine depends on kdelibs4c2a (>= 4:3.5.9); however:
  Package kdelibs4c2a is not installed.
 kaffeine depends on libcdio-cdda0; however:
  Package libcdio-cdda0 is not installed.
 kaffeine depends on libcdio-paranoia0; however:
  Package libcdio-paranoia0 is not installed.
 kaffeine depends on libxine1-all-plugins; however:
  Package libxine1-all-plugins is not installed.
dpkg: error processing kaffeine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kaffeine-sc-plugin-0.4.2-svn:
 kaffeine-sc-plugin-0.4.2-svn depends on kaffeine; however:
  Package kaffeine is not configured yet.
dpkg: error processing kaffeine-sc-plugin-0.4.2-svn (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kaffeine
 kaffeine-sc-plugin-0.4.2-svn
mohamed@mohamed:~$ 

```

---

### Post by NikTh on 2012-10-13
Try ```
sudo apt-get install kdelibs5 kdelibs5-data libcdio-cdda1 libxine1-all-plugins
sudo dpkg-reconfigure kaffeine
``` 

I don't know the package vdr.

---

