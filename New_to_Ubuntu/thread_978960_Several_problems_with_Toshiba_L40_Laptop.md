---
title: "Several problems with Toshiba L40 Laptop"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by D-TurboKiller on 2008-11-11
Hey guys, first time in the forums.
I'm a hardcore gamer. I've been a bit angry with Windows Vista since it wasn't exactly good in terms of performance, and for my laptop, that's not good at all. Also the Intel graphics drivers are really sucky, especially for OpenGL (Definitely noted in the game Sauerbraten).
I remembered Ubuntu and I thought "why not? It's such a great OS anyway". So I installed Ubuntu 8.10 (Intrepid Ibex), which FINNALY supports my wireless device. I've been exploring it a bit, adding apps, trying new stuff, etc. But I found some annoying & serious problems, mostly graphics related.

First of all, here are my specs:
Computer: Toshiba L40 Laptop
OS: Ubuntu 8.10 (Intrepid Ibex)
CPU: Intel Core 2 Duo T5200 (I think)
GPU: Mobile Intel 965 Express Chipset Family
RAM: 1 GB


Now, the problems...
-Many games and apps have serious graphics problems. Some examples are Neverball (runs much slower than on Vista...), Neverputt, Scorched3D, Urban Terror (which also runs slow as hell for some reason), Elisa Media Center, etc. They have garbled graphics. Example: Neverball after a few seconds becomes all garbled.

-Related to the previous problem... On windowed mode, for example on Neverball, whenever I click with the left mouse button the game screen suddenly goes black for just a fraction of the second and then the game screen appears again, but with garbled graphics. I think it also tends to garble in fullscreen mode when I click. These graphical problems lead me to the next question...

-Is there an easy tutorial on how to get and install the linux intel drivers for my graphics card? I went to "System->Administration->Hardware Drivers" and the list is empty, so I'm assuming I don't have anything. That would also explain why some games run so slow...

-Some applications won't run. For example ZSNES, the Super Nintendo Emulator, doesn't even start when I click the icon on the apps menu. It doesn't happen anything at all. I got it from the third-party repository included in Ubuntu.
Also, Extreme Penguin Racer doesn't run after I'm in the game and I click the run button. It just exits to the desktop.

-Some apps, when at fullscreen mode, suddenly switch to windowed mode, leaving the mouse locked, which leaves me no choice but to restart Ubuntu. For example, Sauerbraten suddenly switched to windowed mode while I was playing. I could see the mouse cursor in the center of the window, but I couldn't move it. Even in-game it didn't move...

-Some apps don't play music. The Enigma game, for example, doesn't play music at all, even when it's turned on.

-This one isn't a problem, but more of a question. Is there a good Benchmark program like the 3DMark series but for linux? It would be a great performance test for my laptop. Of course, I'd only use it after someone helps me with the Intel graphics drivers...

EDIT:
-I was forgetting this one. The wireless connection tends to fail sometimes. Not sure why... it works fine on Vista. It happens more ofter when I start Ubuntu, after that it's pretty much rare.


Well, I think these are all of them. I hope you can help me with this; I'm really stumped here.
Anyway I'll be going to bed in an hour or so. Thank you all, and good night ;)

---

### Post by D-TurboKiller on 2008-11-12
*bump*
Come on, I need help here.

---

### Post by eternalnewbee on 2008-11-12
Hi there, and welcome to the Ubuntu forums.
That's a lot of info you provided.But let's start with the graphic card: As there was nothing to be seen in **Hardware Drivers** you most probably have an onboard card, and that might explain the sloppy performance of your games.
If I were you, and I had some cash, I'd buy me a decent graphic card. I use Nvidia 7300GT, so something similar would suit your purposes. If you can't afford to buy one, I suggest you check out some places here on the forums that might be able to help you further with your issues.
[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)
[http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php)

Hope this will ease your suffering a bit[-o<

---

### Post by 3rdalbum on 2008-11-12
I can't explain the decreased performance of your card when running in Ubuntu, but Intel's graphics drivers are open-source and therefore already installed. If you're getting incredibly low frame rates like 2 fps (or 3D games won't run), then that's when you know you don't have graphics drivers.

