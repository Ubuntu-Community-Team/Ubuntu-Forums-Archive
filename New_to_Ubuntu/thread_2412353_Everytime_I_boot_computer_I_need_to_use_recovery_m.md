---
title: "Everytime I boot computer I need to use recovery mode"
date: 2019-02-11
forum: New to Ubuntu
---

### Post by crinlorite on 2019-02-11
Hello, this' not my first time in Ubuntu, it's a comeback, everything I wanted to make work in Ubuntu is working, my favorite game, my favorite android emulator, my favorite streaming client, but something's amiss, every time I boot the computer I need to use the recovery mode and click on resume, if I try to boot it normal this happens:

[https://photos.app.goo.gl/Y553riMVejA2jGAu9](https://photos.app.goo.gl/Y553riMVejA2jGAu9)

Then the screen turns black and monitor goes to sleep mode. Any ideas?

Thank you very much!

---

### Post by TheFu on 2019-02-11
Check the log files for errors and warnings.
I can't see any google stuff for some reason. Sorry.

---

### Post by crinlorite on 2019-02-12
> **TheFu said:**
> Check the log files for errors and warnings.
I can't see any google stuff for some reason. Sorry.
It's not my first time in Ubuntu but I've never been an experienced user.

How could I check those logs?

I'll upload the google photos video on YouTube asap.

---

### Post by oldfred on 2019-02-12
What video card/chip?

Often from installing nVidia driver from nVidia, not from Ubuntu repository. You have to reinstall into every new kernel if you install directly from nVidia with .run file.

---

### Post by oldrocker99 on 2019-02-12
> **oldfred said:**
> What video card/chip?

Often from installing nVidia driver from nVidia, not from Ubuntu repository. You have to reinstall into every new kernel if you install directly from nVidia with .run file.

That won't happen if you do this first:```
sudo apt install dkms
```. DKMS, Dynamic Kernel Module Support, will link a new kernel to the nVidia driver.

The **best** way to install nVidia drivers is this:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-410
```

Reboot, and you're all set.

This does assume that you have an nVidia card or chip.

---

