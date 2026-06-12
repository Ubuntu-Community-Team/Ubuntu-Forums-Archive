---
title: "dead audio out jack and question about sound cards"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-09-16
Hi Ubuntu Community:

I connect my computer to my stereo amplifier with a 3.5mm jack in that green hole in the back of my computer to the RCA jacks in the back of my stereo amplifier.

That green hole is the output audio jack that was on the sound card that is integrated into my motherboard, I think.

After a few years, that green jack in the back of my computer died.... 

What should I do??

I've looked at the community support sites [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards") on sound cards. I'm pretty confused by them. It looks like if I install a new sound card, there might not be drivers for it. 

After refering to that community page, it looked like the Behringer UCA202 would work... I bought it, plugged it in, and it didn't!

What should I do? Buy another sound card?? How do I choose one, and how to I make sure that it is "plug and play?" Or do I have to find and install drivers?


Thanks,
Phil Smith
Duluth, GA

---

### Post by pyromanic123boom on 2008-09-16
Let's find out if your soundcard has popped or just the jack.
Open up a terminal and type in 

alsamixer

Then see what the outputs are. Should be a few ones- scroll to the left and right with the arrow keys. You should find a Master or something similar. If you find it, try toggling it all the way to max and make sure mute is off. fiddle with the alsamixer to try and obtain some results. 

Do you have a font panel audio jack? If you do, use that one. 
If there's no luck with any of this, your best option is probably either a external USB soundcard, or internal one. The computer is funcational but it seems useless without one of those simple fuctions, like sound.

---

### Post by gregphil on 2008-09-16
When you tried your new sound card, did you disable "motherboard audio" in the BIOS?

Sometimes the operating system has a hard time dealing with more than one audio device, or at least you need to know how to select it.

****************
BTW, to connect you computer to your stereo you should really use an isolation transformer.  This is needed to protect the sound card and to eliminate 'hum' that typically results from the slight difference in the ground voltage between the two pieces of electronics.  In the U.S. Radio Shack sells such a device for about $20.

---

### Post by Old Jimma on 2008-09-17
Hi Pyromaniacboom:

Thanks for your reply.

alamixer works. When I plugin my 3.5mm minijack into the green input plug, I get sound, but only on 1 channel and not 2 (for stereo).

Both the front and back plugs on my computer have that same problem... sound on one channel and not the other... I switched the wires on the RCA ports on the back of my stereo amp to test whether one of them were dead... When I did that switching, the "other" speaker worked, indicating that the green hole was transmitting only 1 channel, not 2.

I bought an external USB sound card... or at least something that was listed on the Ubuntu community soundard page: [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards")

It is a Behringer U-Control UCA202. It has a USB plug, RCA inputs, and RCA outputs. WHen I plug in the USB, and connect the RCA outputs to the RCA cables that lead to the RCA inputs on my stereo amp, there is no sound.

It makes me thing that a driver is missing, or that I go fooled on that purchase.

Any thoughts on how to get that U-Control thing to work?

THanks,
Phil

---

### Post by Old Jimma on 2008-09-17
Hi Gregphil:

How do I disable "motherboard audio" in the BIOS?

I saw the isolation transformer at [http://www.radioshack.com/sm-isolation-transformer--pi-2103994.html]("http://www.radioshack.com/sm-isolation-transformer--pi-2103994.html")

How do I connect that thing, and what does it connect to what???

Thanks!
Phil

---

### Post by Old Jimma on 2008-09-17
PhilGreg was right about needing to disable the onboard sound card to make my external USB soundcard to work. 

I checked the Ubuntu community page to identify one that was automatically detected and was known to work. See the page in making your own selection: [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards) 

I found the forums discussion on how to disable your onboard soundcard on your bios. ALATACK is credited to this solution at [http://ubuntuforums.org/showthread.php?t=233294](http://ubuntuforums.org/showthread.php?t=233294) 

1) Issue the command "lsmod | grep snd-*
" and find the mods for your internal sound card

My onboard soundcard was identified by the following lines in that listing:

snd_intel8x0 33692 0
snd_ac97_codec 93088 1 snd_intel8x0
snd_ac97_bus 2304 1 snd_ac97_codec

2) sudo gedit /etc/modprobe.d/blacklist
3) For each module, append "blacklist <module>" to /etc/modprobe.d/blacklist where <module> is the name of your module.
Here is what I added to mine:
# turn off internal soundcard
blacklist snd_intel8x0
blacklist snd_ac97_codec
blacklist snd_ac97_bus
4) Reboot and enjoy.



Plug your external soundboard into your USB port, plug the RCA outputs into the leads to your stereo, and then resume a life of music enjoyment.

My thanks to philgreg and pyromaniac (!) for their help.

Many, many thanks, Ubuntu community!!

Best regards,
Phil Smith
Duluth, GA

---

### Post by pyromanic123boom on 2008-09-18
Great that you got it to work! Audio is a little difficult to deal with in linux - I had some issues when I first installed, but a little hunting around, and it was fixed. Again, it's great you got it fixed.

---

