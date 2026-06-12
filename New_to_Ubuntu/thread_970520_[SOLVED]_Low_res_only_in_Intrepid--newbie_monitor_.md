---
title: "[SOLVED] Low res only in Intrepid--newbie monitor and NVidia issues"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by jweaver28 on 2008-11-04
Hi. I'm a newbie starting this thread after trying various solutions for 2 days and only losing hair and/or patience. Many threads marked as "solved" in Hardy or earlier just don't seem to work in Intrepid or because of what now seem to be dual problems. I have an Olevia 337 monitor and EVGA MOBO with onboard GeForce 7150. 

Apparently, there are no linux drivers for the monitor, though it works fine in Vista with an HDMI connection. Intrepid uses the default 800x600, 640x480 settings, though the manual lists possible resolutions of "1360x768" "1280x768" "1024x768" "800x600" "640x480". The manual does not specify refresh rates in horizontal and vertical, though it does give a 56-75 range.

I have installed, activated, uninstalled and reinstalled the NVidia 177 restricted drivers, and even tried the 173 drivers mentioned in what as a dissatisfied Vista user I'll call the Ubuntu NVidia FAQ thread. Rebooting gives me various error messages, all of which list low-res as my only solution. The really frustrating one refers me to "common problem" documentation, but without saying where that is. Several threads keep mentioning Envy, which doesn't work in Intrepid (and also doesn't have the latest NVidia drivers). According to the Ubuntu FAQ, the 7150 is a supported NVidia video chip. It's just that following those directions to the letter doesn't work.

I don't understand much about EDID and binary drivers, nor have I figured out how to start Nautilus. FYI, downloading a custom EDID doesn't work because I can't figure out how to open it. Nonetheless, emboldened by having gotten the latest NVidia/Realtek audio drivers to work and after reading some threads about it needing some tweaking for the 7150, I once tried to edit my xorg.conf file. My attempt to translate language from another NVidia chip to the 7150 generated an incorrect parsing error message upon reboot. After the latest reboot (post-more "solutions") the 177 drivers are listed as activated under System/Hardware drivers, but clicking on System/X server settings says they aren't. The latest bootup error message said the X system wasn't able to start. It tells me to run the nvidia x-config as root, which I now know means start a command in terminal as "sudo" but apparently I've messed up newbie-style with spaces or capitalization or something, because I get "command not found".

I hope I don't sound too frustrated or imperious, but someday I'd like to be able to use this monitor and my hauppage1600 card, which is supposed to work in Linux. First things first, though, since with the low-res I can't even see the bottoms of some of the ubuntu's non-scrollable default boxes!

---

### Post by brandoncolorado on 2008-11-05
Does this bug apply to you?
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/261977](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/261977)

---

### Post by Peter09 on 2008-11-05
Initially reboot into recovery mode (hit esc at the grub prompt and select the second line down).
On the recovery menu that will come up select xfix, see if that works as a first pass.

---

### Post by jweaver28 on 2008-11-07
Thanks, Brandon and Peter, but neither fix worked. it's a different bug (or me). Recovery mode and XFIX said no upgrade was necessary, and then the same old "Failed to initialize the NVidia graphics driver" and "Screens found, but none have a usable configration."

Sorry for the delay, but I carried this drive to Philly to try on the Hardy machine with GeForce 5200 card (AGP) and an old (very heavy) dell 19 inch monitor. Swapping sata cables so this was the only drive led to the same low-res problem, and my internet connection (muni wifi) was spotty (storms didn't help). 

When I carried the hard drive back home to the Vista machine with the Olevia LCD monitor, I noticed Update Manager downloaded some new NVidia stuff. But it didn't solve the problem (and then ubuntuforums was down upgrading its hardware!)

I don't know whether any of the following info helps: Looking under Sysinfo, the kernel now recognizes my MOBO and graphics card, with NVidia MCP73 Host Bridge (Rev a2) and PCI Bridge (rev a1), with NVidia Corp Device cb73).  I've tried loading and unloading the Nvidia 177 drivers from ubuntu/synaptic. However, they seem to be the 10/1 version, and not the end-of-month one. I've tried editing the xorg.conf file in various ways (screen, monitor, device and the glx module is loaded), but get various parsing error messages which I don't understand. The monitor's native resolution is 1360x768 and while according to the model-related threads, Olevia monitors don't always play well with ATI graphics, they do play well with NVidia graphics (these HDTV and HDTV-ready monitors distributed by Syntax are a Black Friday staple, even if this exact model is no longer produced). 

I can't get the NVidia display X-server working, either through the terminal nor the GUI Admin/Nvidia route. I get an error message about "just run nvidia-xconfig as root and restart the X server" (and sudo nvidia-xconfig doesn't help).

I'd appreciate any help/insight you can give!

---

