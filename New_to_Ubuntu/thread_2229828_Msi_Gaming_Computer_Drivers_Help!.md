---
title: "Msi Gaming Computer Drivers Help!"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by Henry_Prickett-Mor on 2014-06-15
I have a newish (august 2013) gaming rig. I have been running windows 7 without incident for over a year, so the hardware is fine. However, yesterday I decided to try dual booting windows 7 and Ubuntu 14.04. I have re-installed multiple times but have finally gotten it working. My question is: Will Ubuntu require the 10s of drivers that windows wants to get working? 
The Hardware
Power Supply: Themaltake SMART Series SP-750PCBUS 750W ATX 12V 2.2 SLI Ready CrossFire Ready 80 PLUS BRONZE Certified Active PFC Power ...
HDD: Seagate Barracuda STBD2000101 2TB 7200 RPM SATA 6.0 Gb/s 3.5" Internal Hard
Processor: Intel Core 15-4670 Haswell 3.4 GHz LGA 1150 84W Quad-Core Desktop Processor Intel HD Graphics BX80646154670
Mother Board: MSI Z87-G45 Gaming LGA 1150 Intel Z87 HDMI SATA 6Gb/s USB 3.0 ATX Pro Gaming with Killer Networking & Soundblaster Intel
Ram: G.Skill Ripjaws X Seiries 16GB (2x8GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model F3-1600C9D-16GXM
Dvd/Cd Drive: ASUS DRW-24B1ST/BLK/B/AS Black SATA 24x DVD Burner - Bulk - OEM
Video Card: nVIDIA EVGA GTX 580
Thanks in advance:).

---

### Post by Mark Phelps on 2014-06-15
> Will Ubuntu require the 10s of drivers that windows wants to get working? 

The Ubuntu installer collects the drivers needed based on hardware detection and installs them for you.

If some piece of hardware is not working after install, that means the driver was not installed -- and unlike with Windows, you're probably NOT going to find it by doing various Web searches.  There is the utility of Additional Drivers, but that only supports video and WiFi drivers, not other devices.

And, before someone misleads you otherwise, you can not use Wine to install Windows drivers.

---

