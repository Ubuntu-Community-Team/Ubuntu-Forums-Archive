---
title: "Laptop Heat"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by JamButty on 2011-12-23
I have spent days reading old threads about various overheating issues and the only advice I've found is to replace fans/heat sink (no$, not possible now) or apply new thermal grease (getting that massively into the internals of a laptop scares the silicon out of me). All heat exits have been thoroughly vacuumed out (and the unit is fairly new and unused, so dust bunnies should not be an issue). Just transferred from 7 years on a Dell Inspiron, the last two on Lucid with very few problems - very good experience overall. It is mostly dead now and I got gifted an HP Elitebook, lightly used. I've got Win7 and Oneiric on it. I can't use the Oneiric side more than about an hour at a time before the temps go up into the mid-80's, even while idling. On the windoze side, there is a slight problem (gpu gets hot after intensive gaming applications), but is radically cooler on all sensors otherwise. I can overheat it on the win side also with thrasher progs like Prime95. I've tried Xsensors and Psensor - neither can appropriately identify which temp refers to which item (e.g. core 1, core 2, gpu), both programs just give me generic temp1, temp2 etc.(temp sensor prog on win side identifies those items correctly), so I can only guess that the hottest component running under Oneiric is the GPU, though it gets hot regardless of the type of prog running (cpu intensive or graphics intensive). All sensor progs and system info I can find only refers to 1 fan, which seems odd. 

There are no general overheating issues with this model I have read about.

So, lengthy intro aside, any tips on why a laptop should run radically hotter under Linux than under Windoze? - Any software-based solutions? HW/SW data below, thanks.

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
``````
uname -r
3.0.0-14-generic
``````
sudo lshw -C display

  *-display              
       description: VGA compatible controller
       product: Mobility Radeon HD 3650
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:80000000-8fffffff memory:98300000-9830ffff ioport:7000(size=256) memory:98320000-9833ffff
``````

sudo lshw -short
H/W path         Device      Class       Description
====================================================
                             system      Notebook
