---
title: "Ubuntu newbie question about drivers"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by toxict35 on 2012-10-07
Hey gang, new Ubuntu user here, and first-time poster.

After a good two weeks of online researching, I was finally able to get my Linux install up and running a couple of days ago, due mostly to all of the info on this forum (another victim of the black screen), and a little bit of luck.

Which leads me to wonder; if the black screen problem is now fixed for me, do I still need a proprietary driver to insure that things remain in good working order? Obviously, I had to use the **nomodeset** command to get to this point, but will that be enough in the long run? And if not, where do I find the drivers that I need (HP Pavillion a566n, which as far as I can tell has integrated video built into the motherboard)?

At this point, my main use of Ubuntu has been web browsing more Ubuntu info, but I did check out Youtube just to see how the machine/OS combination handled video, and it seems just fine, so maybe all is good. So just wondering if I need to go any further before jumping into the deep end of the pool... ;)

Thanks in advance, everyone.

---

### Post by sandyd on 2012-10-07
Can you go to the terminal (Unity Dash, type "terminal", and select 'terminal')

and post the output of
```

lspci

```

Thanks!

---

### Post by toxict35 on 2012-10-07
Is this what you mean? I'm guessing that the 2nd line is what you were asking about.

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
**00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)**
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 03)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
01:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

-Tony

---

### Post by sandyd on 2012-10-07
A small trial - you do have to use nomodeset I think, but here are some options that can give you a bit more stability (if they work)

Replace 'nomodeset' with
```

i915.modeset=0

```

or

```

i810.modeset=0

```

Test them out, and see if either of them are more stable for you.

---

### Post by Paqman on 2012-10-07
You don't need separate drivers for Intel graphics chipsets, they're included in the Linux kernel.

---

### Post by toxict35 on 2012-10-07
I don't seem to be experiencing any stability issues with the graphics, and video looks to be fine. I was just wondering if not having drivers would cause any long-term problems that might arise in the future.

So if the drivers are included in the Linux kernel, why the **nomodeset** command in the first place? And please don't take this as my being argumentative, I'm just trying to learn. Thanks!

-Tony

---

### Post by dodo3773 on 2012-10-07
> **toxict35 said:**
> 

So if the drivers are included in the Linux kernel, why the **nomodeset** command in the first place? And please don't take this as my being argumentative, I'm just trying to learn. Thanks!

-Tony

Because your graphics driver and kms are two different things. Google kms aka 'kernel mode setting' and read up on it. It will make more sense if you do and you will probably understand why the solutions above work to get your system to boot properly.

---

