---
title: "[SOLVED] Device Management HELP"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by SupLegolas on 2008-06-10
Hi,

I've posted in other forums to no avail, but I hope here someone can help me. I have looked for a device manager, similar to the Microsoft Windows Device Manager, that could disable/enable a specific device  (PCI/USB/Anything). I have been told that there is something under the System->Administrator panel called "Hardware Information" yet I can not find such a listing. I don't need a GUI, all I would like to do is disable a USB device and then later enable it, without the need to reach behind my computer and take it out physically.

Thanks,

-Ian

Ubuntu 8.04

ex) Device 001 is wireless adapter.
I want to disable it for some reason (maybe it failed temporarily and I simply wish to restart it)

---

### Post by miss.magenta on 2008-06-10
The device managers that are available for gnome and kde (as far as I know), do not have the same type of functionality that you are used to in Windows - they will list your hardware info, but you won't be able to enable or disable your hardware with them.

For network adapters, it's easy enough - just issue sudo ifup <adapter> or sudo ifdown <adapter>

For other things, you are probably going to have to remove the appropriate kernel module using sudo modprobe -r <modulename> (this does not do anything to the module itself, just unloads it from the running kernel) and then use it again to load it up again like sudo modprobe <modulename>; however, in the case of a USB device, it will likely still need to be unplugged and plugged back in before it will be recognized after using modprobe -r.  

Useful commands for device management:

lsmod - listing of kernel modules
lsusb - listing of usb devices
lspci - listing of pci devices
modprobe - to load and unload dynamic kernel modules
dmesg

And, an interesting command, I think, when you're stuck and don't know what commands are available for a general topic, is 'apropos'.  Try apropos network from a terminal...you should see a list of all commands available that pertain to networking functions along with a very brief description of what they are.

---

### Post by Darkade on 2008-06-10
And anyway Hardware Information has been removed in 8.04 but there's this app instead that just might do some of the things you might want to do just there in "System>administration>authorizations"

---

### Post by SupLegolas on 2008-06-11
Miss.magenta,

Thank you very much! 

-Ian

---