/0                           bus         30E7
/0/9                         memory      64KiB BIOS
/0/0                         processor   Intel(R) Core(TM)2 Duo CPU     P8600  @
/0/0/1                       memory      3MiB L2 cache
/0/0/3                       memory      32KiB L1 cache
/0/0/0.1                     processor   Logical CPU
/0/0/0.2                     processor   Logical CPU
/0/2                         memory      32KiB L1 cache
/0/4                         memory      2GiB System Memory
/0/4/0                       memory      2GiB SODIMM DDR2 Synchronous 800 MHz (1
/0/4/1                       memory      SODIMM [empty]
/0/100                       bridge      Mobile 4 Series Chipset Memory Controll
/0/100/1                     bridge      Mobile 4 Series Chipset PCI Express Gra
/0/100/1/0                   display     Mobility Radeon HD 3650
/0/100/1/0.1                 multimedia  RV635 Audio device [Radeon HD 3600 Seri
/0/100/19        eth0        network     82567LM Gigabit Network Connection
/0/100/1a                    bus         82801I (ICH9 Family) USB UHCI Controlle
/0/100/1a.1                  bus         82801I (ICH9 Family) USB UHCI Controlle
/0/100/1a.2                  bus         82801I (ICH9 Family) USB UHCI Controlle
/0/100/1a.7                  bus         82801I (ICH9 Family) USB2 EHCI Controll
/0/100/1b                    multimedia  82801I (ICH9 Family) HD Audio Controlle
/0/100/1c                    bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.1                  bridge      82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0    wlan0       network     Ultimate N WiFi Link 5300
/0/100/1c.2                  bridge      82801I (ICH9 Family) PCI Express Port 3
/0/100/1c.4                  bridge      82801I (ICH9 Family) PCI Express Port 5
/0/100/1d                    bus         82801I (ICH9 Family) USB UHCI Controlle
/0/100/1d.1                  bus         82801I (ICH9 Family) USB UHCI Controlle
/0/100/1d.2                  bus         82801I (ICH9 Family) USB UHCI Controlle
/0/100/1d.7                  bus         82801I (ICH9 Family) USB2 EHCI Controll
/0/100/1e                    bridge      82801 Mobile PCI Bridge
/0/100/1e/9                  bus         R5C832 IEEE 1394 Controller
/0/100/1e/9.1                generic     R5C822 SD/SDIO/MMC/MS/MSPro Host Adapte
/0/100/1e/9.2                generic     R5C592 Memory Stick Bus Host Adapter
/0/100/1e/9.3                generic     xD-Picture Card Controller
/0/100/1e/9.4                bridge      RL5c476 II
/0/100/1f                    bridge      ICH9M-E LPC Interface Controller
/0/100/1f.2      scsi0       storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0    /dev/sda    disk        250GB WDC WD2500BEVT-0
/0/100/1f.2/0/1  /dev/sda1   volume      58GiB Windows NTFS volume
/0/100/1f.2/0/2  /dev/sda2   volume      170GiB EXT4 volume
/0/100/1f.2/0/3  /dev/sda3   volume      4000MiB Linux swap volume
/0/100/1f.2/1    /dev/cdrom  disk        DVD RW AD-7561S
/0/1             scsi6       storage     
/0/1/0.0.0       /dev/sdb    disk        40GB iPod
/0/1/0.0.0/0     /dev/sdb    disk        40GB 
/0/1/0.0.0/0/1   /dev/sdb1   volume      39MiB Empty partition
/0/1/0.0.0/0/2   /dev/sdb2   volume      37GiB Windows FAT volume
/1                           power       AV08073
```

---

### Post by nothingspecial on 2011-12-23
Question moved to it's own thread.

---

### Post by Lars Noodén on 2011-12-23
I'm running into the same or similar problem on a MacBook Pro and Mac Mini:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/881593](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/881593)

My solution is to run the fans manually at a higher speed, but that is a kludge and not a real solution.  Not to mention that it does nothing for battery life if I were to try to run unplugged.

---

### Post by Basher101 on 2011-12-23
It is a hardware sided. I had owned a HP pavilion Dv5 and it got always very hot, even on idle with either windows or ubuntu...I got myself a new Acer laptop and even under load on both operating systems it stays cooler than the HP on idle..

---

### Post by Mark Phelps on 2011-12-23
The following provides some info as to why a PC would run hotter in Linux than in Windows:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

---

### Post by JamButty on 2011-12-23
Thanks for suggestion. Have applied and will see. Initial results not promising. Seems to be pointing primarily at a power issue (I am not often off the mains power, so no much of an issue for me), and only indirectly a heat issue.

---

### Post by Mark Phelps on 2011-12-23
Sorry the results aren't promising.

It generally manifests itself as a heat issue because folks who are dual-booting (often with Win7) notice their laptops running a lot hotter -- and the fan running either loudly or all the time.

What makes it a heat issue is that, due to the kernel bug, the processor does not throttle back when demand lessens, causing it to run at full power, and consequently, run hotter over time.

---

### Post by blackbird34 on 2011-12-23
Would the Jupiter applet help in this, do you think? 

From this thread:
[http://ubuntuforums.org/showthread.php?t=1854019](http://ubuntuforums.org/showthread.php?t=1854019)[]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html")

> **Rasa1111 said:**
> Hey!

Just wanted to share my experience with the Jupiter Applet, designed to  easily adjust performance/system settings on laptops and netbooks. 

I've been using it for about 4 days now..
and I've noticed some great changes to my laptop since then!

Here is what Jupiters site says about Jupiter..

[http://www.jupiterapplet.org/](http://www.jupiterapplet.org/)

Our friends over at webupd8 have made it so that it's easily installable and works well in 11.10, 
See here> [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)
I own an IBM Thinkpad Z61t, which is about 5 years old.
It runs great, and is very fast..
But it often gets quite hot when running things that require a lot from the CPU's.

My battery is also not as good as it once was.. (only at 62% capacity now)

Usually, when Im playing a movie or something...
(or the few times Ive played Vendetta online)
my temps will often climb to above 70 degrees Celsius. 
I've even watched get above 80 in the past. lol

 My battery typically only lasts on a full charge for about an hour and a half, maybe 2 if Im lucky. 

But since Ive installed Jupiter, 
I have it set on "Power Saver"..

and no matter what I do, or run...
My temps are not climbing above 55 C or so, and that's with my CPU's maxed out. 

My battery has also been lasting a good 2 and half , to 3 hours on a full charge!

Im not sure exactly *what* Jupiter is doing in/to my system..
But I'm amazed by the outcome! 

I really didn't expect much from it..
and I certainly didn't expect *this much* from it! 

So anyone who has issues with heat, or with battery life..
Do give Jupiter a try! 

There are quite a few things it can do I guess..
But my main focus was the heat and battery life...
and the change to both has been awesome!

Anyone else using this, and experiencing similar changes? 

I'm really amazed by it! haha

many thanks to the developers of Jupiter!
You've done well!
and probably extended the life of my beloved Thinkpad. lol

 The bottom of my laptop is actually cool to the touch now!
which it never was, even when running just a browser and music player. 

Very, very cool! 
Got to be one of the greatest pieces of software Ive installed in my 2 years of using Ubuntu! :KS

Amazing. :smile: <3

---

### Post by kaldor on 2011-12-23
You're using the open source Radeon driver.

Sadly, the power management is crap with the open source NVIDIA and AMD drivers. This can lead to poor battery life and high heating issues. Your best bet is to install the proprietary AMD driver (Catalyst) in the Additional Drivers application. 

Advice regarding the proprietary driver..

The proprietary AMD driver has been known to cause issues for some users. While everything might work out fine, don't be surprised if you end up having some random display issues which will need fixing. It has superior power management compared to the default driver. It lacks in simple 2d performance to some extent, though.

My laptop runs about 50 degrees hotter with the default Nouveau driver than when I use the proprietary NVIDIA one. Hopefully this will be the solution to your problem as well.

---

### Post by JamButty on 2011-12-24
Thanks Kaldor - that may be it. I did multiple wipes and reinstalls initially (problems on Win side) and each time the proprietary graphics drivers bombed so I gave up. Tried again now and the main driver loaded (updates bombed). So far it looks good. The sensor programs don't tell me which temp is which part, so I am not sure which one is the GPU. Ran Prime95 for a while to stress the CPUs, so I've identified at least one core temp. So far everything is staying under 50C. I've had one severe display problem. The display got so severely pixelated that it was unusable and I had to power-crash it. I will continue to monitor and mark this solved if this works out.

---

### Post by JamButty on 2011-12-28
Marking solved. Still runs hot (CPU 50-70) but much more manageable - no longer in the crash range. Jupiter also helps. Thanks blackbird34. Tried a game with Jupiter on "max performance" and it went to over 90 in a few minutes, so keeping that on "power saver" works well.

---

