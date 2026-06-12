---
title: "update gone bad"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by krishnan t s on 2013-09-03
i recently purchased a lenovo laptop(g505s) and installedd ubuntu on it. install went well and i even got the proprietory graphics card installed. after install, i tried to update the laptop..there was a brief 30 second power outage and the laptop connected to the power source switched off as it had very little charge. on resuming, it continued with update and even rebooted successfully. However, the machine would not boot into the desktop.. itinstead booted saying that the system was running on low graphics. i rebooted and entered the previous kernel version. when i again tried to update from here, it showed the following text

E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libxcb-xfixes0_1.8.1-2ubuntu2.1_amd64.deb
debconf: apt-extracttemplates failed: 
dpkg-deb: error: `/var/cache/apt/archives/libxcb-xfixes0_1.8.1-2ubuntu2.1_amd64.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/libxcb-xfixes0_1.8.1-2ubuntu2.1_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libxcb-xfixes0_1.8.1-2ubuntu2.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


please help me.. i cant keep rebooting to the recovery console everytime i switch off the laptop.
P.S. i already tried sudo dpkg --configure -a and sudo apt-get -f install.. both show no errors
Thanks and have a nice day:)

---

### Post by Bashing-om on 2013-09-03
krishnan t s; Hi !

The files within "/var/cache/apt/archives/" -presently corrupted- may be safely removed.
```

sudo apt-get clean

```
will do the chore nicely.
Then in terminal, rebuild the index files:
```

sudo apt-get update
sudo apt-get upgrade

```

Please to advise of results.
[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

