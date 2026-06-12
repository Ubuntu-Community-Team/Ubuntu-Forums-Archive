---
title: "Cannot install network printer"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-01-30
We have a Samsung SCX-4826FN network printer which is regularly accessed by one 10.04, one 12.04, and one Windows computer.

I have just installed 12.04 on a SSD in a new HP computer. I have just tried to set up this machine to print. When I click on add printer, it finds no less than four instances of the printer, but when I click on any of them, it flashes (and I mean flashes, these SSD's are really fast and those error message timers are set for much slower disks) this message:

Firewall ID is not running. Network printer detection needs services mdns, ipp, ipp-client, and samba-client enabled on firewall.

What firewall? What and where are "services mdns, ipp, ipp-client, and samba-client"?

I have downloaded the Unified Linux Driver from the Samsung website, unzipped, and tried to run it. But am now at a dead end. Nothing I try is working.

To add to my confusion. I thought I had already set it up to print a couple of weeks ago when I first started the installation, but haven't needed to print and so now am unsure if I did install it.

Help please.

---

### Post by Easy Limits on 2014-01-30
Try this command: system-config-printer 

There is a bug in 12.04 in regards to network printing.

---

### Post by Odyssey1942 on 2014-01-30
Easy Limits,

Thanks for this.

Biggest bunch of mumbo-jumbo I ever saw (see below) and had no optimism whatsoever about it working after seeing all those "Unknown parameter encountered:" messages.

But it did!

How did you come to know about this?

```
robert@robert-HP:~$ sudo apt-get install system-config-printer-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  avahi-utils python-cupshelpers python-gnomekeyring python-smbc
  system-config-printer-common system-config-printer-udev
The following NEW packages will be installed:
  avahi-utils python-cupshelpers python-gnomekeyring python-smbc
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev
0 upgraded, 7 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 347 kB of archives.
After this operation, 2,419 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main avahi-utils amd64 0.6.30-5ubuntu2.1 [29.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-cupshelpers all 1.3.8+20120201-0ubuntu8.1 [36.9 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main python-gnomekeyring amd64 2.32.0+dfsg-1 [26.9 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/main python-smbc amd64 1.0.13-0ubuntu1 [17.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main system-config-printer-common all 1.3.8+20120201-0ubuntu8.1 [33.4 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main system-config-printer-gnome all 1.3.8+20120201-0ubuntu8.1 [180 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main system-config-printer-udev amd64 1.3.8+20120201-0ubuntu8.1 [22.4 kB]
Fetched 347 kB in 1s (343 kB/s)                         
Selecting previously unselected package avahi-utils.
(Reading database ... 189448 files and directories currently installed.)
Unpacking avahi-utils (from .../avahi-utils_0.6.30-5ubuntu2.1_amd64.deb) ...
Selecting previously unselected package python-cupshelpers.
Unpacking python-cupshelpers (from .../python-cupshelpers_1.3.8+20120201-0ubuntu8.1_all.deb) ...
Selecting previously unselected package python-gnomekeyring.
Unpacking python-gnomekeyring (from .../python-gnomekeyring_2.32.0+dfsg-1_amd64.deb) ...
Selecting previously unselected package python-smbc.
Unpacking python-smbc (from .../python-smbc_1.0.13-0ubuntu1_amd64.deb) ...
Selecting previously unselected package system-config-printer-common.
Unpacking system-config-printer-common (from .../system-config-printer-common_1.3.8+20120201-0ubuntu8.1_all.deb) ...
Selecting previously unselected package system-config-printer-gnome.
Unpacking system-config-printer-gnome (from .../system-config-printer-gnome_1.3.8+20120201-0ubuntu8.1_all.deb) ...
Selecting previously unselected package system-config-printer-udev.
Unpacking system-config-printer-udev (from .../system-config-printer-udev_1.3.8+20120201-0ubuntu8.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
Setting up avahi-utils (0.6.30-5ubuntu2.1) ...
Setting up python-cupshelpers (1.3.8+20120201-0ubuntu8.1) ...
Setting up python-gnomekeyring (2.32.0+dfsg-1) ...
Setting up python-smbc (1.0.13-0ubuntu1) ...
Setting up system-config-printer-common (1.3.8+20120201-0ubuntu8.1) ...
Setting up system-config-printer-gnome (1.3.8+20120201-0ubuntu8.1) ...
Setting up system-config-printer-udev (1.3.8+20120201-0ubuntu8.1) ...
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@robert-HP:~$ system-config-printer
No ID match for device usb://Samsung/SCX-4x26%20Series?serial=6575BAHSC00933V&interface=1:
MFG:Samsung;MDL:SCX-4x26 Series;CMD:PCL5E,PCL6,GDI,FAX2,FWV;
No ID match for device usb://Samsung/SCX-4x26%20Series?serial=6575BAHSC00933V&interface=1:
MFG:Samsung;MDL:SCX-4x26 Series;CMD:PCL5E,PCL6,GDI,FAX2,FWV;
No ID match for device usb://Samsung/SCX-4x26%20Series?serial=6575BAHSC00933V&interface=1:
MFG:Samsung;MDL:SCX-4x26 Series;CMD:PCL5E,PCL6,GDI,FAX2,FWV;
robert@robert-HP:~$ 

```

---

### Post by Easy Limits on 2014-01-31
I had a similar issue with an Epson RX500 on my home network connected via a print server.  Someone on this forum had the answer.  Glad it worked for you.

---

