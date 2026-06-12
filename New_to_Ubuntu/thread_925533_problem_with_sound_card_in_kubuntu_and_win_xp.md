---
title: "problem with sound card in kubuntu and win xp"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by badperson on 2008-09-20
Hi,
 put together a new build, 
 tyan s2932e mobo, amd operon chips, 
 win xp/kubuntu dual boot. 
 
 in xp, 
 card is detected in device manager,
 drivers are at most current version
 according to device manager, everything is fine. 
 ran the creative diagnostic utilities, according to that, everything is fine. 
 Went through the windows troubleshooting guide, didn't help. 
 went through the creative manual, made sure connections were good, still the same problem. 
 looked at all the system vol settings, they were all good, no "mute all" selected or anything like that. 
 card is selected and enabled, it's pci slot is listed in device manager.
 
 I changed the bios setting so that the os handles all the plug and play stuff, I didn't see any other audio settings in bios, and I looked through the mobo manual and didn't see any onboard audio to disable. 
 
 In kubuntu, 
 I in system settings\sound system, the hard ware was listed as auto detect...didn't see the hardware in the drop down. 
 
 
 tried two sets of headphones in all the jacks. 
 I'm new to kubuntu (used to gnome), so the troubleshooting I did in xp was a lot more extensive, but it feels like that card should have no problem running with xp, and it appears the system thinks it works....
 
 I haven't tried attaching speakers to the card and seeing if I get audio from there...I tried all the jacks on the card itself (the audio isn't hooked up on the case), I'm wondering if that's the problem? maybe the d/a conversion needs to happen in the speakers? 
 
 I need new speakers anyway, so I may try that. 
 
 Any ideas?
 bp

---

### Post by badperson on 2008-09-21
an update:

actually, my sound card does have an aux input (on the inside, meant to be connected to the cd drive) card itself; but there is on corresponding cable on the cd drive; it's a sata drive. 

I'm wondering if a pair of speakers could handle the d/a conversion...

Since windows seems to think everything is working, I would guess it's just a problem with no analog signal getting to the phones. 

just wondering what soundcard cd/drive combos others use.
thanks, 
bp



if not, and I do need to buy a new card

---

### Post by markbuntu on 2008-09-21
What sound card/chip do you have?
Until we know that, answers will be vague or non-existent.
You can find out with:

aplay -l

---

### Post by badperson on 2008-09-21
Hi,

I have a soundblaster audigy se card. 
I have dual amd opteron chips. 
thanks, 
bp

---

### Post by badperson on 2008-09-22
another thing,
I was poking around the internet and realized the card call for a pci slot, but I have it in a pci express slot...could that be the problem?
bp

---

