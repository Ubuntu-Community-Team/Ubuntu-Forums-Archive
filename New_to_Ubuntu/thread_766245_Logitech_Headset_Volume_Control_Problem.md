---
title: "Logitech Headset Volume Control Problem"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by wormser on 2008-04-25
My Logitech [ClearChat Comfort USB headset]("http://www.newegg.com/Product/Product.aspx?Item=N82E16826104214") is working, but I am having problems with the volume control.

The two channels are unable to lock.  The left channel seems to be the biggest issue.  In Volume Control the left channel will not turn up.  When I move it up, it snaps back to 0.  Clicking the lock button causes the right channel volume lower and it stays unlocked.  Turning the volume to 0 just lowers the sound but does not mute it.  The mute button does work fine.

Alsamixer allows me to move the left channel up but eventually it will drop back to 0.  The channels will move up together for a bit then the left channel will increment less compared to the right.

The mic is working properly.  I have not fully tested it but have been able to use Skype with it.

My guess this is a bug or a lack of support.  Has anybody got this headset functioning properly?  BTW, there is a brainstorm to get more USB headset support.  Vote for it here: [http://brainstorm.ubuntu.com/idea/3764/](http://brainstorm.ubuntu.com/idea/3764/)

---

### Post by bschleusner on 2008-04-25
I have a similar problem in 8.04

A work around is to just pause your audio, then move the mixer volume.

---

### Post by bschleusner on 2008-04-25
I figured it out. Just make it so that the channels are NOT locked together, and then when you press the volume up/down it will move them without jumping.
works for me!

---

### Post by wormser on 2008-04-25
I need to do more testing but there defenately is an issue with mine.  It seemed to work better today with Skype.  I'll post back when I have narrowed it down to the problem.

---

### Post by wormser on 2008-04-27
It is looking like this is a bug with my laptop volume control relating to the volume control on the headset.  Any other laptop users seeing this issue?

---

### Post by T313C0mun1s7 on 2008-07-12
I am having this same issue on my desktop running 8.04.1

This is a definite issue. I have no problems with the internal sound card and alsamixer, just the usb headset. My internal card is dsp and my USB headset is dsp1.

I don't know what bschleusner meant my pause the audio, but neither of his suggestions work for me.

Here is the workaround I found. In a terminal window type
```
alsamixer
```This will get you the text version of the alsa mixer, it seems to work better.

Since as I stated before my USB headset is not the default device, but rather dsp1 - then I need to start the mixer in this way:
```
alsamixer -c 1
```you can then use the arrow keys to select the channel and adjust the volume. If the volume is not the same on the left and right hit = to balance it. Esc exits, you may not notice a change until you exit. I hope this helps.

---

