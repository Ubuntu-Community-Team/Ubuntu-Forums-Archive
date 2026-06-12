---
title: "Kernel build: Prevent build of wireless completely"
date: 2017-05-07
forum: Programming Talk
---

### Post by notrightaway on 2017-05-07
Hi guys. I am using the guide here to try and build a smaller kernel. 
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

I made a few config changes as a basic test and I can build a kernel successfully. However it seems to build quite a lot of features that I disabled using menuconfig. I don't see any errors in the stages after menuconfig but something seems to be changing CONFIG_WIRELESS back to "Y" before the build starts.

Any ideas? Is there some sort of override in another file?

I really don't need any of the wireless support - this is an HTPC without wireless hardware.

---