Maybe disabling Compiz will help? I haven't had to do it, but then I've got a modern discrete graphics card. I have actually once experienced the full-screen problem you describe; temporarily disabling Compiz might be the solution.

I would recommend, if you are a hardcore gamer, building a desktop PC. With respect, not too many hardcore gamers get about with Intel integrated graphics :-)

There is a benchmark program for Linux - it's called the Phoronix Test Suite. You can get it from [www.phoronix.com](www.phoronix.com) (which is also a great Linux performance computing news and reviews website).

---

### Post by 3rdalbum on 2008-11-12
> **eternalnewbee said:**
> 
If I were you, and I had some cash, I'd buy me a decent graphic card.

Laptop. Otherwise, good idea.

---

### Post by eternalnewbee on 2008-11-12
By the way. I understood from your post that you're not exactly sure about your system specifications. You can check under: **Main Menu > System > Administration > System Monitor > System**.
There's also a very handy Application called Sysinfo, that will give you extended information about your system. You can install it from **Add/Remove Applications** in the **Main Menu**.
After the installation is complete you can find it under **Main Menu > System Tools**.
Hope this helps.

---

### Post by lisati on 2008-11-12
> **eternalnewbee said:**
> By the way. I understood from your post that you're not exactly sure about your system specifications. You can check under: **Main Menu > System > Administration > System Monitor > System**.
There's also a very handy Application called Sysinfo, that will give you extended information about your system. You can install it from **Add/Remove Applications** in the **Main Menu**.
After the installation is complete you can find it under **Main Menu > System Tools**.
Hope this helps.

Sysinfo is one of several tools that can help with learning about your system specs. If you don't mind using the terminal/command line, then the following can some up with some useful nuggets:
[code]sudo dmidecode[code]

As for the wireless: on my older Toshiba A100 laptop, the wireless has been known to sometimes cut out for no obvious reason. The only pattern I've noticed is that it seems to happen more often when the laptop has been powered up for a while, even though the case doesn't seem to be that hot to the touch. I haven't noticed a problem on my newer Toshiba M200 laptop, but I've only had it a few weeks, and often have it hooked up by ethernet.

---

### Post by eternalnewbee on 2008-11-12
> Laptop. Otherwise, good idea.:oops::oops::oops:

---

### Post by Bartender on 2008-11-12
Wait a minute.  You're a "hardcore gamer" but you bought a laptop with onboard Intel graphics??

Don't get me wrong, Intel graphics chips and Ubuntu play well together, but it sounds like your problem isn't Ubuntu.

The problem is you're asking too much from a basic laptop.

EDIT:  I'm not a hardcore gamer.  Aren't most of those games you mention written for Windows?  Are you running them under WINE or what?

---

### Post by D-TurboKiller on 2008-11-12
Thank you all for your replies!

**eternalnewbee**:
Laptop, onboard Intel card. 'nuff said.
Yes, I do wish I had a better computer, but you don't need a crazily powerful computer to be a hardcore gamer. You just need good games which offer a challenge and of course are fun to play.

**3rdalbum**:
I'm pretty sure I don't have graphics drivers installed. Urban Terror is running at less than 1 FPS in-game; In Vista it would easily top 60 FPS. Also the game has some garbled graphics. Same thing for Neverball: low FPS, a LOT of garbled graphics. Vista? Again, more than 60 FPS.
Well, I'd disable Compiz, but I have no idea how.
And thanks for the benchmark program, it'll prove to be very useful! After I install the graphics drivers, that is. But for that **I NEED A TUTORIAL...**

**lisati**:
Hey thanks! Here's what I got:

