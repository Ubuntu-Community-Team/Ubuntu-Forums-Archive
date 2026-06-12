---
title: "Password locking the firmware?"
date: 2017-05-28
forum: New to Ubuntu
---

### Post by starscream2 on 2017-05-28
I am coming from a Mac, and I read how I can encrypt the hard drive on Ubuntu. So when I do get my new(er) computer with Ubuntu, I'll do that. On my MacBook I can put a password on the firmware to help prevent people from booting my MacBook from an external source, am I able to do this to Ubuntu? 

Thank you

---

### Post by TheFu on 2017-05-28
There are many, many, many different security methods for laptops/PCs.  Because there isn't 1 company making all the HW and SW choices, different hardware and different software will provide different capabilities.

For example, some BIOS makers allow a boot password. This is before any HDD/SSD/Storage is accessed.  It usually has a few other settings, like preventing BIOS settings from being changed without an admin password. This is for corporate owners.  There would be an admin and a boot password.  There might be a password just to view the BIOS too.  Of course, the BIOS can be reset to factory defaults if someone opens the case and does *something*.  On some systems it is pulling the CMOS battery. On others, it is using a pin jumper to create a short.  How it is handled is usually in the motherboard manual.  A proper "workstation" might have a chip that cannot be modified easily.  I've only seen those from Unix vendor equipment.  Resetting the BIOS password on those demands a service call to have chips replaced.

Then there are hardware addon devices tied to a TPM chip.  That could require a smartCARD or some other form of HW device to enable the computer to be used.  Generally only see these used in a govt environment, though I have seen them on high-end Dell business laptops.

Then there are specific types of HDDs which have HW enabled encryption.  Most HDDs don't have this, but you can buy them.

Then there are just pure software methods for encrypting the entire disk.  That really isn't true.  A small part of the disk is NOT encrypted, so the OS can boot, but everything else would be encrypted. This is what I use on my personal laptop.  During installation, you'll be asked if you want whole disk/drive encryption.  Say yes.  
The result will be something like this:
```
$ lsblk
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 55.9G  0 disk  
&#9500;&#9472;sda1                          8:1    0  487M  0 part  /boot
&#9492;&#9472;sda5                          8:5    0 55.4G  0 part  
  &#9492;&#9472;sda5_crypt                252:0    0 55.4G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root   252:1    0 51.5G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 252:2    0    4G  0 lvm   [SWAP]
```
This is **not** a firmware thing.

To make it slightly more secure, I use a Yubikey + a passphase to unlock the disk.  This has to happen before the OS can be fully booted.  LUKS+dm-crypt are the tools which handles the encryption stuff under the covers.  cryptsetup is the command to see the settings, add more unlock keys (useful if multiple people share the computer) or to want more control than the defaults.
This setup also uses LVM, which is a logical volume manager. It make the file system extremely flexible for some complexity.  It also makes getting a completely quiesced file system possible if you leave some room for a snapshot LV within the same VG. That makes backups possible for actively used files, databases, etc. 

This last method can be susceptible to the [evil maid attack]("https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html"), if you ever boot from the unencrypted /boot/ partition.  Basically, the way to prevent that is by having a boot flash drive that never leaves your person - ever and is always used instead of the HDD/SSD-based boot.  By not allowing the BIOS to be modified and setting it to only boot from a specific SATA port, you can lock down a PC fairly well.

So - if you want the most security possible, then be careful picking the exact device. Oddly, the most secure devices that I know are chromebooks.  They all have TPM and boot a signed, read-only, OS.  A 2nd copy of the OS is available and were signed updates go. 

As you probably know, be careful with any fingerprint or facial recognition stuff. I've not seen any fingerprint readers which haven't been compromised using a low-tech method.

Also, every PC/Mac/Linux machine with USB ports are hackable in just a few seconds thanks to automatic driver loading for USB devices.  A choice was made for convenience which isn't secure. With Linux, you can disable that and selectively disable USB ports by using udev rules.

Wish I could provide more specific answers.  I'm just not in the market for a new computer.  You probably know most of this already.

---

