---
title: "Ubuntu 11.10 apt-get update failed"
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by oc666 on 2011-08-17
Hello,
I've upgrade ubuntu 11.10 alpha 3.
When I try to update the system it can't upgrade 2 packages:
```
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gcj-4.5-jre-lib mono-runtime
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up apport (1.21.3-0ubuntu2) ...
SyntaxError: ("'continue' not properly in loop", ('/usr/share/apport/package-hooks/source_ubiquity.py', 30, None, 'continue\n'))

dpkg: error processing apport (--configure):
 subprocess installed post-installation script returned error exit status 101
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 apport
 apport-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How could I fix that?
Thanks

---

### Post by dino99 on 2011-08-17
a new fixed package is coming, patience.

note: you should post into Oneiric subforum, not here.

---

### Post by drs305 on 2011-08-17
Thread moved to "Ubuntu +1".

---

### Post by PaulW2U on 2011-08-17
Bug fixed - [https://bugs.launchpad.net/bugs/828037](https://bugs.launchpad.net/bugs/828037)

---

### Post by jbicha on 2011-08-17
These types of things happen in a development release. The x86 build of mono failed. Architecture independent builds always happen on an x86 machine so even though you're using a 64-bit system (I believe), you're still affected by the failed build. The mono build failure is known and will be fixed.

I think your gcj trouble was just because it takes some time for new packages to get built. Upgrading now should work for that one.

---

### Post by Junior41180 on 2011-10-02
not sure if I should report a separate bug but

```

Setting up flashplugin-installer (10.3.183.10ubuntu5) ...
nspluginwrapper: /usr/lib/flashplugin-installer/libflashplayer.so is not a valid NPAPI plugin
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I was able to apt-get -f install another package, but this error comes up consistently.

I did the update-manager -d to upgrade 11.04 to 11.10, should i have clean installed or is this still a bug?

---

### Post by cbaoth on 2011-10-03
Same issue here, fixed via:

```
sudo apt-get remove --purge flashplugin-downloader flashplugin-installer
sudo apt-get install flashplugin-installer
```

See [Bug #861584]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/861584") for details.

---

### Post by Junior41180 on 2011-10-03
> **cbaoth said:**
> Same issue here, fixed via:

```
sudo apt-get remove --purge flashplugin-downloader flashplugin-installer
sudo apt-get install flashplugin-installer
```See [Bug #861584]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/861584") for details.
TY for the info. :)

---

