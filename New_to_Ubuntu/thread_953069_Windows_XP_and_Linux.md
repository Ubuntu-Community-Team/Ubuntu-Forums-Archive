---
title: "Windows XP and Linux"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Adamisaw12 on 2008-10-19
Hi, im new to linux and i just wanted to know if windows xp drivers worked for linux as well. Thanks

---

### Post by subaruwrc01 on 2008-10-19
No.  Linux driver and Windows drivers are completely different.

---

### Post by Shazaam on 2008-10-19
The only Windows drivers that I know of are some network card/wireless card drivers and those require ndiswrapper to be functional.

---

### Post by niyonk on 2008-10-19
You will find MOST of your driver just work fine out of the box.
The drivers that might not work right away are the wireless ones.

So, no need to worry about the drivers right now.
Also, the wireless drivers issues isn't very common.
Use the LiveCD to see if UBUNTU or any other Live Distro recognises ur hardware

Good Luck!

---

### Post by forger on 2008-10-19
Instead, you can always ask for help with a specific device (brand & model number please) :)

---

### Post by Adamisaw12 on 2008-10-19
i have a sound blaster audigy se and it wont work b/c i dont have the cd and i need the driver. any help?

---

### Post by bodhi.zazen on 2008-10-19
Title changed to a more appropriate title, one less inviting of trolls and flames ;)

---

### Post by forger on 2008-10-20
According to [this linked topic]("http://ubuntuforums.org/showthread.php?t=337985"), people were using sound blaster audigy out-of-the-box, meaning without any hassle for drivers

If you have Ubuntu or the livecd, boot in Ubuntu or livecd environment, then go  to Applications > Accessories > Terminal and execute:
```
sudo update-pciids
sudo update-usbids
lspci
lsmod
```

(note: it will ask for your password, you type it in, it won't be "seen", but press enter after typing it)

Select the output, right click in terminal program and click copy, then reply and paste the output back here :)

---

### Post by forger on 2008-10-20
For your information, the driver in question I think is included in ubuntu:
> PCI Boards
Most SoundBlaster Live, Audigy, Audigy 2, and Audigy 4 cards are supported by the latest ALSA drivers. Most Linux distributions include these drivers. For the latest information on which cards are known to work with the ALSA drivers, look at ALSA's sound card matrix.

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

---

### Post by forger on 2008-10-20
> Sound Blaster Audigy SE
Sound Blaster Audigy Value
CA0106
Details 	[PCI] Digital/Analog input does not work yet. Needs more development work. 
```
$ modinfo snd-ca0106 
filename:       /lib/modules/2.6.27-7-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
license:        GPL
description:    CA0106
author:         James Courtier-Dutton
srcversion:     02A88F862080210795F2472
alias:          pci:v00001102d00000007sv*sd*bc*sc*i*
depends:        snd,snd-pcm,snd-page-alloc,snd-rawmidi,snd-ac97-codec
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
parm:           index:Index value for the CA0106 soundcard. (array of int)
parm:           id:ID string for the CA0106 soundcard. (array of charp)
parm:           enable:Enable the CA0106 soundcard. (array of bool)
parm:           subsystem:Force card subsystem model. (array of uint)
```

---

