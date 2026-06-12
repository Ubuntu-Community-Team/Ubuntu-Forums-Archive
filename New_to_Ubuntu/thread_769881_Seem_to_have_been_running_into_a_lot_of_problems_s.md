---
title: "Seem to have been running into a lot of problems since 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-04-26
Well since I have had 8.04 I have been running into a lot of problems it seems. Some problems are

-Losing sound, forced to restart to gain sound back.
-When I click the power button in top right it doesn't always pop up forcing me to hold power button on pc. 
-Occasionally FireFox doesn't open so I go into the processes and end all of the firefox processes and then try launching firefox and it doesn't come up still. This causes me to restart.
-While using pidgin when someone AIMs me and makes the sound it gets stuck on that sound and keeps looping and only ends when I restart computer.

This is just a **few** of the problems I have been running into. I was curious if anyone else has? Also how easy is it to go back to 7.10 without doing a fresh install?

---

### Post by ImThatNerd on 2008-04-27
Anyone?

---

### Post by BONEDOC on 2008-04-27
Hi. Yes, I have had a whole pile of problems with 8.04, including my USB hub seems to make it crash on start up, the synaptic manger doesn't work, the update manager freezes, hardware drivers and hardware manager don't work. I REALLY regret upgrading from 7.1 to 8.04. Can anyone tell me how to get rid of this infernal 8.04 and re-install 7.1 which I have on CD? 7.1 was great, no problems at all.

---

### Post by mlentink on 2008-04-27
You guys, for being nerds and all, could use some help in getting helped.
If you reall want help in these forums, you could help those wanting to help you by providing just a bit of info.
What cpu's are you running with? What graphics cards? What network interfaces?

In other words, there are quite a few people up here wanting to help. including me, for all that's worth (which admittedly isn't much), but we need something to go on.

To give you an example : Hardy Heron is running perfectly fine, thank you very much,  on a HP/Compaq NX7400 notebook with a Core 2 Duo processor, Intel 945 graphics, etc etc... 

So...
Help us help you...

---

### Post by ImThatNerd on 2008-04-27
Well I have a 8yr old dell desktop, Intel Pentium 4 processor, no clue what graphics card since I know it is just the stock one from dell.

But I thought there was a way just to uninstall 8.04, is that true? Or do I need to do a fresh install for 7.10

---

### Post by WindowsH on 2008-04-27
Damn

That's my first post...

I've got problems on 8.04 version.
I can't run many apps including the following:
- Firefox
- MPlayer
- Thunderbird
And many others.

It says "Floating point exception".
Everything was perfect until I've enabled my NVidia driver through Hardware Manager. I had to do it in order to get 3D graphics enabled.

My computer:
- AMD Athlon 3200+
- MB Asus K8U-X
- NVidia 5200 128 MB video card
- 1 Gb DDR RAM
- 2 HDD (40 gb + 250 gb)
- Kubuntu Hardy 8.04 / KDE 4 - Alternate CD

I got KDE 4 installed.

I've heard it (the problems) could be due to some fonts installed but I don't think so. I tried not enabling my nvidia but the problem remains.
I've never had this problem before when using Kubuntu Gutsy.

I hope you can help me.
Thank you very much.

(I'm using Konqueror now)

---

### Post by ayanph on 2008-04-28
I'm having issues with the bootup sound looping over and over.

This happens in 7.10 and 8.04

7.04 doesn't have this problem.

My computer specs:

MSI (Micro-Star Incorporated) Megabook VR320-K2 Laptop.
* Intel Core 2 Duo Mobile Technology
* Intel Core2 Duo T5200
* (1.60GHz 533MHz 2MB L2 Cache)
* ATI 410ME Chipset
* ATI Mobility Radeon X200 Graphics 256MB Shared
* 1GB DDR2 Memory
* 80GB Hard Disk Drive
* Super Multi DVD+/-RW/Ram Dual Layer Drive
* Super Glare 13.3" Widescreen Display
* 4-in-1 Card Reader
* Firewire port
* 10/100LAN
* 56K Modem
* 6-cell Battery
* 2.1kg


lspci shows:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
04:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
04:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
04:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
04:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
04:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
04:09.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

---

### Post by martrn on 2008-04-28
> **ImThatNerd said:**
> Well since I have had 8.04 I have been running into a lot of problems it seems. Some problems are

-Losing sound, forced to restart to gain sound back.
-When I click the power button in top right it doesn't always pop up forcing me to hold power button on pc. 
-Occasionally FireFox doesn't open so I go into the processes and end all of the firefox processes and then try launching firefox and it doesn't come up still. This causes me to restart.
-While using pidgin when someone AIMs me and makes the sound it gets stuck on that sound and keeps looping and only ends when I restart computer.

This is just a **few** of the problems I have been running into. I was curious if anyone else has? Also how easy is it to go back to 7.10 without doing a fresh install?

```

sudo apt-get install linux-rt

```
+ reboot using that kernel.

TO ADD
File a bug report here :- [https://launchpad.net/ubuntu/+bugs]("https://launchpad.net/ubuntu/+bugs")

---

### Post by Schizmo on 2008-04-28
I am having similar issues as well. This is my first time running Linux on a computer, I did it more as a test than anything. I opted to use Wubi to install a 5gb partition on my main hard drive so that I could try it out, and honestly I really like it. I am, however, running into some of the same issues. 

(Edit: What I mean to say is that I literally installed it Saturday night for the first time ever, and am somewhat of a linux noob.)

-Firefox refusing to open, multiple processes running in the system manager
-Evolution refusing to open, same symptoms.
-Streaming video (flash videos, youtube streams, internet radio) does not appear to work properly. (hangs and lags the computer more than normal, audio does not always play, and when it does its garbled)
-Panels freeze, inhibiting shutdown or access to any programs (like right now, I tried to open the clock and the panels are no longer responding...)

I would check my system but with my panels frozen its rather difficult. I do not know how else to access that information. Lucky for me I wrote it down last week. (this computer is a substitute, my main is having some issues)

Its a Dell Optiplex GX210. Some free thing that work was going to just throw away, so we opted to take it and put it to better use. You know, those streamlined quiet rigs that basically do spreadsheets. Probably not the best thing to do this with.

3.0ghz processor Intel Pentium 4 
510mb Ram (pathetic! I HATE SUBSTITUTE MACHINES)
As for the video card, its whatever comes standard on this thing. I have no idea.

---

### Post by martrn on 2008-04-28
> **Schizmo said:**
> ..8.04......... (hangs and *lags the computer more than normal*, audio does not always play, and when it does its garbled)
-*Panels freeze*, inhibiting shutdown or access to any programs (like right now, I tried to open the clock and the panels are no longer responding...)


try :-

```

sudo apt-get install linux-rt

```

+ reboot using that kernel.

File a bug report here :- [https://launchpad.net/ubuntu/+bugs]("https://launchpad.net/ubuntu/+bugs")

---

### Post by Difranco1911 on 2008-04-28
You certainly are not the only one having issues, I was running Gutsy since last August without issues.

The problems I am having are:

- Choppy video playback
- Gnome occasionally crashes and restarts during video playback occasionally
- Slow Network Browsing / sometimes cant access SMB shares on my Gutsy 

Theres more but these will do for a start.

---

