---
title: "Apt-get upgrade &quot;kept back&quot; question"
date: 2006-07-17
forum: Repositories &amp; Backports
---

### Post by OBnascar on 2006-07-17
```
obnascar@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  gnome-cups-manager python-netcdf
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded
```

Can someone please tell me why these packages would be held back ?

---

### Post by reacocard on 2006-07-17
thay depend on another package that isn't being installed. use ```
sudo apt-get dist-upgrade
``` instead, it automatically installs nessecary dependencies.

---

### Post by OBnascar on 2006-07-17
```
obnascar@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-cups-manager python-netcdf
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

dist-upgrade tells me the same thing

---

### Post by SigmaX on 2006-07-24
I have the same issue -- except mine's with a fresh Breezy-to-Dapper telling me 73 packages have been kept back.

Any ideas?

SigmaX

---

### Post by dolby on 2006-07-25
u need to update the package which apt-get tells u is being kept back. use update manager or synaptic instead

---

### Post by OBnascar on 2006-07-25
> **dolby said:**
> u need to update the package which apt-get tells u is being kept back. use update manager or synaptic instead

You are correct dolby, I used synaptic to update those two packages and now I do not get a "kept back" message.

thanks,
Obnascar

---

### Post by SigmaX on 2006-07-27
Well in my case the inconsistancy prevented X from installing -- so synaptic wasn't an option (And why would synaptic solve what apt-get and aptitude did not?).  I just reinstalled.

For those who wish to avoid my situation in the future, I think it had something to do with installing automatix before the upgrade.  Don't remember exactly what I did, but the only thing I'd touched between Breezy install and Dapper upgrade was Automatix.

SigmaX

---

### Post by napzilla on 2008-06-19
This problem typically crops up every time I do an Ubuntu version upgrade. Sometimes, dist-upgrade works. In other cases, I've found that telling apt to remove the offending packages and then telling apt to install them again convinces it to find the required dependencies and resolves the problem.

---

