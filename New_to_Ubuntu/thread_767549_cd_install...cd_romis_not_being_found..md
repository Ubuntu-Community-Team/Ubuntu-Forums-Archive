---
title: "cd install...cd romis not being found."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Frequent Modulation on 2008-04-25
7.10

trying to install to a laptop...hangs on install when searching for cd rom hardware. no idea how to get around this issue.
Can i install from usb jump drive or perhaps a usb cd rom? 

wwyd?  :)

---

### Post by Frequent Modulation on 2008-04-25
a bit more info: the drive is a pioneer dvd rom k11 in an acer travelmate 213txv. is there a driver for this? how would i install it? floppy?

---

### Post by Frequent Modulation on 2008-04-26
bumping..hope its not to soon

---

### Post by philinux on 2008-04-26
Does the live cd run ok.

---

### Post by Ponomous on 2008-04-26
Is your boot disk a dvd or cd and is the live cd working?

---

### Post by Frequent Modulation on 2008-04-26
the boot disk is a cd. I need to clarify something...I was attempting to install the 7.10 server edition.

I downloaded and burned the 7.10 desktop iso to a cd. I have used 2 options: start or install ubuntu and install with driver update cd. Both options take me through an ubuntu graphic with an orange K.I.T.T light moving left and right then to a screen that seems to be a CLI:

BusyBox v1.1.3 etc,etc,etc


(initramfs) <cursor>


This may have to with me only have 256 megs of ram but I cant be sure.


Whats my next step?

---

### Post by Frequent Modulation on 2008-04-26
i did a forum search on initramfs andthe option that i found was to add all_generic_ide 

So, i got the boot menu. pressed F6 and added that syntax to the boot path (i tried twice. once without deleting the word splash and the second time I deleted the word splash).
Both times im back at busybox.

Here is the exact message on the laptop screen:

Loading, please wait...
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet all_generic_ide --
[   62.824580] irq 15: nobody cared (try booting with the "irqpoll" option)
[   62.825337] handlers:
[   62.825398] [<d00715f0>] (ata interrupt+0x0/0x200 [libata])
[   62.825594] Disabling IRQ #15

should i continue?? or will this be enough? i dont think i will need the cd rom for anything.
can i just use a jump drive to install?

---

### Post by Frequent Modulation on 2008-04-27
Option
	

Impact

vga=xxx
	

Set your [WWW] framebuffer resolution to VESA mode xxx. Check [WWW] here for a list of possible modes.

acpi=off OR noacpi
	

This parameter disables the whole ACPI system. This may prove very useful, for example, if your computer does not support ACPI or if you think the ACPI implementation might cause some problems (for instance random reboots or system lockups).

acpi=force
	

Activates the ACPI system even if your computer BIOS date is older than 2000. This parameter overwrites acpi=off and can also be used with current hardware if the ACPI support is not activated despite apm=off.

pci=noacpi OR acpi=noirq
	

These parameters disable the PCI IRQ routing

pci=acpi
	

This parameter activates the PCI IRQ routing

acpi_irq_balance
	

ACPI is allowed to use PIC interrupts to minimize the common use of IRQs.

acpi_irq_nobalance
	

ACPI is not allowed to use PIC interrupts.

acpi=oldboot
	

Deactivates the ACPI system almost completely; only the components required for the boot process will be used.

acpi=ht
	

Impact Deactivates the ACPI system almost completely; only the components required for hyper threading will be used.

noapic
	

Disable the "Advanced Programmable Interrupt Controller (APIC)".

nolapic
	

Disable the "local APIC".

apm=off OR noapm
	

Disable the Advanced Power Management.

irqpoll
	

Changes the way the kernel handles interrupt calls (set it to [WWW] polling). Can be useful in case of hardware interrupt issues. 


i tried all of these option at boot. im still unable to install.

would it matter wether or not the install is from a cd or dvd? i can try from a dvd if it will help

---

