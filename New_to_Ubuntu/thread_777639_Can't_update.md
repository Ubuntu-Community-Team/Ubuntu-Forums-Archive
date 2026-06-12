---
title: "Can't update"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by alexj.powell on 2008-05-01
Get the following error:

Failed to fetch cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Beta amd64 (20080318.1)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Beta amd64 (20080318.1)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by alan34 on 2008-05-02
Go to System Administration - Synaptic Package Manager then click Settings the Repositories and untick the cdrom option.

Or in a terminal

sudo gedit /etc/apt/soures.list

and put a # in front of the line for the cdrom like this

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted

---

