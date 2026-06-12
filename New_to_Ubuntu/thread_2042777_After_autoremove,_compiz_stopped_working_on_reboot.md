---
title: "After autoremove, compiz stopped working on reboot"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by Cincinnatux on 2012-08-15
Hey, all.  I am running 64-bit Precise Pangolin/Unity, and earlier today I used the "autoremove" command to clean things up a bit.  Turns out I should not have done that.  Apparently, autoremove occasionally removes a bit too much, and I think that happened in my case today.  Upon rebooting, compiz failed to launch, as did unity.  After googling around for some help, I found a suggestion at the LinuxMint forum that solved my problem.

Anyhow, here's what I did:

```
sudo aptitude safe-upgrade
```

It installed about 150 MB of software.  Then I rebooted and everything was back to normal.  Sorry I didn't take the time to document the specifics, but I wanted to share at least in general terms what worked for me.

---

