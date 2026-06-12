---
title: "cannot boot 18.04.1 server after default installation (lenovo t420 or w520)"
date: 2019-02-02
forum: New to Ubuntu
---

### Post by eliu on 2019-02-02
The only extra information I can provide is:
by "cannot boot" I mean the hard drive itself isn't bootable after installation.
I was using this "live" server iso, and used rufus to make an installation usb
single drive for both laptops
both laptops can be installed with 18.04.1 *desktop* ubuntu and boot no problem (default option of using entire disk, wipe everything was on it)
laptops' bioses are set with both "UEFI" and "Legacy" boot mode
I don't fully understand the "Secure Boot" concept and its impact on free software. I don't know how to check of enable/disable it on the laptops either
The 18.04.1 server was installed with default option, so there is this 1MB bios-grub partition, which I have no idea what for.

is there an iso image that is desktop, but without any GUI?

---

### Post by yancek on 2019-02-02
You should be able to enable/disable Secure Boot in your BIOS setup.  Methods for doing that vary with the manufacturer of the computer so you might try an online search for your specific computer's manual if you don't know how to access the BIOS.  You should see a message on screen telling you which key to use but it generally shows for only a few seconds

[https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/T420-Cannot-access-BIOS-settings/td-p/582041](https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/T420-Cannot-access-BIOS-settings/td-p/582041)

The bios_grub partition is required if you are doing a Legacy install with Grub boot code in the MBR and you are using GPT partitioning.  Generally with GPT partitioning, an EFI install is done.

---

### Post by eliu on 2019-02-02
[UPDATE] 
WITHOUT changing anything, I used the NONE-live server iso installation disk, I was able to successfully boot up the server. I think the live server iso failed to install grub, causing the laptop fail to boot

[PROBLEM SOLVED]
the problem is not ubuntu, but rufus. if rufus uses GPT format to burn iso into usb then live iso can boot after installation. if rufus uses MBR, then it won't work

---

### Post by eliu on 2019-02-03
> **yancek said:**
> 
The bios_grub partition is required if you are doing a Legacy install with Grub boot code in the MBR and you are using GPT partitioning.  Generally with GPT partitioning, an EFI install is done.

when creating bootable disk with rufus, rufus presents me with 2 options:
"Partition scheme: MBR + Target system: BIOS or UEFI"
"Partition scheme: GPT + Target system: UEFI (non CSM)"

the bootable usb using MBR option will create an installation on the laptop with 1MB of bios-grub mandatory partition. ( I assume that was the MBR portion of the HDD?)
the bootable usb using GPT option will create an installation with ?MB of /boot/efi partition.

That's very interesting behavior to me. The installer USB's booting scheme mandates the resulting installation HDD's booting scheme

---

