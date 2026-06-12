---
title: "technical error"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by raghutalluri on 2012-10-31
i have a problem.... it is displaying an error message every time.. my lap is becoming too slow.. it does not start normally... after disk checking and after a long time it is getting started..

  the error message is...



           Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5: Input/output error), E:Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by COMECON on 2012-10-31
Try openning a Terminal (*Dash >> Terminal*) and running the following command:
```
$ sudo apt-get update
```Is it displaying any error? If it is, please post it here.

---

### Post by raghutalluri on 2012-11-03
Now the lap is not getting started.. i have to open the recovery in the grub.. later some menu is displayed with options like ENABLE NETWORKING,REPAIR BROKEN PACKAGES,FCSK someting some other options

---

### Post by ibjsb4 on 2012-11-03
> **raghutalluri said:**
> Now the lap is not getting started.. i have to open the recovery in the grub.. later some menu is displayed with options like ENABLE NETWORKING,REPAIR BROKEN PACKAGES,FCSK someting some other options

Lets start with the last one.  FSCK (think you have a typo).  This will check your hard drive and will take a couple of minutes.  [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo shutdown -r -F now

---

