---
title: "AMD Radeon HD 6800"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by Emile_Beaulieu on 2014-06-09
Hi all! I'm new to Linux, and have chosen ubuntu as my first attempt. I downloaded the newest version, created a boot flash drive, and installed it with no issues on my old netbook. 

I've played around a little, and have decided to try it out on my main computer.

Unfortunately, the install is going bad right at the start. After inserting the usb flash drive and booting the computer, after the intial loading screen, I get the screen in the picture that I attached. All the characters are just coming up as squares. 

I didn't have this issue when I installed this on the netbook.

Any ideas?

---

### Post by mörgæs on 2014-06-09
Hi, welcome to the fora.
Please begin with a complete hardware description.

---

### Post by Emile_Beaulieu on 2014-06-09
OS Name	Microsoft Windows XP Professional
Version	5.1.2600 Service Pack 3 Build 2600
OS Manufacturer	Microsoft Corporation
System Name	BEDROOM
System Manufacturer	HP-Pavilion
System Model	GX609AA-A2L m9160f
System Type	X86-based PC
Processor	x86 Family 6 Model 15 Stepping 11 GenuineIntel ~2666 Mhz
BIOS Version/Date	American Megatrends Inc. 5.43, 9/10/2009
SMBIOS Version	2.5
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.5512 (xpsp.080413-2111)"
User Name	BEDROOM\home2
Time Zone	Eastern Daylight Time
Total Physical Memory	4,096.00 MB
Available Physical Memory	1.91 GB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	5.09 GB
Page File	C:\pagefile.sys

---

### Post by Emile_Beaulieu on 2014-06-09
Processor
[COLOR=#000000][FONT=Times New Roman]2.67 gigahertz Intel Core2 Quad[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]64 kilobyte primary memory cache[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]4096 kilobyte secondary memory cache[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]64-bit ready[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Multi-core (4 total)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Not hyper-threaded

[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]Board: PEGATRON CORPORATION Benicia 1.01[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Bus Clock: 1066 megahertz[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]BIOS: American Megatrends Inc. 5.43 09/10/2009

[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]3328 Megabytes Usable Installed Memory

[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]AMD Radeon HD 6800 Series [Display adapter][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Insignia NS-39E480A13 [Monitor] (39.0"vis, August 2012)

[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]AMD High Definition Audio Device[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Realtek High Definition Audio[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2014-06-09
Err... The mod's request was a "complete hardware description". What OS is already installed for this matter is COMPLETELY irrelevant. Your list gives some useful informations but many other parts are missing, namely the graphics card. According to this store [http://www.rakuten.com/prod/hp-pavilion-elite-desktop-computer-intel-core-2-quad-q6700-2-66ghz/207536116.html](http://www.rakuten.com/prod/hp-pavilion-elite-desktop-computer-intel-core-2-quad-q6700-2-66ghz/207536116.html) it has a nVidia GeForce 8600GT, on top of a Intel G33 chipset.

I hope it helps [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar939075_12.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=939075") 				 				 					 						 	[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075") in suggesting some troubleshooting. I suspect This graphics card/chip requires the 'nomodeset' option but I'll wait for some expert input.

---

### Post by Emile_Beaulieu on 2014-06-09
Ya, I realized after I posted the first one, and posted a second message with more hardware info.

---

### Post by Vladlenin5000 on 2014-06-09
I have no suggestion at the moment. Please wait for the real experts ;). And please ignore my previous comment about 'nomodeset' (n/a for ATI/AMD).

---

### Post by mörgæs on 2014-06-10
Thanks for the hardware list. I changed the thread title in order to catch the attention of an ATI/AMD expert, which I am not. 

My only (low-tech) solution would be to try to install using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). The link mentions weak hardware but the approach is also worth trying when new gear is causing trouble.

---

### Post by monkeybrain20122 on 2014-06-10
This may sound stupid but sometimes it is because of your usb port, try insert the live usb into a different port (something similar happened to me once, somehow connection was loose in one of the ports which might be damaged)

---

### Post by Emile_Beaulieu on 2014-06-10
I tried a different USB port, but the problem persisted. 
I have read about a method of installing ubuntu directly from windows, so I may try it that way and see if that has more success.
I also took a guess from that first screen, with a list menu on the left, and two pictures (one of a cd-rom drive and the other a monitor) and chose the cd-rom option. It loaded some more and the next screen came up the same way, all text was only showing as squares.

---

### Post by Mark Phelps on 2014-06-10
> I have read about a method of installing ubuntu directly from windows, so I may try it that way and see if that has more success.

This is know as Wubi -- and has been discontinued. Even if it does work, which it probably will not, there is no longer any support for it.

---

### Post by DuckHook on 2014-06-10
> **Emile_Beaulieu said:**
> ...I also took a guess from that first screen, with a list menu on the left, and two pictures (one of a cd-rom drive and the other a monitor) and chose the cd-rom option. It loaded some more and the next screen came up the same way, all text was only showing as squares.If memory serves me, that next screen is asking you for keyboard layout and language. The defaults are US default and English. Please just hit the enter key to accept defaults in order to finish loading the full graphical OS. I'm suggesting that you try to get to a full desktop to test if the fonts are still wonky. A LiveUSB session can be powered down (I believe) by brute force without damage to the HDD or any of your critical data, so pull the plug if needed.

I have an HD 7950, which occasionally gives me the odd smeared font on the Radeon (open source) driver that I use under 13.10. Not a problem, really, as scrolling a single line will rectify the smears. My old 12.04 install never had font issues (though it had other issues), so I'm a bit stuck on this one. Since the HD 6800 series is not that old, one would think that the driver ought to handle it properly. Are you trying to install 14.04? Also, which flavour?

If you are game, try running a LiveUSB of a different distro. Try both Ubuntu-derived &#8213; I would suggest Mint (because it might default to the proprietary driver) &#8213; and a non-Debian-based &#8213; say, Chakra or Manjaro.

---

### Post by Emile_Beaulieu on 2014-06-11
I spent a bit of time reading and decided to make a bootable DVD for ubuntu 14.04 LTS. This was apparently not the version I installed on my netbook.

I'm typing this message from my newly installed ubuntu OS, so as you can see, all is well!

I still don't know why the USB version didn't work, but I'll experiment with it later.

Thanks so much for all the support guys! I'm sure I'll be back soon with more questions lol

---

### Post by mörgæs on 2014-06-11
Good, please mark the thread 'solved'.

---

