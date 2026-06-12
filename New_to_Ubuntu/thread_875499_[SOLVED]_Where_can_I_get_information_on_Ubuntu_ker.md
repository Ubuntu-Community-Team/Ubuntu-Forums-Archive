---
title: "[SOLVED] Where can I get information on Ubuntu kernel upgrades?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by durundal on 2008-07-30
I have two wireless cards and every time I update the kernel one or the other breaks.  On the last upgrade both of them are now broken.  

My current version is 2.6.24-20-generic and I believe I've installed the most recent proposed updates by accident somehow, since they no longer show up in my update manager.

Where do I find information about the kernels and how to revert back to older ones?

---

### Post by InfinityCircuit on 2008-07-30
Old kernels aren't removed from your system when you upgrade, so you should just be able to boot into an older kernel.

---

### Post by voteforpedro36 on 2008-07-30
> **InfinityCircuit said:**
> Old kernels aren't removed from your system when you upgrade, so you should just be able to boot into an older kernel.


...by holding ESC during boot (when you see GRUB, press ESC to go to menu).

---

### Post by drs305 on 2008-07-30
Install Startup-Manager, then System > Admin > StartUp-Manager > Boot Options and pick any kernel still on your system as the default OS.

```
sudo aptitude install startupmanager
```

See the link in my sig for a tutorial (not that you'd need it for this).

---

### Post by durundal on 2008-07-30
Thanks for your quick responses guys.

Problem solved!

---

