---
title: "Help with SAMBA configuration"
date: 2018-11-12
forum: New to Ubuntu
---

### Post by 52callaway on 2018-11-12
Hello, I'm new to Ubuntu and Unix in general. I built a Ubuntu 18.04.1 server and I have the main OS running on a SSD. I have one internal 2GB hard drive which is partitioned as NTFS and I have an external 2TB drive connected via SATA which is also partitioned as NTFS.  I'm running the MATE 1.20.1 GUI on the server.

I have the SAMBA service loaded on the server and I have tried configuring SMB shares for my family by creating SMB users that have the same user names and passwords as the Windows user using the unix command line. When you access the server via Networks from Windows 10 clients you see your own home folder but I'm having a lot of difficulty creating a shared folder that all users can access! When I created ubuntu users I used all lower case characters but if you look at a logged in user in windows with the command echo %username% they have a Upper case leading character like John vs john. I have no idea if this contributes to the sharing problem!

Command line management of SMB is not working very well for me! I created a shared folder named **1030Share** and I also created a group called sambashare on my server. I added all household users to the group. I tried to give group permissions to the folder/share but that doesn't work. The only person that has access to the share that I created is me!

In frustration I installed and ran system-config-samba and tried to manage the share from this GUI. I created a brand new share with the GUI, assigned every user access to the share, but other users cannot access the share from their Windows desktop!

One other possible contributing factor is the drive that I want shared is the external NTFS permission. This drive does not mount automatically and I always have to mount it by clicking on it in the Mate file handler. 

Any easy to understand instructions would be appreciated! Ubuntu tips seem to be very cryptic and difficult to understand.

---

### Post by mitesh.agrwl on 2018-11-12
Hi,

As everyone is able to access their respective accounts and files/folders, it is not a samba problem. It is configured properly. This might be the problem of folder/file permissions. Please go through the following articles regarding file permissions and change the values as per need.
[URL="https://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/x9543.htm"]
Article 1[/URL]
[Article 2]("http://www.tldp.org/pub/Linux/docs/ldp-archived/linuxfocus/English/January1999/article77.html")

---

### Post by 52callaway on 2018-11-12
If the GUI tools in MATE and in [COLOR=#000000]system-config-samba[/COLOR] don't set the appropriate permissions is this a problem with the ineffectiveness of the GUI? In MATE if you click on the mounted drive device name "Shared" and open as administrator it will show you more group names than without admin rights but it won't allow you to change anything. In SCS the GUI allows you to set all of the permissions for individual users but it also has no effect. I will pour over the two articles you included! Thanks!

---

### Post by 52callaway on 2018-11-12
So what would be the command to allow the group **sambashare** to have access to the SMB share named **1030Share** located on the mounted drive labeled **Shared** and accessed by the path: **/media/john/Shared/1030Share** ? when you do a ls-l the permissions are **drwxrwxrwx 1 john** but who knows what group really has these rights?

---

### Post by mitesh.agrwl on 2018-11-12
Hi,

I have not worked with the GUI tools of Samba, so not sure. In Linux, there are many Desktop Environment and a lot of GUI front ends, each has its own rules/settings. Thus the GUI method is not always reliable, but the command line is almost similar for a tool/program, with no or very little variation, in different flavours.Thus working with command line is more stable and provides better insights, might take a little time to get comfortable with it, but when its done looks more easy and open much opportunities to do. Please verify your settings/configurations using command line, which options are enabled/disabled and what permissions to whom are granted. Then you will be able to diagnose the problem in a better way and will get a effective solution.

---

