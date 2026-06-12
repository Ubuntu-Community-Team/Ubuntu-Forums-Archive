---
title: "CC version check faild Installing driver"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by tprzepiorka on 2008-10-31
Hi,
I upgraded my system to 8.10 and I have had some troubles with my graphics driver. I get an error when I boot that says there is something wrong with my configuration and all I can do is boot into low graphics mode. I then tried to install the two available drivers that are in the Hardare Drivers under Administration, but neither allowed me to use compiz. I wasn't able to detect my screens either (I usually use the NVIDIA utility to set up my two screens). So I read that it was best if I downloaded and installed the driver manually from nvidia's site. However I run into an error when I try to proceed with the installation:
> The CC version check failed:
The compiler used to compile the kernel (gcc 4.2) does not exactly match the current compiler (gcc 4.3). The linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel.
If you know what you are doing and want to ignore the gcc versin check, select "NO" to continue installation. Otherwise, select "Yes" to abort installation, set the cc enviroment variable to the name of the compiler used to compile your kernel, and restart installation. Abort now?

If I click "no" to ignore the warning it still doesn't work. I need to know how to set teh CC enviroment variable to the name of teh compiler used to compile my kernel and have no idea how.

---

### Post by aktiwers on 2008-10-31
i had that error too. I had to uninstall gcc 4.3 and install gcc 4.2.

Other than that, have you tried Envy installer?

---

