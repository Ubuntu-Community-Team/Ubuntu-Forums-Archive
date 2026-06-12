---
title: "Sony UX UMPC"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Sabotage on 2008-08-30
I have a Sony UX UMPC, with touchscreen and many other options.  I have successfully installed Ubuntu, and only problems I have come across is No sound, and touchscreen mouse is not working.  My normal mouse works fine, but when I touch the screen, the mouse jumps around randomly.

I have install Ubuntu because I have seen compiz fusion on another Sony UX, and was impressed how smooth it was running.  I have tried installing compiz fusion, and have been getting an error (attached below).  If anyone can help me with my Sound/Touchscreen/or compiz problem, please help.....

Thanx Jeff...

pizzuto@jeff:~$ sudo apt-get -y remove compiz-core desktop-effects 
[sudo] password for pizzuto: 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
E: Couldn't find package desktop-effects 
pizzuto@jeff:~$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) 
--16:45:16-- [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) 
=> `DD800CD9.gpg.1' 
Resolving download.tuxfamily.org... 88.191.250.18 
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 4,180 (4.1K) [application/octet-stream] 

100%[====================================>] 4,180 20.01K/s 

16:45:17 (19.93 KB/s) - `DD800CD9.gpg.1' saved [4180/4180] 

pizzuto@jeff:~$ sudo apt-key add DD800CD9.gpg 
OK 
pizzuto@jeff:~$ sudo apt-get update 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages 
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources 
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages [14.8kB] 
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources [37B] 
Fetched 29.2kB in 2s (14.0kB/s) 
Reading package lists... Done 
pizzuto@jeff:~$ sudo apt-get -y upgrade 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
pizzuto@jeff:~$ sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf 
Reading package lists... Done 
Building dependency tree 
Reading state information... Done 
compiz is already the newest version. 
compiz-gnome is already the newest version. 
compizconfig-settings-manager is already the newest version. 
compiz-fusion-plugins-extra is already the newest version. 
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 
The following information may help to resolve the situation: 

The following packages have unmet dependencies: 
compizconfig-backend-gconf: Conflicts: libcompizconfig-backend-gconf but 0.6.0~git20071003+3v1ubuntu0 is to be installed 
E: Broken packages

---

### Post by bangmalley on 2008-08-31
compiz fusion is pre-installed in ubuntu. u just need to enable it. You can go to System > Preferences > Appearance, In Appearance Preferences select the Visual Effects tab, then, select Normal or Extra, depending on how fancy you want your desktop effects to be.

touchscreen is hard to setup in ubuntu. So far, I only found how to make touchscreen works in Samsung Q1.
[http://ubuntuforums.org/showthread.php?p=2512327#post2512327](http://ubuntuforums.org/showthread.php?p=2512327#post2512327)

---

