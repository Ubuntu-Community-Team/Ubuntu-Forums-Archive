---
title: "Hardy Heron(sp) and 8139too"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by senkard on 2008-05-01
Hi, I just downloaded the hardy heron desktop i386 iso, and after burning and trying to boot up the live cd, it stops and drops me down into BusyBox, and says that I need to try to boot with 8139too... now when I installed Gutsy I didn't have this problem, does anyone have any suggestions what to do..

---

### Post by aeiah on 2008-05-01
from a quick google it looks like its an ethernet driver, and it seems that sometimes it isnt compatible with 8139cp, which is what it tries to load. im not sure how to get around this besides pulling out the network card, installing, and then trying to manually install the right driver. perhaps the 8139too is present on the livecd and you can invoke it somehow upon boot. you should try and find out if you can do this first before pulling the card out etc

---

### Post by senkard on 2008-05-02
I can't take the Network Card out because I'm using a laptop, the thing that's weird is that I didn't have this with older versions of Ubuntu.

Thanks for the suggestion though, aeiah.

---

### Post by senkard on 2008-05-04
I'll put some more information about my problem... I'm using an Acer Aspire 5050 laptop, I dual boot ubuntu gutsy and windows, the previous versions of Ubuntu have always booted up via live CD. Hardy will not, it drops me down to busybox and says something about using the 8139too driver, as the guy posted above it has something to do with my NIC, it's realtek and since it's my laptop it's built into the motherboard.

Does anybody have any idea on what to do, or a possible way to fix this?

PS I could update from Gutsy to Hardy, but I'm afraid if I do that I'll have more problem then I would by trying to do a fresh install...

---

### Post by senkard on 2008-05-05
I don't mean to sound rude, but why is it so hard for someone to reply or to help me out on this?

---

### Post by sortlan on 2008-05-06
Have the same problem here... Never had any problem in earlier versions of either Ubuntu or any other distro...

Have Linux Mint now, so need a cleen install for 8.04. There is no live cd for Heron out there with the right driver?

---

### Post by senkard on 2008-05-10
It's kinda lame that not a single person has any ideas on what to do, or any helpful suggestions, what a joke...

---

### Post by ugm6hr on 2008-05-10
> **senkard said:**
> It's kinda lame that not a single person has any ideas on what to do, or any helpful suggestions, what a joke...

There is a problem with your LiveCD.

I have an Acer Aspire 5051AWXMi (5050 derivative).

It has the same ethernet card (8139), and the 8139too driver works fine (as you would expect) - lshw:
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:c7:d9:1e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

```

I have used the i386 and AMD64 LiveCDs of 8.04 / Hardy, and both work fine.

I installed 64-bit in the end.

I suggest you check the CD, re-download or re-burn.

---

### Post by senkard on 2008-05-10
ugm6hr thanks for you reply, did you start it up with a special command to have the 8139too driver enabled? or did it just work out of the box?

Oh and about the 64-bit version, is java and flash working correctly finally?

---

### Post by ugm6hr on 2008-05-10
> **senkard said:**
> ugm6hr thanks for you reply, did you start it up with a special command to have the 8139too driver enabled? or did it just work out of the box?

Oh and about the 64-bit version, is java and flash working correctly finally?

Nope. CD in drive and turned on.  My wifi (Atheros) and ethernet just work.

64-bit flash works.  Java not so much.  But I installed 32-bit SwiftWeasel for that with a How-To script from here for that (alongside 64-bit FF3).  Haven't had to test it out yet.

---

### Post by sortlan on 2008-05-14
I used the alternate CD, and did the installing prosess directly (not by the live CD).

Worked like a dream :)

---

