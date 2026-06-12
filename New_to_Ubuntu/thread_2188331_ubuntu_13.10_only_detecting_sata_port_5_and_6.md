---
title: "ubuntu 13.10 only detecting sata port 5 and 6"
date: 2013-11-16
forum: New to Ubuntu
---

### Post by john_k2 on 2013-11-16
[COLOR=#000000][FONT=Verdana][IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/icons_lq/icon7.gif[/IMG] **ubuntu 13.10 only detecting sata port 5 and 6**
[/FONT][/COLOR]
[HR][/HR][COLOR=#000000][FONT=Verdana]Built the followin HTPC:CPU: AMD A8-6500 3.5GHz Quad-Core Processor 
CPU Cooler: Cooler Master GeminII M4 58.4 CFM Sleeve Bearing 
Motherboard: ASRock FM2A75 Pro4-M Micro ATX FM2 
Memory: G.Skill Ripjaws X Series 8GB (2 x 4GB) DDR3-2133 
Storage: Kingston SSDNow V300 Series 60GB 2.5" 
Storage: Seagate Barracuda 1TB 3.5" 7200RPM Internal Hard Drive 
Case: Silverstone ML03B HTPC Case 
Power Supply: Corsair Builder 500W 80 PLUS Bronze Certified ATX12V Power Supply 
[COLOR=DarkGreen]Optical Drive: LG WH14NS40 Blu-Ray/DVD/CD Writer [/COLOR]_missing in ubuntu_
PROBLEM: Motherboard detects all sata ports 1 through 6,BUT ubuntu 13.10 linux 3.12 only detects 5 and 6, which is where my SSD and HDD reside, DVD drive not being detected. So I can boot up, but can't watch DVD or play CDs yet Anybody have ideas on what I'm missing?
~$ sudo lshw -C disk yields:
[sudo] password for john: 
*-disk 
description: ATA Disk
product: ST1000DM003-1CH1
vendor: Seagate
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: CC47
serial: S1DEKVS2
size: 931GiB (1TB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 sectorsize=4096 signature=0001d628
*-disk
description: ATA Disk
product: KINGSTON SV300S3
physical id: 0.0.0
bus info: scsi@1:0.0.0
logical name: /dev/sdb
version: 505A
serial: 50026B72380285BB
size: 55GiB (60GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 sectorsize=512 signature=000754c4

Any help greatly appreciated! Thanks


[/FONT][/COLOR]

---

### Post by smuggly on 2014-01-19
Go into the bios ( Hit Delete during post) look for storage/sata config. Enable AHCI on all but the last 2 or 3 sata ports tose make as sata type. Reboot & reinstall . That should do it.
also if booting from a usb image boot from non uefi.
I had that exact board it will work good with linux.

---

### Post by Mark Phelps on 2014-01-19
Be careful with switching SATA ports from IDE to AHCI.  When I did that, I could no longer boot from the DVD drive; it had to remain IDE to be bootable.  AHCI works fine with hard drives, not so much with DVD drives.

---

