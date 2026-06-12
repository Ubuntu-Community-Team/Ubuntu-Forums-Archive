---
title: "Removing Avast virus scan for linux"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by Michael Steven on 2012-01-12
I installed the deb package avast4workstation_1.3.0-2_i386.deb using the dpkg and I'm not happy with the program. I want to UN-install this and I've tried to use dpkg -r avast4workstation_1.3.0-2_i386.deb but the command line returns an error message saying it needs the program name and not the package it came in. I've looked in /usr/bin and cannot find anything. When I do a whereis avast it tells me it is located in that path but i cannot find it and even when doing an ls- a. Can somebody help me. Having the program installed doesn't really hinder my use of the operating system, I just don't like wasting the space and having software installed that I do not intend to use. Not only that, I would love to know the process and commands for UN-installing deb packages once they are installed. I'm using Ubuntu 11.10 and a bash shell. thanks for the help!

Steve

---

### Post by cortman on 2012-01-12
> **Michael Steven said:**
> I installed the deb package avast4workstation_1.3.0-2_i386.deb using the dpkg and I'm not happy with the program. I want to UN-install this and I've tried to use dpkg -r avast4workstation_1.3.0-2_i386.deb but the command line returns an error message saying it needs the program name and not the package it came in. I've looked in /usr/bin and cannot find anything. When I do a whereis avast it tells me it is located in that path but i cannot find it and even when doing an ls- a. Can somebody help me. Having the program installed doesn't really hinder my use of the operating system, I just don't like wasting the space and having software installed that I do not intend to use. Not only that, I would love to know the process and commands for UN-installing deb packages once they are installed. I'm using Ubuntu 11.10 and a bash shell. thanks for the help!

Steve

```
sudo apt-get purge avast4work*
```

Should totally remove it from the system.

---

### Post by cortman on 2012-01-12
Sorry- missed the part about finding the program name.

```
apt-cache search --names-only avast
```

Will show all packages with the name avast. Find the main package and use the apt-get purge command on it.

---

### Post by critin on 2012-01-12
> Not only that, I would love to know the process and commands for UN-installing deb packages once they are installed

You also  should be able to uninstall any .deb through Software Center.  Find the program in "Installed Software" and choose Remove".

---

