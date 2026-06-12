---
title: "[SOLVED] Completely New"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by yoshimexico on 2008-05-24
so i installed ubuntu after having the image on my laptop for quite some time, the final straw was letting my family (sisters and nephews) borrow my pc for a few days,  as expected they returned it full of viruses and all sorts of goodies that brought my pc to slow laggy paper weight.

i'm enjoying the feel of it thus far.

not having enough money for an external hard drive though, i backed up my stuff into a logical partition i think it's called, and so here are my two questions if someone wouldn't mind answering them.

1. when i try to access my partition it says "Unable to Mount Volume 'DATA'", data being the partition. now i'm completely new to linux so i have NO IDEA what's going on -_-  silly me and experimenting =)

2. and i kind of got the answer by browsing the forums, my laptop is running a bit slow and i guess not to it's full capacity, windows xp was much faster as a fresh install, i followed some steps i found in the forums and the performance has improved a bit, anything else i could do so my pc runs as smoothly as possible? 

so, all in all, i really like ubuntu so far, but i do wish i had my stuff (especially my music) and i would love it to run smoother,  i can't see myself keeping it if the performance is below par, i just hope it's something i can fix.

---

### Post by tamoneya on 2008-05-24
please post the output of this command in terminal(applications->accessories->terminal)```
sudo fdisk -l
```Then we will be able to find your data partition and help you mount it.

---

### Post by yoshimexico on 2008-05-24
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9543    76654116   83  Linux
/dev/hda2            9544        9729     1494045    5  Extended
/dev/hda5            9544        9729     1494013+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65dc4bf5

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS
```

like this? :\  i'm pretty sure i didn't need the code tags, but i was just playing it safe.

---

### Post by mali2297 on 2008-05-24
What are the specs of the laptop? (RAM, graphics card et cetera.)
Do you use desktop effects?

---

### Post by tamoneya on 2008-05-24
that is perfect.  It is preferred if you put the code tags around it since it becomes easier to read.  You can get to your data by mounting like this:```
sudo /data
sudo mount -t ntfs /dev/sdb1 /data
```
Then you can browse however you choose to /data and you will see all your stuff.

---

### Post by yoshimexico on 2008-05-24
> **mali2297 said:**
> What are the specs of the laptop? (RAM, graphics card et cetera.)
Do you use desktop effects?

um, i've had it for a while, so specific specs escape me, anyway of just getting those out?



also, thanks i'll try mounting the drive now! with the terminal right?

---

### Post by tamoneya on 2008-05-24
yes that is all in terminal.  To get some specs you could type ```
cat /proc/cpuinfo
cat /proc/meminfo
lspci
```
Those three commands should tell us all we need to know.

---

### Post by yoshimexico on 2008-05-24
okie doke, sorry about that i ran into some common sense problem =P

now, the mounting gives me this =/
```
yoshi@lesley:~$ sudo /data
[sudo] password for yoshi: 
sudo: /data: command not found
yoshi@lesley:~$ sudo mount -t ntfs /dev/sdb1 /data
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

```

and the ones to find out what my laptop has is this

```


processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 36
model name	: AMD Turion(tm) 64 Mobile Technology ML-32
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good pni lahf_lm
bogomips	: 1597.03
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

MemTotal:       510748 kB
MemFree:          5908 kB
Buffers:          7552 kB
Cached:         167028 kB
SwapCached:         16 kB
Active:         298420 kB
Inactive:       113684 kB
SwapTotal:     1494004 kB
SwapFree:      1493920 kB
Dirty:              80 kB
Writeback:           0 kB
AnonPages:      237548 kB
Mapped:          66440 kB
Slab:            23492 kB
SReclaimable:    11980 kB
SUnreclaim:      11512 kB
PageTables:      13396 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1749376 kB
Committed_AS:   576576 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     16576 kB
VmallocChunk: 34359721723 kB

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

also, i put my desktop graphics to none. i think someone asked that.

---

### Post by tamoneya on 2008-05-24
wow that was my mistake not thinking.```
sudo mkdir /data
sudo mount -t ntfs /dev/hdb1 /data
```

---

