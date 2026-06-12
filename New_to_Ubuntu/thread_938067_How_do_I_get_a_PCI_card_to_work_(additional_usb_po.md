---
title: "How do I get a PCI card to work (additional usb ports)?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by bwallum on 2008-10-04
Hi

I have tried to install a four port usb card. It drops into a PCI slot, one of the normal extension slots on most motherboards. The usb ports are at the back of the computer and present in the same way as vga ports etc.

I get a message at boot up that says 'unknown header type 7f'. It's a plug and play card and doesn't need any drivers apparently. The motherboard comes equipped with 1.1 usb ports. The add on card is 2.0 usb.

Can anybody help me get the usb card running please?

---

### Post by spiderbatdad on 2008-10-04
not sure if i can help or not. It may be possible to pass parameters to the kernel during boot that will enable the use of this card...or it may simply be a bios setting. Upload dmesg if you don't mind...with the card installed.
```
dmesg > ~/Desktop/dmesg.txt
```Right click that file and select create an archive, then upload the archived file with the manage attachment tool below.

---

### Post by bwallum on 2008-10-04
Thanks for helping dmesg.txt uploaded (hopefully). I got the message 'Your file of 24.9 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.' so its in two bits.

---

### Post by spiderbatdad on 2008-10-07
Hi. sorry to be so slow.

```
gksu gedit /boot/grub/menu.lst
```

scroll to this section:

```
## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-5-generic root=UUID=####'s ro **quiet splash **
initrd		/boot/initrd.img-2.6.27-5-generic
quiet

```Delete "quiet splash," shown in bold above. Replace with "lapic pci=routeirq" ```
## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.27-5-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-5-generic root=UUID=##'s ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.27-5-generic
quiet

```save the file and reboot with the card installed.

---

### Post by bwallum on 2008-10-08
Thanks for your help. I'm about 400 miles away from the machine at the moment and I removed the card. This will be a very interesting exercise in remote maintenance! I'll get the card in the post and let you know what happens. I will start a new thread to find out how to work the remote desktop once the card is installed.

Thanks again, brilliant!

Regards
Bob

---

