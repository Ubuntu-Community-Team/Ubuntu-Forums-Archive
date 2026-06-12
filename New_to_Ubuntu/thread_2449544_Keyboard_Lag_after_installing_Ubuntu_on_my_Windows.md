---
title: "Keyboard Lag after installing Ubuntu on my Windows laptop"
date: 2020-08-28
forum: New to Ubuntu
---

### Post by sand2389 on 2020-08-28
I'm a newcomer to Linux. After installing Ubuntu on my Windows laptop this week, I've noticed a lot of lag when performing simple tasks. For example, when writing this post, I would type out a sentence and nothing would appear until I finished typing.

I get the lag a lot when using browsers (e.g., typing emails in Gmail). I just tried switching from Chrome to Firefox and still get lots of keyboard input lag, as well as playback lag when watching YouTube videos on a Udacity course (it would freeze, and then skip forward). I get some keyboard input lag when I'm typing into the Slack desktop client, but not quite as bad as using the internet browsers. Based on my limited testing, I don't seem to get any keyboard input lag when I'm typing into a simple text editor or into the terminal. 

I didn't have any issue with lag when I was just running Windows. I have tried enabling and disabling TurboBoost (when enabled, my fan runs all the time), but it doesn't seem to improve the lag issue when I have TurboBoost enabled. Also, I followed [this tutorial]("https://itsfoss.com/install-additional-drivers-ubuntu/") to see if I needed to install any additional drivers, but none were listed in the additional drivers tab.

I'm running Ubuntu 20.04.1 LTS on a partition of my HP Pavilion 13-an0031wm laptop

**Here's the output I get when I type lspci:**[INDENT]00:00.0 Host bridge: Intel Corporation Device 3e35 (rev 0b)[/INDENT]
[INDENT]00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake)[/INDENT]
[INDENT]00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0b)[/INDENT]
[INDENT]00:12.0 Signal processing controller: Intel Corporation Cannon Point-LP Thermal Controller (rev 30)[/INDENT]
[INDENT]00:14.0 USB controller: Intel Corporation Cannon Point-LP USB 3.1 xHCI Controller (rev 30)[/INDENT]
[INDENT]00:14.2 RAM memory: Intel Corporation Cannon Point-LP Shared SRAM (rev 30)[/INDENT]
[INDENT]00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP Serial IO I2C Controller #0 (rev 30)[/INDENT]
[INDENT]00:16.0 Communication controller: Intel Corporation Cannon Point-LP MEI Controller #1 (rev 30)[/INDENT]
[INDENT]00:17.0 SATA controller: Intel Corporation Cannon Point-LP SATA Controller [AHCI Mode] (rev 30)[/INDENT]
[INDENT]00:19.0 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP Serial IO I2C Host Controller (rev 30)[/INDENT]
[INDENT]00:1d.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #9 (rev f0)[/INDENT]
[INDENT]00:1d.1 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #10 (rev f0)[/INDENT]
[INDENT]00:1e.0 Communication controller: Intel Corporation Device 9da8 (rev 30)[/INDENT]
[INDENT]00:1e.2 Serial bus controller [0c80]: Intel Corporation Device 9daa (rev 30)[/INDENT]
[INDENT]00:1f.0 ISA bridge: Intel Corporation Cannon Point-LP LPC Controller (rev 30)[/INDENT]
[INDENT]00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 30)[/INDENT]
[INDENT]00:1f.4 SMBus: Intel Corporation Cannon Point-LP SMBus Controller (rev 30)[/INDENT]
[INDENT]00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP SPI Controller (rev 30)[/INDENT]
[INDENT]01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter[/INDENT]

**And here's more info about my hardware from lshw:**

