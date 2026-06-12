---
title: "Which distro would work best?"
date: 2013-11-12
forum: Recurring Discussions
---

### Post by stefbeukers on 2013-11-12
Hi,

Right now i'm using ubuntu 12.04 LTS (gnome classic). Everything works fine, except audio and video. Probably cause I have the Intel GMA500 video card. Which distro of Linux would work best with my machine? Hints/Tips?

Packard Bell Dot. M : 2GB RAM, Intel GMA500 (poulsbo), Intel Atom CPU Z520.

---

### Post by Johan De Cauwer on 2013-11-12
The question is why doesn't audio/video work? And what doesn't work? If you can't play a dvd or an mp3 it may have to do with codecs and that's probably the cause because here is what I find on wikipedia about the GMA500:

> The Intel SCH (System Controller Hub; codenamed Poulsbo) for the Atom processor Z5xx series features a GMA 500 graphic system. Rather than being developed in-house, this core is a PowerVR SGX 535 core licensed from Imagination Technologies.[25]

Intel describes this as "a flexible, programmable architecture that supports shader-based technology, 2D, 3D and advanced 3D graphics, high-definition video decode, and image processing. Features include screen tiling, internal true color processing, zero overhead anti-aliasing, programmable shader 3D accelerator, and 32-bit floating-point operations."

So I'd say stay with your version but download the multimedia codecs.

---

### Post by stefbeukers on 2013-11-12
I'm able to play videos and audio, but the audio isn't sync with the video and both seem to have some sort of lack. They stutter, if you know what I mean.

---

### Post by necromonger on 2013-11-12
try ue 3.42 thats what I use.

---

### Post by stefbeukers on 2013-11-12
ue 3.42? what is it and how do I use it?

---

### Post by Bucky Ball on 2013-11-12
*Thread moved to **Recurring Discussions**.*

Entirely down to the specs of the machine and what suits you best. Download the ISOs, burn some disks and try them, or try them in a virtual machine.

As suggested, you'd probably be better off trying to fix the audio/visual issues if that is the only reason you're trying something else. If the something else you try is another *buntu flavour there's every chance it will be exactly the same problems. This is supported by this:

> Unfortunately the support for this hardware is extremely limited on Linux. There are several drivers, but all lack certain basic features, such as future and current maintenance or support for suspend and hardware acceleration. 

... from here:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) 

... regarding the GMA500. Look here:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Video_Playback](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Video_Playback)

---

### Post by stefbeukers on 2013-11-12
Okay, going to read and try some stuff! Thnx!

---

