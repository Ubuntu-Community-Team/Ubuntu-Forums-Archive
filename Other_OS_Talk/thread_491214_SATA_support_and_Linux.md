---
title: "SATA support and Linux"
date: 2007-07-03
forum: Other OS Talk
---

### Post by Shazaam on 2007-07-03
What are your experiences with installing/running any Linux distro on a SATA hard drive(non raid, VIA onboard controller)? I have found that some work and some don't.

Installed fine and run with no problems:
Ubuntu(dapper) of course!
Mepis
Puppy

Install but kernel panic (wrong block device, VFS errors, etc):
Mandriva One

Won't install:
damnsmalllinux

I realise this is a short list but I was suprised that Mandriva dies but PuppyLinux happily ticks along. Some answers given are that you have to add SATA support into the kernel and recompile it. Any distro's to add to this list?

---

### Post by timcredible on 2007-07-03
i've installed ubuntu and pclos on sata drives, haven't run into a problem yet.

---

### Post by adityakavoor on 2007-07-03
no problem here

---

### Post by igknighted on 2007-07-03
Weird, I've always used SATA and never had an issue with any distro (well, except on custom-compiled kernels, expecially gentoo... but thats my own fault).  I have tried every major distro and some not so major distros using a VIA sata chip and an nvidia sata chip, no problems with either.  I bet the errors you got with Mandriva One were an improperly set up GRUB entry.  As for DSL, I'm not sure... since it is made for old hardware perhaps SATA support is poor (its relatively new after all), but who knows.

---

### Post by deepclutch on 2007-07-03
I've got problems,transfer errors etc with feisty(kernel?).I have posted a thread for the same.
[http://ubuntuforums.org/showthread.php?t=489268](http://ubuntuforums.org/showthread.php?t=489268)
i can fix the errors if i try "irqpoll" boot option.but that lets my IDE DVD writer and CD writer detected as scsi :( and I know that from kernel 2.6.19 onwards parallel ata drivers are merged to libata;although older drivers are available.
Now with ide detected as scsi,i am doubtful of DMA support be enabled or what as hdparm(or sdparm too) fails HDIO_DMA_CTL error. :?
So someone show some light on these ?

---

### Post by Shazaam on 2007-07-03
> **igknighted said:**
> Weird, I've always used SATA and never had an issue with any distro (well, except on custom-compiled kernels, expecially gentoo... but thats my own fault).  I have tried every major distro and some not so major distros using a VIA sata chip and an nvidia sata chip, no problems with either.  I bet the errors you got with Mandriva One were an improperly set up GRUB entry.  As for DSL, I'm not sure... since it is made for old hardware perhaps SATA support is poor (its relatively new after all), but who knows.

The Mandriva One install was a fresh install on a blank SATA drive with default partition setup and grub installed to the mbr.

---

### Post by smoker on 2007-07-03
never had a problem so far, even with dsl, but i only ran dsl from live-cd, but it did detect my hard drive.

---

### Post by Shazaam on 2007-07-03
> **smoker said:**
> never had a problem so far, even with dsl, but i only ran dsl from live-cd, but it did detect my hard drive.

That's the funny part. ALL livecd's detect the drive. They will even let me mount it.

---

### Post by ivanrengo on 2007-07-03
I have some problems with a disc SATA 1 in ubuntu/kubuntu.

I have a PCI controller for SATA 1 in my PC to read this HDD because it isn't native in my motherboard (IBM NetVista 8315) and i haven't troubles in Windows, but in ubuntu/kubuntu when i read some files from this disc the system crash.

I appreciate all information that could help me.

Regards

---

### Post by 67GTA on 2007-07-04
I've never had any trouble installing on my SATA drive with any of the major distros. The only problem was not being able to change SATA settings after installation. For some reason they aren't able to be changed. Maybe because they maintain their own settings?

---

### Post by FoolsGold_MKII on 2007-07-04
Actually, I've got BETTER support for my SATA drive in Ubuntu than I did in Vista.

XP was fine, because there were drivers for my chipset (nForce 4). WIth Vista, the NF4 drivers are incomplete and basically rubbish, which meant my SATA controller ran in IDE compatability mode. Simply put, it was slow, used more CPU, didn't properly use my hardware. I had to force my XP chipset drivers in Vista if I wanted SATA support, which was dangerous.

---

### Post by VCSkier on 2007-07-04
I was having somewhat inconsistent, yet often showstopper problems (like the ones you described) with the new SATA drivers starting with the development releases of Feisty, but effecting pretty much ever distribution I tried.  I've more recently found that the problem was because of the HPA on my hdd.  Apparently the new SATA driver dosen't properly fully support HPA.  So I turned HPA off via my bios configuration, and I haven't had any problems since, with any distro.

---

