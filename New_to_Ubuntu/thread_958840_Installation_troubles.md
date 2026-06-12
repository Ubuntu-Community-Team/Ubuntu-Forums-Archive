---
title: "Installation troubles"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Moolatte on 2008-10-25
I can't partition my hard drive from the live installation disk... I can't proceed in the installation either without selecting my hard drive and or a partition. (Which I can't do.)

I'd love to try Ubuntu, to see if it's any better at processing video than Debian, and I've tried LinuxMint, but that has trouble processing web pages correctly, so... help?

Yes, I've tried at both other forums, but they both offered little support, and told me I might want to try another distribution.

I've tried Xubuntu, and loved it. But I updated it, and it CRASHED my hard drive. After that, Xubuntu wouldn't install again.

I'd also like so safety tips uninstalling Debian. I've tried overwriting it before, and it ended up disastrous. I had to format my hard drive cause the GRUB loader didn't like that I overwrote it.

Yes, I do have Windows on another partition.(Mainly because most programs I NEED are for Windows only.)

---

### Post by drowner on 2008-10-25
> **Moolatte said:**
> I can't partition my hard drive from the live installation disk... I can't proceed in the installation either without selecting my hard drive and or a partition. (Which I can't do.)

I'd love to try Ubuntu, to see if it's any better at processing video than Debian, and I've tried LinuxMint, but that has trouble processing web pages correctly, so... help?

Yes, I've tried at both other forums, but they both offered little support, and told me I might want to try another distribution.

I've tried Xubuntu, and loved it. But I updated it, and it CRASHED my hard drive. After that, Xubuntu wouldn't install again.

I'd also like so safety tips uninstalling Debian. I've tried overwriting it before, and it ended up disastrous. I had to format my hard drive cause the GRUB loader didn't like that I overwrote it.

Yes, I do have Windows on another partition.(Mainly because most programs I NEED are for Windows only.)

I have also had problems doing an over-write installation.

It may be worth deleting some partitions (after backing up crucial data) before you start.

The reason you probably had trouble with your grub before, is that its files were kept on the debian installation you deleted, or that when you changed the partitions it couldn't what it was looking for. This doesn't require a reformat - in most cases you can just reinstall GRUB and it can be setup to use your new partitions.

---

### Post by Helios1276 on 2008-10-25
Partition Magic might help your situation.

---

### Post by ssk2006s on 2008-10-25
I had a similar problem installing 64 bit hardy.  Are you using a SATA hard drive?

---

### Post by Moolatte on 2008-10-26
> **ssk2006s said:**
> I had a similar problem installing 64 bit hardy.  Are you using a SATA hard drive?

I don't know if I do, nor am I using a 64 bit computer.

Alrighty... So I got GParted to work. And I'm using Debian at the moment. My next question that I will need help with...

How do I uninstall Debian, and not screw up the GRUB? My entire hard drive is apparently being used, and I can't partition anymore. I don't want to format the Debian partitions for the reason in the first post.

*is complete n00b*

---

