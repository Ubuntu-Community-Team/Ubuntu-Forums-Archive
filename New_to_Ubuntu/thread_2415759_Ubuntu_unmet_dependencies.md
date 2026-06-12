---
title: "Ubuntu unmet dependencies"
date: 2019-03-31
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2019-03-31
I update to ubuntu 18 from 16 LTS

And now I get the following errors whenever I update

Checking connectivity with the snap store
==> Installing the LXD snap from the latest track for ubuntu-18.10
error: cannot perform the following tasks:
- Run install hook of "lxd" snap if present (run hook "install": /var/lib/snapd not root-owned 1001:1000)
dpkg: error processing archive /var/cache/apt/archives/lxd_1%3a0.4_all.deb (--unpack):
 new lxd package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lxd_1%3a0.4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by uRock on 2019-03-31
I am seeing there is a bug report on this issue, though there is no workaround listed, yet. [https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1807856](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1807856)

I also found this [https://github.com/Microsoft/WSL/issues/3664](https://github.com/Microsoft/WSL/issues/3664) with the following text possibly fixing the error;
> For future reference:
After aborting the do-release-upgrade script I was left with a working system, just had a broken lxd. These two lines fixed that:

```
sudo dpkg --force depends -P lxd
sudo dpkg --force depends -P lxd-client
```
Then **sudo apt upgrade** finishes up the upgrade 

This link, [https://askubuntu.com/questions/1119301/your-system-is-unable-to-reach-the-snap-store](https://askubuntu.com/questions/1119301/your-system-is-unable-to-reach-the-snap-store) offers the same advice given in the above quote.

I hope this is helpful.

---

### Post by weirdygeekpsych on 2019-04-01
YAY! thanks it worked

---

### Post by uRock on 2019-04-02
Awesome! That's very good to hear. :guitar:

Please click on the Thread Tools dropdown in the upper right to mark this thread as solved.

---

