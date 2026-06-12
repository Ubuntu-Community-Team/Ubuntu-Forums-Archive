---
title: "Ubuntu sound Issue"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by fenT1 on 2008-07-30
Hello,

I have a pesky little problem with Ubuntu 8.04 and/or My dell precision 650. The problem is that my sound card seems configured (as shown below with the 2 commands) but the sound doesn't seem to work. Also i tried upgrading, updating and troubleshoot options on this an many other forums.

cat /proc/asound/cards
0 [Audigy2 ]: Audigy2 - Audigy 2 ZS [SB0353]
Audigy 2 ZS [SB0353] (rev.4, serial:0x10031102) at 0xccc0, irq 23

sudo lshw -C multimedia
*-multimedia
description: Multimedia audio controller
product: SB Audigy
vendor: Creative Labs
physical id: e
bus info: pci@0000:05:0e.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1

---

### Post by voteforpedro36 on 2008-07-30
Well,[here]("https://answers.launchpad.net/ubuntu/+question/30828")'s what a Google search pulled up.

Try running:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-ubuntu-modules-$(uname -r)
```

As the one post there states.

---

