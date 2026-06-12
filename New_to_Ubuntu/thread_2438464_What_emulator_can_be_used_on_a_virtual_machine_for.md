---
title: "What emulator can be used on a virtual machine for app development"
date: 2020-03-12
forum: New to Ubuntu
---

### Post by booshlub on 2020-03-12
So I installed Ubuntu on Vmware to run on my Windows pc to do React native development because of issues developing with windows. So I was searching online for the best emulators for Ubuntu and a lot of sites suggested Genymotion, but after unsuccessfully installing it on my virtual machine I found out it cant run on virtual machines. So I was wondering if anyone has any suggestions for a good free emulator I can run to test my apps as I'm developing with Ubuntu on Vmware?
Thanks!

---

### Post by TheFu on 2020-03-13
qemu can emulate almost any HW.  But because it is all done via software the emulation will be slow.

BTW, VMware makes 6+ different virtual machine solutions, so saying "VMware" doesn't really tell us anything.

If your target is ReactOS, why not just run that directly in a VM? I'm confused.

---

