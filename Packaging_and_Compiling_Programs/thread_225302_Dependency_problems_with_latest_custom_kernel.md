---
title: "Dependency problems with latest custom kernel"
date: 2006-07-29
forum: Packaging and Compiling Programs
---

### Post by Farenji on 2006-07-29
I'm trying to compile the latest kernel for ubuntu. But I experience some problems. I hope anyone can shed some light on this.

First of all, I downloaded the kernel source using apt. On packages.ubuntu.org it said it was the same version as the stock prebuilt kernel (2.6.15-26) but when I unpacked the sources, I saw it was a older version (2.6.15.7). What's up with that?

Then I tried downloading the latest ubuntu kernel source (2.6.17-5) using git and this page: [https://wiki.kubuntu.org/KernelGitGuide](https://wiki.kubuntu.org/KernelGitGuide). I configured the kernel and followed [https://wiki.kubuntu.org/KernelCustomBuild](https://wiki.kubuntu.org/KernelCustomBuild) to create the .deb files. But when I try to install them I get dependency problems: module-init-tools is not the correct version. I need the version that ships with edgy but when I try to install that version using a .deb, other dependency problems turn up, fe I also have to upgrade libc6. I surely don't want that so I went back to the old situation.

So my questions: how to create a custom kernel using the same version as the Ubuntu stock kernel, or newer, while avoiding dependency hell...

Any help is appreciated!

---

### Post by Farenji on 2006-07-30
Ehm... anyone?

---

### Post by mlind on 2006-07-31
> **Farenji said:**
> 
So my questions: how to create a custom kernel using the same version as the Ubuntu stock kernel, or newer, while avoiding dependency hell...

Any help is appreciated!

```

sudo aptitude install linux-source-2.6.15

```

Remeber to make oldconfig target. use make-kpkg (from kernel-package) to build Debian kernel package from the kernel source.

---

### Post by adamkane on 2006-07-31
There is no benefit to running the latest kernel. 

Ubuntu ships with a safe 386 kernel and kernel-headers. To improve performance, all you need to do is install the 686 or k7 kernel and headers.

Intel Pentium (not Pro or 486):
```

sudo apt-get install linux-686 linux-headers-686

```

AMD K Series (Duron, Athlon, Sempron):
```

sudo apt-get install linux-k7 linux-headers-k7

```

---

### Post by Farenji on 2006-07-31
I'm confused about the difference in version number, the pre built ubuntu kernel is 2.6.15-26 and the kernel compiled from source is 2.6.15.7-ubuntu1 according to uname -a, it seems that one is a lot older or is it something in the versioning system I don't get?

Also does anyone know how to get the ubuntu splash image while booting, with my custom kernel the screen just goes blank until X starts. I compiled it with "make-kpkg --initrd --config menuconfig kernel_image" and assumed that also created the splash image but apparently it doesn't.

---

