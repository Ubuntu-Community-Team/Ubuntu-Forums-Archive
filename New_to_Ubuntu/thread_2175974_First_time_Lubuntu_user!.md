---
title: "First time Lubuntu user!"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by Yuvanesh on 2013-09-22
Hey all,

This is my first installation of lubuntu, decided to build my own pc(first time too). After some time researching decided to go with lubuntu. Hoping you guys will be kind enough to help me :).

[U]system specs

[/U]amd a6-5400k cpu
gigabyte f2a75m-d3h
4gb ram
120gb ssd(primary)
3TB HDD(storage & media)1) After doing a clean install, the first problem i had was the graphics. Open source drivers caused tearing and lag, so i switched to proprietary drivers. There is still some minor lag when i drag a window around the screen. Is there any solution, or is this normal?

2) When i click on "sytem profiler & benchmark" 2 grey windows open and i have to close the smaller window 3 times before i can see system profile. Also the benchmark doesn't work? Picture attached.

3) I installed lm-sensors, but my temperature is shown incorrectly. I tried uninstalling/reinstalling but still the same. 

> it8728-isa-0228Adapter: ISA adapter
in0:          +1.44 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.02 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +1.99 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +2.05 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.22 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.22 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.34 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.07 V  
fan1:        1161 RPM  (min =    0 RPM)
fan2:         362 RPM  (min =   10 RPM)
fan3:        1138 RPM  (min =   10 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +23.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:         -8.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +19.0°C  (low  =  +0.0°C, high = +70.0°C)  sensor = Intel PECI
intrusion0:  ALARM


k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +5.1°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)

4) how do i uninstall the default games , sudo apt-get remove "game name" ?

Any additional advice or recommendations would be much appreciated. I am really excited to be using linux, and i hope that in time i can minimize my usage of windows :D. Thank you for your time in advance.

regards
nesh

---

### Post by nerdtron on 2013-09-22
Why Lubuntu on that powerful machine? Xubuntu or KDE or any desktop environment would run fast on that machine.

4. Does Lubuntu have synaptic or Ubuntu Software center installed? If so, you just search the game in question and you'll see if it is installed or not. You can click uninstall if you no longer want it.

---

### Post by Yuvanesh on 2013-09-22
Great question, my initial plan was to install ubuntu as my main os, lubuntu and other linux os to try and learn more about the the linux world. I first tried ubuntu, but regardless of which drivers i used, open source of fglrx i had very bad screen tearing and lag. Secondly i wanted something lighter because i plan to run this pc 24/7 as pseudo Nas and for XBMC, and other server based applications. Anyway i quite prefer lubuntu , i find the unity desktop environment overwhelming. Too many features that i do not need for this pc.

---

### Post by vasa1 on 2013-09-22
> **Yuvanesh said:**
> ...
4) how do i uninstall the default games , sudo apt-get remove "game name" ?
...
**sudo apt-get purge ace-of-penguins** worked for me. You may see a warning that "lubuntu-desktop" will be removed as well. According to [http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html), that shouldn't be a problem: lubuntu-desktop is a metapackage and not your actual desktop.

Sorry, can't help about the others!

---

### Post by Yuvanesh on 2013-09-22
Thanks vasa1, i did that and it worked great for me :)

---

### Post by DuckHook on 2013-09-22
Hi Yuvanesh and welcome to Lubuntu and the forums!

Good to see another explorer discovering this great OS.

Although you have graciously posted some of your system info (good instincts!), please also post the graphics info for those of us unfamiliar with your motherboard. An easy way to do this is to post results of:```
lspci -vk | grep -iA10 vga
```To answer your questions in the order asked:

1. This depends on your video subsystem, your amount of VRAM, your colour depth/resolution, the effects (esp 3D) that you have turned on and facts about your driver (like the version). Example: even a new video chip with decent VRAM will not perform optimally with a driver that is too old or not optimized for that chip. Also, lots of active desktop/windows effects will slow everything down (which is what most people complain about with Unity), but since you are running Lubuntu--I assume using its default config--this is unlikely to be the problem. Impossible to tell in your case without more info.

