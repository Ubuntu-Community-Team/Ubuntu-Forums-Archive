---
title: "Lost sound after updates?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Wartooth on 2008-06-23
I have looked through other threads and have yet to find a solution to this problem.  My computer was shut down for about a week and a half and I got it back up and running this weekend.  At some point, I realized that I had no sound, and then later recalled that a LOT of updates, including a kernel update, had been installed once I had started up my computer again.  

I'd tried removing the sound card and seeing if the onboard sound would work, but it never, ever has.  I reinserted the sound card into another slot on the motherboard, just for the heck of it, no change.  I put the sound card back into its original location, still no sound.  

All my hardware specs are in my signature. 

I have tried selecting earlier kernel versions w/GRUB to no avail.  The various sound level devices have not been muted as far as I can tell. 

alsamixer gives me this:

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: CA0106                                                                 &#9474;
&#9474; Chip:                                                                        &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: IEC958                                                                 &#9474;
&#9474;                                                                              &#9474;
&#9474;             &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     >
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;                                           &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;                                           &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;            10<>10    10<>10   10<>10   10<>10    15<>15   10<>10   10<>10    &#9474;
&#9474; < IEC958 >IEC958 C  IEC958 F IEC958 R IEC958 U  Analog C Analog F Analog R   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```
And continuing to the right:

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: CA0106                                                                 &#9474;
&#9474; Chip:                                                                        &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: CAPTURE feedback [dB gain=-45.50, -45.50]                              &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
<    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
<    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
<    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
<    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
<    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
<    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;                                &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;
&#9474;                                &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9474;
&#9474;   10<>10   10<>10    10<>10   15<>15   10<>10    10<>10   10<>10   10<>10    &#9474;
&#9474;  IEC958 F IEC958 R  IEC958 U Analog C Analog F  Analog R Analog S<CAPTURE >  &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

Adjusting the bars up and down has also produced no results. 


After trying some of the things suggested in this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I have gotten the following outputs:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` 

That doesn't look very promising since I don't see anything about a Creative SoundBlaster card anywhere.  Or anything I even remotely recognize, but I'm far from experienced at this sort of thing. 

```
lspci -v
03:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at bc00 [size=32]
        Capabilities: <access denied>

```

That at least gives me something, but <access denied> doesn't look like a good thing, either. 

I get to step three and that's where I hit the wall. > (3) Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text).

That link only goes to a directory, and clicking the one folder in there takes me to somewhere that doesn't seem particularly helpful to the lost and confused like myself.  

I'm really, really stuck and am one of those who needs detailed instructions, unfortunately.  I've done as much as I think I can do, in hopes of avoiding making the problem worse.

:(  Help.

---

### Post by slibuntu on 2008-06-23
Did your update work perfectly? Mine fecked up somehow and I had no sound or Wifi until I finished the update fully, it was the .19 kernel update

---

### Post by iaculallad on 2008-06-23
Reinstall the linux-generic to get your sound working:

```
sudo aptitude install linux-generic
```

---

### Post by Wartooth on 2008-06-23
> **slibuntu said:**
> Did your update work perfectly? Mine fecked up somehow and I had no sound or Wifi until I finished the update fully, it was the .19 kernel update

Yes, everything appeared to go well.  I let it do all of the updating while I went and made breakfast, came back and it was fine and happy, or so it seemed.

> **iaculallad said:**
> Reinstall the linux-generic to get your sound working:

```
sudo aptitude install linux-generic
```


Had forgotten to mention that I saw that in one of the threads I read, and I had already done it.  Just confirmed it now:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

Thank you for the suggestions, though.

---

### Post by Wartooth on 2008-06-24
Ran across a thread addressing the same or similar problem, said to check the output of lshw -C sound
```
WARNING: you should run this program as super-user.
  *-multimedia
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=CA0106 latency=32 maxlatency=20 mingnt=2 module=snd_ca0106

```

Is what I got. 

Installing linux-generic was suggested there as well.  Seemed to work for one person, but not the other, like me.

---

### Post by Wartooth on 2008-06-24
Following the lead of this thread: [http://ubuntuforums.org/showthread.php?t=839537](http://ubuntuforums.org/showthread.php?t=839537)

>  sudo alsaconf
sudo: alsaconf: command not found


> sudo apt-get install alsa-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
alsa-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Hrm. 

And another command I saw elsewhere...

```
soundconf list
Names of available sound cards:
CA0106

