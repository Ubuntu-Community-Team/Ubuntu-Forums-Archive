---
title: "What does the &quot;nomodeset&quot; boot parameter actually do?"
date: 2020-04-17
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-04-17
Hello all,

So I recently posted about a couple of issues I was having after installing Ubuntu 18.04 LTS on my Toshiba Satellite laptop, one of which was a black screen hang shortly after powering up, the strange thing was it only happened roughly three in four times I started the laptop up, sometimes more but sometimes less. Out of sheer desperation I followed a guide I found online designed to fix a very similar problem, which advised to edit the grub boot parameters to include "nomodeset". To my surprise it did and has continued to work with no more black screen, however I'm not sure if it is either safe or ideal to leave it this way (I edited /etc/default/grub to make it permanent)

My understanding is the "nomodeset" parameter stops Ubuntu loading a specific driver it uses to display the boot animation (and possibly login screen?) that is not compatible with some GPU's, I also read that this is supposed to be a temporary fix until you download the proprietary drivers your GPU needs, although I *also *read that the LTS version of 18.04 comes with the open source components of AMD's graphics drivers included (I actually have AMD integrated graphics) so a bit confusing.

So my questions are...


[LIST=1]
[*]Is my understanding of "nomodeset" correct, if not I'd be grateful if someone could elaborate (or even if so!)
[*]Is it a good idea to install AMD's drivers and remove "nomodeset" to see if it's fixed and go from there?
[/LIST]

Any info is much appreciated, thanks in advance!

---

### Post by CatKiller on 2020-04-17
In the beforetime the resolution (or screen mode) was set differently in a bunch of different places: the BIOS would set the initial mode, then Grub would set a mode supported by the ancient VESA BIOS Extensions (VBE) system, dependent on which obsolete video card your GPU pretended to be, then X would set a different mode dependent on the driver and the detected display. Lots of mode switches, and lots of mess, and no shared infrastructure. Then Kernel ModeSetting (KMS) was developed that scraps all of that nonsense in favour of simply letting the Linux kernel handle it since the kernel has to interact with the hardware anyway and the software needs to interact with the kernel anyway. nomodeset tells the kernel not to do KMS, so you fall back to the prior hodge-podge. It's useful when nouveau (the open-source driver for Nvidia hardware) fails to detect things properly through KMS, but not for much else.

For newer AMD drivers than the ones that came with the initial 18.04 release you'd want the Hardware Enablement Stack (HWE) selected (the default for fresh installs from 18.04.2 onwards) and a newer version of Mesa. There are different PPAs available that give versions of Mesa with different levels of newness.

---

### Post by Yellow Pasque on 2020-04-17
>  however I'm not sure if it is either safe or ideal to leave it this way

It's not ideal at all since it disables video hardware acceleration. Using the CPU for graphics is going to be slower and use more battery.

> I also read that this is supposed to be a temporary fix until you download the proprietary drivers your GPU needs
In some cases, yes, but that strategy isn't universal. (And it's more likely on Nvidia GPU's, where the proprietary driver is usually the best choice).

> Is it a good idea to install AMD's drivers and remove "nomodeset" to see if it's fixed and go from there?
You already have AMD's open source drivers installed (and that's what most users should be using). From your other thread, it appears you have an E2-1800 APU with RadeonHD 7430. If that's the case, your GPU is too old for the AMD proprietary driver anyway.

[QUOTE=CatKiller]For newer AMD drivers than the ones that came with the initial 18.04 release you'd want the Hardware Enablement Stack (HWE) selected (the default for fresh installs from 18.04.2 onwards) and a newer version of Mesa. There are different PPAs available that give versions of Mesa with different levels of newness.[/QUOTE]

The HWE stack already comes with a newer version of Mesa. (Actually, the newer version of Mesa is also backported to those using the original 18.04/.1 kernel/X versions too.)
Talking about Mesa PPA's seems like it's getting off-topic, or at least, way ahead of the problem. Also, note that the RadeonHD 7430 uses the older r600g driver. I wouldn't expect a bleeding edge version of Mesa to enable additional features or significantly improve 3D performance.

---

### Post by CatKiller on 2020-04-17
> **Yellow Pasque said:**
> Talking about Mesa PPA's seems like it's getting off-topic, or at least, way ahead of the problem.

Well, yes, no argument there. It's just way better than the ex-Windows-user instinct of downloading some random thing off some random website when they're talking about installing drivers.

---

### Post by jcdenton1995 on 2020-04-19
Thanks for the explanation! I'm forced to leave it that way for now as it takes me about 5 attempts at booting up before I get any display output without, but the only impact on me so far is that I can't use the zoom feature under accessibility, although I'm sure there are more I haven't encountered (not tried hooking up an external monitor yet).

---

