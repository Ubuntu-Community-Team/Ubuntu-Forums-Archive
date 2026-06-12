---
title: "Kernel panic following fresh install"
date: 2017-05-23
forum: New to Ubuntu
---

### Post by ryan-n-waggoner on 2017-05-23
I'm totally lost here: Background- I've got a notebook (Dell Latitude 2120) that shipped with Win7 (Professional, 64-bit) installed. It was running too slow for my liking, so I installed Lubuntu 17.04 (64-bit) as a dual boot. After a few days of this, I thought maybe a 32-bit Windows install would run smoother, so I formatted the drive, and installed a copy of Win7 Ultimate that I had. I ran into problems finding drivers, so I said "screw it", and formatted the drive again, installing Lubuntu 17.04 this time as a single boot. Unfortunately, I had installed the 32-bit version, not realizing that there is no longer a 32-bit version of Chrome. (Chromium absolutely will not work for my needs.)

I want to mention that at every single point along the way so far, I never had a single problem booting into any OS I threw at this computer.

The problem: after realizing I was going to need a 64-bit version of Lubuntu, I downloaded the appropriate ISO and installed unetbootin. I busted out my thumb drive, and made a live USB of 64-bit Lubuntu. I booted to the thumb drive, selected "install", and opted to erase the current OS and install Lubuntu. Install seemed to progress normally, but I received a kernel panic after I rebooted.

I booted back into the thumb drive, ran Lubuntu in live mode, completely formatted the drive (slow method), installed again. Kernel panic again.

In a probably fruitless attempt to resolve this, I'm right now copying my entire thumb drive to the installed OS on the hard drive.

In short, I'm lost and confused and don't understand how I can consistently install only to be faced with a kernel panic when the USB made from the exact same image works flawlessly.

---

### Post by oldrocker99 on 2017-05-23
If UEFI is enabled, try installing in BIOS mode. That solved my kernel panic problem recently.

That's **if** your laptop allows non-UEFI booting.

---

### Post by ryan-n-waggoner on 2017-05-23
I can't seem to figure out how to install in BIOS mode; I looked in my laptop's BIOS, and I didn't see any option to switch between UEFI and Legacy. When I pull up the drive in Disks, it shows the drive is partitioned as Master Boot Record.

I've tried changing the partition to EFI and installing onto it, but to no avail.

Is there any easy way I can just start from scratch?

---

