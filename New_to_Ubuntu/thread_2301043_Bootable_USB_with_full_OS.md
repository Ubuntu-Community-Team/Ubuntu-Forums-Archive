---
title: "Bootable USB with full OS"
date: 2015-10-30
forum: New to Ubuntu
---

### Post by Emanuel_Rom on 2015-10-30
Hi

I'm running a Lenovo Thinkpad t450s with windows 10 on it. I was able to install Ubuntu to a flash drive using the live CD and can boot it from my computer since it installed GRUB. I was wondering if i could make it possible for the flash drive itself to load GRUB so that i could boot my Ubuntu from a computer that does not have GRUB preinstalled. When i try booting the Drive directly from the BIOS boot menu it just gets me back to the BIOS even though GRUB should be installed on the drive.

---

### Post by ian-weisser on 2015-10-30
Yes, and if you search this forum you will discover many threads on the topic.
Did it myself, too, years ago.

Your BIOS must be capable of booting a USB stick. Your description is vague, but seems like you are unable to do that.
Most BIOS are quite clear about what they will/won't boot.

---

### Post by Emanuel_Rom on 2015-10-30
Thank you for your reply. I know there are threads on here that have the answer, but i tried many options that didn't work. My BIOS can boot USB sticks, that's how i was able to boot the live version of Ubuntu (which i installed on a stick)

---

### Post by ian-weisser on 2015-10-30
You should probably tell us what you have tried, and what failed.
For example, did you *install* Ubuntu to a USB stick using the Ubuntu installer?

---

### Post by Emanuel_Rom on 2015-10-30
From the live version i installed Ubuntu to a usb stick. This also installed GRUB in my laptop allowing me to boot it, but when choosing the stick from the boot menu, it wouldn't boot. Then i tried reinstalling GRUB by booting the live cd and installing GRUB onto my USB using grub-install. Once that also failed i booted into the stick and used YannUbuntu's boot-repair tool but it still hasn't loaded. I just can't seem to figure out why it will boot the live version directly from the flash drive it's installed on, but not my full version of Ubuntu. The live version was installed on a fat32 formatted flash drive, my Ubuntu desktop is installed on ext4.

---

### Post by sudodus on 2015-10-30
Welcome to the Ubuntu Forums :-)

[Is the computer running in UEFI mode or in classical BIOS mode?](http://ubuntuforums.org/showthread.php?t=2230389&p=13370798#post13370798)

It is often easiest to remove the internal drive before installing Ubuntu into a USB stick.

1. You eliminate the risk to write anything to the internal drive.

2. The installer 'has no choice', it must install everything to the USB stick, including the bootloader and EFI directory and files.

I think it is easier to re-install after removing the internal drive than to repair your current system in the USB stick.

---

### Post by Emanuel_Rom on 2015-10-30
I am running in UEFI mode, but i could change that if you believe that that is the problem. I can't remove the internal drive since on my Laptop it is hard to remove and not worth it for this job

---

### Post by sudodus on 2015-10-30
I think that the installer in UEFI mode will 'do what it wants to do' and install the bootloading system into the internal drive, particularly when it finds an EFI partition there. And Windows has created such a partition when it was installed.

Instead you can make  a system according to this thread (clone from dd_Ubuntu_14.04.2-UEFI-n-BIOS-10GB.img.xz),

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506")

You need a drive with at least 10 GB (it usually means a USB pendrive with 16 GB or more).

---

### Post by Emanuel_Rom on 2015-10-30
That's an interesting idea. Since the system is new i don't mind reinstalling it, so i'll try reinstalling using an old mac laptop, hoping that it'll install GRUB to the external instead of the internal drive.

---

### Post by oldfred on 2015-10-30
With my full install of Ubuntu to a flash drive, I had to partition in advance to make sure I had the ESP - efi system partition. I also added the bios_grub partition, but did not install the BIOS version of grub.  BIOS boot is probably a bit easier to configure.

With UEFI, grub always installs to the ESP on sda. I even see it saying it is installing to sdb during install, but it overwrites my /EFI/ubuntu folder in sda.
And external devices with UEFI boot from a FAT32 formatted partition with the boot flag. Or is using gdisk the code is ef00. The actual code UEFI looks for is a very long GUID which different tools use different methods to assign the correct GUID.

And UEFI only boots /EFI/Boot/bootx64.efi on external devices and similar path is fallback or alternative boot for internal devices.
So you have to copy existing /EFI/ubuntu on sda to /EFI/ubuntu on sdb. Then copy again to /EFI/Boot. Then rename shimx64.efi to bootx64.efi. You need both copies as grub only looks for /EFI/ubuntu/grub.cfg. The copy of grub in the ESP is just a configfile entry to find the full grub.cfg in your install.

---

### Post by sudodus on 2015-10-30
> **Emanuel_Rom said:**
> That's an interesting idea. Since the system is new i don't mind reinstalling it, so i'll try reinstalling using an old mac laptop, hoping that it'll install GRUB to the external instead of the internal drive.

Cloning the system means that each byte will be copied, so there will be bootloaders for UEFI as well as for BIOS mode :-)

---

