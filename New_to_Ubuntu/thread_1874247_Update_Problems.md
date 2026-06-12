---
title: "Update Problems"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-11-02
I tried to update and ended up with a failed to update packages window with this explination

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygobject/python-gobject_3.0.0-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygobject/python-gobject-cairo_3.0.0-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.5.0-8ubuntu3_all.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.5.0-8ubuntu3_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_3.2.1-0ubuntu1_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_3.2.1-0ubuntu1_all.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.2.1-0ubuntu1_i386.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/python-cupshelpers_1.3.6+20110831-0ubuntu9.2_all.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.3.6+20110831-0ubuntu9.2_all.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.3.6+20110831-0ubuntu9.2_all.deb 404  Not Found [IP: 91.189.92.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-udev_1.3.6+20110831-0ubuntu9.2_i386.deb 404  Not Found [IP: 91.189.92.182 80]

```

---

### Post by alco75 on 2011-11-02
Well, it's all the same IP address.

I can reach that IP from my browser right now ...

---

### Post by jiggajoe506 on 2011-11-02
It is telling me to check my connection but I am posting here so obviously I have a connection....

---

### Post by jiggajoe506 on 2011-11-04
no help here?

---

### Post by philinux on 2011-11-04
> **jiggajoe506 said:**
> no help here?

Try changing the server to Main in software sources.

Also post back this.

cat /etc/apt/sources.list

---

### Post by Suroh66 on 2011-11-04
I've been seeing this a lot lately as well

---

### Post by jiggajoe506 on 2011-11-04
> **philinux said:**
> Try changing the server to Main in software sources.

Also post back this.

cat /etc/apt/sources.list

this is what I got...

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

Thanks in advance for your help

---

### Post by adamj2502 on 2011-11-08
I had the same issue, and fixed it by redirecting the repositories in Synaptic to the main ones, rather than UK. Maybe the UK servers aren't currently synchronised properly.

---

### Post by nnithi16 on 2011-11-08
I have the same problem as well. Tried changing over all the listed repositories, but no joy :(

---

### Post by jiggajoe506 on 2011-11-09
Yeah I still have this problem.

---

### Post by Silent Warrior on 2011-11-09
You have run apt-get update in between, I hope? Still, it's a weird issue... Most likely the server is just not in the mood, but ALL servers couldn't possibly have problems at once. With luck, though, apt-get is just looking for the wrong filenames - which should really have been noticed and fixed long ago. It doesn't happen to me, though, and I'm using 64-bit Oneiric.

---

