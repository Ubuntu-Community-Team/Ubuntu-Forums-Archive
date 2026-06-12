---
title: "Problems resuming from standby and sporadic desktop 'crashes'"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by Sebastian_Llabres on 2014-03-18
Hi All,

I decided to make the switch from Windows 7 and performed a completely fresh install wiping out Windows completely.  I was having problems with blue screens but it was giving me no clues as to what the problem was.  In Windows 7 I would sometimes get blue screens at boot (before hitting the desktop) and the machine often would fail to resume correctly from standby requiring a hard reset. 

I seem to be having similar problems with Ubuntu (I've had no failed boots), I understand this points at a hardware problem.   Resuming from standby is sometimes a problem, the desktop, other than background, seems to sometimes refuse to reappear after standby, yet the cursor can be seen and moved.  I've also had the desktop environment "crash" (all icons / menus vanished) on me.  On one occasion when having problems I used the ctrl-alt-f1 command which gave the following output, seemingly repeated (I ended up resetting the machine):

EXT4-fs error (device sda2): ext4_find_entry 1309: inode #4456450

After this I checked this forum and ran the Smart utility, I'm not sure how to copy it's output but it seems to give the all clear (Overall assessment Disk is OK).

I'm very new to Linux so apologies I've missed something.  I checked what I understand are the system logs in /var/logs/dmesg I'm not really sure what I'd be looking for though.

Thanks for any help at all and let me know if I need to provide anything further!!

I've taken the following hardware output:

lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF104 High Definition Audio Controller (rev a1)
03:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
05:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
06:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]

---

### Post by fantab on 2014-03-18
Yep. sounds to me lika Hardware issue. 
Do a 'memtest'... should tell you about RAM condition. Its slow and time consuming, maybe hours.

Best contact authorized hardware service...

---

### Post by Sebastian_Llabres on 2014-03-18
Will give it ago, depressingly I've already had this RAM replaced a few months back due to the original pair failing.   Running memtest was fun the first time :S  ta!

---

### Post by sandyd on 2014-03-18
see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389154](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389154) for the ext4 errors :)

---

### Post by Sebastian_Llabres on 2014-03-19
Ok, ran memtest on the first stick last night and got 5 passes.  Ran it against the second this morning and it "froze" after 10 minutes or so (the plus sign was still blinking on "memtestx86+").  Checked the memory settings on the stick and they read a voltage of 1.36, the bios had it set at 1.50..Changed it to match and started running memtest again, fingers crossed.  Sound like a cause?

Sorry, my post may be veering into more hardware related now..

---

