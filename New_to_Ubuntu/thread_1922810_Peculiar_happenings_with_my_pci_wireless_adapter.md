---
title: "Peculiar happenings with my pci wireless adapter"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by rabidtetra on 2012-02-09
Hello, 
I am brand new to ubuntu (started yesterday) and I had just intalled ubuntu on my desktop, when I decided I needed internet. I threw in a netgear wireless adapter to a pci slot, and proceeded to attempt to install ndiswrapper. After failing miserably, and reaching a point in which I decided it would be best to simply format the drive and reinstall ubuntu. When I did this, my wireless adapter was not only recognized by ubuntu, but it works perfectly now. I haven't installed ndiswrapper yet, but I was curious as to why it wouldn't work before. Yet, it works now. I assume it has something to do with the fact that it was actually in the motherboard when I installed ubuntu the second time, but I do not know enough to figure out why on my own. There is no emergency, I am just curious to find out how/why this happened.
 
Thank you

---

### Post by grahammechanical on 2012-02-09
When we use the live CD/DVD to either try Ubuntu without installing or to install Ubuntu we get a screen when nothing happens but a lot of disk activity and four or five dots on the screen slowly changing colour.

That is the Ubuntu install process interrogating the hardware. When you first installed Ubuntu it did not find a PCI wireless adapter so it did not install the driver module for it.

The second install found the PCI wireless adapter and installed the driver module.

An alternative method would have been to run the Additional Drivers utility. This will check and install any drivers that are available. In the case of something like a newly installed wireless adapter we might need to re-boot for the module to be loaded.

We should not need to re-install when we add or change things like wireless and video adapters. And I do not think that we need to.

Regards.

---

### Post by Cheesemill on 2012-02-09
> **rabidtetra said:**
> I threw in a netgear wireless adapter to a pci slot, and proceeded to attempt to install ndiswrapper.

Why did you attempt to install ndiswrapper? Did you test to see if the network was working before you tried this?

With Linux, nearly all of the drivers  you need are already built in to the OS, it doesn't matter if the card was there when you installed or not. The OS automatically probes for all connected hardware every time you boot and attempts to load the correct drivers.

If it works OK after a fresh install then it's likely that you broke something when you tried using ndiswrapper to install drivers for the card.

---

### Post by rabidtetra on 2012-02-09
Thank you, I am pretty sure that I broke something trying to install ndiswrapper. But It works now, and I understand why. 
 
Thanks again

---

