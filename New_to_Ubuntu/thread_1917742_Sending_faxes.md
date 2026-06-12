---
title: "Sending faxes"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Faan on 2012-01-30
Something which I cannot understand is why I cannot send faxes from my PC under the UBUNTU OS.  To me this is such a basic thing.  I could do it when I still had Windows.  
I am told that it could be due to the modem being a Windows "hardware" inside the PC.  If this is the case should I then buy a new modem (external) which is compatible with UBUNTU?
The person/company where I have bought most of my hardware is not at all in favour of UBUNTU and this will mean that if I cannot come right with the existing software that I will have to search for a supplier who could provide me with the modem.
I would appreciate some help please.
Thank you

---

### Post by DNSBubba on 2012-01-30
I know this is not an actual hardware solution, but I use an online service to send faxes.  The one I use is less than $10 per month, and I can send and receive from anywhere I have a wifi connection.

A quick google search would revel some choices, if you're interested in going that route.

---

### Post by Lars Noodén on 2012-01-30
What you have might be a [Windmodem](http://modemdriver.com/winmodems.htm) and not a real modem.  It would be something to avoid on a future modem, either internal or external.  Can you provide some specifics as to the hardware you currently have using [lshw](http://manpages.ubuntu.com/manpages/oneiric/en/man1/lshw.1.html)?

```

sudo lshw -html > systeminfo.html
firefox systeminfo.html

```

(I think that might find your current modem.)

---

### Post by halitech on 2012-01-30
most internal modems that have been coming in computers for probably the last 10 years have been called Winmodems or software modems due to the fact that the actual card is really nothing more then a place to plug in a phone cord. At one point there was work being done on drivers for linux that were working with software modems but with the majority of people having access to highspeed of some sort, I'm not sure if that project is still alive or not.

As far as finding new hardware, you don't need to buy new and you may actually have better luck finding an old hardware modem that will work properly. Since most modems still only fax at 14.4 or maybe 28.8, even a 15 year old modem will work (provided you can find a PCI based one instead of an ISA one)


seems Ubuntu is still maintaining a page on dialup modems, not sure how old it is but maybe it will still be useful (as long as the packages still exist)

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by satanselbow on 2012-01-30
Do you really need to send traditional paper faxes? There are numerous online fax services and fax to email providers that negates the need for the hardware altogether ;)

