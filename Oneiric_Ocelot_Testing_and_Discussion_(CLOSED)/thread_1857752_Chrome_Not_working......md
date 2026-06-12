---
title: "Chrome Not working....."
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by parkerskouson on 2011-10-10
Why wont google chrome work in oneiric???? 
Any one who knows how to fix it let me know...

Parker

---

### Post by effenberg0x0 on 2011-10-11
Hey, 

See the attached screenshot.
Please be more specific about the problem you're having.

Regards,
Effenberg

---

### Post by awam66 on 2011-10-11
> **parkerskouson said:**
> Why wont google chrome work in oneiric???? 
Any one who knows how to fix it let me know...

Parker

It works OK here both in 32bit and 64bit versions!

---

### Post by zenarcher on 2011-10-11
Likewise, Chrome in 64 bit is working fine here on 3 different machines.

Regards,
zenarcher

---

### Post by psypher on 2011-10-11
I am unable to install the latest chrome deb file at all, via Software Center or dpkg. In SC I get error: "Internal Error, the file "PATH/google-chrome-stable_current_amd64.deb" could not be opened" and via dpkg:


sudo dpkg -i google-chrome-stable_current_amd64.deb 
Selecting previously deselected package google-chrome-stable.
(Reading database ... 126362 files and directories currently installed.)
Unpacking google-chrome-stable (from google-chrome-stable_current_amd64.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libnspr4-0d (>= 4.7.3-0ubuntu1~); however:
  Package libnspr4-0d is not installed.
 google-chrome-stable depends on libxss1; however:
  Package libxss1 is not installed.
 google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Errors were encountered while processing:
 google-chrome-stable


I have tried paying with permissions and downloading the deb again.

EDIT: After trying to install that deb I got an notice to upgrade some apps but couldn't via update manager due to unmet dependencies. So i tried apt-get upgrade and it complained the same and suggested i try -f, so after upgrade -f it installed those pkgs AND chrome:

ruald@schweet:~$ sudo apt-get upgrade
[sudo] password for ruald: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 google-chrome-stable : Depends: libnspr4-0d (>= 4.7.3-0ubuntu1~) but it is not installed
                        Depends: libxss1 but it is not installed
                        Depends: libcurl3 but it is not installed
E: Unmet dependencies. Try using -f.
user@schweet:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  libcurl3 libnspr4-0d libxss1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 250 kB of archives.
After this operation, 750 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric/universe libnspr4-0d amd64 4.8.7-0ubuntu3 [11.1 kB]
Get:2 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric/main libxss1 amd64 1:1.2.1-2 [8,646 B]
Get:3 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) oneiric/main libcurl3 amd64 7.21.6-3ubuntu3 [230 kB]
Fetched 250 kB in 0s (729 kB/s)  
Selecting previously deselected package libnspr4-0d.
(Reading database ... 126448 files and directories currently installed.)
Unpacking libnspr4-0d (from .../libnspr4-0d_4.8.7-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libxss1.
Unpacking libxss1 (from .../libxss1_1%3a1.2.1-2_amd64.deb) ...
Selecting previously deselected package libcurl3.
Unpacking libcurl3 (from .../libcurl3_7.21.6-3ubuntu3_amd64.deb) ...
Setting up libnspr4-0d (4.8.7-0ubuntu3) ...
Setting up libxss1 (1:1.2.1-2) ...
Setting up libcurl3 (7.21.6-3ubuntu3) ...
Setting up google-chrome-stable (14.0.835.202-r103287) ...
update-alternatives: using /usr/bin/google-chrome to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/google-chrome to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ruald@schweet:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by zenarcher on 2011-10-11
I did my install using Synaptic, after adding the PPA for Chrome.  Don't know if that would make a difference.  And I used Chrome-Unstable.

Cheers,
zenarcher

---

### Post by miguelelmalo on 2011-10-11
Are you using encryption for your home directory?

I have had this problen duriing the whole development cycle of oneiric and just today, while testing the daily build I realized that I can "install" opera or chrome from the live cd, but not after I have installed to my HDD. I use encryption for my /home and I am gonna reinstall without this option.  

I&#314;l keep you informed

---

### Post by miguelelmalo on 2011-10-11
OK, I filed my observations under bug [#868188]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188") in Ubuntu Software Center Launchpad. I hope this get fixed ASAP because it seems to me a pretty important issue. You know, an inconvenience like this might frustrate a lot of users...

---