```

Should it be called that or should it somehow reflect something more specific about the card?

Is there a way I can uninstall my soundcard and reinstall it?  Would that have any chance at all at bringing sound capabilities back?

---

### Post by Wartooth on 2008-06-24
Going to keep posting outputs of various things in hope that it can help someone help me or point me in the right direction.  I hate being annoying and pathetic about this, but I'm still searching and still have no solutions.

```

lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
03:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
evlgt85@Wartooth:~$ dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c000 (usable)
[    0.000000]  BIOS-e820: 000000000009c000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fef0000 (usable)
[    0.000000]  BIOS-e820: 000000005fef0000 - 000000005fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fef3000 - 000000005ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 638MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3ab0
[    0.000000] Entering add_active_range(0, 0, 392944) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   392944
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   392944
[    0.000000] On node 0 totalpages: 392944
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1277 pages used for memmap
[    0.000000]   HighMem zone: 162291 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7BF0 checksum 0
[    0.000000] ACPI: RSDP 000F7BF0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 5FEF3040, 0038 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 5FEF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 5FEF3180, 617C (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FEF0000, 0040
[    0.000000] ACPI: SSDT 5FEF9400, 00F7 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: SRAT 5FEF9540, 0090 (r1 AMD    HAMMER          1 AMD         1)
[    0.000000] ACPI: MCFG 5FEF9640, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 5FEF9340, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5ff00000:80100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389875
[    0.000000] Kernel command line: root=UUID=4a3fdd64-eb4a-4351-95ec-f5e16e80c88f ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1004.615 MHz processor.
[   27.755967] spurious 8259A interrupt: IRQ7.
[   27.758252] Console: colour VGA+ 80x25
[   27.758257] console [tty0] enabled
[   27.758922] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.759635] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.857581] Memory: 1545404k/1571776k available (2157k kernel code, 25176k reserved, 998k data, 364k init, 654272k highmem)
[   27.857595] virtual kernel memory layout:
[   27.857597]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   27.857600]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.857602]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.857604]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.857606]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   27.857609]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   27.857611]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   27.857616] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.857675] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.937682] Calibrating delay using timer specific routine.. 2011.33 BogoMIPS (lpj=4022663)
[   27.937724] Security Framework initialized
[   27.937734] SELinux:  Disabled at boot.
[   27.937759] AppArmor: AppArmor initialized
[   27.937765] Failure registering capabilities with primary security module.
[   27.937779] Mount-cache hash table entries: 512
[   27.937965] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[   27.937980] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.937985] CPU: L2 Cache: 512K (64 bytes/line)
[   27.937989] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[   27.938007] Compat vDSO mapped to ffffe000.
[   27.938024] Checking 'hlt' instruction... OK.
[   27.954128] SMP alternatives: switching to UP code
[   27.955952] Freeing SMP alternatives: 11k freed
[   27.956137] Early unpacking initramfs... done
[   28.610036] ACPI: Core revision 20070126
[   28.610144] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.616960] CPU0: AMD Athlon(tm) 64 Processor 3400+ stepping 02
[   28.616992] Total of 1 processors activated (2011.33 BogoMIPS).
[   28.617303] ENABLING IO-APIC IRQs
[   28.617555] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   28.761530] Brought up 1 CPUs
[   28.761590] CPU0 attaching sched-domain:
[   28.761594]  domain 0: span 01
[   28.761597]   groups: 01
[   28.761840] net_namespace: 64 bytes
[   28.761848] Booting paravirtualized kernel on bare hardware
[   28.762628] Time: 19:27:13  Date: 06/24/08
[   28.762663] NET: Registered protocol family 16
[   28.762926] EISA bus registered
[   28.762957] ACPI: bus type pci registered
[   28.769906] PCI: PCI BIOS revision 3.00 entry at 0xfa7c0, last bus=3
[   28.769910] PCI: Using configuration type 1
[   28.769913] Setting up standard PCI resources
[   28.775129] ACPI: EC: Look up EC in DSDT
[   28.786313] ACPI: Interpreter enabled
[   28.786317] ACPI: (supports S0 S1 S4 S5)
[   28.786338] ACPI: Using IOAPIC for interrupt routing
[   28.803923] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.805194] PCI: Transparent bridge - 0000:00:10.0
[   28.805220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.805710] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   28.970797] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.971140] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.971478] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[   28.971812] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.972148] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 *10 11 14 15)
[   28.972482] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.972816] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.973151] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.973493] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   28.973827] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.974164] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[   28.974499] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.974834] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.975175] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   28.975510] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.975848] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   28.976191] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   28.976532] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   28.976870] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   28.977268] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   28.977660] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   28.978043] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   28.978423] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   28.978805] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   28.979191] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   28.979572] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   28.979954] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   28.980336] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   28.980720] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   28.981109] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   28.981496] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   28.981880] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[   28.982263] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   28.982646] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   28.983034] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   28.983417] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   28.983799] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   28.984183] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   28.984567] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   28.984791] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.984834] pnp: PnP ACPI init
[   28.984845] ACPI: bus type pnp registered
[   28.994813] pnpacpi: exceeded the max number of mem resources: 12
[   28.994924] pnp: PnP ACPI: found 13 devices
[   28.994928] ACPI: ACPI bus type pnp unregistered
[   28.994933] PnPBIOS: Disabled by ACPI PNP
[   28.995241] PCI: Using ACPI for IRQ routing
[   28.995248] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.093390] NET: Registered protocol family 8
[   29.093394] NET: Registered protocol family 20
[   29.093488] AppArmor: AppArmor Filesystem Enabled
[   29.097378] Time: tsc clocksource has been installed.
[   29.105427] system 00:01: ioport range 0x1000-0x107f has been reserved
[   29.105432] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   29.105437] system 00:01: ioport range 0x1400-0x147f has been reserved
[   29.105442] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   29.105446] system 00:01: ioport range 0x1800-0x187f has been reserved
[   29.105451] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   29.105456] system 00:01: ioport range 0x2000-0x207f has been reserved
[   29.105461] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   29.105467] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[   29.105472] system 00:01: iomem range 0x0-0x0 could not be reserved
[   29.105483] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   29.105488] system 00:02: ioport range 0x800-0x87f has been reserved
[   29.105493] system 00:02: ioport range 0x290-0x29f has been reserved
[   29.105497] system 00:02: ioport range 0x290-0x297 has been reserved
[   29.105512] system 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   29.105518] system 00:0b: iomem range 0xbf00000-0xbffffff could not be reserved
[   29.105523] system 00:0b: iomem range 0x1bf00000-0x1bffffff could not be reserved
[   29.105529] system 00:0b: iomem range 0x2bf00000-0x2bffffff could not be reserved
[   29.105534] system 00:0b: iomem range 0x3bf00000-0x3bffffff could not be reserved
[   29.105539] system 00:0b: iomem range 0x4bf00000-0x4bffffff could not be reserved
[   29.105544] system 00:0b: iomem range 0x5bf00000-0x5bffffff could not be reserved
[   29.105550] system 00:0b: iomem range 0x6bf00000-0x6bffffff has been reserved
[   29.105555] system 00:0b: iomem range 0x7bf00000-0x7bffffff has been reserved
[   29.105564] system 00:0c: iomem range 0xce200-0xcffff has been reserved
[   29.105569] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   29.105574] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   29.105579] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   29.105584] system 00:0c: iomem range 0x5fef0000-0x5fefffff could not be reserved
[   29.105590] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[   29.105595] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   29.105600] system 00:0c: iomem range 0x100000-0x5feeffff could not be reserved
[   29.105605] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   29.105610] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   29.105615] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
[   29.105621] system 00:0c: iomem range 0xfefff000-0xfeffffff could not be reserved
[   29.136182] PCI: Bridge: 0000:00:03.0
[   29.136186]   IO window: a000-afff
[   29.136191]   MEM window: fdb00000-fdbfffff
[   29.136196]   PREFETCH window: fde00000-fdefffff
[   29.136203] PCI: Bridge: 0000:00:04.0
[   29.136206]   IO window: c000-cfff
[   29.136211]   MEM window: fa000000-fcffffff
[   29.136215]   PREFETCH window: d0000000-dfffffff
[   29.136219] PCI: Bridge: 0000:00:10.0
[   29.136223]   IO window: b000-bfff
[   29.136228]   MEM window: fdd00000-fddfffff
[   29.136232]   PREFETCH window: fdc00000-fdcfffff
[   29.136252] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   29.136264] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   29.136275] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   29.136292] NET: Registered protocol family 2
[   29.173475] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.173970] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   29.175332] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   29.176066] TCP: Hash tables configured (established 131072 bind 65536)
[   29.176070] TCP reno registered
[   29.185556] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   29.789485]  it is
[   30.446093] Freeing initrd memory: 7970k freed
[   30.446934] audit: initializing netlink socket (disabled)
[   30.446951] audit(1214335634.488:1): initialized
[   30.447163] highmem bounce pool size: 64 pages
[   30.449852] VFS: Disk quotas dquot_6.5.1
[   30.449956] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.450158] io scheduler noop registered
[   30.450162] io scheduler anticipatory registered
[   30.450166] io scheduler deadline registered
[   30.450182] io scheduler cfq registered (default)
[   38.462092] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   38.462112] Boot video device is 0000:02:00.0
[   38.462260] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   38.462296] assign_interrupt_mode Found MSI capability
[   38.462326] Allocate Port Service[0000:00:03.0:pcie00]
[   38.462415] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   38.462449] assign_interrupt_mode Found MSI capability
[   38.462474] Allocate Port Service[0000:00:04.0:pcie00]
[   38.462764] isapnp: Scanning for PnP cards...
[   38.816025] isapnp: No Plug & Play device found
[   38.858743] Real Time Clock Driver v1.12ac
[   38.858894] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.859049] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.859863] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.860950] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.861054] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   38.861180] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   38.861185] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   38.861629] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.866175] mice: PS/2 mouse device common for all mice
[   38.866337] EISA: Probing bus 0 at eisa.0
[   38.866345] Cannot allocate resource for EISA slot 1
[   38.866350] Cannot allocate resource for EISA slot 2
[   38.866376] EISA: Detected 0 cards.
[   38.866380] cpuidle: using governor ladder
[   38.866383] cpuidle: using governor menu
[   38.866511] NET: Registered protocol family 1
[   38.866545] Using IPI No-Shortcut mode
[   38.866585] registered taskstats version 1
[   38.866754]   Magic number: 12:744:496
[   38.866990] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   38.866993] EDD information not available.
[   38.867317] Freeing unused kernel memory: 364k freed
[   38.901952] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   40.318455] fuse init (API version 7.9)
[   40.345888] ACPI: Fan [FAN] (on)
[   40.355071] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   40.357539] ACPI: Thermal Zone [THRM] (40 C)
[   42.428808] usbcore: registered new interface driver usbfs
[   42.428841] usbcore: registered new interface driver hub
[   42.439757] usbcore: registered new device driver usb
[   42.473023] SCSI subsystem initialized
[   42.564713] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   42.565397] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   42.565411] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   42.565430] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   42.565435] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   42.565747] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   42.565770] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
[   42.616663] libata version 3.00 loaded.
[   42.622832] usb usb1: configuration #1 chosen from 1 choice
[   42.622872] hub 1-0:1.0: USB hub found
[   42.622884] hub 1-0:1.0: 8 ports detected
[   42.724969] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   42.725609] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   42.725622] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 17
[   42.725633] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   42.824477] FDC 0 is a post-1991 82077
[   43.028570] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   43.241604] usb 1-3: configuration #1 chosen from 1 choice
[   43.245011] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:e0:4d:11:05:16
[   43.245019] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   43.245206] hub 1-3:1.0: USB hub found
[   43.245875] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[   43.245888] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 18
[   43.245904] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   43.245909] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   43.245949] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   43.245988] ehci_hcd 0000:00:0b.1: debug port 1
[   43.245994] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   43.246010] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xfe02e000
[   43.253472] hub 1-3:1.0: config failed, can't read hub descriptor (err -22)
[   43.253615] usb 1-3: USB disconnect, address 2
[   43.256475] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   43.256636] usb usb2: configuration #1 chosen from 1 choice
[   43.256671] hub 2-0:1.0: USB hub found
[   43.256680] hub 2-0:1.0: 8 ports detected
[   43.360684] sata_nv 0000:00:0e.0: version 3.5
[   43.361318] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   43.361332] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
[   43.361394] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   43.363262] scsi0 : sata_nv
[   43.364684] scsi1 : sata_nv
[   43.364974] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 19
[   43.364980] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 19
[   43.676308] ata1: SATA link down (SStatus 0 SControl 300)
[   43.928201] usb 1-3: new full speed USB device using ohci_hcd and address 3
[   43.996176] ata2: SATA link down (SStatus 0 SControl 300)
[   44.012409] pata_amd 0000:00:0d.0: version 0.3.10
[   44.012487] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   44.013772] scsi2 : pata_amd
[   44.015136] scsi3 : pata_amd
[   44.016366] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[   44.016371] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[   44.140296] usb 1-3: configuration #1 chosen from 1 choice
[   44.143230] hub 1-3:1.0: USB hub found
[   44.146181] hub 1-3:1.0: 4 ports detected
[   44.201713] ata3.00: ATA-8: WDC WD5000AAJB-00YRA0, 12.01C02, max UDMA/100
[   44.201720] ata3.00: 976773168 sectors, multi 16: LBA48
[   44.202677] ata3.01: ATA-5: WDC WD400BB-00DEA0, 05.03E05, max UDMA/100
[   44.202682] ata3.01: 78165360 sectors, multi 16: LBA
[   44.217361] ata3.00: configured for UDMA/100
[   44.233232] ata3.01: configured for UDMA/100
[   44.481055] usb 1-3.1: new full speed USB device using ohci_hcd and address 4
[   44.552384] ata4.00: ATAPI: TDK DVDRW0404N, 1.0C, max UDMA/33
[   44.592152] usb 1-3.1: configuration #1 chosen from 1 choice
[   44.595093] hub 1-3.1:1.0: USB hub found
[   44.598976] hub 1-3.1:1.0: 4 ports detected
[   44.724230] ata4.00: configured for UDMA/33
[   44.724376] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAJB-0 12.0 PQ: 0 ANSI: 5
[   44.724530] scsi 2:0:1:0: Direct-Access     ATA      WDC WD400BB-00DE 05.0 PQ: 0 ANSI: 5
[   44.727859] scsi 3:0:0:0: CD-ROM            TDK      DVDRW0404N       1.0C PQ: 0 ANSI: 5
[   44.759557] Driver 'sd' needs updating - please use bus_type methods
[   44.759667] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   44.759686] sd 2:0:0:0: [sda] Write Protect is off
[   44.759690] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.759714] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.759778] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   44.759791] sd 2:0:0:0: [sda] Write Protect is off
[   44.759795] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.759817] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.759822]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   44.791500]  sda5 >
[   44.791638] sd 2:0:0:0: [sda] Attached SCSI disk
[   44.791725] sd 2:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   44.791743] sd 2:0:1:0: [sdb] Write Protect is off
[   44.791748] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   44.791772] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.791833] sd 2:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   44.791847] sd 2:0:1:0: [sdb] Write Protect is off
[   44.791851] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   44.791873] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.791879]  sdb: sdb1 sdb2 < sdb5 >
[   44.825082] sd 2:0:1:0: [sdb] Attached SCSI disk
[   44.840633] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   44.840641] Uniform CD-ROM driver Revision: 3.20
[   44.840703] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   44.840800] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   44.840827] sd 2:0:1:0: Attached scsi generic sg1 type 0
[   44.840851] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   44.944909] usb 1-3.2: new low speed USB device using ohci_hcd and address 5
[   45.063996] usb 1-3.2: configuration #1 chosen from 1 choice
[   45.276795] usb 1-3.3: new low speed USB device using ohci_hcd and address 6
[   45.377532] Attempting manual resume
[   45.377538] swsusp: Resume From Partition 8:5
[   45.377541] PM: Checking swsusp image.
[   45.377780] PM: Resume from disk failed.
[   45.392908] usb 1-3.3: configuration #1 chosen from 1 choice
[   45.446824] kjournald starting.  Commit interval 5 seconds
[   45.446845] EXT3-fs: mounted filesystem with ordered data mode.
[   45.620681] usb 1-3.1.1: new low speed USB device using ohci_hcd and address 7
[   45.733771] usb 1-3.1.1: configuration #1 chosen from 1 choice
[   45.952567] usb 1-3.1.4: new full speed USB device using ohci_hcd and address 8
[   46.072668] usb 1-3.1.4: configuration #1 chosen from 1 choice
[   46.076543] usbcore: registered new interface driver hiddev
[   46.085783] input: Fellowes Inc. Fellowes 5 Button as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3.2/1-3.2:1.0/input/input2
[   46.095492] input,hidraw0: USB HID v1.00 Mouse [Fellowes Inc. Fellowes 5 Button] on usb-0000:00:0b.0-3.2
[   46.108622] input: No brand SP02-A1 as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3.3/1-3.3:1.0/input/input3
[   46.119480] input,hidraw1: USB HID v1.10 Keyboard [No brand SP02-A1] on usb-0000:00:0b.0-3.3
[   46.124719] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint
[   46.129792] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3.1/1-3.1.1/1-3.1.1:1.0/input/input4
[   46.143511] input,hidraw2: USB HID v1.10 Keyboard [Logitech Logitech Gaming Keyboard] on usb-0000:00:0b.0-3.1.1
[   46.155590] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3.1/1-3.1.1/1-3.1.1:1.1/input/input5
[   46.167497] input,hiddev96,hidraw3: USB HID v1.10 Device [Logitech Logitech Gaming Keyboard] on usb-0000:00:0b.0-3.1.1
[   46.177610] input: G15 Keyboard G15 Keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3.1/1-3.1.4/1-3.1.4:1.0/input/input6
[   46.187513] input,hiddev97,hidraw4: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:0b.0-3.1.4
[   46.187540] usbcore: registered new interface driver usbhid
[   46.187547] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   52.933135] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   53.001185] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.561107] input: Power Button (FF) as /devices/virtual/input/input7
[   53.572868] ACPI: Power Button (FF) [PWRF]
[   53.573026] input: Power Button (CM) as /devices/virtual/input/input8
[   53.588841] ACPI: Power Button (CM) [PWRB]
[   53.588938] input: Sleep Button (CM) as /devices/virtual/input/input9
[   53.600859] ACPI: Sleep Button (CM) [SLPB]
[   54.128858] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   54.128904] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   54.173841] usb 1-3.3: USB disconnect, address 6
[   54.493726] usb 1-3.3: new low speed USB device using ohci_hcd and address 9
[   54.608836] usb 1-3.3: configuration #1 chosen from 1 choice
[   54.628820] input: No brand SP02-A1 as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3.3/1-3.3:1.0/input/input10
[   54.644547] input,hidraw1: USB HID v1.10 Keyboard [No brand SP02-A1] on usb-0000:00:0b.0-3.3
[   54.652798] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint
[   58.791066] Linux agpgart interface v0.102
[   59.806896] input: PC Speaker as /devices/platform/pcspkr/input/input11
[   63.030859] parport_pc 00:09: reported by Plug and Play ACPI
[   63.030918] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   63.257740] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   63.257756] ACPI: PCI Interrupt 0000:03:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[   63.257786] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   67.007837] lp0: using parport0 (interrupt-driven).
[   67.091121] Adding 4361608k swap on /dev/sda5.  Priority:-1 extents:1 across:4361608k
[   67.903952] EXT3 FS on sda1, internal journal
[   68.144765] device-mapper: uevent: version 1.0.3
[   68.144808] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   69.919973] ip_tables: (C) 2000-2006 Netfilter Core Team
[   70.552649] No dock devices found.
[   71.288178] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[   71.288234] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   71.288238] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[   71.288243] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   71.288247] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   32.391051] Marking TSC unstable due to: cpufreq changes.
[   32.392138] Time: acpi_pm clocksource has been installed.
[   32.719534] Clocksource tsc unstable (delta = 392794916 ns)
[   34.384809] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   34.384814] apm: overridden by ACPI.
[   34.596438] ppdev: user-space parallel port driver
[   34.954515] audit(1214335678.995:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5298 profile="/usr/sbin/cupsd" namespace="default"
[   38.029778] Bluetooth: Core ver 2.11
[   38.030640] NET: Registered protocol family 31
[   38.030644] Bluetooth: HCI device and connection manager initialized
[   38.030648] Bluetooth: HCI socket layer initialized
[   38.114403] Bluetooth: L2CAP ver 2.9
[   38.114408] Bluetooth: L2CAP socket layer initialized
[   38.121535] Bluetooth: RFCOMM socket layer initialized
[   38.121551] Bluetooth: RFCOMM TTY layer initialized
[   38.121553] Bluetooth: RFCOMM ver 1.8
[   40.802159] NET: Registered protocol family 17
[   96.700205] NET: Registered protocol family 10
[   96.701459] lo: Disabled Privacy Extensions
[  111.323216] eth0: no IPv6 routers present

```

---

### Post by Wartooth on 2008-06-25
I've now discovered that all flash videos stop playing after a couple of seconds.  This is a mess. :(

---

### Post by Wartooth on 2008-06-25
Continuing my notes...
```
 groups
adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
```

---

### Post by Wartooth on 2008-07-26
STILL NO SOUND. And still no further replies :/

I do have sound when I use the Live CD, so it isn't the sound card. 

I've done this: 
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```


```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

---

### Post by drs305 on 2008-07-26
I have not used kubuntu. This is going back to basics, but do you have the option to go to System, Preferences, Sound? Are they set to ALSA? Can you hear anything when you hit the 'Test' box?  If not, can you hear anything if you change the settings to OSS or any of the other choices?

4 weeks without sound???

---

### Post by Wartooth on 2008-07-26
Hi, thanks for the reply.

Kubuntu's version of System > Preferences > Sound, I think, is System Settings > Sound System > Hardware > Select & Configure your Audio Device. 

From that I have picked the options:

Autodetect
Open Sound System
Advanced Linux Sound Architecture
Enlightened Sound Daemon
Threaded Open Sound System

It says it's restarting the sound system after I hit 'apply' after each one, and then I click the General tab and hit 'Test Sound' and still nothing each time. 

There are options below the Select & Configure, none of which are checked, and I am unsure as to what they really mean or do:

Full duplex
Use custom sampling rate
Override device location
Use other custom options

Yes, it's been a month since I've had sound on this machine.  I've tried pretty much everything that I've come across, have searched loads, and really haven't much of a clue as to what I'm doing, but I've tried my best.  It's really frustrating that I have sound on my Live CD, but not on the newest and latest and greatest updated version.

---

### Post by kavoura on 2008-07-26
I am having the same problem. THis is really bugging me. I am using 64-bit Ubuntu 8.04, and so far Ubuntu has been very good. But if the sound will not work, then I shall have to consider using a different distro.

---

### Post by kavoura on 2008-07-26
UPDATE

I rebooted the PC to a live DVD and still no sound.

But then I rebooted the PC and went into the BIOS settings. Everything seemed okay, and I did not make any changes, but I then booted into Ubuntu and the sound is back. The only thing I did previously was to use the Hibernate feature, and then restart the PC and it returned from hibernation. Maybe that temporarily disabled the sound.

But it works again now. Sometimes just rebooting the PC can fix things, but probably also going into the BIOS and saving, but without having changed anything.

---

### Post by Wartooth on 2008-07-26
Glad to hear your battle with this is over.  Unfortunately, mine is still here. 

I've been in and out of the BIOS several times, making sure onboard sound was disabled, enabling onboard sound, disabling it again, booting from cd, putting it back to HDD, etc.  No luck :(

---

### Post by Eredeath on 2008-07-26
Okay,  i've read all your posts and feel for you...

do you have speakers of some sort plugged into a port? if so maybe unplug them and restart the computer then try plugging them in. 
Or if you have your speakers pluged in the front port move it to the back port. I found that if i have my headphones in the front speaker port after a re-start i can't get my sound to work.

---

### Post by Wartooth on 2008-07-26
Howdy, thanks for the empathy :)  I'm always up for checking the details, just in case.  

The speakers are plugged directly into the sound card's port, and gave me sound when trying out the Live CD earlier.  My front port is disabled, as is the one on the mobo after I disabled the onboard sound.

---

### Post by Eredeath on 2008-07-26
okay I'm not claiming to know very much here, i am quite new to Linux, but like to solve problems. i find it is best to solve computer problems by comparison... looking at someone else's info compared to yours... so her is what i get when i use lspci -v

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8290
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fea78000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

i realize i have a completely different audio controller but your lspci info is missing memory allocation of the device (compared to mine), maybe try searching along those terms of loading it into memory...

Or perhaps trying the sound card in a different i/o port (as my info doesn't contain this) and re-installing the drivers

---

### Post by bjschuma on 2008-07-27
I had a sound problem after upgrading to Intrepid.  I finally managed to fix it today after installing nvidia-glx-177.  

I had the same problem when upgrading to Hardy, but I never found a solution.  It did work after I reinstalled from the Hardy livecd.

---

