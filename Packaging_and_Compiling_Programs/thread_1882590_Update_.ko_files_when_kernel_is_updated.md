---
title: "Update .ko files when kernel is updated?"
date: 2011-11-17
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-11-17
Will a .ko compiled for, say, 2.6.32-35 work with 2.6*, 2.6.32*, or only with that exact version? 

In any case, what is the best way to go about keeping .ko files up to date when a new kernel is installed?

---

### Post by Bachstelze on 2011-11-17
The module will refuse to load by default. I think you can force it with modprobe -f, but then it's your luck whether it works or not. Better not take chances and recompile it against the new kernel. Look into DKMS, that's what is used in Ubuntu for packages that use kernel modules (like the nvidia drivers or VirtualBox).

---

### Post by djsephiroth on 2011-11-17
Thanks, I will!

---

