---
title: "Samba won't install"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by Dyzphagia on 2011-09-26
I'm trying to install samba so I can transfer some files to windows and I've tried  ```
sudo apt-get install samba
```  I've tried  ```
sudo apt-get install samba4
```  And the same error I get is  ```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```  I've tried autoremove, removing what I've gotten with synaptic, purging the configuration file from some post I read on google. I cannot figure this out and it's really irritating me. What do I do?

---

### Post by garvinrick4 on 2011-09-26
system-config-samba 
is the GUI application for making samba shares.
windows workgroup and Ubuntu will work out of box.
Need to configure samba shares for windows box to see shares in Ubuntu
```
sudo apt-get install system-config-samba
```Make sure you set up your shares in windows and then in Network open 
windows workgroup and will work. Again works out of box from Ubuntu to windows workgroup (must set your windows box up)

---

### Post by Dyzphagia on 2011-09-26
Well I went and used ```
sudo apt-get system-config-samba
``` there and I'm still getting ```
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```  I am also getting ```
ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it dpkg: error processing samba4 (--configure):  subprocess installed post-installation script returned error exit status 1 No apport report written because MaxReports is reached already 
```  The full reading in the terminal is ```
ryan@ryan-GT5220:~$ sudo apt-get install system-config-samba [sudo] password for ryan:  Reading package lists... Done Building dependency tree        Reading state information... Done The following packages were automatically installed and are no longer required:   libkldap4 libsolidcontrol4abi2 libqca2 libqimageblitz4 libkpimtextedit4   libprison0 libkscreensaver5 libkcalutils4 libmicroblog4 freespacenotifier   oxygen-icon-theme libkephal4abi1 kde-workspace-kgreet-plugins   mysql-client-core-5.1 libkidletime4 libboost-program-options1.46.1 libgps19   shared-desktop-ontologies iw akonadi-backend-mysql   libplasma-geolocation-interface4 libntrack-qt4-1 libcln6 kde-runtime-data   libqrencode3 libkmbox4 libprocessui4a mysql-server-core-5.1 libkcalcore4   libkdnssd4 libksgrd4 libmailtransport4 libqapt1 libakonadi-kde4   libqalculate5 libkabc4 libkworkspace4 libkresources4 libkdecorations4   libkpimutils4 libplasmagenericshell4 libkpimidentities4 icoutils   libthreadweaver4 kde-wallpapers-default libkmediaplayer4 libkcal4 libntrack0   libknewstuff3-4 libqapt-runtime libkimap4 libknotifyconfig4 libplasma3   ksysguardd libkmime4 libweather-ion6 libakonadi-contact4 libakonadi-kabc4   libkholidays4 libplasmaclock4abi2 akonadi-server libksignalplotter4   plasma-widget-folderview libkunitconversion4 libtaskmanager4abi2   plasma-scriptengine-javascript libssh-4 libprocesscore4abi1   libakonadiprotocolinternals1 kde-baseapps-data libakonadi-kcal4   libsolidcontrolifaces4abi2 libsyndication4 libakonadi-kmime4 libkdesu5   kde-workspace-data kdepimlibs-kio-plugins ntrack-module-libnl-0   libkwineffects1abi2 oxygen-cursor-theme libdmtx0a Use 'apt-get autoremove' to remove them. The following extra packages will be installed:   libuser1 python-libuser samba Suggested packages:   openbsd-inetd inet-superserver smbldap-tools The following NEW packages will be installed:   libuser1 python-libuser samba system-config-samba 0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded. 1 not fully installed or removed. Need to get 701 kB/8,700 kB of archives. After this operation, 29.5 MB of additional disk space will be used. Do you want to continue [Y/n]? y Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libuser1 i386 1:0.56.9.dfsg.1-1.2ubuntu1 [75.7 kB] Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe python-libuser i386 1:0.56.9.dfsg.1-1.2ubuntu1 [43.5 kB] Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe system-config-samba all 1.2.63-0ubuntu4 [582 kB] Fetched 701 kB in 1s (397 kB/s)               Preconfiguring packages ... Selecting previously deselected package libuser1. (Reading database ... 284754 files and directories currently installed.) Unpacking libuser1 (from .../libuser1_1%3a0.56.9.dfsg.1-1.2ubuntu1_i386.deb) ... Selecting previously deselected package python-libuser. Unpacking python-libuser (from .../python-libuser_1%3a0.56.9.dfsg.1-1.2ubuntu1_i386.deb) ... Selecting previously deselected package samba. Unpacking samba (from .../samba_2%3a3.5.11~dfsg-1ubuntu1_i386.deb) ... Selecting previously deselected package system-config-samba. Unpacking system-config-samba (from .../system-config-samba_1.2.63-0ubuntu4_all.deb) ... Processing triggers for man-db ... Processing triggers for ufw ... Processing triggers for ureadahead ... ureadahead will be reprofiled on next reboot Processing triggers for bamfdaemon ... Rebuilding /usr/share/applications/bamf.index... Processing triggers for gnome-menus ... Processing triggers for desktop-file-utils ... Processing triggers for hicolor-icon-theme ... Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ... Administrator password will be set randomly! Unknown parameter encountered: &quot;max log size&quot; Ignoring unknown parameter &quot;max log size&quot; Unknown parameter encountered: &quot;syslog&quot; Ignoring unknown parameter &quot;syslog&quot; Unknown parameter encountered: &quot;passdb backend&quot; Ignoring unknown parameter &quot;passdb backend&quot; Unknown parameter encountered: &quot;unix password sync&quot; Ignoring unknown parameter &quot;unix password sync&quot; Unknown parameter encountered: &quot;passwd program&quot; Ignoring unknown parameter &quot;passwd program&quot; Unknown parameter encountered: &quot;pam password change&quot; Ignoring unknown parameter &quot;pam password change&quot; Unknown parameter encountered: &quot;map to guest&quot; Ignoring unknown parameter &quot;map to guest&quot; Unknown parameter encountered: &quot;usershare allow guests&quot; Ignoring unknown parameter &quot;usershare allow guests&quot; Unknown parameter encountered: &quot;guest ok&quot; Ignoring unknown parameter &quot;guest ok&quot; Unknown parameter encountered: &quot;guest ok&quot; Ignoring unknown parameter &quot;guest ok&quot; Unknown parameter encountered: &quot;max log size&quot; Ignoring unknown parameter &quot;max log size&quot; Unknown parameter encountered: &quot;syslog&quot; Ignoring unknown parameter &quot;syslog&quot; Unknown parameter encountered: &quot;passdb backend&quot; Ignoring unknown parameter &quot;passdb backend&quot; Unknown parameter encountered: &quot;unix password sync&quot; Ignoring unknown parameter &quot;unix password sync&quot; Unknown parameter encountered: &quot;passwd program&quot; Ignoring unknown parameter &quot;passwd program&quot; Unknown parameter encountered: &quot;pam password change&quot; Ignoring unknown parameter &quot;pam password change&quot; Unknown parameter encountered: &quot;map to guest&quot; Ignoring unknown parameter &quot;map to guest&quot; Unknown parameter encountered: &quot;usershare allow guests&quot; Ignoring unknown parameter &quot;usershare allow guests&quot; Unknown parameter encountered: &quot;guest ok&quot; Ignoring unknown parameter &quot;guest ok&quot; Unknown parameter encountered: &quot;guest ok&quot; Ignoring unknown parameter &quot;guest ok&quot; ProvisioningError: guess_names: 'realm =' was not specified in supplied /etc/samba/smb.conf.  Please remove the smb.conf file and let provision generate it dpkg: error processing samba4 (--configure):  subprocess installed post-installation script returned error exit status 1 No apport report written because MaxReports is reached already                                                               Setting up libuser1 (1:0.56.9.dfsg.1-1.2ubuntu1) ... Setting up python-libuser (1:0.56.9.dfsg.1-1.2ubuntu1) ... Setting up samba (2:3.5.11~dfsg-1ubuntu1) ... Generating /etc/default/samba... Importing account for nobody...ok Importing account for ryan...ok update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode. smbd start/running, process 2657 nmbd start/running, process 2684 Setting up system-config-samba (1.2.63-0ubuntu4) ... Processing triggers for libc-bin ... ldconfig deferred processing now taking place Processing triggers for python-support ... Processing triggers for python-central ... Errors were encountered while processing:  samba4 E: Sub-process /usr/bin/dpkg returned an error code (1) 
```  So is the answer in there somewhere?  Is there also any other windows transfer client or something? I just need to transfer my files to a windows pc.

---

### Post by Morbius1 on 2011-09-26
[1] Remove Samba4 from your system.

It's alpha level software - says so in synaptic - and not meant to be installed. Having it in the repositories is just cruel.

[2] I don't know what's going on here with this error message but you should try to search for that entire message in this forum:
> E: Sub-process /usr/bin/dpkg returned an error code (1)[3] If all you need is  to transfer files from A to B I would suggest Dukto: [http://code.google.com/p/dukto/downloads/list](http://code.google.com/p/dukto/downloads/list)
> **What is it?**

Dukto  is a standalone software, it doesn't need installation, it doesn't  creates any configuration file or registry key on your PC, it doesn't  require any software (apart from the operating system) to run, it  doesn't require configuration or account registration. And it runs on  Windows, Mac OS X and Linux. 

> **How it works?**

Dukto  usage is very simple, just start it on the two PC connected over the  LAN (or directly connected). On the buddy list will be showed the other  peer. Now simply drag and drop your files and folders over the dukto  window and they'll be transferred to the other end. That's all. 
It doesn't replace Samba or any other true file sharing protocol it simply lets someone transfer a file from A to B on your LAN. Comes in handy in situations like this. I actually carry it around on a usb stick just in case I have a "file transfer emergency".

---

### Post by Dyzphagia on 2011-09-26
Wonderful, thank you! I just need to transfer all these files so I can get my new hard drive in and install Crunchbang and it's hard when your external drive dies.

---

### Post by FOSScula on 2012-03-10
thank you Morbius1
> [1] Remove Samba4 from your system.

It's alpha level software - says so in synaptic - and not meant to be installed. Having it in the repositories is just cruel.thank you, this indirectly helped us in getting our LAN happily sharing between our windows & linux boxes. Never realized samba4 was an Alpha release. Glad to have removed the extra packages as well.

---

