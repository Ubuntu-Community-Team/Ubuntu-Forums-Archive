---
title: "Compiling with other kernel (than the one in use)"
date: 2007-02-11
forum: Packaging and Compiling Programs
---

### Post by elektronaut on 2007-02-11
I know, the topic is a bit awkward, but I don't really know how to express this better. This is the problem: An automatic kernel update on a Dapper system made the ndiswrapper module, which was compiled from source, useless. I'm giving the user remote assistance and told her to choose the older kernel in the grub menu during startup, so now she can use the wireless connection again. I then edited the boot menu, so that the older kernel is default. So for now everything is working. But I would like to compile ndiswrapper again for the new kernel. As the user doesn't have the knowledge to do this, I would have to do it via ssh. But as described, there is only an internet connection possible if the old kernel is loaded. Is it somehow possible to tell make to compile for the newer kernel?

---

