---
title: "MB recomendation"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by westcoast01 on 2012-03-25
Checked to see if there is another post on this but surprisingly nothing came up so here it is. The machine that I built specifically for Ubuntu has a major problem in that I must run a mem test, cancel test, in order to boot. This really sucks! Another Linux lesson learned, but before I go onto 12.04 I want to replace the mother board, I do prefer full size ATX boards. Any suggestions? Thanks, West.

Seagate Barracuda 7200.12 ST3500413AS 500GB 7200 RPM SATA 6.0Gb/s
3.5" Internal Hard Drive -Bare Drive
PNY 2GB 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop
Memory Model MD2048SD3-1333-V2
Rosewill DESTROYER Black Gaming ATX Mid Tower Computer Case,
comes with Three Fans-1x Front Blue LED 120mm Fan, 1x Top 120mm
LITE-ON DVD Burner - Bulk Black SATA Model iHAS124-04 – OEM
BIOSTAR A770E3 AM3 AMD 770 ATX AMD Motherboard
Rosewill 20" Serial ATA Red Flat Cable w/ Locking Latch Support 6 Gbps, 3
Gbps, and 1.5 Gbps transfer rate Model RCW-204
AMD Phenom II X2 555 Black Edition Callisto 3.2GHz Socket AM3 80W Dual-
Core Desktop Processor - C3 Revision HDZ555WFGMB OX
Antec BP550 Plus 550W Continuous Power ATX12V V2.2 80 PLUS
Certified Modular Active PFC Power Supply
Used: EVGA GE Force 7800 gts (PCIE)
Used: EDIMAX EW-7128G PCI Wireless Card

---

### Post by collisionystm on 2012-03-25
Have you checked your BIOS options to disable the memtest?

---

### Post by mal1958 on 2012-03-25
Westcoast, as collisionystm said, check the bios.  You can do this by pressing and holding a key (normally a function key, and most times it is F1) when you do a reboot.  When you reboot, Before grub loads (in fact, I start pressing the key as soon as I can).  That should bring you into the bios screen.  Now here, you must be careful.  Use the arrow keys to move around the screen and find the section that deals with mem test.  You should be able to disable it from there.

Edit:  And when you have solved the problem, please mark this thread solved to help others who may have a similar problem find it.  Take care.

---

### Post by westcoast01 on 2012-03-25
Hi mal1958 & collisionystm, thanks but on this MB when I check the bios (F12) it reads "no bios found". Well of course there is a bios??? I went to the manufacturers web site to find out that there is zero support for anything linux only MS. Coming from MS I never imagined that I needed to check out the bios compatibility (my linux lesson). Well if your company does not support linux then I will not use it! Hence my MB query. Thanks again and I hope to find a MB soon that has Linux support. West.

---

### Post by anewguy on 2012-03-25
It really shouldn't make any difference about official support from a vendor for the motherboard.  More importantly, getting into the BIOS set-up is independent of operating system.  Some motherboards have the option for long or short tests at power up or reset.  I believe the memory test is usually included in that but may be separate.

The point is that when you boot your machine, while the PC is starting up there should be a note on the screen on how to get into the BIOS setup - it could be F1, it could be the delete key - I haven't checked the site for you motherboard to check it.

Get into that setup, disable the long memory test and the long tests at boot.  Save and exit and let it boot.

Linux support is way beyond that stage.  While a vendor may not say they support Linux, I would be more than amazed if you have found a motherboard that can't run linux.

Dave ;)

---

### Post by collisionystm on 2012-03-25
No Bios found?

Well that would leave me to believe you have a corrupt chipset. Honestly I am surprised the machine boots if that is indeed the message you are receiving. 

However if my memory serves me right... With ever biostar I ever had it was always F1 or ESC to enter the bios.

---

### Post by westcoast01 on 2012-03-25
Hello guys, misunderstood you a little, the delete key is the entry to bios set up, F12 is for bios flash and bios version. F12 shows "no bios found". Not exactly sure what you mean but the bios is set for quick boot, the memory timing is correct, memory hole remapping is disabled. As far as I can tell the problem is after leaving basic input/output there is a timing issue with the PCIE graphics. (no onboard gpu). After six months of frustration I am ready to try some different hardware. I'll keep working on it but ... Hey you guys are the greatest, I really appreciate all the help, maybe we can get this figured out. Thanks again, West.

---

### Post by motoroller on 2012-03-25
to answer your original question, I've had good luck with my ASUS M5A97.... The UEFI BIOS it comes with is really easy to set up and use. I mean, ridiculously easy. It's all graphical with mouse support, and has basic and advanced modes depending on what you want to do. 

It's a full-size ATX board and I believe it supports up to 32 GB memory, has 6 SATA ports, and of course, has a AM3+ socket.

Just my experience personally but I've had good luck with ASUS.

---

### Post by anewguy on 2012-03-25
+1.  I use the same motherboard - it also has a couple of USB 3 ports, but I don't have any USB 3 devices.  Plenty of "regular" USB ports.  I'm running an AMD 8120, very slightly overclocked, nVidia GTS 450 and the thing has been rock solid.

> **motoroller said:**
> to answer your original question, I've had good luck with my ASUS M5A97.... The UEFI BIOS it comes with is really easy to set up and use. I mean, ridiculously easy. It's all graphical with mouse support, and has basic and advanced modes depending on what you want to do. 

It's a full-size ATX board and I believe it supports up to 32 GB memory, has 6 SATA ports, and of course, has a AM3+ socket.

Just my experience personally but I've had good luck with ASUS.

---

### Post by mal1958 on 2012-03-26
Did a quick search on the web and found your MB.  [[COLOR="Blue"]_Here is a link_[/COLOR]]("http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=450&tab=3") for you to get the manual for it, and the standard bios it uses (AMI)  This should tell you what each and every setting for the MB and the BIOS is for.  Hope this helps.

---

### Post by anewguy on 2012-03-28
> **mal1958 said:**
> Did a quick search on the web and found your MB.  [[COLOR="Blue"]_Here is a link_[/COLOR]]("http://www.biostar.com.tw/app/en/mb/introduction.php?S_ID=450&tab=3") for you to get the manual for it, and the standard bios it uses (AMI)  This should tell you what each and every setting for the MB and the BIOS is for.  Hope this helps.

Love your signature! And BTW - that's MISTER idiot to you! ;) ;)

Hope you have a good one!

Dave ;)

---

### Post by mal1958 on 2012-03-28
> **anewguy said:**
> Love your signature! And BTW - that's MISTER idiot to you! ;) ;)

Hope you have a good one!

Dave ;)

A bit off topic here but I chose this sig because I have a warped sense of humor.  Once I can replace Methusela (My current System) with something a bit more up to date, I probably will be putting my system specs in it like many here do.  This P3 1 gig system with its 512 'meg' of ram and a 135 watt power supply is old and on it's last legs.  

And I hope you have a good one too.

---

### Post by cmcanulty on 2012-03-28
that system should run lubuntu or other lighter weight linux fine.

---

### Post by mal1958 on 2012-03-28
> **cmcanulty said:**
> that system should run lubuntu or other lighter weight linux fine.

Again, I am off topic and I am sorry, but this system runs full Ubuntu 10.04 just peachy now. (plus I can play one of my favorite games Neverwinter Nights 1 on it) I can't do a dual boot since win xp is no longer supported, and I cannot install vista or win7 to this ancient box.  the full flavor works just fine and I have no complaints, save I know this system will probably not last this year out.  In fact, I will be surprised if I make it to June or July with it.  But without a real job, I have a problem in pulling some money together to get a more modern system.

---

