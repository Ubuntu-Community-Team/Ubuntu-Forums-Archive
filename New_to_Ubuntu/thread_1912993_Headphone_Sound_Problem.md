---
title: "Headphone Sound Problem"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by BHS427 on 2012-01-21
[SIZE=2]I've just installed Ubuntu 11.10 (64-bit) and its been a great improvement from my former Windows Vista. The only problem I've come across so far is that my headphones do not give me any sound.

The computer speakers work fine but the moment I plug anything into the audio jack everything is silent. The biggest problem is that I can't listen to anything on my headphones, but it also means that I can't use my much-better-than-computer speakers on my desk.

I've noticed that in the Output tab of the Sound System Settings the connector switches from Analog Speakers to Analog Headphones whenever I put anything into the audio jack.

I've confirmed that it's not a problem with my headphones and my audio jack was working perfectly fine before I switched to Ubuntu.

My computer is an Asus G51V if that helps. If there's any other information I should supply go ahead and let me know

Thanks


[/SIZE]

---

### Post by trikster_x on 2012-01-21
In terminal, run:
```
alsamixer
```
Make sure the master volume for headphones is turned up.

---

### Post by BHS427 on 2012-01-21
I got to alsamixer and can adjust the volumes on Master and Speakers, but Alsamixer won't allow me to change the level of headphones. It's stuck on 00

---

### Post by trikster_x on 2012-01-21
Can you run alsamixer and post a screenshot of the headphone volume control?

---

### Post by BHS427 on 2012-01-21
Here 'tis.

(Still not sure about the best way to put images up on this site)

---

### Post by trikster_x on 2012-01-21
Try turning your line volume all the way up and unmuting it. I'm not certain why alsa has disabled your headphones. It may be that on your card they are considered line out, not headphones.

---

### Post by heshoots67 on 2012-01-21
> **BHS427 said:**
> Here 'tis.

(Still not sure about the best way to put images up on this site)

What type of card are you using.

---

### Post by BHS427 on 2012-01-22
I attempted to try the Line Out and it didn't work. But at least I have a much better idea of what the problem is so thanks for that.

I think my sound card is: HDA Intel at 0xf9ff8000 irq 48

At least thats what came up when I selected system info, asound/cards in Alsamixer. If that doesn't seem right I'll try a different way

---

### Post by trikster_x on 2012-01-24
Use the command:
```
lspci -v
```
in a terminal and copy paste all the information for your audio device, please. What you gave us was the driver your system is using.

Should look like:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at 9f300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by BHS427 on 2012-01-28
Oh, I see. Here it is.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a3
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by sandyd on 2012-01-28
> **BHS427 said:**
> Oh, I see. Here it is.

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a3
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
you need a options snd-hda-intel.
Try these until you get sound.
[https://help.ubuntu.com/community/HdaIntelSoundHowto#Manually_Specify_Module_Parameters](https://help.ubuntu.com/community/HdaIntelSoundHowto#Manually_Specify_Module_Parameters)

---

### Post by BHS427 on 2012-01-31
> **sandyd said:**
> you need a options snd-hda-intel.
Try these until you get sound.
[https://help.ubuntu.com/community/HdaIntelSoundHowto#Manually_Specify_Module_Parameters](https://help.ubuntu.com/community/HdaIntelSoundHowto#Manually_Specify_Module_Parameters)

Just worked my way through that page. It still doesn't work; Alsamixer doesn't seem to recognize Headphones as a valid output and there's no bar to adjust volume for Headphones

---

