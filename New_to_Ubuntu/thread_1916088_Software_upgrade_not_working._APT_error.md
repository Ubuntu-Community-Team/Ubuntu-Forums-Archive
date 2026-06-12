---
title: "Software upgrade not working. APT error"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by AliSajidImami on 2012-01-27
Hi guys. I was trying to upgrade to 10.10 from 10.04, when i hit the following error.


> [CENTER]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/mirror.letsopen.com_os_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
[/CENTER]


 Now no repository will load and i'm unable to user synaptic or apt or software center.

I googled and found out that running

```
sudo rm /var/lib/apt/lists/* -vrf
```

Will fix it, but that didn't work either. Any ideas?

---

### Post by cortman on 2012-01-27
Did you try running

```
sudo rm -r /var/lib/apt/*
```

without the -vrf? You then have to run

```
sudo apt-get update
```

If you get any errors from the second command, post them here.

---

