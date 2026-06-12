---
title: "USB Disk Troubles (LACIE)"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by casemilk on 2012-12-29
Hello
 Trying to mount my Lacie hard disk via USB to back up some files. 
 The disk does not appear to be read.. no icon shows up on desktop or "computer". The external hard drive's light is coming on so it seems to be getting power from the computer. 
USB has read iPod and camera.
Lacie has previously been used on a Mac. 
I've googled the problem but nothing I've found so far has helped so I'm looking here. 
Thanks!

---

### Post by Cheesemill on 2012-12-29
Can you plug the drive in, then wait about 10 seconds and type the following commands:
```
dmesg | tail -n 30
sudo fdisk -l
```

Post the results back here (inbetween [noparse]```
 
```[/noparse] tags to make it easier to read).

---

### Post by casemilk on 2012-12-29
```
 casey@nc6120:~$ dmesg | tail -n 30
[   26.671197] serio: Synaptics pass-through port at isa0060/serio4/input0
[   26.710937] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   26.717098] type=1505 audit(1356805666.750:10):  operation="profile_load" pid=840 name="/usr/bin/evince-previewer"
[   26.764701] tg3 0000:02:0e.0: firmware: requesting tigon/tg3_tso5.bin
[   26.767376] type=1505 audit(1356805666.798:11):  operation="profile_load" pid=840 name="/usr/bin/evince-thumbnailer"
[   27.082956] AC'97 0 analog subsections not ready
[   27.088989] yenta_cardbus 0000:02:06.1: ISA IRQ mask 0x0c78, PCI irq 19
[   27.088994] yenta_cardbus 0000:02:06.1: Socket status: 30000006
[   27.088999] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   27.089010] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   27.089014] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x4fff: clean.
[   27.089262] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd03fffff
[   27.089266] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x27ffffff
[   27.168782] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.313706] apm: BIOS not found.
[   27.656037] intel8x0_measure_ac97_clock: measured 55395 usecs (2669 samples)
[   27.656042] intel8x0: clocking to 48000
[   27.840188] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   27.842081] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   27.842853] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   27.843530] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   27.844622] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   27.846512] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   27.847285] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   27.847968] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   27.849074] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   27.850728] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   33.712757] lib80211_crypt: registered algorithm 'WEP'
[   37.456026] eth1: no IPv6 routers present
[ 1769.993443] ipw2200: Firmware error detected.  Restarting.
casey@nc6120:~$ sudo fdisk -l
[sudo] password for casey: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00062bf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

```

---

### Post by Cheesemill on 2012-12-29
It's not being recognised at all.

How is the Lacie powered, is it just via USB or does it use an adapter as well?

If it's just USB then try a different port in your machine as only some USB ports can supply enough power to switch it on properly (usually the ones at the rear of the case work best).

Also do you have a different cable you can check it with to rule out a faulty USB lead.

---

### Post by casemilk on 2012-12-29
The hard drive is powered by USB only. 
 I tried it in all different ports and nothing changed. 
 I have only used this hard drive on a mac with a firewire previously. Unfortunately I have no similar usb cable to try. 
Maybe I should try someone else's computer to see if it can be read.

---

