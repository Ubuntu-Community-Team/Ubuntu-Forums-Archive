---
title: "Windows 7 and USB 3.0 through Ubuntu?"
date: 2015-06-06
forum: New to Ubuntu
---

### Post by dazedandconfused75 on 2015-06-06
Hello,

I'd like to start out by saying that I've been trying Ubuntu 12.04 for two weeks, it's a terrific OS, but it's not for me. Been a gamer and windows user too long to permanently switch to Ubuntu or anything else for that matter. Through a series of circumstances, however, I'm stuck with Ubuntu OS. Here's the situation:

Basically, the optical drive on my laptop has died a long time ago (replacing it would take time and money which I don't have), and all I have left are only USB 3.0 ports. I have a windows 7 USB kit, but it doesn't have in-built drivers for USB 3.0, which means it can't install the OS through USB.

Apparently, [you can install these drivers on the usb installation disk through the windows command line]("http://codeabitwiser.com/2014/03/how-to-install-windows-7-with-only-usb-3-0-ports/"), but obviously, I don't have access to one in Ubuntu, and the command line in the windows repair kit can't see the folders I'm using. Aaand, to top it all off, I don't have access to another windows machine...

So, I guess it boils down to this:

1. Is there a way to issue these windows command lines through Ubuntu?

2. If 1) isn't possible, is there an alternative way to install windows from Ubuntu? I'm thinking a virtual win7 instalation image mounted on a virtual drive, and wine? Are there any easy guides out there to do this?

Thanks in advance.

---

### Post by TheFu on 2015-06-06
Use USB2 for the install. You don't need USB3. Are there any USB2 ports on the machine?

---

### Post by dazedandconfused75 on 2015-06-06
Wish I did. Wouldn't have bothered you guys about this...

---

### Post by TheFu on 2015-06-06
> **dazedandconfused75 said:**
> Wish I did. Wouldn't have bothered you guys about this...

Sorry - don't have any answer. WINE won't help - it is an API layer that makes Linux appear to be Windows. It is not complete. It is a way to run windows programs under Linux. It is not a way to run Windows.

The question really is more about Windows, than Linux. I

If you live near a metro area, most have Windows User Groups, you could ask for help there. Someone will have knowledge and a way to help, I suspect.

---

### Post by sotiris2 on 2015-06-06
How about installling windows on a virtual machine on the linux host to get access to the windows command line?

---

### Post by TheFu on 2015-06-06
> **sotiris2 said:**
> How about installling windows on a virtual machine on the linux host to get access to the windows command line?

A few more thoughts ... 
Is it possible to have the BIOS disable USB3 and force USB2 or USB1.1 support for the remaining USB ports?  I know that to get my USB3 add-on cards working for a few of my systems, I had to completely disable all built-in USB2 ports on the motherboard. One of the boxes had 8 of those - all disabled.

Using a VM isn't likely to work, since the VM provides virtual-hardware. USB3 is not supported thru VM USB passthru, only USB2 and only for a subset of devices, not all of them. 

Gaming inside a VM is tough too.  It requires PCI passthru.  Doing PCIx/PCIe passthru requires VT-d, a BIOS that supports/allows it, and a special kernel. The card will be assigned 100% to the VM, not available at all to the hostOS. In short, it is non-trivial, if you have the right hardware.  Normally people passthru a $350 video card - there are specific models that are known to work. Another video card is needed for the host. The Windows license needs to be portable to new hardware too.  There is a very long thread about doing this in the virtualization subforum. It is difficult for someone with 5 yrs of CLI linux experience. 

Hopefully someone will brainstorm a solution.

---

### Post by dazedandconfused75 on 2015-06-07
Managed to solve it in the meantime. Apparently, the windows repair command prompt did the trick. Thanks for all the replies.

---

### Post by sotiris2 on 2015-06-08
> **TheFu said:**
> A few more thoughts ... 
Is it possible to have the BIOS disable USB3 and force USB2 or USB1.1 support for the remaining USB ports?  I know that to get my USB3 add-on cards working for a few of my systems, I had to completely disable all built-in USB2 ports on the motherboard. One of the boxes had 8 of those - all disabled.

Using a VM isn't likely to work, since the VM provides virtual-hardware. USB3 is not supported thru VM USB passthru, only USB2 and only for a subset of devices, not all of them. 

Gaming inside a VM is tough too.  It requires PCI passthru.  Doing PCIx/PCIe passthru requires VT-d, a BIOS that supports/allows it, and a special kernel. The card will be assigned 100% to the VM, not available at all to the hostOS. In short, it is non-trivial, if you have the right hardware.  Normally people passthru a $350 video card - there are specific models that are known to work. Another video card is needed for the host. The Windows license needs to be portable to new hardware too.  There is a very long thread about doing this in the virtualization subforum. It is difficult for someone with 5 yrs of CLI linux experience. 

Hopefully someone will brainstorm a solution.

Well he wouldn't require direct acess to the usb device, in the linked tutorial a file is copied of the usb stick, processed via windows cli and then copied back to the usb.

---

