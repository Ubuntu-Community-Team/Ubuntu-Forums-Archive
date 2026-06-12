---
title: "HDD with Ubuntu installed is inaccessible except when booting from Live CD first"
date: 2014-12-05
forum: New to Ubuntu
---

### Post by justme3 on 2014-12-05
I have what seems like a strange problem.  When I installed Ubuntu (14.04) as the only operating system to my SATA HDD everything went great, until I powered off my system. When I powered the system back on, the drive wasn't accessible and the BIOS only recognized a device, but couldn't recognize any drive information.  And I couldn't get back in Ubuntu on the HDD.  However, I discovered that if I brought up the live CD version of the install disk, I could access the drive using the live CD.  

Now, if I reboot right after first using the Ubuntu CD in try mode (live CD), then when my motherboard reboots, it recognizes the drive and off I go.  But if I power down the system, then boot up from a powered down state, I can't access the drive at all (the BIOS doesn't recognize it) until I run a Linux live CD (any that I have seem to work).

I tried wiping the drive clean and reinstalling Ubuntu, and I noticed that the bare drive isn't recognized by my system until I boot with a Linux live CD, then it's accessible.

At this point Ubuntu (installed on the HDD) is only accessible from a powered down state after first running a Linux live CD.

I've run all kinds of diagnostics on the drive.  If I test it through DOS utilities, the drive isn't recognized or accessible except for a few programs like Active@KillDisk identifiying every sector as bad.  Yet when I use Linux-based utilities, the drive passes every health test using any program with no problems whatsoever.

Is the drive bad, or could it be something else?

---

### Post by Gordonbp531 on 2014-12-05
What make of computer, and is it UEFI enabled?

I had exactly this problem (albeit dual-boot, not single boot) with a new Acer Aspire E3 that came with Windows 8.1 + Bing pre-installed.
I installed ubuntu 14.04 - no grub, booted straight into Windows, although all the files were installed in the Ubuntu partition.
I eventually discovered that I had to go into the BIOS and in the Security tab, I had to set a Supervisor Password.
That then allowed me access to the Secure Boot settings, where I was able to add the Ubuntu EFI entry to the Secure Boot database. Exited, and lo! and behold! The Grub menu appeared on boot up.
You might try something like that....

---

### Post by justme3 on 2014-12-05
Thanks for the suggestion.

The motherboard is a MSI 785GM-E51 without UEFI, only BIOS.  It's from 2009.  Searching around some more I discovered a firmware update to the drive (Samsung HD502HJ) that fixed a very similar bug where the drive wouldn't show up in the BIOS.  I couldn't update the drive's firmware (using the Samsung/Seagate DOS firmware update utility) until I booted up from a Linux live CD first, then the program ran and updated the drive's firmware.  But that hasn't changed a thing.  Even Samsung's own disk diagnostics program can't recognize the drive unless I boot up with a live CD first and warm boot. 

My guess is that this is not a Ubuntu problem and the drive is dying.  But I wanted to check here first, in case someone might know something otherwise.

---

### Post by oldfred on 2014-12-05
Is BIOS correctly seeing drive.

What does Disks and Smart data show. Use tiny icon in upper right to get to Smart data.
It can run tests on drive, but all I know is passed is good and just about anything else is a new drive.

---

### Post by justme3 on 2014-12-12
The drive was bad.


Thanks.

---

