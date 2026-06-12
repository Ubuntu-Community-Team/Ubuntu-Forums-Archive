---
title: "Device Manager install errors"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Ed J on 2008-07-12
I'm getting the following error while installing gnome device manager

:~/Desktop$ sudo dpkg -i libgnome-device-manager0_0.2-2_i386.deb
Selecting previously deselected package libgnome-device-manager0.
(Reading database ... 95672 files and directories currently installed.)
Unpacking libgnome-device-manager0 (from libgnome-device-manager0_0.2-2_i386.deb) ...
dpkg: dependency problems prevent configuration of libgnome-device-manager0:
 libgnome-device-manager0 depends on libpango1.0-0 (>= 1.20.2); however:
  Version of libpango1.0-0 on system is 1.20.1-1.
dpkg: error processing libgnome-device-manager0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnome-device-manager0


Do I have to install the libgnome-device-manager0 package?

Ed

---

### Post by drs305 on 2008-07-12
> **Ed J said:**
> I'm getting the following error while installing gnome device manager

:~/Desktop$ sudo dpkg -i libgnome-device-manager0_0.2-2_i386.deb
[B]dpkg: dependency problems prevent configuration of libgnome-device-manager0:
 libgnome-device-manager0 depends on libpango1.0-0 (>= 1.20.2); however:
  Version of libpango1.0-0 on system is 1.20.1-1.[/B]
dpkg: error processing libgnome-device-manager0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnome-device-manager0


Do I have to install the libgnome-device-manager0 package?

Ed

The area in bold is where the problem lies. The libpango version in the repos is older than that required for the install (1.20.1-1 vs 1.20.2).

It's possible that libpango just hasn't been updated quite yet. You may be able to find a later version on another server (synaptic, settings, repositories, download from > other).

---

### Post by Ed J on 2008-07-12
> **drs305 said:**
> The area in bold is where the problem lies. The libpango version in the repos is older than that required for the install (1.20.1-1 vs 1.20.2).

It's possible that libpango just hasn't been updated quite yet. You may be able to find a later version on another server (synaptic, settings, repositories, download from > other).

My synaptic settings were default and not updating squat.  That did the trick, thanks for the quick reply.

Ed J.

---

