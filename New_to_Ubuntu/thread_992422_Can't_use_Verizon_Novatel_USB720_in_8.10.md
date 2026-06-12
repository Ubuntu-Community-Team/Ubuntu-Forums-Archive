---
title: "Can't use Verizon Novatel USB720 in 8.10"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by dmalpack89 on 2008-11-24
Hi here are my stats:

Dual boot with Windows Vista Home Premium

AMD64 on a dv6000 pavilion

Ubuntu 8.10

Is there a way I can connect to the internet with my Verizon USB720?

I pay for the monthly subscription and since I plan to use Ubuntu more it would suck if I could only connect with it in Windows. Any ideas!

Thanks everyone

---

### Post by crjackson on 2008-11-24
> **dmalpack89 said:**
> Hi here are my stats:

Dual boot with Windows Vista Home Premium

AMD64 on a dv6000 pavilion

Ubuntu 8.10

Is there a way I can connect to the internet with my Verizon USB720?

I pay for the monthly subscription and since I plan to use Ubuntu more it would suck if I could only connect with it in Windows. Any ideas!

Thanks everyone

The UM150 from Verizon works great. I would look into grabing one of those if you can't get it worked out.

---

### Post by pcweeny on 2008-11-25
I'm in the same boat.
S720 (Sprint) on Ubuntu 8.10 (64bit)

The system is a brand new Dell D830 (Intel Core2 Duo Mobile T9500)

The card is recognized at some level:

excerpt from lspci output:

04:00.0 USB Controller: NEC Corporation USB (rev 43)
04:00.1 USB Controller: NEC Corporation USB (rev 43)

(those entries don't appear when the card isn't plugged in)

lsusb gives me idential results whether the card is installed or not, and I certainly don't have any /dev/ttyUSB* devices, so the ball is being dropped somewhere.

Syslog entries on card eject / reconnect below, with emphasis on the "USB HC takeover failed!  (BIOS/SMM bug)" lines for each of the above listed devices.

I tried the advice in this thread:
[http://ubuntuforums.org/showthread.php?t=169458](http://ubuntuforums.org/showthread.php?t=169458)
But that only changed the reported error to a timeout.

First, the original errors:

Nov 24 23:34:45 DellLaptop kernel: [ 2624.873109] pccard: card ejected from slot 0
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144174] pccard: CardBus card inserted into slot 0
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144277] PCI: 0000:04:00.0 reg 10 32bit mmio: [0, fff]
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144397] pci 0000:04:00.0: supports D1
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144401] pci 0000:04:00.0: supports D2
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144405] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144417] pci 0000:04:00.0: PME# disabled
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144494] PCI: 0000:04:00.1 reg 10 32bit mmio: [0, fff]
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144610] pci 0000:04:00.1: supports D1
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144613] pci 0000:04:00.1: supports D2
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144617] pci 0000:04:00.1: PME# supported from D0 D1 D2 D3hot
Nov 24 23:34:50 DellLaptop kernel: [ 2630.144628] pci 0000:04:00.1: PME# disabled
Nov 24 23:34:50 DellLaptop kernel: [ 2630.146307] ohci_hcd 0000:04:00.0: enabling device (0000 -> 0002)
Nov 24 23:34:50 DellLaptop kernel: [ 2630.146325] ohci_hcd 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 24 23:34:50 DellLaptop kernel: [ 2630.146362] ohci_hcd 0000:04:00.0: setting latency timer to 64
Nov 24 23:34:50 DellLaptop kernel: [ 2630.146371] ohci_hcd 0000:04:00.0: OHCI Host Controller
Nov 24 23:34:50 DellLaptop kernel: [ 2630.147455] ohci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
**Nov 24 23:34:58 DellLaptop kernel: [ 2638.156096] ohci_hcd 0000:04:00.0: USB HC takeover failed!  (BIOS/SMM bug)**
Nov 24 23:34:58 DellLaptop kernel: [ 2638.156114] ohci_hcd 0000:04:00.0: can't setup
Nov 24 23:34:58 DellLaptop kernel: [ 2638.156123] ohci_hcd 0000:04:00.0: USB bus 8 deregistered
Nov 24 23:34:58 DellLaptop kernel: [ 2638.161748] ohci_hcd 0000:04:00.0: PCI INT A disabled
Nov 24 23:34:58 DellLaptop kernel: [ 2638.161763] ohci_hcd 0000:04:00.0: init 0000:04:00.0 fail, -16
Nov 24 23:34:58 DellLaptop kernel: [ 2638.164500] ohci_hcd: probe of 0000:04:00.0 failed with error -16
Nov 24 23:34:58 DellLaptop kernel: [ 2638.166129] ohci_hcd 0000:04:00.1: enabling device (0000 -> 0002)
Nov 24 23:34:58 DellLaptop kernel: [ 2638.166148] ohci_hcd 0000:04:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 24 23:34:58 DellLaptop kernel: [ 2638.166176] ohci_hcd 0000:04:00.1: setting latency timer to 64
Nov 24 23:34:58 DellLaptop kernel: [ 2638.166185] ohci_hcd 0000:04:00.1: OHCI Host Controller
Nov 24 23:34:58 DellLaptop kernel: [ 2638.172153] ohci_hcd 0000:04:00.1: new USB bus registered, assigned bus number 8
**Nov 24 23:35:06 DellLaptop kernel: [ 2646.176092] ohci_hcd 0000:04:00.1: USB HC takeover failed!  (BIOS/SMM bug)**
Nov 24 23:35:06 DellLaptop kernel: [ 2646.176108] ohci_hcd 0000:04:00.1: can't setup
Nov 24 23:35:06 DellLaptop kernel: [ 2646.176119] ohci_hcd 0000:04:00.1: USB bus 8 deregistered
Nov 24 23:35:06 DellLaptop kernel: [ 2646.177745] ohci_hcd 0000:04:00.1: PCI INT B disabled
Nov 24 23:35:06 DellLaptop kernel: [ 2646.177752] ohci_hcd 0000:04:00.1: init 0000:04:00.1 fail, -16
Nov 24 23:35:06 DellLaptop kernel: [ 2646.177773] ohci_hcd: probe of 0000:04:00.1 failed with error -16