### Post by mali2297 on 2008-05-24
> **yoshimexico said:**
> 
and the ones to find out what my laptop has is this

```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
.
.
.
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

also, i put my desktop graphics to none. i think someone asked that.

Those specs are almost identical to mine, except for the graphics card. How  does the slow performance manifest itself? (Long time before applications open, windows are slow to move around, or...)

---

### Post by yoshimexico on 2008-05-24
thanks i got my partition to work =D

also, it's slow in the fact that i can't multitask worth crap, i'm running xubuntu now since i read it was a tad more lightweight.

i don't know i mean i'm playing my music and i can't do anything else because it'll skip uncontrollably, and that's just web browsing, i wish to web browse, chat, listen to music, maybe edit some pictures, and thus far it doesn't seem at all possible... so what do you think i should do?

---

### Post by Sinkingships7 on 2008-05-24
> **yoshimexico said:**
> thanks i got my partition to work =D

also, it's slow in the fact that i can't multitask worth crap, i'm running xubuntu now since i read it was a tad more lightweight.

i don't know i mean i'm playing my music and i can't do anything else because it'll skip uncontrollably, and that's just web browsing, i wish to web browse, chat, listen to music, maybe edit some pictures, and thus far it doesn't seem at all possible... so what do you think i should do?

take a dive and use fluxbuntu

---

### Post by yoshimexico on 2008-05-24
hmm, i have no idea about that, how does it differ/where can i get it?

---

### Post by tamoneya on 2008-05-25
fluxbuntu is even more light weight than xubuntu.  You can get it here:
[http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html)

---

### Post by Sinkingships7 on 2008-05-25
you can go [here]("http://releases.fluxbuntu.org/7.10/rc/") and choose the i386 iso.

you should be warned. flux is not as easy to use as metacity (ubuntu).

but it is definitely faster.

---

### Post by yoshimexico on 2008-05-25
hmm nah i'm not going to go deeper into linux, i'm already having a field day working this one haha

right now i'm chatting browsing burning a cd and listening to music flawlessly, i guess i just have to break it in or something... 

still any more tips on getting it to run smoother? my music still skips once in a while

---

### Post by mali2297 on 2008-05-25
Ordinary Ubuntu really should run smoothly on your system. As for the skippy sound, which music player do you use? Have you tried different ones? Are you listening to streaming music from the net or just local files from your hard disk?

---

### Post by Sinkingships7 on 2008-05-25
> **yoshimexico said:**
> hmm nah i'm not going to go deeper into linux, i'm already having a field day working this one haha

right now i'm chatting browsing burning a cd and listening to music flawlessly, i guess i just have to break it in or something... 

still any more tips on getting it to run smoother? my music still skips once in a while

just try to keep your multi-tasking at a minimum. i went back up and looked at your specs. an 800MHz cpu isn't very good, especially for multitasking.

---

### Post by halitech on 2008-05-25
I've got a P3-750 with 192meg of RAM and I can multitask in Xubuntu fine, no issues with listening to music in XMMS and browse the web and chat in AMSN just fine so with his system, it should be fairly smooth due to the fact that he has 512meg of RAM and an overall better system. 

OP - what browser and program are you using to listen to music?

---

### Post by mali2297 on 2008-05-25
> **Sinkingships7 said:**
> just try to keep your multi-tasking at a minimum. i went back up and looked at your specs. an **800MHz** cpu isn't very good, especially for multitasking.

I have the same output. I was somewhat confused about this value at first because I thought I had a better processor than that. Then I found out that the system uses CPU frequency scaling. The potential frequency is really twice as much, but it will not be put in use until it is needed.

---

### Post by yoshimexico on 2008-05-25
i'm using amarok for music and firefox for browsing, and i really like both, it's going pretty well now... so if there really isn't anything else i could do i'm going to consider this case solved =)

---

### Post by Sinkingships7 on 2008-05-25
Well, apps like Amarok and Firefox tend to need quite a bit more power than their smaller, more lightweight counterparts. 

For music, I'd suggest XMMS. For web browsing, I'd recommend Dillo. Obviously, using more lightweight applications means you'll sacrifice some of the luxuries of the heavier apps, with the benefit of speed and usability.

---

