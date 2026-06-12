---
title: "error dont have hardware to run unity  run classic"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by 450rOOST on 2011-10-06
This is the error I got after install.  Id unity another desktop other than gnome?  What's cooler, more stable, which should I use, and does this error mean that my graphics card is not communicating?


I retained this piece of info after a command I entered last night while reading threads about this, not sure what command that was.
```
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)
```

---

### Post by wolfen69 on 2011-10-06
What is the model # of the video card?

---

### Post by wildmanne39 on 2011-10-06
Hi, go into additional drivers and install the nvidia driver for your card then you might be able to run unity.

Warning if you have an optimus card then when you install the driver you will not be able to boot back into ubuntu I believe, so you need to know first.
Thank you

---

### Post by 450rOOST on 2011-10-06
nVidia 525m Sandybridge 1GB

```
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 04b6
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 3000 [size=128]
	Expansion ROM at f1000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

```

---

### Post by proxy.qtz on 2011-10-07
Don't use nouveau. Try using proprietary drivers.

---

### Post by .hfxdesign on 2011-10-07
Also if you're still running into problems try updating your drivers. This can be done by opening a command terminal (CTRL+ALT+T) and using this command: ```
sudo apt-get update && sudo apt-get install nvidia-current
```

---

### Post by 450rOOST on 2011-10-07
awesome, thanks folks.  

Any comments or whether I should run unity or gnome?

---

### Post by thatguruguy on 2011-10-07
Try both, see which one you're comfortable with.

---

### Post by 450rOOST on 2011-10-07
> **thatguruguy said:**
> Try both, see which one you're comfortable with.


good answer, thanks.  I've checked out screen shots of unity and gnome.  I'm new to linux if you can't tell and I want to have a cool desktop.

---

### Post by wildmanne39 on 2011-10-07
Hi, also if you install the nvidia driver from a source other then additional driver, you will need to open synaptic and remove all but one because it does not uninstall the old driver you have to do it your self and it will only show one in additional drivers.

---