And after applying the "fix":

Nov 24 23:55:33 DellLaptop kernel: [ 3872.610567] pccard: card ejected from slot 0
Nov 24 23:56:33 DellLaptop kernel: [ 3932.981339] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416091] pccard: CardBus card inserted into slot 0
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416204] PCI: 0000:04:00.0 reg 10 32bit mmio: [0, fff]
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416330] pci 0000:04:00.0: supports D1
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416334] pci 0000:04:00.0: supports D2
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416339] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416350] pci 0000:04:00.0: PME# disabled
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416423] PCI: 0000:04:00.1 reg 10 32bit mmio: [0, fff]
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416531] pci 0000:04:00.1: supports D1
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416535] pci 0000:04:00.1: supports D2
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416539] pci 0000:04:00.1: PME# supported from D0 D1 D2 D3hot
Nov 24 23:56:47 DellLaptop kernel: [ 3946.416550] pci 0000:04:00.1: PME# disabled
Nov 24 23:56:47 DellLaptop kernel: [ 3946.419511] ohci_hcd 0000:04:00.0: enabling device (0000 -> 0002)
Nov 24 23:56:47 DellLaptop kernel: [ 3946.419536] ohci_hcd 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 24 23:56:47 DellLaptop kernel: [ 3946.419575] ohci_hcd 0000:04:00.0: setting latency timer to 64
Nov 24 23:56:47 DellLaptop kernel: [ 3946.419584] ohci_hcd 0000:04:00.0: OHCI Host Controller
Nov 24 23:56:47 DellLaptop kernel: [ 3946.419667] ohci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
Nov 24 23:56:47 DellLaptop kernel: [ 3946.419701] ohci_hcd 0000:04:00.0: irq 19, io mem 0x124000000
**Nov 24 23:56:47 DellLaptop kernel: [ 3946.473140] ohci_hcd 0000:04:00.0: USB HC reset timed out!**
Nov 24 23:56:47 DellLaptop kernel: [ 3946.473157] ohci_hcd 0000:04:00.0: can't start
Nov 24 23:56:47 DellLaptop kernel: [ 3946.473175] ohci_hcd 0000:04:00.0: startup error -1
Nov 24 23:56:47 DellLaptop kernel: [ 3946.473184] ohci_hcd 0000:04:00.0: USB bus 8 deregistered
Nov 24 23:56:47 DellLaptop kernel: [ 3946.475204] ohci_hcd 0000:04:00.0: PCI INT A disabled
Nov 24 23:56:47 DellLaptop kernel: [ 3946.475220] ohci_hcd 0000:04:00.0: init 0000:04:00.0 fail, -1
Nov 24 23:56:47 DellLaptop kernel: [ 3946.475281] ohci_hcd: probe of 0000:04:00.0 failed with error -1
Nov 24 23:56:47 DellLaptop kernel: [ 3946.477456] ohci_hcd 0000:04:00.1: enabling device (0000 -> 0002)
Nov 24 23:56:47 DellLaptop kernel: [ 3946.477478] ohci_hcd 0000:04:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 24 23:56:47 DellLaptop kernel: [ 3946.477509] ohci_hcd 0000:04:00.1: setting latency timer to 64
Nov 24 23:56:47 DellLaptop kernel: [ 3946.477518] ohci_hcd 0000:04:00.1: OHCI Host Controller
Nov 24 23:56:47 DellLaptop kernel: [ 3946.479201] ohci_hcd 0000:04:00.1: new USB bus registered, assigned bus number 8
Nov 24 23:56:47 DellLaptop kernel: [ 3946.479242] ohci_hcd 0000:04:00.1: irq 19, io mem 0x124001000
**Nov 24 23:56:47 DellLaptop kernel: [ 3946.533238] ohci_hcd 0000:04:00.1: USB HC reset timed out!**
Nov 24 23:56:47 DellLaptop kernel: [ 3946.533247] ohci_hcd 0000:04:00.1: can't start
Nov 24 23:56:47 DellLaptop kernel: [ 3946.533259] ohci_hcd 0000:04:00.1: startup error -1
Nov 24 23:56:47 DellLaptop kernel: [ 3946.533266] ohci_hcd 0000:04:00.1: USB bus 8 deregistered
Nov 24 23:56:47 DellLaptop kernel: [ 3946.533978] ohci_hcd 0000:04:00.1: PCI INT B disabled
Nov 24 23:56:47 DellLaptop kernel: [ 3946.533983] ohci_hcd 0000:04:00.1: init 0000:04:00.1 fail, -1
Nov 24 23:56:47 DellLaptop kernel: [ 3946.533991] ohci_hcd: probe of 0000:04:00.1 failed with error -1

---

