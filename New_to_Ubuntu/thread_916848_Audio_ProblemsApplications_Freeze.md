---
title: "Audio Problems/Applications Freeze"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by iamthemicrowave on 2008-09-11
Hi everyone.  I am having some sort of sound problem on my linux rig.  Occasionally audio files freeze my computer and the program running it.

Rhythmbox, Youtube.com, Pandora.com...None of these will play audio files.  I hit play but the track will not start, and no sound comes out.  Rhythmbox will crash and I have to restart it.

The problem can be fixed by restarting my computer.

I followed the audio sticky to install everything, including medibuntu.  This problem does only happen occasionally, but it is a large nuisance.

Thank you for reading this, and any input/advice you have.  I am running openJDK with icedTea and icedTea browser plug-in.

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
(only relevant device shown)
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

---

### Post by dhtseany on 2008-09-12
Hey,
I have a Latitude D610 with pretty much the same problems. Try the following code and see if it temporarily fixes it. If so then I'm gonna submit a bug ticket.

```
$: /etc/init.d/alsa-utils restart
```

Peace
Sean

---

### Post by jdorenbush on 2008-09-12
I have a problem with Pandora.com as well. It feels like it is really slow and sometimes just won't work. However, it occasionally will play songs, so it is not totally screwed up.

I download fast and I have high speed cable Internet, so connection speed shouldn't be a problem.

Seeing as my external hard drive with over 200GB of media crashed, all I have is Pandora for music. So I would really like a solution. Any help is more than appreciated.

---

### Post by carlo c on 2008-11-07
I have a possibly related problem- Pandora skips like a CD. Repeats the same note after playing fine for as much as 20 songs in a row. It continues repeating dididididididididi even after I turn off Pandora, even after I turn off Firefox, even after I go off-line (Sprint aircard), until I shut down the computer! (HP dv6324us laptop running Ubuntu Hardy Heron 8.04, 2 gig RAM). (Pandora plays fine on the Windows side.) I'm kinda new with Linux, I like the idea of it and the speed of boot up. I don't know if the problem is Pandora, Firefox, or Ubuntu- I'm guessing Firefox? Thank you for any help.

---