### Post by mapes12 on 2008-11-07
Not sure if it will work for you but probably worth a go: [http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

---

### Post by jweaver28 on 2008-11-07
Thanks, Mapes. It was worth a try. Same error messages, but different log file. Bummer.

---

### Post by mapes12 on 2008-11-07
> EVGA MOBO with onboard GeForce 7150.

Mine is also onboard my motherboard being an ATI Rage XL device that is not supported by Linux.

My solution - I visited [http://www.x.org/wiki/Projects/Drive...t=VideoDrivers](http://www.x.org/wiki/Projects/Drive...t=VideoDrivers) and found a supported chipset. Went onto eBay and bought one for the princely sum of £4.50 inc P&P. It's a S3 Savage PCI card that should take priority over the onboard device at start up. I say should as I have done this before on another base unit and it worked fine. That's what generally happens i.e. the onboard device is configured to be submissive. Just waiting for it to arrive in the mail to try it out and get away from this horrible 800x600 resolution.

Good luck in your quest.

BTW - I've been with Ubuntu now for about 12 months and have it as the only OS on my main Desktop and Laptop. It's well worth staying with it :)

---

### Post by m_l17 on 2008-11-10
Try this:

[http://http://ubuntuforums.org/showthread.php?t=975058]("http://http://ubuntuforums.org/showthread.php?t=975058")

or 


[http://ubuntuforums.org/showpost.php?p=6071334&postcount=12]("http://ubuntuforums.org/showpost.php?p=6071334&postcount=12")

---

### Post by jweaver28 on 2008-11-13
Still looking for a solution, M_117. BTW, the parsing error appeared due to my cutting and pasting in the xorg.conf file, which inserted the wrong kind of quotation marks. But still my device won't initialize. 

I like your new photo, Mapes, but don't want to go the new card route just yet. This video setup works well in Vista, the boot alternative on this machine. Plus, a better card with comparable hdmi input would cost over $100, and might well not work because of the same nvidia driver issue. I filed a bug report, for what it's worth, and notice lots of other complaints about Nvidia drivers.

---

### Post by philinux on 2008-11-13
How about reinstalling Hardy for now.

---

### Post by jweaver28 on 2008-11-13
:confused::confused:

---

### Post by jweaver28 on 2008-11-13
:confused:

Thanks for the reply Phil, but the Hardy machine's in Philly (really!).  Envy and Hardware Drivers both say the Nvidia 177 driver is installed and active, but X-settings says the opposite. 

The revised xorg file that does NOT work is as follows: 

Section "Monitor"
Identifier    "Configured Monitor"
HorizSync 30-80
VertRefresh 60
EndSection

Section "Device"
Identifier    "Configured Video Device"
Driver    "nvidia"
Option    "NoLogo"    "True"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device        "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1360x768" "1280x768" "1024x768" "800x600" "640x480"
EndSubSection
EndSection


Section "Module"
Load    "glx"
EndSection 

I'm at my wit's end. Is the problem that I have the monitor connected by HDMI cable? Or that Olevia/Syntax does not publish its precise monitor capabilities? Otherwise, I love Ubuntu's speed!

---

### Post by mapes12 on 2008-11-13
> How about reinstalling Hardy for now.

Yep. That's what I did and back up and running with my preferred screen res.

> I like your new photo, Mapes

That's me having a beer on a sailing boat a few weeks ago around Greece..............really good fun.:guitar:

---

### Post by jweaver28 on 2008-12-02
The system seems to have resolved itself--almost.

I ended up reinstalling Ubuntu 8.10 as a partition on a new WD hard drive (Vista first this time since it was trying to cannibalize Ubuntu on the separate drive, or maybe the decompilation issue had something to do with Seagate's nonsupport of Linux). Anyway, after restart, the Nvidia 177.80 drivers loaded flawlessly, Another restart and X-Server noted the 7150 video chip, as well as recognized the Olevia monitor as Syn(tac) 337-B11 with a 1368x768 native resolution.:P

Of course, no install is perfect. I'm now downloading the newest Realtek audio drivers since I have no sound. And my initial downloads of Opera and Skype didn't work because somebody thinks this system is an AMD64 rather than an Intel dual core.....):P

---

### Post by jweaver28 on 2008-12-05
I'm going to mark this as closed, if I can figure out how and though I'm dissatisfied with the solution. I installed my cyberMonday splurge, a videocard by the same manufacturer. I have to connect my Tv/monitor by a vga cable and dvi adapter, but both video and audio work in both Ubuntu and Vista.

---

### Post by gbswales on 2008-12-05
I am trying ubuntu once more - everytime there seems to be something that doesn't work "out of the box"

I installed the nvidia driver reccomended by the tool in ubuntu and rebooted but I cant find a way to get it to use my second monitor. In windows I just installed the driver and selected dual monitor display - ubuntu doesnt seem to even recognise what my working monitor is and I cant see any controls at all for setting dual display

Looks like I shall be uninstalling again because it looks as if ubuntu still haven't got around to plug and play

Is there a simple programme I can run for the 7300 so I get all the functions? (not that I have found how to run programmes yet!)

---

