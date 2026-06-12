---
title: "Unmet dependencies"
date: 2016-09-09
forum: New to Ubuntu
---

### Post by geirlock on 2016-09-09
Hey. 
I have a red stop sign on my toolbar that says 'Error BorkenCount >0', and I cant install packages needed for school.
When running commands I've seen from other threads with similar problems I get:

```

Bash@:~$ sudo dpkg --configure -a
Bash@:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
hannes@:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I'm running ubuntu 14.04 LTS

Help would be much appreciated, thanks!

---

### Post by Impavidus on 2016-09-09
Which version of Ubuntu?

Have you added any PPAs or stand-alone .deb packages?

---

### Post by mc4man on 2016-09-09
Open up Software & Updates > Updates tab & enable the first 2 (trusty-security, trusty-updates
Then reload your sources & proceed
(- libnl-genl-3-200 (3.2.21-1ubuntu3) is in trusy-updates, as seen here
[http://packages.ubuntu.com/trusty-updates/libnl-genl-3-200](http://packages.ubuntu.com/trusty-updates/libnl-genl-3-200)

---

### Post by geirlock on 2016-09-09
I'm running ubuntu 14.04 LTS.

I'm not sure what PPA's or stand-alone .deb packages are (even after googling it). But I've added a lot of packages to enable use of python / latex etc.

---

### Post by geirlock on 2016-09-09
> **mc4man said:**
> Open up Software & Updates > Updates tab & enable the first 2 (trusty-security, trusty-updates
Then reload your sources & proceed
(- libnl-genl-3-200 (3.2.21-1ubuntu3) is in trusy-updates, as seen here
[http://packages.ubuntu.com/trusty-updates/libnl-genl-3-200](http://packages.ubuntu.com/trusty-updates/libnl-genl-3-200)


Those were enabled. I don't know what you mean by 'reload your sources & proceed'.

---

### Post by mc4man on 2016-09-09
> **geirlock said:**
> Those were enabled. I don't know what you mean by 'reload your sources & proceed'.
If they were enabled then the newer version should be available. So go
```
sudo apt-get update
``` & see if you can install. If not post result of  - 
```
apt-cache policy libnl-genl-3-200
```

---

### Post by geirlock on 2016-09-09
> **mc4man said:**
> If they were enabled then the newer version should be available. So go
```
sudo apt-get update
``` & see if you can install. If not post result of  - 
```
apt-cache policy libnl-genl-3-200
```

The update worked, but I got the same error when using install. 
Requested results:

```

Bash@:~$ apt-cache policy libnl-genl-3-200libnl-genl-3-200:
  Installed: 3.2.21-1ubuntu1
  Candidate: 3.2.21-1ubuntu3
  Version table:
     3.2.21-1ubuntu3 0
        500 http://no.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 3.2.21-1ubuntu1 0
        100 /var/lib/dpkg/status
     3.2.21-1 0
        500 http://no.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages



```

---

### Post by mc4man on 2016-09-09
Sorry, I typed in wrong name - use this (seen here [http://packages.ubuntu.com/trusty-updates/libnl-3-200](http://packages.ubuntu.com/trusty-updates/libnl-3-200)
```
apt-cache policy libnl-3-200
```

---

### Post by geirlock on 2016-09-09
> **mc4man said:**
> Sorry, I typed in wrong name - use this (seen here [http://packages.ubuntu.com/trusty-updates/libnl-3-200](http://packages.ubuntu.com/trusty-updates/libnl-3-200)
```
apt-cache policy libnl-3-200
```
No problem, thanks for helping.


```

Bash@:~$ apt-cache policy libnl-3-200
libnl-3-200:
  Installed: 3.2.21-1
  Candidate: 3.2.21-1ubuntu3
  Version table:
     3.2.21-1ubuntu3 0
        500 http://no.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 3.2.21-1 0
        500 http://no.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by mc4man on 2016-09-09
