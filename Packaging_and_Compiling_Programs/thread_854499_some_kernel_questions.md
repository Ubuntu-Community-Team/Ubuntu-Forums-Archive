---
title: "some kernel questions"
date: 2008-07-09
forum: Packaging and Compiling Programs
---

### Post by Maccabee on 2008-07-09
I ve some basic questions

1. Can i compile a linux kernel 2.6.9 in a 2.6.24 Ubuntu hardy??
2..If possible ,Can i boot with that kernel into my current OS
3.If 1 not possible then wat is the most appropriate solution without changing my current OS??

I need to use a kernel 2.6.9 since the package rtlinux has only patches upto tat version

---

### Post by cwii on 2008-07-10
It's really a bad idea to go back kernels.
You're leaving yourself open to security holes.

---

### Post by colo on 2008-07-10
No, you probably won't be able to boot up your system with Linux 2.6.9, because the way the Kernel and udev interact may have already changed enough for it not to work relibaly for this already anvient kernel release.

There are rt-pacthed kernel images provided in the Ubuntu repositories: [http://packages.ubuntu.com/hardy/linux-image-2.6.24-16-rt](http://packages.ubuntu.com/hardy/linux-image-2.6.24-16-rt)

---

