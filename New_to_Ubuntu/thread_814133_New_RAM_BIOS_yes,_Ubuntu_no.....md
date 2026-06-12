---
title: "New RAM: BIOS yes, Ubuntu no....?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by spoonmason on 2008-05-31
I have ubuntu 8.04 on an hp ( [http://reviews.cnet.com/desktops/hp-pavilion-734n-athlon/4507-3118_7-20832635.html](http://reviews.cnet.com/desktops/hp-pavilion-734n-athlon/4507-3118_7-20832635.html)  )
I installed a new stick of RAM (512MB)
The BIOS recognizes it but Ubuntu does not...
What do I do?????

---

### Post by shifty_powers on 2008-05-31
what makes you say ubuntu does not?

---

### Post by jd65pl on 2008-05-31
You may want to look at the "free" command
```

man free

```

---

### Post by quelx on 2008-05-31
How much RAM does the BIOS say you have and how much does Ubuntu say you have?

Open a terminal **Applications** > **Accessories** > **Terminal**

type ```
cat /proc/meminfo |grep MemTotal
``` **<enter>**

---

### Post by spoonmason on 2008-05-31
Terminal prints out:     255684 kB
I have two 512MB sticks installed... All I did was install the hardware what is should I do?

---

### Post by shifty_powers on 2008-05-31
go system>administration>system monitor>resources

take a screenshot and post it ;)

---

### Post by spoonmason on 2008-05-31
********-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           249        244          5          0          3         53
-/+ buffers/cache:        187         61
Swap:         1466        199       1267
*********-desktop:~$ free -g
             total       used       free     shared    buffers     cached
Mem:             0          0          0          0          0          0
-/+ buffers/cache:          0          0
Swap:            1          0          1
*********-desktop:~$

---

### Post by spoonmason on 2008-05-31
[IMG]http://i87.photobucket.com/albums/k140/spoon_mason/Screenshot.png[/IMG]

so... its in swap?

---

### Post by spoonmason on 2008-05-31
sorry that was so big...

---

### Post by shifty_powers on 2008-05-31
no, swap is like the page file in windows.

brb.

---

### Post by shifty_powers on 2008-05-31
right type

```
sudo dmidecode
```

into a terminal and post the out put.

put it in code tags as it is a long list;)

---

### Post by spoonmason on 2008-05-31
```
# dmidecode 2.9
SMBIOS 2.3 present.
38 structures occupying 1103 bytes.
Table at 0x000F0800.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: AM37308
	Release Date: 12/16/2002
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 512 kB
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
		5.25"/360 KB floppy services are supported (int 13h)
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
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer: HP Pavilion 06
	Product Name: DA192A-ABA 734N
	Version: 05/1211RE101SALSA
	Serial Number: MX25123945 NA920
	UUID: 0032F578-F149-D711-9DC4-8AE127278698
	Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer:  
	Product Name: KM266-8235
	Version:  
	Serial Number: KE1249084684

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer:  
	Type: Desktop
	Lock: Not Present
	Version:  
	Serial Number:  
	Asset Tag:  
	Boot-up State: Unknown
	Power Supply State: Unknown
	Thermal State: Unknown
	Security Status: Unknown
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket A
	Type: Central Processor
	Family: Duron
	Manufacturer: AMD
	ID: 81 06 00 00 FF FB 83 03
	Signature: Family 6, Model 8, Stepping 1
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
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
	Version: AMD Athlon(tm) XP
	Voltage: 1.6 V
	External Clock: 133 MHz
	Max Speed: 1500 MHz
	Current Speed: 2000 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0009
	L2 Cache Handle: 0x000A
	L3 Cache Handle: Not Provided
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x0005, DMI type 5, 22 bytes
Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: Four-way Interleave
	Maximum Memory Module Size: 32 MB
	Maximum Total Memory Size: 96 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Standard
		EDO
	Memory Module Voltage: 5.0 V
	Associated Memory Slots: 3
		0x0006
		0x0007
		0x0008
	Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 0 1
	Current Speed: 60 ns
	Type: Other SDRAM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2 3
	Current Speed: 60 ns
	Type: Other SDRAM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A2
	Bank Connections: None
	Current Speed: 60 ns
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 128 KB
	Maximum Size: 128 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000A, DMI type 7, 19 bytes
Cache Information
	Socket Designation: External Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: External
	Installed Size: 256 KB
	Maximum Size: 256 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRIMARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SECONDARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FDD
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: 8251 FIFO Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM1
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: LPT1
	Internal Connector Type: DB-25 female
	External Reference Designator:  
	External Connector Type: DB-25 female
	Port Type: Parallel Port ECP/EPP

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Keyboard
	Internal Connector Type: PS/2
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PS/2 Mouse
	Internal Connector Type: PS/2
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Other
	Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: AUDIO
	External Connector Type: None
	Port Type: Audio Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: ETHERNET
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x0015, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI0
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 1
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0016, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 2
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0017, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI2
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 3
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0018, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI3
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 4
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0019, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: ..

Handle 0x001A, DMI type 9, 13 bytes
System Slot Information
	Designation: AGP
	Type: 32-bit AGP
	Current Usage: Available
	Length: Long
	ID: 8
	Characteristics:
		5.0 V is provided

Handle 0x001B, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

Handle 0x001C, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 1536 MB
	Error Information Handle: Not Provided
	Number Of Devices: 3

Handle 0x001D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x001F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x001C
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A2
	Bank Locator: Bank4/5
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x0020, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x001C
	Partition Width: 0

Handle 0x0021, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x001D
	Memory Array Mapped Address Handle: 0x0020
	Partition Row Position: 1

Handle 0x0022, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x001E
	Memory Array Mapped Address Handle: 0x0020
	Partition Row Position: 1

Handle 0x0023, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x001F
	Memory Array Mapped Address Handle: 0x0020
	Partition Row Position: 1

Handle 0x0024, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0025, DMI type 127, 4 bytes
End Of Table
```

