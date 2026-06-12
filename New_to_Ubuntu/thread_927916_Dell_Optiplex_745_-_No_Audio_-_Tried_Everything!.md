---
title: "Dell Optiplex 745 - No Audio - Tried Everything!"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by dizzygoldfish on 2008-09-23
Hi all,

I'm very much a noobie to the world of Ubuntu.  So far everything has been great.  However, no matter what I do I cannot get sound to work on my Optiplex 745.  

I have been all through the instructions found [here.]("http://ubuntuforums.org/showthread.php?t=205449")  I can see the various audio levels in alsamixer and everything seems to be setup properly but no dice.  Just for the record, I've also tried the Dell Wiki, some stuff at the ALSA project site, and all kinds of other tutorials.

I also went through the advice found [here]("http://ubuntuforums.org/archive/index.php/t-465599.html") but that actually caused my sound card to stop functioning all together.  I eventually reinstalled Ubuntu.

Can anyone help me figure out what I'm missing?  My card may not be supported, according to the Alsa website it looked like they had several ICH"X" listed but not my ICH8.  Is that the case?

Thanks!


Results of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Results of lspci -v:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell OptiPlex 745
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

Not sure what additional information I need to post, let me know if I've missed something critical.

---

### Post by overdrank on 2008-09-23
Hi and welcome, I have closed your duplicate post and moved this one to ABT 
Absolute Beginner Talk so hopefully you will receive some assistants. :)

---

### Post by sneeks on 2008-09-24
hi there,at least we can see your card and i have had these working before.
have you done the simple stuff first by going to your sound icon and right clicking it,going to options and unclicking the headphone icon,this is normally a quick fix but if you still have no go let us know.

---

### Post by dizzygoldfish on 2008-09-25
> have you done the simple stuff first by going to your sound icon and right clicking it,going to options and unclicking the headphone icon

I beleive so.  There is no options when I right click the speaker icon up next to the clock.  Under preferences I get a list for "Select the device and track to control" which is currently set to "HDA Intel (Alsa Mixer).  Headphone is in the list of devices along with Master, PCM, Front, etc. but there is no way to turn them off.  

The following settings are checked under the switches tab I see the following:
Line-in Capture: unchecked
Microphone Capture: unchecked
IEC958: checked
Mix: checked
Mix Mono: unchecked.

Under the options tab the only option is IEC958 playback source which is set to PCM.  

Under the playback screen everything (including headphones) is unmuted with the volume at 100%.

Thanks for the reply, I hope this answers your question.

I think I've tried all of the easy stuff, I've gone step-by-step through as many audio troubleshooting posts that I can find.

---

### Post by jamesknight on 2012-01-04
HI..

Hope im not too late.. check this link for the solution

[http://ubuntuforums.org/showthread.php?t=1474729](http://ubuntuforums.org/showthread.php?t=1474729)

---

### Post by overdrank on 2012-01-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

