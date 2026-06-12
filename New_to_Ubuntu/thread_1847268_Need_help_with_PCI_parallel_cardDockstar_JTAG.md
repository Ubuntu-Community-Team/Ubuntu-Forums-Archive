---
title: "Need help with PCI parallel card/Dockstar JTAG"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by kanishk619 on 2011-09-20
I bought a PCI parallel card to use with a JTAG adapter, also got the driver CD and installed it on windows, but the problem is the program(depends on a cfg file in which the address has to be saved) which m using depends on a particular address so that it can communicate with the parallel port, here is the below output of the file

File: parport.cfg
> 
#

# Parallel port wiggler (many clones available) on port 0x378
#

# Addresses: 0x378/LPT1 or 0x278/LPT2 ...



interface parport

parport_port 0x378
parport_cable wiggler

all i came across is the info that 0x378 and 0x278 address comes with mostly onboard parallel ports. 

I can also try with ubuntu if needed, but again have tried almost everything. Below is the output of the lspci -v

LINUX

> 04:05.0 Serial controller: Device 4348:5053 (rev 10) (prog-if 02 [16550])
    Subsystem: Device 4348:5053
    Flags: medium devsel, IRQ 20
    I/O ports at e800 [size=8]
    I/O ports at e400 [size=8]
    Kernel driver in use: serial


I also came across this info,
> 
sudo bash
cd /lib/modules/2.6.32-29-generic/kernel/drivers/char
rmmod lp
cd /lib/modules/2.6.32-29-generic/kernel/drivers/parport
rmmod parport_pc
insmod parport_pc.ko io=0xd000 #replace 0xd000 with whatever you see in your system above

but when i enter "rmmod lp" , it shows the below output
> ERROR: Module lp does not exist in /proc/modules


Any kind of help is very much appreciated.

---

### Post by kanishk619 on 2011-09-21
no 1 ? :(

---

### Post by ian dobson on 2011-09-21
Hi,

In the good old days of ISA bus (XT-486) all I/O cards sat in low memory (Parallel 378,278 for lpt1/2 and 3f8/3f8 for com1,com2) Modern I/O (PCI) cards sit in high memory.

What you need to do is run lspci -v and find the parallel port card and then use that address for the insmod for the parallelport and for your bitwiggler.

Ps the lspci -v you supplied what for the serial ports not parallel.

Regards
Ian Dobson

---

