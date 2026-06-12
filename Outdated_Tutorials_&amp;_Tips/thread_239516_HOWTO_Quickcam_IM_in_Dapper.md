---
title: "HOWTO: Quickcam IM in Dapper"
date: 2006-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by mattyh on 2006-08-19
**Introduction**
I recently got my Quickcam IM working under Dapper Drake.  It is not that difficult, but it requires compiling and installing a more updated version of the spca5xx module than comes with dapper.

In order to make sure you have a Quickcam IM (though this newer version adds support for other webcams as well), make sure you webcam is plugged into a usb port and type the following into the terminal.

```
lsusb
```

My output is:
Bus 003 Device 002: ID 046d:08d9 Logitech, Inc.

According to the documentation, the following ID numbers are for this camera as well.
046d:08a0
046d:08a1
046d:08a6

Now, let's get to the fun part.

**Compiling**
First off, let's grab the source from [http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz]("http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz")

Let's also make sure the needed packages are installed by typing the following:
```

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname-r` build-essential
```

After those packages are done installing, extract the file we downloaded to a folder of your choosing (/usr/local/src works well) and navigate there in a terminal.
```
tar -xzf spca5xx-20060501.tar.gz
``` or right-click the file and select Extract Here...

Compile the files:

```
sudo make
```

Remove the old spca5xx files:

```
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
```

Install the new files:

```
sudo make install
sudo modprobe spca5xx
```

**Testing**
Whenever you plug your camera in, the green light should light up and typing 
```
dmesg
``` into the console should show the spca5xx module being loaded.

A good program to install in order to test your camera is camorama, it can be installed by typing
```
sudo apt-get install camorama
``` and accessed from the Applications menu under Graphics.

**Comments**
In writing this I borrowed from the Ubuntu wiki page which described installing a version on Breezy at [https://help.ubuntu.com/community/Spca5xx]("https://help.ubuntu.com/community/Spca5xx").  I didn't originally use that page when I figured out how to do this, but it was close enough since I cannot recall which page I used prior.

Hopefully, this has been helpful for anyone trying to get this webcam working, if you have any questions or suggestions post here so I can try to help.

---

### Post by macewan on 2006-08-19
Do you know how to have camorama switch from using /dev/video0 to /dev/video1?

---

### Post by mattyh on 2006-08-20
Taking a quick look at the man pages for camorama ```
man camorama
``` it would appear that ```
camorama -d /dev/video1
``` should do the trick.

---

### Post by macstevejb on 2006-08-21
Hey I just bought this webcam and for the past few days, I've been tearing my hair out trying to get it to work with Ubuntu Dapper LTS 6.06.1.

I just came across your new HOWTO and, after following your instructions, my webcam now works!!!

Just wanted to say, thank you so much MATTYH for your help and sharing your knowledge!

regards

:D

---

### Post by KingFuzz on 2006-08-21
I've been trying to follow this how-to in an attempt to get my webcam working. I'm a complete linux-newbie but at least I didn't get any error-messages while compiling og executing any of the above commands.

When running Camorama i get an error-message saying "Could not connect to video device (/dev/video0)"

I've tried switching camorama to /dev/video1 but no luck..
Any suggestions, you wise men of Ubuntu?

-Christian

---

### Post by mattyh on 2006-08-23
Sorry to take so long to notice your reply.  Plugin your camera, and then type dmesg at the command prompt.  Copy your output here and I'll see what I can do.

---

### Post by Der_Bettler on 2006-08-24
I seem to be stuck.  The fact that I'm quite new probably isn't helping.  I managed to install the packages listed and to extract the files after downloading.  However, when I run the "sudo make" command to compile, I get an error.  It looks something like this:

   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/local/src/webcam/spca5xx-20060501 CC=cc modules
make[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [default] Error 2


I ran the command "sudo chown [my user name] /lib/modules/2.6.15-26-386/build" to make sure I have read/write permissions to that directory.  I did the same for the /kernel directory.  Does anyone have any ideas?

Thanks.

---

### Post by carney1979 on 2006-08-24
lsusb returns:

```
 Bus 003 Device 006: ID 046d:08d9 Logitech, Inc.
``` 
My QuickCam IM won't work.

Camorama starts fine, but the video window has a garbled image of part of my desktop.

Help!

David

---

### Post by mattyh on 2006-08-25
That very well could have something to do with your X11 setup, I wish I could be more helpful :(  Unfortunately I haven't run into any of those issues in my readings.  

As for the ownership issues, I'm a bit confused about why you would have ownership issues if you are using sudo...try sudo make clean in the spca5xx directory and try the directions again is the best advice I can suggest

---

### Post by carney1979 on 2006-08-28
Eurika!

My NEC MultiSync LCD monitor has USB ports (built-in hub) on the side. The USB part is connected to a USB connector on the back of my computer. The webcam was connected to the monitor's USB system as when I had my FC5 Linux system. It worked OK that way, but it won't work that way with Ubuntu Dapper.

On a whim, I disconnected the camera from the monitor's USB port and plugged it in directly to a USB port on the computer.

It works now!

I'm not sure why it wouldn't work the other way, but at this point, I really don't care....It just works _now_.

Thanks to all!

David

---

### Post by Techman010 on 2006-08-28
When I run:
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname-r` build-essential

I get:

E: Couldn't find package linux-restricted-modules

Any suggestions?

I have been using ubuntu\linux for only a month...
thanks

---

### Post by Techman010 on 2006-08-30
I hate bumping with a passion, but it would really be nice if I could maybe get a suggestion.

---

### Post by carney1979 on 2006-08-31
Techman010:

I had the same problem and this is how I solved it. Maybe this will work for you.

The command you mention in my mind should work perfectly but it doesn't always.

I went into a gnome-terminal (or any terminal of your choice) and gave the following command and then hit the enter key:

