---
title: "Internal mic not working on dell vostro 1310"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Mal__ on 2008-07-06
I've tried searching for solutions to this and found many posts relating to checking the devices enabled in volume control, preferences.  I have enabled all devices and set all volumes to max.

I then found this thread: [http://ubuntuforums.org/showthread.php?t=707231&highlight=ICH8+sound]("http://ubuntuforums.org/showthread.php?t=707231&highlight=ICH8+sound") with the advice from 'hyperandy'.  Following these instructions seemed to work up until the very last stage - specifically these instrutions: 

> Reboot the machine and run more these comands:

```
sudo cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
sudo depmod -a

```

When I try this I get the following:
```
cp: cannot stat `/lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory

```

If I manually navigate to the /lib/modules folder I see 2 folders - 2.6.24-16-generic and 2.6.24-19-generic.  So I thought changing 24 for 22 in the code above would work, but sadly not.

The output I get from lspci -v is:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Unknown device 026f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f8300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

I'm pretty new to linux so not entirely sure what I'm doing, so any advice would be much appreciated!

Thanks in advance,

Mal

edit: I'm running ubuntu 8.04

---

### Post by KnightOnline on 2008-09-12
I have the same laptop and the same problem, did you find any solution?

---

### Post by EarloftheWest on 2008-09-12
I have the Lenovo T61 with a similar problem.
Here's what I have to do:
Right click volume icon.
Open Volume Control 
Edit
Preferences
Add one of the Input Sources.

You may have to add all of the volume control inputs one by one until you find the one that will work. Also, you'll probably need to play with the volume and mute on the individual sources.

---

### Post by KnightOnline on 2008-09-12
I've done that already, and set everything to maximum. still nothing.

---

### Post by Mal__ on 2008-09-13
Sorry I could not get the problem fixed.  I would recommend having a look at this thread ([http://ubuntuforums.org/showthread.php?t=804780&highlight=dell+microphone](http://ubuntuforums.org/showthread.php?t=804780&highlight=dell+microphone)) if you have not done so already as it may provide a solution.  

I have not got ubuntu installed right now so can't try it, but have been keeping an eye on that thread as I plan to give it another go when I have more time.  Hope it helps!

---

