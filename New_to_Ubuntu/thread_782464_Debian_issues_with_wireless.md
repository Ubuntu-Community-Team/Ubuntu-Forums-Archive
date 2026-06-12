---
title: "Debian issues with wireless"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by hockeyfighter09 on 2008-05-05
I have a weird problem, When I install debian etch in virtualbox my wireless works perfectly with it.  So then I go and install it and get it all installed and discover my wireless now doesn't work at all.  Any ideas why this is happening?
Also I am running on a Dell XPS M1210, I cannot remember the command to type into terminal to show my Internals if anyone needs me to do that.

---

### Post by SunnyRabbiera on 2008-05-05
well the debian in virtualbox is probably leeching off the wireless in your ubuntu install.
Remember that debian does not come with the proprietary stuff that ubuntu does, especially etch.

---

### Post by hockeyfighter09 on 2008-05-05
Is there a way to get this working that doesnt require too much effort?  Its the only thing that isnt working for me, but I know these types of issues require some hard work and I am not up to it right now.  If there isnt that fine, I just want to know if theres a simple way to fix this or not.

---

### Post by Monicker on 2008-05-05
The only type of wireless devices which can be accessed directly from a VM are usb ones. So, as SunnyRabbiera stated, it would be relying on your host for its network connectivity.

Unless you happen to actually have a usb wireless device dedicated solely to the guest os in the vm.......

Debian does have non-free repositories, but they are certainly more strict than Ubuntu in what they will offer packages for.

---

### Post by Monicker on 2008-05-05
> **hockeyfighter09 said:**
> Is there a way to get this working that doesnt require too much effort?  Its the only thing that isnt working for me, but I know these types of issues require some hard work and I am not up to it right now.  If there isnt that fine, I just want to know if theres a simple way to fix this or not.

Hard to say without knowing which wireless device it is.  Do you know the chipset of the wireless adapter?

---

### Post by hockeyfighter09 on 2008-05-05
> **Monicker said:**
> Hard to say without knowing which wireless device it is.  Do you know the chipset of the wireless adapter?

I am not sure.  I know theres a command I can type into the terminal that shows me everything I have in this computer but I forgot it.

---

### Post by Monicker on 2008-05-05
lspci -v 

Though I am not sure if that information will show everything about your hardware if you run it from linux within a virtual machine.  Virtualization emulates hardware for the guest, and usually it is not the same as what the host machine has.

---

### Post by hockeyfighter09 on 2008-05-05
```
 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1020
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```
Thats what wireless card I have in my laptop

---

### Post by Monicker on 2008-05-05
Hrmm. Judging by some of the posts I have seen in the Networking & Wireless forum that chipset can be somewhat of a bear.  It supposed to be supported with the iwl3045 driver in Hardy Heron 8.04.

The most I can suggest for that card is to search and rummage through the previous threads about it.  I have not seen any definitive Howto guides for it yet.

---

### Post by hockeyfighter09 on 2008-05-05
> **Monicker said:**
> Hrmm. Judging by some of the posts I have seen in the Networking & Wireless forum that chipset can be somewhat of a bear.  It supposed to be supported with the iwl3045 driver in Hardy Heron 8.04.

The most I can suggest for that card is to search and rummage through the previous threads about it.  I have not seen any definitive Howto guides for it yet.

Aw man that sucks. Thanks so much for the info, guess I'll be sticking with Ubuntu for now.:)

---

### Post by hockeyfighter09 on 2008-05-05
Does anyone know if I download and install Debian Lenny if that will solve my problem or will I end up with the same result?

---

