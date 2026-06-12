---
title: "Packet Manager errors"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by s_x_g_t on 2008-11-27
Unable to even get started with it due to this error message. NO idea what to do next.

E: Dynamic MMap ran out of room
E: Error occurred while processing vlc-nox (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by Elfy on 2008-11-27
Check that you've not run out of room 

```
df -h
```

---

### Post by Michael.Godawski on 2008-11-27
You probably are either low on space or you have to increase the cache size.

To do so run this command:
```
gksudo gedit /etc/apt/apt.conf.d/70debconf
```and add this line:
```
APT::Cache-Limit "8388608";
```
or this if it's still now working:
```
APT::Cache-Limit "16777216";
```
But please post also your sources.list file before doing any changes:

```
cat /etc/apt/sources.list
```

---

