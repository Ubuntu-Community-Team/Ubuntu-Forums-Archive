---
title: "Ubuntu 18.04 : Cannot install WPS office , Cannot open gitkracken."
date: 2018-05-02
forum: New to Ubuntu
---

### Post by abhijith.r on 2018-05-02
After upgrading to 18.04 , Im unable to open certain apps that i used to use in ubuntu 16. 
I installed WPS office, the icons do appear in the dock and menu. But when launched , nothing happens.
While i installed it , it showed that certains processes connot be completed.
A red icon showed up in the above panel, which displayed a message saying something like "Error > 0", and said "dependency not available".
Same happened in the case of gitkracken.
Im not an expert in ubuntu, donno how to solve this issue, need help in this issue. 

Thanks in advance ! :)

---

### Post by howefield on 2018-05-02
Looks like WPS has libpng12-0 as a dependency which is not available in the Bionic repositories. You could revert back to 16.04 which is supported till 2021.

```
hugh@bionic:~$  sudo apt install -s /home/hugh/Downloads/wps-office_10.1.0.5707_a21_amd64.deb
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'wps-office' instead of '/home/hugh/Downloads/wps-office_10.1.0.5707_a21_amd64.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 wps-office : Depends: libpng12-0 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

Alternatively, you could get the libpng12-0 package and install it, then install WPS. I've tested and it appears to work, but wouldn't generally recommend using packages form outside the version repositories that you are using.

---

### Post by howefield on 2018-05-02
PS. Didn't notice you mentioned gitkracken also, it seems to be installing no problem on 18.04 providing you haven't "broken" apt with the WPS install.

```
sudo apt install /home/hugh/Downloads/gitkraken-amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'gitkraken' instead of '/home/hugh/Downloads/gitkraken-amd64.deb'
The following additional packages will be installed:
  gconf-service gconf-service-backend gconf2 gconf2-common libgconf-2-4
Suggested packages:
  gconf-defaults-service gir1.2-gnomekeyring-1.0
The following NEW packages will be installed
  gconf-service gconf-service-backend gconf2 gconf2-common gitkraken libgconf-2-4
0 to upgrade, 6 to newly install, 0 to remove and 6 not to upgrade.
Need to get 911 kB/58.9 MB of archives.
After this operation, 278 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 gconf2-common all 3.2.6-4ubuntu1 [700 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 libgconf-2-4 amd64 3.2.6-4ubuntu1 [84.8 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 gconf-service-backend amd64 3.2.6-4ubuntu1 [58.1 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 gconf-service amd64 3.2.6-4ubuntu1 [2,036 B]
Get:5 http://gb.archive.ubuntu.com/ubuntu bionic/universe amd64 gconf2 amd64 3.2.6-4ubuntu1 [66.9 kB]
Get:6 /Data/Downloads/gitkraken-amd64.deb gitkraken amd64 3.6.0 [58.0 MB]
Fetched 911 kB in 2s (418 kB/s)
Selecting previously unselected package gconf2-common.
(Reading database ... 167840 files and directories currently installed.)
Preparing to unpack .../0-gconf2-common_3.2.6-4ubuntu1_all.deb ...
Unpacking gconf2-common (3.2.6-4ubuntu1) ...
Selecting previously unselected package libgconf-2-4:amd64.
Preparing to unpack .../1-libgconf-2-4_3.2.6-4ubuntu1_amd64.deb ...
Unpacking libgconf-2-4:amd64 (3.2.6-4ubuntu1) ...
Selecting previously unselected package gconf-service-backend.
Preparing to unpack .../2-gconf-service-backend_3.2.6-4ubuntu1_amd64.deb ...
Unpacking gconf-service-backend (3.2.6-4ubuntu1) ...
Selecting previously unselected package gconf-service.
Preparing to unpack .../3-gconf-service_3.2.6-4ubuntu1_amd64.deb ...
Unpacking gconf-service (3.2.6-4ubuntu1) ...
Selecting previously unselected package gconf2.
Preparing to unpack .../4-gconf2_3.2.6-4ubuntu1_amd64.deb ...
Unpacking gconf2 (3.2.6-4ubuntu1) ...
Selecting previously unselected package gitkraken.
Preparing to unpack .../5-gitkraken-amd64.deb ...
Unpacking gitkraken (3.6.0) ...
Setting up gconf2-common (3.2.6-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Setting up libgconf-2-4:amd64 (3.2.6-4ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Setting up gconf-service (3.2.6-4ubuntu1) ...
Setting up gconf-service-backend (3.2.6-4ubuntu1) ...
Setting up gconf2 (3.2.6-4ubuntu1) ...
Setting up gitkraken (3.6.0) ...
```

---

### Post by abhijith.r on 2018-05-04
I installed [COLOR=#000000]libpng12-0[/COLOR]

When: 
sudo dpkg -i wps-office_10.1.0.5707_a21_amd64.deb


Log:

Selecting previously unselected package wps-office.
(Reading database ... 153844 files and directories currently installed.)
Preparing to unpack wps-office_10.1.0.5707_a21_amd64.deb ...
Unpacking wps-office (10.1.0.5707~a21) ...
dpkg: dependency problems prevent configuration of wps-office:
 wps-office depends on libpng12-0; however:
  Package libpng12-0 is not installed.


dpkg: error processing package wps-office (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.13.3-11ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for shared-mime-info (1.9-2) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Errors were encountered while processing:
 wps-office



WPS icons appeared in the menu, When clicked :

This notification came at the upper right corner of my desktop.

[Image]("https://ibb.co/hqkfyn")
[IMG]https://ibb.co/hqkfyn[/IMG]
[IMG]https://ibb.co/hqkfyn[/IMG]

---

### Post by howefield on 2018-05-09
Try running 

```
sudo apt-get install --fix-broken
```

Purge the existing WPS installation if you haven't already and then use apt to install the .deb package.

```
sudo apt install wps-office_10.1.0.5707_a21_amd64.deb
```

Use the full path to where the .deb package is stored, copy/pasting the file into the terminal will give you the correct path.

---

### Post by monkeybrain20122 on 2018-05-09
> **howefield said:**
> Try running 

```
sudo apt-get install --fix-broken
```

Purge the existing WPS installation if you haven't already and then use apt to install the .deb package.

```
sudo apt install wps-office_10.1.0.5707_a21_amd64.deb
```

Use the full path to where the .deb package is stored, copy/pasting the file into the terminal will give you the correct path.

Or OP could just right click it and bring up the software centre to install the .deb

@OP, dpkg does not download and install dependencies, so the recommended way is to either right click it (I prefer gdebi to the GSC) or do as howfield said ( but you need the full path for the .deb as he said, another way is to cd into the directory where the .deb is then run sudo apt install ./yourprogram.deb

---

### Post by Csar_Biosca. on 2018-10-31
Same problem and none of the above work for me... Tested installing the a21 which currently installs but after a few seconds it closes. And the 2016 does not let me install for dependencies... (libpng12-0 which by the way I can't install).
Is it a glitch or something else?

---