2. I've never used this app so can't help much here. Will look into it further. It looks interesting. But please don't hold your breath as it will be a case of the blind leading the blind.

3. lm-sensors will sometimes return loopy readings for some sensors, though I've never seen readings quite as wonky as yours. Coretemp readings seem to be missing, but that may only be available on Intel CPUs. I don't know anything about AMD. Perhaps an AMD user could help here. At any rate, it appears that you only have motherboard info being reported, with temp1 to temp3 as likely various regions of the MB, and some of these clearly out to lunch (i.e. -8°C, and even 19°C). I wouldn't worry about this, as I have had a CPUTIN reading of 117°C for months, which initially panicked me, until it became clear that it was flaky data (any temp really that high would have burned out the MB in weeks if not days). A bigger mystery is your second group of readings which I am wildly guessing to be your video adapter. Again, a 5.1°C temp is just flaky data, since no component could be running that low unless you are cooling your system with liquid nitrogen.

While my own knowledge of lm-sensors is severely limited, here is what I do know: lm-sensors searches for chips that report raw sensor data about the system. In raw form, this data is often quirky and must be processed by lm-sensors before it generates sensible numbers. Some raw data may be multiples of their real value. Other data may need to be offset by a certain integer value to return a proper result. lm-sensors is aware of the foibles in most sensor chips and will process the raw data properly using its default configuration, which can be found in */etc/sensors.conf* or */etc/sensors3.conf*. However some CPU/MB combos require a custom config file which can be placed in the */etc/sensors.d* directory. Some of these custom config files have been pregenerated by other users and kindly contributed to the community at [this]("http://www.lm-sensors.org/wiki/Configurations") site. Unfortunately, I could not find any config file for my MB, and a quick look shows that your MB is not represented either. I suppose that a hardware guru could decipher what values are being returned for your MB and generate a custom config file, but that task is far beyond my abilities.

I don't know of any alternate sensor apps, but others may.

4. Others have given good answers as to how to purge unwanted apps, so no further comments from me.

---

### Post by Yuvanesh on 2013-09-22
Thanks for the in-depth explanation duckhook! Below is the graphics info

> 00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7540D] (prog-if 00 [VGA controller])	Subsystem: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7540D]
	Flags: bus master, fast devsel, latency 0, IRQ 51
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=256]
	Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci


00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Trinity HDMI Audio Controller
--
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	Memory behind bridge: fea00000-feafffff


00:14.5 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
	Subsystem: Gigabyte Technology Co., Ltd Device 5004
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at feb4c000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd


00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0




I read a post on another part of the forum, just as you said, some changes have to be made to lm-sensors to get it working on certain systems. Unfortunately still new to this! Not too urgent though, since this was a new build i wanted to monitor temperatures as i use applications. Thanks again , for some reason people using linux seem to be more cheerful then *cough cough* folks.

---

### Post by Bucky Ball on 2013-09-22
I don't see that you've mentioned which release you are using, unless I've missed it. Which one? 12.04, 13.04? Not 13.10 by any chance?

---

### Post by Yuvanesh on 2013-09-22
Sorry, lubuntu 13.04
*I see that you live in AU :)

---

### Post by DuckHook on 2013-09-22
You don't actually have a dedicated graphics card. The 7540D is a graphics subsystem integrated into your CPU without dedicated VRAM. This makes it a rather underpowered graphics performer and is likely the cause of your lagging when you drag windows around on your desktop. Downloading, compiling and installing the latest graphics driver from AMD might squeeze out a smidgeon more performance, but unless you know how to recover, the process is fraught with pitfalls and can hose your display. It's probably not worth the risk for the relatively limited reward. I suspect that the graphics performance you currently have is about the maximum performance you are likely to get.

