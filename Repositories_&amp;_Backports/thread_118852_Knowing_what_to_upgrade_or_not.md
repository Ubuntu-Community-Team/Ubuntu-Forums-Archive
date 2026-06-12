---
title: "Knowing what to upgrade or not"
date: 2006-01-17
forum: Repositories &amp; Backports
---

### Post by seakiwi on 2006-01-17
Hi 

I'm slowly getting my head around linux and Ubuntu and synaptic/Adept etc but the problem I have is knowing which updates I really need and which ones to ignore. Some are obvious, but many are not. For instance, there is currently a linux kernel update mentioned - actually several references to the linux kernel, and even though I've read the details about each one I still have no idea whether I need them, and if I do, which ones I need. 

I prefer not to blindly update everything that comes along - I never did in Windows either. I like to know that anything I install is something I actually need, especially when it comes to security updates as opposed to application upgrades.

Is there a way to sort the wheat from the chaff? :???:

---

### Post by rjwood on 2006-01-17
The maintainers are giving you the wheat. I certainly undertand your concerns.Trust the people in Ubuntu---its ok... Microsoft has left you scared--take a chance and let it update---you'll be glad you did!!!;)

---

### Post by matthew on 2006-01-17
Just to echo rjwood. The updates you see are good ones, primarily security, stability, or on occasion feature related (if you have backports enabled).

---

### Post by seakiwi on 2006-01-17
[QUOTE=rjwood]The maintainers are giving you the wheat. I certainly undertand your concerns.Trust the people in Ubuntu---its ok... Microsoft has left you scared--take a chance and let it update---you'll be glad you did!!!;)[/QUOTE]

Well I forgot to mention that I'm on a dial up connection, so it's not practical to update absolutely **everything **

Having just installed Ubuntu, there are heaps of updates sitting there waiting - I need some way to figure out which ones are critical and which ones can wait weeks ;)

As for the kernel ones. Which ones should I apply and are there any risks?

As an example there is one listed there now as: 

[I]Complete Linux kernel on 386.
This package will always depend on the latest complete Linux kernel available
for 386.[/I]

and
[I]
Linux kernel image on 386.
This package will always depend on the latest kernel image available
for 386.[/I]

Not to mention:
[I]
Linux kernel image for version 2.6.12 on PPro/Celeron/PII/PIII/PIV.
This package contains the Linux kernel image for version 2.6.12 on
 Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV,
the corresponding System.map file, and the modules built by the packager.
It also contains scripts that try to ensure that the system is not left in
a unbootable state after an update.

If you wish to update a bootdisk, or to use a bootloader to make
installing and using the image easier, we suggest you install the latest
fdutils (for formatting a floppy to be used as boot disk), and LILO, for a
powerful bootloader. Of course, both these are optional.

Kernel image packages are generally produced using kernel-package,
and it is suggested that you install that package if you wish to
create a custom kernel from the sources.[/I]

See what I mean? I have absolutely no idea which, if any, of those I should install, and those are just the tip of the iceberg. I'm not stupid ... I'll learn all this stuff eventually, but in the meantime it would be nice to have some kind of guidelines on how to pick and choose these things, especially the base system things like these. Messing about making mistakes with kernels doesn't sound like a good idea to me :???:

---

