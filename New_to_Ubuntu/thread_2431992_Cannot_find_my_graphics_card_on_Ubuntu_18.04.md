---
title: "Cannot find my graphics card on Ubuntu 18.04"
date: 2019-11-25
forum: New to Ubuntu
---

### Post by astorian on 2019-11-25
So I'm having an issue with finding my nvidia driver. I am new to ubuntu and using it while my main computer is at the service shop. I wanted to install world of warcraft. But now the only thing in my way is the graphic card isnt found.

hwinfo --gfxcard --short


graphics card:                                                  
                       Intel 3rd Gen Core processor Graphics Controller


Primary display adapter: #19

That's what I get when i look what cards i got, my nvidia isn't even showing up.




nvidia-smi


NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

Checked if it was properly installed and got that one.

Have installed the drivers through the console.

---

### Post by mörgæs on 2019-11-25
Hi, welcome to the fora.

Please run the command again without the *short* option and post the output in CODE tags. This will show us more details.

---

### Post by astorian on 2019-11-25
Thank you :) Here is what I got, unforunatly I didin't manage to get it in "code tags". Will google and see how I can get it. The only thing that was weird during instalations was that after installing wine and starting up Lutrius, it told me I had some components missing from wine, so it automaticly dloaded and installed something. And at some point it told me I didn't have Vulkan "installed" (can't remember if it said installed or not, followed a guide and "fixed it" and when i opened the program again it didin't warn me of this. Can these things be where it all went wrong? But still I am unsure how these things are connected to the Nvidia drivers not even being visible anywhere :D 

```
hwinfo --gfxcard


19: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.378]
  Unique ID: _Znp.dSULDHE_czE
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel 3rd Gen Core processor Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0166 "3rd Gen Core processor Graphics Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x124d 
  Revision: 0x09
  Driver: "i915"
  Driver Modules: "i915"
  Memory Range: 0xf7800000-0xf7bfffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (ro,non-prefetchable)
  I/O Ports: 0xf000-0xf03f (rw)
  Memory Range: 0x000c0000-0x000dffff (rw,non-prefetchable,disabled)
  IRQ: 29 (479719 events)
  Module Alias: "pci:v00008086d00000166sv00001043sd0000124Dbc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


Primary display adapter: #19
```

---

### Post by TheFu on 2019-11-25
What does :
```
lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
```
say?
How about: 
```
sudo lshw -C video
```

Again, please use code tags, like I have.

---

### Post by astorian on 2019-11-26
```
lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. 3rd Gen Core processor Graphics Controller
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915



```

```
sudo lshw -C video[sudo] password for trapped: 
  *-display                 
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff



```

---

### Post by deadflowr on 2019-11-26
Try a different variant of the lspci command
```
lspci | egrep "VGA|3D" 
```

Also double check in the machine's BIOS settings that the card is accessibly set to use.

---

### Post by astorian on 2019-11-26
```
lspci | egrep "VGA|3D"00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)



```

I was unable to find the hardware tab in my bios. Can this be the problem? Do I have to update my bios? &#129300;

---

### Post by TheFu on 2019-11-26
The system doesn't see your discrete GPU at all.  I'd pull the card out and test it in a different slot and a different system.
Sometimes 1 slot in a motherboard will fail, though it is really odd.  Motherboards do fail, but so do GPUs.  I've also seen a PSU failure take out a GPU.

Which model nvidia card is it?  I have a few different cards here.
GeForce GT 1030
GeForce GT 430
and those are seen always.

---

### Post by astorian on 2019-11-26
The computer is a laptop and the graphics card is a 710M, a older one. Should still be comaptible with the new Nvidia 430 drivers though.

```
apt list --upgradableListing... Done
libpython3.6/bionic-updates 3.6.9-1~18.04 amd64 [upgradable from: 3.6.8-1~18.04.3]
libpython3.6-minimal/bionic-updates 3.6.9-1~18.04 amd64 [upgradable from: 3.6.8-1~18.04.3]
libpython3.6-stdlib/bionic-updates 3.6.9-1~18.04 amd64 [upgradable from: 3.6.8-1~18.04.3]
python3.6/bionic-updates 3.6.9-1~18.04 amd64 [upgradable from: 3.6.8-1~18.04.3]
python3.6-minimal/bionic-updates 3.6.9-1~18.04 amd64 [upgradable from: 3.6.8-1~18.04.3]



```

What does this mean?

---

### Post by TheFu on 2019-11-26
For laptops, often there are how-to guides for some models to get things working.  Search for the *{exact model} ubuntu 18.04 install* . I have an Asus F510UA laptop, so my search would be **Asus F510UA ubuntu 18.04 install**.  

nvidia drivers for LTS Ubuntu Releases: [https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)
Seems that some laptops with nvidia GPUs need the nomemset grub option to get the installer working. I suspect you are way passed that.

If you want to know what any command or option does, there are manpages.   **man apt** which should explain. To search the summary line of every manpage, use *man -k {search term}* - or apropos.  For example, **apropos passwd** will find all the different passwd related manpages. Note that the file description is in section 5. **man man** explains how to see the different section manpages.

Running updates at least weekly and doing backups **at least** monthly is expected systems maintenance for all Linux machines.  Seems a few packages can be updated for your install. 
```
sudo apt update
sudo apt dist-upgrade
sudo apt autoremove

```

Some of us crazy people do daily, versioned, backups.  Doing them daily means just a few minutes are needed. With versioned backups, the longer period between backups, the longer each version will require and the greater risk of data loss.

---

### Post by astorian on 2019-11-26
> **TheFu said:**
> 

Seems that some laptops with nvidia GPUs need the nomemset grub option to get the installer working. I suspect you are way passed that.



Unfortunatly I have no idea what that means, after googling I am still not any closer to understand what Grub is or how I can get it/set it up :D

---

### Post by TheFu on 2019-11-26
If you have an installed system ... then 
> I suspect you are way passed that.  Not all systems need it. If you have an installed system, then yours doesn't.  BTW, I made a mistake - google autocorrected to show nomodeset results, which is what you would have wanted, if that was an issue, but since it isn't.

What about the other items?  Like searching for specific setup instructions for ubuntu 18.04 with your exact laptop model?
or
Following the instructions for nvidia drivers for LTS Ubuntu Releases: [https://www.omgubuntu.co.uk/2019/07/...ate-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/...ate-ubuntu-its) 
?

---

