---
title: "module compiled on Fiesty Desktop (2.6.20-16-generic)"
date: 2007-06-07
forum: Packaging and Compiling Programs
---

### Post by PFilter on 2007-06-07
Hello!
I have an Ubuntu Fiesty desktop install that I use for normal daily stuff. I constantly keep it up-to-date with the update manager. 
I also set up the development environment for compiling the OSE version of VirtualBox. That included manually asking for things like gcc and g++ (sudo apt-get install g++, for example).

It all compiles and runs fine on this Fiesty.

So, onward with my project. I then installed a Fiesty server (2.6.20-16-server kernel). I would have compiled virutalbox there, but the development environment was not set up, and much more was missing than was the case on the desktop build. My plan was to move the binaries and kernel module to the server from the desktop and run it.

But, after copying the vboxdrv.ko module to the server machine, an insmod or modprobe will return the 'Invalid module format' error usually ascribed to a mismatch between the version of gcc used to compile the module and the version used to compile the kernel. The version of gcc is 4.1.2 on both PCs, so I can only guess that the 2.6.20-16-server kernel and the 2.6.20-16-generic kernel from the repositories were compiled under different versions of gcc.

So, unless someone has insight into how to better fix this, I looks like I will either need to change my gcc to the same version used for the 2.6.20-16-server kernel and recompile virtualbox, or recompile 2.6.20-16-server using the same gcc I used to compile virtualbox.

Simply setting up the dev environment on the server seems like it will not work: it's gcc is the same as my desktop and therefor must be different than the version used to compile the running kernel.

linux-headers-2.6.20-16-server are already installed.

modinfo /lib/modules/2.6.20-16-server/kernel/drivers/net/3c509.ko (as example from Server):
vermagic: 2.6.20-16-server SMP mod-unload 686

modinfo /lib/modules/2.6.20-16-server/misc/vboxdrv.ko (for the one I compiled on Desktop)
vermagic: 2.6.20-16-generic SMP mod-unload 586

Can anyone help out here? Need more info? I'm already on the right track?

Thanks in advance,

PFilter

---

### Post by PFilter on 2007-06-08
I am such a noob.

apt-get build-essential
and I had to add
apt-get libhal-dev which virtualbox requires.
Then it ./configured quite nicely right on the server box.
Module loaded fine.

I am such a noob. Did I say that?




> **PFilter said:**
> Hello!
I have an Ubuntu Fiesty desktop install that I use for normal daily stuff. I constantly keep it up-to-date with the update manager. 
I also set up the development environment for compiling the OSE version of VirtualBox. That included manually asking for things like gcc and g++ (sudo apt-get install g++, for example).

It all compiles and runs fine on this Fiesty.

So, onward with my project. I then installed a Fiesty server (2.6.20-16-server kernel). I would have compiled virutalbox there, but the development environment was not set up, and much more was missing than was the case on the desktop build. My plan was to move the binaries and kernel module to the server from the desktop and run it.

But, after copying the vboxdrv.ko module to the server machine, an insmod or modprobe will return the 'Invalid module format' error usually ascribed to a mismatch between the version of gcc used to compile the module and the version used to compile the kernel. The version of gcc is 4.1.2 on both PCs, so I can only guess that the 2.6.20-16-server kernel and the 2.6.20-16-generic kernel from the repositories were compiled under different versions of gcc.

So, unless someone has insight into how to better fix this, I looks like I will either need to change my gcc to the same version used for the 2.6.20-16-server kernel and recompile virtualbox, or recompile 2.6.20-16-server using the same gcc I used to compile virtualbox.

Simply setting up the dev environment on the server seems like it will not work: it's gcc is the same as my desktop and therefor must be different than the version used to compile the running kernel.

linux-headers-2.6.20-16-server are already installed.

modinfo /lib/modules/2.6.20-16-server/kernel/drivers/net/3c509.ko (as example from Server):
vermagic: 2.6.20-16-server SMP mod-unload 686

modinfo /lib/modules/2.6.20-16-server/misc/vboxdrv.ko (for the one I compiled on Desktop)
vermagic: 2.6.20-16-generic SMP mod-unload 586

Can anyone help out here? Need more info? I'm already on the right track?

Thanks in advance,

PFilter

---