If you like, a relatively trouble free way to try optimizing settings is through AMD's Catalyst control centre. It should already be installed on your system when you installed the proprietary driver. If not, then:```
sudo apt-get install fglrx-amdcccle
```You must open the *administrator* version of Catalyst on your menu. Or you can:```
gksudo amdcccle
```It is very important to use *gksudo* and not just *sudo* for all graphics programs. Navigate to "3D>More Settings" and set the performance bar closer to "performance" rather than "quality". You will have to experiment to see what setting gives you the best compromise between acceptable performance vs quality. Next, navigate to "Display Options>Tear Free" and enable Tear Free Desktop to see if this helps your lag/tearing issues. If no noticeable difference, then it is best to disable it. I'm afraid that your graphics system is too underpowered for GPU-intensive tasks like 3D gaming, but it should handle videos and 2D stuff tolerably well. NAS should be fine as will be most server functions. XBMC will depend on whether you are running as client or server. You may wish to invest in a dedicated graphics card if you find your current setup too limiting.

To get snapshot of current GPU clock rate, load and temperature, try:```
aticonfig --odgc --odgt
```or for ongoing updates, do:```
watch aticonfig --odgc --odgt
```These commands may not return any results for an integrated chip, so don't be surprised if they don't work for you. If they do, then at least you have a temp reading without lm-sensors.> ...people using linux seem to be more cheerful...This is the case on this forum for sure, but then, it's a help forum and tends to attract a certain type of responder. Glad you are enjoying your ride so far.

---

### Post by santosh83 on 2013-09-22
> **DuckHook said:**
> You don't actually have a dedicated graphics card. The 7540D is a graphics subsystem integrated into your CPU without dedicated VRAM. This makes it a rather underpowered graphics performer and is likely the cause of your lagging when you drag windows around on your desktop. Downloading, compiling and installing the latest graphics driver from AMD might squeeze out a smidgeon more performance, but unless you know how to recover, the process is fraught with pitfalls and can hose your display. It's probably not worth the risk for the relatively limited reward. I suspect that the graphics performance you currently have is about the maximum performance you are likely to get.

Just an anecdotal counterpoint though. I just installed the latest AMD drivers for the desktop HD 6xxx series PCIe cards on 10.10 and both installation and use were trouble free! A bit amazing a driver compiled just a few months ago still works with a kernel and system dating back three years!

> 
To get snapshot of current GPU clock rate, load and temperature, try:```
aticonfig --odgc --odgt
```or for ongoing updates, do:```
watch aticonfig --odgc --odgt
```These commands may not return any results for an integrated chip, so don't be surprised if they don't work for you. If they do, then at least you have a temp reading without lm-sensors.

Here I have the fglrx from the repos installed on 13.10, and the above command gives:
```
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again. 
```

However the Catalyst Control Center does correctly display my graphics card and says the driver is installed. Should I take the risk of invoking 'aticonfig --install'?

---

### Post by vasa1 on 2013-09-22
> **Yuvanesh said:**
> ... i wanted to monitor temperatures as i use applications. ....
Why don't you explore the options that come with Lubuntu? I use a temp monitor and a CPU usage monitor to keep tabs on applications. You can find these monitors if you have lxpanel installed (which it should be in a default Lubuntu). 

Here is an oldish but largely valid read about it: [http://pclosmag.com/html/Issues/201010/page07.html](http://pclosmag.com/html/Issues/201010/page07.html)

One image is of the tab that allows you to add monitors and the other is an image of what mine look like: 53 is some temperature (I'm assuming it's that of the cpu) and the CPU % is currently 1.52%. I see a good correlation between temperature and CPU usage and so I feel the temperature is relevant.

---

### Post by santosh83 on 2013-09-22
> **vasa1 said:**
> Why don't you explore the options that come with Lubuntu? I use a temp monitor and a CPU usage monitor to keep tabs on applications. You can find these monitors if you have lxpanel installed (which it should be in a default Lubuntu). 

Here is an oldish but largely valid read about it: [http://pclosmag.com/html/Issues/201010/page07.html](http://pclosmag.com/html/Issues/201010/page07.html)

One image is of the tab that allows you to add monitors and the other is an image of what mine look like: 53 is some temperature (I'm assuming it's that of the cpu) and the CPU % is currently 1.52%. I see a good correlation between temperature and CPU usage and so I feel the temperature is relevant.

I selected the "Temperature Monitor" in the list that pops up when I click the Add button in Panel Applets tab of Panel Preferences. However it shows -273 as the temperature by default, and that too in fluorescent green on light grey background making it difficult to read. See the screenshot of it below, with it's Settings control opened. Apparently the user needs to set all the temperature values...

[ATTACH=CONFIG]246436[/ATTACH]

---

### Post by vasa1 on 2013-09-22
> **santosh83 said:**
> I selected the "Temperature Monitor" in the list that pops up when I click the Add button in Panel Applets tab of Panel Preferences. However it shows -273 as the temperature by default, and that too in fluorescent green on light grey background making it difficult to read. See the screenshot of it below, with it's Settings control opened. Apparently the user needs to set all the temperature values...

[ATTACH=CONFIG]246436[/ATTACH]
Santosh, that's a problem reported by some users. There was a thread about it a while ago. I'll try and dig out the link although there didn't seem to be a solution; it works on some systems and not on others :(

Here: [http://ubuntuforums.org/showthread.php?t=2148296](http://ubuntuforums.org/showthread.php?t=2148296)

---

### Post by DuckHook on 2013-09-22
> **santosh83 said:**
> ...I just installed the latest AMD drivers for the desktop HD 6xxx series PCIe cards on 10.10 and both installation and use were trouble free! A bit amazing a driver compiled just a few months ago still works with a kernel and system dating back three years!Are you referring to the driver from the Ubuntu repos or did you install the one from the AMD site? I installed a bleeding edge (at the time) 7970 on a new system at the beginning of the year and had to install the corresponding bleeding edge drivers directly from AMD. This involves not only compiling the driver, but the addition of *dkms* and related apps so that every kernel update wouldn't hose my video driver. The process is complex, especially for new users, and almost always leads to problems unless you know exactly what you are doing. It was this process that I was referring to as not worth the risk.

In contrast, the drivers in the Ubuntu repos have usually been tested by the Ubuntu team to ensure compatibility with a number of different versions, so it's no surprise that they work well even with older versions and kernels. They also update automatically with apt-get update because they are supported by the update team. Problem is, they are not bleeding edge and will sometimes not work optimally with the latest HW.

As a rule, I recommend staying with the repo version of drivers unless the video card is so new that the repo version just doesn't work. The OP had already installed the--presumably latest--proprietary fglrx driver from the repos, so the only further step available to him was the bleeding edge driver directly from AMD.

Going off topic, just a note that 10.10 has reached end of life. You may wish to upgrade versions to continue covering yourself on the security front.> Here I have the fglrx from the repos installed on 13.10, and the above command gives:
```
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again. 
```

However the Catalyst Control Center does correctly display my graphics card and says the driver is installed. Should I take the risk of invoking 'aticonfig --install'?I believe what you mean is "aticonfig --initial". This command generates a generic ati-compatible xorg.conf file if one doesn't already exist. There is a very remote possibility that such a process could render your DE unstartable. You should still be able to log in to the CLI, so it is good practice to backup your old xorg.conf file before running the command. If you choose to run it, you will need to run it with *sudo* because you will be changing a system file and will need root privilges to do so.

The decision to run it is yours. If the new xorg.conf file hoses your X environment, you can always delete it and restore the backup. If you are comfortable with this restoration process, then I see the risk as being minimal. I'm happy monkeying around with my video system even for the sake of enabling marginally useful info like GPU temp, but then, I have a reasonable confidence in my ability to recover. Every user has different risk tolerance and recovery knowledge, so this decision varies with individual circumstance. Only you can determine if reward is worth the risk.

---

### Post by santosh83 on 2013-09-22
> **DuckHook said:**
> Are you referring to the driver from the Ubuntu repos or did you install the one from the AMD site? I installed a bleeding edge (at the time) 7970 on a new system at the beginning of the year and had to install the corresponding bleeding edge drivers directly from AMD. This involves not only compiling the driver, but the addition of *dkms* and related apps so that every kernel update wouldn't hose my video driver. The process is complex, especially for new users, and almost always leads to problems unless you know exactly what you are doing. It was this process that I was referring to as not worth the risk.

I downloaded the Catalyst 13.4 driver from this page, and simply unpacked and ran it:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

I had to do this because the fglrx in 10.10's repos did not detect my HD 6670 card, possibly because the card is a new model while 10.10 and it's fglrx are ~3 years old.
I simply clicked through the GUI installer, accepted the license and selected all components in custom install and everything completed without a hitch, and cccle also reports the driver and graphics card correctly.
This was what surprised me... that AMD's latest stable driver (released May 2013) for my card installs and works smoothly on 10.10!

> In contrast, the drivers in the Ubuntu repos have usually been tested by the Ubuntu team to ensure compatibility with a number of different versions, so it's no surprise that they work well even with older versions and kernels. They also update automatically with apt-get update because they are supported by the update team. Problem is, they are not bleeding edge and will sometimes not work optimally with the latest HW. As a rule, I recommend staying with the repo version of drivers unless  the video card is so new that the repo version just doesn't work.

Which is exactly my issue since the fglrx in 10.10's repository simply doesn't detect my HD 6670 card, falling back to VESA and software rendering. That's why I went to AMD's site to begin with.

> I believe what you mean is "aticonfig --initial". This command generates a generic ati-compatible xorg.conf file if one doesn't already exist. There is a very remote possibility that such a process could render your DE unstartable. You should still be able to log in to the CLI, so it is good practice to backup your old xorg.conf file before running the command. If you choose to run it, you will need to run it with *sudo* because you will be changing a system file and will need root privilges to do so.


Where is the x11.conf file on Ubuntu (Lubuntu) 13.10 anyway? I don't see any such file in /etc or /etc/X11... A system wide search from PCManFM also fails to find any such file...

---

### Post by Elfy on 2013-09-22
@santosh83 - please do not hijack threads - you are talking about an unreleased version for one thing - post in [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427) for your issue.

---

### Post by Yuvanesh on 2013-09-22
Hello, Yep i'm aware that its an apu and that performance wise it isn't fantastic. I did spend some time researching and i got that cpu because it was shown to be able to handle low to medium settings for the average game especially on lower resolutions. I believe on the average tv the resolution is lower then pc monitors. I've set up everything else, xbmc is very smooth. I have no issues whatsoever with anything else. I'll try the commands in the cli and post back on the results. Thank you :D. 

* I actually had a spare i7-960 pc sitting around with a vapor 5770, 16gb of ram and some high end gaming motherboard blah blah. I sold it off for aud$900 to build this for $700. I know it sounds dumb, but that pc was being under utilized and i felt that someone else would put better use to it. And i wanted to build my own htpc from scratch that was low powered and specifically designed for me to mess around and learn new things. (i know amd consumes more power then intel, but i just couldnt resist getting an amd processor). Apologise for the digression ,but i'm still so damn excited about this project.

---

### Post by mastablasta on 2013-09-22
A6 and A8 shoudl be well supported. I think A10 has some issues.

which is why thi sis a bit strange. i wonder if your issues exist in another desktop. note that KDE draws differently and uses different set of libraries.so might be worth a try, just to see if same problems exist there.

---

### Post by Yuvanesh on 2013-09-22
On ubuntu i tried switching to xfce, and kde but still has extreme tearing. On lubuntu other then the fact that dragging windows around shows signs of lag its perfect. From what i have read, it seems that the latest fglrx drivers has a bug. Still trying to figure it out but the only gpu intensive action will be movie playbacks which i have tested and is very smooth.

---

### Post by vasa1 on 2013-09-22
> **Yuvanesh said:**
> ...
3) I installed lm-sensors, but my temperature is shown incorrectly. I tried uninstalling/reinstalling but still the same. 
...
In case you're still interested, a little bit more about temperatures, lmsensors, and Lubuntu is here: [https://www.facebook.com/groups/lubuntu.official/permalink/535842359805922/](https://www.facebook.com/groups/lubuntu.official/permalink/535842359805922/)

Unfortunately, the Lubuntu Official page needs you to apply to join it. I keep a separate browser and (another) fake id for such things ;)

---

