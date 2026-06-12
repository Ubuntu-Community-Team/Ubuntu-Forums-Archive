---
title: "Running Ubuntu 12.04 on VMware player: Icon issues"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by ari8792 on 2013-06-18
Hello all, 

I'm completely new at this so bear with me.
I've just installed VMware player and downloaded and am installing/creating for the 3rd time a VM with Ubuntu 12.04 LTS 32 bit (tried 64 bit when after three attempts of uninstalling and reinstalling did not work and still did not work). The issue: each time I'm finished downloading and login the completed VM the icons appear to be black. The background is visible and the icons are operable but I cannot see them.

Solutions I have found online:
- installing a NVIDIA driver (I'm not quite sure which is appropriate to install on my machine)
- Messing with the BIOS (enabling virtualization, haven't tried because I don't have the 64-bit error message)

Any suggestions?

---

### Post by ari8792 on 2013-06-19
> **ari8792 said:**
> Hello all, 

I'm completely new at this so bear with me.
I've just installed VMware player and downloaded and am installing/creating for the 3rd time a VM with Ubuntu 12.04 LTS 32 bit (tried 64 bit when after three attempts of uninstalling and reinstalling did not work and still did not work). The issue: each time I'm finished downloading and login the completed VM the icons appear to be black. The background is visible and the icons are operable but I cannot see them.

Solutions I have found online:
- installing a NVIDIA driver (I'm not quite sure which is appropriate to install on my machine)
- Messing with the BIOS (enabling virtualization, haven't tried because I don't have the 64-bit error message)

Any suggestions?

So I figured it out without have to use the above solutions by doing the following:

Once Ubuntu is installed on VMware player and the VM rebooted, **power off the VM.** Then disable 3D graphics by going to **player > Manage> Virtual Machine setting> Display> and uncheck accelerate 3D graphics**

Good luck!

---

