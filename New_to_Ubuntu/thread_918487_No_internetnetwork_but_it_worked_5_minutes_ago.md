---
title: "No internet/network but it worked 5 minutes ago?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by shud on 2008-09-13
Cross posting this from the network forum:

Hey guys -

Pretty new to Linux and Ubuntu in general.

I wanted to throw a bunch of my drives onto my Ubuntu box, so I plugged them in, turned it on, and it mounted them no problem (all NTFS).

Now, to do this on my fairly new mobo, I had to throw in a PCI SATA/IDE card since my mobo only has one IDE port.

At some point I noticed that I couldn't get any internet connection. I'm getting an IP and the right subnet, gateway, and Comcast DNS servers from my router.

Somewhat funny, my VMware machines all have internet access!

Is this some kind of IRQ conflict with the card? 

EDIT: Update...I can ping the gateway (192.168.1.1) without any issue, but I can't ping any other computers on the network. I'm so lost.

How can I paste in my ifconfig and LSPCI from Ubuntu if I have no network on that box? :confused: I have a Windows workstation running in VMWare that gets internet just fine if I could figure out how to paste information into that.

---

### Post by doas777 on 2008-09-13
can you nslookup [www.google.com](www.google.com) from the host os?

also what happens when you disable your VMs and reboot? I think VMware may be the cause. do you specify a MAC address for your virtual nics?

---

### Post by shud on 2008-09-13
I turned the VM off and I'm rebooting now, so I'll see. I have a feeling that the PCI SATA/IDE card and my network dropping were no coincidence. If rebooting yields no results I may try using the other PCI slot.

The virtual NICs all get valid MAC addresses, so that isn't really an issue. I double checked and it's not just cloning my NVIDIA onboard MAC.

---

### Post by doas777 on 2008-09-13
> **shud said:**
> I turned the VM off and I'm rebooting now, so I'll see. I have a feeling that the PCI SATA/IDE card and my network dropping were no coincidence. If rebooting yields no results I may try using the other PCI slot.

The virtual NICs all get valid MAC addresses, so that isn't really an issue. I double checked and it's not just cloning my NVIDIA onboard MAC.

ok, if you think you have hardware problems, then you prolly do. but it seems to me that if your vms can get network connectivity thru teh same physical nic, then it appeears to be operational on a hardware/bios level.

let us know hwo it works out

---

### Post by shud on 2008-09-13
> **doas777 said:**
> ok, if you think you have hardware problems, then you prolly do. but it seems to me that if your vms can get network connectivity thru teh same physical nic, then it appeears to be operational on a hardware/bios level.

let us know hwo it works out

Yep, just as I thought...I pull that SATA/IDE card out and my network connectivity pops right back up. It has to be some kind of IRQ thing. 

Also, oddly enough, that card doesn't even show up in an lspci scan.

---

### Post by doas777 on 2008-09-13
> **shud said:**
> Yep, just as I thought...I pull that SATA/IDE card out and my network connectivity pops right back up. It has to be some kind of IRQ thing. 

Also, oddly enough, that card doesn't even show up in an lspci scan.

weird

---

### Post by shud on 2008-09-13
I put it in the other PCI slot, same deal. What the hell? Do I just have a crappy SATA/IDE carD?

---

