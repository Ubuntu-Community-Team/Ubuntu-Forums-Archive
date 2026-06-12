---
title: "[SOLVED] Microphone does not work"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by gadec on 2008-07-04
Hi everyone, I am new to linux and to Ubuntu. I recently installed Ubuntu 8.04 on my Dell PC and I am very happy because everything is working except the microphone which I would need for Skype.

I have been looking for several threads about this topic and tried some of the suggestions but nothing worked :-(

I can say that I can hear sound from the speakers and from the headphone, so I believe that the sound card is properly recognized and configured. But when I try my minijack microphone (which works with Windows) I cannot hear my voice, record it with Sound Recorder or Skype. 

In sound preferences I set ALSA in Sound Capture and in the Volume Control I enabled everything in the Preferences and in the Tab Recording I unmute Capture and set the volume at 100% (I have the TABS: Playback, Recording, Switches and Options, in Recording I have Capture and Digital but I mute digital, it only makes "digital" noise and in Options I have IEC958 Playback Source put to ADC).

The output of aplay -l is:

**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]

  Subdevices: 1/1

  Subdevice #0: subdevice #0


That of lspci -v regarding the audio device is:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

	Subsystem: Dell OptiPlex 745

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]

	Capabilities: <access denied>


I don't know what else I should report. I will be very grateful if someone from the community could help fixing my problem.

gadec

---

### Post by apswartz on 2008-07-05
See if [any of these posts]("http://www.dellcommunity.com/supportforums/search?submitted=true&type=message&sort_by=score&advanced=true&q=microphone&phrase=&one_or_more=&without=&f=subject&f=body&f=attach&f=tags&page_size=250&author=&board_id=sw_linux") help...
[http://www.dellcommunity.com/supportforums/search?submitted=true&type=message&sort_by=score&advanced=true&q=microphone&phrase=&one_or_more=&without=&f=subject&f=body&f=attach&f=tags&page_size=250&author=&board_id=sw_linux](http://www.dellcommunity.com/supportforums/search?submitted=true&type=message&sort_by=score&advanced=true&q=microphone&phrase=&one_or_more=&without=&f=subject&f=body&f=attach&f=tags&page_size=250&author=&board_id=sw_linux)

---

### Post by gadec on 2008-08-27
Hi, thanks for the reply. I tried some of the proposed fixes but they did not work.

When I record I hear a choppy noise but I cannot hear my voice even if I scream!

Any other ideas?

gadec

---

### Post by Eredeath on 2008-08-27
I had a simular problem... My computer has a front mic jack that i was trying to use, i tried for hours to get it to work... when i couldn't i tried the plug directly into the audio card in the back of the PC and all-of-a-sudden my mic worked... so maybe you're having the same problem?

---

### Post by gadec on 2008-08-28
Hi thanks for the replies.

I think it is similar: originally I plugged the microphone in the back of the pc but it did not work, after looking carefully at the computer I found another plug in the front of my computer. I plugged and it works perfectly without installing or configuring anything.

gadec

---

### Post by kc6ymp on 2012-09-08
> **gadec said:**
> Hi thanks for the replies.

I think it is similar: originally I plugged the microphone in the back of the pc but it did not work, after looking carefully at the computer I found another plug in the front of my computer. I plugged and it works perfectly without installing or configuring anything.

gadec

i have the same problem ? i understand it is a preamp config setting ? the front is preamped for the microphone the rear is not it is a line in for a stereo ? i just cannot find the setting for the rear jack ?

---

### Post by wildmanne39 on 2012-09-09
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

