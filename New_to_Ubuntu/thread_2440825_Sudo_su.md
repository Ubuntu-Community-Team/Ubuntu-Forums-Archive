---
title: "Sudo su"
date: 2020-04-15
forum: New to Ubuntu
---

### Post by canahmetdursun on 2020-04-15
Why is opening spotify with SU redirects me to create an account?
Simple question thx :)

---

### Post by CelticWarrior on 2020-04-15
Yes, simple question with a simple answer: Different user, different account.
But also dumb & dangerous - It clearly show you don't know what you're doing.

Please read this [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) in order to understand how Ubuntu is designed regarding root privileges (for the moment ignore the warning about outdated info; some of it is actually outdated but it doesn't concern you) and how nobody should use 'su', especially newbies.

And, generally speaking, running any graphical software as root is a very bad idea. Why do you want to run Spotify as such, of all things? What problem are you trying to solve?

---

### Post by canahmetdursun on 2020-04-16
I want to solve core dump crashes. Spotify sometimes crashes and gives me "Core dumped" error immediately after it opens and i have some troubles with nvidia drivers i cant choose nvidia-420 driver when i clicked and chose recommended driver it jumps back to X.Org XServer driver. :/ 
Btw thanks for your reply man! Really appreciate it! :)

---

### Post by CelticWarrior on 2020-04-17
So those are the questions you should be asking instead of what you you think is a solution - IT ISN'T -, this is called a X-Y problem.

Regarding the Nvidia driver, why 420 specifically? Likely you want some current version instead.
Please start by posting your Ubuntu release/version and your hardware specifications and get into the habit of doing that whenever posting a support request.

---

### Post by canahmetdursun on 2020-04-17
Okay! Thanks! I will post it soon :)

---

### Post by canahmetdursun on 2020-04-17
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 19.04
Release:        19.04
Codename:       disco
*******************************
H/W path       Device     Class          Description
====================================================
                          system         G5 5587 (0825)
/0                        bus            0M2MWX
/0/0                      memory         64KiB BIOS
/0/45                     memory         16GiB System Memory
/0/45/0                   memory         8GiB SODIMM DDR4 Synchronous 2667 MH
/0/45/1                   memory         8GiB SODIMM DDR4 Synchronous 2667 MH
/0/4e                     memory         384KiB L1 cache
/0/4f                     memory         1536KiB L2 cache
/0/50                     memory         9MiB L3 cache
/0/51                     processor      Intel(R) Core(TM) i7-8750H CPU @ 2.2
/0/100                    bridge         8th Gen Core Processor Host Bridge/D
/0/100/1                  bridge         Xeon E3-1200 v5/E3-1500 v5/6th Gen C
/0/100/1/0                display        GP106M [GeForce GTX 1060 Mobile]
/0/100/1/0.1              multimedia     GP106 High Definition Audio Controll
/0/100/2                  display        Intel Corporation
/0/100/4                  generic        Xeon E3-1200 v5/E3-1500 v5/6th Gen C
/0/100/8                  generic        Xeon E3-1200 v5/v6 / E3-1500 v5 / 6t
/0/100/12                 generic        Cannon Lake PCH Thermal Controller
/0/100/14                 bus            Cannon Lake PCH USB 3.1 xHCI Host Co
/0/100/14/0    usb1       bus            xHCI Host Controller
/0/100/14/0/2             input          SteelSeries Rival 600
/0/100/14/0/5             multimedia     Integrated_Webcam_HD
/0/100/14/0/9             communication  Goodix Fingerprint Device
/0/100/14/0/e             communication  Bluetooth wireless interface
/0/100/14/1    usb2       bus            xHCI Host Controller
/0/100/14.2               memory         RAM memory
/0/100/14.3    wlp0s20f3  network        Wireless-AC 9560 [Jefferson Peak]
/0/100/15                 bus            Intel Corporation
/0/100/15.1               bus            Intel Corporation
/0/100/16                 communication  Cannon Lake PCH HECI Controller
/0/100/17                 storage        Intel Corporation
/0/100/1b                 bridge         Cannon Lake PCH PCI Express Root Por
/0/100/1d                 bridge         Intel Corporation
/0/100/1d/0    enp59s0    network        Killer E2400 Gigabit Ethernet Contro
/0/100/1f                 bridge         Intel Corporation
/0/100/1f.3               multimedia     Cannon Lake PCH cAVS
/0/100/1f.4               bus            Cannon Lake PCH SMBus Controller
/0/100/1f.5               bus            Cannon Lake PCH SPI Controller
/0/1           scsi0      storage        
/0/1/0.0.0     /dev/sda   disk           1TB ST1000LM035-1RK1
/0/1/0.0.0/1   /dev/sda1  volume         15MiB reserved partition
/0/1/0.0.0/2   /dev/sda2  volume         736GiB Windows NTFS volume
/0/1/0.0.0/3   /dev/sda3  volume         487MiB Windows FAT volume
/0/1/0.0.0/4   /dev/sda4  volume         48GiB EXT4 volume
/0/1/0.0.0/5   /dev/sda5  volume         27GiB Linux swap volume
/0/1/0.0.0/6   /dev/sda6  volume         118GiB EXT4 volume
/0/2           scsi1      storage        
/0/2/0.0.0     /dev/sdb   disk           256GB LITEON CV8-8E256
/1                        power          DELL W7NKD86
/2             docker0    network        Ethernet interface
```

---

### Post by CelticWarrior on 2020-04-17
Thank you for posting the detailed information as requested.
Here's the first problem:
```
 Description:    Ubuntu 19.04
