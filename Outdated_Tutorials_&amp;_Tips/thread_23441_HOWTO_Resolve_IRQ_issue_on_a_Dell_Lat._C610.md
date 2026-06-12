---
title: "HOWTO: Resolve IRQ issue on a Dell Lat. C610"
date: 2005-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by und3rdog on 2005-04-01
Well, I recently aquired a used Dell latitude to doink around with.  After installing the core of Ubuntu I realized that niether my sound nor my ip2200bg intel wireless card was working.

It turns out there is an issue with some IRQ overlap when using Ubuntu in a default.  You have two options to resolve this.

1.> Disable support for you parallel port in bios.  This works great, only you have no parallel port now....

2.> boot with the kernel option (acpi = noirq)  and while your at add (nolapic noapic) as well.  The way I find that works is to edit (/boot/grub/menu.lst) find your kernel line and add those parameters. 
***WARNING***  ](*,) - Don't be susprised if synaptic wipes out these settings it's done this to me twice already.  I added those option to singlely comment section of menu.lst and now it seems to retain my settings on upgrades.  


Use this at your own risk.  Remember menu.lst tells grub how to load the OS, you break it you bought it.

Peace,
-Luke

---

