---
title: "Acer Aspire One 5251 User w/ Internet but w/out Wireless Capability"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by Tupaq on 2012-01-28
Hello all,

I am new here at the fora though I have been using Ubuntu, as a beginner, on my laptop of the type described in the title for over a year now and used a netbook of Acer manufacture even earlier.

For now, I have but one problem: Unlike my previous Acer Netbook, I cannot get my current, otherwise wonderfully functioning Acer Aspire One 5251, to use any of the three or so wireless routers that I have purchased for it, leading to my being forced to shuttle my house's single modem to and from my study and the family room, often thrice or more per day.

Obviously, this is a great issue and prevents my household's other member from using our only computer much of the time as well as preventing me from keeping my computer in my study all the time. Thus, I need to figure out how to get the driver (or something else?) for my computer, which displays "disconnected" with regards to networking atop my computer screen. I know that this is not a problem with my operating system as my previous netbook worked fine with all wireless routers.

By the way, I have no trouble using wired Internet connections anywhere, but I need to figure out how to get a wireless router to work for my computer as I cannot get another modem from my Internet service provider (I live in the United States of America, by the way.)

Thank you all very much for any help that has been provided to me!

---

### Post by westie457 on 2012-01-28
Hello and welcome.

Could you open a terminal and run the following commands one at a time  and paste all of the output into a new reply here between ```
 and [Code] tags by clicking the # symbol at the top of the message pane.
[CODE]lspci -vnn

lsmod

lshw -C network

rfkill list all
```


Thank you

---

### Post by Tupaq on 2012-01-28
```
 description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 88:ae:1d:15:08:e8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb ip=76.20.36.86 latency=0 multicast=yes
       resources: irq:27 memory:d1100000-d110ffff
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: c4:46:19:24:69:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d1000000-d1003fff

```

---

### Post by westie457 on 2012-01-29
Hi could we have the output from the other commands please. There is not enough information given so far to help you properly. 

Any suggestions for the correct driver to use will be guess work and might not work.

---

### Post by Tupaq on 2012-01-29
> **westie457 said:**
> Hi could we have the output from the other commands please. There is not enough information given so far to help you properly. 

Any suggestions for the correct driver to use will be guess work and might not work.I apologize; though I have been using Ubuntu for quite a while, I have almost no experience at using the terminal.

```
lspci -vnn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d2100000-d22fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00005fff
	Memory behind bridge: d1100000-d20fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1000000-d10fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391] (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 26
	I/O ports at 7038 [size=8]
	I/O ports at 704c [size=4]
	I/O ports at 7030 [size=8]
	I/O ports at 7048 [size=4]
	I/O ports at 7010 [size=16]
	Memory at d2307000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2306000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2307500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2305000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2307400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c] (rev 40) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 7000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=64

00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399] (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2304000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
	Flags: fast devsel

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 6000 [size=256]
	Memory at d2200000 (32-bit, non-prefetchable) [size=64K]
	Memory at d2100000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2210000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:036e]
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at d1100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e021]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

lsmode
No command 'lsmode' found, did you mean:
 Command 'lsmod' from package 'module-init-tools' (main)
lsmode: command not found
yachay@Yupana:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
ipmi_msghandler        32803  0 
nfsd                  238903  11 
lockd                  64881  1 nfsd
nfs_acl                 2245  1 nfsd
auth_rpcgss            33767  1 nfsd
sunrpc                193578  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3437  1 nfsd
joydev                  8740  0 
dlm                   118691  0 
snd_hda_codec_atihdmi     2367  1 
configfs               22475  2 dlm
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203440  1 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_hda_intel          22069  2 
snd_seq_midi            4557  0 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
uvcvideo               57438  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_mixer_oss          13746  1 snd_pcm_oss
radeon                678831  3 
videodev               34425  1 uvcvideo
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ttm                    49847  1 radeon
drm_kms_helper         29329  1 radeon
lib80211_crypt_tkip     7596  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l1_compat            13251  2 uvcvideo,videodev
drm                   163747  5 radeon,ttm,drm_kms_helper
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                31724  2 ttm,drm
snd_timer              19130  2 snd_pcm,snd_seq
i2c_algo_bit            5028  1 radeon
snd                    54244  16 snd_hda_codec_realtek,snd_seq_oss,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_rawmidi,snd_mixer_oss,snd_pcm,snd_seq,snd_seq_device,snd_timer
led_class               2864  0 
psmouse                63677  0 
serio_raw               3978  0 
shpchp                 28835  0 
wl                   1959598  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
pata_atiixp             3148  0 
tg3                   109324  0 
ahci                   32680  2 
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 88:ae:1d:15:08:e8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb ip=76.20.36.86 latency=0 multicast=yes
       resources: irq:27 memory:d1100000-d110ffff
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: c4:46:19:24:69:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d1000000-d1003ff
```f

