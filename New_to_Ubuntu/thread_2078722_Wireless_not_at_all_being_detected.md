---
title: "Wireless not at all being detected"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by 7Starphy on 2012-10-31
Hello :)

 I am using Ubuntu 12.04 for the first time , everything is working fine ,just that there is no sign of the word 'wireless' in the Network settings in system settings . I dual boot Ubuntu with Windows 7 ,wireless is working fine there . I tried many command line prompts from many threads suggestion ,but couldnt get a convincing solution . Can anyone please help me out ? I dont know how to proceed about ... :(

---

### Post by squakie on 2012-10-31
Post back the output of  lspci.  If your wireless adapter is USB then post back the output of lsusb.

---

### Post by 7Starphy on 2012-10-31
Hello thanks for your quick reply :) . I tried lspci -v and this was my following output
```


00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0000000-c0ffffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at c1000000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Dell Device 056a
	Flags: bus master, medium devsel, latency 0, IRQ 42
	Memory at c1600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at c1614000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Dell Device 056a
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at c1619000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at c1610000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Prefetchable memory behind bridge: 00000000c1400000-00000000c14fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: c1500000-c15fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Dell Device 056a
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at c1618000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
	Subsystem: Dell Device 056a
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 056a
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at 4088 [size=8]
	I/O ports at 4094 [size=4]
	I/O ports at 4080 [size=8]
	I/O ports at 4090 [size=4]
	I/O ports at 4060 [size=32]
	Memory at c1617000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
	Subsystem: Dell Device 056a
	Flags: medium devsel, IRQ 10
	Memory at c1615000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4040 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0000000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at c0020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
	Subsystem: Dell Device 056a
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at 2000 [size=256]
	Memory at c1404000 (64-bit, prefetchable) [size=4K]
	Memory at c1400000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

08:00.0 Network controller: Broadcom Corporation Device 4365 (rev 01)
	Subsystem: Dell Device 0016
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at c1500000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>

```

---

### Post by 7Starphy on 2012-10-31
Sorry for the impatience ,I am very excited about getting started with ubuntu ..so anyone please help to the above output

---

### Post by Hadaka on 2012-10-31
Hi, please post the output of..

```
rfkill list all 
``````
lspci -nnk | grep i-A3 net 
```thanks.

---

### Post by 7Starphy on 2012-10-31
Thanks for the reply :)

Reply for rfkill list all
```


0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no



```

And for the following code
```

lspci -nnk | grep i-A3 net 
```

I got a reply telling no such file or directory exists :(

---

### Post by Hadaka on 2012-10-31
Hi, please try again and..

```
lspci -nnk | grep -iA3 net 
``````
lspci -nn | grep 0280 
```copy and paste one command at a time into your terminal.

thanks

* first post  grep command was a typo...sorry.

---

### Post by 7Starphy on 2012-10-31
Ok no probs :)

This is the output for ```
 lspci -nnk | grep -iA3 net 
```

```


lspci -nnk | grep -iA3 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:056a]
	Kernel driver in use: r8169
	Kernel modules: r8169
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
	Subsystem: Dell Device [1028:0016]

```

And the output for ```
lspci -nn | grep 0280 
```

is 

```


08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)

```

---

### Post by Hadaka on 2012-10-31
Hi, im guessing you have the Dell vostro

Your card BCM4365 is not a common broadcom card and i am
not finding any easy fixes for it on extensive searches. There are
only about 3 different drivers for broadcom, so you could try one
at a time and possibly find a fix, or i would suggest you ask a mod
to move this thread to Networking/Wireless and slap a "Help Chilli555"
note on it. If anyone can find a fix for this it would be him. Or...if you have time
and feel like experimenting... I can possibly guide you on the
install of each driver and get it working for you.

---

### Post by 7Starphy on 2012-10-31
I am having a Dell INSPIRON 15R...I have all the time in the world :D 

Please tell me how to fix this :)

---

### Post by chili555 on 2012-10-31
> **7Starphy said:**
> I am having a Dell INSPIRON 15R...I have all the time in the world :D 

Please tell me how to fix this :)Since your card may or may not be a Broadcom, previously discussed in this thread, please start your own new thread and include, from a terminal:```
lspci -nn | grep 0280
```Please post it over in Networking and Wireless. I'll be happy to help.

---

### Post by Hadaka on 2012-10-31
Hi, ok..first, since you just loaded 12.04
please run...

```
sudo apt-get update 
```

you will be asked for a password, when you type it in
it is not echo'd.

then, make a sandwich and relax...it takes some time to load, we want to
make sure you have all the latest patches and needed data to your os.
Then, we will take a look in additional drivers and hope your needed driver
is there.

thanks

---

### Post by 7Starphy on 2012-10-31
I already did the update stuffs ,downloaded Ubuntu Restricted Xtras ,so that I get to play mp3 and videos . So the problem is that I dont know packages I have missed out :( 

And I have started a new thread in the appropriate forum as asked by Chili555 and hadaka .

Thanks for the help so far friends :)

---

