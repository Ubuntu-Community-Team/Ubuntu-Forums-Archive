---
title: "Compiz config on old computer"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by seal308 on 2012-05-14
Hello i am interested in using compizconfig but i'm not sure if that would be the best on my computer. Because my computer is old.

Here are my stats
```
# dmidecode 2.11
SMBIOS 2.5 present.
22 structures occupying 1192 bytes.
Table at 0x000FD1C0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 0501   
	Release Date: 07/31/2009
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.14
	Firmware Revision: 0.84

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: EB1006
	Version: System Version
	Serial Number: 98ESAB009459
	UUID: 606A40CC-8EFE-D511-8BB2-002618CCF599
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: Eee Family

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: P5G-EB1006-DHS
	Version: Rev 1.xx
	Serial Number: MF7098G01600425
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: Chassis Manufacture
	Type: Desktop
	Lock: Not Present
	Version: Chassis Version
	Serial Number: Chassis Serial Number
	Asset Tag: Asset-1234567890
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Other
	Manufacturer: Intel            
	ID: C2 06 01 00 FF FB E9 BF
	Version: Intel(R) Atom(TM) CPU N270 @ 1.60GHz                
	Voltage: 1.2 V
	External Clock: 133 MHz
	Max Speed: 3800 MHz
	Current Speed: 1600 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 1
	Core Enabled: 1
	Thread Count: 2
	Characteristics: None

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 24 kB
	Maximum Size: 24 kB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: Other

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 512 kB
	Maximum Size: 512 kB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Internal
	Installed Size: 0 kB
	Maximum Size: 0 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0008, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 2048 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		DIMM
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 2
		0x0009
		0x000A
	Enabled Error Correcting Capabilities:
		None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: 0 1
	Current Speed: 37 ns
	Type: DIMM SDRAM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 2 3
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000B, DMI type 11, 5 bytes
OEM Strings
	String 1: To Be Filled By O.E.M.
	String 2: AEMS000000000000000001000
	String 3: To Be Filled By O.E.M.
	String 4: To Be Filled By O.E.M.

Handle 0x000C, DMI type 13, 22 bytes
BIOS Language Information
	Language Description Format: Abbreviated
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x000D, DMI type 15, 35 bytes
System Event Log
	Area Length: 4 bytes
	Header Start Offset: 0x0000
	Header Length: 2 bytes
	Data Start Offset: 0x0002
	Access Method: Indexed I/O, one 16-bit index port, one 8-bit data port
	Access Address: Index 0x046A, Data 0x046C
	Status: Invalid, Not Full
	Change Token: 0x00000000
	Header Format: No Header
	Supported Log Type Descriptors: 6
	Descriptor 1: End of log
	Data Format 1: OEM-specific
	Descriptor 2: End of log
	Data Format 2: OEM-specific
	Descriptor 3: End of log
	Data Format 3: OEM-specific
	Descriptor 4: End of log
	Data Format 4: OEM-specific
	Descriptor 5: End of log
	Data Format 5: OEM-specific
	Descriptor 6: End of log
	Data Format 6: OEM-specific

Handle 0x000E, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x000F, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000400003FF
	Range Size: 1 GB
	Physical Array Handle: 0x000E
	Partition Width: 4

Handle 0x0010, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x0011, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Device Handle: 0x0010
	Memory Array Mapped Address Handle: 0x000F
	Partition Row Position: 1
	Interleaved Data Depth: 1

Handle 0x0012, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x0013, DMI type 126, 19 bytes
Inactive

Handle 0x0014, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0015, DMI type 127, 4 bytes
End Of Table

```

Would i be able to use some of the features.
Are there some features that are less processor intensive that others.
Thanks

---

### Post by mastablasta on 2012-05-15
hardware acceleration depends on your graphics card not the age of the maschine :-) the GPU processor and ram handles the acceleration.
 
post result of lspci or lshw to see what graphics card you have. if you have ATI or nvidia there is high chance that 3d effects will work well. especially if GPU is 128 Mb or higher.

---

### Post by Paddy Landau on 2012-05-15
An alternative reply is that if your computer is old, you may find Ubuntu slow (even with Ubuntu 2D). If it is, try instead using [Lubuntu]("http://lubuntu.net/"), designed for slower and older computers.

---

### Post by roelforg on 2012-05-15
My laptop has an 1.5ghz Intel Celeron Dual-Core CPU, 2gb of ram and an ATI Mobility Radeon HD2400 XT card (the sticker on the bottom says it's from 28 sep 2007).
Runs compiz with hightened 3D effects just fine whilst running mixxx and firefox with 12+ tabs at the same time, no pops,stutters,cracks,hangs or anything (for both the 3d effects AND the sound).
So yours (which has a better cpu than mine) should work fine.
When running the afformentioned program combination, i never get the cpu to use more than 60% (and that's when mixxx is loading a song, on average it hangs at around 50% with mixxx and 0-10% w/o mixxx) and i haven't ever seen the systemmonitorindicator (i installed that myself, very useful) to show me more then 40% ram usage (yes, i'm serious, even with all that heavy stuff open).

---

### Post by mastablasta on 2012-05-15
as mentiond before the graphics card will handle compiz. if the user has an old intel GPu the compiz will nto work but with descent ati and nvidia cards it will work. the ATI card from linux mashcine i use is at least 5 years old. probably more. yet is is supported nicely and it does all compiz effects or now they are plasma desktop effects...

---

