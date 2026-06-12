---
title: "22&quot; (1920 x 1080) dual screens with Radeon R300"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by JdeP on 2012-04-22
I've been reading forum threads and trying various things all day with no luck, so it's time to call on the community's help and kindness ...

Having successfully used Ubuntu 11.04 with dual screens (both Acer P225HQ) for some months using the proprietary driver, I have just been given some newer hardware (including a newer graphics card) and installed 11.10. I hope to be able to use the pre-installed open source driver from now on. 

The 'Displays' option in 'System Settings' recognises both monitors, and they work fine as 'Mirror displays'. But I want to use them like two separate workspaces, not as duplicates of one another.

If I uncheck the ‘Mirror displays’ option and click ‘Apply’ the screens go blank for a short while, then re-appear with messed-up displays; after a while they revert to the mirrored displays setting. In earlier attemps I got a message saying that my displays were too big to use with default Unity so I have switched to Unity 2D.  It may be relevant that one is connected by VGA, the other by DVI.

Thanks in advance!

Peter

Here’s some output from lshw that may help:
           *-display:0
                description: VGA compatible controller
                product: Radeon R300 ND [Radeon 9700 Pro]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:c0000000-c7ffffff ioport:d000(size=256) memory:feae0000-feaeffff memory:feac0000-feadffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: Radeon R300 [Radeon 9700 Pro] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:c8000000-cfffffff memory:feaf0000-feafffff


Let me know what further info you may need to diagnose/fix this problem.

---

### Post by JdeP on 2012-04-25
I don't want anyone to waste a lot of time on trying to solve this problem, as I now appear to have a solution.

I tried a whole range of things, including clean-installing several versions of Ubuntu from 10.04 onwards (I really don't like Unity, so I avoided recent releases to being with.) The monitors worked flawlessly without any extra configuration from me, in 10.04! But then some of my programs would not run correctly, so I had to upgrade, and the monitors started having problems again. 

As as last resort I downloaded the not-released-until-tomorrow 12.04 and so far it has behaved perfectly. Now I just have to get used to (or get rid of) Unity ...

---

### Post by sffvba[e0rt on 2012-04-25
> **JdeP said:**
> I don't want anyone to waste a lot of time on trying to solve this problem, as I now appear to have a solution.

I tried a whole range of things, including clean-installing several versions of Ubuntu from 10.04 onwards (I really don't like Unity, so I avoided recent releases to being with.) The monitors worked flawlessly without any extra configuration from me, in 10.04! But then some of my programs would not run correctly, so I had to upgrade, and the monitors started having problems again. 

As as last resort I downloaded the not-released-until-tomorrow 12.04 and so far it has behaved perfectly. Now I just have to get used to (or get rid of) Unity ...

A lot of work went into getting dual displays to work correctly in 12.04... and also in improving Unity.  I would suggest giving it a good go, for at least a week or two and try to use it in the way it is trying to make you use it rather than the way you always did.  Then if you it isn't for you there is more WM and DE available than you care to use :)


404

---

