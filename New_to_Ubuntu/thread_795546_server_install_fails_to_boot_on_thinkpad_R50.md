---
title: "server install fails to boot on thinkpad R50"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by fhqwhgad on 2008-05-15
Hi,
I decided to install an ubuntu-server on my old thinkpad R50.
After the install it tries to boot for the very first time and it gives me: 
Starting up ...
This kernel requires the following features not present on the CPU:
0:6
Unable to boot - please use a kernel appropriate for your CPU.

What is the problem here? Is it something in my install?
I did use the x86 version of 8.04 LTS Server Edition. It's a Centrino CPU, so i believe it is 32bit, but even if the CPU was 64bit, it should still be able to run the x86, right?

Anyone know what to do?

---

### Post by spiderbatdad on 2008-05-15
It may be possible to set cpu usage in the BIOS under the power option. Or it may be simply a matter of instructing the kernel with some boot parameters. From the boot options screen (press esc as the system loads, if your boot options are hidden) at start up, press F6, and edit the kernel line by deleting anything after 'ro' at the end of the line. Add 'lapic pci=routeirq' So it looks like:```
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=xxxxx(some #'s) ro lapic pci=routeirq
```
and boot.

---

