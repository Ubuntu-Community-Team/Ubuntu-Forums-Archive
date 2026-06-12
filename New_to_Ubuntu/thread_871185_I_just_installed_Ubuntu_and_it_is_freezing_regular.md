---
title: "I just installed Ubuntu and it is freezing regularly"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by pfeifferock on 2008-07-26
I just installed Ubuntu 8.04 onto my laptop (Fujitsu Lifebook S) and when ever i try to play any media with totem player or with rythombox the screen goes black and i cant do anything with it and just hold the power button till it shuts down. 

The last time it did this i was installing some updates and when i tried to do it again after i rebooted it gave me this error message 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

i researched dpkg and found advice on manually installing it here [https://lists.ubuntu.com/archives/ubuntu-accessibility/2006-September/001008.html](https://lists.ubuntu.com/archives/ubuntu-accessibility/2006-September/001008.html) but i realy don't understand what to do. 
Any help would be appreciated
-Matthew Pfeiffer

---

### Post by Troll_the_Great on 2008-07-26
Open a terminal and type
```
sudo dpkg --configure -a
``` 
and see if it helps.
It is not good to do a hard shut down with the power button.If your computer freezes do this:hold Alt and Print Screen pressed and press R,E,I,S,U,B about a second delay between the letters.This will safely shut down the computer.
Hope this helps.Post back the results.
Cheers!

---

### Post by ibuclaw on 2008-07-26
The most common reason for frequent freezing is due to a serious hardware failure/incompatible hardware.

Such includes Motherboards too. (My first Linux install was on a Foxconn M/B that froze indefinately quite frequently, especially when connecting to the Internet wirelessly. A few months later, I switched to a AmiTrends Motherboard, using the exact same device/peripherals, I haven't had a problem with it in 2 years :)) 

Can you post the output of this command up:
```
sudo lshw -short
```
This will list all hardware of your system.

With it, someone could identify or confirm that it is the fault of an incompatible hardware/device.

Regards
Iain

---

### Post by pfeifferock on 2008-07-27
this is what my terminal told me about my hardware does any of this look suspicious? 
"system         LifeBook S Series
/0                             bus            FJNB181
/0/0                           memory         128KiB BIOS
/0/4                           processor      Intel(R) Pentium(R) M processor 16
/0/4/8                         memory         64KiB L1 cache
/0/4/9                         memory         1MiB L2 cache
/0/23                          memory         512MiB System Memory
/0/23/0                        memory         256MiB SODIMM DDR Synchronous 166 
/0/23/1                        memory         256MiB SODIMM DDR Synchronous 166 
/0/100                         bridge         82852/82855 GM/GME/PM/GMV Processo
/0/100/0.1                     system         82852/82855 GM/GME/PM/GMV Processo
/0/100/0.3                     system         82852/82855 GM/GME/PM/GMV Processo
/0/100/2                       display        82852/855GM Integrated Graphics De
/0/100/2.1                     display        82852/855GM Integrated Graphics De
/0/100/1d                      bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.1                    bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.2                    bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.7                    bus            82801DB/DBM (ICH4/ICH4-M) USB2 EHC
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1e/a                    bridge         OZ711M3/MC3 4-in-1 MemoryCardBus C
/0/100/1e/a.1                  bridge         OZ711M3/MC3 4-in-1 MemoryCardBus C
/0/100/1e/a.2                  system         OZ711Mx 4-in-1 MemoryCardBus Accel
/0/100/1e/a.3                  bridge         OZ711M3/MC3 4-in-1 MemoryCardBus C
/0/100/1e/c        eth0        network        BCM4401-B0 100Base-TX
/0/100/1e/d        eth1        network        PRO/Wireless 2200BG Network Connec
/0/100/1e/e                    bus            TSB43AB21 IEEE-1394a-2000 Controll
/0/100/1f                      bridge         82801DBM (ICH4-M) LPC Interface Br
/0/100/1f.1        scsi0       storage        82801DBM (ICH4-M) IDE Controller
/0/100/1f.1/0      /dev/sda    disk           60GB IC25N060ATMR04-0
/0/100/1f.1/0/1    /dev/sda1   volume         54GiB EXT3 volume
/0/100/1f.1/0/2    /dev/sda2   volume         1451MiB Extended partition
/0/100/1f.1/0/2/5  /dev/sda5   volume         1451MiB Linux swap / Solaris parti
/0/100/1f.1/1      /dev/cdrom  disk           DVD-RAM UJ-840S
/0/100/1f.3                    bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1f.5                    multimedia     82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1f.6                    communication  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/1                             power          CP176595-XX / CP176596-XX"

sry this is so long i just don't know what any of this means. if any of this hardware looks iffy let me know. i'm not having the problems with the screen going blank black so much (at least not in the past couple hours) but now my firefox is freezing up if i have too many tabs open at the same time. this wasn't happening my laptop when i was running xp. and i am connecting with wireless internet. let me know if you have any advice thanks.
-Matthew Pfeiffer

---

### Post by pfeifferock on 2008-07-28
thanks so far but bump

---

### Post by cotcot on 2008-07-28
Maybe [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=767833&page=8") thread could give you some suggestions.

---

