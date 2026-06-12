---
title: "No wireless"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by uunbeliever on 2008-04-24
Upgraded to 8.04 and. . . no wireless! My old linksys wpc11 ver4 works fine with 7.10 but 8.04 says no network device detected. WTF! I re installed 7.10 to use internet to try to solve the problem. Any suggestions?

---

### Post by spiderbatdad on 2008-04-24
file a bug with launchpad. Stick with what works. Gutsy is not unsupported yet.

---

### Post by stchman on 2008-04-24
> **uunbeliever said:**
> Upgraded to 8.04 and. . . no wireless! My old linksys wpc11 ver4 works fine with 7.10 but 8.04 says no network device detected. WTF! I re installed 7.10 to use internet to try to solve the problem. Any suggestions?

Try installing Hardy from scratch, not the upgrade route.

---

### Post by WitchCraft on 2008-04-24
> **stchman said:**
> Try installing Hardy from scratch, not the upgrade route.

No, no no!

This usually happens when you update to a new kernel, and Hardy has a new Kernel. 

That means that the firmware image & driver module of your WLAN-Card don't work with this new kernel. You need to download the latest drivers & firmware image, then compile it, and restart the computer to be sure, then it SHOULD work again...

You now need to look up your WLAN-Card manufacturer and model, and then search with google for drivers for this WLAN card.
At least this always did the job for me when I had the very same problem. Or if you still have the old kernel, you can boot with the old kernel, then it will work again with the old drivers.

---

### Post by uunbeliever on 2008-04-24
> **WitchCraft said:**
> No, no no!

This usually happens when you update to a new kernel, and Hardy has a new Kernel. 

That means that the firmware image & driver module of your WLAN-Card don't work with this new kernel. You need to download the latest drivers & firmware image, then compile it, and restart the computer to be sure, then it SHOULD work again...

You now need to look up your WLAN-Card manufacturer and model, and then search with google for drivers for this WLAN card.
At least this always did the job for me when I had the very same problem. Or if you still have the old kernel, you can boot with the old kernel, then it will work again with the old drivers.
I am new to linux (ubuntu) and have no idea how to compile, etc. It seems like a lot of effort for something that works with the old ubuntu.

---

### Post by grybi on 2008-04-24
wifi Problem :) no wifi on ubuntu 8.10


[   17.983170] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   17.983173] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   17.983349] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.206908] iwl3945: Radio Frequency Kill Switch is On:
[   19.207834] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   19.217890] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   19.237873] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   19.265241] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   19.285274] cs: IO port probe 0xa00-0xaff:<6>iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels

---

### Post by ekravche on 2008-04-24
Try to use an older kernel. 2.4.22 works for me, while the kernel that comes with hardy 2.4.24 seems to break wireless for me.

---

### Post by sharris203 on 2008-04-25
> **uunbeliever said:**
> Upgraded to 8.04 and. . . no wireless! My old linksys wpc11 ver4 works fine with 7.10 but 8.04 says no network device detected. WTF! I re installed 7.10 to use internet to try to solve the problem. Any suggestions?

I have the opposite problem. I upgraded, now the wireless ONLY work with the hardy kernel, not with the gutsy kernel. Nothing shows up in the restricted drivers program. Seems completely undetected. But I don't use it much, so I stick with the old kernel. My tv tuner and vm ware installation don't work with the new kernel anyway.

---

### Post by uunbeliever on 2008-04-25
> **ekravche said:**
> Try to use an older kernel. 2.4.22 works for me, while the kernel that comes with hardy 2.4.24 seems to break wireless for me.
For fun, lets pretend I have no idea how to change the kernel.

---

### Post by nina_aoki on 2008-04-25
Before you do that - have you checked your restricted drivers?

---

### Post by Donskov on 2008-04-25
Not sure wether you are using Ndiswraper or Madwifi(HAL) but if you did an up grade I suggest the following

open a terminal and type the following.

lspci

Post your output here.

Don't worry about compiling things everyone on here is more then glad to walk you through the whole thing.

---

### Post by uunbeliever on 2008-04-25
> **Donskov said:**
> Not sure wether you are using Ndiswraper or Madwifi(HAL) but if you did an up grade I suggest the following

open a terminal and type the following.

lspci

Post your output here.

Don't worry about compiling things everyone on here is more then glad to walk you through the whole thing.
The hardline also does not work. So I am reluctant to reinstall 8.04. Is there any significant advantage to 8.04? I am running it on an older 750mhz thinkpad with 300 something ram.

---

### Post by Donskov on 2008-04-25
Well since your not running it on newer hardware there isn't any real distinct advantage for you. There are how ever newer versions of some packages, fixes ect..

You could also try 
ALT+CTRL+F1
login and run the above.

OR:

You might want to also try some of the more light-weight Linux distros like [_**DSL**_]("http://www.damnsmalllinux.org/")

You could just go back to the last version since it is supported till 2009

---

### Post by uunbeliever on 2008-04-25
> **Donskov said:**
> Well since your not running it on newer hardware there isn't any real distinct advantage for you. There are how ever newer versions of some packages, fixes ect..

You could also try 
ALT+CTRL+F1
login and run the above.

OR:

You might want to also try some of the more light-weight Linux distros like [_**DSL**_]("http://www.damnsmalllinux.org/")