```
david@n1zhe:~$ uname -r
2.6.15-26-k7
david@n1zhe:~$
``` 
What you get mey very well be different.

I believe I then issued (in my example):

```
 sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-2.6.15-26-k7 build-essential
``` 
It then worked OK for me.

Hope it does for you to. Just substitute whatever the uname -r gives you for 2.6.15-26-k7.

Best to you.

David

---

### Post by mattyh on 2006-09-04
I ran into problems with the ` character as well.  Make sure you aren't using ' (which is a single quote) and instead use `.  That solved my issues.

---

### Post by dullroar on 2006-09-04
Great stuff! I also had been tearing my hair out, but this "just worked" with only one mild alteration. FWIW, I am running Dapper Drake AMD64.

```

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname-r` build-essential
```

The only part that didn't work was the above, and the only part that would not install was linux-restricted-modules for AMD64 (I have every repository I can think of turned on, but perhaps not every one I need?) I took it out and followed everything else step by step and it worked right up through the test with Camarama. Cool.

FWIW, extracting the tar for spca5xx drivers gives an "implausibly old time stamp 1969-12-31 18:00:00", but it goes ahead and extracts everything with no ill effect.

Good job!

---

### Post by molgar on 2006-10-21
Thanks, this howto worked perfectly under Ubuntu Edgy RC1.

---

### Post by gerowen on 2006-10-29
I'm in Edgy, and using a Logitech Quickcam Messenger, and have a couple of questions.

1)  Does this driver work with the Quickcam Messenger.
2)  What is wrong with my camorama?  Whenever I start it I don't even get to see a garbled image, it just gives me an error "Could not connect to video device(/dev/video0)Please check connection."

Help please?

---

### Post by KhaaL on 2006-10-30
I also use a QuickCam Messenger under edgy. I followed this guide: removed the old driver, replaced with the new driver etc. Yet I have no luck in kickstarting my webcam. according to [this site]("http://mxhaard.free.fr/spca5xx.html") QuickCam Messenger also use spca5xx (EDIT: ok, i lied. it uses spca5xx/LE. does it make a diffrence?) chipset so it should work. But in my case, it dosen't.

When i list /dev/v*, I don't see any video links/files. My dmesg:

[17206477.056000] Linux video capture interface: v1.00
[17206477.064000] usbcore: registered new driver spca5xx
[17206477.064000] /usr/local/src/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[17206481.308000] usb 2-4: USB disconnect, address 3
[17206489.676000] usb 2-4: new full speed USB device using ohci_hcd and address 4
[17206489.888000] usb 2-4: configuration #1 chosen from 1 choice


Help will be rewarded with a webcam image of me :mrgreen:

---

### Post by airrazor on 2006-11-03
I'm not sure why guy above didn't answer your question, I was getting the same error with my camera and was wondering if you could help?  This is the output

desktop:~$ dmesg
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fffc000 (usable)
[17179569.184000]  BIOS-e820: 000000003fffc000 - 000000003ffff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262140
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32764 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5e20
[17179569.184000] ACPI: RSDT (v001 ASUS   A7V8X-X  0x42302e31 MSFT 0x31313031) @ 0x3fffc000
[17179569.184000] ACPI: FADT (v001 ASUS   A7V8X-X  0x42302e31 MSFT 0x31313031) @ 0x3fffc0b2
[17179569.184000] ACPI: BOOT (v001 ASUS   A7V8X-X  0x42302e31 MSFT 0x31313031) @ 0x3fffc030
[17179569.184000] ACPI: MADT (v001 ASUS   A7V8X-X  0x42302e31 MSFT 0x31313031) @ 0x3fffc058
[17179569.184000] ACPI: DSDT (v001   ASUS A7V8X-X  0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xe408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1905.505 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.416000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.416000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.448000] Memory: 1028872k/1048560k available (1976k kernel code, 18932k reserved, 606k data, 288k init, 131056k highmem)
[17179569.448000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.528000] Calibrating delay using timer specific routine.. 3814.65 BogoMIPS (lpj=7629316)
[17179569.528000] Security Framework v1.0.0 initialized
[17179569.528000] SELinux:  Disabled at boot.
[17179569.528000] Mount-cache hash table entries: 512
[17179569.528000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.528000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.528000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.528000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.528000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179569.528000] mtrr: v2.0 (20020519)
[17179569.528000] CPU: AMD Athlon(TM) XP 2600+ stepping 00
[17179569.528000] Enabling fast FPU save and restore... done.
[17179569.528000] Enabling unmasked SIMD FPU exception support... done.
[17179569.528000] Checking 'hlt' instruction... OK.
[17179569.544000] checking if image is initramfs... it is
[17179570.092000] Freeing initrd memory: 6614k freed
[17179570.104000] ACPI: Looking for DSDT ... not found!
[17179570.108000] ENABLING IO-APIC IRQs
[17179570.108000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.252000] NET: Registered protocol family 16
[17179570.252000] EISA bus registered
[17179570.252000] ACPI: bus type pci registered
[17179570.252000] PCI: PCI BIOS revision 2.10 entry at 0xf1960, last bus=1
[17179570.252000] PCI: Using configuration type 1
[17179570.252000] ACPI: Subsystem revision 20051216
[17179570.256000] ACPI: Interpreter enabled
[17179570.256000] ACPI: Using IOAPIC for interrupt routing
[17179570.256000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[17179570.256000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12)
[17179570.256000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 9 10 11 12)
[17179570.256000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12)
[17179570.256000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 9 10 11 12)
[17179570.256000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12) *15, disabled.
[17179570.256000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179570.256000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.256000] PCI: Probing PCI hardware (bus 00)
[17179570.260000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.260000] PCI quirk: region e400-e47f claimed by vt8235 PM
[17179570.260000] PCI quirk: region e800-e80f claimed by vt8235 SMB
[17179570.260000] Boot video device is 0000:01:00.0
[17179570.260000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.264000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179570.268000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.268000] pnp: PnP ACPI init
[17179570.268000] pnp: PnP ACPI: found 10 devices
[17179570.268000] PnPBIOS: Disabled by ACPI PNP
[17179570.268000] PCI: Using ACPI for IRQ routing
[17179570.268000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.280000] pnp: 00:01: ioport range 0xe400-0xe47f could not be reserved
[17179570.280000] pnp: 00:01: ioport range 0xe800-0xe81f could not be reserved
[17179570.280000] pnp: 00:09: ioport range 0x290-0x297 has been reserved
[17179570.280000] pnp: 00:09: ioport range 0x370-0x375 has been reserved
[17179570.280000] PCI: Bridge: 0000:00:01.0
[17179570.280000]   IO window: d000-dfff
[17179570.280000]   MEM window: d7000000-d7ffffff
[17179570.280000]   PREFETCH window: d8000000-efffffff
[17179570.280000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.280000] Simple Boot Flag at 0x3a set to 0x1
[17179570.280000] audit: initializing netlink socket (disabled)
[17179570.280000] audit(1162563535.280:1): initialized
[17179570.280000] highmem bounce pool size: 64 pages
[17179570.280000] VFS: Disk quotas dquot_6.5.1
[17179570.280000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.280000] Initializing Cryptographic API
[17179570.280000] io scheduler noop registered
[17179570.280000] io scheduler anticipatory registered
[17179570.280000] io scheduler deadline registered
[17179570.280000] io scheduler cfq registered
[17179570.280000] isapnp: Scanning for PnP cards...
[17179570.632000] isapnp: No Plug & Play device found
[17179570.644000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.644000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179570.652000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.652000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.652000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.652000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.652000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.652000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.652000] mice: PS/2 mouse device common for all mice
[17179570.652000] EISA: Probing bus 0 at eisa.0
[17179570.652000] EISA: Detected 0 cards.
[17179570.656000] NET: Registered protocol family 2
[17179570.696000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.708000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.708000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179570.708000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.708000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.708000] TCP reno registered
[17179570.708000] TCP bic registered
[17179570.708000] NET: Registered protocol family 1
[17179570.708000] NET: Registered protocol family 8
[17179570.708000] NET: Registered protocol family 20
[17179570.708000] Using IPI Shortcut mode
[17179570.708000] ACPI wakeup devices:
[17179570.708000] PCI0 PCI1 USB0 USB1 USB2 SU20 SLAN
[17179570.708000] ACPI: (supports S0 S1 S4 S5)
[17179570.708000] Freeing unused kernel memory: 288k freed
[17179570.756000] vga16fb: initializing
[17179570.756000] vga16fb: mapped to 0xc00a0000
[17179570.848000] Console: switching to colour frame buffer device 80x25
[17179570.848000] fb0: VGA16 VGA frame buffer device
[17179571.868000] Capability LSM initialized
[17179572.372000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179572.372000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179572.372000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[17179572.372000] VP_IDE: chipset revision 6
[17179572.372000] VP_IDE: not 100% native mode: will probe irqs later
[17179572.372000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179572.372000]     ide0: BM-DMA at 0xa000-0xa007, BIOS settings: hda:DMA, hdb:DMA
[17179572.372000]     ide1: BM-DMA at 0xa008-0xa00f, BIOS settings: hdc:DMA, hdd:DMA
[17179572.372000] Probing IDE interface ide0...
[17179572.900000] hda: HL-DT-ST RW/DVD GCC-4521B, ATAPI CD/DVD-ROM drive
[17179573.180000] hdb: Maxtor 2F030L0, ATA DISK drive
[17179573.236000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.256000] Probing IDE interface ide1...
[17179573.788000] hdc: HL-DT-ST DVDRAM GSA-H10A, ATAPI CD/DVD-ROM drive
[17179574.068000] hdd: Maxtor 6E040L0, ATA DISK drive
[17179574.124000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.148000] hda: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.148000] Uniform CD-ROM driver Revision: 3.20
[17179574.152000] hdb: max request size: 128KiB
[17179574.152000] hdb: 60058656 sectors (30750 MB) w/2048KiB Cache, CHS=59582/16/63, UDMA(133)
[17179574.152000] hdb: cache flushes supported
[17179574.152000]  hdb:<6>hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.164000]  hdb1 hdb2 < hdb5 >
[17179574.228000] hdd: max request size: 128KiB
[17179574.228000] hdd: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179574.228000] hdd: cache flushes supported
[17179574.228000]  hdd: hdd1
[17179574.460000] usbcore: registered new driver usbfs
[17179574.460000] usbcore: registered new driver hub
[17179574.460000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179574.460000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179574.460000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[17179574.464000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[17179574.464000] ohci_hcd 0000:00:0b.0: irq 169, io mem 0xd6800000
[17179574.496000] USB Universal Host Controller Interface driver v2.3
[17179574.520000] hub 1-0:1.0: USB hub found
[17179574.520000] hub 1-0:1.0: 2 ports detected
[17179574.528000] ieee1394: Initialized config rom entry `ip1394'
[17179574.624000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 177
[17179574.624000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 1
[17179574.624000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179574.624000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[17179574.624000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000b000
[17179574.624000] hub 2-0:1.0: USB hub found
[17179574.624000] hub 2-0:1.0: 2 ports detected
[17179574.624000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179574.624000] ACPI: PCI Interrupt 0000:00:0e.2[B] -> GSI 18 (level, low) -> IRQ 185
[17179574.672000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185]  MMIO=[d6000000-d60007ff]  Max Packet=[2048]
[17179574.728000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 177
[17179574.728000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 1
[17179574.728000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179574.728000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[17179574.728000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000a800
[17179574.728000] hub 3-0:1.0: USB hub found
[17179574.728000] hub 3-0:1.0: 2 ports detected
[17179574.832000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 177
[17179574.832000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 1
[17179574.832000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179574.832000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[17179574.832000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000a400
[17179574.832000] hub 4-0:1.0: USB hub found
[17179574.832000] hub 4-0:1.0: 2 ports detected
[17179574.936000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 177
[17179574.936000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 1
[17179574.936000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179574.936000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[17179574.936000] ehci_hcd 0000:00:10.3: irq 177, io mem 0xd5000000
[17179574.936000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.936000] hub 5-0:1.0: USB hub found
[17179574.936000] hub 5-0:1.0: 6 ports detected
[17179574.968000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179575.092000] Attempting manual resume
[17179575.100000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179575.100000] EXT3-fs: write access will be enabled during recovery.
[17179575.944000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c01510d9bd3]
[17179576.280000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[17179576.700000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[17179576.844000] usbcore: registered new driver hiddev
[17179576.860000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input1
[17179576.860000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-1
[17179576.860000] usbcore: registered new driver usbhid
[17179576.860000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179586.128000] EXT3-fs: hdb1: orphan cleanup on readonly fs
[17179586.128000] ext3_orphan_cleanup: deleting unreferenced inode 1144643
[17179586.128000] EXT3-fs: hdb1: 1 orphan inode deleted
[17179586.128000] EXT3-fs: recovery complete.
[17179586.128000] kjournald starting.  Commit interval 5 seconds
[17179586.144000] EXT3-fs: mounted filesystem with ordered data mode.
[17179595.676000] ts: Compaq touchscreen protocol output
[17179597.232000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.232000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179597.240000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179597.244000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.256000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.548000] gameport: EMU10K1 is pci0000:00:0e.1/gameport0, io 0xb400, speed 1269kHz
[17179598.020000] irda_init()
[17179598.020000] NET: Registered protocol family 23
[17179598.068000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 193
[17179598.068000] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[17179598.120000] input: PC Speaker as /class/input/input2
[17179598.156000] Real Time Clock Driver v1.12
[17179598.240000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179598.240000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 201
[17179598.240000] PCI: Via IRQ fixup for 0000:00:12.0, from 0 to 9
[17179598.240000] eth0: VIA Rhine II at 0x19800, 00:0c:6e:9a:4a:5b, IRQ 201.
[17179598.240000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[17179598.388000] Floppy drive(s): fd0 is 1.44M
[17179598.448000] FDC 0 is a post-1991 82077
[17179599.468000] usbcore: registered new driver snd-usb-audio
[17179599.496000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179599.908000] lp: driver loaded but no devices found
[17179599.988000] SCSI subsystem initialized
[17179600.000000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179600.000000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179600.000000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179600.072000] Adding 1253028k swap on /dev/hdb5.  Priority:-1 extents:1 across:1253028k
[17179600.204000] EXT3 FS on hdb1, internal journal
[17179600.460000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179600.460000] md: bitmap version 4.39
[17179600.528000] NET: Registered protocol family 17
[17179601.016000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179601.268000] cdrom: open failed.
[17179601.752000] cdrom: open failed.
[17179601.764000] cdrom: open failed.
[17179603.376000] NET: Registered protocol family 10
[17179603.376000] lo: Disabled Privacy Extensions
[17179603.376000] IPv6 over IPv4 tunneling driver
[17179609.664000] ACPI: Power Button (FF) [PWRF]
[17179609.664000] ACPI: Power Button (CM) [PWRB]
[17179609.764000] ibm_acpi: ec object not found
[17179609.796000] pcc_acpi: loading...
[17179612.872000] ppdev: user-space parallel port driver
[17179613.456000] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[17179613.456000] apm: overridden by ACPI.
[17179614.184000] eth0: no IPv6 routers present
[17179619.780000] Bluetooth: Core ver 2.8
[17179619.780000] NET: Registered protocol family 31
[17179619.780000] Bluetooth: HCI device and connection manager initialized
[17179619.780000] Bluetooth: HCI socket layer initialized
[17179619.840000] Bluetooth: L2CAP ver 2.8
[17179619.840000] Bluetooth: L2CAP socket layer initialized
[17179619.844000] Bluetooth: RFCOMM socket layer initialized
[17179619.844000] Bluetooth: RFCOMM TTY layer initialized
[17179619.844000] Bluetooth: RFCOMM ver 1.7
[17179624.096000] [drm] Initialized drm 1.0.1 20051102
[17179624.108000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179624.108000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179625.160000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179625.160000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179625.160000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179641.536000] [drm] Setting GART location based on new memory map
[17179641.536000] [drm] Loading R300 Microcode
[17179641.536000] [drm] writeback test succeeded in 1 usecs
[17180298.220000] usb 2-2: USB disconnect, address 4
[17189864.680000] Linux video capture interface: v1.00
[17190269.392000] usbcore: registered new driver quickcam
[17190269.848000] usb 2-2: new full speed USB device using uhci_hcd and address 5
[17190270.812000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17190270.812000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17190270.812000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17190271.088000] [drm] Setting GART location based on new memory map
[17190271.088000] [drm] Loading R300 Microcode
[17190271.088000] [drm] writeback test succeeded in 1 usecs
[17190729.916000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17190729.916000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17190729.916000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17190730.192000] [drm] Setting GART location based on new memory map
[17190730.192000] [drm] Loading R300 Microcode
[17190730.192000] [drm] writeback test succeeded in 1 usecs
[17207845.376000] usbcore: registered new driver spca5xx
[17207845.376000] /usr/local/src/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered

Thanks in advance

---

### Post by Hanzerik on 2007-01-09
Thanks Matth, was getting worried about this cam, your instructions worked great. The only thing I didn't do was install the restricted modules for my kernel, the `uname -r` portion of that apt-get command didn't work for the modules for the server kernel, but worked for the headers. I already had the build-essential installed. 

I had a QuickCam express running before, but it would mess up during bright sunlight. I use my Web Cam for streaming video of my back yard.

[http://hanzerik.no-ip.org/campics/](http://hanzerik.no-ip.org/campics/)

It was dark when I set this new camera up, so it probably needs to be adjusted come daylight.

---

### Post by duojet on 2007-03-01
oddly enough the problem I'm running into is this:

isaac@box:~/Desktop/spca5xx-20060501$ sudo make
sudo: make: command not found

anybody know what I'm not doing right?
I'm using kubuntu dapper

---

### Post by rajesh243 on 2007-03-03
i purchased Logitech camera and was trying to make it work in Dapper(worked iin Edgy).
your post was really helpfull and it worked 

thanks :)
Rajesh
[http://sabrenews.blogspot.com](http://sabrenews.blogspot.com)
[http://techpicks.blogspot.com](http://techpicks.blogspot.com)

---

### Post by subhash on 2007-04-17
> **mattyh said:**
> Sorry to take so long to notice your reply.  Plugin your camera, and then type dmesg at the command prompt.  Copy your output here and I'll see what I can do.

i am having problem with camorama
"could not connect to device(/dev/video)"
there is no such file or folder in dev

i hv installed spca5xx 
i hv follwed all steps it worked fine
bt when i srated camorama it gave error

plz smbody help me
i am running into serious problem

[4294948.695000] end_request: I/O error, dev hda, sector 216
[4294948.784000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294948.784000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294948.784000] ide: failed opcode was: unknown
[4294948.784000] end_request: I/O error, dev hda, sector 220
[4294948.872000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294948.872000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294948.872000] ide: failed opcode was: unknown
[4294948.872000] end_request: I/O error, dev hda, sector 224
[4294948.960000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294948.960000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294948.960000] ide: failed opcode was: unknown
[4294948.960000] end_request: I/O error, dev hda, sector 228
[4294949.048000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.048000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.048000] ide: failed opcode was: unknown
[4294949.048000] end_request: I/O error, dev hda, sector 232
[4294949.136000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.136000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.136000] ide: failed opcode was: unknown
[4294949.136000] end_request: I/O error, dev hda, sector 236
[4294949.224000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.224000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.224000] ide: failed opcode was: unknown
[4294949.224000] end_request: I/O error, dev hda, sector 240
[4294949.313000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.313000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.313000] ide: failed opcode was: unknown
[4294949.313000] end_request: I/O error, dev hda, sector 244
[4294949.401000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.401000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.401000] ide: failed opcode was: unknown
[4294949.401000] end_request: I/O error, dev hda, sector 248
[4294949.489000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.489000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.489000] ide: failed opcode was: unknown
[4294949.489000] end_request: I/O error, dev hda, sector 252
[4294949.577000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.577000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.577000] ide: failed opcode was: unknown
[4294949.577000] end_request: I/O error, dev hda, sector 256
[4294949.665000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.665000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.665000] ide: failed opcode was: unknown
[4294949.665000] end_request: I/O error, dev hda, sector 260
[4294949.756000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.756000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.756000] ide: failed opcode was: unknown
[4294949.756000] end_request: I/O error, dev hda, sector 0
[4294949.844000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4294949.844000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294949.844000] ide: failed opcode was: unknown
[4294949.844000] end_request: I/O error, dev hda, sector 4
[4296377.333000] Linux video capture interface: v1.00
[4296377.337000] usbcore: registered new driver spca5xx
[4296377.337000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[4296651.668000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4298159.621000] usbcore: deregistering driver spca5xx
[4298159.621000] /usr/src/spca5xx-20060501/drivers/usb/spca5xx.c: driver spca5xx deregistered
[4298159.655000] spca5xx: version magic '2.6.15-23-386 preempt 486 gcc-3.4' should be '2.6.15-23-386 preempt 486 gcc-4.0'
[4298159.662000] Linux video capture interface: v1.00
[4298159.663000] spca5xx: version magic '2.6.15-23-386 preempt 486 gcc-3.4' should be '2.6.15-23-386 preempt 486 gcc-4.0'
[4298872.579000] spca5xx: version magic '2.6.15-23-386 preempt 486 gcc-3.4' should be '2.6.15-23-386 preempt 486 gcc-4.0'
[4298872.586000] Linux video capture interface: v1.00
[4298872.586000] spca5xx: version magic '2.6.15-23-386 preempt 486 gcc-3.4' should be '2.6.15-23-386 preempt 486 gcc-4.0'
[4298942.206000] Linux video capture interface: v1.00
[4298942.210000] usbcore: registered new driver ov511
[4298942.210000] /usr/share/EasyWebcam/ov511-2.30/ov511_core.c: v2.30 : ov511 USB Camera Driver (V4L2 disabled)
[4299059.732000] usbcore: deregistering driver ov511
[4299059.732000] /usr/share/EasyWebcam/ov511-2.30/ov511_core.c: driver deregistered
[4299060.098000] Linux video capture interface: v1.00
[4299060.100000] usbcore: registered new driver ov511
[4299060.100000] /usr/share/EasyWebcam/ov511-2.30/ov511_core.c: v2.30 : ov511 USB Camera Driver (V4L2 disabled)
[4299151.970000] usbcore: deregistering driver ov511
[4299151.970000] /usr/share/EasyWebcam/ov511-2.30/ov511_core.c: driver deregistered
[4299152.042000] Linux video capture interface: v1.00
[4299152.044000] usbcore: registered new driver ov511
[4299152.044000] /usr/share/EasyWebcam/ov511-2.30/ov511_core.c: v2.30 : ov511 USB Camera Driver (V4L2 disabled)
[4299198.139000] usbcore: deregistering driver ov511
[4299198.140000] /usr/share/EasyWebcam/ov511-2.30/ov511_core.c: driver deregistered
[4299198.247000] Linux video capture interface: v1.00
[4299198.249000] usbcore: registered new driver ov511
[4299198.249000] /usr/share/EasyWebcam/ov511-2.30/ov511_core.c: v2.30 : ov511 USB Camera Driver (V4L2 disabled)
[4299246.845000] pwc Philips webcam module version 10.0.6-unofficial loaded.
[4299246.845000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[4299246.845000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[4299246.845000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[4299246.845000] pwc Trace options: 0x00a1
[4299246.846000] usbcore: registered new driver Philips webcam
[4299660.327000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299660.327000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299660.327000] ide: failed opcode was: unknown
[4299660.327000] end_request: I/O error, dev hda, sector 64
[4299660.327000] printk: 28 messages suppressed.
[4299660.327000] Buffer I/O error on device hda, logical block 16
[4299660.417000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299660.417000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299660.417000] ide: failed opcode was: unknown
[4299660.417000] end_request: I/O error, dev hda, sector 68
[4299660.417000] Buffer I/O error on device hda, logical block 17
[4299662.484000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299662.484000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299662.484000] ide: failed opcode was: unknown
[4299662.484000] end_request: I/O error, dev hda, sector 64
[4299662.484000] Buffer I/O error on device hda, logical block 16
[4299662.547000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299662.547000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299662.547000] ide: failed opcode was: unknown
[4299662.547000] end_request: I/O error, dev hda, sector 68
[4299662.547000] Buffer I/O error on device hda, logical block 17
[4299664.328000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299664.328000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299664.328000] ide: failed opcode was: unknown
[4299664.328000] end_request: I/O error, dev hda, sector 0
[4299664.328000] Buffer I/O error on device hda, logical block 0
[4299664.397000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299664.397000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299664.397000] ide: failed opcode was: unknown
[4299664.397000] end_request: I/O error, dev hda, sector 4
[4299664.397000] Buffer I/O error on device hda, logical block 1
[4299664.854000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299664.854000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299664.854000] ide: failed opcode was: unknown
[4299664.854000] end_request: I/O error, dev hda, sector 0
[4299664.854000] Buffer I/O error on device hda, logical block 0
[4299664.911000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299664.911000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299664.911000] ide: failed opcode was: unknown
[4299664.911000] end_request: I/O error, dev hda, sector 4
[4299664.911000] Buffer I/O error on device hda, logical block 1
[4299665.167000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299665.167000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299665.167000] ide: failed opcode was: unknown
[4299665.167000] end_request: I/O error, dev hda, sector 0
[4299665.167000] Buffer I/O error on device hda, logical block 0
[4299665.236000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299665.237000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299665.237000] ide: failed opcode was: unknown
[4299665.237000] end_request: I/O error, dev hda, sector 4
[4299665.237000] Buffer I/O error on device hda, logical block 1
[4299666.269000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299666.269000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299666.269000] ide: failed opcode was: unknown
[4299666.269000] end_request: I/O error, dev hda, sector 0
[4299666.269000] Buffer I/O error on device hda, logical block 0
[4299666.339000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299666.339000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299666.339000] ide: failed opcode was: unknown
[4299666.339000] end_request: I/O error, dev hda, sector 4
[4299666.609000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299666.609000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299666.609000] ide: failed opcode was: unknown
[4299666.609000] end_request: I/O error, dev hda, sector 8
[4299666.678000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299666.678000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299666.678000] ide: failed opcode was: unknown
[4299666.678000] end_request: I/O error, dev hda, sector 12
[4299667.073000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299667.073000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299667.073000] ide: failed opcode was: unknown
[4299667.073000] end_request: I/O error, dev hda, sector 16
[4299667.656000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299667.656000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299667.656000] ide: failed opcode was: unknown
[4299667.656000] end_request: I/O error, dev hda, sector 20
[4299667.713000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299667.713000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299667.713000] ide: failed opcode was: unknown
[4299667.713000] end_request: I/O error, dev hda, sector 24
[4299668.077000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299668.077000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299668.077000] ide: failed opcode was: unknown
[4299668.077000] end_request: I/O error, dev hda, sector 28
[4299668.128000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299668.128000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299668.128000] ide: failed opcode was: unknown
[4299668.128000] end_request: I/O error, dev hda, sector 32
[4299668.197000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299668.197000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299668.197000] ide: failed opcode was: unknown
[4299668.197000] end_request: I/O error, dev hda, sector 36
[4299668.367000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299668.367000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299668.367000] ide: failed opcode was: unknown
[4299668.367000] end_request: I/O error, dev hda, sector 40
[4299668.430000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299668.430000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299668.430000] ide: failed opcode was: unknown
[4299668.430000] end_request: I/O error, dev hda, sector 44
[4299668.788000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299668.788000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299668.788000] ide: failed opcode was: unknown
[4299668.788000] end_request: I/O error, dev hda, sector 48
[4299668.845000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299668.845000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299668.845000] ide: failed opcode was: unknown
[4299668.845000] end_request: I/O error, dev hda, sector 52
[4299669.328000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299669.328000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299669.328000] ide: failed opcode was: unknown
[4299669.328000] end_request: I/O error, dev hda, sector 56
[4299669.623000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299669.623000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299669.623000] ide: failed opcode was: unknown
[4299669.623000] end_request: I/O error, dev hda, sector 60
[4299669.718000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299669.718000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299669.718000] ide: failed opcode was: unknown
[4299669.718000] end_request: I/O error, dev hda, sector 64
[4299670.063000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299670.063000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299670.063000] ide: failed opcode was: unknown
[4299670.063000] end_request: I/O error, dev hda, sector 68
[4299670.139000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299670.139000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299670.139000] ide: failed opcode was: unknown
[4299670.139000] end_request: I/O error, dev hda, sector 0
[4299670.297000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299670.297000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299670.297000] ide: failed opcode was: unknown
[4299670.297000] end_request: I/O error, dev hda, sector 4
[4299670.377000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299670.377000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299670.377000] ide: failed opcode was: unknown
[4299670.377000] end_request: I/O error, dev hda, sector 0
[4299670.377000] printk: 19 messages suppressed.
[4299670.377000] Buffer I/O error on device hda, logical block 0
[4299670.660000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299670.660000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299670.660000] ide: failed opcode was: unknown
[4299670.660000] end_request: I/O error, dev hda, sector 4
[4299670.734000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299670.734000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299670.734000] ide: failed opcode was: unknown
[4299670.734000] end_request: I/O error, dev hda, sector 0
[4299671.186000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299671.186000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299671.186000] ide: failed opcode was: unknown
[4299671.186000] end_request: I/O error, dev hda, sector 4
[4299671.254000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299671.254000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299671.254000] ide: failed opcode was: unknown
[4299671.254000] end_request: I/O error, dev hda, sector 0
[4299671.549000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299671.549000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299671.549000] ide: failed opcode was: unknown
[4299671.549000] end_request: I/O error, dev hda, sector 4
[4299671.605000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299671.605000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299671.605000] ide: failed opcode was: unknown
[4299671.605000] end_request: I/O error, dev hda, sector 0
[4299671.994000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299671.994000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299671.994000] ide: failed opcode was: unknown
[4299671.994000] end_request: I/O error, dev hda, sector 4
[4299672.049000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299672.049000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299672.049000] ide: failed opcode was: unknown
[4299672.049000] end_request: I/O error, dev hda, sector 0
[4299672.225000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299672.225000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299672.225000] ide: failed opcode was: unknown
[4299672.225000] end_request: I/O error, dev hda, sector 4
[4299672.594000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299672.594000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299672.594000] ide: failed opcode was: unknown
[4299672.594000] end_request: I/O error, dev hda, sector 0
[4299672.645000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299672.645000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299672.645000] ide: failed opcode was: unknown
[4299672.645000] end_request: I/O error, dev hda, sector 4
[4299672.693000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299672.693000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299672.693000] ide: failed opcode was: unknown
[4299672.693000] end_request: I/O error, dev hda, sector 72
[4299673.145000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299673.145000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299673.145000] ide: failed opcode was: unknown
[4299673.145000] end_request: I/O error, dev hda, sector 76
[4299673.233000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299673.233000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299673.233000] ide: failed opcode was: unknown
[4299673.233000] end_request: I/O error, dev hda, sector 80
[4299673.710000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299673.710000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299673.710000] ide: failed opcode was: unknown
[4299673.710000] end_request: I/O error, dev hda, sector 84
[4299673.785000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299673.785000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299673.785000] ide: failed opcode was: unknown
[4299673.785000] end_request: I/O error, dev hda, sector 88
[4299674.168000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299674.168000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299674.168000] ide: failed opcode was: unknown
[4299674.168000] end_request: I/O error, dev hda, sector 92
[4299674.557000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299674.557000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299674.557000] ide: failed opcode was: unknown
[4299674.557000] end_request: I/O error, dev hda, sector 96
[4299674.627000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299674.627000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299674.627000] ide: failed opcode was: unknown
[4299674.627000] end_request: I/O error, dev hda, sector 100
[4299676.134000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.134000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.134000] ide: failed opcode was: unknown
[4299676.134000] end_request: I/O error, dev hda, sector 104
[4299676.134000] printk: 19 messages suppressed.
[4299676.134000] Buffer I/O error on device hda, logical block 26
[4299676.221000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.221000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.221000] ide: failed opcode was: unknown
[4299676.221000] end_request: I/O error, dev hda, sector 108
[4299676.309000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.309000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.309000] ide: failed opcode was: unknown
[4299676.309000] end_request: I/O error, dev hda, sector 112
[4299676.397000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.397000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.397000] ide: failed opcode was: unknown
[4299676.397000] end_request: I/O error, dev hda, sector 116
[4299676.484000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.484000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.484000] ide: failed opcode was: unknown
[4299676.484000] end_request: I/O error, dev hda, sector 120
[4299676.572000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.572000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.572000] ide: failed opcode was: unknown
[4299676.572000] end_request: I/O error, dev hda, sector 124
[4299676.660000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.660000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.660000] ide: failed opcode was: unknown
[4299676.660000] end_request: I/O error, dev hda, sector 128
[4299676.748000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.748000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.748000] ide: failed opcode was: unknown
[4299676.748000] end_request: I/O error, dev hda, sector 132
[4299676.836000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.836000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.836000] ide: failed opcode was: unknown
[4299676.836000] end_request: I/O error, dev hda, sector 136
[4299676.925000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299676.925000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299676.925000] ide: failed opcode was: unknown
[4299676.925000] end_request: I/O error, dev hda, sector 140
[4299677.013000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.013000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.013000] ide: failed opcode was: unknown
[4299677.013000] end_request: I/O error, dev hda, sector 144
[4299677.101000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.101000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.101000] ide: failed opcode was: unknown
[4299677.101000] end_request: I/O error, dev hda, sector 148
[4299677.189000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.189000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.189000] ide: failed opcode was: unknown
[4299677.189000] end_request: I/O error, dev hda, sector 152
[4299677.277000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.277000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.277000] ide: failed opcode was: unknown
[4299677.277000] end_request: I/O error, dev hda, sector 156
[4299677.365000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.365000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.365000] ide: failed opcode was: unknown
[4299677.365000] end_request: I/O error, dev hda, sector 160
[4299677.453000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.453000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.453000] ide: failed opcode was: unknown
[4299677.453000] end_request: I/O error, dev hda, sector 164
[4299677.541000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.541000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.541000] ide: failed opcode was: unknown
[4299677.541000] end_request: I/O error, dev hda, sector 168
[4299677.629000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.629000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.629000] ide: failed opcode was: unknown
[4299677.629000] end_request: I/O error, dev hda, sector 172
[4299677.717000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.717000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.717000] ide: failed opcode was: unknown
[4299677.717000] end_request: I/O error, dev hda, sector 176
[4299677.805000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.805000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.805000] ide: failed opcode was: unknown
[4299677.805000] end_request: I/O error, dev hda, sector 180
[4299677.893000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.893000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.893000] ide: failed opcode was: unknown
[4299677.893000] end_request: I/O error, dev hda, sector 184
[4299677.981000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299677.981000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299677.981000] ide: failed opcode was: unknown
[4299677.981000] end_request: I/O error, dev hda, sector 188
[4299678.069000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.069000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.069000] ide: failed opcode was: unknown
[4299678.069000] end_request: I/O error, dev hda, sector 192
[4299678.157000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.157000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.157000] ide: failed opcode was: unknown
[4299678.157000] end_request: I/O error, dev hda, sector 196
[4299678.245000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.245000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.245000] ide: failed opcode was: unknown
[4299678.245000] end_request: I/O error, dev hda, sector 200
[4299678.333000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.333000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.333000] ide: failed opcode was: unknown
[4299678.333000] end_request: I/O error, dev hda, sector 204
[4299678.421000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.421000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.421000] ide: failed opcode was: unknown
[4299678.421000] end_request: I/O error, dev hda, sector 208
[4299678.509000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.509000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.509000] ide: failed opcode was: unknown
[4299678.509000] end_request: I/O error, dev hda, sector 212
[4299678.597000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.597000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.597000] ide: failed opcode was: unknown
[4299678.597000] end_request: I/O error, dev hda, sector 216
[4299678.685000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.685000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.685000] ide: failed opcode was: unknown
[4299678.685000] end_request: I/O error, dev hda, sector 220
[4299678.773000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.773000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.773000] ide: failed opcode was: unknown
[4299678.773000] end_request: I/O error, dev hda, sector 224
[4299678.861000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.861000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.861000] ide: failed opcode was: unknown
[4299678.861000] end_request: I/O error, dev hda, sector 228
[4299678.950000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299678.950000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299678.950000] ide: failed opcode was: unknown
[4299678.950000] end_request: I/O error, dev hda, sector 232
[4299679.038000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.038000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.038000] ide: failed opcode was: unknown
[4299679.038000] end_request: I/O error, dev hda, sector 236
[4299679.126000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.126000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.126000] ide: failed opcode was: unknown
[4299679.126000] end_request: I/O error, dev hda, sector 240
[4299679.214000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.214000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.214000] ide: failed opcode was: unknown
[4299679.214000] end_request: I/O error, dev hda, sector 244
[4299679.302000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.302000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.302000] ide: failed opcode was: unknown
[4299679.302000] end_request: I/O error, dev hda, sector 248
[4299679.390000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.390000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.390000] ide: failed opcode was: unknown
[4299679.390000] end_request: I/O error, dev hda, sector 252
[4299679.478000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.478000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.478000] ide: failed opcode was: unknown
[4299679.478000] end_request: I/O error, dev hda, sector 256
[4299679.566000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.566000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.566000] ide: failed opcode was: unknown
[4299679.566000] end_request: I/O error, dev hda, sector 260
[4299679.657000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.657000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.657000] ide: failed opcode was: unknown
[4299679.657000] end_request: I/O error, dev hda, sector 0
[4299679.745000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[4299679.745000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4299679.745000] ide: failed opcode was: unknown
[4299679.745000] end_request: I/O error, dev hda, sector 4
[4299700.462000] usb 1-1: USB disconnect, address 2
[4299704.263000] usb 5-1: new high speed USB device using ehci_hcd and address 4
[4299704.656000] Initializing USB Mass Storage driver...
[4299704.656000] scsi2 : SCSI emulation for USB Mass Storage devices
[4299704.656000] usb-storage: device found at 4
[4299704.656000] usb-storage: waiting for device to settle before scanning
[4299704.656000] usbcore: registered new driver usb-storage
[4299704.656000] USB Mass Storage support registered.
[4299709.657000]   Vendor: JetFlash  Model: TS512MJF110       Rev: 0.00
[4299709.657000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4299709.658000] SCSI device sdb: 1024000 512-byte hdwr sectors (524 MB)
[4299709.659000] sdb: Write Protect is off
[4299709.659000] sdb: Mode Sense: 00 00 00 00
[4299709.659000] sdb: assuming drive cache: write through
[4299709.661000] SCSI device sdb: 1024000 512-byte hdwr sectors (524 MB)
[4299709.661000] sdb: Write Protect is off
[4299709.661000] sdb: Mode Sense: 00 00 00 00
[4299709.661000] sdb: assuming drive cache: write through
[4299709.661000]  sdb: sdb1
[4299709.733000] sd 2:0:0:0: Attached scsi removable disk sdb
[4299709.733000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[4299709.734000] usb-storage: device scan complete
[4299710.663000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4299723.807000] usb 5-1: USB disconnect, address 4
[4299723.885000]  2:0:0:0: rejecting I/O to dead device
[4299723.885000] FAT: bread failed in fat_clusters_flush
subhash@subhash-desktop:~$

---

