---
title: "Upgrading and dependencies"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by digitalsky on 2008-10-31
Hi,

I just upgraded from 8.04 server to 8.10 using do-release-upgrade. There were some errors in the process with some packages:

```
Setting up dbus (1.2.4-0ubuntu1) ...^M
Warning: The home dir /var/run/dbus you specified can't be accessed: No such file or directory^M
The system user `messagebus' already exists. Exiting.^M
chown: cannot access `/var/run/dbus': No such file or directory^M
dpkg: error processing dbus (--configure):^M
 subprocess post-installation script returned error exit status 1^M
dpkg: dependency problems prevent configuration of avahi-daemon:^M
 avahi-daemon depends on dbus (>= 0.60); however:^M
  Package dbus is not configured yet.^M
dpkg: error processing avahi-daemon (--configure):^M
 dependency problems - leaving unconfigured^M
dpkg: dependency problems prevent configuration of avahi-utils:^M
 avahi-utils depends on avahi-daemon; however:^M
  Package avahi-daemon is not configured yet.^M
dpkg: error processing avahi-utils (--configure):^M
 dependency problems - leaving unconfigured^M
Setting up libapache2-mod-mono (1.9-1) ...^M
Using mono-apache-server...^M
^M
Errors were encountered while processing:^M
 dbus^M
 avahi-daemon^M
 avahi-utils^M
```

I used apt-get remove to try to remove dbus, apt-get also removed consolekit that's "automatically installed".  But when I try to apt-get install dbus later:

```
Reading state information... Done
The following extra packages will be installed:
  consolekit dbus-x11 libpam-ck-connector
The following NEW packages will be installed:
  consolekit dbus dbus-x11 libpam-ck-connector
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 328kB of archives.
After this operation, 1389kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Why is it installing "dbus-x11" and "libpam-ck-connector", which weren't needed before?  I didn't see them when I removed dbus - so either something else depends on them or they were not there.  If something else depends on them, they should still be in the system and I won't need to install them now.  If they were not there, why would I need them now?

(I noticed in packages.ubuntu.com/intrepid that these are just recommended packages)

Also, is there a place where I can find packages that are installed by default in each release?

Thanks!

---

### Post by directhex on 2008-10-31
> **digitalsky said:**
> Also, is there a place where I can find packages that are installed by default in each release?

Thanks!

Install the "ubuntu-desktop" package, it will pull in all the packages required for a given release. If you have it already but have removed "Recommends:" packages you want to restore, run "apt-get install --fix-policy --install-recommends"

---

### Post by digitalsky on 2008-10-31
Thank you. That's helpful.  What if I want to find out what extra packages I installed that wasn't part of the default ubuntu-desktop package? (actually I'm using ubuntu server)

---

