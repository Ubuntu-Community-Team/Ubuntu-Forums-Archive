---
title: "Commandline Web Server Questions"
date: 2013-12-06
forum: New to Ubuntu
---

### Post by skstid2012 on 2013-12-06
I'm running a commandline version of Ubuntu 12.04 LTS with Apache and PHP 5.3 in VMWare, acting as a webhost. After logging in, I've been prompted that several updates are available (11 being security updates).  Is there a way, through the commandline, to see which packages have upgrades available? Like, to display them as a list?  It's easy using Synaptic or the package manager that comes with Ubuntu to see these packages ... I'm just trying to find a way to do so through the commandline.  I've searched using Google. I've searched this forum. I've searched the Linux Mint and Debian forums.

All help is very much appreciated.


Thanks

---

### Post by oldos2er on 2013-12-06
How much detail do you want? ```
sudo apt-get update && sudo apt-get upgrade
``` will show you a list of package names to be upgraded. So will ```
sudo apt-get update && sudo apt-get upgrade -u
```

The package apt-listchanges will not only show you a list of packages to be upgraded, but the changelogs for each package too.

---

### Post by steeldriver on 2013-12-06
There's also

```
/usr/lib/update-notifier/apt-check --package-names
```

(it's a python script I think)

---

### Post by skstid2012 on 2013-12-06
steeldriver, you provided me with the answer I was actually looking for. This is the same thing I used a while back to get the last, I just couldn't remember the name. Thank you so very much!!!!!

---

### Post by skstid2012 on 2013-12-06
oldos2er,

I wanted to see the names of the packages in question before actually applying the upgrade. I decided to make a backup of my VM before going through with the upgrade.

---

### Post by oldos2er on 2013-12-06
Besides the commands I posted earlier, you can add -s to most any apt-get command to simulate the actions to be taken. ```
sudo apt-get update && sudo apt-get dist-upgrade -s
```

---

