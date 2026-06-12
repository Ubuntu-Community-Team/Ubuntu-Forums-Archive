---
title: "Re: Linux newbie - New 14.04 LTS install. Lots of errors"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by Jeffrey_Becker on 2015-10-29
I was previously hosting serveral services on a windows machine when one of my favorite services stopped supporting windows in favor of Linux.
Realizing that Linux is popular for hosting and getting windows to play nice with Apache, PHP, MySQL in the past has been a huge pain I decided to come ~/
I'm about halfway through the CompTIA Linux+ class and I installed Ubuntu Desktop on my former windows server.

EDIT starting to think this is a problem with linux and the SSD drive it's installed on.

I feel like I've done plenty of digging on the forums but there are still some persistent errors.
Firefox crashes instantly or after a few web page requests.  Software-center crashes regularly.
Apport-gtk-root crashes as well as other apport related processes. I've also seen dpkg and python errors.

Some commands I've used to try and update:
```
sudo apt-get update
sudo apt-get upgrade 
sudo rm /var/crash/*
sudo apt-get -f instal
```

apt-get update has the following errors
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages)  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.



I've installed chromium and google chrome but can't find them now (lol I know I'm a newb)
EDIT ok I found chrome OSError ('CRC check failed 0x28f91159 != 0x1e0abb57',)

I also have TeamViewer installed since the server is a few states away at my dads house.
Open SSH server is installed as well in case TeamViewer locks up I can use another machine to init 6

Reading the forums I noticed people have had some trouble with the default eth driver r8169
I had rolled back to r8168 but have since done a complete reinstall of Ubuntu since I thought my DVD burn was corrupt.
Since I've compared MD5 hash on my iso file and verified the installation disk is intact.
currently I'm using the default r8169 driver

ls /var/crash/
```

_opt_teamviewer_tv_bin_TeamViewer_Desktop.1000.crash
_opt_teamviewer_tv_bin_TeamViewer_Desktop.1000.upload
_opt_teamviewer_tv_bin_TeamViewer_Desktop.1000.uploaded
_usr_bin_gdb.0.crash
_usr_lib_firefox_firefox.0.crash
_usr_lib_firefox_firefox.0.upload
_usr_lib_firefox_firefox.0.uploaded
_usr_lib_firefox_firefox.1000.crash
_usr_lib_firefox_firefox.1000.upload
_usr_lib_firefox_firefox.1000.uploaded
_usr_sbin_aptd.0.crash
_usr_sbin_aptd.0.upload
_usr_sbin_aptd.0.uploaded
_usr_sbin_update-apt-xapian-index.0.crash
_usr_share_oneconf_oneconf-query.1000.crash
_usr_share_software-center_piston_generic_helper.py.1000.crash
_usr_share_software-center_update-software-center-agent.1000.crash
```

cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse main restricted universe #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse main restricted universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports multiverse universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse universe main restricted
deb-src http://extras.ubuntu.com/ubuntu trusty main
```

[https://www.leaseweb.com/labs/2013/07/5-crucial-optimizations-for-ssd-usage-in-ubuntu-linux/](https://www.leaseweb.com/labs/2013/07/5-crucial-optimizations-for-ssd-usage-in-ubuntu-linux/)
Followed some of the instructions here.

---

### Post by yancek on 2015-10-29
You could try the suggestion at the link below for the 'failed to fetch' problem.

[http://askubuntu.com/questions/553765/failed-to-fetch-update-on-ubuntu-14-04-lts-trusty-tahr](http://askubuntu.com/questions/553765/failed-to-fetch-update-on-ubuntu-14-04-lts-trusty-tahr)

> I've installed chromium and google chrome but can't find them now (lol I know I'm a newb)

Type google-chrome in a terminal.  I beleive for chromium it is chromium-browser.  You should also be able to access them through the dash, the Ubuntu logo in the upper left of the Desktop.  Click it and type google-chrome or chromium-browser in the Search tab and it's icon should show up.

To find any installed application, you can also simply use the whereis command in a terminal::  EX:  whereis google-chrome.

---

### Post by Jeffrey_Becker on 2015-11-05
I did this 
> [COLOR=#111111][FONT=Consolas]sudo rm /var/lib/apt/lists/* -vf
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]sudo apt-get update[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
and still got errors > Fetched 31.6 MB in 11s (2,806 kB/s)                                            W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources)  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages)  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages)  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.




Now my GUI just crashed and I can connect using Teamviewer but I can't open the terminal with CTRL ALT T and I can't ssh in from another local machine. EDIT I got into ssh and rebooted the system with init 6 however it did not come back up in teamviewer.
I can still ping the device from the other local machine.

I don't have physical access and trying to move to ubuntu is proving very frustrating.

I haven't been getting many hits so I wanted some advice on what information would be helpful. 
I'm thinking it may be a hardware issue or some incompatible driver but I'm new to Linux and not too saavy on how to troubleshoot. Linux is currently installed on a solid state drive and I've been having some trouble with the graphics now.

Teamviewer will not stay loaded (graphics lock up, GUI locks up) and at one point I got a Linux config box saying something about low graphics mode but none of the options presented would allow me to continue into the GUI.

I still have SSH access so I can run commands with sudo and user but not as root since root was still disabled for ssh

---

### Post by Bucky Ball on 2015-11-06
Welcome. Did you check the disk for defects before installing? There is an option to do this at the 'Try Ubuntu' 'Install Ubuntu' screen prior to install. Did you check the md5sum of the ISO after downloading and prior to creating the install media? 

It looks like you somehow installed okay but your sources.list is pointing to the wrong repos. Thus the hashsum mismatch. This is unusual.

Have you changed the mirror in 'Software and Updates' by any chance? Have you done anything after install that may have caused this? Did you successful update and now it is giving this error the next time you try? Anything you can think of, obscure as it may seem?

It might be an idea to check the md5sum of the ISO, if that's okay, burn the install disk or USB, boot from it and 'Check disk for defects'. If that works ok then 'Try Ubuntu'. If all is still looking good, try again.

---

### Post by Jeffrey_Becker on 2015-11-06
Thanks for the reply! Yes after my first install attempt started throwing so many errors I checked the md5sum of the ISO and it was a match to the published md5.

> I had rolled back to r8168 but have since done a complete reinstall of Ubuntu since I thought my DVD burn was corrupt.
 Since I've compared MD5 hash on my iso file and verified the installation disk is intact.

The mirror was set to Americas and I did try changing it AFTER the problems popped up, to the other option I think it said default or official or main.. something like that.  It may be the disk and I'll check that but right now I think my dad is preparing to install 15.10.. I let him know to check the disk using the install DVD as you suggested

---

### Post by Bucky Ball on 2015-11-07
If you're still having issues, you might try 14.04 LTS. That has been around awhile, is long-term support and very stable. It is also upgradeable to the next LTS release 16.04 LTS directly next April. That will take you through to 2021. The interim releases, like 15.10, have nine months support and 15.10 dies next June, although that too is directly upgradeable to 16.04 LTS.

---

### Post by Jeffrey_Becker on 2015-11-07
14.04 LTS actual *IS* the ISO I downloaded and reinstalled twice. Thanks for the info though

---

### Post by Bucky Ball on 2015-11-07
> **Jeffrey_Becker said:**
> 14.04 LTS actual *IS* the ISO I downloaded and reinstalled twice. Thanks for the info though

Apologies. Mixed up with another thread while I was doing [s]five[/s] two things at once ... again. :)

---

### Post by Geoffrey_Arndt on 2015-11-07
One thought occurs after reading whole thread . . . *it's always a good idea to make the first install as "vanilla" as possible*.    Those optimizations in the link you provided may actually be unneeded or contributing to your specific configuration issue(s).   Also, hold off on intalling TeamViewer "temporarily" . . . . so you can test the vanilla install including Firefox.    Just a place to start . . . . this just doesn't fit the mold or seem like a successful install from the get go, with the mods compounding the instability of the core system.

Plus, in your next reply, a full recap of your hardware specs including gpu and wireless chipset if laptop.   Always a good idea initially to run off ethernet connection to verify install integrity.

---

### Post by Jeffrey_Becker on 2015-11-07
All drives tested good.. Perhaps a reinstall is in order?

Can you tell me how to determine which hardware I have and where to find the best libraries and driver packages for them?

---

### Post by Geoffrey_Arndt on 2015-11-08
Bunch o' ways . . . 

One easy way is:   
$ inxi -Fx

Post the output and we can determine which (if any) drivers needed.   The Linux kernel has many driver modules built in . . . for example, most INTEL wireless and gpu (e.g., Iris Pro 5200) don't require ANY driver installs.   But, if the hardware has proprietary elements such as nVidia or AMD/ATI or broadcom - then drivers are required.   These drivers normally can be installed via "System Settings>Software & Updates>Additional Drivers (tab).   

Re packages . . . . as long as the package/program is from an official source (ubuntu repositories) - it will be compatible.    

Other sources can be used for packages on an exception, as-needed basis.   Those packages should still be "debian" files (.deb), and can be installed via an official package manager app (ubuntu software center), or better yet, the "gdebi" stand-alone package manager.

Note:  gdebi and inxi may need to be installed first . . . can't recall if installed by default.

---

### Post by Jeffrey_Becker on 2015-11-08
I'm in software and updates. I checked the box to select the DVD.
Failed to load the package list
This is a serious proble. Try again later. If this problem appears again, please report an error to the developers
Details: 
> E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.

> **Bucky Ball said:**
> Welcome. Did you check the disk for defects before installing? There is an option to do this at the 'Try Ubuntu' 'Install Ubuntu' screen prior to install. Did you check the md5sum of the ISO after downloading and prior to creating the install media? 

It looks like you somehow installed okay but your sources.list is pointing to the wrong repos. Thus the hashsum mismatch. This is unusual.

Have you changed the mirror in 'Software and Updates' by any chance? Have you done anything after install that may have caused this? Did you successful update and now it is giving this error the next time you try? Anything you can think of, obscure as it may seem?

It might be an idea to check the md5sum of the ISO, if that's okay, burn the install disk or USB, boot from it and 'Check disk for defects'. If that works ok then 'Try Ubuntu'. If all is still looking good, try again.

Ubuntu Software: everything is checked. Source code has a check instead of a - like it did at first, Server is set to 'Server for United States'
Other software has canonical partners (source code), independent, independent (source code) and [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
Updates has trusty-security, trusty-updates, (pre-released not checked) unsupported updates.  Daily/ display immediately/ display weekly.

I removed the google stuff and got the same error as my last post

sudo rm -vf /var/lib/apt/lists/* ; sudo apt-get update | tee /output.txt
```
rm: cannot remove ‘/var/lib/apt/lists/partial’: Is a directorytee: /output.txt: Permission denied
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty InRelease
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty Release.gpg
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty Release
Err cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805) trusty/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [933 B]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release [58.5 kB]
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release [11.9 kB]
Get:6 [http://archive.canonical.com](http://archive.canonical.com) trusty Release [9,359 B]
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources [14 B]
Get:8 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources [10.0 kB]
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages [14 B]
Get:10 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages [5,637 B]
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages [14 B]
Get:12 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages [6,301 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources [1,064 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security InRelease [64.4 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease [64.5 kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources [5,433 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [64.4 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg [933 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Sources [2,346 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Sources [3,357 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Sources [98.1 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Sources [30.9 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main amd64 Packages [362 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted amd64 Packages [12.4 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe amd64 Packages [117 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse amd64 Packages [3,688 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main i386 Packages [342 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted i386 Packages [12.2 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe i386 Packages [117 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse i386 Packages [3,846 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en [196 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en [1,679 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en [3,076 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en [68.4 kB]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [32.1 kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [7,547 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [28 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1,571 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [38.3 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [8,999 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [38.3 kB]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [9,017 B]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en [5,013 B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en [1,215 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en [14 B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [33.7 kB]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,145 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [143 kB]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [242 kB]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [4,722 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [326 kB]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [644 kB]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.4 kB]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [327 kB]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.1 kB]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [313 kB]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,148 B]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,569 B]
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [172 kB]
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release [58.5 kB]
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [623 kB]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources [174 kB]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources [5,433 B]
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources [1,064 kB]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages [13.0 kB]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages [132 kB]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages [1,348 kB]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages [13.4 kB]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages [5,866 kB]
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages [134 kB]
Get:77 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en [762 kB]
Get:78 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en [102 kB]
Get:79 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en [3,457 B]
Get:80 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en [4,089 kB]
Get:81 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources [6,399 kB]
Get:82 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages [1,350 kB]
Get:83 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages [5,859 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
W: Failed to fetch cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Fetched 33.2 MB in 2min 4s (265 kB/s)
Failed to fetch cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Removing the CD-ROM as a possible repo put the - back in source code and completed without the error in my other post.
I ran sudo apt-get update again and it actually took some time to complete and OMG it finished with no errors. lol

I just tried this:
```
jnjinca@jnjinca-server:~$ sudo apt-get install[sudo] password for jnjinca: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
```

I then emptied /var/crash and I'm rebooting

Rebooted and all I got was a graphics error about the mode being wrong or something. I dismissed it since I think it's related to TeamViewer.
I'll let you know if anything else happens.

> **Bucky Ball said:**
> Welcome. Did you check the disk for defects before installing? There is an option to do this at the 'Try Ubuntu' 'Install Ubuntu' screen prior to install. Did you check the md5sum of the ISO after downloading and prior to creating the install media? 

It looks like you somehow installed okay but your sources.list is pointing to the wrong repos. Thus the hashsum mismatch. This is unusual.

Have you changed the mirror in 'Software and Updates' by any chance? Have you done anything after install that may have caused this? Did you successful update and now it is giving this error the next time you try? Anything you can think of, obscure as it may seem?

It might be an idea to check the md5sum of the ISO, if that's okay, burn the install disk or USB, boot from it and 'Check disk for defects'. If that works ok then 'Try Ubuntu'. If all is still looking good, try again.

The disks were all GOOD!

Ok I still can't open Chrome nor firefox.  Firefox opened and loaded google but crashed with SIGSEGV.
There are crash files from apport-gtk as well.

---

### Post by Bucky Ball on 2015-11-09
Do the full bit before going any further just so you know you have the latest. You had 36 held back from the update/upgrade command, probably a newer kernel, so:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Hopefully that will get through, get you updated/upgraded without spitting an error. :)

---

### Post by Jeffrey_Becker on 2015-11-09
sudo apt-get update succeeded with no problem
sudo apt-get upgrade crashed on the first attempt with SIGSEGV in strlen()
```
Segfault happened at: 0x7f4bfb780aea <strlen+42>:  movdqu(%rax,%xmm12
PC(0x7f4bfb780aea) ok
source"(%rax)"(0x7f4c908a76dc) not located in a known VMA region (needed readable region)!
destination "%xmm12" ok

```
second attempt was done immediately after that error and succeeded with no errors.
sudo apt-get dist-upgrade also appears to have been successful with no issues.

Rebooted. No errors.
Chrome crashed still says the error report belongs to a package that isn't installed.
Tried firefox and it worked a bit longer. Even go to run a speedtest and got some results. Once I tried another page it crashed.

More details about the FF crash

```
Add-ons: %7B972ce4c6-7e08-4474-a285-3208198ce6fd%7D:42.0,langpack-en-GB%40firefox.mozilla.org:42.0,langpack-en-ZA%40firefox.mozilla.org:42.0BuildID: 20151030084315
CrashTime: 1447057856
EMCheckCompatibility: true
Email: 
FramePoisonBase: 7ffffffff0dea000
FramePoisonSize: 4096
InstallTime: 1447057642
Notes: OpenGL: X.Org -- Gallium 0.4 on AMD TURKS -- 3.0 Mesa 10.5.9 -- texture_from_pixmap


ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SafeMode: 0
SecondsSinceLastCrash: 77
StartupTime: 1447057826
TelemetryEnvironment: {"build":{"applicationId":"{ec8030f7-c20a-464f-9b0e-13a3a9e97384}","applicationName":"Firefox","architecture":"x86-64","buildId":"20151030084315","version":"42.0","vendor":"Mozilla","platformVersion":"42.0","xpcomAbi":"x86_64-gcc3","hotfixVersion":null},"partner":{"distributionId":null,"distributionVersion":null,"partnerId":null,"distributor":null,"distributorChannel":null,"partnerNames":[]},"system":{"memoryMB":16019,"cpu":{"count":6,"vendor":null,"family":null,"model":null,"stepping":null,"extensions":["hasMMX","hasSSE","hasSSE2","hasSSE3","hasSSSE3","hasSSE4A","hasSSE4_1","hasSSE4_2"]},"os":{"name":"Linux","version":"3.19.0-32-generic","locale":"en-US"},"hdd":{"profile":{"model":null,"revision":null},"binary":{"model":null,"revision":null},"system":{"model":null,"revision":null}},"gfx":{"D2DEnabled":null,"DWriteEnabled":null,"adapters":[{"description":"X.Org -- Gallium 0.4 on AMD TURKS","vendorID":"X.Org","deviceID":"Gallium 0.4 on AMD TURKS","subsysID":null,"RAM":null,"driver":null,"driverVersion":"3.0 Mesa 10.5.9","driverDate":null,"GPUActive":true}],"monitors":[],"features":{"compositor":"none"}}},"settings":{"addonCompatibilityCheckEnabled":true,"blocklistEnabled":true,"isDefaultBrowser":false,"e10sEnabled":false,"telemetryEnabled":false,"isInOptoutSample":false,"locale":"en-US","update":{"channel":"release","enabled":true,"autoDownload":true},"userPrefs":{"browser.cache.disk.capacity":358400,"browser.newtabpage.enhanced":true}},"profile":{"creationDate":16735},"addons":{"activeAddons":{},"theme":{"id":"{972ce4c6-7e08-4474-a285-3208198ce6fd}","blocklisted":false,"description":"The default theme.","name":"Default","userDisabled":false,"appDisabled":false,"version":"42.0","scope":4,"foreignInstall":false,"hasBinaryComponents":false,"installDay":16652,"updateDay":16748},"activePlugins":[{"name":"QuickTime Plug-in 7.6.6","version":"","description":"The <a href=\"http://www.gnome.org/\">Videos</a> 3.10.1 plugin handles video and audio streams.","blocklisted":false,"disabled":false,"clicktoplay":true,"mimeTypes":["video/quicktime","video/mp4","image/x-macpaint","image/x-quicktime","video/x-m4v","application/vnd.apple.mpegurl"],"updateDay":16161},{"name":"DivX® Web Player","version":"","description":"DivX Web Player version 1.4.0.233","blocklisted":false,"disabled":false,"clicktoplay":true,"mimeTypes":["video/divx"],"updateDay":16161},{"name":"Windows Media Player Plug-in 10 (compatible; Videos)","version":"","description":"The <a href=\"http://www.gnome.org/\">Videos</a> 3.10.1 plugin handles video and audio streams.","blocklisted":false,"disabled":false,"clicktoplay":true,"mimeTypes":["application/x-mplayer2","video/x-ms-asf-plugin","video/x-msvideo","video/x-ms-asf","video/x-ms-wmv","video/x-wmv","video/x-ms-wvx","video/x-ms-wm","video/x-ms-wmp","application/x-ms-wms","application/x-ms-wmp","application/asx","audio/x-ms-wma"],"updateDay":16161},{"name":"VLC Multimedia Plugin (compatible Videos 3.10.1)","version":"","description":"The <a href=\"http://www.gnome.org/\">Videos</a> 3.10.1 plugin handles video and audio streams.","blocklisted":false,"disabled":false,"clicktoplay":true,"mimeTypes":["application/x-vlc-plugin","application/vlc","video/x-google-vlc-plugin","application/x-ogg","application/ogg","audio/ogg","audio/x-ogg","audio/x-vorbis+ogg","video/ogg","video/x-ogg","video/x-theora+ogg","application/annodex","audio/annodex","video/annodex","video/mpeg","audio/wav","audio/x-wav","audio/mpeg","application/x-nsv-vp3-mp3","video/flv","video/webm","application/x-totem-plugin","audio/midi"],"updateDay":16161},{"name":"iTunes Application Detector","version":"","description":"This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.","blocklisted":false,"disabled":false,"clicktoplay":true,"mimeTypes":["application/itunes-plugin"],"updateDay":16188},{"name":"Shockwave Flash","version":"11.2.202.540","description":"Shockwave Flash 11.2 r202","blocklisted":false,"disabled":false,"clicktoplay":false,"mimeTypes":["application/x-shockwave-flash","application/futuresplash"],"updateDay":16735}],"activeGMPlugins":{"gmp-gmpopenh264":{"version":null,"userDisabled":false,"applyBackgroundUpdates":1}},"activeExperiment":{},"persona":null}}
Theme: classic/1.0
Throttleable: 1
URL: 
Vendor: Mozilla
Version: 42.0
useragent_locale: chrome://global/locale/intl.properties


This report also contains technical information about the state of the application when it crashed.
```

---

### Post by Bucky Ball on 2015-11-09
Unreadable. Please see the last link in my signature and use code tags which will keep the formatting. Thanks.

If this is how the output actually looked, not much help to anyone, really. :|

Also, no idea what this is or where it popped up from in your output at the bottom:

URL: [https://habitica.com/#/tasks](https://habitica.com/#/tasks)

Do you even have habitica installed?

---

### Post by Jeffrey_Becker on 2015-11-09
the post looks neat and tidy and enclosed in QUOTE for me. Also I removed that URL from the post it was the website I was visiting.

---

### Post by howefield on 2015-11-09
> **Jeffrey_Becker said:**
> the post looks neat and tidy and enclosed in QUOTE for me....

Only because I changed the tags that you had used.

Use quote tags if you are quoting something another poster has said, use code tags for command line output - it preserves formatting and is usually easier to read.

---

### Post by Jeffrey_Becker on 2015-11-09
Noted. Sorry for that but thanks for fixing it.

---

### Post by Jeffrey_Becker on 2015-11-09
I've been using QUOTE the whole time because the CODE format button is only available in the advanced post editor and I've been using quick reply and on that note I'm going to bed. I'll try disabling addons and reinstalling firefox and chrome tomorrow (later today)

---

### Post by howefield on 2015-11-09
> **Jeffrey_Becker said:**
> I've been using QUOTE the whole time because the CODE format button is only available in the advanced post editor and I've been using quick reply

Cool, now you know,.

You can still use quick reply.. but type the tags out using [ code] at the beginning of the output and [ /code] (without the spaces) at the end of the output. Also please note the edit button which you can use to edit your previous post if you think of something to add shortly after your previous posting.

---

### Post by Geoffrey_Arndt on 2015-11-09
Yes,   it's a good idea to resist the urge to customize everything right away, before you understand the ABC's of the Linux/Unix environment.   Among other things, in a former life was a software tester . . . load, stress, HF, install/uninstall, etc.   

It especially matters in this case because of the unusual amount of errors you're getting.    Always a good thing to post (wish it were a standard requirement) is your hardware specs - - to eliminate those factors such as gpu driver/mismatch etc.

In a terminal (ctrl+alt+t), input below

inxi -Fx 

note:  you may have to install inxi first via Synaptic or USC

---

### Post by Jeffrey_Becker on 2015-11-10
```
System:    Host: jnjinca-server Kernel: 3.19.0-32-generic x86_64 (64 bit, gcc: 4.8.2)            Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: MSI model: 990XA-GD55 (MS-7640) version: 4.0 Bios: American Megatrends version: V22.5 date: 10/12/2012
CPU:       Hexa core AMD FX-6200 Six-Core (-MCP-) cache: 12288 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 45601.9 
           Clock Speeds: 1: 1400.00 MHz 2: 3800.00 MHz 3: 1400.00 MHz 4: 1900.00 MHz 5: 1400.00 MHz 6: 3800.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Turks XT [Radeon HD 6670/7670] bus-ID: 01:00.0 
           X.Org: 1.17.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on AMD TURKS GLX Version: 3.0 Mesa 10.5.9 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD 6000 Series] 
           driver: snd_hda_intel bus-ID: 01:00.1 
           Card-2: Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA) driver: snd_hda_intel bus-ID: 00:14.2 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-32-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: d000 bus-ID: 02:00.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: d4:3d:7e:91:4a:60
Drives:    HDD Total Size: 6625.5GB (23.6% used) 1: id: /dev/sda model: Samsung_SSD_840 size: 120.0GB temp: 0C 
           2: id: /dev/sdb model: ST2000DM001 size: 2000.4GB temp: 25C 3: id: /dev/sdc model: ST2000DM001 size: 4.1GB temp: 0C 
           4: USB id: /dev/sdd model: FreeAgent_GoFlex size: 1500.3GB temp: 0C 5: USB id: /dev/sde model: EZEX size: 1000.2GB temp: 0C 
           6: USB id: /dev/sdf model: EADS size: 1000.2GB temp: 0C 7: USB id: /dev/sdg model: 28AS size: 1000.2GB temp: 0C 
Partition: ID: / size: 95G used: 5.1G (6%) fs: ext4 ID: swap-1 size: 17.15GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 15.6C mobo: N/A gpu: 31.0 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 239 Uptime: 1 day Memory: 849.0/16018.9MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 



```

---

### Post by Jeffrey_Becker on 2015-11-10
Well some of the errors I believed were corrected are back.

EDIT: The problem is gone again.. Except now when I use sudo apt-get dist-upgrade it crashed the terminal at 50%.. trying another restart. I also installed Synaptic to try that.
EDIT: no errors now with apt update and upgrade.  Synaptic crashes. Firefox still crashes. random Apport-gtk-root crashes

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  Hash Sum mismatch


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources  Hash Sum mismatch


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  Hash Sum mismatch


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

Inside /var/lib/apt/lists I've cleared the lists and /partial folder
sudo apt-get update will redownload.. one file however is a bzip2 file named us.archive.ubuntu.com_ubuntu_trusty_universe_i18n_Translation_en

Can I disable the problematic repos? Can I change the mirror?

EDIT: I am definitely not getting errors from the terminal for apt-get update/upgrade/dist-upgrade and everything appears to be up to date. Firefox is up to date and still crashing regularly.
I still have crashes from seemingly random things. 
```
jnjinca@jnjinca-server:/$ ls /var/crash
libgdk-pixbuf2.0-0:i386.0.crash_usr_bin_apt-get.0.crash
_usr_bin_dpkg.0.crash
_usr_bin_gdb.1000.crash
_usr_bin_gdb.1000.upload
_usr_bin_gdb.1000.uploaded
_usr_bin_software-properties-gtk.1000.crash
_usr_lib_update-notifier_apt_check.py.1000.crash
_usr_share_apport_apport-checkreports.1000.crash
_usr_share_apport_apport-checkreports.1000.upload
_usr_share_apport_apport-checkreports.1000.uploaded
_usr_share_apport_apport-gtk.1000.crash
_usr_share_apport_apport-gtk.1000.upload
_usr_share_apport_apport-gtk.1000.uploaded
_usr_share_oneconf_oneconf-query.1000.crash
_usr_share_oneconf_oneconf-query.1000.upload
_usr_share_oneconf_oneconf-query.1000.uploaded
_usr_share_oneconf_oneconf-service.1000.crash



```!!
some other errors I'm getting are
```

Calculating upgrade... *** Error in `apt-get': corrupted double-linked list: 0x00000000020157b0 ***
----
dpkg: error processing package libgdk-pixbuf2.0-0:i386 (--configure):
 package libgdk-pixbuf2.0-0:i386 is not ready for configuration
 cannot configure (current status `half-installed')
----
Errors were encountered while processing:
 libgdk-pixbuf2.0-0:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----
E: Internal error, non-zero counts

```
Uninstalled and reinstalled Firefox - still crashing.
I also installed fglrx and it caused TeamViewer to stop working so I logged in with SSH and removed it.[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by Geoffrey_Arndt on 2015-11-11
With this hardware, you may want to take a shot at installing Wiley Werewolf . . . . with the latest kernel (4.2x).

---

### Post by Jeffrey_Becker on 2015-11-15
TL;DR  how can I properly read the error logs to see what is causing this stuff.. a missing lib maybe?
is there a way to narrow it down to hardware?

now using 15.10 kernel 4.2

Still getting seemingly random errors. They now appear linked to unity interface so I'm going to try LXDE

I'm also going to try switching from TeamViewer to VNC

Ok I'm using the Lubuntu guid. still getting crashes with ubuntu software center.
I've used Xdiagnose to disable bootloader graphics, VESA framebuffer driver, and PAT memory
Looks like using the Lubuntu stuff is not throwing errors and Chrome is working without issue.

Well.. now things are getting worse again..
When it boots up it hangs on the Ubuntu screen.
I was briefly connected through ssh but now that is not working either
Completely locked out again..

Had my dad reboot and 
sudo apt-get update/upgrade/dist-upgrade reports nothing
sudo apt-get autoremove

---

### Post by Jeffrey_Becker on 2015-11-17
Probably my last post here since the Title doesn't really fit all that well now that I'm using 15.10
I had my dad buy a new SSD and he's installed 15.10 again for me.

Then we installed TeamViewer and openssh-server
ran apt-get update/upgrade (not dist-upgrade)

In software and updates in additional drivers there's an entry
 Unknown: Unknown
This device is using an alternate driver.
Using Processor microcode firmware for AMD CPUs from amd64-microcode (proprietary)
Previously this was disabled

I'm reluctant to report 0 errors but it's definitely not spitting them every 10 seconds.
Firefox crashed once but I'm not planning on using it regularly.

AMDs catalyst software is installed but not using it yet. I still have the XOrg.org driver enabled.
I've tried enabling fglrx-updates and it takes a long time. I cancelled it on first attempt, later I was more patient and it is now using fglrx-updates.
pressing close triggered an error
software-properties-gtk crashed with SIGSEGV in PyTuple_ClearFreeList()
another error popped up briefly. /var/crash shows it was
_usr_share_apport_apport-gtk.1000.crash

I'm installing google-chrome-stable now.
After installing Software center crashed.

software-center crashed with SIGSEGV in PyGC_Collect()
the crash has about 5k lines of text
reopening it gave another errors
SIGSEGV in g_datalist_id_set_data_full()

installed apache2
restarted the machine.
It didn't start up TeamViewer so I had to ssh into it from my dad's PC and issue the sudo init 6 command.
I only have ssh access again. 

```
sudo apt-get remove fglrx-updates   fglrx-amdcccle-updates

```

after restarting again I can get into teamviewer again
firefox is behaving much better.. Still some minor problems but ultimately I think it was a failing SSD .
tomorrow I'll format and partition my HDD data disk so I can move some of the high write folders off the SSD.

---

