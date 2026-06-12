---
title: "VLinux: Wubi, VMWare or VirtualBox?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Armandoban on 2008-10-06
Hello all!

I've been running dual-boot Ubuntu for a while and I want to try running a virtual installation inside Windows. What's the best method for getting the most functional installation?

My question comes from some confusion, so here's what I *think *I know.. I've read that Wubi is not a virtual machine, but a loopmounted device, meaning Wubi Ubuntu is actually a Windows application running Linux. So is it a form of emulation? I'm guessing maybe this is not as functional as using VMWare or VirtualBox and the Intel-VT features. And Wubi doesn't support hibernation? Meaning hibernating just the Linux window or the whole Windows computer?

I've also read in a few places that the free VMWare player doesn't utilize virtualization technology in hardware. Only the VMWare Workstation and Fusion access those functions. I couldn't find a specific answer on the VMWare site. Other than that I guess I'm just seeking a good idea of advantages/disadvantages in all these things.

Thanks!
Ab

---

### Post by SamNSane on 2008-10-06
Hi,

I'm kind of confused by your reference to "most functional installation" because it seems as though you're going in the opposite direction from functionality -- if you're talking about the functionality of Ubuntu.

In other words, it seems to me that the only more functional installation of Ubuntu than the one you have now is to just boot it by itself on its own system instead of dual booting with Windows.

Using virtualization (VMWare) or a loopback system (like Wubi) is going to get you a less functional installation of Ubuntu than the one you have now. It will be slower (maybe only a little), and it won't have the same relationship with the system hardware, which has to be emulated in some fashion for the virtual environment. It will also be entirely dependent upon the health of the host OS. If the host OS goes toes up, so does your Ubuntu installation. And even fixing the Ubuntu installation itself -- if you're looking to learn about such things as fixes for boot issues -- will be different in that environment than it is in a standard installation.

Since Wubi resides within the Windows partition as a set of files, I think that hibernating Wubi is probably not a great idea. If you hibernate it, and then do something (like defragging maybe?) in the Windows partition, you've probably whacked Wubi. But that's a guess. I haven't really looked at in for a couple of years, and even then only for a few minutes.

There are certainly some good reasons for using a VM, like being able to run both operating systems simultaneously. Is that what you're shooting for?

---

### Post by Armandoban on 2008-10-26
> **SamNSane said:**
> ..even fixing the Ubuntu installation itself -- if you're looking to learn about such things as fixes for boot issues -- will be different in that environment than it is in a standard installation... 
..Since Wubi resides within the Windows partition as a set of files, I think that hibernating Wubi is probably not a great idea...
There are certainly some good reasons for using a VM, like being able to run both operating systems simultaneously. Is that what you're shooting for?

Yes I was looking to learn about the standards, play with multiple kernels, breaking and fixing and such.. Just thought it would be a nice change to be able to keep working on other things while the broken OS gets tweaked and repaired instead of waiting for reboots. Also didn't want to risk breaking my dual-boot until I was at least familiar with the basic Ubuntu system (IE when you bust the graphics driver you have to be able to "visualize" where the dialog buttons are :)).

Took your advice and didn't do Wubi. I ended up using VirtualBox. I was annoyed by the endless registrations and the huge footprint of VMWare Server, and couldn't find any free "blanks" or complete images for VMWare Player preconfigured to match my hardware. Since you can't configure a VMWare Player image after creating it (I don't think?) if things like virtualization aren't already enabled you can't turn them on.

And based on what I found even though the virtual version couldn't access the 3D card and was missing most of the "fun" stuff, I've cleared a partition and started downloading 8.10 rc!

---

### Post by The Cog on 2008-10-26
My understanding is that wubi is a complete Linux installation that uses a file on the Windows disk rather that a separate partition. It becomes a boot option under the Windows bootloader and apart from the unusual disk arrangement is a full Linux - no Windows OS underneath.

---

