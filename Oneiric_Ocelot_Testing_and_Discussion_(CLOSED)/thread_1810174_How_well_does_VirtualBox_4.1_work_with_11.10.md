---
title: "How well does VirtualBox 4.1 work with 11.10?"
date: 2011-07-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-07-22
With VirtualBox 4.1, comes full Windows Aero support. Finally.

But I'm holding of on installing because I'm not sure if it works correctly in 11.10.

Is anyone using VirtualBox in 11.10? Are there any problems that I should be aware of?

---

### Post by dj_palindrome on 2011-07-22
Let's put it this way. I have a Windows 7 *host,* and I run Oneiric as a g*uest *in both Vbox and VMware. My life with 11.11 is far from trouble-free, but when problems *do *arise, they surface in both virtualizations simultaneously, which sort of exonerates both hypervisors. They'd have to be in collusion to be having the *same* bugs.
 
One thing though. The "virtual" kernel seems to become more and more useless as more and more "core" drivers seem to be disappearing from it. On my system, vboxvideo has a dependency on drm which is most easily satisfied by just switching to the "generic" kernel, which has it, and ditching the "virtual" kernel, which doesn't. 
 
You may find the same situation obtains for sound-card drivers. At least this was the reason for no sound after Maverick in Vmware.
 
Like I said, I'm not the sharpest knife in the drawer.

---

### Post by PhantmKllr on 2011-07-22
I'm more interested in how well VirtualBox 4.1 works inside an Oneiric host.

I'm already aware of how much Windows sucks. :lolflag:

---

### Post by dino99 on 2011-07-23
its working smootly on my Oneiric i386, but i've installed some packages first:
-dkms
-virtualbox-dkms
-dh-modaliases

---

### Post by PhantmKllr on 2011-07-23
VirtualBox 4.1 installed in working well in Oneiric 64-bit. :D

---

