---
title: "Crossdev for Ubuntu?"
date: 2009-10-24
forum: Packaging and Compiling Programs
---

### Post by mikeym on 2009-10-24
Hi,

I'm trying to setup my Ubuntu desktop to help my gentoo laptop compile using distcc.

I'm almost through their guide but it says you have to setup a  cross-toolchain on my machine for the architecture of my laptop. Gentoo has a tool for this *crossdev* is there one for Ubuntu?

---

### Post by mikeym on 2009-10-25
Hmmm.... not found one, but I've found [a guide]("http://www.sable.mcgill.ca/~dbelan2/crossdev/crossdev-powerpc-i686.html") based on the approach of crossdev.

But I'm still stuck. I get as far as [installing the kernel-headers]("http://www.sable.mcgill.ca/~dbelan2/crossdev/crossdev-powerpc-i686.html#doc_chap4_sect6") (which is the first thing I need to compile on my Ubuntu machine to allow it to compile for my PowerPC) and I get an error about not having the PowerPc version of gcc. 

```
make: powerpc-unknown-linux-gnu-gcc: Command not found
```

Which is not right as this is the program I eventually hoping to compile!

Has anyone any ideas?

(**[COLOR="Red"]edit[/COLOR]**) This is the actuall line it fails on:

```
make ARCH=ppc CROSS_COMPILE=powerpc-unknown-linux-gnu- mrproper
```

Well almost :) I found that it complains if I use the line above:

```
arch/ppc/Makefile: No such file or directory
```

so I chaecked the *arch* folder and found that there was a *powerpc* folder so I tried:

```
make ARCH=powerpc CROSS_COMPILE=powerpc-unknown-linux-gnu- mrproper
```

Which is where I get the error.

---

### Post by mikeym on 2009-10-26
Well I gave up on the guide, but I had an idea. I've been working on installing gentoo on my AMD64 machine which I want to use as a distcc client so I used the gentoo cross development tool to compile a toolchain for the AMD64 machine.

[COLOR="Red"]**Is it possible then just to copy the toolchain from my gentoo partition to my ubuntu partition? **[/COLOR]

If it is where do I need to put them for distcc to use them? And do I need to link them?

---

