---
title: "Yeah. It's me again. Still need help."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Haioko on 2008-07-29
I know I said I was getting rid of Ubuntu. But I'm going to have to stick with it until my copy of XP I ordered arrives. But I need help fixing my sound.

Sound files play fine but no sound comes out of my speakers. I don't know what the make it is because it's onboard.

Help please?

---

### Post by billgoldberg on 2008-07-29
In a terminal, type

```
alsamixer
```

Make sure nothing is muted.

---

### Post by Haioko on 2008-07-29
Comes up
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by lukjad on 2008-07-29
How do you know that it plays fine? If the sound doesn't come out, there are a few things that come to mind.

1) Do you have ubuntu-restricted-extras installed?

Go to Application->Accessories->Terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

Try that and tell us what happens.

---

### Post by billgoldberg on 2008-07-29
Go to system -> preferences -> sound

Switch everything to alsa.

Then run the command again.

If that doesn't work, it might be the speakers itself.

---

### Post by halitech on 2008-07-29
> **Haioko said:**
> I know I said I was getting rid of Ubuntu. But I'm going to have to stick with it until my copy of XP I ordered arrives. But I need help fixing my sound.
see, told ya ;) 
> 
Sound files play fine but no sound comes out of my speakers. I don't know what the make it is because it's onboard.

Help please?


as lukjad007 suggested, install the restricted extras and try again. another option would be to see if ogg files work, if they do, then its a matter of the codecs, if not there is some other issue

---

### Post by Haioko on 2008-07-29
> **lukjad007 said:**
> How do you know that it plays fine? If the sound doesn't come out, there are a few things that come to mind.

1) Do you have ubuntu-restricted-extras installed?

Go to Application->Accessories->Terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

Try that and tell us what happens.

It's already at the newest version.

And becuase on the media player the file IS playing. Like the file plays (The time decreases you see the scroller moving, it changes song when one is done) But there isn't any sound

[QUOTE=billgoldberg] 

Done. The exact same thing came up. it's definetly not the speakers. They work fine.

It might be because I need a driver for my motherboard? Which I can't install.

---

### Post by halitech on 2008-07-29
open a terminal and post the results back of```
lspci
``` and hopefully we can see what you have for a card

---

### Post by Haioko on 2008-07-29
05:00.1 Audio device: ATI Technologies Inc Unknown device aa28

Unknown.

Full Code

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 95c5
05:00.1 Audio device: ATI Technologies Inc Unknown device aa28

---

### Post by Haioko on 2008-07-29
Bump. I really would like to get this sorted. Any help is apreciated. Thanks.

---

### Post by halitech on 2008-07-29
ok, this makes no sense to me. Googling the sound card comes up with information about the Radeon video cards and Radeon drivers...


do you have an ATI video card in this computer?

---

### Post by steveneddy on 2008-07-29
I assume this is a laptop?

Do headphones work when you plug them in?

---

### Post by Haioko on 2008-07-29
No it's a desktop. And they don't =/

---

### Post by halitech on 2008-07-29
I think we should work in just 1 thread instead of 2 as I think both threads are related to one another

---

### Post by Haioko on 2008-07-29
Ok. Sorry.

---

