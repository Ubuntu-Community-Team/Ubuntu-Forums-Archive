---
title: "[SOLVED] Removing Old/Out Dated Kernels"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by takuhii on 2008-05-27
I have about 16 kernels installed on my PC how do I go about cleaning them up. I'm using Hardy Heron (8.04), I'd like to just keep one of two in case of errors in any updated kernels going forwards...

---

### Post by drs305 on 2008-05-27
> **takuhii said:**
> I have about 16 kernels installed on my PC how do I go about cleaning them up. I'm using Hardy Heron (8.04), I'd like to just keep one of two in case of errors in any updated kernels going forwards...

You can uninstall them via synaptic and it will update grub as well. It is recommended to keep at least the 2 most recent ones.

---

### Post by Cypher on 2008-05-27
You can safely remove the older kernels with
```

sudo apt-get autoremove linux-image-<version>-generic

```
Where <version> would be something like 2.6.22-14.52, and so on.

---

### Post by wdaniels on 2008-05-27
In Synaptic search on package name for linux-image, there you can select to remove all the kernels you no longer want to keep.

---

### Post by Scooby Doo on 2008-05-27
How can I find out which versions I have installed?

---

### Post by Cypher on 2008-05-27
```

dpkg -l | grep linux-image

```

---

### Post by Nepherte on 2008-05-27
Search for linux-headers in synaptic.

---

### Post by drs305 on 2008-05-27
> **Scooby Doo said:**
> How can I find out which versions I have installed?

Those that are installed (used and not used) will all have the green check box in synaptic. Look for linux-image

---

### Post by Scooby Doo on 2008-05-27
Thanks. I have 3 installed so I think I'll leave it for now.

---

### Post by kansasnoob on 2008-05-27
Some alternatives to removal:

[http://ubuntuforums.org/showthread.php?t=808132](http://ubuntuforums.org/showthread.php?t=808132)

---