You could just go back to the last version since it is supported till 2009
I have been using ubuntu for about 2 weeks now. At first it was great but then. . .No hard line LAN, then updated to 8.04 and no wireless or hard line, back to 7.10 and now DVDs will not play . Not to mention that open office is not compatible with office 2007 (which Even though is Microsoft is pretty slick), ubuntu cant use my Crative Zen player either. Hmm. . .what is the advantage? A few dollars? I have wasted alot of time with stupid little fixes that do not exist in Xp. I really want to like Linux but so far it kinda sucks.

---

### Post by Kess on 2008-04-25
> **uunbeliever said:**
> I have been using ubuntu for about 2 weeks now. At first it was great but then. . .No hard line LAN, then updated to 8.04 and no wireless or hard line, back to 7.10 and now DVDs will not play . Not to mention that open office is not compatible with office 2007 (which Even though is Microsoft is pretty slick), ubuntu cant use my Crative Zen player either. Hmm. . .what is the advantage? A few dollars? I have wasted alot of time with stupid little fixes that do not exist in Xp. I really want to like Linux but so far it kinda sucks.

If you want to use your Zen, download Amarok from the repositories.

---

### Post by Mazza558 on 2008-04-25
> **uunbeliever said:**
> I have been using ubuntu for about 2 weeks now. At first it was great but then. . .No hard line LAN, then updated to 8.04 and no wireless or hard line, back to 7.10 and now DVDs will not play . Not to mention that open office is not compatible with office 2007 (which Even though is Microsoft is pretty slick), ubuntu cant use my Crative Zen player either. Hmm. . .what is the advantage? A few dollars? I have wasted alot of time with stupid little fixes that do not exist in Xp. I really want to like Linux but so far it kinda sucks.

No problem. Use what works best for you and come back in 6 months for the release of 8.10 - maybe these things will be fixed.

---

### Post by uunbeliever on 2008-04-25
> **Kess said:**
> If you want to use your Zen, download Amarok from the repositories.
For some reason amarok recognises all but the 8gig zen.

---

### Post by EarloftheWest on 2008-04-25
grybi,

This may help you.
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61)
Essentially, it says that Hardy uses the new Intel driver where 7.10 used the old one. 
I wiped my drive and did a fresh install and everything seems to work just fine for me out of the box. Just a few specific hardware tweaks that I'll need to make at some point. (I'm not sure I'm a fan of the upgrade route at this point, but I don't mind doing fresh installs of OSes. I do know that others have better luck at the upgrades than I. It's just as easy for me to do a fresh install as an upgrade.)

---

### Post by EarloftheWest on 2008-04-25
uunbeliever,

You can install Office 2007 in Ubuntu:
[http://wine-review.blogspot.com/2008/03/microsoft-office-2007-update.html](http://wine-review.blogspot.com/2008/03/microsoft-office-2007-update.html)

I haven't done it myself. Let me know if you get it working.

---

### Post by uunbeliever on 2008-04-26
> **uunbeliever said:**
> The hardline also does not work. So I am reluctant to reinstall 8.04. Is there any significant advantage to 8.04? I am running it on an older 750mhz thinkpad with 300 something ram.
ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03) 
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) 
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03) 
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03) 
00:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 09) 
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01) 
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02) 
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) 
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) 
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03) 
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

---

### Post by almayer on 2008-04-28
Hi all,

I'm completely new to Ubuntu, I installed it (8.04) on an old IBM T21 laptop, and was going to use it with a Linksys WPC11 (ver. 3) PCMCIA card: it didn't work, the card was not recognized. I decided to wipe out the HD and install Xubuntu instead (also 8.04), to get some more speed (only have 256 megs of ram), and same issue. Now, the card seems to be connected, as per leds status, but I don't see an IP address assigned to it in ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:06:25:a9:3b:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0x100 

with lpsci I get:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)
00:03.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 20)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)

On my router I don't see the laptop connecting, I have a wireless network with WEP, and have included the corrected HEX key under the manual config of the network card, which I can see under Applications/System/Network (Wireless connection enabled, and it's red colored). I've downloaded a linux driver from the Linksys website but have no clue on how to install it. Any clue?

---

### Post by uunbeliever on 2008-04-30
> **almayer said:**
> Hi all,

I'm completely new to Ubuntu, I installed it (8.04) on an old IBM T21 laptop, and was going to use it with a Linksys WPC11 (ver. 3) PCMCIA card: it didn't work, the card was not recognized. I decided to wipe out the HD and install Xubuntu instead (also 8.04), to get some more speed (only have 256 megs of ram), and same issue. Now, the card seems to be connected, as per leds status, but I don't see an IP address assigned to it in ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:06:25:a9:3b:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 Base address:0x100 

with lpsci I get:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)
00:03.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 20)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)

On my router I don't see the laptop connecting, I have a wireless network with WEP, and have included the corrected HEX key under the manual config of the network card, which I can see under Applications/System/Network (Wireless connection enabled, and it's red colored). I've downloaded a linux driver from the Linksys website but have no clue on how to install it. Any clue?
Everything works fine with 7.1. Except the hard LAN line.

---

### Post by master5o1 on 2008-04-30
When you rebot, press escape when the Grub counter comes and boot into the kernel just before 8.04 came along (2.6.24-16 = 8.04)

---

