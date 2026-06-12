---
title: "[SOLVED] parallel port through usb interface?!!"
date: 2008-11-14
forum: Programming Talk
---

### Post by SIGTERMer on 2008-11-14
hi, i need to write a program that uses the parallel port to access an external circuit. of course outb and inb will be used. the problem is that i don't have a parallel port on the computer i will be using! so my question is: will i be able to use outb and inb normally if i use a usb-to-parallel cord? or even more, use a usb-to-serial cord with a parallel to serial converter? and if you haven't figured out yet what language im using, it c

---

### Post by Zugzwang on 2008-11-14
I don't know about the serial-to-parallel converter, but the USB-parallel port interface is likely not to work, mainly because these special cables do not emulate a full parallel port, just enough that printers which do not need some "back-channel" (unlike the HP scanner/printer combination) work.

---

### Post by SIGTERMer on 2008-11-14
if thats true, how much of the port can i use?

---

### Post by samjh on 2008-11-14
> **SIGTERMer said:**
> hi, i need to write a program that uses the parallel port to access an external circuit.If your program will be using a parallel port, then it needs a physical parallel port on the machine it is running on.  You won't get that effect with a mere USB-to-parallel cable.

Therefore, no go.

You might want to purchase a PCI parallel port card.  They will need a bit of tinkering to work under Linux (Verbatim has instructions available for Linux setup for its cards).

Alternatively, you might want to look for a software emulator to create a fake parallel port on your machine, but which will use a USB port for physical communication.  I don't know if anything exists for Linux.

---

### Post by SIGTERMer on 2008-11-14
pci is not an option for me (laptop). i guess i'll have to get my self a pc... isn't there any way i can use my laptop?

---

### Post by Zugzwang on 2008-11-14
> **SIGTERMer said:**
> pci is not an option for me (laptop). i guess i'll have to get my self a pc... isn't there any way i can use my laptop?

There are some "generic" docking stations for notebooks, i.e. you plug it in and get a bunch of connectors, like PS/2 keyboard connectors, more USB ports, serial and parallel port. These **might** have true parallel ports. I have seen such a device once for ~100€. But I have no idea about the Linux support.

---

### Post by SIGTERMer on 2008-11-15
thanks people, but i guess i'll just have to use a normal desktop :(
thanks anyways.

---

### Post by Tails86 on 2009-02-02
I was wondering the same thing. I did some quick searching on google and found one guy's site where he made a USB parallel port emulator that can be used for any parallel device (not just printer). Found here: [http://www-user.tu-chemnitz.de/~heha/bastelecke/Rund%20um%20den%20PC/USB2LPT/index.html.en](http://www-user.tu-chemnitz.de/~heha/bastelecke/Rund%20um%20den%20PC/USB2LPT/index.html.en)

I'm not sure how well it works, but it at least gives hope that it's possible.

---

### Post by wmcbrine on 2009-02-02
Hardware aside, you aren't going to able to use inb and outb under any modern operating system, except through DOS emulation, unless you're actually writing a kernel-level device driver, with all that entails. Banging directly on the hardware went out of style with DOS.

---

### Post by balagosa on 2009-02-03
sorry for reviving a SOLVED thread but i have the same problem.

Mind if I ask what is "inb" and "outb". I know it is a Port interface, but what exactly does it do? Because in my I/O systems in school, we have this library (inpout32.lib) that was made by one of my professors that has a function Out32(short data, short address). Is this possible that outb will be the same as Out32? There is also a function named Inp32(short address) which accepts data from a port.

In my case, I use 0x378 (Data Register for parallel port) for address.

---

### Post by Tails86 on 2009-02-03
> **balagosa said:**
> sorry for reviving a SOLVED thread but i have the same problem.

Mind if I ask what is "inb" and "outb". I know it is a Port interface, but what exactly does it do? Because in my I/O systems in school, we have this library (inpout32.lib) that was made by one of my professors that has a function Out32(short data, short address). Is this possible that outb will be the same as Out32? There is also a function named Inp32(short address) which accepts data from a port.

In my case, I use 0x378 (Data Register for parallel port) for address.

I've actually used that same library a couple years ago (or at least one with the same name). outb/inb and Out32/Inp32 basically do the same thing. As wmcbrine has said, inb and outb will not work under any modern operating system. That library gets around all the crap and puts your right at the hardware. Not sure how, but it works and it's fun to play with :-)

---

