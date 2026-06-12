---
title: "High Pitch Sound when not playing any audio"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by dodskaper on 2012-01-30
Hello,

I have a problem with my speakers. I'm running a dual boot Mac OSX Lion and Ubuntu 11.10.  

Whenever I am not playing any audio, my speakers give a really high pitch noise. Kinda annoying when trying to work in silence.

Is there a way to fix this?

Thanks in advance

---

### Post by rgreener25 on 2012-01-30
mute it when your not using it? or you could see if there is a dodgy connection on the lead or jack

---

### Post by QIII on 2012-01-30
Muting is avoidance, not a solution.

I'm assuming the problem is not present when running OSX?

What happens in Ubuntu when you turn down the volume low with software control.

If you turn it back up with software control, does the squeal go away if you turn the speaker volume knob (or whatever hardware control you have) down a bit?

What happens if you turn your mic gain down?

---

### Post by rgreener25 on 2012-01-30
btw. What mac is it and are speakers built in

---

### Post by dodskaper on 2012-02-01
> **QIII said:**
> Muting is avoidance, not a solution.

I'm assuming the problem is not present when running OSX?

What happens in Ubuntu when you turn down the volume low with software control.

If you turn it back up with software control, does the squeal go away if you turn the speaker volume knob (or whatever hardware control you have) down a bit?

What happens if you turn your mic gain down?

Thanks for the replies.

Indeed nothing happens when I'm using OSX. 

When i turn the volume down using the software control the pitch goes and stays away. However I have to do this every time I boot the system or log back in. I changed the drivers but this didn't help. I closed my mic but still the high pitch remains. 

I use a late 2008 MacBook pro. So the speakers a build in.

---

### Post by QIII on 2012-02-01
Do you hear the squeal/hum in the background when you are playing something or only when you are not?

Both speakers?  One speaker?

---

### Post by dodskaper on 2012-02-01
> **QIII said:**
> Do you hear the squeal/hum in the background when you are playing something or only when you are not?

Both speakers?  One speaker?

Only when I don play any sound what so ever. When I played a sound the pitch is gone for like 2 seconds then its back. You hear a small click or bump when I start to play a sound. You can compare it when you plug in headphones into your mp3 player.

And the problem involves both speakers.

---

### Post by QIII on 2012-02-01
Ignore what I had before.

Would you run


```
lspci -v
```

And post back the section on your audio device?

---

### Post by dodskaper on 2012-02-04
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Computer Inc. Device 00a3
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at 9b500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by QIII on 2012-02-04
Thanks.

I just popped on for a minute to check in on you.  Unfortunately, we have house guests this weekend and I am already being rude -- a hazard of being an old fart who is still a geek.

I just found a lot of google hits that are along the lines of your problem, but I only had time to do a quick look at a couple of them.  Those didn't quite fit.

If something in the results of the google query below is helpful, and especially if it works, please let everyone know what that was and mark the thread closed so others can benefit.

I'll check in during the week to see how it's going for you.

```
site:ubuntuforums.org sound intel 82801h oneiric mac
```

---

### Post by dodskaper on 2012-02-05
Thanks QIII for the help! I'll check Google with your search Query and report back when I've found something.

---

