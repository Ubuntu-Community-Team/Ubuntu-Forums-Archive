---
title: "pci to parallel port card and Cups"
date: 2019-07-13
forum: New to Ubuntu
---

### Post by jim Kane on 2019-07-13
Has anyone successfully used one of these with a parallel port printer 
I have the opportunity to acquire a much newer PC then im using now but it has not got a parallel port 
I really really need to be able to still use my trusty HP laser jet 5 printer 
I have read that the USB to parallel port adaptor leads dont work with Linux/cups
 but cant find any info on the  pci to parallel port cards 
Thanks

---

### Post by kurt18947 on 2019-07-13
Hi Jim
I do not have experience with PCI to Parallel cards but I do have experience with PCI to USB and I suspect compatibility issues are similar. You need to determine

1) what chipsets for your card type are supported by the Linux Kernel
2) what chipset prospective cards use.

The name on the package may have little bearing on whether the enclosed device will work or not. Manufacturers change chipsets and may or may not change model/version information on the packaging. Some wifi device manufacturers are notorious for this. If you're unable to find a PCI/PCI-e card that works I've had luck with an old but still available Netgear ethernet-parallel port adapter if that would be an option for you. There are also wifi-parallel port devices but I have no experience with those.

---

### Post by jim Kane on 2019-07-13
thanks
 i will have a look at the Netgear ethernet-parallel port adapter 
never heard of them before  
im really trying to spend as little money as possible

---

### Post by kurt18947 on 2019-07-14
This is the one I have

