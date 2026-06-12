---
title: "Ubuntu64 Not running on 64bit Dual-core"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by cpgifford on 2012-06-17
So I'm Relatively new to Linux beside rooting and modding Android. I have installed Ubuntu in the past on most my machines but never made the leap into full on linux, mainly because it lacked some stupid feature windows had or something to that affect. Anyways, 


My Question is. When I try to boot Ubuntu-64 From a Live CD, It shows alot of white "stuff" on the screen. It honestly looks like it has the wrong driver installed because i can see little things like text but its jumbled up to make it unrecogizable. I can run and install Ubuntu-32 Just fine without a Hitch but 64 just doesnt want to work. Any Ideas?

BTW Computer Specs

HP DV6140US Series Laptop
US Product Number	RG274UA#ABA
Microprocessor	1.8 GHz AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-56
Microprocessor Cache	2 X 512KB L2 Cache
Memory	2048MB DDR2 System Memory (2 Dimm)
Memory Max	2048MB
Video Graphics	NVIDIA GeForce Go 6150 (UMA)
Video Memory	up to 128MB (shared)
Hard Drive	120GB 5400RPM (SATA)
Multimedia Drive	LightScribe SuperMulti 8X DVD±RW with Double Layer Support
Display	15.4” WXGA High-Definition BrightView Widescreen (1280 x 800) Display
Fax/Modem	High speed 56k modem
Network Card	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity	 802.11b/g WLAN
HP Features	HP Imprint finish & HP Pavilion WebCam with Integrated Microphone
Sound	Altec Lansing
Keyboard	101-key compatible

2 Quick Launch Buttons (HP Quick Play Menu and DVD buttons)
Pointing Device	Touch Pad with On/Off button and dedicated vertical Scroll Up/Down pad
PC Card Slots	
1 ExpressCard/54 Slot (also supports ExpressCard/34)
External Ports	
5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
3 Universal Serial Bus (USB) 2.0
2 Headphone out - 1 w/SPDIF Digital Audio & 1 stereo
1 microphone-in
1 VGA (15-pin)
1 TV-Out (S-video)
1 RJ-11 (modem)
1 RJ -45 (LAN)
1 notebook expansion port 3
1 IEEE 1394 Firewire (4-pin)
1 Consumer IR

---

### Post by anewguy on 2012-06-17
You will probably need the nomodeset option to boot.  It seems that some nVidia adapters need that option.

[See this]("http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation").

Dave ;)

---

