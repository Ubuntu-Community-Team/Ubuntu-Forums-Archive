---
title: "External USB drive"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Primetime65 on 2008-08-20
Hi Everyone,

I have an external usb hard disk (WD SATA NTFS format) that I am trying to "get to" while using Ubuntu. I am the newbest of newb with Ubuntu. I have searched the forums regarding this, but nothing is really fitting my exact predicament. I tried looking at Places> Computer, but it does not show up. I know the drive and enclosure are good, it works fine on the laptop using XP. Any suggestions are greatly appreciated, I have a lot of stuff backed up on this drive and would like to be able to use Ubuntu going forward

---

### Post by lianne_john07 on 2008-08-20
#Do you know its partition type.

---

### Post by mlentink on 2008-08-20
@lianne_john07: Just out of curiosity: any particular reason why you precede all your lines with a hash (#) sign?
The OP already specified the partition: NTFS.

---

### Post by philinux on 2008-08-20
Plug the drive in. 

Then open a terminal and copy and paste this command in. Post the results.

```
dmesg | tail -30
```

---

### Post by bobnutfield on 2008-08-20
With the drive plugged in, type in a terminal:

> sudo fdisk -l

You need to have ntfs-3g installed (available in Synaptics) to mount it and read it.  The output of fdisk -l will tell you how Ubuntu recogizes it.  Example "/dev/sdb"

It should show up automatically when you have ntfs-3g installed.

---

### Post by philinux on 2008-08-20
> **bobnutfield said:**
> With the drive plugged in, type in a terminal:



You need to have ntfs-3g installed (available in Synaptics) to mount it and read it.  The output of fdisk -l will tell you how Ubuntu recogizes it.  Example "/dev/sdb"

It should show up automatically when you have ntfs-3g installed.

I thought that but I checked my new install and ntfs-3g got installed by default.

---

### Post by lianne_john07 on 2008-08-20
oops sorry mlentink...
Primetime, you can try
1.) dmesg | tail -n50
2.) you will find there the direct path of your device
       ex. sdb

---

### Post by philinux on 2008-08-20
> **lianne_john07 said:**
> oops sorry mlentink...
Primetime, you can try
1.) dmesg | tail -n50
2.) you will find there the direct path of your device
       ex. sdb

You're repeating what I already posted.

---

### Post by Primetime65 on 2008-08-20
> **philinux said:**
> Plug the drive in. 

Then open a terminal and copy and paste this command in. Post the results.

```
dmesg | tail -30
```

Here are the results:

primetime@rogue:~$ dmesg | tail -30
[   51.987271] usb 2-2: device descriptor read/64, error -62
[   52.270918] usb 2-2: device descriptor read/64, error -62
[   52.550578] usb 2-2: new low speed USB device using ohci_hcd and address 7
[   52.730357] usb 2-2: device descriptor read/64, error -62
[   53.014019] usb 2-2: device descriptor read/64, error -62
[   53.293680] usb 2-2: new low speed USB device using ohci_hcd and address 8
[   53.701185] usb 2-2: device not accepting address 8, error -62
[   53.876976] usb 2-2: new low speed USB device using ohci_hcd and address 9
[   54.274261] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   54.274273] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ20
[   54.472249] usb 2-2: device not accepting address 9, error -62
[   54.647380] NET: Registered protocol family 17
[   57.265069] NET: Registered protocol family 10
[   57.265274] lo: Disabled Privacy Extensions
[   57.774982] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   57.774990] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   57.774994] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[   57.775570] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   57.775734] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   57.775932] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[   57.776094] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   57.780164] [fglrx] GART Table is not in FRAME_BUFFER range
[   57.780173] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   57.891364] [fglrx] interrupt source 20008000 successfully enabled
[   57.891371] [fglrx] enable ID = 0x00000004
[   57.891671] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   57.891890] [fglrx] interrupt source 10000000 successfully enabled
[   57.891894] [fglrx] enable ID = 0x00000005
[   57.892128] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   68.143662] eth0: no IPv6 routers present

---

### Post by Primetime65 on 2008-08-20
> **bobnutfield said:**
> With the drive plugged in, type in a terminal:



You need to have ntfs-3g installed (available in Synaptics) to mount it and read it.  The output of fdisk -l will tell you how Ubuntu recogizes it.  Example "/dev/sdb"

It should show up automatically when you have ntfs-3g installed.

Here is the output for fdisk -l

primetime@rogue:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd367d367

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris

This looks like the output for the internal drive

---

### Post by philinux on 2008-08-20
Correct sda is your linux install on the internal drive

```
usb 2-2: device descriptor read/64, error -62
[ 52.270918] usb 2-2: device descriptor read/64, error -62
[ 52.550578] usb 2-2: new low speed USB device using ohci_hcd and address 7
[ 52.730357] usb 2-2: device descriptor read/64, error -62
[ 53.014019] usb 2-2: device descriptor read/64, error -62
[ 53.293680] usb 2-2: new low speed USB device using ohci_hcd and address 8
[ 53.701185] usb 2-2: device not accepting address 8, error -62
[ 53.876976] usb 2-2: new low speed USB device using ohci_hcd and address 9
```

This looks like why you cant see the drive.
I'd plug it into the laptop and have xp do a chkdsk on it. Then safely unmount it before trying it on you buntu machine.

---

### Post by Primetime65 on 2008-08-20
So having a USB 2.0 enclosure connected to a USB 1.1 hub will not work?

---

### Post by philinux on 2008-08-20
> **Primetime65 said:**
> So having a USB 2.0 enclosure connected to a USB 1.1 hub will not work?

They're backwards compatible so should be no worries there, apart from the speed. It might be you unplugged the drive from the laptop without unmounting it first that can cause errors on the drive.

---

### Post by timcredible on 2008-08-20
> **Primetime65 said:**
> So having a USB 2.0 enclosure connected to a USB 1.1 hub will not work?
it should work, but some usb 2.0 devices/enclosures don't pass the 1.1 backward compatibility test.  if i were you, i'd spend the $5US or $10US on a usb 2.0 card for your pc.  you don't really want to use usb 1.1 speeds anyway.

---

### Post by bobnutfield on 2008-08-20
It is very long and drawn out, but this issue is discussed in this page:

[http://www.linux-usb.org/FAQ.html#ts6]("http://www.linux-usb.org/FAQ.html#ts6")

This device descriptor error is discussed in many places (googled).  Apparently, it is not accepting the address, and this page discusses some solutions.  I read some posts on the Arch forum where some users solved this by simply replacing the cable.

But, I believe timcredible has the answer.  A USB 2.0 card, very inexpensive and easy to install.

---

### Post by philinux on 2008-08-20
> raman aka morph said on 2007-12-16:

ya the problem is that ehci_hcd loads before ohci_hcd or maybe the vice versa .
and only solution to this is to use >>"modprobe -r ehci_hcd "<< and the device will be mounted .
the problem is due to parallel running of these modules maybe this will help?


From here. [https://answers.launchpad.net/ubuntu/+question/4272](https://answers.launchpad.net/ubuntu/+question/4272)

+1 for the usb 2 card.

---

### Post by Primetime65 on 2008-08-20
I plugged the drive directly into the the USB2 slot, it shows up, but when i select it, i get can't mount drive message, the "modprobe -r ehci_hcd" command, where do I put this, i tried running it in the konsole, but it gives me a Fatal error....

Again all help is greatly appreciated..

---