[https://www.amazon.com/NETGEAR-PS101-Mini-Print-Server/dp/B00006B9HK/ref=sr_1_1?keywords=netgear+parallel+port+print+server&qid=1563089875&s=gateway&sr=8-1](https://www.amazon.com/NETGEAR-PS101-Mini-Print-Server/dp/B00006B9HK/ref=sr_1_1?keywords=netgear+parallel+port+print+server&qid=1563089875&s=gateway&sr=8-1)

There are others on New Egg. Not inexpensive.

---

### Post by Autodave on 2019-07-14
Just for anyone else that can help: that printer shows as having parallel, LAN, and serial connectivity.

---

### Post by SeijiSensei on 2019-07-14
According to [https://en.wikipedia.org/wiki/HP_LaserJet_5#5Si_Network_Connection](https://en.wikipedia.org/wiki/HP_LaserJet_5#5Si_Network_Connection) the printer requires an add-in network card to support LAN connections. If the OP's printer has such a card, then that would be the way to go. Hardwire the printer to your router with an Ethernet cable, then assign the printer a static IP address within your network subnet.

---

### Post by jim Kane on 2019-07-14
its a 5P and only has a parallel port
i think made for the the Asian market
perhaps I should have made that clear
which is why i would like to use a cheap and easy to get PCI card

---

### Post by kurt18947 on 2019-07-14
Hi Jim
I took some time on Amazon to look at PCI - parallel cards. Here's one of the first to come up:[INDENT][https://www.amazon.com/Port-Profile-Parallel-Adapter-Card/dp/B00006B8DW/ref=sr_1_3?crid=2QZV6ZVZW7C6K&keywords=pci+parallel+port+card&qid=1563145998&s=gateway&sprefix=PCi+para%2Caps%2C128&sr=8-3](https://www.amazon.com/Port-Profile-Parallel-Adapter-Card/dp/B00006B8DW/ref=sr_1_3?crid=2QZV6ZVZW7C6K&keywords=pci+parallel+port+card&qid=1563145998&s=gateway&sprefix=PCi+para%2Caps%2C128&sr=8-3)

The PCI1P_LP 1 Port Low Profile PCI Parallel Adapter Card adds one IEEE  1284 port to your small form factor PC, with data transfer speeds of up  to 1.5 Mbps - up to 3 times faster than on-board parallel ports. The  adapter card features a low profile design that is suited to small form  factor computer cases, while including a full height bracket to adapt to  any installation.  Installation is a breeze with plug and play  support and drivers for Windows 7, Vista, XP, ME, 2000, 98, 95, NT4, **DOS  and Linux. **IRQ sharing and hot swapping capabilities guarantee  convenient, hassle-free connections to any parallel peripheral. 
[/INDENT]
 
That this card is supposed to work with older versions of Windows as well as DOS and Linux is usually a plus. Hardware that only works with the latest & greatest Windows is less likely to work with Linux in my experience.  Here's another where people have said the card works with Linux. Scroll down about 2/3 of the page:

[https://www.amazon.com/dp/B003D7TCZ6/ref=psdc_3015423011_t1_B00XBX05V2](https://www.amazon.com/dp/B003D7TCZ6/ref=psdc_3015423011_t1_B00XBX05V2)

  There's no guarantee though.

---

### Post by jim Kane on 2019-07-15
Kurt 
Thank you so much for your help and time looking into my question
I have found a Startech adaptor on ebay for not a lot of money :)
 so will try it, and will report back if it works or not
Jim

---

### Post by jim Kane on 2019-07-17
I have not yet received the pci adaptor but found this on the startech site,
 how to install card in Linux 
I know to use LSPCI but does the last two command make sense if there is no built in 
parallel port ? 


Q: How do I install this card in Linux?
A: Once you have physically installed the card in the computer, follow the following steps to
activate the port(s) in the operating system:
1.     List the resources assigned to the PCI card by typing this command:
more /proc/pci
The response will include something similar to the following, however, yours will be
different:
Bus 0, Device 11, function 0:
Serial controller : Unknown vendor Unknown device (rev 01).
Vendor id=9710, Device id=9715
Medium devsel. Fast back-to-back capable. IRQ 11
I/O at 0xc000 [0xc001] printer port 1
I/O at 0xc400 [0xc401] ECP/EPP config registers 1
I/O at 0xc800 [0xc801] printer port 2
I/O at 0xd000 [0xd001] ECP/EPP config registers 2
I/O at 0xd400 [0xd401] not used
I/O at 0xd800 [0xd801] not used

2.     Unload the paraport_pc.o module by typing in this command:
rmmod paraport_pc.o

3.     Reload the parport_pc.o module to include the new parallel port. The following example
assumes the resources discovered in step 1 and a built-in motherboard parallel port with a
memory address of 378 and an IRQ setting of 7.
insmod parport_pc.o io=0x378,0xc000,0xc800 irq=7,11,none
The first port assigned will be /dev/lp0, the second will be /dev/lp1, etc. In this case, the built-in
parallel port will be assigned /dev/lp0, and the port on the PCI parallel card will be
/dev/lp1 (and /dev/lp2 if you are using a two port model).

---

### Post by SeijiSensei on 2019-07-19
There may well not be a parallel port module loaded, so step 3 may not apply. You'll know soon enough because you'll get an error message.  Also that command has a typo; it should be parport_pc.o.

Those instructions are written for a machine with an existing parallel port at /dev/lp0. You obviously don't have one of those. The add-on card will likely be assigned to /dev/lp0 and /dev/lp1.

---

### Post by jim Kane on 2019-07-19
Thank i will update when i get the card fitted

---

### Post by kurt18947 on 2019-07-20
I would try the card and printer before changing anything. If it doesn't work then attempt to diagnose the problem.

---

### Post by jim Kane on 2019-07-21
Yes was going to do that first,
 but all of the positive info I have read so far relates to 32bit OS not 64bit so that may well kill this idea stone dead  
but you can never tell with Linux I have a usb wifi stick which will not work on any post windows XP (no drivers)
 but works fine with all Xubuntu going back to 10.4

---

### Post by kurt18947 on 2019-07-21
As regards hardware, it seems like the latest & greatest is not the bestest with Linux. WiFi adapters are prime examples, new WiFi chipsets come out every few weeks or months and oftentimes require extraordinary steps to enable if they can be made to work at all. An adapter (chipset really) that's been around for many months or years is likely to work with no problem, or at least there'll be documenatation.

---

### Post by jim Kane on 2019-07-22
Nope doesn't work,
 listed in Lspci as on LP0 installed Hplip and correct driver but test print just hangs as pending ;(
how very annoying

---

