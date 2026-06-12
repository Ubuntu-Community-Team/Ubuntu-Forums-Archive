---
title: "No GUI, Raid1 NAS configuration help pls"
date: 2015-07-04
forum: New to Ubuntu
---

### Post by Nelg on 2015-07-04
Hi All,

A noobie to Ubuntu and raid1 server setup

I have installed Ubuntu Server 14.04 LTS on my N54L micro-server and have configured Server for contact with the outside world internet.

I have decided not to install a GUI on the server due to:
   1. the advice I've gained from reading these forums - security, CPU usage, etc
   2. the belief that I can use an 'icon driven' remote management panel (eg Home-Laptop with Windows installed) to configure and manage the server

***I am needing some assistance with point #2 please***

MY SCENARIO:
Server has Ubuntu Server 14.04 LTS installed (Install type: Basic server, DNS, OpenSSH, LAMP, SAMBA)
Server has no GUI installed
Server has successful connection with Intra and internet

Home-Laptop has windows 7 installed (newly formatted and Win7 install due to getting virus whilst trying to install Webmin)
Home-Laptop can see Server over LAN

MY CONFIGURATION REQUIREMENTS:
I would like to setup Server as NAS (RAID1)
I would like to setup 3-4 Users
I use Server as DLNA to watch movies and music
I often connect to my server from outside my local LAN to download files
I also use server to download torrent files

MY QUESTION:
[SIZE=2]**Which Home-Laptop Win7 remote software is easiest to INSTALL and USE to enable me to configure the Ubuntu Server (no GUI)?**[/SIZE]
Webmin so far has only given me viruses (due to reverting to previous Activestate Perl 5.8.8.8)


Thanks heaps in advance for your help...I think this is my last ditch effort at Ubuntu Server


Nelg

---

### Post by sandyd on 2015-07-04
> **Nelg said:**
> Hi All,

A noobie to Ubuntu and raid1 server setup

I have installed Ubuntu Server 14.04 LTS on my N54L micro-server and have configured Server for contact with the outside world internet.

I have decided not to install a GUI on the server due to:
   1. the advice I've gained from reading these forums - security, CPU usage, etc
   2. the belief that I can use an 'icon driven' remote management panel (eg Home-Laptop with Windows installed) to configure and manage the server

***I am needing some assistance with point #2 please***

MY SCENARIO:
Server has Ubuntu Server 14.04 LTS installed (Install type: Basic server, DNS, OpenSSH, LAMP, SAMBA)
Server has no GUI installed
Server has successful connection with Intra and internet

Home-Laptop has windows 7 installed (newly formatted and Win7 install due to getting virus whilst trying to install Webmin)
Home-Laptop can see Server over LAN

MY CONFIGURATION REQUIREMENTS:
I would like to setup Server as NAS (RAID1)
I would like to setup 3-4 Users
I use Server as DLNA to watch movies and music
I often connect to my server from outside my local LAN to download files
I also use server to download torrent files

MY QUESTION:
[SIZE=2]**Which Home-Laptop Win7 remote software is easiest to INSTALL and USE to enable me to configure the Ubuntu Server (no GUI)?**[/SIZE]
Webmin so far has only given me viruses (due to reverting to previous Activestate Perl 5.8.8.8)


Thanks heaps in advance for your help...I think this is my last ditch effort at Ubuntu Server


Nelg
Mainly, I recommend no control panel at all, and using SSH to administer the server, however Ajenti is a nice alternative to webmin.

If you want to actually have all the listed features by default, try using OpenMediaVault. It will require a total of 2 disks. One disk or a USB drive will be required for OpenMediaVault to be installed to + the two disks in RAID1. It will include a web panel to add and administer all the features you listed above.

Few options to provide the features you want without installing a panel:
I would like to setup Server as NAS (RAID1) -> MDADM
I would like to setup 3-4 Users -> Use useradd
I use Server as DLNA to watch movies and music -> Plex/Subsonic
I often connect to my server from outside my local LAN to download files -> Many options: Webserver, SSH/SCP, FTP.

---

### Post by gordintoronto on 2015-07-05
Your life would get a lot easier if you installed a GUI such as XFCE. Then you could install X11vnc and control the computer using RealVNC in Windows. There would be a small performance hit, but you aren't trying to support 1,000 users on a web site.

---

### Post by mastablasta on 2015-07-06
> **gordintoronto said:**
> Your life would get a lot easier if you installed a GUI such as XFCE. Then you could install X11vnc and control the computer using RealVNC in Windows. There would be a small performance hit, but you aren't trying to support 1,000 users on a web site.

it would also offer more attack vectors. besides there is no need for a desktop environment as there are plenty of tools out there that offer to control the server via browser.

the officialy supported one is Zentyal. 

OpenMediaVault is easy to install and maintain however it has a bug which will make it's monitoring software write errors into logs constantly spinning disks and filling up the log files with errors that are not errors. in a couple of minutes session I had 26 pages of logs full with bogus error. compared to Ubuntu install, where a page or so was made in almost 2 days running. they say it is not an issue. sure until you need to read logs or if you want disks spinning constantly then it is not an issue.
other than that it is easy to use and install.

Ajenti is OK though maybe has a few things missing (not many plugins). but it has a web terminal as well as "notepad" - both make it easy to edit config files and run commands to start and stop services for example.

not sure how you got a virus with webmin, especially since it is installed on the server.

I would search for software RAID1 instructions. it's quite easy to do on install I am sure it is not that difficult to add after OS install.

