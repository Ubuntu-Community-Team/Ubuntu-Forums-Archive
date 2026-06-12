---
title: "Will i3 or i5 processors work with Ubuntu?"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by resander on 2012-09-15
I am thinking about getting a new desktop based on an Intel i3 or i5 processor. The last two release families of the i-series are code-named Sandy Bridge (2nd generation) and Ivy Bridge (3rd Generation). The latter appeared a couple of months ago use less power, are a bit faster and have improved onchip graphics.

I am considering:
 
-  Ivy Bridge   i3-3240 dual-core 3.3 GHz 3MB onchip cache, 55W or
-  Ivy Bridge   i5-3570 quad-core 3.4 GHz 6MB onchip cache, 77W or   
-  Sandy Bridge i3-2120 dual-core 3.3 GHz 3MB onchip cache, 65W or
-  Sandy Bridge i5-2500 quad-core 3.4 GHz 6MB onchip cache, 95W

Q1.  will the above models or any other i-series model work with Ubuntu?
Q2.  did you have to tweak and do extra steps not needed for other more 'classical' CPUs? Was it difficult? For example, did you have to install a more recent version of Linux (to get current linux version enter uname -r from the command line), did you have to download and install anything extra? Anything not working that should be, etc, etc...
Q3.  Ubuntu and Linux versions used?  

Ken

---

### Post by Bufeu on 2012-09-15
It'll work.

---

### Post by Sylos on 2012-09-15
I am running an i5 2500K with no additional tweaking required (not for the CPU anyway). If your looking at the i5 2500 hen I would recomend looking at the price difference between it and the 2500K. The 2500K is unlocked so it can be overclocked (subject to having a suitable motherboard, PSU, cooling etc). I havent done the OC yet but I hear they clock rather well.

Cheers

---

### Post by lolpenguin on 2012-09-15
No problems with mainstream Intel processors. They'll work fine as long you don't use ancient (5+ years old) versions of Ubuntu.
Overclocking is the same as Windows, done from the BIOS.

---

### Post by Wim Sturkenboom on 2012-09-15
I'm using a i3-2120 with 8GB memory on an Asrock H61M-VS motherboard; no additional video card. Ubuntu 12.04 and Win7 Home Basic 64 in dual boot.

Issues encountered
[LIST=1]
[*]After install of Ubuntu, the system booted straight into Windows; no grub menu. Solution found in [http://ubuntuforums.org/showthread.php?t=1974392](http://ubuntuforums.org/showthread.php?t=1974392)
[*]Windows worked fine in 1920x1200 resolution on Acer X243W monitor, but Ubuntu wouldn't really. This was solved after swapping the VGA cable (don't ask why).
[/LIST]

---

### Post by oldfred on 2012-09-15
The issue is not the processor.

This site has reviews of many of the new Intel processors. Your porbably have to read all the reviews to pick up the minor issues, but generally he says the new Intel chips work well with the newer versions of Ubuntu.

