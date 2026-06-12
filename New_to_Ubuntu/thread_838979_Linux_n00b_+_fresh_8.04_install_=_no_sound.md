---
title: "Linux n00b + fresh 8.04 install = no sound"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-06-24
Just installed ubuntu 8.04 and i get no sound at all. 

I did a search on the forums, and got lost in trying to follow along.

Did an "aplay -l" in terminal and it came back with:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I believe this to be my video card and not my sound. I have a Dell Dimension E521. It is a 7.1 onboard soundcard. I am using Logitech 5.1 speakers. I also put in a Nvidia 8600 GTS in my system. That is why i believe the playback list is wrong. 

Under Sound Preferecnces. my default mixer tracks options are: 
- HDA NVidia (Alsa mixer)
-SigmaTel STAC9227 (OSS Mixer)    --I think this is what i want
- Playback: ALSA PCM on front:0 (STAC92xx Analog via...
- Capture: Monitor Source of ALSA PCM on frount:0
- Capture: ALSA PCM on front:0 (STAC92xx Analog) vi..

If you could also tell me what all these other options are that would be cool.

Things I have tried:
-  One post said to go to System-Prefrences-Sounds and change all the options to ALSA instead of autodetect and reboot. needless to say it didnt work. 

- Another said to reinstall the ALSA files, and to mess around with the config files. Dont want to do that just yet without specific-to-my-machine instructions.

-Checked my BIOS to make sure the sound was turned on. 

Thanks in advance, mike c.

---

### Post by aquavitae on 2008-06-24
I think that although its a Dell sound card, it has an Nvidia chipset. When you play music, does it play (without sound) or do you get an error message? Also try checking the volume using the terminal command ```
alsamixer
```I've sometimes found that the unimportant looking volumes towards the end have an effect.

---

### Post by Nepherte on 2008-06-24
The entries listed in aplay -l are your sound card. It's probably an on board sound card where the chipset of your motherboard is nvidia. Sigmatel is the codec used. I have a similar card and it works out of the box. So you should get it working too. Try this trouble shooting guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

As a last resort (postpone this one till the very end), you could try reinstalling alsa manually. I recently wrote a very specific guide how you should do it: [http://bart.4aps.be/linux/howto_compile_alsa_drivers.html](http://bart.4aps.be/linux/howto_compile_alsa_drivers.html)

---

### Post by deathvalleyjoker on 2008-06-24
I dont get any error messages, just no sound. I tried the alsamixer in the terminal, and then either that or just waking up made me think to check the cables in the back.

When the cables are plugged into the 5.1 slots, no sound. but when i take the green plug out and put it into the single output slot i get sound, but only out of my bass, center, and two fronts, nothing out of the rear left or right. 

So I guess this has turned into a 5.1 sound question: how do i get 5.1 sound to work?

Thanks, mike c.

---

### Post by Nepherte on 2008-06-24
I guess you shouldn't use 5.1 slot. This is what I've found: [http://ubuntuforums.org/showthread.php?p=4718373](http://ubuntuforums.org/showthread.php?p=4718373)

I hope it works out for you.

---

### Post by deathvalleyjoker on 2008-06-24
"It's probably an on board sound card where the chipset of your motherboard is nvidia. Sigmatel is the codec used. I have a similar card and it works out of the box. "

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Dell Unknown device 01ed
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

You are right my sound card is nvidia onboard. The first link was the most helpful so far. no that i knida know what i am looking at, i am gonna try it.

---

### Post by Tomatz on 2008-06-24
You need to correctly setup pulseaudio for 5.1 sound. Check out the link below:

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by deathvalleyjoker on 2008-06-24
> **Tomatz said:**
> You need to correctly setup pulseaudio for 5.1 sound. Check out the link below:

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

Thanks I will try this out and let you know how it goes.

---

### Post by aquavitae on 2008-06-24
I have a very similar setup (nvidia chipset and 5.1 sound) and I seem to remember having the same problem when I installed it. But I can't remember how I resolved it - I think it was actually just an application setting. Kaffeine was set to use stereo or something like that. Try checking the settings for your music player and see if you need to change it. Maybe also try the gstreamer config.

---

### Post by deathvalleyjoker on 2008-06-24
Tomatz: Tried that links method and it didnt work..

aquavitae: i double-clicked a mp3 of mine and it opened it in totem(?) movie player. i went to settings-audio tab, then put it to 5.1. it came up with an internal dataflow error. no idea what that means. i know what a dataflow is, but not where it could be or why in a linux system as i am new to linux.

i get this error in each audio setting(?) under system-sound. 

sorry if i am missing anything. i am doing this from memory as i am at work now. if anyone has any more ideas i can try, i will try it out as soon as i get home.

thanks, mike c.

---

### Post by Tomatz on 2008-06-24
> **deathvalleyjoker said:**
> Tomatz: Tried that links method and it didnt work..

aquavitae: i double-clicked a mp3 of mine and it opened it in totem(?) movie player. i went to settings-audio tab, then put it to 5.1. it came up with an internal dataflow error. no idea what that means. i know what a dataflow is, but not where it could be or why in a linux system as i am new to linux.

i get this error in each audio setting(?) under system-sound. 

sorry if i am missing anything. i am doing this from memory as i am at work now. if anyone has any more ideas i can try, i will try it out as soon as i get home.

thanks, mike c.

Can you post the exact error (word for word).

---

### Post by aquavitae on 2008-06-24
Sounds like a bug in totem. Post the message as tomatz says, but maybe also try a different engine, e.g. mplayer (you'll probably have to install it first).

---

### Post by deathvalleyjoker on 2008-06-24
tinking around with another player made me relize its not the program bc no 5.1 on diffrent players. it made me look at my set up again i played with system-preferences-sounds some more and got it working. I believe it was tomatz first suggestion bc i use the pulseaudio setting to finally get it. 

Thanks everyone for helping me on this.

---