[INDENT]H/W path Device Class Description
========================================================
system HP Pavilion Laptop 13-an0xxx (5FS56
/0 bus 84C5
/0/0 memory 128KiB BIOS
/0/4 processor Intel(R) Core(TM) i3-8145U CPU @ 2.
/0/4/5 memory 128KiB L1 cache
/0/4/6 memory 512KiB L2 cache
/0/4/7 memory 4MiB L3 cache
/0/17 memory 8GiB System Memory
/0/17/0 memory 8GiB Row of chips DDR4 Synchronous
/0/100 bridge Intel Corporation
/0/100/2 display UHD Graphics 620 (Whiskey Lake)
/0/100/4 generic Xeon E3-1200 v5/E3-1500 v5/6th Gen
/0/100/12 generic Cannon Point-LP Thermal Controller
/0/100/14 bus Cannon Point-LP USB 3.1 xHCI Contro
/0/100/14/0 usb1 bus xHCI Host Controller
/0/100/14/0/1 input Dell KB216 Wired Keyboard
/0/100/14/0/2 input 2.4G Receiver
/0/100/14/0/3 multimedia HP Wide Vision HD Camera
/0/100/14/0/a communication Bluetooth Radio
/0/100/14/1 usb2 bus xHCI Host Controller
/0/100/14.2 memory RAM memory
/0/100/15 bus Cannon Point-LP Serial IO I2C Contr
/0/100/16 communication Cannon Point-LP MEI Controller #1
/0/100/17 scsi2 storage Cannon Point-LP SATA Controller [AH
/0/100/17/0.0.0 /dev/sda disk 128GB SAMSUNG MZNLN128
/0/100/17/0.0.0/1 /dev/sda1 volume 259MiB Windows FAT volume
/0/100/17/0.0.0/2 /dev/sda2 volume 15MiB reserved partition
/0/100/17/0.0.0/3 /dev/sda3 volume 96GiB Windows NTFS volume
/0/100/17/0.0.0/4 /dev/sda4 volume 979MiB Windows NTFS volume
/0/100/17/0.0.0/5 /dev/sda5 volume 21GiB EXT4 volume
/0/100/19 bus Cannon Point-LP Serial IO I2C Host
/0/100/1d bridge Cannon Point-LP PCI Express Root Po
/0/100/1d/0 wlo1 network RTL8822BE 802.11a/b/g/n/ac WiFi ada
/0/100/1d.1 bridge Cannon Point-LP PCI Express Root Po
/0/100/1d.1/0 generic RTS522A PCI Express Card Reader
/0/100/1e communication Intel Corporation
/0/100/1e.2 bus Intel Corporation
/0/100/1f bridge Cannon Point-LP LPC Controller
/0/100/1f.3 multimedia Cannon Point-LP High Definition Aud
/0/100/1f.4 bus Cannon Point-LP SMBus Controller
/0/100/1f.5 bus Cannon Point-LP SPI Controller
/0/1 system PnP device PNP0c02
/0/2 system PnP device PNP0c02
/0/3 system PnP device PNP0c02
/0/5 system PnP device PNP0c02
/0/6 generic PnP device HPQ8001
/0/7 generic PnP device SYN3280
/0/8 system PnP device PNP0c02
/0/9 system PnP device PNP0c02
/1 power MM02037
/2 power OEM Define 5[/INDENT]

**Here's what I get when I run free - m**

[INDENT]total    used    free    shared    buff/cache    available
Mem:    7850    1859    3199    470    2791    5232
Swap:    1022    0    1022              [/INDENT]

**and top:**

[INDENT]top - 20:28:13 up 7:54, 1 user, load average: 0.70, 0.76, 0.36
Tasks: 244 total, 1 running, 243 sleeping, 0 stopped, 0 zombie
%Cpu(s): 10.5 us, 2.7 sy, 0.0 ni, 86.5 id, 0.0 wa, 0.0 hi, 0.3 si, 0.0 st
MiB Mem : 7850.4 total, 3120.7 free, 1918.8 used, 2810.8 buff/cache
MiB Swap: 1022.4 total, 1022.4 free, 0.0 used. 5157.8 avail Mem
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
1507 steve 20 0 4635204 260544 104356 S 15.3 3.2 16:52.96 gnome-s+
14687 steve 20 0 4617956 122040 78220 S 13.0 1.5 0:17.70 chrome
1131 steve 20 0 837984 71236 40604 S 5.0 0.9 13:20.52 Xorg
2862 steve 20 0 8976080 235936 97004 S 2.3 2.9 6:53.63 chrome
2509 steve 20 0 885996 310116 144140 S 2.0 3.9 21:34.60 chrome
12391 steve 20 0 4789956 259980 142332 S 2.0 3.2 1:35.00 chrome
14588 steve 20 0 971032 52468 39724 S 1.3 0.7 0:03.44 gnome-t+
12194 root 20 0 0 0 0 I 1.0 0.0 0:13.62 kworker+
1 root 20 0 167732 11740 8512 S 0.3 0.1 0:32.90 systemd
2578 steve 20 0 391912 106688 67420 S 0.3 1.3 7:05.11 chrome
2613 steve 20 0 9018444 315388 117464 S 0.3 3.9 2:09.87 chrome
14202 root 20 0 0 0 0 I 0.3 0.0 0:01.04 kworker+
14329 root 20 0 0 0 0 I 0.3 0.0 0:02.04 kworker+
2 root 20 0 0 0 0 S 0.0 0.0 0:00.04 kthreadd
3 root 0 -20 0 0 0 I 0.0 0.0 0:00.00 rcu_gp
4 root 0 -20 0 0 0 I 0.0 0.0 0:00.00 rcu_par+
6 root 0 -20 0 0 0 I 0.0 0.0 0:00.00 kworker+[/INDENT]

---

### Post by mastablasta on 2020-08-29
what are you running when getting that output? it shows 2GB RAM is used up. by what? GPU?

Also check how much ram is set for the GPU in BIOS setting. lag comes when disk is used instead of ram or when some software acceleration is used instead of hardware GPU acceleration. but these chips are well supported, so PC should be running well. you could also try switching from wayland session to xorg session and see if that helps. wayland came a long way but some things might still not be as polished as the old xorg.

my free -m with just the firefox browser (3 tabs open curently):

```
              total        used        free      shared  buff/cache   available
Mem:           3944        1006        1087          64        1850        2608
Swap:          5721           0        5721


```

---

### Post by sand2389 on 2020-08-29
I don't know what's using all my ram. Here's another shot of free -m. I took this with Chrome (3 tabs open) and the terminal.

```
              total        used        free      shared  buff/cache   available
Mem:           7850        1803        3682         336        2364        5408
Swap:          1022           0        1022

```

I checked the BIOS, and I couldn't see any setting for the GPU. All I saw was 8 GB of Total Memory.

It looks like I wasn't running in Wayland. I've switched to that and it looks like it's using slightly less ram, but I'm still getting keyboard input lag when I type stuff into gmail.

```
 
              total        used        free      shared  buff/cache   available
Mem:           7850        1408        4048         308        2393        5831
Swap:          1022           0        1022

```

---