---

### Post by anewguy on 2012-01-29
Please see the following thread - in particular, follow the link in the thread and follow the 2 posts mentioned.

[http://ubuntuforums.org/showthread.php?t=1778661]("http://ubuntuforums.org/showthread.php?t=1778661")

Dave ;)

---

### Post by Tupaq on 2012-01-30
> **anewguy said:**
> Please see the following thread - in particular, follow the link in the thread and follow the 2 posts mentioned.

[http://ubuntuforums.org/showthread.php?t=1778661]("http://ubuntuforums.org/showthread.php?t=1778661")

Dave ;)Excuse me, but could you perchance tell me exactly which two posts I am to follow? I am not sure what you mean and I am still confused. ;)

---

### Post by Tupaq on 2012-01-30
Here is what I think is my wireless chipset: 
```
Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
```I am very new at the terminal and thus am quite possibly mistaken, but this is part of the output from the ```
lspci
``` command (the full command in the ```
link,lspci | grep -i wireless
``` ,did not work, by the way.)

---

### Post by anewguy on 2012-01-30
Perhaps this will clarify?
> Old June 14th, 2011 	  #5
bkratz
Chocolate-Covered Ubuntu Beans
 
Join Date: Apr 2009
Beans: 2,400
	
Re: upgraded to 11.04 and unable to get wireless working
Post 44 of this thread has a pretty good description

[http://ubuntuforums.org/showthread.php?t=1748245&page=5]("http://ubuntuforums.org/showthread.php?t=1748245&page=5")


> 
Old June 17th, 2011 	  #6
GrandVizier
5 Cups of Ubuntu
 
Join Date: Feb 2006
Beans: 27
Ubuntu 11.04 Natty Narwhal
	
Re: upgraded to 11.04 and unable to get wireless working
thanks bkratz - between post #44 and the subsequent post #55 on that thread, my wireless is now working

So follow the link at the end of the 1st quoted post, read that thread paying particular attention to posts 44 and 55.

---

### Post by anewguy on 2012-01-30
The controller you posted is the wired ethernet controller.

The wireless would be:

08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e021]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

You use the USB manufacturer id and product it (the [14e4:4357] ) and do a net search, and you find it is a Broadcom 4322.  The same search returned many page hits on the net with comments/solutions.  What I've been posting here is from one of those links.

Remember:  Google/Yahoo/Bind, etc., are your friend! ;)  It's what most of us use trying to find solutions for people.

Dave ;)

---

### Post by Tupaq on 2012-02-01
> **anewguy said:**
> The controller you posted is the wired ethernet controller.

The wireless would be:

08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e021]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d1000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

You use the USB manufacturer id and product it (the [14e4:4357] ) and do a net search, and you find it is a Broadcom 4322.  The same search returned many page hits on the net with comments/solutions.  What I've been posting here is from one of those links.

Remember:  Google/Yahoo/Bind, etc., are your friend! ;)  It's what most of us use trying to find solutions for people.

Dave ;)Thank you very much Dave!

I actually found an intriguing solution: I simply made my own wireless network. It works fine for me but my household's other computer, though it can detect it like the neighbors' wireless networks, cannot get into it due to the fact that said other computer is a VERY poor quality (and old) Windows laptop that requires a password of 5 OR 10 ASCII characters, which is ridiculous (I like to put in strange characters in my passwords to make them more secure) as my password is not 5 or 10 ASCII characters exactly and thus the other computer cannot use my wireless network... even though my old Acer netbook, which runs on Ubuntu, can use it without issue.

So now all I have to do is figure out how to get my mother (my household's other member) to fix up her laptop so that she can stop making me shuttle my laptop back and forth between the kitchen and my study and start using her beloved Windows again. I do not expect any help on this issue, by the way ;).

---

### Post by anewguy on 2012-02-01
I would imagine that the wireless adapter in an old laptop is probably pretty out of date - it might be only B, not B/G or B/G/N.  This would make it slower when accessing the net.  In addition, it's probably the driver that's responsible for needing 5 or 10 characters.  I doubt there are going to be any work-arounds for that short of changing the router password to be 5 or 10 characters.

Depending on the age of the laptop, the version of Windows it's running, etc., you can decide if you want to spend any more money on it and if you have any money to spend on it (I'm on disability, so I really understand the "I can't just go out and buy something").  If you want, you could check the net for the list of USB wireless adapters supported by Ubuntu and then buy one of those, perhaps off Ebay.  This might allow the password as you like defined.

Dave ;)

---

