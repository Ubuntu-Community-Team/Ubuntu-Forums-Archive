---
title: "how do i find the name of my soundcard driver?"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by lizziemel on 2012-04-23
Hi,

I'm a real newby here, and trying to work out why the sound isn't working on my linux system.  I believe my sound card is being detected, and am trying to work out if the driver is available.  Having used several terminal commands from this page :[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) I am trying to manually start the driver, but am unsure as to what part of the name I need to use for the driver.

this is the info i get back from the following terminal window:

 lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 8415
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

--
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: nVidia Corporation Device 0794
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fbe7c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Really not sure what I am trying to decipher from what, so any help appreciated.

Thanks, L.

---

### Post by papibe on 2012-04-23
Hi lizziemel. Welcome to the forums!

This is the name of your driver: HDA Intel. And this is the actual driver module: snd-hda-intel

Hope that helps.
Regards.

---

### Post by lizziemel on 2012-04-24
Cheers, I shall have a play with that - looks quite obvious when you point it out, guess I was quite tired at that point of the evening!

---

### Post by anewguy on 2012-04-24
As simple as it sounds, if you're not getting sound click the volume icon on the top bar and be sure (1) the volume is up far enough (2) it's not muted [I had a new install once actually mute my sound for some reason, but only that 1 time].

If you are having other problems please post back with more detail.

Dave ;)

---

### Post by lizziemel on 2012-04-25
Cheers again, yes I've been searching out the sound all over, and it all appears to be at max levels.  I've seen the test, which I think was under system settings and that doesn't do anything either.

Just doing a bit more research, before I post more info/questions.  Thanks

---

