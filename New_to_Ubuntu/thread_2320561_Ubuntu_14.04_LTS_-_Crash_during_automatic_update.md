---
title: "Ubuntu 14.04 LTS - Crash during automatic update"
date: 2016-04-15
forum: New to Ubuntu
---

### Post by Zawfish on 2016-04-15
I have installed Ubuntu 14.04 LTS with a minimum of extra programs. Among these are Chrome browser and VLC media player.
 I just accepted the automatic update from Ubuntu. When I accept the update, I always check the details during the update. This time I think the update was 65 Mb. After the files were uploaded the update started, but suddenly my desktop restarted without any warning. I am sure it wasn&#8217;t because of any power failure. When the update wants to restart, there is usually an warning after the update, but this time I didn&#8217;t see any. After the restart the update apparently were finished. How can I check the update, and is this issue something I should report?

Best regards
ZF

---

### Post by grahammechanical on 2016-04-15
You can run Update Manager again. Look for it in the Dash by searching for Software Updater. You can also run a couple of commands and make a note of any errors. If there are errors then post them in the thread. Knowing the errors will be useful.

```
sudo apt-get update
sudo apt-get upgrade
```

Regards.

---

### Post by Zawfish on 2016-04-15
Thank you for the fast answer.

 
 sudo apt-get update &#8211; No errors reported, only 1.419 kB Fetched.

I am not sure if sudo apt-get upgrade are OK.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  linux-signed-image-3.19.0-25-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libmm-glib0 libnautilus-extension1a modemmanager nautilus nautilus-data
  simple-scan xserver-xorg-core-lts-vivid
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2.613 kB of archives.
After this operation, 108 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://dk.archive.ubuntu.com/ubuntu/ trusty-updates/main libmm-glib0 amd64 1.0.0-2ubuntu1.1 [130 kB]
Get:2 http://dk.archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a amd64 1:3.10.1-0ubuntu9.11 [52,1 kB]
Get:3 http://dk.archive.ubuntu.com/ubuntu/ trusty-updates/main modemmanager amd64 1.0.0-2ubuntu1.1 [473 kB]
Get:4 http://dk.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.11 [50,7 kB]
Get:5 http://dk.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus amd64 1:3.10.1-0ubuntu9.11 [481 kB]
Get:6 http://dk.archive.ubuntu.com/ubuntu/ trusty-updates/main simple-scan amd64 3.12.3-0ubuntu1 [135 kB]
Get:7 http://dk.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-core-lts-vivid amd64 2:1.17.1-0ubuntu3.1~trusty1 [1.291 kB]
Fetched 2.613 kB in 0s (3.387 kB/s)                    
(Reading database ... 288276 files and directories currently installed.)
Preparing to unpack .../libmm-glib0_1.0.0-2ubuntu1.1_amd64.deb ...
Unpacking libmm-glib0:amd64 (1.0.0-2ubuntu1.1) over (1.0.0-2ubuntu1) ...
Preparing to unpack .../libnautilus-extension1a_1%3a3.10.1-0ubuntu9.11_amd64.deb ...
Unpacking libnautilus-extension1a (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.9) ...
Preparing to unpack .../modemmanager_1.0.0-2ubuntu1.1_amd64.deb ...
modemmanager stop/waiting
Unpacking modemmanager (1.0.0-2ubuntu1.1) over (1.0.0-2ubuntu1) ...
Preparing to unpack .../nautilus-data_1%3a3.10.1-0ubuntu9.11_all.deb ...
Unpacking nautilus-data (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.9) ...
Preparing to unpack .../nautilus_1%3a3.10.1-0ubuntu9.11_amd64.deb ...
Unpacking nautilus (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.9) ...
Preparing to unpack .../simple-scan_3.12.3-0ubuntu1_amd64.deb ...
Unpacking simple-scan (3.12.3-0ubuntu1) over (3.12.1-0ubuntu1) ...
Preparing to unpack .../xserver-xorg-core-lts-vivid_2%3a1.17.1-0ubuntu3.1~trusty1_amd64.deb ...
Unpacking xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) over (2:1.17.1-0ubuntu3~trusty1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Setting up libmm-glib0:amd64 (1.0.0-2ubuntu1.1) ...
Setting up libnautilus-extension1a (1:3.10.1-0ubuntu9.11) ...
Setting up modemmanager (1.0.0-2ubuntu1.1) ...
modemmanager start/running, process 12795
Setting up nautilus-data (1:3.10.1-0ubuntu9.11) ...
Setting up nautilus (1:3.10.1-0ubuntu9.11) ...
Setting up simple-scan (3.12.3-0ubuntu1) ...
Setting up xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
zawfish@desktop:~$ 
```

Best regards

ZF

---

### Post by grahammechanical on 2016-04-15
Have you restarted? That is the test that will let you know if you have a working OS. If everything loads fine, then update daily for a few days just to see if there is anything that you did not get. But this is a concern.

> suddenly my desktop restarted without any warning.

Was it the desktop environment or the computer? If it was the computer then think about over-heating issues. Updating/Upgrading can be CPU intensive and that can increase heat output. Rather then burn out the CPU the motherboard may just restart.

Regards

---

### Post by Zawfish on 2016-04-15
Thank you for your advice. I will follow it and come back if there is any issues. I just made a hard restart, and everything seems to be OK, therefore I mark the thread solved.
Without going into details, I am confident the crash was not caused by CPU overload or similar.


 Thanks for your kind help.
 
 ZF

---

