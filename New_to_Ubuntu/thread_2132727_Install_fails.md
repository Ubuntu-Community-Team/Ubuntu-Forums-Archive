---
title: "Install fails"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by ECMLfan on 2013-04-05
Hi all,

I was so fed up with certain frustrating things in Windows that I whish to use another real operating system. (I use OSX on my mac and macbook).

So I used DBAN to wipe my hard drive and all partitions on it. 

I now have a fresh 3TB HDD where I can install Ubuntu. (I am planning to allocate 1 TB for the OS) There is however one issue. When I complete the installation and reboot my PC it tells me "Loading OS......." But nothing happens. I think that the PC just can't find Ubuntu.

Lets say I wish to start over and do a fresh install, what do I have to do with partitions etc. to get things right?

---

### Post by DuckHook on 2013-04-05
Hi and welcome to Linux, Ubuntu and the forums.

Please tell us a little more about your system. Does it have a UEFI BIOS? What video card? All info you can think of is helpful, but these two pieces of info are critical.

If UEFI, then you may wish to consider partitioning your disk as GPT rather than the ancient MBR. GPT will allow you to see the whole disk. MBR cannot address more than 2 TB.

Also, make sure that you turn secure boot off in your BIOS. This will likely be turned on if your box came with Windows 8 preinstalled.

Before getting into details, have you tried booting into LiveDVD/USB mode? If not, try this first before actually installing the system. It is always a good idea to see if the video, network, audio, etc work before actually installing.

---

### Post by ECMLfan on 2013-04-05
Hi Duckhook,

How can I find out if my BIOS is UEFI BIOS?

Further more some system specs:

3TB HDD
3Ghz AMD Octacore
2GB Sapphire GPU 7870
8GB RAM

---

### Post by DuckHook on 2013-04-05
UEFI BIOSes are very obvious once you boot into your BIOS. Most of them look far prettier than the old BIOS screens, and have actual graphics. They will usually tell you that they are UEFI or EFI (same thing) right on the first BIOS screen. They will also offer options like "UEFI boot", "UEFI mode" or "Legacy BIOS mode", etc. These options don't make sense if you have just the old BIOS.

You still need to make this determination, but if i were a betting man, I would guess that your BIOS is UEFI. I'm just looking at the rest of your specs, and they are pretty powerful, so my guess is that your motherboard is new and fully UEFI. Posting your motherboard specs or brand and model would clarify instantly. The docs that came with your box would also tell you instantly.

---

### Post by ECMLfan on 2013-04-06
Just went into BIOS and turned: EFI CD?DVD Boot option to : EFI

Fact is the damn thing will install and when I boot the system it's blank. 

What I did:

Formatted entire HDD
- Created 200 Mib partition with a root to /Boot
- Created 500 GB partition with a root to /
- Creaed 25GB partition with a root to /Home

All in all, the bootloader seems unable to boot the OS.

What on earth am I missing?

---

### Post by DuckHook on 2013-04-06
Things to check:

1. Did you turn off secure boot in the BIOS? If your computer came with Win 8 preinstalled, this is probably on.
2. Did you create a GPT partition table or did you leave it as MBR (MSDOS)?
3. Did you tell the install process to install bootloader to sda (NOT a specific partition like sda1 or sda2)?
4. The problem may also be your video driver. Do you get any screen activity at all? If so, please describe.
5. Did you try a LiveDVD session? If so, did it work? If not, try one now and describe result.

---

### Post by DuckHook on 2013-04-06
Please do all steps in last post. If system seems to boot to a point but hangs at Ubuntu screen, then, to address possible video issue, do following:

1. Hold down <Shift> key while system is booting. This will/should bring up the GRUB menu.
2. Select "Advanced options for Ubuntu".
3. Select "Recovery mode"

If this doesn't work, then:

1. Hold down <Shift> key while system is booting. This will/should bring up the GRUB menu.
2. Press <e> key to enter edit mode.
3. Find the line /boot/vmlinuz-[your version]...quiet splash $vt_handoff
4. Type in nomodeset at end of this line separated by <space> from other options
5. Press <Ctrl>+<x> or <F10> to continue booting

You will need to install the AMD proprietary driver for your video card from "additional drivers"

---

