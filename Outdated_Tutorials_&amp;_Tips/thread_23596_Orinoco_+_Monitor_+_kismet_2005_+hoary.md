---
title: "Orinoco + Monitor + kismet_2005 +hoary"
date: 2005-04-02
forum: Outdated Tutorials &amp; Tips
---

### Post by jshein on 2005-04-02
**2005-10-19  Breezy 5.10 driections are here [http://ubuntuforums.org/showthread.php?p=427388#post427388](http://ubuntuforums.org/showthread.php?p=427388#post427388)**

I posted this earlier on another thread. But felt that after all the hassles I went through to get this to work, others should not have to do the same.

I am running with universe sources enabled in /etc/apt/sources.list

All commands need to be done as root. To do this type this in the regular terminal:

sudo -s

Install kismet 
> wget [http://mirror.aarnet.edu.au/debian/pool/main/k/kismet/kismet_2005.04.R1-1_i386.deb](http://mirror.aarnet.edu.au/debian/pool/main/k/kismet/kismet_2005.04.R1-1_i386.deb)
apt-get install ethereal-common
dpkg -i kismet_2005.04.R1-1_i386.deb 


Install the kernel sources
> apt-get install linux-source-2.6.10 build-essential 

go to the /usr/src directory
> cd /usr/src 

extract the kernel-source
> bunzip2 linux-source-2.6.10.tar.bz2
tar -xvf linux-source-2.6.10.tar 

make a link to the kernel source
> ln -s /usr/src/linux-source-2.6.10 /usr/src/linux 

cd to the source dir
> cd /usr/src/linux 

get the monitor mode patch
> wget [http://www.kismetwireless.net/code/orinoco-2.6.9-rfmon-dragorn-1.diff](http://www.kismetwireless.net/code/orinoco-2.6.9-rfmon-dragorn-1.diff) 

(Note: copying this from the forum directly will result in a truncated address that will not work. Copy the link instead.)

patch the kernel-source
> patch -p1 --dry-run < ./orinoco-2.6.9-rfmon-dragorn-1.diff 

and if no errors appear
> patch -p1 < ./orinoco-2.6.9-rfmon-dragorn-1.diff 

Make a directory to backup the existing drivers.
> mkdir /orinoco 

Move orinoco drivers to backup location
> mv /lib/modules/2.6.10/kernel/drivers/net/wireless/orinoco* /orinoco
mv /lib/modules/2.6.10/kernel/drivers/net/wireless/hermes.ko /orinoco 

If you are using an Apple airport card, you must do this to:
> mv /lib/modules/2.6.10/kernel/drivers/net/wireless/airport.ko /orinoco 

copy the config file to the source directory
> cp /boot/config-2.6.10-5-386 /usr/src/linux/.config 

(Replace 386 with 686 and powerpc if that is what kernal you are using).

compile the modules
> make modules
make modules_install 

copy the new modules to the proper directory
> cp /usr/src/linux/drivers/net/wireless/orinoco*ko /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/
cp /usr/src/linux/drivers/net/wireless/hermes.ko /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ 

(Replace 386 with 686 and powerpc if that is what kernal you are using).

If you are using an Apple airport card, you must do this to:
> 
cp /usr/src/linux/drivers/net/wireless/airport.ko /lib/modules/2.6.10-5-powerpc/kernel/drivers/net/wireless/ 

edit /etc/kismet/kismet.conf for your card

> gedit /etc/kismet/kismet.conf

use > orinoco,eth1,orinocosource

comment out all others.

Insert your card, wait a few seconds, and stop the card with:
> sudo ifdown eth1    ( if you omit this step kismet crashes every time after about 5 seconds )


enjoy

---

### Post by poofyhairguy on 2005-04-08
[QUOTE=jshein]I posted this earlier on another thread. But felt that after all the hassles I went through to get this to work, others should not have to do the same.

I am running with universe sources enabled in /etc/apt/sources.list

All commands need to be done as root

Install kismet
# wget [http://mirror.aarnet.edu.au/debian/pool/main/k/kismet/kismet_2005.01.R1-2_i386.deb](http://mirror.aarnet.edu.au/debian/pool/main/k/kismet/kismet_2005.01.R1-2_i386.deb)
# apt-get install ethereal-common
# dpkg -i kismet_2005.01.R1-2_i386.deb

Install the kernel sources
# apt-get install linux-source-2.6.10

go to the /usr/src directory
# cd /usr/src

extract the kernel-source
# bunzip2 linux-source-2.6.10.tar.bz2
# tar -xvf linux-source-2.6.10.tar

make a link to the kernel source
# ln -s /usr/src/linux-source-2.6.10 /usr/src/linux

cd to the source dir
# cd /usr/src/linux

get the monitor mode patch
# wget [http://www.kismetwireless.net/code/orinoco-2.6.9-rfmon-dragorn-1.diff](http://www.kismetwireless.net/code/orinoco-2.6.9-rfmon-dragorn-1.diff)

patch the kernel-source
# patch -p1 --dry-run < ./orinoco-2.6.9-rfmon-dragorn-1.diff

and if no errors appear
# patch -p1 < ./orinoco-2.6.9-rfmon-dragorn-1.diff

Make a directory to backup the existing drivers.
# mkdir /orinoco

Move orinoco drivers to backup location
# mv /lib/modules/2.6.10/kernel/drivers/net/wireless/orinoco* /orinoco
# mv /lib/modules/2.6.10/kernel/drivers/net/wireless/hermes.ko /orinoco

copy the config file to the source directory
# cp /boot/config-2.6.10-5-386 /usr/src/linux/.config

compile the modules
# make modules
# make modules_install

copy the new modules to the proper directory
# cp /usr/src/linux/drivers/net/wireless/orinoco*ko /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/

# cp /usr/src/linux/drivers/net/wireless/hermes.ko /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/

edit /etc/kismet/kismet.conf for your card
use orinoco,eth1,orinocosource

enjoy[/QUOTE]

Thank you so much for maing this. As soon as I saw it in the wiki, I have spent the past three days trying it. It doesn't work on my iBook, but it does work on my Toshiba laptop. Thanks!

Now if only I could find a GUi for Kismet...

---

### Post by jshein on 2005-04-09
Glad it helped. Every time ou update the kernel you will have to recompile & copy over the modules again. ( As I had t o a few days ago, due to the kernel update )

As for the gui there is Gkismet [http://gkismet.sourceforge.net/](http://gkismet.sourceforge.net/)

I have not tried it with the latest kismet, as console mode works for me. I have tried it in the past and it worked well.

---

### Post by aarono on 2005-04-14
Thanks for posting this - I've come at the patch-my-orinoco several times, and these instructions got me further than ever before... now, for the last few feet.

I'm running hoary on an iBook (tangerine first generation - an antique!). The system recognizes my (non-extreme) Airport card when installed, and works like a champ.

When trying the instructions here, I get through the 'make modules' and 'make modules_install' step, but when I actually move the modules into place and reboot, they fail when loading. Here's what I see in the kernel log:

Apr 11 08:28:14 localhost kernel: hermes: no version for "struct_module" found:\ kernel tainted.
Apr 11 08:28:14 localhost kernel: orinoco 0.13e (David Gibson <hermes@gibson.dr\opbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
Apr 11 08:28:14 localhost kernel: airport: disagrees about version of symbol he\rmes_struct_init
Apr 11 08:28:14 localhost kernel: airport: Unknown symbol hermes_struct_init
Apr 11 08:28:14 localhost kernel: airport: disagrees about version of symbol he\rmes_init
Apr 11 08:28:14 localhost kernel: airport: Unknown symbol hermes_init
Apr 11 08:28:14 localhost kernel: airport: disagrees about version of symbol al\loc_orinocodev
Apr 11 08:28:14 localhost kernel: airport: Unknown symbol alloc_orinocodev

As you can imagine, the system now fails to recognize eth1. Any idea what's happening here?

Thanks!
A

---

### Post by jshein on 2005-04-14
Here are my thoughts on this matter, read all before trying any as they are not in numerical order of preference.

1 - Did you remember to remove the original orinoco modules ( copy to backup location ) before installing/copying over the new ones.

2 - same thing for the hermes driver

3 -  what is your firmware revision on your card?

4 - I found other referneces to this error in a debian environment on google. all were related to the ppc kernels. you might have to compile your own kernel from vanilla sources to make this work.

5 - try this
[I]
**# sudo update-modules**[/I]

6 - make sure the modules are unloaded before you install / copy over the new modules.

[B][I]# sudo rmmod orinoco
# sudo rmmod hermes[/I][/B]



try this before you insert the card

***# tail -f  /var/log/messages***


Post what comes up after you insert thecard I will see if I can be of any assistance.

---

### Post by aarono on 2005-04-14
Thanks for your continuing help! I had backed up the drivers (thankfully), and can back out to my old working state by swapping them back in. I tried your other suggestions (short of rebuilding the kernel) to no avail - same result. This card is internal to the machine - there's no inserting to be done, but /var/log/messages contains the same lines as I reported earlier. I don't know how to check the firmware revision - I know I updated it back when I was running OS9 but none of the iw* tools are a help.

I should have googled the problem myself - if I find out anything from those various threads, I'll report it here...

A

---

### Post by jshein on 2005-04-15
Internal card. Hmm. Can you disable this in the BIOS ?

idea:

1 Disable wireless in the bios
2 boot & compile drivers
3 install drivers
4 reboot & re-enable wireless
5 maybe yes, maybe no, It was just a thought sfter all.

While I was figuring out how to do this, numerous pages I found insisted that the card must not be inserted / modules unloaded before installing the drivers. Are you making sure the modules are unloaded?

**# lsmod | grep orinoco**

---

### Post by aarono on 2005-04-17
Ah - got it - it helps to actually read the error message in the boot log. There's an airport.ko module that gets rebuilt along with hermes.ko etc - it  must also be copied to /lib/modules/.../kernel/drivers/net/wireless to keep things happy.

So, for airport users (can't warrant this works with airport extreme):

- when you copy orinoco*.ko and kismet.ko to /orinoco for safekeeping, also copy over airport.ko

- after rebuilding the modules, copy airport.ko from the same place as hermes.ko et all.

Yahoo!

---

### Post by aarono on 2005-04-17
[QUOTE=aarono]Ah - got it - it helps to actually read the error message in the boot log. There's an airport.ko module that gets rebuilt along with hermes.ko etc - it  must also be copied to /lib/modules/.../kernel/drivers/net/wireless to keep things happy.

So, for airport users (can't warrant this works with airport extreme):

- when you copy orinoco*.ko and kismet.ko to /orinoco for safekeeping, also copy over airport.ko

- after rebuilding the modules, copy airport.ko from the same place as hermes.ko et all.

Yahoo![/QUOTE]
 (Of course, there is no kismet.ko - in the first step, I meant hermes.ko)

---

### Post by greenwom on 2005-04-28
<---Frustrated Newbee

I've followed the WIKI and it didn't work.

I have a fresh install of Hoary and..... this is frustrating.

when I iwconfig there isn't a eth1

IWconfig shows lo, [COLOR=DarkRed]eth0[/COLOR], sit0..........

Where do I go next, understanding this is what's keeping me from killing my windows partition.........

 :mad:    ](*,)     :-#

EDIT :[COLOR=DarkRed]My stupid mistake in red :)[/COLOR]

---

### Post by jshein on 2005-04-28
BEWARE THE WIKI!

I have given up editing it every time someone changes it. Look to this thread to see it as I originally posted the howto.

I have used these directions on 7 different laptops now with no problems.

I am looking to help. But I need you to clarify:

"when I iwconfig there isn't a eth1

IWconfig shows lo, eth1, sit0.........."


I see eth1 in that statement.

please post what you get from dmesg, as well as #tail -f /var/log/messages      before you insert the card.

---

### Post by greenwom on 2005-04-28
[QUOTE=jshein]BEWARE THE WIKI!

"when I iwconfig there isn't a eth1

IWconfig shows lo, eth1, sit0.........."


I see eth1 in that statement.

please post what you get from dmesg, as well as #tail -f /var/log/messages      before you insert the card.[/QUOTE]

YA I'm an idiot, it's eth0, I'll edit my post and try your sujestion

---

### Post by greenwom on 2005-04-28
[COLOR=Navy]Here you go knock yourself out (thanks)[/COLOR]

mike@mikesubuntu:~$ dmesg
Qs 3 4 *5 7 9 10 11 12)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
ACPI: Embedded Controller [EC0] (gpe 1)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
ACPI: Power Resource [PCR0] (off)
ACPI: Power Resource [PCR1] (off)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:05: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:05: ioport range 0x8000-0x807f could not be reserved
pnp: 00:05: ioport range 0x8080-0x80ff has been reserved
pnp: 00:05: ioport range 0x8100-0x811f could not be reserved
pnp: 00:05: ioport range 0x6800-0x687f has been reserved
Simple Boot Flag at 0x37 set to 0x1
audit: initializing netlink socket (disabled)
audit(1114707858.509:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Applying VIA southbridge workaround.
PCI: Disabling Via external APIC routing
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 6
Cannot allocate resource for EISA slot 8
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
MODM  LAN CRD0 CRD1
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Processor [CPU0] (supports 16 throttling states)
ACPI: Thermal Zone [THRM] (34 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:07.1
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
    ide0: BM-DMA at 0x1c40-0x1c47, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1c48-0x1c4f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: HITACHI_DK23CA-20, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(100)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Probing IDE interface ide1...
hdc: UJDA720 DVD/CDRW, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (455 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: hda2: orphan cleanup on readonly fs
ext3_orphan_cleanup: deleting unreferenced inode 591026
ext3_orphan_cleanup: deleting unreferenced inode 591023
EXT3-fs: hda2: 2 orphan inodes deleted
EXT3-fs: recovery complete.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 425680k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda2, internal journal
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
parport_pc: VIA 686A/8231 detected
parport_pc: probing current configuration
parport_pc: Current parallel port base: 0x378
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EC P]
parport_pc: VIA parallel port: io=0x378, irq=7
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
ts: Compaq touchscreen protocol output
hermes: no version for "struct_module" found: kernel tainted.
orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski @gnu.org>, et al)
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <pro [email]ski@gnu.org[/email]>, et al)
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
agpgart: Maximum main memory to use for agp memory: 204M
agpgart: AGP aperture is 128M @ 0xf0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
PCI: setting IRQ 9 as level-triggered
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 9 (level, low) -> IRQ 9
uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
PCI: Setting latency timer of device 0000:00:07.2 to 64
uhci_hcd 0000:00:07.2: irq 9, io base 0x1c00
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:07.3[D] -> GSI 9 (level, low) -> IRQ 9
uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
PCI: Setting latency timer of device 0000:00:07.3 to 64
uhci_hcd 0000:00:07.3: irq 9, io base 0x1c20
uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:07.5[C] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:07.5 to 64
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 9 (level, low) -> IRQ 9
Yenta: CardBus bridge found at 0000:00:0a.0 [104d:80f6]
Yenta: Enabling burst memory read transactions
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:0a.0, mfunc 0x012c1222, devctl 0x66
Yenta: ISA IRQ mask 0x0c08, PCI irq 9
Socket status: 30000006
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:0a.1[B] -> GSI 10 (level, low) -> IRQ 10
Yenta: CardBus bridge found at 0000:00:0a.1 [104d:80f6]
Yenta: Using CSCINT to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:0a.1, mfunc 0x012c1222, devctl 0x66
Yenta: ISA IRQ mask 0x0808, PCI irq 10
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:00:0e.0[A] -> GSI 9 (level, low) -> IRQ 9
PCI: Setting latency timer of device 0000:00:0e.0 to 64
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[e8004000-e80047ff]  Max Packet=[2048]
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:10.0 to 64
eth0: RealTek RTL8139 at 0x1800, 08:00:46:2f:e8:25, IRQ 10
eth0:  Identified 8139 chip type 'RTL-8139C'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth0: link down
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460300f57c19]
NET: Registered protocol family 17
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
NET: Registered protocol family 24
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [ACAD] (off-line)
ACPI: Battery Slot [BAT1] (battery absent)
ACPI: Battery Slot [BAT2] (battery absent)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SBTN]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 920296
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 919272
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 919048
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 920288
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 919264
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 919040
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 919696
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 918672
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 918448
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 919688
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 918664
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 918440
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 755124
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 754100
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 753876
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 755116
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 754092
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 753868
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 754524
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 753500
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 753276
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 754516
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 753492
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 753268
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1248
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1024
UDF-fs: No partition found (1)
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

mike@mikesubuntu:~$ sudo tail -f /var/log/messages
Password:
Apr 28 13:59:53 localhost kernel: end_request: I/O error, dev fd0, sector 68
Apr 28 13:59:54 localhost kernel: floppy0: data CRC error: track 1, head 1, sector 15, size 2
Apr 28 13:59:54 localhost kernel: floppy0: data CRC error: track 1, head 1, sector 15, size 2
Apr 28 13:59:54 localhost kernel: end_request: I/O error, dev fd0, sector 68
Apr 28 13:59:55 localhost kernel: floppy0: data CRC error: track 1, head 1, sector 15, size 2
Apr 28 13:59:55 localhost kernel: floppy0: data CRC error: track 1, head 1, sector 15, size 2
Apr 28 13:59:55 localhost kernel: end_request: I/O error, dev fd0, sector 68
Apr 28 13:59:56 localhost kernel: floppy0: data CRC error: track 0, head 1, sector 15, size 2
Apr 28 13:59:56 localhost kernel: floppy0: data CRC error: track 0, head 1, sector 15, size 2
Apr 28 13:59:56 localhost kernel: end_request: I/O error, dev fd0, sector 32

---

### Post by jshein on 2005-04-29
I noticed that eth0 is a 
> 
eth0: RealTek RTL8139 at 0x1800, 08:00:46:2f:e8:25, IRQ 10
eth0: Identified 8139 chip type 'RTL-8139C'

This is a 10/100 lan not wireless. Probably the on-board ethernet port on your pc.

The wireless card is not detected at all. Anywhere. Period.

This possibly means that:


a - The card is dead ( hopefully not, check on other machine )
b - The PCMCIA socket is dead ( check card on other machine )
c - PCMCIA socket driver issues
d - hotplug issues

---

### Post by greenwom on 2005-04-29
Ok, 

ETH0 is my network plug this "Ubunutu maching hard wire into a network.
I use the same machine 'dual boot' with XP and same wireless card.

In Ubuntu's device manager the PCI1420 port brings up the card 


As far as hot plug, my jump drive mounts when I plug it in (USB)

When I plug the card in (in Ubuntu) it lights up but that's it.

 When I plud the card in I can watch  it apear in Ubuntu's device manager,the PCI1420 port brings up the card and it shows linksys 

HELP ME PLEASE...    :-x 

                          :roll:

---

### Post by greenwom on 2005-04-30
Honestly I've looked at your instructions, I've tried the Ndiswrapepr wiki and man I'm stuck in a rut. 

Ubuntu is useless on my laptop with no wireless.

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

Should I try and reinstall Ubuntu with the wireless card in the port?  Wil it possibly install it?

---

### Post by poofyhairguy on 2005-05-13
bump

Edit: I moved this to keep it from getting lost.

---

### Post by bobby555 on 2005-05-16
thanks for taking the effort of creating a guide!

still a complete noob, i probably shouldn't even have tried this, but here we go:

(almost) every command needs to have sudo in front of it (duh!) adding this would make straight copy/paste action even quicker.

mkdir /orinoco doesn't work quite the way i thought it would.. perhaps you should change it..

thanks again,

am

(i've gotten to compiling modules now, doesn't quite work..)

```
/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: Filen eller katalogen finns inte
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  SYMLINK include/asm -> include/asm-i386
/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: Filen eller katalogen finns inte
make[2]: scripts/Makefile.build: Filen eller katalogen finns inte (no such file or folder)
make[2]: *** Ingen regel för att skapa målet "scripts/Makefile.build".  Stannar. (no rule for creating target(?) stopping)
make[1]: *** [scripts_basic] Fel 2 (fel=error)
make: *** [include/linux/autoconf.h] Fel 2
```

---

### Post by jshein on 2005-05-16
[QUOTE=greenwom]Honestly I've looked at your instructions, I've tried the Ndiswrapepr wiki and man I'm stuck in a rut. 

Ubuntu is useless on my laptop with no wireless.

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

Should I try and reinstall Ubuntu with the wireless card in the port?  Wil it possibly install it?[/QUOTE]

Exactly what wireless card are you using? These instructions are for an orinoco type card. If you use Ndiswrapper kismet ( monitor mode ) will not work.

I am starting to suspect your card is just not linux compatible.... again, let me know the make & model.

---

### Post by jshein on 2005-05-16
[QUOTE=bobby555]

(almost) every command needs to have sudo in front of it (duh!) adding this would make straight copy/paste action even quicker.[/QUOTE]

Sorry, the first thing I do in ubuntu is enable the root account.

> mkdir /orinoco doesn't work quite the way i thought it would.. perhaps you should change it..

I noticed that on my laptop # 1 ( upgraded from kubuntu beta ) the directory is different than on laptop #2 I installed the other day ( kubuntu release ) I am looking into editing my post.


> (i've gotten to compiling modules now, doesn't quite work..)

```
/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: Filen eller katalogen finns inte
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  SYMLINK include/asm -> include/asm-i386
/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: Filen eller katalogen finns inte
make[2]: scripts/Makefile.build: Filen eller katalogen finns inte (no such file or folder)
make[2]: *** Ingen regel för att skapa målet "scripts/Makefile.build".  Stannar. (no rule for creating target(?) stopping)
make[1]: *** [scripts_basic] Fel 2 (fel=error)
make: *** [include/linux/autoconf.h] Fel 2
```

Make sure you install GCC 3 along side the exisiting version before compiling modules. Having just the default GCC causes some errors, and complaining about missing files.

---

### Post by bobby555 on 2005-05-17
[QUOTE=jshein]Sorry, the first thing I do in ubuntu is enable the root account.

Make sure you install GCC 3 along side the exisiting version before compiling modules. Having just the default GCC causes some errors, and complaining about missing files.[/QUOTE]

Well I meant 'orinoco' instead of '/orinoco'..

I installed gcc 3.3 but it still doesn't work. I'll try to get some help from a Linux-savvy friend..

AM

---

### Post by NTolerance on 2005-05-17
Thanks for this guide.  I have used it several times in the past to enable monitor mode with my Orinoco card.  What I am puzzled about is how to enable scanning as well.  I believe that the drivers that we are patching with this guide don't support scanning.  Is there a way similar to this in which scanning support can be enabled?

---

### Post by poofyhairguy on 2005-05-22
Author, please note that I have edited your FAQ in order to increase clarity, allow for easy copy and paste and include a greater range of kernels. I have changed NOTHING essential and I invite you to PM me if you notice something wrong.

Please do not interpret this as a flaw on your part. I did this because its my favorite on the forum and I wanted to add things that I have hammered out through experiance.

This is a wonderful thing, and I thank you kindly for it.

---

### Post by linTrog on 2005-06-12
[QUOTE=bobby555]I installed gcc 3.3 but it still doesn't work. I'll try to get some help from a Linux-savvy friend..

AM[/QUOTE]

Ditto.  I'm having the same issue (i am a noob too)
________________________________________________________________________________
root@ubuntupo:/usr/src/linux # make modules
/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: No such file or directory
  CHK     include/linux/version.h
  SYMLINK include/asm -> include/asm-i386
/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: No such file or directory
make[2]: scripts/Makefile.build: No such file or directory
make[2]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[1]: *** [scripts_basic] Error 2
make: *** [include/linux/autoconf.h] Error 2
root@ubuntupo:/usr/src/linux #
__________________________________________________________________________________


Anyone know why it doesn't compile?

(i did install gcc 3 also)
thanks

ps 
if this is an ignorant question, feel free to call me names too =]

---

### Post by bobby555 on 2005-06-12
I still didn't get it to work.. My main problem seems to be PCMCIA related. The compiling stuff I got working, but I'm not sure how.. My friend helped me install some packages, kernel headers (?) and som tools for compiling..

AM

---

### Post by jshein on 2005-06-13
What is the problem you are having now?

Inert the card the post the output from:

#dmesg

and

#nano /var/log/messages

and

#iwpriv eth1 ( or whatever your card is deteced as wlan0 etc. )

---

### Post by linTrog on 2005-06-13
I've figured out that I can activate the card itself (without the patched drivers)  It looks like the orinoco drivers are in there somewhere =]

I seem to be having problems compiling the module for monitor mode.

I'm not sure if you were asking me, but I can give you the output from those commands if you wish =]

---

### Post by jshein on 2005-06-13
If you follow the directions step by step you **should** be able to get monitor mode.

#iwpriv eth1 ( or whatever your card is detected as )

will tell you if monitor mode is available

---

### Post by linTrog on 2005-06-13
I appreciate all your help. 
I have been following the instructions, it's where I try and compile the module that I'm having the issue (I think).  I posted the output above.  This is a fresh install of Ubuntu and I installed the gcc's to no avail...

iwpriv >>
eth1      Available private ioctl :
          force_reset      (8BE0) : set   0       & get   0      
          card_reset       (8BE1) : set   0       & get   0      
          set_port3        (8BE2) : set   1 int   & get   0      
          get_port3        (8BE3) : set   0       & get   1 int  
          set_preamble     (8BE4) : set   1 int   & get   0      
          get_preamble     (8BE5) : set   0       & get   1 int  
          set_ibssport     (8BE6) : set   1 int   & get   0      
          get_ibssport     (8BE7) : set   0       & get   1 int  
          dump_recs        (8BFF) : set   0       & get   0      


kismet output:
root@ubuntupo:/home/trog # kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before startuing UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (orinocosource): Enabling monitor mode for orinoco source interface eth1 channel 6...
FATAL: Could not find 'monitor' private ioctl or use the newer style 'mode monitor' command.  This typically means that the drivers have not been patched or the correct drivers are being loaded. See the troubleshooting section of the README for more information.
root@ubuntupo:/home/trog #

thx

---

### Post by jshein on 2005-06-13
this line

> /bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: No such file or directory 

says that the script can not be found to detect your gcc version.

What is your output of

#ls -lh /usr/src/linux-source-2.6.10/scripts/gcc-version.sh

Is the file even there ?

If it is, check it's interity by using

#md5sum /usr/src/linux/scripts/gcc-version.sh

The latest version as of June 13, 2005 should result in

#e1b3007ed6b6fd17419df91123297790  /usr/src/linux/scripts/gcc-version.sh



Make sure that you fully extracted the kernel source, and linked to it with /usr/src/linux

---

### Post by linTrog on 2005-06-13
it's fixed, up and running.  

I went through the instructions again, slowly, using verbose and checking to see if I had the desired output.  I think I missed the linking part - I don't know for sure.

Thanks all for your help, and the instructions were wonderful!

- linTrog

---

### Post by bobby555 on 2005-06-16
[QUOTE=jshein]What is the problem you are having now?

Inert the card the post the output from:

#dmesg

and

#nano /var/log/messages

and

#iwpriv eth1 ( or whatever your card is deteced as wlan0 etc. )[/QUOTE]

I appreciate you taking your time to help me out. I am on vacation right now and didn't bring the card. I'll get back to you as soon as I am back home.

Check out [this thread](http://ubuntuforums.org/showthread.php?t=37079) for some info I posted earlier.. I'm not so good at this log-decoding business

AM

---

### Post by 6tnine on 2005-06-20
I'm a relative newbie at this also, so please bear with me here, but I followed the steps.  I'm using an IBM T22 lappy w/ an orinoco silver and here is the error message I'm getting.  Any help would be appreciated.

Jun 20 04:04:01 localhost -- MARK --
Jun 20 04:06:38 localhost kernel: eth0: trigger_send() called with the transmitter busy.
Jun 20 04:06:43 localhost kernel: orinoco: Unknown symbol hermes_read_ltv
Jun 20 04:06:43 localhost kernel: orinoco: Unknown symbol hermes_init
Jun 20 04:06:43 localhost kernel: orinoco: Unknown symbol hermes_bap_pwrite
Jun 20 04:06:43 localhost kernel: orinoco: Unknown symbol hermes_write_ltv
Jun 20 04:06:43 localhost kernel: orinoco: Unknown symbol hermes_docmd_wait
Jun 20 04:06:43 localhost kernel: orinoco: Unknown symbol hermes_allocate
Jun 20 04:06:43 localhost kernel: orinoco: Unknown symbol hermes_bap_pread
Jun 20 04:06:44 localhost kernel: orinoco_cs: Unknown symbol orinoco_reinit_firmware
Jun 20 04:06:44 localhost kernel: orinoco_cs: Unknown symbol hermes_struct_init
Jun 20 04:06:44 localhost kernel: orinoco_cs: Unknown symbol orinoco_interrupt
Jun 20 04:06:44 localhost kernel: orinoco_cs: Unknown symbol __orinoco_up
Jun 20 04:06:44 localhost kernel: orinoco_cs: Unknown symbol __orinoco_down
Jun 20 04:06:44 localhost kernel: orinoco_cs: Unknown symbol alloc_orinocodev

---

### Post by MrSandman on 2005-06-20
can anyone tell me how to enable sound for kismet? the path /usr/bin/play isnt working for me.

---

### Post by jshein on 2005-06-20
Play won't work, or you do not have it installed?

#sudo apt-get install sox

should fix you up.

---

### Post by MrSandman on 2005-06-20
[QUOTE=jshein]Play won't work, or you do not have it installed?

#sudo apt-get install sox

should fix you up.[/QUOTE]


if appears i already have sox, and the play script is in the /usr/bin/play...sound works on others apps, but not kismet, any suggestions. ](*,) 

thanks

---

### Post by jshein on 2005-06-20
I think alpay can be used instead of play. Try installing that, and changing the kismet.conf to point to it.

---

### Post by MrSandman on 2005-06-20
[QUOTE=jshein]I think alpay can be used instead of play. Try installing that, and changing the kismet.conf to point to it.[/QUOTE]


did you mean aplay? if so it did not work for me.

---

### Post by jshein on 2005-06-21
try using /usr/bin/play to play a .wav file directly

#play ( path to wav file )

It should play the wav file with no problems. If it works then the problem is with kismet. If it does not, look in /var/log/messages and see what errors are being reported

---

### Post by bobby555 on 2005-06-26
[QUOTE=bobby555]I appreciate you taking your time to help me out. I am on vacation right now and didn't bring the card. I'll get back to you as soon as I am back home.

Check out [this thread](http://ubuntuforums.org/showthread.php?t=37079) for some info I posted earlier.. I'm not so good at this log-decoding business

AM[/QUOTE]

The only thing that happens when I insert card(s) with dmesg is that this line is inserted at the bottom: ```
cs: memory probe 0xa0000000-0xa0ffffff: clean.
```

/var/log/messages shows:
```
Jun 26 15:28:35 localhost kernel: cs: memory probe 0xa0000000-0xa0ffffff: clean.
```
When I insert both cards, one after the other.

The PCMCIA cards aren't really detected, so iwpriv gives:
```
~$ iwpriv
lo        no private ioctls.

eth0      no private ioctls.

sit0      no private ioctls.

```

Let me know if you can read anything from this or if you need additional info.

AM

---

### Post by jshein on 2005-06-27
Lets get the basics out of the way here first. Do you have any other PCMCIA cards to use to test that the PCMCIA system is in fact working under linux ?

Next, if it works wth another card ( does not need to be wireless I often use a realtek 10/100 card for diagnostic purposes ), what is your card exactly. model - manufacturer and revision number.

There are some good troubleshooting ideas on this page regarding PCMCIA issues

[http://www.lugor.org/sig/newbie/PCMCIA-HOWTO/PCMCIA-HOWTO-3.html](http://www.lugor.org/sig/newbie/PCMCIA-HOWTO/PCMCIA-HOWTO-3.html)

Let me know how you make out.

---

### Post by bobby555 on 2005-06-27
[QUOTE=jshein]Lets get the basics out of the way here first. Do you have any other PCMCIA cards to use to test that the PCMCIA system is in fact working under linux ?

Next, if it works wth another card ( does not need to be wireless I often use a realtek 10/100 card for diagnostic purposes ), what is your card exactly. model - manufacturer and revision number.

There are some good troubleshooting ideas on this page regarding PCMCIA issues

[http://www.lugor.org/sig/newbie/PCMCIA-HOWTO/PCMCIA-HOWTO-3.html](http://www.lugor.org/sig/newbie/PCMCIA-HOWTO/PCMCIA-HOWTO-3.html)

Let me know how you make out.[/QUOTE]

Well the PCMCIA system is not working, and none of the scenarios in the PCMCIA Howto matches what I get..

I'm not really sure what to do next.

AM

---

### Post by bobby555 on 2005-07-11
Ok, so now I got the wireless card working. The command needed was
```
sudo cardmgr
```
The rest I think will be a piece of cake.

AM

---

### Post by Transmit on 2006-10-03
will this make it work with broadcom cards?

---

