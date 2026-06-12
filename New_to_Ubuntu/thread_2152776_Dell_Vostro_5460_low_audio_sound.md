---
title: "Dell Vostro 5460 low audio sound"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by badsector16 on 2013-06-09
I have just bought a  new Dell Vostro 5460 with ubuntu preinstalled. 
However the problem is that the internal speaker is so slow almost as if it is silent.

i have  been looking around and i found this command

cat /proc/asound/card0/codec* | grep Codec

this is the output

Codec: Realtek ALC290
Codec: Intel PantherPoint HDMI

i tried searching for fix Realtek ALC290 and i found no luck.

The sound works perfectly fine on windows 7

---

### Post by mveplus on 2013-06-29
I do have the same problem with my Dell Vostro 5460-1316, 

I was so happy to buy it pre-installed with Ubuntu, but this very low sound output compared to Windows 7, kills all multimedia positive experience.

Looked everywhere for change or recompile the drivers and hacks and tried everything I found but no change, I guess it's because this one has 2.1 sound (build-in sub-buffer) does not coupe with Linux drivers well.

```

$lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M / GT 620M/625M/630M/720M] (rev a1)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
03:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

```

dmesg.log:[ATTACH]244269[/ATTACH]

So if anyone has any clue or advice will be glad to try it out. I hate to switch back to Windows when I want to watch movie or listen music....

Best Regards,

---

### Post by shunji on 2013-06-30
Hi Vostro 5460 users, unfortunately to declare... I have the same problem too! =(

In the time mean, I can only plug into my external speaker for music and movies.

Let's hope this issue can be rectified soon. =)

---

### Post by purezen on 2013-07-01
Hey guys..!

Just confirming that I have the same issue with my Vostro 5460 as well.. Also, does the issue have something to do with UCM profiles or something similar ?
Hoping that the issue get resolved soon..:-)

---

### Post by purezen on 2013-07-03
Hey guys !

I have started a thread for discussing the issues with the Vostro 5460 in the Dell Support section at:
[http://ubuntuforums.org/showthread.php?t=2159407](http://ubuntuforums.org/showthread.php?t=2159407)

Hope that you check it out :smile:

Thanks..!!

---

### Post by wsxadf on 2013-07-03
Can you guys posts some hardware information? The output for

```
sudo lshw -C sound
```

will be very helpful.

---

### Post by purezen on 2013-07-04
Hey..!

Here's the output for the command.

  *-multimedia
       description: Audio device
       product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:47 memory:f2510000-f2513fff

---

### Post by wsxadf on 2013-07-04
Hmm, seems like there are no unclaimed device... But this output is pretty annoying.

```
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
```

Can you try

```
alsamixer
```

and try to raise both master and pcm volume.

---

### Post by purezen on 2013-07-04
Well, they are already maxed out..

---

### Post by purezen on 2013-08-05
Hey..!

I would suggest changing the forum of this thread from 'Absolute Beginners Section' to 'Dell Ubuntu Support'.

Please consider the same. It might be more appropriate.

Thanks..!

---

### Post by coffeecat on 2013-08-07
> **purezen said:**
> I would suggest changing the forum of this thread from 'Absolute Beginners Section' to 'Dell Ubuntu Support'.


Since you've started a thread about Vostro 5460 issues in the Dell sub-forum - [http://ubuntuforums.org/showthread.php?t=2159407](http://ubuntuforums.org/showthread.php?t=2159407) - I'll close this one to avoid duplication.

Thread closed.

---

