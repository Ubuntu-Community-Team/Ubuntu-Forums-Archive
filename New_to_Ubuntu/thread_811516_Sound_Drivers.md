---
title: "Sound Drivers"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by General Specific on 2008-05-29
New to Ubuntu.  How do I reload sound drivers.

I loaded HH 8.04 on a Gateway Laptop.  Everything worked, including the sound.  Now my apps say I don't have a sound driver loaded.

Where do I begin?

---

### Post by quelx on 2008-05-29
Post the bits that say **multimedia** or **audio** or **media** or the like from the output of **lspci | less**

Open a terminal (**Applications** > **Accessories** >  **Terminal**) and type ```
lspci|less
```

---

### Post by ApUUbunU on 2008-05-29
Incientally, I am doing the same thing. Here is the output for my audio card:

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

Now just to get me some drivers...
For some reason Ubuntu doesn't recognise my audio card when I go to the hardware drivers (System > Adminstration > Hardware Drivers), though my graphics card is recognised.

---

### Post by quelx on 2008-05-29
> **ApUUbunU said:**
> Incientally, I am doing the same thing. Here is the output for my audio card:

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

Now just to get me some drivers...
For some reason Ubuntu doesn't recognise my audio card when I go to the hardware drivers (System > Adminstration > Hardware Drivers), though my graphics card is recognised.

from the terminal try ```
sudo modprobe snd-via82xx
``` then try to play something (right click the **Volume control** > **Preferences** and see if your device shows up now

---

### Post by ApUUbunU on 2008-05-29
I put that code in the terminal, and then I went to Volume Control > Preferences as you said to do.
Here are the option I get:
VIA 8236 (Alsa Mixer)
Realtek ALC655 rev 0 (OSS Mixer)

However, I don't think any of these are my card. It should be Realtek AC97, according to the output of that code you gave me.
VIA 8236 looks very promising as it has all (I think) of the connections that were available on my Windows system. But I also have the option to choose a great deal more of volumes. I shall try this current set up, and see if my rear speakers are working, which were not under the previous configuration.

---

### Post by ApUUbunU on 2008-05-29
Update:

I've tried all devices, but sound only comes out of two speakers. The rear and centre/subwoofer speakers aren't utilised. I think I need a more AC97 specific driver..., which I will look for soon.

---

### Post by General Specific on 2008-05-29
Mine did work, but then it stopped.

I will try these and post back.

---

### Post by General Specific on 2008-05-29
> **quelx said:**
> Post the bits that say **multimedia** or **audio** or **media** or the like from the output of **lspci | less**

Open a terminal (**Applications** > **Accessories** >  **Terminal**) and type ```
lspci|less
```


00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

---

### Post by quelx on 2008-05-29
> **General Specific said:**
> 00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

then try ```
sudo modprobe snd-atiixp
``` from the terminal

---

### Post by General Specific on 2008-05-29
Module snd_atiixp not found.

---

### Post by quelx on 2008-05-29
```
ls -la /lib/modules/2.6.24-1{6,7}-generic/ubuntu/sound/alsa-driver/pci/snd-atiixp.ko
```

and 

```
sudo update-modules
```

---

