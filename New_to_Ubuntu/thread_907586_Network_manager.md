---
title: "Network manager"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by moody_mark on 2008-09-01
Im using network manager in KDE and its working a charm. I would like to know though where it keeps all the settings. At my work I use unix (solaris) and a lot of the settings is in files like hme0.conf for the interface (dhcp or static ip). Some are there like /etc/resolv.conf but I cant find the setting for eth0 or eth1 for example.

But i cant seem to find where the settings are in kubuntu? :confused:

---

### Post by Sarah L on 2008-09-01
Settings for KDE apps are stored within the .kde folder in your home directory.

The settings for knetworkmanager are saved at:
[/home/username/.kde/share/config/knetworkmanagerrc]("/home/username/.kde/share/config/knetworkmanagerrc")

Hope this helps,
Sarah

---

### Post by moody_mark on 2008-09-02
Thank you! and would this be similar for the gnome desktop? If found a xml file in .gconf/system/networking/wireless/networks/<mynetworkname>

---

### Post by brentoboy on 2008-09-02
> **moody_mark said:**
> I cant find the setting for eth0 or eth1 for example.:confused:


Text file with per interface settings:
/etc/sysconfig/network

and the scripts for bringing things up and down are inside this directory:
/etc/sysconfig/network-scripts

---

### Post by moody_mark on 2008-09-04
> **brentoboy said:**
> Text file with per interface settings:
/etc/sysconfig/network

and the scripts for bringing things up and down are inside this directory:
/etc/sysconfig/network-scripts

I couldnt find those directories, all I got is /etc/network, which has the following;

```
curtis@Barney:/etc$ ls -la network
total 36
drwxr-xr-x   6 root root  4096 2008-07-02 11:16 .
drwxr-xr-x 127 root root 12288 2008-09-04 21:04 ..
drwxr-xr-x   2 root root  4096 2008-07-02 11:28 if-down.d
drwxr-xr-x   2 root root  4096 2008-07-02 11:20 if-post-down.d
drwxr-xr-x   2 root root  4096 2008-07-02 11:16 if-pre-up.d
drwxr-xr-x   2 root root  4096 2008-07-02 11:32 if-up.d
-rw-r--r--   1 root root    32 2008-09-02 07:50 interfaces

```

and the interfaces file has;

```
auto lo
iface lo inet loopback

```

Is there anywhere else I could look?

---

