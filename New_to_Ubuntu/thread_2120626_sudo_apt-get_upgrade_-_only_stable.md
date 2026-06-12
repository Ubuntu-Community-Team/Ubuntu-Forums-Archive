---
title: "sudo apt-get upgrade - only stable?"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-27
Hi all, 

how do I perform 

# sudo apt-get upgrade

only for stable versions? 
Is it possible at all? 

Today my OS crashed just after upgrade. 
As far as I've heard before, Ubuntu installs unstable versions by default... Can I change these default settings or just set some additional console option to avoid unstable versions to be installed?

---

### Post by deadflowr on 2013-02-27
You heard wrong.

The command sudo apt-get upgrade only updates the software on your system. It does not upgrade the system version.



To only install stable updates, don't turn on proposed-updates.

---

### Post by marchelloUA on 2013-02-27
Ok, how do I turn off proposed-updates?

---

### Post by Paqman on 2013-02-27
> **marchelloUA said:**
> Ok, how do I turn off proposed-updates?

It's turned off by default, but if you did turn it on, you can turn it back off by opening Software Sources.

---

### Post by marchelloUA on 2013-02-27
Could someone please be so kind to tell me what console command should I perform to see what updates are turned on?

---

### Post by schragge on 2013-02-27
```

grep '^[^#]' /etc/apt/sources.list{,.d/*}

```

---

### Post by marchelloUA on 2013-02-27
Could someone please take a look at this list to help me turn off proposed-updates (if present) ? 

user@ubuntu:~$ sudo grep '^[^#]' /etc/apt/sources.list{,.d/*}
[sudo] password for user: 
/etc/apt/sources.list:deb [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal main restricted
/etc/apt/sources.list:deb-src [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal main restricted
/etc/apt/sources.list:deb [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal-updates main restricted
/etc/apt/sources.list:deb-src [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal-updates main restricted
/etc/apt/sources.list:deb [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal universe
/etc/apt/sources.list:deb-src [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal universe
/etc/apt/sources.list:deb [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal-updates universe
/etc/apt/sources.list:deb-src [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal-updates universe
/etc/apt/sources.list:deb [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal-security main restricted
/etc/apt/sources.list:deb-src [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal-security main restricted
/etc/apt/sources.list:deb [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal-security universe
/etc/apt/sources.list:deb-src [http://mirror.mirohost.net/ubuntu/](http://mirror.mirohost.net/ubuntu/) quantal-security universe
/etc/apt/sources.list.d/apachelogger-ubuntuone-kde-quantal.list:deb [http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu](http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu) quantal main
/etc/apt/sources.list.d/apachelogger-ubuntuone-kde-quantal.list:deb-src [http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu](http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu) quantal main
/etc/apt/sources.list.d/michael-gruz-canon-quantal.list:deb [http://ppa.launchpad.net/michael-gruz/canon/ubuntu](http://ppa.launchpad.net/michael-gruz/canon/ubuntu) quantal main
/etc/apt/sources.list.d/michael-gruz-canon-quantal.list:deb-src [http://ppa.launchpad.net/michael-gruz/canon/ubuntu](http://ppa.launchpad.net/michael-gruz/canon/ubuntu) quantal main
/etc/apt/sources.list.d/michael-gruz-canon-quantal.list.save:deb [http://ppa.launchpad.net/michael-gruz/canon/ubuntu](http://ppa.launchpad.net/michael-gruz/canon/ubuntu) quantal main
/etc/apt/sources.list.d/michael-gruz-canon-quantal.list.save:deb-src [http://ppa.launchpad.net/michael-gruz/canon/ubuntu](http://ppa.launchpad.net/michael-gruz/canon/ubuntu) quantal main
/etc/apt/sources.list.d/nilarimogard-webupd8-quantal.list:deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) quantal main
/etc/apt/sources.list.d/nilarimogard-webupd8-quantal.list:deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) quantal main
/etc/apt/sources.list.d/nilarimogard-webupd8-quantal.list.save:deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) quantal main
/etc/apt/sources.list.d/nilarimogard-webupd8-quantal.list.save:deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) quantal main
/etc/apt/sources.list.d/stvs-tomate-quantal.list:deb [http://ppa.launchpad.net/stvs/tomate/ubuntu](http://ppa.launchpad.net/stvs/tomate/ubuntu) quantal main
/etc/apt/sources.list.d/stvs-tomate-quantal.list:deb-src [http://ppa.launchpad.net/stvs/tomate/ubuntu](http://ppa.launchpad.net/stvs/tomate/ubuntu) quantal main
/etc/apt/sources.list.d/stvs-tomate-quantal.list.save:deb [http://ppa.launchpad.net/stvs/tomate/ubuntu](http://ppa.launchpad.net/stvs/tomate/ubuntu) quantal main
/etc/apt/sources.list.d/stvs-tomate-quantal.list.save:deb-src [http://ppa.launchpad.net/stvs/tomate/ubuntu](http://ppa.launchpad.net/stvs/tomate/ubuntu) quantal main

---

### Post by deadflowr on 2013-02-27
Well, you don't have proposed-updates enabled, however you are running bleeding edge (something thought of as highly unstable) PPAs such as the webupd8 ppa.

If you want stable, then avoid ppas for the bleeding edge.

---

### Post by marchelloUA on 2013-02-27
How do I turn off the webupd8 ppa ?

---

### Post by oldos2er on 2013-02-27
```
kdesudo software-properties-kde
``` Other Software tab, uncheck the appropriate box.

---

### Post by arpanaut on 2013-02-27
[https://help.ubuntu.com/community/Repositories/Kubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