---

### Post by spoonmason on 2008-05-31
:popcorn:

---

### Post by shifty_powers on 2008-06-01
ok, going by the dmidecode, the system does indeed recognise the fact that the ram is installed.

ok, which motherboard are you using?

edit: and do you have a spare live-cd to hand?

---

### Post by OldTimeTech on 2008-06-01
You also might want to flash your bios as your running a 2002 version.

---

### Post by shifty_powers on 2008-06-01
> **OldTimeTech said:**
> You also might want to flash your bios as your running a 2002 version.

i would investigate other avenues first, and have a look at the release notes for the new bios, to see if it has any relation to this problem.

flashing the bios is NOT without risk, and should only be done as a last resort ;)

---

### Post by spoonmason on 2008-06-01
> **shifty_powers said:**
> ok, going by the dmidecode, the system does indeed recognise the fact that the ram is installed.

ok, which motherboard are you using?

edit: and do you have a spare live-cd to hand?
Sorry I haven't ever had to do this kinda stuff before... kinda why I wanted to use linux, to learn!!! :)
I don't know 'which motherboard' I am using. How do I find that out?
And I I do have 2 live cd's of ubuntu 6.** vrs and 8.04 ??


Oh ane I try'd flashing the BIOS once and it was a desaster!! I'll not do that again, untill I know more about it. :))

---

### Post by shifty_powers on 2008-06-01
ok. boot into one of the live-cd's and go into system monitor again. I want to see if it is something thet ubuntu isn't liking or just your particular installation...

---

### Post by spoonmason on 2008-06-01
ok... I did that... it read the same.
I also took out the new RAM, boot up...same
swaped new for old... same
left new in first position and but old in secound...same
BIOS read correct in each case.... I'm stumped....:|

---

### Post by shifty_powers on 2008-06-01
how old is this motherboad?

might have found it here