to connect to server and securely transfer files you can use Filezilla or WinScp and then use the sFTP protocol (part of SSH server). for administering in CLI you can also use putty terminal.

if you want a more user friendly file upload/download you can use owncloud but make sure you install it from their PPA and do not forget to configure it as https (it seems this is still done post install). you can then install an owncloud client on windows machines and have your personal "dropbox". it supports versioning but as I understand it doesn't really do well as backup service.

---

### Post by Nelg on 2015-07-06
Wowzers! thanks for the advice...

I followed up on the idea of OpenMediaVault but I think there was a stronger argument to go with something like FreeNas...either way, I think I will persevere with SSH...like anything I guess, once you've done it once (SSH), it gets easier...

Regarding the virus...I had read that Webmin would only work with versions of Activestate Perl prior to 5.10.  I downloaded some dodgy version of 5.8.8.8 that loaded a heap of bloatware and a virus that slowed my data transfer rates...lesson learned...formatted my HDD and started again

I will give Zentyal a crack, as well as SSH
[COLOR=#000000]Few options to provide the features you want without installing a panel:[/COLOR]
[COLOR=#000000]I would like to setup Server as NAS (RAID1) -> MDADM[/COLOR]
[COLOR=#000000]I would like to setup 3-4 Users -> Use useradd[/COLOR]
[COLOR=#000000]I use Server as DLNA to watch movies and music -> Plex/Subsonic[/COLOR]
[COLOR=#000000]I often connect to my server from outside my local LAN to download files -> Many options: Webserver, SSH/SCP, FTP.

[/COLOR]A quick question...
re "[COLOR=#000000]to connect to server and securely transfer files you can use Filezilla or WinScp and then use the sFTP protocol (part of SSH server). for administering in CLI you can also use putty terminal."
[/COLOR]I take it this is idea is from external to my home LAN?
When I'm at home and inside my LAN, simple windows file explore is all that is required
this question feels really dumb...but just checking.

Thanks again and please keep the advice coming

Regards

Nelg

---

### Post by mastablasta on 2015-07-06
> **Nelg said:**
> Wowzers! thanks for the advice...

I followed up on the idea of OpenMediaVault but I think there was a stronger argument to go with something like FreeNas...either way, I think I will persevere with SSH...like anything I guess, once you've done it once (SSH), it gets easier...

FreeNas does seem better. at least they can't afford such bugs to be on their OS since they sell quite expencive NAS boxes with it. they also want to have plenty of RAM but most users said it runs fine on N54L even when you max it out at 8GB and on disks. FreeNAS is not a Linux system though it's BSD (unix descendant). if you start new it doesn't matter much. you have to learn it anyway. you just won't get much help here about it (you can try your luck in other OS part of forum maybe).

> 
Regarding the virus...I had read that Webmin would only work with versions of Activestate Perl prior to 5.10.  I downloaded some dodgy version of 5.8.8.8 that loaded a heap of bloatware and a virus that slowed my data transfer rates...lesson learned...formatted my HDD and started again 
I would think that is refereed to server side. not sure. anyway it looked overwhelming to me compared to clean &light interface like Ajenti.

> I will give Zentyal a crack, as well as SSH
[COLOR=#000000]
just remember Zentyal is aimed to replace Windows small business server so they aim to provide the same Service but in Linux. they had more modules but then moved them to community maintenance and dint' work out so well. so while it runs well now it doesn't have many modules and I think it rests on Ubuntu 15.04. if you do install it I suggest "expert mode" and then install without the desktop. it is still very easy to use. just a shame they lost so many modules that they had.

> 
[/COLOR]A quick question...
re "[COLOR=#000000]to connect to server and securely transfer files you can use Filezilla or WinScp and then use the sFTP protocol (part of SSH server). for administering in CLI you can also use putty terminal."
[/COLOR]I take it this is idea is from external to my home LAN?
When I'm at home and inside my LAN, simple windows file explore is all that is required
this question feels really dumb...but just checking.

sFTP can be used in both cases. you will setup SSH to log to it with keys. means any program that offers sFTp access can just load a key to access the files. I use it at LAN as well. it is just faster it seems. also I had issue with SAMBA (slow) on Linux-Linux. though it has some strange kinks (e.g. it's showing copy but there is no copy command only move on server)...

What you are talking about (using explorer to access files on server) - SAMBA is used for this. SAMBA is OK for LAN, I am not sure how secure it is for internet access. once setup you use favourites in explorer to reach server and then it asks you for password. after that it's like browsing windows machine. setup can be tricky (or not, depends really on LAN setup) but there a few people here that know how to do it. Zentyal makes it easy in that way that you can use the windows user password (AD) to authenticate and also it's easy to setup these services there.

not to scare you - I set it up on Linux desktops and it was relatively easy. you need to make sure that all computers are in same "workgroup". and on desktop it's easy to setup shared folder (right click & share) and such. even then I would often not see the PC from windows, however trying to connect manually to the PC by typing the address I get prompted for password and afterwards I can see it in networks. I use it sometimes but not too often. the benefit is that you could set it to be always mounted (this is the part that is having problem in my windows).

anyway it's your server, software is open source, set it up as you like it best, ask for advice. and make sure you secure it and that you have backup procedure in place.

I used internal USB to store the OS on a USB Flash drive. worked well for about 8 months until I think some power fluctuation corrupted the USB. the backup I had wasn't good so I had to reinstall the whole thing. I am still setting it up now. seriously thinking of getting an UPS but money is tight and it's cheaper to get a good backup going on another USB stick. Maybe we should create an N54L or microserver club. there is quite a few here using this little bad boy.

---

