---
title: "how to get the old kernel version...."
date: 2007-03-19
forum: Programming Talk
---

### Post by Mateo on 2007-03-19
I'm trying to create a script that takes the pain out of uninstalling an old kernel version.  Instead of going into synaptic and having to uninstall the "linux-image-", "linux-headers-", "linux-restricted-modules-" and so forth, I should be able to do it with one script.

But how can I get the name of the previous kernel?  I know that uname -r will give me the current kernel... but the previous?

---

### Post by lloyd_b on 2007-03-20
> **Mateo said:**
> I'm trying to create a script that takes the pain out of uninstalling an old kernel version.  Instead of going into synaptic and having to uninstall the "linux-image-", "linux-headers-", "linux-restricted-modules-" and so forth, I should be able to do it with one script.

But how can I get the name of the previous kernel?  I know that uname -r will give me the current kernel... but the previous?

I see a few possibilities:

1.  Look in the directory "/lib/modules" - there should be one subdirectory here for each installed kernel. 

2.  Look in "/boot" for "vmlinuz..." files - there should be one for each installed kernel version.

3.  Parse the output from the "dpkg-query" command:
dpkg-query -l "linux-image*"
will get you a list of all installed linux-images.

Once you have a list of all installed kernels, you just need to identify which is the current version, and uninstall the rest.

Lloyd B.

---