[http://www.via.com.tw/en/products/chipsets/legacy/km266/](http://www.via.com.tw/en/products/chipsets/legacy/km266/)

or at least the chipset it is based on....

also, what speed is the ram you have bought?

---

### Post by shifty_powers on 2008-06-01
how old is this motherboad?

might have found it here

[http://www.via.com.tw/en/products/chipsets/legacy/km266/](http://www.via.com.tw/en/products/chipsets/legacy/km266/)

or at least the chipset it is based on....

also, what speed is the ram you have bought? (this could be important ;))

---

### Post by spoonmason on 2008-06-01
I didn't buy it I just took it out of an old e-machine. It is an aftermarket stick. but I don't know any of the specs on it other then it is 512MB 

If the stick was not compatible wouldn't that keep it from showing up at all...

---

### Post by spoonmason on 2008-06-01
Also, why is it only showing what would be 256MB of RAM when if its reading one stick it should it least be 512MB????:confused:

---

### Post by spoonmason on 2008-06-11
Another thing (may be connected) in the Disk Usage Analyzer it says that my "Total filesystem capacity: **148.6** (used: 8.0 GB available: 140.6 GB)".

My Computer only has an 80 GB HDD!  When I go to 'File System' properties it reads 80 GB..... there is something wrong here... I only wish I knew what to do about it cause I would like to be able to use my full GB of RAM instead of 1/4 of it.

---

### Post by kansasnoob on 2008-06-11
"flashing the bios is NOT without risk, and should only be done as a last resort"

+1 to Mr. Shifty for that piece of advice. I've more than once opened a can of worms I later wished I hadn't by flashing my BIOS.

And if BIOS recognizes the RAM I doubt that's the problem.

---

### Post by spoonmason on 2008-06-11
well do you have any idea what the problem could be?

---

### Post by kansasnoob on 2008-06-11
I'm picking my brain (and trying to see if I made any notes in my spiral notebook), but when I built the computer I'm using now, about 4 months ago, while ordering my 2 1GB sticks of RAM I ordered 4 sticks so I could upgrade my daughter from 512mb to 2GB in her puter (it just made sense due to shipping cost savings).

But for some reason her puter/w Gutsy did not recognize the RAM upgrade until I did some darn thing. If only I could remember :confused:

---

### Post by Jazzy_Jeff on 2008-06-11
I believe your system is to old to use 512 mb sticks. My sister had the same problem on her older windows system and come to find out she could only use 2 256 mb chips. If you know the model # of the computer you pulled the mother board out of, go to crucial.com and look up the ram for that system. It will tell you what it supports.

---

### Post by spoonmason on 2008-06-11
well thats a look in the right direction\\:D/ at least I know I'm not the only one to report this type of problem.

---

### Post by kansasnoob on 2008-06-11
Oh shoot! Reading Shifty's last post made think of something. It may have been that her old RAM had a CAS Latency of 2.5 or 3, and the new Ram was slower ............. like 4 or 5 (which explains the close-out price).

But my memory sucks! Which is why I keep notes (and prefer gui to cli)............ now if I made notes in that instance is another story.

I am looking :(

Just a (very basic and incomplete) note about CAS Latency: If BIOS is set to "refresh" RAM at a faster rate than the RAM will handle you actually dump data. The numbers 2.5, 3, 4, etc. can be thought of as "ticks" of the clock so 3 is faster than 5, so if the RAM "refreshes" in 3 "ticks" but needed 5 "ticks" you actually can dump data, but I'm NOT sure at all that's what's going on here.

At the very least you can consider this a free bump.

---

### Post by kansasnoob on 2008-06-11
Silly thought! Can someone post how to properly run memtest?

Assuming that this is an Ubuntu only puter (I'm so used to dual boots that's almost all I know) how could someone run memtest (as I recall the GRUB screen doesn't show up in a single boot), and would that show any problems?

---

### Post by spoonmason on 2008-06-11
> **Jazzy_Jeff said:**
> I believe your system is to old to use 512 mb sticks. My sister had the same problem on her older windows system and come to find out she could only use 2 256 mb chips. If you know the model # of the computer you pulled the mother board out of, go to crucial.com and look up the ram for that system. It will tell you what it supports.

In response: [http://reviews.cnet.com/desktops/hp-pavilion-734n-athlon/4507-3118_7-20832635.html](http://reviews.cnet.com/desktops/hp-pavilion-734n-athlon/4507-3118_7-20832635.html) <---- will tell you that it comes with 512MB from the factory. So thats not it. ;)

oh and yes it is Ubuntu only. I haven't had time to set up a dual booty yet

---

### Post by spoonmason on 2008-06-11
I believe if I run the live CD of 8.04 then it gives the option of a memtest. I'll let you know in a min.

---

### Post by kansasnoob on 2008-06-11
I'm stuck on one thing, your original post says, "The BIOS recognizes it but Ubuntu does not...".

Uh, I really think Ubuntu should recognize it! Now, it may not work right, like you could get data loss, system crashes, etc. But Ubuntu should recognize it.

Sadly it appears that I didn't keep any notes regarding that.

If you have an Ubuntu Live CD I'm just curious what System Monitor shows when you're booted into the Live CD. If that shows all your RAM then it definitely has to be correctable.

---

### Post by kansasnoob on 2008-06-11
I hope you saw that last post before you booted the live CD :confused:

---

### Post by spoonmason on 2008-06-11
Take a look at posts #18 and #19 on page 2 of this thread I have done the System monitor thing already but not the memory test from boot. I will try that in just a min. :)

---

### Post by spoonmason on 2008-06-11
yeah I did see it :)

> **kansasnoob said:**
> I'm stuck on one thing, your original post says, "The BIOS recognizes it but Ubuntu does not...".

Uh, I really think Ubuntu should recognize it! Now, it may not work right, like you could get data loss, system crashes, etc. But Ubuntu should recognize it.

Sadly it appears that I didn't keep any notes regarding that.

If you have an Ubuntu Live CD I'm just curious what System Monitor shows when you're booted into the Live CD. If that shows all your RAM then it definitely has to be correctable.

I see... but I'm not having "data loss, system crashes, etc."... everything is working fine just not fast enough.... (not at 1 GB of RAM speeds anyway.)

the memtest from the live cd showed 256MB...](*,) it seems everything, except the BIOS, is showing that. If the BIOS wasn't reading it I would say the sticks are bad... but.... ](*,)

---

### Post by kansasnoob on 2008-06-11
If the live CD doesn't recognize it I'm clueless ........... sorry:(

I still believe Ubuntu should recognize the same amount of RAM as BIOS.

---

### Post by spoonmason on 2008-06-11
Don't be sorry that is exactly what I said. I am by no means and expert when it comes to Ubuntu but I do know that any OS should read the same components as the BIOS. I have thought about reinstalling but, if the live CD reads the same, I fear that wouldn't help.

---

### Post by kansasnoob on 2008-06-11
"if the live CD reads the same, I fear that wouldn't help."

I agree! And I believe this can be solved.

I'm sure you've already said, but are you using Hardy?

---

### Post by kansasnoob on 2008-06-11
This is possibly the dumbest thing I've ever asked, but I admit I'm dumb.

What size is your Swap?

I think gparted was installed by default in Gutsy (but don't remember for sure), while it's not installed in Hardy, but still available in synaptic.

Anyway, just check and see if Swap is ridiculously small. Just maybe (hey I have bad dreams ... it goes with age) when Ubuntu was installed it created a Swap partition based on the installed RAM and that could foul things up ............. but I'm really grabbing at straws :confused:

---

### Post by kansasnoob on 2008-06-11
I'd love to see a solution to this!

---

### Post by spoonmason on 2008-06-12
See post # 8 on page 1 :) that is a screen shot of my system monitor panel; resorses tab. 

yes I am using Ubuntu 8.04 hardy...

....and your not dumb at all! I thank you for trying to figure this out with me. Shifty is very busy and hasn't had time so I'm just glad some one else looked at my post.

Another peace of the puzzle  (that doesn't help me):popcorn:
    |
    |
   \ /
    v

> **spoonmason said:**
> Another thing (may be connected) in the Disk Usage Analyzer it says that my "Total filesystem capacity: **148.6** (used: 8.0 GB available: 140.6 GB)".

My Computer only has an 80 GB HDD!  When I go to 'File System' properties it reads 80 GB..... there is something wrong here... I only wish I knew what to do about it cause I would like to be able to use my full GB of RAM instead of 1/4 of it.

---

### Post by skymera on 2008-06-12
The RAM isn't limited by the BIOS is it?

I have 3GB installed and in the BIOS i can configure it so only 256MB is given to the OS. Why? no clue. But that might have happened to yours, have a flick through but don't change anything unless you know what your doing.

The option was called "OS Install" in my BIOS.

---

### Post by spoonmason on 2008-06-12
Hmmmm sounds like a 'worth a look' suggestion... I don't remember seeing anything like that in my BIOS but I will have a quick gander :)

Thanks for your input and any more will be greatly appreciated!!!

---

### Post by spoonmason on 2008-06-12
Nope couldn't find anything like it even.... I have went threw that BIOS at least a dozen times and haven't been able to see anything about the RAM other then 'INSTALLED RAM'...   still stumped.....

---

### Post by skymera on 2008-06-12
Just a stab in the dark here, what if you swap the sticks around?

My 512MB sticks only work in certain slots, if i change them other way round they're not recognised and i get a BIOS error.

---

### Post by melrom on 2008-06-12
> **kansasnoob said:**
> 
I think gparted was installed by default in Gutsy (but don't remember for sure), while it's not installed in Hardy, but still available in synaptic.


Why does everyone say this? Hardy ships with gparted too! Doesn't it? I could've sworn.

---

### Post by kansasnoob on 2008-06-12
I discussed this over morning coffee with a couple of friends.

The only real thing to come from it was whether or not the RAM contacts are clean. I do suppose it's possible that all RAM might show up in BIOS since BIOS uses very low system resources, whereas booting the OS would place much greater demand on system resources.

My favorite method for cleaning the contacts on the sticks themselves is using a brand new little pencil eraser (the little diamond shaped replaceable kind). Isopropyl alcohol is also nice, but I don't have to tell you that liquids and electronics don't mix! Easy does it here, contacts are easily damaged, or even folded over one another sometimes!

The DIMM slots are a little tougher. Here I usually grab a cheapo disposable plastic knife leftover from the last bbq and a small peice of lint-free cloth (white is nice because you can see how much gunch your removing) and just a couple drops of isopropyl alcohol. Here again liquids and electronics DO NOT mix so certainly make sure all power is disconnected and be certain everything is dry, dry, dry when you're done.

Of course it's always great to finish up with compressed air. Also a magnifying glass is a must have (more so for a blind old fart like me). And of course it's not only dirt and dust bunnies but also tarnish that can interfere with connectivity.

I'd also add that when cleaning be gentle and follow anti-static safety rules. Many electronic components die from just the discharge of static from the human body (nothing makes me cringe worse than seeing someone build a computer on the living room carpet). And make sure everything you work with is non-conductive! That's why I suggested the plastic knife, metal would be a major no-no. 

Otherwise I'm just stumped!

---

### Post by kansasnoob on 2008-06-12
"Why does everyone say this? Hardy ships with gparted too! Doesn't it? I could've sworn."

Melrom,

It certainly is on the live CD, it's an integral part of the installer, but I think it's not "installed" by default when the Hardy install is complete. I'm pretty sure that I've had to add it from synaptic. (Of course since partitions must be unmounted to "work" with them it's seldom used from the desktop anyway)

Then again it's been a few weeks since my last install so I could be mistaken. And my memory is bad, thus the absolute need for a spiral notebook and why I prefer gui to cli.

I'm absolute proof positive that anyone can learn Ubuntu! If I can do it it is truly idiot-proof:)

---

### Post by nhsbgeek2011 on 2008-06-12
[http://s6.gladiatus.us/game/c.php?uid=42772](http://s6.gladiatus.us/game/c.php?uid=42772)

---

### Post by spoonmason on 2008-06-12
> **skymera said:**
> Just a stab in the dark here, what if you swap the sticks around?

My 512MB sticks only work in certain slots, if i change them other way round they're not recognised and i get a BIOS error.

Tried that already. :(

> **spoonmason said:**
> ok... I did that... it read the same.
I also took out the new RAM, boot up...same
swaped new for old... same
left new in first position and but old in secound...same
BIOS read correct in each case.... I'm stumped....:|

---

### Post by spoonmason on 2008-06-23
I have received a suggestion, from my friends of a local Linux user group, to allow the memtest86 to complete itself. I haven't done this yet, as I have been told it could take several hours to complete. My hope is that it will find some error that is causing my problem and be able to fix it or give me more info so that I can try to fix it.

any comments...?

---

