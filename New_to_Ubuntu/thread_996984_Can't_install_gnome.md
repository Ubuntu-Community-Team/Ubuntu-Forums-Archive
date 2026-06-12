---
title: "Can't install gnome"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by jamil_1 on 2008-11-29
I am having following error when I try to Install gnome:

```
jamil@jamil-desktop:/$ sudo apt-get install ubuntu-desktop
[sudo] password for jamil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: rss-glx but it is not going to be installed
                  Recommends: bluez-gnome but it is not going to be installed
                  Recommends: openoffice.org-calc but it is not going to be installed
                  Recommends: openoffice.org-gnome but it is not going to be installed
                  Recommends: openoffice.org-writer but it is not going to be installed
                  Recommends: pulseaudio-module-gconf but it is not going to be installed
                  Recommends: pulseaudio-module-hal but it is not going to be installed
                  Recommends: pulseaudio-module-x11 but it is not going to be installed
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
E: Broken packages
jamil@jamil-desktop:/$ sudo apt-get install rss-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rss-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by Olivier2371 on 2008-11-29
What are trying to do.

Which Ubuntu version.

---

### Post by jamil_1 on 2008-11-29
jamil@jamil-desktop:/$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"


I messed dist-upgrade

---

### Post by Olivier2371 on 2008-11-29
When you say you messed up the upgrade, do you mean that you interrupted the update. 

Why are you trying to upgrade using the terminal?

Which version did youhave previously.

---

### Post by jamil_1 on 2008-11-29
I had feisty
I ran out of memory during upgrade(I have very small ubuntu partition)
I had previously KDE and Gnome but now KDE only. I want to install Gnome as well

---

### Post by oldos2er on 2008-11-29
Check your Software Sources to make sure they're all enabled.

---

### Post by Olivier2371 on 2008-11-29
If you have a very small Ubuntu partition, you should try Xubuntu.

---

