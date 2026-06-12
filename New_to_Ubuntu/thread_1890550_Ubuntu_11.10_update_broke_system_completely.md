---
title: "Ubuntu 11.10 update broke system completely"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by beew on 2011-12-03
Reinstalled Ubuntu 11,10 the forth time last night. It was a clean install. It seems fine but then after the first attempted post installed update the system was completely broken , AGAIN!!! After update was aborted with these errors

```
3a3.2.2-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnomine_1%3a3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-sudoku_1%3a3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-mahjongg_1%3a3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-games-common_1%3a3.2.1-0ubuntu1_all.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-keyring_3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/python-pyatspi2_2.2.1-0ubuntu1_all.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/libbrlapi0.5_4.2-8ubuntu5.1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/python-brlapi_4.2-8ubuntu5.1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-orca_3.2.1-0ubuntu1_all.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/nautilus_1%3a3.2.1-0ubuntu3.1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/unity-2d-spread_4.12.0-0ubuntu1.1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/unity-2d-places_4.12.0-0ubuntu1.1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/unity-2d-panel_4.12.0-0ubuntu1.1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/unity-2d-launcher_4.12.0-0ubuntu1.1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/libunity-2d-private0_4.12.0-0ubuntu1.1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/unity-2d_4.12.0-0ubuntu1.1_all.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-session-bin_3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-power-manager_3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-session_3.2.1-0ubuntu1_all.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-session-common_3.2.1-0ubuntu1_all.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-screenshot_3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-search-tool_3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-session-canberra_0.28-0ubuntu11_all.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-system-log_3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gnome-system-monitor_3.2.1-0ubuntu1_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gwibber_3.2.1-0ubuntu1.3_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/gwibber-service_3.2.1-0ubuntu1.3_all.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
E: /var/cache/apt/archives/libgwibber2_3.2.1-0ubuntu1.3_i386.deb: unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
```The file system is completely corrupted and become "read only". Firefox claims it has not been shut down even though "top" command shows it is not running and "killall firefox" results in nothing.

Run fsck against the OO partition and fixed a long list of errors.  It seems to be working again (have write access) but attempted update results in the same error messages and broken system. 

I have not installed any ppa, this is the vanilla official updates except for Oneiric proposed, but in earlier trials I had disabled it and there was no difference.

---

### Post by bluexrider on 2011-12-03
Could it be that the "server of choice" is an issue when updating? 

I think I would 

sudo rm /var/cache/apt/archives/*

sudo apt-get clean

then in software sources make a different choice of servers

sudo apt-get update && sudo apt-get upgrade



I mean if its a 4th time install something else is wrong?

---

### Post by beew on 2011-12-03
> **bluexrider said:**
> Could it be that the "server of choice" is an issue when updating? 

I think I would 

sudo rm /var/cache/apt/archives/*

sudo apt-get clean

then in software sources make a different choice of servers

sudo apt-get update && sudo apt-get upgrade



I mean if its a 4th time install something else is wrong?

It is the 4th time because of other issues before unreleated to this. 11.10 is the most buggy release I have experienced. Even 11.04 on its first month of release (which was pretty bad) was not like this.

Will try your suggestion. But I will likely do it a 5th time. :) Even if I fix it I wouldn't trust it, just want to see if I can locate what causes the problem.

---

### Post by bluexrider on 2011-12-03
ever go skeet shooting....well you could make that 11.10 disk fly and use a 12 gauge

---

### Post by beew on 2011-12-04
Just finished the 5th reinstall. Seems ok then tried to install synaptic and gdebi from terminal. Busted again! These are the error message

```
Selecting previously deselected package gdebi-core.
(Reading database ... 125550 files and directories currently installed.)
Unpacking gdebi-core (from .../gdebi-core_0.8.1_all.deb) ...
Selecting previously deselected package gdebi.
Unpacking gdebi (from .../archives/gdebi_0.8.1_all.deb) ...
Selecting previously deselected package libept1.
Unpacking libept1 (from .../libept1_1.0.5build1_i386.deb) ...
Selecting previously deselected package synaptic.
Unpacking synaptic (from .../synaptic_0.75.2ubuntu8_i386.deb) ...
Processing triggers for man-db ...
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Read-only file system
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for gnome-menus ...
dpkg: unrecoverable fatal error, aborting:
 unable to flush updated status of `gnome-menus': Read-only file system
No apport report written because MaxReports is reached already
                                                              touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': Read-only file system
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

