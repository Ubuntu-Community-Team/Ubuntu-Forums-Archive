---
title: "Gettting gcc"
date: 2004-12-20
forum: Packaging and Compiling Programs
---

### Post by Brian_X7 on 2004-12-20
I have installed ubuntu yesterday and it went pretty painless.  However, I need to compile a driver to get my usb wireless working on that machine.  I've already seen that gcc is not installed by default and the solutions I've seen mention using the apt-install mechanism.  But I can't use that since I don't have internet access on that machine yet.  How can I download the correct gcc packages?

Thanks,
Brian

---

### Post by az on 2004-12-20
sudo apt-get install build-essential


Or get it through synaptic.  It is on the cd.

---

### Post by Brian_X7 on 2004-12-20
Thanks, after I posted, I was able to figure that out on my very own .  Now I believe I need the kernel sources to compile this puppy.  Where would I find those?

Brian

---

### Post by az on 2004-12-20
You can use the kernel-headers, instead.

linux-headers-2.6-386

The kernel source package is called linux-source-2.6

---

