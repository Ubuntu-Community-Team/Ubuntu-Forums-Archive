---
title: "No Unity in 11.10 64-bit under OS X VMware Fusion 4"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by barnsleyboy on 2012-01-29
I just installed 11.10 64-bit using VMware Fusion 4.1.0 under OS X 10.7.2, on a Mac Pro with a 4-core Xeon. The VM boots to a command line login that works fine, but I have no idea how to get to the Unity GUI, or whether there is some issue preventing it loading. No previous Ubuntu experience!

---

### Post by mcduck on 2012-01-29
Have you installed the WMvare Tools on the guest operating system? You'll need to do that to get graphics acceleration working.

...although you should get at least into the login screen and Unity 2D even without accelerated graphics, so there might be some other problem involved. But if you are lucky installing WMvare Tools might still be enough to get everything working.

---

### Post by barnsleyboy on 2012-01-30
Thanks, but VMware tools downloaded and installed without obvious error, so I don't think that's my problem.

---

### Post by lechien73 on 2012-01-30
Did you install the Ubuntu Server edition, or Desktop? The Server edition doesn't install the GUI as standard.

---

