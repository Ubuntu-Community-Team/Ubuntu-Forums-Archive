---
title: "Cannot find repositories in Edgy"
date: 2019-03-04
forum: New to Ubuntu
---

### Post by rccharles on 2019-03-04
Ubuntu 6.10 Edgy.  I'm running on a Thinkpad T22. I'm a luddite, what can I say. 

I think that the pointers to the repositories/library are outdated.  Are these repositories/libraries archived somewhere?  How to I change ubuntu to reach the proper repositories/libraries? 
```

linux $ sudo apt-get install xkeycaps
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xkeycaps

```

Software Sources application said I wasn't up-to-date when I agreed to up date, I got these messages.
[ATTACH=CONFIG]282694[/ATTACH]

When I tried to update, I got a bunch of error messages.

```

linux $ sudo apt-get update
Ign http://us.archive.ubuntu.com edgy Release.gpg
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
... clipped ...
Err http://us.archive.ubuntu.com edgy/main Packages
  404 Not Found [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com edgy/restricted Packages
  404 Not Found [IP: 91.189.91.23 80]
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.91.23 80]
... clipped ...
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.91.23 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.91.23 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.91.23 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.91.23 80]
... clipped ...

```

---

### Post by CatKiller on 2019-03-04
That... wasn't even an LTS.

Those repositories have long been put out to pasture.

Reinstall with something supported.

---

### Post by rccharles on 2019-03-05
How to find archival versions of Ubuntu:
[https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

Working as I write this.

---

### Post by QIII on 2019-03-05
You do realize, of course, that using such an old and unsupported release will mean that you are working with no security updates for either the OS or any software you install?

I wouldn't let that machine get within 10 feet of any connection to the web.  That would be begging for compromise.

A chuckle to yourself about being a Luddite does not change the danger you place yourself in.

---

### Post by rccharles on 2019-03-06
Yes, I am aware of the security issues.  I use the machine as a VNC client.  That's all.

---

### Post by DuckHook on 2019-03-06
At the risk of belabouring the point:

[LIST]
[*]VNC is already one of the worst ever protocols in terms of security holes to start with.
[*]You have 13 years of accumulated security holes in what is already a heavily compromised protocol.
[*]You are operating a setup that has hundreds of security holes, each larger than a barn door.
[/LIST]
It's obviously your decision whether you upgrade or not because it's your neck that is being exposed, but these are public forums, so such awful, shoddy security practice cannot be permitted to go unremarked.

---

