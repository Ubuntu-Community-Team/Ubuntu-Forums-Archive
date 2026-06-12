---
title: "[SOLVED] another no sound thread"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Mr Pockets151 on 2008-06-04
This is the second time I've tried ubuntu.  I still can't get any sound.  It's not my sound card because it works in XP and Mandriva without any problems.  I have an Audigy 2 Platinum (driver emu10k1).

The results of ```
aplay -l 
```is
```
card 1: Audigy2 [Audigy 2 Platinum [SB0240P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 2 Platinum [SB0240P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 2 Platinum [SB0240P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 2 Platinum [SB0240P]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I've searched the forums for "no sound" and tried everything that other users have suggested to no avail.  Any suggestions.  Google isn't working to great either.

---

### Post by ajmorris on 2008-06-05
hi there,
even though you have marked the thread as solved, perhaps you can post the answer to your problem for others that may have this, it may help them. I assume you just ran sudo alsaconf in a terminal and selected emu10k1 from the list as your driver, (since that sound card and driver work out of the box) 

AJ

---

### Post by meaufaux on 2008-06-12
I am having a similar issue in 8.04, and so far haven't been able to find a solution in my forum trolling and Googling efforts.  I think I have my Audigy2 set as the default audio device, but I get no sound.

Similar to the OP, I have an Audigy2, though I also have a VT8237 southbridge with AC'97 audio which, despite being disabled via the BIOS, was apparently detected by Ubuntu during install and seems to be the default sound device.

I've changed the device to "Audigy 2 Platinum [SB0240P] (Alsa mixer)" via File -> Change Device in the Volume Control GUI.  This doesn't appear to have any effect.

I've seen people mention running 'sudo alsaconf' from the terminal, but when I do this it says "command not found" and I cannot turn up alsaconf with 'locate alsaconf' either.

aplay -l gives me the following:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 2: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any insight would be greatly appreciated.

---