[http://www.phoronix.com/scan.php?page=article&item=intel_corei5_3470&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei5_3470&num=1)

For old time users, there are major changes. Almost all the new motherboards with the new i series processor are UEFI. They will also boot in BIOS mode. But if you dual boot you have to install both Windows & Ubuntu in UEFI with gpt partitioning or both in BIOS with MBR partitioning. Whichever mode you boot install media in, will be the mode it installs.

---

### Post by resander on 2012-09-20
Many thanks, it is reassuring to hear you have had little or no difficulty in getting the Intel i-series work with Ubuntu.

Oldfred, special thanks for letting me know about phoronix. It is brilliant. I read the article/benchmark about the i5 3470 and also found the following very useful:
  
-  Intel Core i7 3770K Ivy Bridge Linux Performance
     [http://www.phoronix.com/scan.php?page=article&item=intel_corei7_3770k&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_corei7_3770k&num=1)
-  Intel HD 4000 Ivy Bridge Graphics On Linux   [http://www.phoronix.com/scan.php?page=article&item=intel_hd4000_ivybridge&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_hd4000_ivybridge&num=1)
-  Intel HD 2500 Ivy Bridge Graphics On Linux  [http://www.phoronix.com/scan.php?page=article&item=intel_hd2500_ivybridge&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_hd2500_ivybridge&num=1)


Having read these I think my choice will be i7-3770 or possibly i5-3570, the only i5 with inbuilt graphics HD 4000. Have been surfing to the big online stores and UK companies that build custom PCs and found a wide spectrum of specs and prices. For example:  

i7:  predefined (with very limited configurability)
English Windows® 7 Professional (64 BIT) for Emerging Markets
3rd generation Intel® Core™ i7-3770 processor (3.40GHz with Turbo Boost 2.0 up to 3.90GHz)
4GB (2X2GB) 1600 MHz DDR3 Non-ECC
1TB Serial ATA III (7.200 Rpm) Hard Drive
NVIDIA® GeForce GT 640 1GB Graphics Card
16X DVD+/-RW Drive
Driver 1703 Wireless Card
19-in-1 Multicard Reader
Dell Wireless 1703 802.11b/g/n, Bluetooth v4.0+LE
Motherboard Intel with H77 ??? (not in online info, got from call centre)

i5: configurable from custom PC providers
English Windows® 7 Home Premium (64 BIT) optional
3rd generation Intel® Core™ i7-3770 processor 3.40GHz
4GB (2X2GB) 1333 MHz DDR3 Non-ECC (Samsung, Kingston, Corsair)
500GB or 1TB Serial ATA III (7.200 Rpm) Hard Drive generic or branded
Graphics cards: many from xxx to xxxNVIDIA® GeForce GT 640 1GB
16X-24x DVD+/-RW Drive
Motherboard Asus P8Z77-M, P8Z77-V and many more


I am currently using a 6-8 year old Compaq desktop that is beginning to show signs of age. It is pleasantly quiet for browsing, word processing, simple drawing, design and program development, but when using it for converting movie formats (with DeVeDe) it soon becomes very noisy. Converting a dvd takes about 3-5 hours. Noise and duration intolerable!

I want the i-series replacement PC to be reasonably quiet too most of the time. When it is working flat out, for example with video conversion, I understand it cannot be as quiet, but it must not sound like a vacuum cleaner. I am not playing games so video format conversion is probably going to be the most compute-intensive task for this PC. In the light of this:

Q1. how quiet or noisy is your i-series PC? Like it is quiet enough for x type of tasks but would need extra fans/cooling for y tasks... 

Q2. how does having or not having a graphics card affect the noise level
and temperature levels. For example, would a PC without a graphics card using only HD 4000 be cool enough and hence quiet without any specials?

Q3. if I get a Custom PC I can have it 'sound-proofed'. I know there are quiet cpu fans, quiet power supplies, insulated computer cases and probably more. What should be prioritised? The cpu fan? Anything that would only have marginal effect? Is sound-proofing really needed for my type of usage?

Q4. Would an i-series PC always have/need temperature monitoring? (my Compaq has none as far as I can see). What about fan control? The big online suppliers never mention that in their ads, the Custom PC builders usually list fan control as an option. 

Q5. HD 4000/2500 GPU would be equivalent to what graphic cards?


Hoping for your assistance in selecting a system.

Ken

---

### Post by vexorian on 2012-09-20
Just remember to disregard the supposed "recommendation" to use 32 bits ubuntu and use the 64 bits version. If you go with 32 bits, you will get performance similar to having something older than an i5. But with 64 bits ubuntu, it will fly (Speaking from experience here).

---

### Post by jrog on 2012-09-20
Just to add to the data, I am running Ubuntu 12.10 Beta 1 on an i5-3210M (see my signature) and it is going excellently. However, I *was* encountering occasional system locks on a stock install of Ubuntu 12.04 LTS. I upgraded to 12.10 Beta 1 for the latest Linux kernel support; I believe it will make a difference to your experience with some of these newer processors. It apparently has in my case -- I haven't had an issue since upgrading.

EDIT: Oh, you asked for the kernel version used, so here you go: Linux 3.5.0-15-generic

---

### Post by oldfred on 2012-09-20
I think they post this once a month. The last page is a chart of approximate equivalents. But if upgrading you have to move more than 2 tiers to really see much difference. Does not discuss Linux compatibility or performance with Linux but gives some idea based on the hardware.
[http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107.html](http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107.html)

I have not edited video, but seen some posts on swap vs. RAM that when editing video you cannot have enough RAM. With RAM as cheap as it is now, I would suggest more.

---

