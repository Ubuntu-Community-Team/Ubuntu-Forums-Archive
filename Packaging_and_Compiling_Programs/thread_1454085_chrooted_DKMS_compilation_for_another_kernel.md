---
title: "chrooted DKMS compilation for another kernel"
date: 2010-04-14
forum: Packaging and Compiling Programs
---

### Post by benj.david on 2010-04-14
Hi all,
I'm building a custom Ubuntu. For this, I build a minimal OS using debootstrap and I chroot in this build to install some additional packages.

I need to install packages that use DKMS such as nvidia drivers or virtuabox additional tools.
The problem is those packages can't be installed properly as the kernel running on my computer is not the one installed by debootstrap.

Does somebody know how to tell DKMS to compile using the kernel headers installed in the chroot environnement, and not the host system one ?

Thank you in advance,
ben

---

### Post by SevenMachines on 2010-04-14
dkms assumes the running kernel and architecture if you dont specify it, have you tried passing the -k <kernel> option to dkms?

---

### Post by ppetraki on 2010-06-25
That more depends on the dkms package you're trying to build
than anything else. Since alot of makefile aren't written with
chroot's in mind so they often use uname -r to grab the kernel
version to build against. This should help.

[https://wiki.ubuntu.com/KernelTeam/BuildKernelWithChroot](https://wiki.ubuntu.com/KernelTeam/BuildKernelWithChroot)

There's a create_chroot.sh script that's pretty good which you can download from there. There's a bug in the config file it makes for you though. Make sure you add 'type=directory' to the schroot config. Moving on, like the other poster said, the -k argument is all you need, this presumes that /lib/modules/xxxxx/build exists and is pointing to the linux headers installed in /usr/src.

---

