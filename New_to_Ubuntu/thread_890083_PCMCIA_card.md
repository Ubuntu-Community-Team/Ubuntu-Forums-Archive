---
title: "PCMCIA card"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by palmtree3000 on 2008-08-14
First of all, this is my first post here, so hello, ubuntu forums!

I'm trying to use my pcmcia card (A Network Everywhere Ethernet 10BaseT) with my newly xubuntified laptop. It was working on the old OS (Windows 2000). I looked up the drivers for this card, and found under the linux the readme attached.

However, the mentioned utility (pcmcia-cs-3.2.8) is apparently outdated, according to [http://pcmcia-cs.sourceforge.net](http://pcmcia-cs.sourceforge.net), so I followed the link to [http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html).

I was unable to use make successfully and all the other instructions presume skills I do not have. On searching these forums, I saw a request to post the results of lspci, so here it is:
palmtree3000@laptop1:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
palmtree3000@laptop1:~$ 

Any help would be greatly appreciated!

---

### Post by anewguy on 2008-08-14
I don't know about xubuntu, but for regular Ubuntu, there is a new package called pcmciautils that replace pcmcia-cs.  So, as a new Ubuntu user, one of the first things you need to know is to first try to install packages from the normal package manager included - in Ubuntu the graphical front end is called Synaptic Package Manager.  I don't know if that is available in xubuntu or not, but if so you should use it.  Xubuntu may use a different package manager, but you should look there for the package and install it from there and you should be fine.

Post back if you have more questions or problems.  :)

---

### Post by halitech on 2008-08-14
> **palmtree3000 said:**
> 
palmtree3000@laptop1:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
palmtree3000@laptop1:~$ 


I don't see a network controller listed there. With mine (an airlink using the RT61 chipset) and even before I enabled the drivers it still showed up. Was the card plugged in when you did the lspci?

> 
I don't know about xubuntu, but for regular Ubuntu, there is a new package called pcmciautils that replace pcmcia-cs. So, as a new Ubuntu user, one of the first things you need to know is to first try to install packages from the normal package manager included - in Ubuntu the graphical front end is called Synaptic Package Manager. I don't know if that is available in xubuntu or not, but if so you should use it. Xubuntu may use a different package manager, but you should look there for the package and install it from there and you should be fine.

pcmciautils is the same in xubuntu and should have been installed when he installed xubuntu if it detected a laptop. And yes, Xubuntu also uses Synaptic

---

### Post by palmtree3000 on 2008-08-15
I discovered that it was installed by default, but I don't know what to do with it.

Yes, the card was plugged in at the time I ran lspci. I ran it with and without the card again, and the results were identical, so it's not just an odd name. However, I know the card is not broken, as it works with windows 2000.

---

### Post by halitech on 2008-08-15
if the results are identical with and without the card then Ubuntu is not seeing it as the list should have changed when you took it out or put it in

---

### Post by palmtree3000 on 2008-08-15
I thought that Ubuntu not recognizing my card *was *the problem.

---

### Post by halitech on 2008-08-15
it is a problem but its different then in most cases where Ubuntu knows the card or device is there but doesn't have drivers to use it.

Have you tried installing pcmciautils to see if its just the pcmcia bus isn't activated properly?

---

### Post by palmtree3000 on 2008-08-15
I did try to install pcmcia tools, but ran into masses of errors. However, it turns out that it's already installed (I checked the package manager) so I might be able to do whatever you had in mind using pcmcia tools.

---

### Post by halitech on 2008-08-15
I'm not really sure, I've never had to use the pcmcia tools as I'm on a desktop and on my laptop, it just worked as soon as I plugged in my pcmcia wireless nic. Hopefully someone else will have an idea for you

---

### Post by palmtree3000 on 2008-08-15
Ok, thanks anyway for your help.

---

### Post by palmtree3000 on 2008-08-15
Update!

Based upon the "CardBus (sometimes also PCMCIA) cards not found" error on [http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) , I tried the boot line edit (to no avail). However, the pccardctl ident command does work, and returns:
> Socket 0:
no product info available
Socket 1:
product info: "Network Everywhere","Ethernet 10BaseT PC Card", "2.0", " "
manfid: 0x0149, 0xclab
function: 5 (network)
The sucess of pccardctl ident is independent of the revised boot settings.

---

