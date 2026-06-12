---
title: "Still USB speed: why can't I use ehci_hcd module?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by kilou on 2008-11-18
Hi,

I'm using Intrepid on my laptop (MSI S260) and I still can't achieve USB 2.0 speeds with it. This is a very famous topic and it seems there is still no solution. I can see on my system that the default loaded module for usb is uhci_hcd, so it is USB 1.1. With this module evyrthing works...but very slowly (1Mb/sec when transferring files to USB stick...)

So I've been trying the usually recommended:

sudo rmmod uhci_hcd
and then
sudo modprobe ehci_hcd

This doesn't work although lsmod lists ehci_hcd module as loaded after the second command. With ehci_hcd loaded no USB device is working, even my USB mouse doesn't light up..... Things only start to work again if I reload uhci_hcd=>USB 1.1 :( 

I've also tried to force ehci_hcd with:

sudo modprobe -f ehci_hcd

and got

FATAL: Error inserting ehci_hcd (/lib/modules/2.6.27-7-generic/kernel/drivers/usb/host/ehci-hcd.ko): Invalid module format

All BIOS settings are OK (I don't have much anyway). Is there any other command I may try (like in fstab or something??)?

Does anyone know what's going on and why it is impossible to get USB2 speeds back in Ubuntu? As far as I remember Feisty was OK but then I couldn't get USB 2 back :( Now seriously considering going back to XP....I love Ubuntu but it's just unproductive with all these problems.

Thanks for any inputs!

---

### Post by vivichrist on 2008-11-26
yep me too.

---

### Post by anewguy on 2008-11-26
In one of the threads I found about this, they claim the plugging the device in before booting at least mounts the device at USB 2 speeds.  As noted in the thread, this does no good once you unplug the device and plug it back in.  Sometimes doing a sudo modprobe -r ehci_hcd followed by sudo moprobe ehci_hcd provides a temporary solution as the device is then allowed to mount and mounts at USB 2 speeds.

When you have these problems, what does dmesg show?  The other threads I have seen show error messages in the log that show with dmesg.

Dave :)

---

