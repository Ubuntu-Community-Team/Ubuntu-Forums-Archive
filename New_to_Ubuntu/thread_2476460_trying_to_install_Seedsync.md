---
title: "trying to install Seedsync"
date: 2022-06-27
forum: New to Ubuntu
---

### Post by billy3xs on 2022-06-27
Job for seedsync.service failed because the control process exited with error code.
See "systemctl status seedsync.service" and "journalctl -xe" for details.

The package installer seems to work, but Seedsync does not seem to be in applications.

~$ sudo dpkg -i seedsync_0.8.6_amd64.deb
(Reading database ... 213763 files and directories currently installed.)
Preparing to unpack seedsync_0.8.6_amd64.deb ...
Unpacking seedsync (0.8.6) over (0.8.6) ...
Setting up seedsync (0.8.6) ...
Setting user to henry           [COLOR=#008000]  (that part looks good, at least I got somewhere!)[/COLOR]
Job for seedsync.service failed because the control process exited with error code.
See "systemctl status seedsync.service" and "journalctl -xe" for details.
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...

So how do i "See "systemctl status seedsync.service" and "journalctl -xe" for details."

Or is there another way to install Seedsync?

thanks for your time!

---

### Post by ActionParsnip on 2022-06-27
What is the output of:
```

lsb_release -a

```
Thanks

---

### Post by ActionParsnip on 2022-06-27
Try:
```

sudo apt -f install

```
May help

---

### Post by ActionParsnip on 2022-06-27
Considering the package hasn't been updated since Dec 2020....is it still developed?
[https://github.com/ipsingh06/seedsync/releases/tag/v0.8.6](https://github.com/ipsingh06/seedsync/releases/tag/v0.8.6)

---

### Post by billy3xs on 2022-06-27
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.4 LTS
Release:	20.04
Codename:	focal
thanks!

---

### Post by billy3xs on 2022-06-27
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.4 LTS
Release:	20.04
Codename:	focal

---

### Post by billy3xs on 2022-06-27
~$ sudo apt -f install
[sudo] password for billy2xs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by billy3xs on 2022-06-27
> **ActionParsnip said:**
> Considering the package hasn't been updated since Dec 2020....is it still developed?
[https://github.com/ipsingh06/seedsync/releases/tag/v0.8.6](https://github.com/ipsingh06/seedsync/releases/tag/v0.8.6)

Good point, I'm using Filezilla and my download speads are terrible, 2-3 Mbit/sec.
So I'm just trying to find a better file download program.

---

