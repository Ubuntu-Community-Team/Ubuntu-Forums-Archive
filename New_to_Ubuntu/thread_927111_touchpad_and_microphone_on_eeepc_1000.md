---
title: "touchpad and microphone on eeepc 1000"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by tjikko on 2008-09-22
Heya, 

I got Ubuntu almost fully working on my eeepc 1000, only 2 things remain.

I can't get gsynaptics to work it keeps give me the error
"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"
But 1 did Enabled it
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option          "SHMConfig"             "true"
EndSection
```


What could be the problem? I can't find any how to on the net.

And the other thing is that the build in microphone doesn't work. I tryed the how to of the eeepc900 but that one didn't do the trick.

If there is a helping hand out there I would really appreciate it

Tjikko

---

### Post by mister_pink on 2008-09-22
I have a 901, so this advice is probably applicable.

Firstly, have you already installed the custom kernel? ([www.array.org](www.array.org)). I'm guessing so as otherwise nothing would be working.

For the microphone I'm guessing you have done the thing in alsa-mixer as you mention a how-to. (Run alsa-mixer and turn on capture). Even after this I thought it was not working as blowing into it gives nothing on the speakers, but if I use sound recorder it does seem to work.

I'm not entirely sure what you're trying to do with the touchpad. The shmconfig thing I know does not work with the eeePC though.

---

### Post by tjikko on 2008-09-24
I want to alter de touch sensitivity en I want to enable horizon scrolling since that worke with the default linux that came with it. Would that costum kernel support all of that then?

---

### Post by mister_pink on 2008-09-24
I don't know that the custom kernel would help you with that. It sorts out the wireless and everything without having to do anything manually.

I'd guess you're more likely to get an answer on an eee forum than here

---

### Post by piq on 2008-10-21
the build in microphone doesn't work


I've got an eee 1000 and am using ubuntu eee. The microphones are working fine. I just had to increase the sensibility a bit.

---

