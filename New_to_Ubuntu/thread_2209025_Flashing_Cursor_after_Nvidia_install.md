---
title: "Flashing Cursor after Nvidia install"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by bug67 on 2014-03-03
I hope you guys can help. 

Everything was working fine with the Nvidia 319 drivers provided by the "additional drivers" tool.  However, being unable to let sleeping dogs lie, and knowing there was a more current driver available, I decided to update by:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
```

Upon re-boot, I am confronted with a blank screen with a flashing white cursor in the upper left hand.

I *believe* the problem lies with bumblebee, however, when I boot into recovery mode and do:

```
root@Lilly-Dell:~# sudo apt-get --purge remove bumblebee
```

I get the following return:

```
W:  Not using locking for read only lock file /var/lib/dpkg/lock
E:  Unable to write to /var/cache/apt/
E:  The package lists or status file could not be parsed or opened
```

What do I need to do here?

---

### Post by phidia on 2014-03-03
Look over [this thread]("http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process") for an answer to those locked directories maybe.

---

### Post by bug67 on 2014-03-03
Turns out I had to run fsck from the recovery menu first.  That allowd me to enter read/write of my file system.  I was then able to purge bumblebee and start my system running Nvidia driver 331.49!  :guitar:

---

