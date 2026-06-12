---
title: "Need help applying a kernel patch"
date: 2007-07-03
forum: Programming Talk
---

### Post by rubix64 on 2007-07-03
I am working through the hack that lets my feisty box talk to my winmoble5 pda and now that I have dpwnloaded and compiled synCE step two calls for downloading and installing a driver called usb-rndis-lite and compile it.

The instructions for kernels < 2.6.21   (I have 2.6.20-16-generic)  are as follows:

Download synce-usb-rndis-lite-0.10.0.tar.gz and then:

```
tar zxf synce-usb-rndis-lite-0.10.0.tar.gz
cd synce-usb-rndis-lite-0.10.0/
```

Compile and Install

Note: you must have your Kernel Headers installed:

Note: You need to have CONFIG_USB_NET_CDCETHER compiled either into the kernel, or as a module, in your kernel config. Located in Device Drivers -> USB support -> USB Gadget support -> Ethernet Gadget

Then you have to
 
```
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
```


If you get no errors with the last step, you can plug your device into the computer. This should automatically load the new usb-rndis driver that was just installed. 

I have 2 questions please:

**1. **I have downloaded the driver but when trying to install my kernel headers ```
sudo apt-get install kernel-headers-2.6.20-16-generic
``` I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-headers-2.6.20-16-generic

could someone tell me what the correct package to download is?

**2. ** I have no idea how to " have CONFIG_USB_NET_CDCETHER compiled either into the kernel, or as a module, in your kernel config. Located in Device Drivers -> USB support -> USB Gadget support -> Ethernet Gadget"

Thank you in advance for your kind help

---

### Post by Soybean on 2007-07-03
I'm not exactly an expert here... it's been a very long time since I've done any of this stuff, since my current systems all have pretty well-supported hardware. But I might be able to point you in the right general direction, at least. :)

> **rubix64 said:**
> could someone tell me what the correct package to download is?
I believe it's "linux-headers-2.6.20-16-generic", as opposed to "kernel-..." 

BTW, if you're trying to find a particular package but don't know the name, Synaptic's search feature can be pretty handy. :)

> **2. ** I have no idea how to " have CONFIG_USB_NET_CDCETHER compiled either into the kernel, or as a module, in your kernel config. Located in Device Drivers -> USB support -> USB Gadget support -> Ethernet Gadget"

This is where my memory is a little fuzzy. If it were me, I'd just hope it was compiled as a module by default (which is entirely possible), and proceed accordingly until something went wrong. ;) If something does go wrong, come back here... or look for a guide on compiling your own kernel. You don't need to compile the whole kernel , but compiling kernel modules is part of that (and requires almost all of the same steps, IIRC). 


Oh, something else you should know: if you get this working, you'll have to be more careful with Ubuntu's automatic updates. The updater won't know about your kernel patch, so if you let it, it'll update your kernel and break the patch. That will *probably* just make the link between your computer and your PDA stop working, and you'll *probably* just have to run through this procedure again to fix it... but it's something you likely want to be aware of in advance.

---

### Post by runningwithscissors on 2007-07-03
> **rubix64 said:**
> Note: You need to have CONFIG_USB_NET_CDCETHER compiled either into the kernel, or as a module, in your kernel config. Located in Device Drivers -> USB support -> USB Gadget support -> Ethernet GadgetI am not sure if Ubuntu supplies a kernel config alongwith the compiled kernel. If it does you could grep it to check the value for CONFIG_USB_NET_CDCETHER. It should either be 'y' or 'm'.

If it says that the value for CONFIG_USB_NET_CDCETHER is not set, you'll need to enable support for it in the kernel. Which you do by recompiling it.

---

