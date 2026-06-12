---
title: "Using Compiz Settings Manager"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by meweedman on 2011-11-29
I'm having trouble with CCSM in 11.10, running in VirtualBox. None of the settings I try to change in CCSM seem to have any effect. For example, I tried to set the launcher to never autohide, but nothing changed. Same with every other setting. Unity itself is running fine. I have a feeling I'm missing something simple, but I can't find anyone else with this problem. Any ideas?

---

### Post by mikewhatever on 2011-11-30
Make sure you actually use Compiz and not Metacity. Since Ubuntu runs in VirtualBox, it's likely that either Unity2d gets loaded, and it doesn't run Compiz.

---

### Post by lolpenguin on 2011-11-30
You are probably changing settings for Unity, while running Unity 2D, since you mentioned Virtualbox. Install guest additions to use the full interface. (You can do this by installing the packages ```
virtualbox-guest-dkms virtualbox-guest-x11 virtualbox-guest-utils
```
or by running the Guest Additions disc image installer.

---

### Post by Jacobonbuntu on 2011-11-30
> **mikewhatever said:**
> Make sure you actually use Compiz and not Metacity. Since Ubuntu runs in VirtualBox, it's likely that either Unity2d gets loaded, and it doesn't run Compiz.

+1!
even if I install guest additions (I have an extra Oneiric in vbox to do some experiments), it runs unity 2d...
....the same (kind of) issue I have running W7 in virtual box, where the graphic capacities "cannot be determined". My graphics card should be sufficient to do well in virtualbox, but I think it is one of the issues running a virtual machine.

---