```
Ubuntu 19.04 is Out of Support since January. You need to upgrade to a supported release. Ubuntu 20.04 with 5 years support (19.04 had 9 months only because unlike 18.04 and 20.04, it isn't a LTS release) will be officially released in a few days but you can install it right now. I have have one installed a couple of weeks ago running solid.

There's absolutely no point in troubleshooting your current installation.

Then the graphics
```
/0/100/1/0                display        GP106M [GeForce GTX 1060 Mobile]
```
do indeed beg for Nvidia proprietary drivers and currently the recommendation is 440.xx only. It can be latter updated but in any case you shouldn't try to force installation of previous, now deprecated, versions. And you can't install any because there are no software repositories available for your defunct release.

In an nutshell: Install 20.04 from scratch and if you still have problems with some software ASK! Do NOT in any case try to run GUI apps as root.

---

### Post by canahmetdursun on 2020-04-17
```

 Description:    Ubuntu 19.04


```
Is this why this doesn't work?
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by CelticWarrior on 2020-04-17
> **canahmetdursun said:**
> ```

 Description:    Ubuntu 19.04


```
Is this why this doesn't work?
```

sudo apt-get update
sudo apt-get upgrade

```

Of course it is. The software repositories APT depends on aren't available because 19,04 is EoL and those repos have been moved to archive.

---

### Post by canahmetdursun on 2020-04-17
Should I do a clean setup ?

---

### Post by CelticWarrior on 2020-04-17
> **canahmetdursun said:**
> Should I do a clean setup ?

Absolutely.
Backup your personal files if you haven't done that already, nuke & pave.

---

### Post by canahmetdursun on 2020-04-20
I nuked and paved! x) Just installed a stable version of ubuntu 19.10 .20.04 threw so many errors to me. Now what should i do ? :  )

---

### Post by canahmetdursun on 2020-04-21
SOLVED: SOLUTION


This is because you have a Nvidia Graphics not properly supported by the open-source driver *nouveau*  (see the preceding error message) therefore you need to add 'nomodeset'  to have a desktop environment in the live session and then install as  usual. make sure to select the option to install third-party drivers,  codecs, etc.

How to add nomodeset?
In the first menu (Grub) with the "Try Ubuntu" option selected, press  'e' to edit. Use the cursor keys to navigate to where "quiet splash" is  and add "nomodeset" after it. Confirm and proceed. It should now boot  the live session with low graphics.

---