I rarely have the need to send fax these days but have used [http://www.comfax.co.uk/](http://www.comfax.co.uk/) previously.

---

### Post by Faan on 2012-01-30
> **Lars Noodén said:**
> 

```

sudo lshw -html > systeminfo.html
firefox systeminfo.html

```

(I think that might find your current modem.)

I inserted this and then got a long list of things on my Firefox web browser:

faan@faan-P4M266-8233:~$ firefox systeminfo.html

(firefox:21060): Bonobo-WARNING **: Bonobo must be initialized before use
No bp log location saved, using default.
[000:051] Browser XEmbed support present: 1
[000:063] Browser toolkit is Gtk2.
[000:064] Using Gtk2 toolkit
[000:149] Read port file, port=42552
[000:191] Initiated connection to GoogleTalkPlugin
[000:543] Socket connection established
[000:543] ScheduleOnlineCheck: Online check in 5000ms
[000:543] Got cookie response, socket is authorized
[000:543] AUTHORIZED; socket handshake complete
[005:615] HandleOnlineCheck: Starting check
[005:615] HandleOnlineCheck: OK; current state: 3

It then also opened Firefox giving me a long list of things including the following:
"id:	
faan-p4m266-8233
description: 	Desktop Computer
width: 	32 bits
capabilities: 	smbios-2.2 dmi-2.2 smp-1.4 smp
configuration:	
boot	=	normal
chassis	=	desktop
cpus	=	1
id:	
core
description: 	Motherboard
product: 	P4M266-8233
vendor: 	MICRO-STAR INTERNATIONAL CO., LTD
physical id: 	
0
id:	
firmware
description: 	BIOS
vendor: 	Phoenix Technologies, LTD
physical id: 	
0
version: 	6.00 PG
date: 	03/31/2004
size: 	128KiB
capacity: 	448KiB
capabilities: 	isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot" etc.

Difficult for me to make out anything of this.

---

### Post by halitech on 2012-01-30
difficult for anyone else to as well since you didn't post the entire output. Please post all of it so we can determine if Ubuntu is even seeing a modem

---

### Post by Lars Noodén on 2012-01-30
> **Faan said:**
> Difficult for me to make out anything of this.

I don't see anything there either, but I'm not really a hardware person.

Do you see any modem using [lspci](http://manpages.ubuntu.com/manpages/oneiric/en/man8/lspci.8.html) or [lsusb](http://manpages.ubuntu.com/manpages/oneiric/en/man8/lsusb.8.html) ?

---

### Post by Faan on 2012-01-30
Everything:

id:	
faan-p4m266-8233
description: 	Desktop Computer
width: 	32 bits
capabilities: 	smbios-2.2 dmi-2.2 smp-1.4 smp
configuration:	
boot	=	normal
chassis	=	desktop
cpus	=	1
id:	
core
description: 	Motherboard
product: 	P4M266-8233
vendor: 	MICRO-STAR INTERNATIONAL CO., LTD
physical id: 	
0
id:	
firmware
description: 	BIOS
vendor: 	Phoenix Technologies, LTD
physical id: 	
0
version: 	6.00 PG
date: 	03/31/2004
size: 	128KiB
capacity: 	448KiB
capabilities: 	isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
id:	
cpu:0
description: 	CPU
product: 	Intel(R) Pentium(R) 4 CPU 2.40GHz
vendor: 	Intel Corp.
physical id: 	
4
bus info: 	
cpu@0
version: 	15.3.3
serial: 	0000-0F33-0000-0000-0000-0000
slot: 	Socket 478
size: 	2400MHz
width: 	32 bits
clock: 	133MHz
capabilities: 	boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid
configuration:	
id	=	0
id:	
cache:0
description: 	L1 cache
physical id: 	
a
slot: 	Internal Cache
size: 	32KiB
capacity: 	32KiB
capabilities: 	synchronous internal write-back
id:	
cache:1
description: 	L2 cache
physical id: 	
c
slot: 	External Cache
size: 	1MiB
capacity: 	1MiB
capabilities: 	synchronous external write-back
id:	
cpu:1
description: 	CPU
vendor: 	Unknown
physical id: 	
5
bus info: 	
cpu@1
version: 	15.3.3
serial: 	0000-0F33-0000-0000-0000-0000
slot: 	Socket 478
size: 	2400MHz
clock: 	133MHz
capabilities: 	ht
configuration:	
id	=	0
id:	
cache:0
description: 	L1 cache
physical id: 	
b
slot: 	Internal Cache
size: 	32KiB
capacity: 	32KiB
capabilities: 	synchronous internal write-back
id:	
cache:1
description: 	L2 cache
physical id: 	
d
slot: 	External Cache
size: 	1MiB
capacity: 	1MiB
capabilities: 	synchronous external write-back
id:	
memory
description: 	System Memory
physical id: 	
1e
slot: 	System board or motherboard
size: 	768MiB
capacity: 	1536MiB
id:	
bank:0
description: 	DIMM
physical id: 	
0
slot: 	A0
size: 	256MiB
id:	
bank:1
description: 	DIMM
physical id: 	
1
slot: 	A1
size: 	512MiB
id:	
bank:2
description: 	DIMM [empty]
physical id: 	
2
slot: 	A2
id:	
pci
description: 	Host bridge
product: 	P4M266 Host Bridge
vendor: 	VIA Technologies, Inc.
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	00
width: 	32 bits
clock: 	66MHz
configuration:	
driver	=	agpgart-via
latency	=	8
resources:	
irq	:	0
memory	:	e8000000-ebffffff
id:	
pci
description: 	PCI bridge
product: 	VT8633 [Apollo Pro266 AGP]
vendor: 	VIA Technologies, Inc.
physical id: 	
1
bus info: 	
pci@0000:00:01.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pci pm normal_decode bus_master cap_list
resources:	
memory	:	ec000000-edffffff
memory	:	e0000000-e7ffffff
id:	
display
description: 	VGA compatible controller
product: 	VT8375 [ProSavage8 KM266/KL266]
vendor: 	S3 Inc.
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pm agp agp-2.0 vga_controller bus_master cap_list
configuration:	
latency	=	32
maxlatency	=	255
mingnt	=	4
resources:	
memory	:	ed000000-ed07ffff
memory	:	e0000000-e7ffffff
memory	:	ec000000-ec00ffff
id:	
communication
description: 	Communication controller
product: 	HSF 56k HSFi Modem
vendor: 	Conexant Systems, Inc.
physical id: 	
5
bus info: 	
pci@0000:00:05.0
version: 	01
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	32
resources:	
memory	:	ee000000-ee00ffff
ioport	:	d000(size=8)
id:	
usb:0
description: 	USB Controller
product: 	VT82xxxxx UHCI USB 1.1 Controller
vendor: 	VIA Technologies, Inc.
physical id: 	
10
bus info: 	
pci@0000:00:10.0
version: 	80
width: 	32 bits
clock: 	33MHz
capabilities: 	pm uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	32
resources:	
irq	:	21
ioport	:	d400(size=32)
id:	
usb:1
description: 	USB Controller
product: 	VT82xxxxx UHCI USB 1.1 Controller
vendor: 	VIA Technologies, Inc.
physical id: 	
10.1
bus info: 	
pci@0000:00:10.1
version: 	80
width: 	32 bits
clock: 	33MHz
capabilities: 	pm uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	32
resources:	
irq	:	21
ioport	:	d800(size=32)
id:	
usb:2
description: 	USB Controller
product: 	VT82xxxxx UHCI USB 1.1 Controller
vendor: 	VIA Technologies, Inc.
physical id: 	
10.2
bus info: 	
pci@0000:00:10.2
version: 	80
width: 	32 bits
clock: 	33MHz
capabilities: 	pm uhci bus_master cap_list
configuration:	
driver	=	uhci_hcd
latency	=	32
resources:	
irq	:	21
ioport	:	dc00(size=32)
id:	
usb:3
description: 	USB Controller
product: 	USB 2.0
vendor: 	VIA Technologies, Inc.
physical id: 	
10.3
bus info: 	
pci@0000:00:10.3
version: 	82
width: 	32 bits
clock: 	33MHz
capabilities: 	pm ehci bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	32
resources:	
irq	:	21
memory	:	ee010000-ee0100ff
id:	
isa
description: 	ISA bridge
product: 	VT8235 ISA Bridge
vendor: 	VIA Technologies, Inc.
physical id: 	
11
bus info: 	
pci@0000:00:11.0
version: 	00
width: 	32 bits
clock: 	33MHz
capabilities: 	isa pm bus_master cap_list
configuration:	
latency	=	0
id:	
ide
description: 	IDE interface
product: 	VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
vendor: 	VIA Technologies, Inc.
physical id: 	
11.1
bus info: 	
pci@0000:00:11.1
logical name: 	
scsi0
logical name: 	
scsi1
version: 	06
width: 	32 bits
clock: 	33MHz
capabilities: 	ide pm bus_master cap_list emulated
configuration:	
driver	=	pata_via
latency	=	32
resources:	
irq	:	20
ioport	:	1f0(size=8)
ioport	:	3f6
ioport	:	170(size=8)
ioport	:	376
ioport	:	e000(size=16)
id:	
disk:0
description: 	ATA Disk
product: 	HDS722580VLAT20
physical id: 	
0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	V32O
serial: 	VNR81EC2D8EYHL
size: 	76GiB (82GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	00083648
id:	
volume
description: 	Windows NTFS volume
physical id: 	
1
bus info: 	
scsi@0:0.0.0,1
logical name: 	
/dev/sda1
version: 	3.1
serial: 	001bb75c-5c89-e64f-87e8-a81d18bbe215
size: 	76GiB
capacity: 	76GiB
capabilities: 	primary bootable ntfs initialized
configuration:	
clustersize	=	4096
created	=	2011-03-11 19:46:57
filesystem	=	ntfs
state	=	clean
id:	
disk:1
description: 	ATA Disk
product: 	WDC WD800BB-00DK
vendor: 	Western Digital
physical id: 	
0.1.0
bus info: 	
scsi@0:0.1.0
logical name: 	
/dev/sdb
version: 	77.0
serial: 	WD-WMAHL1245097
size: 	74GiB (80GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	000014bd
id:	
volume:0
description: 	Extended partition
physical id: 	
1
bus info: 	
scsi@0:0.1.0,1
logical name: 	
/dev/sdb1
size: 	38GiB
capacity: 	38GiB
capabilities: 	primary extended partitioned partitioned:extended
id:	
logicalvolume:0
description: 	HPFS/NTFS partition
physical id: 	
5
logical name: 	
/dev/sdb5
capacity: 	37GiB
id:	
logicalvolume:1
description: 	Linux swap / Solaris partition
physical id: 	
6
logical name: 	
/dev/sdb6
capacity: 	1610MiB
capabilities: 	nofs
id:	
volume:1
description: 	EXT4 volume
vendor: 	Linux
physical id: 	
2
bus info: 	
scsi@0:0.1.0,2
logical name: 	
/dev/sdb2
logical name: 	
/
version: 	1.0
serial: 	babd600c-8aa1-46ed-af8b-474b2803a45a
size: 	35GiB
capacity: 	35GiB
capabilities: 	primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration:	
created	=	2011-03-22 14:41:13
filesystem	=	ext4
lastmountpoint	=	/
modified	=	2012-01-28 09:44:36
mount.fstype	=	ext4
mount.options	=	rw,relatime,errors=remount-ro,barrier=1,data=ordered
mounted	=	2012-01-30 06:53:04
state	=	mounted
id:	
cdrom
description: 	DVD-RAM writer
product: 	DVDRAM GSA-H12N
vendor: 	HL-DT-ST
physical id: 	
1
bus info: 	
scsi@1:0.0.0
logical name: 	
/dev/cdrom
logical name: 	
/dev/cdrw
logical name: 	
/dev/dvd
logical name: 	
/dev/dvdrw
logical name: 	
/dev/scd0
logical name: 	
/dev/sr0
version: 	UL02
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
status	=	nodisc
id:	
multimedia
description: 	Multimedia audio controller
product: 	VT8233/A/8235/8237 AC97 Audio Controller
vendor: 	VIA Technologies, Inc.
physical id: 	
11.5
bus info: 	
pci@0000:00:11.5
version: 	50
width: 	32 bits
clock: 	33MHz
capabilities: 	pm cap_list
configuration:	
driver	=	VIA 82xx Audio
latency	=	0
resources:	
irq	:	22
ioport	:	e400(size=256)
id:	
network
description: 	Ethernet interface
product: 	VT6102 [Rhine-II]
vendor: 	VIA Technologies, Inc.
physical id: 	
12
bus info: 	
pci@0000:00:12.0
logical name: 	
eth0
version: 	74
serial: 	00:0c:76:e3:d4:b4
size: 	100Mbit/s
capacity: 	100Mbit/s
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	via-rhine
driverversion	=	1.5.0
duplex	=	full
ip	=	192.168.1.4
latency	=	32
link	=	yes
maxlatency	=	8
mingnt	=	3
multicast	=	yes
port	=	MII
speed	=	100Mbit/s
resources:	
irq	:	23
ioport	:	ec00(size=256)
memory	:	ee011000-ee0110ff
id:	
scsi
physical id: 	
1
bus info: 	
usb@2:2
logical name: 	
scsi2
capabilities: 	emulated scsi-host
configuration:	
driver	=	usb-storage
id:	
disk
description: 	SCSI Disk
product: 	PSC 1613
vendor: 	HP
physical id: 	
0.0.0
bus info: 	
scsi@2:0.0.0
logical name: 	
/dev/sdc
version: 	1.00
capabilities: 	removable
configuration:	
ansiversion	=	2
id:	
medium
physical id: 	
0
logical name: 	
/dev/sdc

---

### Post by Faan on 2012-01-30
> **satanselbow said:**
> Do you really need to send traditional paper faxes? There are numerous online fax services and fax to email providers that negates the need for the hardware altogether ;)

I rarely have the need to send fax these days but have used [http://www.comfax.co.uk/](http://www.comfax.co.uk/) previously.

I do not send traditional paper faxes, but directly from the PC to some people who still do not have an email facility and only a fax receiver. And I cannot phone the fax line as no one will answer and I do not have a phone number.

---

### Post by halitech on 2012-01-30
okay, here is your modem
```
communication
description: Communication controller
product: HSF 56k HSFi Modem
vendor: Conexant Systems, Inc.
physical id:
5
bus info:
pci@0000:00:05.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration:
latency = 32
resources:
memory : ee000000-ee00ffff
ioport : d000(size=
id: 
```

You don't mention which version of Ubuntu you are using but there is info here that should help you out
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

---

### Post by Faan on 2012-01-30
I will look at all the proposals when it is morning again with us and see what works and hopefully something will.
Thanks for all the help in the meantime.

---

### Post by Faan on 2012-01-30
I think it is 11.04

---

