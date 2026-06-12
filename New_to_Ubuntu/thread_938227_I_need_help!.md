---
title: "I need help!"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Draco(*)Knight on 2008-10-04
hi i am new with Ubuntu i have never used it before in my life i have an hp pavilion dv6000 and for some reason everything works except for my external display ie. s-video and external monitor does anybody have any tips?

---

### Post by howefield on 2008-10-04
I think that model has an nvidia graphics card, is that right ?

If so install nvidia-settings from synaptic package manager. Should be able to set up your displays from there.

---

### Post by Draco(*)Knight on 2008-10-04
this is what i did in terminal
stephen@stephen-laptop:~$ sudo apt-get install nvidia-settings
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  artsbuilder
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 679kB of archives.
After this operation, 1503kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe nvidia-settings 1.0+20080304-0ubuntu1.1 [679kB]
Fetched 679kB in 3s (210kB/s)           
Selecting previously deselected package nvidia-settings.
(Reading database ... 128702 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_1.0+20080304-0ubuntu1.1_i386.deb) ...
Setting up nvidia-settings (1.0+20080304-0ubuntu1.1) ...

it was successfully installed but how to configure my settings?

---

### Post by howefield on 2008-10-04
in terminal type

```
gksudo nvidia-settings
```

Backup your xorg.conf file first, just in case.

---

