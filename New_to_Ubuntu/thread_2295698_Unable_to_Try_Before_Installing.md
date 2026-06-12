---
title: "Unable to Try Before Installing"
date: 2015-09-20
forum: New to Ubuntu
---

### Post by Kirasha on 2015-09-20
Hello!

I've been considering switching to Linux from Windows and recently purchased an Ubuntu 14.04.3 live drive (usb) from OSDisk to test it out. (I realize I could have made my own. But, as I've never done something like that before, I opted to go with having someone who knows what they're doing do it.)

When I boot from the USB stick, it seems to be fine. I get the option to Try before installing and once selected, the purple loading screen with colored dots appears. But, then it seems to drop me into some sort of shell program and displays the following:[INDENT][I]
4.068889 ACPI: More than one Lid device found
4.135728 ACPI PCC probe failed
5.438847 sd 3:0:0:0: [sdb] No caching mode page found
5.438877 sd 3:0:0:0: [sdb] Assuming drive cache: write through

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
(initramfs)
[/I][/INDENT]

I'm trying to run this on a brand new (literally fresh out of the box) Toshiba Satellite C50-B with Win7 Pro 64-bit pre-installed. If I do install Ubuntu, I'll need to dual boot it with Windows in order to run a couple of particular programs I haven't found reasonable substitutes for, yet. So, I definitely do not want to overwrite Windows.

I did some research both here and on other sites and found recommendations to defrag through Windows, which I did. And that seemed to temporarily resolve the two [sdb] lines. But, on a subsequent reboot after I still couldn't get past the (initramfs) prompt, they came back. It did not resolve the issue of being dumped into the built-in shell.

I also found numerous mentions of an issue similar to this on earlier versions of Ubuntu that could be resolved by taking out the physical hard drive, something I'm hesitant to do as I would only barely consider myself to be a slightly above average computer user and this is a brand new laptop, so it would likely void my warranty if I were to try messing with it that way.

My research also brought up several references to having unallocated space when installing. Nothing seemed to specify if this was necessary to simply run Ubuntu off the USB drive itself without installing. I've checked my system and it looks like the hard drive (a Toshiba MQ01ABD100 with 1TB space) has been pre-configured with three partitions:

1. Active, Recovery Partition (1.46GB allocated, 1.46GB free)
2. Primary Partition (9.86GB allocated, 9.86GB free)
3. Boot, Page File, Crash Dump, Primary Partition (920.18 GB allocated, 875.76GB free after activating Windows and installing updates)

I'm thinking I need to shrink that third one and create the unallocated space? But then, I also found several references to a problem with having four partitions on Windows?

Any advice or simple steering in the right direction would be greatly appreciated! At this point, I think I'm confusing myself with too much research on top of too little experience.

---

### Post by newb85 on 2015-09-21
Concerning 4 partitions: the number of partitions you can have depends not on the operating system, but on the partitioning scheme.  If you're using the older MBR/BIOS scheme, than you can't have *more* than 4 primary partitions.  The way around this is to have one of those four be an extended partition, which is simply a container for logical partitions.  If, on the other hand, you're using GPT/UEFI, then the number is virtually unlimited, and you don't need to worry about it.

You're using Win 7, which could have been installed either way, so you'll have to check which one it is.  (Google how to check this.)

If you are on MBR, you still have one left.  You may want to create an extended partition anyway, in case you determine down the road that you want an additional partition for something.

Either way, you'll need to make sure you install Ubuntu using the same system Windows uses if you go dual boot.


Regarding the Lid device error: I don't know much about this, but my suggestion is that you make sure you're booting from a completely powered down state.  (No suspend or hibernate.)

---