So both packages need to be upgraded to current -updates versions. (3.2.21-1ubuntu3 
For starters just try this -
```
sudo apt-get upgrade
```
If that doesn't work we can try manually.

---

### Post by geirlock on 2016-09-12
> **mc4man said:**
> So both packages need to be upgraded to current -updates versions. (3.2.21-1ubuntu3 
For starters just try this -
```
sudo apt-get upgrade
```
If that doesn't work we can try manually.

Sorry for late response (been busy procrastinating.) Running upgrade and install I get:


```

bash@:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is installed
E: Unmet dependencies. Try using -f.


bash@:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu1) but 3.2.21-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies



```



Note: I might have disabled this update some months ago and forgot, I remember uninstalling an update because it caused problems.
But since I currently cant use the programs I need ill take my chances regardless.

---

### Post by ian-weisser on 2016-09-12
How might you have 'disabled this update'? Forcing? Holding? Pinning?

---

### Post by geirlock on 2016-09-12
> **ian-weisser said:**
> How might you have 'disabled this update'? Forcing? Holding? Pinning?

I don't know, I have zero skill with this, so I searched my error message and followed a threads guidelines. All I know is that I wrote some line in the terminal after uninstalling an update to keep it from getting reapplied.

---

### Post by ian-weisser on 2016-09-12
Can you recall the thread? Can you recall *any* details?
There are several  methods to accomplish what you seemed to do, no easy way to determine from here which method you did.
We can help you much better and faster a link to the instructions you followed, or knowing what command you used.
Check your browser history and bash history. Try to retrace your chain of googling.

Here's one shot in the dark: Please show us the complete contents of ALL files in /etc/apt/preferences.d/

---

### Post by geirlock on 2016-09-12
> **ian-weisser said:**
> Can you recall the thread? Can you recall *any* details?
There are several  methods to accomplish what you seemed to do, no easy way to determine from here which method you did.
We can help you much better and faster a link to the instructions you followed, or knowing what command you used.
Check your browser history and bash history. Try to retrace your chain of googling.

Here's one shot in the dark: Please show us the complete contents of ALL files in /etc/apt/preferences.d/

It occurred anywhere between 4 and 12 months ago and I cant recall many details so it would be very hard to find. I remember that It was targeted at this specific update and that It was supposed to update automatically when a newer version (where the bug that I don't remember what was, was fixed.)
But cant I install it manually as mac4man suggested, If I just disabled it from automatically updating that should still work right?

Anyway:
There are no files in  /etc/apt/preferences.d/

---

### Post by mc4man on 2016-09-12
you could try this - 
```
mkdir fixme1 && cd fixme1
```
```
wget http://mirrors.kernel.org/ubuntu/pool/main/libn/libnl3/libnl-3-200_3.2.21-1ubuntu3_amd64.deb \
http://mirrors.kernel.org/ubuntu/pool/main/libn/libnl3/libnl-genl-3-200_3.2.21-1ubuntu3_amd64.deb
```
If both dl successfully then in same terminal
```
sudo dpkg -i *.deb
```

---

### Post by geirlock on 2016-09-12
> **mc4man said:**
> you could try this - 
```
mkdir fixme1 && cd fixme1
```
```
wget http://mirrors.kernel.org/ubuntu/pool/main/libn/libnl3/libnl-3-200_3.2.21-1ubuntu3_amd64.deb \
http://mirrors.kernel.org/ubuntu/pool/main/libn/libnl3/libnl-genl-3-200_3.2.21-1ubuntu3_amd64.deb
```
If both dl successfully then in same terminal
```
sudo dpkg -i *.deb
```

Everything worked till the last part. 

```

 bash@:fixme1$ sudo dpkg -i *.deb

dpkg: regarding libnl-3-200_3.2.21-1ubuntu3_amd64.deb containing libnl-3-200:amd64:
 libnl-3-200:amd64 breaks network-manager (<< 0.9.8.8-0ubuntu7.3~)
  network-manager (version 0.9.8.8-0ubuntu7.2) is present and installed.


dpkg: error processing archive libnl-3-200_3.2.21-1ubuntu3_amd64.deb (--install):
 installing libnl-3-200:amd64 would break network-manager, and
 deconfiguration is not permitted (--auto-deconfigure might help)
(Reading database ... 1302466 files and directories currently installed.)
Preparing to unpack libnl-genl-3-200_3.2.21-1ubuntu3_amd64.deb ...
Unpacking libnl-genl-3-200:amd64 (3.2.21-1ubuntu3) over (3.2.21-1ubuntu1) ...
dpkg: dependency problems prevent configuration of libnl-genl-3-200:amd64:
 libnl-genl-3-200:amd64 depends on libnl-3-200 (= 3.2.21-1ubuntu3); however:
  Version of libnl-3-200:amd64 on system is 3.2.21-1.


dpkg: error processing package libnl-genl-3-200:amd64 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libnl-3-200_3.2.21-1ubuntu3_amd64.deb
 libnl-genl-3-200:amd64
Bash@:fixme1$ 



```

---

### Post by ian-weisser on 2016-09-12
> **geirlock said:**
> But cant I install it manually as mac4man suggested, If I just disabled it from automatically updating that should still work right?
[...]
dpkg: regarding libnl-3-200_3.2.21-1ubuntu3_amd64.deb containing libnl-3-200:amd64:
 libnl-3-200:amd64 **breaks network-manager** (<< 0.9.8.8-0ubuntu7.3~)

You answered most of that yourself.

The correct way to 'disable [some packages] from automatically upgrading'  is called *apt-pinning*, and it involves placing a simple *pin file* in /etc/apt/preferences.d/.
Easy to place, easy to check, easy to remove.
If yours is empty, then you didn't do that. You apparently haywired some other non-standard solution that could be anywhere in the system.
It would be too much to ask that the solution left log traces...haywires rarely do...but we'll check the logs anyway below.

Finding old details or links may be hard to find, but without more information, we are merely guessing blindly.
We might hit a solution. We might not. We might make things worse.

Here are some blind gropings to try:
Look at your /etc/apt settings.
Look in your /var/log/syslog and /var/log/apt/apt.history logs for clues.
Look for non-Ubuntu sources that have packages with wrong version numbers.

Do you recall the original error message thatled you to disable upgrading the package?

---

### Post by mc4man on 2016-09-12
so now check what version of network-manager
```
apt-cache policy network-manager
```

---

### Post by geirlock on 2016-09-12
> **mc4man said:**
> so now check what version of network-manager
```
apt-cache policy network-manager
```


```

network-manager:
  Installed: 0.9.8.8-0ubuntu7.2
  Candidate: 0.9.8.8-0ubuntu7.3
  Version table:
     0.9.8.8-0ubuntu7.3 0
        500 http://no.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 0.9.8.8-0ubuntu7.2 0
        100 /var/lib/dpkg/status
     0.9.8.8-0ubuntu7.1 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     0.9.8.8-0ubuntu7 0
        500 http://no.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages



```

---

### Post by geirlock on 2016-09-12
> **ian-weisser said:**
> You answered most of that yourself.

...
Here are some blind gropings to try:
Look at your /etc/apt settings.
Look in your /var/log/syslog and /var/log/apt/apt.history logs for clues.
Look for non-Ubuntu sources that have packages with wrong version numbers.

Do you recall the original error message thatled you to disable upgrading the package?

I'm sorry, the search history is wiped, I don't remember the error message (which is what I would have copy pasted into google to find the help thread). I've had many problems and done many fixes, now that mac4man asked about network manager I recall vaguely not having internet connection (I had to reboot to windows to get help), so that might be it. Also I remember running a script in one of the fixes but I don't think it was the same problem. 

I don't know how I look at /etc/apt settings.

Syslog only goes back to July, and I'm 99 % sure this fix happened before that (July is after programming season.) I'll have to look trough history later, it looks something like this though:

```

Start-Date: 2015-06-03  10:54:49
Commandline: aptdaemon role='role-commit-packages' sender=':1.58'
Upgrade: apt:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.8), libsystemd-login0:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), systemd-services:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), libssl1.0.0:amd64 (1.0.1f-1ubuntu2.11, 1.0.1f-1ubuntu2.12), apt-transport-https:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.8), isc-dhcp-common:amd64 (4.2.4-7ubuntu12.1, 4.2.4-7ubuntu12.2), apt-utils:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.8), unity:amd64 (7.2.4+14.04.20150316-0ubuntu1, 7.2.5+14.04.20150521.1-0ubuntu1), libunity-core-6.0-9:amd64 (7.2.4+14.04.20150316-0ubuntu1, 7.2.5+14.04.20150521.1-0ubuntu1), libsystemd-daemon0:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), libgudev-1.0-0:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), grub-common:amd64 (2.02~beta2-9ubuntu1.1, 2.02~beta2-9ubuntu1.2), libpam-systemd:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), libapt-inst1.5:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.8), unity-services:amd64 (7.2.4+14.04.20150316-0ubuntu1, 7.2.5+14.04.20150521.1-0ubuntu1), udev:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), grub2-common:amd64 (2.02~beta2-9ubuntu1.1, 2.02~beta2-9ubuntu1.2), gir1.2-gudev-1.0:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), libudev1:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), libreoffice-help-en-us:amd64 (4.2.7-0ubuntu1, 4.2.8-0ubuntu1), libapt-pkg4.12:amd64 (1.0.1ubuntu2.6, 1.0.1ubuntu2.8), libsystemd-journal0:amd64 (204-5ubuntu20.11, 204-5ubuntu20.12), isc-dhcp-client:amd64 (4.2.4-7ubuntu12.1, 4.2.4-7ubuntu12.2), grub-pc-bin:amd64 (2.02~beta2-9ubuntu1.1, 2.02~beta2-9ubuntu1.2), grub-pc:amd64 (2.02~beta2-9ubuntu1.1, 2.02~beta2-9ubuntu1.2), openssl:amd64 (1.0.1f-1ubuntu2.11, 1.0.1f-1ubuntu2.12)
End-Date: 2015-06-03  10:56:37

```

There are tons of these and I'm not quite sure how to filter them.

---

### Post by ian-weisser on 2016-09-12
Well...I'm terribly sorry, but without more information there's not much more I can safely suggest.
Perhaps another forum member will be able to help you further.

How critical is this system?
If you need it functioning quickly, are you willing to backup the data and reinstall?
Or are you willing to invest a few minutes across days (or weeks) to repair it and learn from the experience?

---

### Post by mc4man on 2016-09-12
Later i'll be at a 14.04 machine, maybe I can see better. For info run & post
```
apt-cache -a show network-manager
```
and what does this produce? (just a simulation, nothing will actually be done
```
sudo apt-get -s --ignore-hold dist-upgrade
```

---

### Post by geirlock on 2016-09-13
> **ian-weisser said:**
> Well...I'm terribly sorry, but without more information there's not much more I can safely suggest.
Perhaps another forum member will be able to help you further.

How critical is this system?
If you need it functioning quickly, are you willing to backup the data and reinstall?
Or are you willing to invest a few minutes across days (or weeks) to repair it and learn from the experience?

Oh I was not expecting it to be this hard, thanks a lot for your help anyway!
I need it for school, but I can use remote login. I'm not sure what I will do, seeing as I've had so many issues it might be best to reinstall.

---

### Post by geirlock on 2016-09-13
> **mc4man said:**
> Later i'll be at a 14.04 machine, maybe I can see better. For info run & post
```
apt-cache -a show network-manager
```
and what does this produce? (just a simulation, nothing will actually be done
```
sudo apt-get -s --ignore-hold dist-upgrade
```

```

@:~$ apt-cache -a show network-manager
Package: network-manager
Priority: optional
Section: net
Installed-Size: 2000
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 0.9.8.8-0ubuntu7.3
Depends: libc6 (>= 2.14), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libglib2.0-0 (>= 2.31.8), libgudev-1.0-0 (>= 146), libmm-glib0 (>= 0.7.991), libnl-3-200 (>= 3.2.7), libnl-genl-3-200 (>= 3.2.7), libnl-route-3-200 (>= 3.2.7), libnm-glib4 (>= 0.9.8.0), libnm-util2 (>= 0.9.6.0+git201212071413.8a9759a), libpolkit-gobject-1-0 (>= 0.99), libsoup2.4-1 (>= 2.26.1), libsystemd-login0 (>= 31), sysv-rc (>= 2.88dsf-24) | file-rc (>= 0.8.16), lsb-base (>= 3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev, isc-dhcp-client (>= 4.1.1-P1-4), iproute2, dnsmasq-base, policykit-1, iputils-arping
Pre-Depends: multiarch-support
Recommends: network-manager-pptp, network-manager-gnome | plasma-widget-networkmanagement | plasma-nm, ppp (>= 2.4.5), iptables, modemmanager, systemd-services, crda
Suggests: avahi-autoipd, python
Conflicts: connman
Breaks: network-manager-gnome (<< 0.9), network-manager-kde (<< 1:0.9), network-manager-openconnect (<< 0.9), network-manager-openvpn (<< 0.9), network-manager-pptp (<< 0.9), network-manager-vpnc (<< 0.9), plasma-widget-networkmanagement (<< 0.9~), ppp (<< 2.4.5)
Filename: pool/main/n/network-manager/network-manager_0.9.8.8-0ubuntu7.3_amd64.deb
Size: 500068
MD5sum: 0ec8580d5eb0c0ca878403c7137234c0
SHA1: e3eba78f07e03cf86d96b2b3ae4e54dfa9fe99fc
SHA256: 602e0c62ec42ec0e583c115fa69eec840cdc5473bee7cb40f3ce9074892caeb6
Description-en: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when
 available. It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE
 devices, and provides VPN integration with a variety of different VPN
 services.
 .
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager.
 .
 Optional dependencies:
  * ppp: Required for establishing dial-up connections (e.g. via GSM).
  * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
    address configuration.
Description-md5: 8f6f8b56b77097ec1e2134d2c9189882
Homepage: http://www.gnome.org/projects/NetworkManager/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-full, kubuntu-active, kubuntu-active-desktop, kubuntu-active-full, kubuntu-active, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-desktop, ubuntustudio-desktop, ubuntu-gnome-desktop


Package: network-manager
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 2000
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.9.8.8-0ubuntu7.2
Depends: libc6 (>= 2.14), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libglib2.0-0 (>= 2.31.8), libgudev-1.0-0 (>= 146), libmm-glib0 (>= 0.7.991), libnl-3-200 (>= 3.2.7), libnl-genl-3-200 (>= 3.2.7), libnl-route-3-200 (>= 3.2.7), libnm-glib4 (>= 0.9.8.0), libnm-util2 (>= 0.9.6.0+git201212071413.8a9759a), libpolkit-gobject-1-0 (>= 0.99), libsoup2.4-1 (>= 2.26.1), libsystemd-login0 (>= 31), sysv-rc (>= 2.88dsf-24) | file-rc (>= 0.8.16), lsb-base (>= 3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev, isc-dhcp-client (>= 4.1.1-P1-4), iproute2, dnsmasq-base, policykit-1, iputils-arping
Pre-Depends: multiarch-support
Recommends: network-manager-pptp, network-manager-gnome | plasma-widget-networkmanagement | plasma-nm, ppp (>= 2.4.5), iptables, modemmanager, systemd-services, crda
Suggests: avahi-autoipd, python
Breaks: network-manager-gnome (<< 0.9), network-manager-kde (<< 1:0.9), network-manager-openconnect (<< 0.9), network-manager-openvpn (<< 0.9), network-manager-pptp (<< 0.9), network-manager-vpnc (<< 0.9), plasma-widget-networkmanagement (<< 0.9~), ppp (<< 2.4.5)
Conflicts: connman
Conffiles:
 /etc/dbus-1/system.d/nm-dhcp-client.conf 06b1ecfd8f1fa2a501a5f352e2e5e88e
 /etc/dbus-1/system.d/nm-ofono.conf f59b8838ed17cfc66de16a977e87a66f
 /etc/dbus-1/system.d/org.freedesktop.NetworkManager.conf 6452efc377d78dac9ca1fb830fa74d94
 /etc/dbus-1/system.d/nm-avahi-autoipd.conf 91ab68968b0dc06c3a55b482b50b3028
 /etc/dbus-1/system.d/nm-dispatcher.conf 5711a76c31a3763750fe2c331741f679
 /etc/dnsmasq.d/network-manager c1f294c4513fa544565d671dcba6a913
 /etc/init/network-manager.conf 080b2a860317698f65f960687f5363cc
 /etc/NetworkManager/dispatcher.d/01ifupdown 9c08ef6e3612599c97d2404e3a9551a0
 /etc/NetworkManager/NetworkManager.conf 6e21dde76719887007828a1757643976
Description-en: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when
 available. It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE
 devices, and provides VPN integration with a variety of different VPN
 services.
 .
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager.
 .
 Optional dependencies:
  * ppp: Required for establishing dial-up connections (e.g. via GSM).
  * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
    address configuration.
Description-md5: 8f6f8b56b77097ec1e2134d2c9189882
Homepage: http://www.gnome.org/projects/NetworkManager/
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>


Package: network-manager
Priority: optional
Section: net
Installed-Size: 2000
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 0.9.8.8-0ubuntu7.1
Depends: libc6 (>= 2.14), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libglib2.0-0 (>= 2.31.8), libgudev-1.0-0 (>= 146), libmm-glib0 (>= 0.7.991), libnl-3-200 (>= 3.2.7), libnl-genl-3-200 (>= 3.2.7), libnl-route-3-200 (>= 3.2.7), libnm-glib4 (>= 0.9.8.0), libnm-util2 (>= 0.9.6.0+git201212071413.8a9759a), libpolkit-gobject-1-0 (>= 0.99), libsoup2.4-1 (>= 2.26.1), libsystemd-login0 (>= 31), sysv-rc (>= 2.88dsf-24) | file-rc (>= 0.8.16), lsb-base (>= 3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev, isc-dhcp-client (>= 4.1.1-P1-4), iproute2, dnsmasq-base, policykit-1, iputils-arping
Pre-Depends: multiarch-support
Recommends: network-manager-pptp, network-manager-gnome | plasma-widget-networkmanagement | plasma-nm, ppp (>= 2.4.5), iptables, modemmanager, systemd-services, crda
Suggests: avahi-autoipd, python
Conflicts: connman
Breaks: network-manager-gnome (<< 0.9), network-manager-kde (<< 1:0.9), network-manager-openconnect (<< 0.9), network-manager-openvpn (<< 0.9), network-manager-pptp (<< 0.9), network-manager-vpnc (<< 0.9), plasma-widget-networkmanagement (<< 0.9~), ppp (<< 2.4.5)
Filename: pool/main/n/network-manager/network-manager_0.9.8.8-0ubuntu7.1_amd64.deb
Size: 501324
MD5sum: e9e8b097712c52c3da381c17299b255a
SHA1: f0728b347476c9ef8f4e50ff4bf387119d84688d
SHA256: 04412458f59f3bcb435cf8707fcc58ef9481a486936cd6fc0bff519d34799400
Description-en: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when
 available. It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE
 devices, and provides VPN integration with a variety of different VPN
 services.
 .
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager.
 .
 Optional dependencies:
  * ppp: Required for establishing dial-up connections (e.g. via GSM).
  * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
    address configuration.
Description-md5: 8f6f8b56b77097ec1e2134d2c9189882
Homepage: http://www.gnome.org/projects/NetworkManager/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-full, kubuntu-active, kubuntu-active-desktop, kubuntu-active-full, kubuntu-active, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-desktop, ubuntustudio-desktop, ubuntu-gnome-desktop


Package: network-manager
Priority: optional
Section: net
Installed-Size: 2000
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 0.9.8.8-0ubuntu7
Depends: libc6 (>= 2.14), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libglib2.0-0 (>= 2.31.8), libgudev-1.0-0 (>= 146), libmm-glib0 (>= 0.7.991), libnl-3-200 (>= 3.2.7), libnl-genl-3-200 (>= 3.2.7), libnl-route-3-200 (>= 3.2.7), libnm-glib4 (>= 0.9.8.0), libnm-util2 (>= 0.9.6.0+git201212071413.8a9759a), libpolkit-gobject-1-0 (>= 0.99), libsoup2.4-1 (>= 2.26.1), libsystemd-login0 (>= 31), sysv-rc (>= 2.88dsf-24) | file-rc (>= 0.8.16), lsb-base (>= 3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev, isc-dhcp-client (>= 4.1.1-P1-4), iproute2, dnsmasq-base, policykit-1, iputils-arping
Pre-Depends: multiarch-support
Recommends: network-manager-pptp, network-manager-gnome | plasma-widget-networkmanagement | plasma-nm, ppp (>= 2.4.5), iptables, modemmanager, systemd-services, crda
Suggests: avahi-autoipd, python
Conflicts: connman
Breaks: network-manager-gnome (<< 0.9), network-manager-kde (<< 1:0.9), network-manager-openconnect (<< 0.9), network-manager-openvpn (<< 0.9), network-manager-pptp (<< 0.9), network-manager-vpnc (<< 0.9), plasma-widget-networkmanagement (<< 0.9~), ppp (<< 2.4.5)
Filename: pool/main/n/network-manager/network-manager_0.9.8.8-0ubuntu7_amd64.deb
Size: 501576
MD5sum: acb7a7e2139a0c7436fc18d8037e52a6
SHA1: 003a45fcd9e4be7e8b4fa969b685dc9584be2178
SHA256: 254fa3383c735e0009849818775cb178d364cb1329dea019f0ac4561697cb6a3
Description-en: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when
 available. It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE
 devices, and provides VPN integration with a variety of different VPN
 services.
 .
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager.
 .
 Optional dependencies:
  * ppp: Required for establishing dial-up connections (e.g. via GSM).
  * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
    address configuration.
Description-md5: 8f6f8b56b77097ec1e2134d2c9189882
Homepage: http://www.gnome.org/projects/NetworkManager/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-full, kubuntu-active, kubuntu-active-desktop, kubuntu-active-full, kubuntu-active, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-desktop, ubuntustudio-desktop, ubuntu-gnome-desktop

```


```

Bash@:~$ sudo apt-get -s --ignore-hold dist-upgrade
[sudo] password for Bash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu3) but 3.2.21-1 is installed
E: Unmet dependencies. Try using -f.



```

---

### Post by mc4man on 2016-09-13
How about
```
sudo apt-get --only-upgrade install network-manager
```

---

### Post by geirlock on 2016-09-14
> **mc4man said:**
> How about
```
sudo apt-get --only-upgrade install network-manager
```

```

Bash@:~$ sudo apt-get --only-upgrade install network-manager


Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libnl-genl-3-200 : Depends: libnl-3-200 (= 3.2.21-1ubuntu3) but 3.2.21-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




```

---

### Post by mc4man on 2016-09-14
Does this show anything?
```
dpkg -l | grep ^h
```

---

### Post by geirlock on 2016-09-17
> **mc4man said:**
> Does this show anything?
```
dpkg -l | grep ^h
```

Yes, I get:
```

hi  libnl-route-3-200:amd64                               3.2.21-1                                            amd64        library for dealing with netlink sockets - route interface



```

---

### Post by mc4man on 2016-09-17
> **geirlock said:**
> Yes, I get:
```

hi  libnl-route-3-200:amd64                               3.2.21-1                                            amd64        library for dealing with netlink sockets - route interface



```

Try 
```
sudo apt-mark unhold libnl-route-3-200
```
Then sudo apt-get update & sudo apt-get upgrade ect.

---

### Post by geirlock on 2016-09-17
> **mc4man said:**
> Try 
```
sudo apt-mark unhold libnl-route-3-200
```
Then sudo apt-get update & sudo apt-get upgrade ect.
update worked, upgrade didn't, but then I used apt-get -f install and now upgrade seemed to work. I think this solved the problem, so thank you very much!!

I'm just curious though, was this caused by me disabling an update or was that an unrelated issue?

---

### Post by mc4man on 2016-09-17
> **geirlock said:**
> 

I'm just curious though, was this caused by me disabling an update or was that an unrelated issue?
It was caused by pinning that particular package which prevented those related packages from upgrading.

---

### Post by geirlock on 2016-09-18
Alright. Thanks again, cheers!:)

---

