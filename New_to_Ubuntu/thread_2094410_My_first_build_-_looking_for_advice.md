---
title: "My first build - looking for advice"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by Statler on 2012-12-13
Hi all,

This is my first post to the forum - and it will appropriately be looking for advice about my first build & experience with Ubuntu :p 
(Apologies in advance for beginners' word-smithing below) 


Let me begin by explaining what I want it to do. 
[INDENT]1. Needs to act as my media server; ripping, streaming, & storing all my movies & music [/INDENT]
[INDENT]2. Gain & store backups of the other home PC & laptop [/INDENT]
[INDENT]3. Ethernet wired to networked home receiver[/INDENT]
[INDENT]4. Head - Output via HDMI to the living room TV [/INDENT]
[INDENT]5. Stable & solid PC[/INDENT]
[INDENT]6. I'm not a gamer, but I do want to stream HD movies [/INDENT]


Here's my plan so far,

_MoBo_: ASUS M5A97 LE R2.0 AM3+ Motherboard - ATX, Socket AM3+, AMD 970 Chipset, AMD FX, 2133MHz DDR3 (O.C.), SATA 6.0 Gb/s, RAID, 8-CH Audio, Gigabit LAN, USB 3.0, CrossFireX Ready

_CPU_: AMD FD6100WMGUSBX FX-6100 Processor - Six Core, 8MB L3 Cache, 6MB L2 Cache, 3.30GHz (3.90GHz Max Turbo), Socket AM3+, 95W, Fan, Unlocked, Retail

_Memory_: Kingston HyperX Blu KHX1600C10D3B1/8G 8GB Desktop Memory Module - DDR3, 1600MHz, CL10, DIMM, 240 Pin

_Storage_: Seagate Barracuda ST2000DM001 2TB Serial ATA Hard Drive - 2TB, 7200RPM, 64MB, SATA 6Gb/s

_Vid Card_: XFX PV-T86S-ZHF2 GeForce 8400 GS Video Card - 1GB, DDR3, 1GB, PCI-Express 2.0 (x16), DVI, HDMI, VGA, DirectX 10, Single-Slot, Low Profile

_WiFi Card_: TP-Link TL-WDN4800 450Mbps Wireless-N Dual Band PCI Express Adapter - 450Mbps, PCI Express x1, RP-SMA, Wireless-N, 3x 2dBi Antennas

_DVD-RW_: Samsung SH-224BB/BEBE Internal 24X DVD Burner -Tray, SATA, 1.5MB Buffer Memory, 16x DVD-R Read, 48x CD-R Write (OEM)

_PSU_: OEM 450W Power Supply - ATX, Dual +12V Rail, Ultra Silent

_Case_: Cooler Master RC-430-KWN1 Elite 430 Mid Tower ATX Case - ATX/Micro-ATX, USB, Audio, 120mm Blue LED Fan, Black

_Fans_: (3) SilenX EFX-12-15T Effizio Silent Thermistor Edition Case Fan - 120mm, Fluid Dynamic Bearing, 15dBA, 1400 RPM


I'm not sure yet what version of Ubuntu would be appropriate - I was planning on working with the latest LTS...

What do you think?  Any issues with drivers on the above components?  Outlandish over/underkill?

Looking forward to any advice. Thanks!

---

### Post by dannyboy79 on 2012-12-13
I have read that the AMD Phenom II X6 (6 actual cores) runs circles around the newer bulldozer chipset (FX series) so you may want to look into that.

I also just purchased the 8400 GS and love it. I am using 12.10 with the Nvidia binary from their website 310.19. HDMI out works as well as a VGA connection and it's powering a 23" Olevia HDTV, it runs at 1440x900 on VGA and 1360x768 over HDMI but that's based on the display you have it hooked to. I love it.

Are you planing on Blu Ray support? May want to look into a BluRay drive. Also not sure how streaming HD (1080p) content will be over wifi?

I read some bad things about a firmware bug with the 2TB seagate drives, may want to google that a bit.

---

### Post by oldfred on 2012-12-13
There is a sub-forum on mythubuntu
[http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301)

And one of the stickies is discussion of hard ware for recording or playing video.

---

### Post by andrew.46 on 2012-12-13
> **dannyboy79 said:**
> I have read that the AMD Phenom II X6 (6 actual cores) runs circles around the newer bulldozer chipset (FX series) so you may want to look into that.

Bulldozer got some very bad press although better results on Linux. Not sure if the 2nd generation (Piledriver) is getting better press, although I installed one yesterday and trust me it screams along :)

---

### Post by MButterman on 2012-12-14
My first bit of advice is to up the power of PSU and make sure it is a quality built one, I would recommend Antec. If you get an underpowered PSU, it will often heat up and make it less efficient and stable. Don't cheap out on the PSU, you'll thank yourself later

For the purpose you state, I use a MSI 880GM-E43. It already had video onboard plus HDMI connection.  As for a processor, you could go for a Phenom 2 quad core or six core. If you on a budget, the quad-core would do fine. The reason I run a six core is because I was able to buy one that was less than a top of the line quad core

You could get away with 512 of RAM but I would use 2Gb

Truth is Ubuntu doesn't require much hardware horsepower as other O/S's You could use less power hardware and pocket the savings for other projects.

---

### Post by andrew.46 on 2012-12-14
> **MButterman said:**
> You could get away with 512 of RAM but I would use 2Gb

Mind you I bought 8gig hyperX ram this week for about $46 AUS, amazingly cheap. Buy in big numbers I would say...

---

### Post by Statler on 2012-12-14
> **MButterman said:**
> My first bit of advice is to up the power of PSU and make sure it is a quality built one, I would recommend Antec. If you get an underpowered PSU, it will often heat up and make it less efficient and stable. Don't cheap out on the PSU, you'll thank yourself later

For the purpose you state, I use a MSI 880GM-E43. It already had video onboard plus HDMI connection.  As for a processor, you could go for a Phenom 2 quad core or six core. If you on a budget, the quad-core would do fine. The reason I run a six core is because I was able to buy one that was less than a top of the line quad core

You could get away with 512 of RAM but I would use 2Gb

Truth is Ubuntu doesn't require much hardware horsepower as other O/S's You could use less power hardware and pocket the savings for other projects.


Thanks for the info.  Moving to that MB will save some cost as well, plus save on the extra cards.  The $$ saved will go towards upgrading the PSU.

Thanks again for the advice!

---

### Post by Statler on 2012-12-14
> **dannyboy79 said:**
> I have read that the AMD Phenom II X6 (6 actual cores) runs circles around the newer bulldozer chipset (FX series) so you may want to look into that.

I also just purchased the 8400 GS and love it. I am using 12.10 with the Nvidia binary from their website 310.19. HDMI out works as well as a VGA connection and it's powering a 23" Olevia HDTV, it runs at 1440x900 on VGA and 1360x768 over HDMI but that's based on the display you have it hooked to. I love it.

Are you planing on Blu Ray support? May want to look into a BluRay drive. Also not sure how streaming HD (1080p) content will be over wifi?

I read some bad things about a firmware bug with the 2TB seagate drives, may want to google that a bit.


Good call on the BluRay drive.  I was wondering about the wifi capabilities as well - I upgraded the router to dual band N900, but it still seems iffy.
I'll be hard wired to my AVR, so anything from storage would be fine.

Thanks for the tip on the seagate drives.  After a little reading it looks like I'm better off with a WD or Samsung.

Thanks again for the advice!

---

