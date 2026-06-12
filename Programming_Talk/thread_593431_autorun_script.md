---
title: "autorun script"
date: 2007-10-27
forum: Programming Talk
---

### Post by kaiwan on 2007-10-27
Hi! A have s mp3 player, and music manager program written in java. 
This program is stored in root folder of my mp3 player.
When I want to launch it I have to do: 
cd /media/disk/
java -jar manager.jar
I wolud like to write s script which will do this automatically when I plug in 
my player?
I have never wrote a script so I have no knowledge of this.

---

### Post by kast on 2007-10-27
plug in your media layer and do a 

**dmesg | grep usb**

and find the line (assuming its usb device) that contains your device and paste it here for me.

we could write a little **"while"** statement that would try and grep out your device, if it doesn't find it it could sleep for 15 second and then run threw the loop again. that of course would mean that there would at up to  a 15 second delay once you plug in your device till your Java app runs. could be less if you sleep 10 or 5 seconds, but then you run into CPU cycles being eaten up for no reason.

---

### Post by kaiwan on 2007-10-28
This is what I get in terminal:
I had only my mp3 pluged in, nothine else
but I am not sure which line is it :)
[   31.492709] usbcore: registered new interface driver usbfs
[   31.492750] usbcore: registered new interface driver hub
[   31.492787] usbcore: registered new device driver usb
[   32.700749]  sda: sda1 sda2 sda3 <<6>usb usb1: configuration #1 chosen from 1 choice
[   32.883162] usb usb2: configuration #1 chosen from 1 choice
[   33.042704] usb usb3: configuration #1 chosen from 1 choice
[   33.145056] usb usb4: configuration #1 chosen from 1 choice
[  158.635309] usb 4-1: new high speed USB device using ehci_hcd and address 2
[  158.769686] usb 4-1: configuration #1 chosen from 1 choice
[  158.898887] usbcore: registered new interface driver libusual
[  159.098408] usb-storage: device found at 2
[  159.098412] usb-storage: waiting for device to settle before scanning
[  159.098530] usbcore: registered new interface driver usb-storage
[  164.086443] usb-storage: device scan complete

---

### Post by kast on 2007-10-28
Well lets see i think its the

158.635309] usb 4-1: new high speed USB device using ehci_hcd and address 2

but if you take the mp3 player out and do the command again do you see those two lines still there?

---

### Post by kaiwan on 2007-10-28
I think not ... 
but to be sure .. with no USB I get this:

miroslav@miroslav-desktop:~$ dmesg | grep us
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[   27.999441] Calibrating delay using timer specific routine.. 4012.90 BogoMIPS (lpj=8025808)
[   28.595070] EISA bus registered
[   28.595090] ACPI: bus type pci registered
[   28.597302] PCI: PCI BIOS revision 2.10 entry at 0xfdb11, last bus=2
[   28.618190] PCI: Probing PCI hardware (bus 00)
[   28.618580] Enabling SiS 96x SMBus.
[   28.622860] ACPI: bus type pnp registered
[   28.627403] ACPI: ACPI bus type pnp unregistered
[   29.967965] input: Macintosh mouse button emulation as /class/input/input0
[   29.968817] mice: PS/2 mouse device common for all mice
[   29.968990] EISA: Probing bus 0 at eisa.0
[   29.970747] Freeing unused kernel memory: 364k freed
[   31.319426] fuse init (API version 7.8)
[   32.359261] usbcore: registered new interface driver usbfs
[   32.359302] usbcore: registered new interface driver hub
[   32.359338] usbcore: registered new device driver usb
[   32.360732] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.547725] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   33.582243]  sda: sda1 sda2 sda3 <<6>usb usb1: configuration #1 chosen from 1 choice
[   33.706332] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   33.764171] usb usb2: configuration #1 chosen from 1 choice
[   33.866117] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   33.923829] usb usb3: configuration #1 chosen from 1 choice
[   34.025974] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   34.026181] usb usb4: configuration #1 chosen from 1 choice
[   34.200005] swsusp: Resume From Partition 8:5
[   34.200008] PM: Checking swsusp image.
[   43.936234] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   46.315784] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   46.500690] intel8x0_measure_ac97_clock: measured 54903 usecs
[   47.064467] lp0: using parport0 (interrupt-driven).
[   58.768932] ppdev: user-space parallel port driver
[   58.945641] audit(1193587553.707:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4647 profile="/usr/sbin/cupsd"

---

### Post by kast on 2007-10-28
humm.. maybe 

[ 159.098408] usb-storage: device found at 2
[ 159.098412] usb-storage: waiting for device to settle before scanning
[ 164.086443] usb-storage: device scan complete
:)

if so then an **until** statement will work

[B]#!/bin/sh

until dmesg | grep usb-storage >/dev/null
do
sleep 15
done

cd /media/disk/
java -jar manager.jar &
exit 1[/B]

of course usb-storage might show up also say with an external hard drive. we will probably need a better grep ???? name.

---

### Post by kaiwan on 2007-10-28
And where do I put this script? 
And how do I name it?
What do you mean by better grep name?
:)

---

### Post by kast on 2007-10-28
Ok first you could put it in **/usr/local/bin **or create your own binary folder in **/usr/local**. there is arguments on where to put your home grown scripts its really up to you.

Name it what ever you want.

What I mean by grep name is that using usb-storage: might work right now, but i believe that's probably a generic name for all usb storage devices, so if down the road (or right now) you get a; say external hard drive this might also show up with usb-storage: and then that script will be getting a false positive.

I don't have a mp3 player to plug in an test, hopefully someone else reading (or research on-line I can check) can get a better way to query you mp3 device and get a better name to put in the script instead of **usb-storage: **

what mp3 player do you have?

---

### Post by kaiwan on 2007-10-29
So if I put it in /usr/local/bin it will run every time I start Ubuntu?
Name should be something like: mp3autorun.**sh**?
Is extension good?

I have Sony NE-E003, which is great, but Sony's music manager is vary bad. So I found some free java music manager that does the job more easily and more user-friendly

---

### Post by kast on 2007-10-29
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by kaiwan on 2007-10-29
thanks for help :)

---

### Post by kast on 2007-10-29
your welcome! take care.

---

### Post by kaiwan on 2007-10-29
Could you please see this:
[http://ubuntuforums.org/showthread.php?p=3663962#post3663962](http://ubuntuforums.org/showthread.php?p=3663962#post3663962)

---

