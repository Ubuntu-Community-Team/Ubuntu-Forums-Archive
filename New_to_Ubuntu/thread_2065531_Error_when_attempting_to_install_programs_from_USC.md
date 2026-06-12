---
title: "Error when attempting to install programs from USC"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by DePariah on 2012-10-02
When ever I try to install a program I get the following error:

installArchives() failed: Selecting previously unselected package kdrill. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 254008 files and directories currently installed.) 
Unpacking kdrill (from .../kdrill_6.5deb2-7ubuntu1_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Setting up ntp (1:4.2.6.p3+dfsg-1ubuntu3.1) ... 
useradd: cannot lock /etc/passwd; try again later. 
adduser: `/usr/sbin/useradd -d /home/ntp -g ntp -s /bin/false -u 118 ntp' returned error code 1. Exiting. 
chown: invalid user: `ntp:ntp' 
dpkg: error processing ntp (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up whoopsie (0.1.32) ... 
No apport report written because MaxReports is reached already
useradd: cannot lock /etc/passwd; try again later. 
adduser: `/usr/sbin/useradd -d /nonexistent -g whoopsie -s /bin/false -u 118 whoopsie' returned error code 1. Exiting. 
dpkg: error processing whoopsie (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Setting up kdrill (6.5deb2-7ubuntu1) ... 
Errors were encountered while processing: 
 ntp 
 whoopsie 
Error in function:  
Setting up ntp (1:4.2.6.p3+dfsg-1ubuntu3.1) ... 
useradd: cannot lock /etc/passwd; try again later. 
adduser: `/usr/sbin/useradd -d /home/ntp -g ntp -s /bin/false -u 118 ntp' returned error code 1. Exiting. 
chown: invalid user: `ntp:ntp' 
dpkg: error processing ntp (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up whoopsie (0.1.32) ... 
useradd: cannot lock /etc/passwd; try again later. 
adduser: `/usr/sbin/useradd -d /nonexistent -g whoopsie -s /bin/false -u 118 whoopsie' returned error code 1. Exiting. 
dpkg: error processing whoopsie (--configure): 
 subprocess installed post-installation script returned error exit status 1



Appologies if this is a really simple problem and I'm just being nooby, but hey everyone starts off knowing nothing :) I am running Ubuntu 12.04 on an eeePC (model 1001HA) if that helps with anything :) Thanks for taking the time to give me a hand :)

---

### Post by jerrrys on 2012-10-02
Welcome to the forums :)

For starters try this.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

Sudo apt-get clean

sudo apt-get update

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Get any errors?

---

