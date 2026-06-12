---
title: "Live USB recovery with chroot"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by prad1 on 2014-02-25
I am using ubuntu 12.04.3 ( LTS - raring stack ) and had updated the kernel and xorg from the quantal one. Couple of weeks ago, while cleaning my computer of the old kernels etc... I saw some files under residual config section in Synaptic Package manager like xorg-lts-quantal, mesa etc... don't remember the exact names, but all versions were the quantal ones. Anyway, I selected them all and completely removed. Few minutes later, unity crashed and I could'nt restart it. So I logged out, but came up against a black screen. Upon restarting, after the ubuntu splash screen, it says

Unable to write bytes: broken pipe

So, I figure I ve messed up the graphics stack somehow. I want to try to repair it and read about chroot. I also read the saucy stack has been released. Now if I do a chroot from a live usb and then do apt-get the new stack, that should work, right?
Or is it better to just reinstall?
Any help given would be appreciated.

---

### Post by jimmyh1972 on 2014-02-25
My advise to you, just re install a fresh copy.
it's always shorter and much more effective than to try fixing an-almost-dead-machine.

---

### Post by zvacet on 2014-02-25
Boot in recovery mode and type

```
apt-get install xorg
```

See if that help.

---

### Post by prad1 on 2014-02-25
> **zvacet said:**
> Boot in recovery mode and type

```
apt-get install xorg
```

See if that help.

Well, that worked.
Just booted in recovery mode & installed the saucy stack.
Thanks a lot. I guess I should mark this thread as solved.

---

