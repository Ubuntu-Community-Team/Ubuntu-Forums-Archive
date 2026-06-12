---
title: "flash just died"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-10-05
flash aid will not resolve.

i get this for 64 bit

--2011-10-05 22:34:39--  [http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz)
Resolving download.macromedia.com... 95.100.83.191
Connecting to download.macromedia.com|95.100.83.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-10-05 22:34:40 ERROR 404: Not Found.

md5sum: *flash*: No such file or directory
Flash 64bit installation aborted, due to md5 checksum mismatch!


...and this for 32 bit


Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-downloader:i386

E: Package 'flashplugin-nonfree' has no installation candidate


ideas / solutions ?

---

### Post by cariboo on 2011-10-05
The 32-bit flash installer is just called flashplugin-installer. For 64-bit I use [SevenMachines ppa]("https://launchpad.net/~sevenmachines/+archive/flash")

---

### Post by flipper T on 2011-10-05
yes tried that.

after adding ppa and updating i do this:

sudo apt-get install flashplugin64-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xulrunner-1.9
The following NEW packages will be installed
  flashplugin64-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/9,122 B of archives.
After this operation, 246 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin64-installer.
(Reading database ... 266153 files and directories currently installed.)
Unpacking flashplugin64-installer (from .../flashplugin64-installer_11.0.1.129-0ubuntu0~sevenmachines1_amd64.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up flashplugin64-installer (11.0.1.129-0ubuntu0~sevenmachines1) ...
Downloading...
Getting [http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz)
--2011-10-05 23:28:14--  [http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_rc1_install_lin_64_090611.tar.gz)
Resolving download.macromedia.com... 95.100.83.191
Connecting to download.macromedia.com|95.100.83.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-10-05 23:28:15 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.




ps is the macromedia website down ?

---

### Post by flipper T on 2011-10-05
... and then


sudo apt-get install flashplugin64-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin64-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


but as far as i know, its not installed, certainly not working

---

### Post by garvinrick4 on 2011-10-05
Download from adobe.com and extract and install libflashplayer.so 
to /usr/lib/mozilla/plugins
Remove all other attempts just in case remnants hanging around first.
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
```One at a time below.
```
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

```
This above is for last resort, do not know why your flash is giving you trouble but this cleans up flash and lets you start anew.

---

### Post by paul_in_london on 2011-10-05
Have you tried downloading the .tar.gz from here?

[https://www.adobe.com/support/flashplayer/downloads.html](https://www.adobe.com/support/flashplayer/downloads.html)

I did this yesterday. Working ok here (32 bit and 64 bit).

---

### Post by flipper T on 2011-10-05
> **garvinrick4 said:**
> Download from adobe.com and extract and install libflashplayer.so 
to /usr/lib/mozilla/plugins


worked great

thx alot

what has caused this, working fine minutes before

---

### Post by garvinrick4 on 2011-10-05
> worked great

thx alot

what has caused this, working fine minutes before
Your welcome and I really have no idea why it fails, I just remove all things flash and
reinstall. Though I do not get hardly any flash problems anymore.
Flash aids script does this plus more usually that cures all that ails Flash, curios why that
did not cure.
ppa of seven machines works great also, again why it did not work with you is curios.
As long as you are working, should have had lovinglinux in thread who wrote flash aid now
he can talk some flash. Have a nice day flipperT

---

### Post by flipper T on 2011-10-05
did not need to do all that purging, but have saved text for future reference.

thx again.

first time flash aid has not worked for me in 2 years.

---

### Post by lovinglinux on 2011-10-10
> **flipper T said:**
> did not need to do all that purging, but have saved text for future reference.

thx again.

first time flash aid has not worked for me in 2 years.

The problem is that Adobe removed the old flash file from the server. I have already updated Flash-Aid server couple of days ago, so you can run it again to install the newest version of Flash.

---

### Post by Harry33 on 2011-10-10
For both 32-bit and 64-bit (native) architectures the latest Adobe flashplugin is best installed from the Oneiric repos directly.
Before the installation, the previous flashplugin must be uninstalled.

The package adobe-flashplugin (version 11.0.1.152-0oneiric1) can be installed for example with synaptic (from the partner repositories).

See here:
[https://launchpad.net/ubuntu/oneiric/amd64/adobe-flashplugin/11.0.1.152-0oneiric1](https://launchpad.net/ubuntu/oneiric/amd64/adobe-flashplugin/11.0.1.152-0oneiric1)

---

