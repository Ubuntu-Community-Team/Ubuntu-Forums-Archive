---
title: "FAQ: Ubuntu doesn't detect my cd.  How do I install?"
date: 2004-11-11
forum: Outdated Tutorials &amp; Tips
---

### Post by FLeiXiuS on 2004-11-11
-Hard Drive Install
-Networked Install (http/ftp)

**Hard Drive Install**
1.) Place Ubuntu ISO onto a seperate partition/hard drive other then what you're planning to install Ubuntu on.
2.) When the CDROM drive fails to ignitiate stage 1, it will prompt you with other methods of installations.
3.) Select Hard Drive Installation
4.) Enter in the location of the ISO then begin.


**Network Install**
I haven't tried this yet with Ubuntu, but with many other distrobutions it has been a sucess story.

Requirements: HTTP or FTP Remote Server
Keep in mind, LAN is much faster. So a local PC would be critical.

_HTTP_
1.) Extract the ISO in a directory with http access on the remote machine.
2. )Boot the Ubuntu CD and let the cdrom fail at stage 1.
3. )Select HTTP install
4.) Enter in the IP / Location of the extracted ISO on the remote server
5.) The Process should begin to install

_FTP_
1.) Extract the ISO in a directory with http access on the remote machine.
2.) Setup a username/password to access these files
3.) Boot the Ubuntu CD and let the cdrom fail at stage 1.
4.) Select FTP install
5.) Enter in the IP / Location / Username / Password of the FTP server where the ISO is located
6.) The Process should begin to install

---

### Post by herregud on 2005-03-03
Where can I select FTP install? When the CD-ROM detection fails the installation goes directly to the "Ubuntu installer main menu" where I can select the following:

Choose languange
Choose your location
Select a keyboard layout
Detect and mount CD-ROM
Load installer components from CD
Change debconf priority
Check the CD-ROM(s) integrity
Execute a shell
Abort the installation and reboot

 :confused:

---

