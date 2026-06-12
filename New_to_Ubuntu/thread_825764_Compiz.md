---
title: "Compiz??"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by meatlegs on 2008-06-11
Can someone tell me what this means after typing 'Compiz' into the terminal?

Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

Cheers

---

### Post by Joeb454 on 2008-06-11
What video card do you have? And do you have the restricted driver installed for it?

---

### Post by meatlegs on 2008-06-11
Umm, I'm not sure. 
I'm running an Acer Travelmte 2420 with Hardy

---

### Post by Joeb454 on 2008-06-11
Ok can you post the output of ```
lspci
``` Thanks :) and please encase the output in [code] tags :)

---

### Post by meatlegs on 2008-06-11
ok, I think this will encase it:
[00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)]

---

### Post by meatlegs on 2008-06-11
oops sorry
how do you do that?

---

### Post by Joeb454 on 2008-06-11
It doesn't matter - it's not too long :) Sometimes you get really long posts from that command, that's all.

It's the # symbol in the advanced reply

---

### Post by Joeb454 on 2008-06-11
And you have an Intel graphics chipset :) Go into System > Administration > Hardware Drivers

Is anything listed in there that needs to be enabled?

---

### Post by meatlegs on 2008-06-11
```
oh you mean like this?
```
:)

---

### Post by meatlegs on 2008-06-11
No there is nothing listed:confused:

---

### Post by meatlegs on 2008-06-11
I did a compix check and got this:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04.1
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

```

---

### Post by overdrank on 2008-06-11
> **meatlegs said:**
> I did a compix check and got this:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04.1
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

```

Hi and it appears you are using the vesa driver and you will need to use the intel driver or the i810 driver. You may just reconfigure your xorg and correct the issue.

---

### Post by meatlegs on 2008-06-11
Oh...
How would I get those drivers or configure the xorg???

---

### Post by stchman on 2008-06-11
That card should work OOB on Hardy using Compiz.  If not try this:

```
sudo apt-get install xserver-xorg-video-intel
```

That should take care of the problem.

---

### Post by meatlegs on 2008-06-11
Hi there
I tried that and got this:
```
:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

:confused:

---

### Post by ZarathustraDK on 2008-06-11
If you have the intel GMA x3100 graphiccard, which I think is the one on your chipset, then it's blacklisted by compiz by default. I had the same problem.

You can remove it from the blacklist by editing a certain file (can't remember which, sorry, somebody else probably knows). It's a matter of removing a "#" from one line.

It's blacklisted because not all the compiz-plugins work with the x3100, the "rain"-plugin is one of them for instance. Still, all the good stuff works: cubespin, wobbly windows, scale, app-switcher etc.

Somebody remember where the blacklist-file for compiz is?

---

### Post by meatlegs on 2008-06-11
Awesome, thanks for the input DK
Now all we need is to find that line!:p

---

### Post by stchman on 2008-06-11
> **meatlegs said:**
> Awesome, thanks for the input DK
Now all we need is to find that line!:p

The X3100 is part of the 965 chipset.  You card should work OOB.

My recommendation is to try Hardy.  If you like then do a clean install.

---

### Post by meatlegs on 2008-06-11
I am on Hardy, although it was an upgrade
So you think a clean install would do the trick?

---

### Post by squet.pack on 2008-06-11
This should get it done. In a Terminal type:

```
echo 'SKIP_CHECKS="yes"' >> ~/.config/compiz/compiz-manager
```

This will create a problem with displaying video.

1. Alt-F2

2. Type gstreamer-properties

3. Under the Video tab select for output as "X Window System (No xV)"

   If i'm correct this isn't a x3100 because it is the wrong intel chipset. I may be wrong though post back on if it works.

---

### Post by meatlegs on 2008-06-11
Hi Squet,
Nope, still no dice.
Although after those steps the screen did some crazy flashing thing when I changed the visual effects from 'none' to 'normal'
But I still get the 'Could not enable desktop effects"

---

### Post by squet.pack on 2008-06-11
Run this command in a Terminal:

```
compiz --replace ccp & emerald --replace &
```

Post the output from the command here. If you see these in the output:

```
Wnck-WARNING **: Unhandled action type (nil)
```

Or

```
A handler is already registered for the path starting with path[0] = "org"
```

They won't interrupt normal usage of Compiz so don't worry bout' those errors.

[EDIT] I noticed that Compiz didn't find Xgl so I'm guessing you are using AiLGX if so, you may have to start Compiz with this command:

```
LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp &
```

---

### Post by meatlegs on 2008-06-11
Ok, sorry for the long response, here's what I get from the first command:

```
noble@noble-laptop:~$ compiz --replace ccp & emerald --replace &
Checking for Xgl: [1] 15669
[2] 15671
noble@noble-laptop:~$ not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/home/noble/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/home/noble/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'


```

---

### Post by meatlegs on 2008-06-11
Ok, now I'm running the live cd and the effects work, should I just do a clean install??

---

### Post by st33med on 2008-06-11
meatlegs, no. You should instead have the 'intel' driver enabled. Usually, Ubuntu detects your gpu, but, for some reason, it does not...

do this in the terminal:
```
cat /etc/X11/xorg.conf
```

---

### Post by meatlegs on 2008-06-11
Wow!
That did it St33med!
Thanks to all for their help, my Hardy is now solid!!

---

### Post by stalkier on 2008-06-11
> **meatlegs said:**
> I am on Hardy, although it was an upgrade
So you think a clean install would do the trick?

Yes I think it would cure it. (Or should at least)

---

### Post by stalkier on 2008-06-11
> **meatlegs said:**
> Wow!
That did it St33med!
Thanks to all for their help, my Hardy is now solid!!

Don't forget to mark the thread as solved. Glad we could help...well I didn't help but you get the picture. ;)

---

### Post by overdrank on 2008-06-11
> **meatlegs said:**
> Wow!
That did it St33med!
Thanks to all for their help, my Hardy is now solid!!

HI and what worked. The command posted just lets you view the xorg.

---

### Post by meatlegs on 2008-06-11
I'm not sure exactly what just happened. I did all the above steps, but I then had to run out for a couple hours and once I was back, I restarted and tried the last command, not knowing what it did. I tried effects and it worked!?
So not sure exactly what happened, was it the restart or the steps or both combined??
Hmm, does that count as 'Solved?'

---

