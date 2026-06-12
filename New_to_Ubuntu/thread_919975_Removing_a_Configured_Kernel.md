---
title: "Removing a Configured Kernel"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Unanimated on 2008-09-14
I recently configured the rt2x00 kernel so I can get my Wi-Fi card to be a HostAP. When I was configuring it, I stupidly forgot to add support for my hard drive. So, now when I boot into it, it gives an error saying it can't get into my hard drive. How do I delete that kernel so I can reconfigure it and actually look at the options? Or, how do I add the kernel's features into my Ubuntu 8.04 kernel? I'm new-ish at this whole kernel compilation thing, simple, guided instructions would be really nice.

---

### Post by Sorivenul on 2008-09-14
As for removing the a current kernel compiled outside of the regularly accessible Ubuntu repos, I am not so familiar.  As for compiling, you may look the the [Master Kernel thread]("http://ubuntuforums.org/showthread.php?t=311158").  Or take a look at [KernelCheck]("http://kcheck.sourceforge.net/").

---

### Post by Marshal0505 on 2008-09-14
Boot into an older kernel,
I first remove the *.deb files in /usr/src and rename the /lib/modules/linux/*whateverversionname/kernel to kernel.old.
Proceed with "make xconfig', adjust your preferred settings and recompile your kernel.
After that its smooth sailing.

---

### Post by Unanimated on 2008-09-14
There are no .deb files in /usr/src.

---

