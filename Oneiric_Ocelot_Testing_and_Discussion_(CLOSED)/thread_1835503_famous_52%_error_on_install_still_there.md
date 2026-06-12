---
title: "famous 52% error on install still there"
date: 2011-08-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sartic on 2011-08-29
It happens when u try to install width alternate cd on system that has already linux (ubuntu installed).
Like always I just use parted boot iso and delete all partition.
Why this problem is still no solved?!

I tried xubuntu and still it has no .... example simple folder sharing. So I put Kubuntu alternate and as suspected halts on 52% during scanning for partion :)

ps: problem is not only in alpha release. I get this error width post LTS stable releases.

---

### Post by effenberg0x0 on 2011-09-01
I have spent more than 10 hours fighting to install Ubuntu. As I was working with two new machines, I obviously thought I had defective hardware. Changed memory modules, changed HDD, got to the point of putting the cases apart and changing motherboards, PSUs, SATA cables, CPU coolers, etc.

Then I got suspicious of BIOS settings. As this are ASUS M4A89GTD Pro motherboards with Phenom II X6 1100T cpus 16GB of RAM, 18 SATA 6.0Gbps disks in hot swap bays, NVIDIA QUadro Cards, etc, there's absolutely anything you can think off in BIOS options. Fiddled with BIOS for hours. No luck.

I had never seen such a bug in many years of IT and linux. By then I had burned 5 versions of Ubuntu, Kibuntu, Xubuntu, etc. Had 6 Pen Drives with ISOs recorded using different software. I had PC parts scattered all over and had obviously already cut my finger somewhere inside the cases.  

Then I installed Windows 7 64bits in both machines so I could run software to test the hardware (from WD, Seagate, AMD, etc). Then, when I realized it could not be anything with the hardware, I figured it had to do with partitioning and formatting somehow.

So I used a Gparted live CD to format and partition the HDD and mounted the Pen Drive ISOs. Success...yey.

Regards,
Effenberg

---

### Post by pressureman on 2011-09-01
You spent 10 hours trying to install an alpha version of an OS, without once suspecting that that could be the cause of your problems?

---

### Post by effenberg0x0 on 2011-09-01
The same OS version was installed at a similar machine that was sitting aside (not by me, don't know who installed it or how). So it was obviously possible. I couldn't predict the headache cause I never had that much problem installing anything. And, by the end of the day, I am paid to do things, not to ask how or why :)

(As we sometimes joke at work: "-More typing, less talking. Look busy.")

---

### Post by sartic on 2011-09-24
I tried Kubuntu beta 2. It still has this problem jeee....

---

### Post by lucazade on 2011-09-24
is there a bug report to look at? I've never experienced this with alternate cd if it can help.

---

### Post by Quackers on 2011-09-24
Is your partition table good?

---

### Post by sartic on 2011-09-24
I repeat.. Ubuntu is already installed. New install stalls width 52% during scanning hd.

---

### Post by effenberg0x0 on 2011-09-24
Hey,

This *seems* to be related to installing over a pre-partitioned disk. I've also seen reports about acpi boot options, wrong udma modes, mdadm interfering. I've been trying to understand what exactly is the problem but couldn't isolate it. So far it just seems random to me. Can you please post some info?

- Do you get a "[Errno 5] Input/output error" ?(Or any message like that)
- Are you confident about your RAM or have you ever ran the memtest?
- Same question about the HDD?
- Is is a IDE, SATA 1, Sata 2, Sata 3 disk?
- Do you try to change installation defaults (acpi, raid, etc)
- If you switch to a VT, can you tell us where the install stopped / what the last messages were?
- On your working install, I'd like to see the output of some commands. Please attach the files created at your home directory by the following commands:
```

sudo lcpci -nn > ~/lspci.txt
sudo cat /boot/grub/grub.cfg > ~/grub.txt
sudo fdisk -l > ~/fdisk.txt
sudo smartctl -a /dev/sda > ~/smart.txt
sudo hdparm -I /dev/sda > ~/hdparm.txt
sudo df -H > ~/df.txt

```Regards,
Effenberg

---

### Post by sartic on 2011-09-27
1. never get any error. it just freeze on 52% (for me, some have stall example on 47%)
2. 1st thing i do on new (for me) machine
3. yeap. it works great on same machine even width same ubuntu version :)
4. most of them are ide, some sata2 (i use "ide" mode in bios)
5. no default install
6. i switch vt only if i will use vbox in this machine (if there is switch in bios)
7. i will ;)

---