> # dmidecode 2.9
SMBIOS 2.4 present.
34 structures occupying 1534 bytes.
Table at 0x000FCD10.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: V1.60  
	Release Date: 09/19/2007
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
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
	BIOS Revision: 6.24
	Firmware Revision: 188.11

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: TOSHIBA
	Product Name: Satellite L40
	Version: PSL48E-01T00GPT
	Serial Number: X7191891R
	UUID: 9B3B81DC-8874-C8C1-CC00-001D60F5B140
	Wake-up Type: Power Switch
	SKU Number:                     
	Family:                     

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: TOSHIBA
	Product Name: Satellite L40
	Version: 1.0       
	Serial Number: BSN12345678901234567
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
	Manufacturer: TOSHIBA
	Type: Notebook
	Lock: Present
	Version:                       
	Serial Number:                       
	Asset Tag:                       
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket 478
	Type: Central Processor
	Family: Pentium M
	Manufacturer: Intel            
	ID: FD 06 00 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 15, Stepping 13
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) Dual CPU T2310 @ 1.46GHz        
	Voltage: 1.4 V
	External Clock: 133 MHz
	Max Speed: 1467 MHz
	Current Speed: 1463 MHz
	Status: Populated, Enabled
	Upgrade: Socket 423
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Instruction
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 2048 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		Other
		70 ns
		60 ns
		50 ns
	Supported Memory Types:
		Standard
		DIMM
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 2
		0x0008
		0x0009
	Enabled Error Correcting Capabilities:
		None

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: 0 1
	Current Speed: Unknown
	Type: Standard DIMM SDRAM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 2 3
	Current Speed: Unknown
	Type: Standard DIMM SDRAM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON3602
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON3601
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON3601
	Internal Connector Type: None
	External Reference Designator: USB3
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON3501
	Internal Connector Type: None
	External Reference Designator: MODEM
	External Connector Type: RJ-11
	Port Type: Modem Port

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON3501
	Internal Connector Type: None
	External Reference Designator: LAN
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON2202
	Internal Connector Type: None
	External Reference Designator: Headphone Out
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON2301
	Internal Connector Type: None
	External Reference Designator: Mic In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON1302
	Internal Connector Type: None
	External Reference Designator: Video
	External Connector Type: DB-15 female
	Port Type: Video Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON3301
	Internal Connector Type: None
	External Reference Designator: SD/MMC/MS/XD
	External Connector Type: Other
	Port Type: Other

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON2802 - PRI SATA
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CON2803 - SEC IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0015, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Short
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0016, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI2
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0017, DMI type 11, 5 bytes
OEM Strings
	String 1: PSL48E-01T00GPT,H07695PT

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		en|US|iso8859-1
		fr|FR|iso8859-1
		ja|JP|unicode-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x0019, DMI type 15, 35 bytes
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

Handle 0x001A, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x001B, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x001A
	Partition Width: 0

Handle 0x001C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer0
	Serial Number: AssetTagNum0
	Asset Tag: N/A                           
	Part Number: N/A                           

Handle 0x001D, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000400
	Ending Address: 0x00003496BFF
	Range Size: 53850 kB
	Physical Device Handle: 0x001C
	Memory Array Mapped Address Handle: 0x001B
	Partition Row Position: Unknown
	Interleave Position: Unknown

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001A
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM1
	Bank Locator: BANK1
	Type: DDR2
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer1
	Serial Number: AssetTagNum1
	Asset Tag: N/A                           
	Part Number: N/A                           

Handle 0x001F, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000800
	Ending Address: 0x000034BCBFF
	Range Size: 54001 kB
	Physical Device Handle: 0x001E
	Memory Array Mapped Address Handle: 0x001B
	Partition Row Position: Unknown
	Interleave Position: Unknown

Handle 0x0020, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0021, DMI type 127, 4 bytes
End Of Table

Hope this helps in any way ;)

**Bartender:**
See my response to eternalnewbee.
And yeah, all those games are available for Windows (Well, I have Windows Vista installed for some reason :P ) but ALSO for Linux. Wine is not necessary.

---

### Post by D-TurboKiller on 2008-11-13
*bump*
Still need help. A lot.

---

### Post by D-TurboKiller on 2008-11-13
*bump*
Still no answers... I REALLY need help here...
Even if you can't answer them all I'd still appreciate it if you could answer one or two...

---

