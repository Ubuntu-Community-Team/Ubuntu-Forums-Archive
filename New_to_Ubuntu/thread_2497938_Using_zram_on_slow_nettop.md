---
title: "Using zram on slow nettop"
date: 2024-05-23
forum: New to Ubuntu
---

### Post by alex7376363 on 2024-05-23
Hello everyone,

I have a question regarding the use of zram on my nettop, and I hope you can provide some insights.My device is an ASUS L210ma with the following specifications:Intel Celeron N4020 1.1 GHz4 GB RAM, DDR4256 GB SSDI'm considering using zram to improve performance, but I'm concerned that it might consume a significant amount of CPU resources given the limited processing power of the Celeron N4020.

Is it worthwhile to use zram in this setup, or should I avoid it to preserve CPU performance?

Thank you for your help!

---

### Post by #&amp;thj^% on 2024-05-23
That's something only you can decide, I use it off and on depending on what I'm doing and mostly just testing.
```
cat /proc/swaps
Filename				Type		Size		Used	Priority
/dev/zram0                              partition	8110812		0	5

```
It's easy enough to flip between the both to see if it helps you.

---

### Post by alex7376363 on 2024-05-23
Sorry, I confused zram with zswap. So, is zswap is good idea to enable on this nettop?

size: 232.89 GiB speed: 31.6 Gb/s lanes: 4 tech: SSD
serial: <filter> fw-rev: S5Z42109 temp: 23.9 C scheme: GPT
ID-3: /dev/sda vendor: Kingston model: DT microDuo 3.0
size: 14.44 GiB type: USB rev: 3.0 spd: 5 Gb/s lanes: 1 tech: N/A
serial: <filter> fw-rev: PMAP scheme: MBR
Partition:
ID-1: / size: 1.84 GiB used: 42.7 MiB (2.3%) fs: overlay
source: ERR-102
ID-2: /cdrom raw-size: 3.07 GiB size: <superuser required>
used: <superuser required> fs: N/A dev: /dev/dm-0 mapped: ventoy
Swap:
ID-1: swap-1 type: zram size: 1.84 GiB used: 0 KiB (0.0%)
priority: 5 dev: /dev/zram0
Sensors:
System Temperatures: cpu: 42.0 C mobo: N/A
Fan Speeds (rpm): cpu: 0
Repos:
Packages: 1976 pm: dpkg pkgs: 1968 pm: snap pkgs: 8
Active apt repos in: /etc/apt/sources.list
1: deb cdrom:[Lubuntu 24.04 LTS _Noble Numbat_ - Release amd64
(20240425.1)]/ noble main multiverse restricted universe
2: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) noble main restricted
universe multiverse
3: deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) noble-security main
restricted universe multiverse
4: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) noble-updates main
restricted universe multiverse
Info:
Processes: 187 Power: uptime: 1m states: freeze,mem,disk
suspend: deep wakeups: 0 hibernate: platform Init: systemd v: 255
default: graphical
Compilers: N/A Shell: Bash v: 5.2.21 running-in: qterminal
inxi: 3.3.34

---

### Post by #&amp;thj^% on 2024-05-23
Again it's a choice you have to decide, here is a .25 cent rundown.
Summary of their implementations:
[list]
    [*]ZRAM is a compressed RAM based block device (that can be used for swap)
    [*]ZSWAP is a compressed Cache if you already have a swap.
    [*]ZCache is a backend for a special type of Virtual RAM thingy (Transcendent memory) that can be used to cache filesystem pages or swap data.[/list]
I prefer zram with my ZFS-root:
```
zramctl
NAME       ALGORITHM DISKSIZE DATA COMPR TOTAL STREAMS MOUNTPOINT
/dev/zram0 lzo-rle       7.7G   4K   74B   12K      12 [SWAP]

```
Details:
[list]
    [*]ZRAM: Makes a block device in the RAM. When a block is written, the block will be compressed. When used as a swap device, zram has a higher priority than other swap devices: pages that are swapped out are preferentially sent to the zram device till it is full, only then are any other swap devices used.
       [*] Benefits: Independent of other (physical) swap devices. It can be used when there is no swap partition to expand the available memory.
        [*]Disadvantages: If other swap devices (HDD/SSD) are present they are not used optimally. As the zram device is an independent swap device, once it is full, any new pages that need to be swapped out are sent to next swap device directly.[/list]

But wait there's more, pages and pages to read about on the web.

---

