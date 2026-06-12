---
title: "Mobile internet doesn't work"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by Carnivorum on 2012-07-01
Bs'd

I made a dual installation on my new laptop, I put on Ubuntu 12.04, and my mobile internet doesn't work. 

He recognizes the device in the network department, but it doesn't connect to the internet.

On my desktop where I also installed U 12.04 it worked immediately.

---

### Post by mapes12 on 2012-07-01
Go to the Terminal ```
sudo lshw -short
``` and post back the output here.

---

### Post by Carnivorum on 2012-07-01
> **mapes12 said:**
> Go to the Terminal ```
sudo lshw -short
``` and post back the output here.

Bs'd

When I type that in the terminal, he says:  "Command not found".

---

### Post by mapes12 on 2012-07-01
```
sudo lshw -C network
```Copy and paste into Terminal

---

### Post by Carnivorum on 2012-07-01
> **mapes12 said:**
> Go to the Terminal ```
sudo lshw -short
``` and post back the output here.

Bs'd

I realized that I misread that L in the beginning for a one.

I did it again, the first code, and got this: 

                system         SATELLITE C660 (PSC1LE-054009H2) 
/0                              bus            PWWHA 
/0/0                            memory         64KiB BIOS 
/0/4                            processor      Intel(R) Core(TM) i3-2350M CPU @ 
/0/4/5                          memory         64KiB L1 cache 
/0/4/6                          memory         512KiB L2 cache 
/0/4/7                          memory         3MiB L3 cache 
/0/4/0.1                        processor      Logical CPU 
/0/4/0.2                        processor      Logical CPU 
/0/4/0.3                        processor      Logical CPU 
/0/4/0.4                        processor      Logical CPU 
/0/4/0.5                        processor      Logical CPU 
/0/4/0.6                        processor      Logical CPU 
/0/4/0.7                        processor      Logical CPU 
/0/4/0.8                        processor      Logical CPU 
/0/4/0.9                        processor      Logical CPU 
/0/4/0.a                        processor      Logical CPU 
/0/4/0.b                        processor      Logical CPU 
/0/4/0.c                        processor      Logical CPU 
/0/4/0.d                        processor      Logical CPU 
/0/4/0.e                        processor      Logical CPU 
/0/4/0.f                        processor      Logical CPU 
/0/4/0.10                       processor      Logical CPU 
/0/e                            memory         4GiB System Memory 
/0/e/0                          memory         4GiB SODIMM DDR3 Synchronous 1333 
/0/e/1                          memory         DIMM [empty] 
/0/e/2                          memory         DIMM [empty] 
/0/e/3                          memory         DIMM [empty] 
/0/1                            processor       
/0/1/0.1                        processor      Logical CPU 
/0/1/0.2                        processor      Logical CPU 
/0/1/0.3                        processor      Logical CPU 
/0/1/0.4                        processor      Logical CPU 
/0/1/0.5                        processor      Logical CPU 
/0/1/0.6                        processor      Logical CPU 
/0/1/0.7                        processor      Logical CPU 
/0/1/0.8                        processor      Logical CPU 
/0/1/0.9                        processor      Logical CPU 
/0/1/0.a                        processor      Logical CPU 
/0/1/0.b                        processor      Logical CPU 
/0/1/0.c                        processor      Logical CPU 
/0/1/0.d                        processor      Logical CPU 
/0/1/0.e                        processor      Logical CPU 
/0/1/0.f                        processor      Logical CPU 
/0/1/0.10                       processor      Logical CPU 
/0/100                          bridge         2nd Generation Core Processor Fam 
/0/100/2                        display        2nd Generation Core Processor Fam 
/0/100/16                       communication  6 Series/C200 Series Chipset Fami 
/0/100/1a                       bus            6 Series/C200 Series Chipset Fami 
/0/100/1b                       multimedia     6 Series/C200 Series Chipset Fami 
/0/100/1c                       bridge         6 Series/C200 Series Chipset Fami 
/0/100/1c/0        eth0         network        RTL8101E/RTL8102E PCI Express Fas 
/0/100/1c.1                     bridge         6 Series/C200 Series Chipset Fami 
/0/100/1c.1/0      wlan0        network        AR9285 Wireless Network Adapter ( 
/0/100/1d                       bus            6 Series/C200 Series Chipset Fami 
/0/100/1f                       bridge         HM65 Express Chipset Family LPC C 
/0/100/1f.2        scsi0        storage        6 Series/C200 Series Chipset Fami 
/0/100/1f.2/0      /dev/sda     disk           500GB Hitachi HTS54755 
/0/100/1f.2/0/1    /dev/sda1    volume         400MiB Windows NTFS volume 
/0/100/1f.2/0/2    /dev/sda2    volume         232GiB Windows NTFS volume 
/0/100/1f.2/0/3    /dev/sda3    volume         116GiB Windows NTFS volume 
/0/100/1f.2/0/4    /dev/sda4    volume         115GiB Extended partition 
/0/100/1f.2/0/4/5  /dev/sda5    volume         112GiB Linux filesystem partition 
/0/100/1f.2/0/4/6  /dev/sda6    volume         4002MiB Linux swap / Solaris part 
/0/100/1f.2/1      /dev/cdrom1  disk           DVDRAM GT51N 
/0/100/1f.2/1/0    /dev/cdrom1  disk            
/0/100/1f.3                     bus            6 Series/C200 Series Chipset Fami 
/0/2               scsi6        storage         
/0/2/0.0.0         /dev/cdrom   disk           SCSI CD-ROM 
/0/2/0.0.0/1                    volume         17KiB Apple partition map 
/0/2/0.0.0/2                    volume         28MiB Apple HFS 
/1                              power          BATT 1 
/2                              power          Battery Name 
/3                              power          To Be Filled By O.E.M. 
eliyahu@eliyahu-SATELLITE-C660:~$

---

