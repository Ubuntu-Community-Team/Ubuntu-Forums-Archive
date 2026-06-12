---
title: "Grub2 not working but Grub Legacy does"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by Wiking on 2013-04-16
Hi, I just finished installing Kubuntu 12.10 on a pc with windows7,  using EasyBCD I was trying to add the boot entry to mbr.

For some reason Grub2 did not work and when I chose Linux in the OS selection screen on boot, I would end up on the Grub4DOS screen instead of the usual Grub screen where you select a distro. I had to use Grub Legacy and point to the device.

I have 2 questions:

1 - Why didn't Grub2 work? Since I started dual booting, I've only used Grub2 and it's always worked but why not in this case?

2 - If I want to add another distro would there be a complication if I used Grub 2 for one distro and Legacy for another?

---

### Post by nerdtron on 2013-04-16
1 - I haven't had any experience with EasyBCD since GRUB takeover everything at boot and manages all OS on my laptop. But have you looked at Boot Repair?
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
It can reinstall and update GRUB for you.
2 - Only one instance of GRUB2 is needed for boot. I mean, for example, Ubuntu installs it own GRUB 2. When you run sudo update-grub command it will scan all the OS that is installed in your PC and it will create a boot entry for it. You can also edit its own configuration file to add custom entries.

---

### Post by oldfred on 2013-04-16
I do not know EasyBCD. But it uses grub4dos as Windows does not multi-boot. It used to be that some with DRM licensed software had issues with grub2 in the MBR and they needed EasyBCD or other work arounds. But grub2 now writes around flexnet which is the main DRM software, so few have issues with grub2. Hibernation may be any issue but you really should not be hibernating with dual boot as that can cause file system issues.

Grub2 does not like to install to a partition which EasyBCD forces you to do. Then it has to use blocklists to find the rest of grub in root. Blocklists are hardcoded addresses, so updates my force a grub reinstall as old address then is not valid. Old grub legacy was smaller as it did not support as many features.

Some versions of grub legacy may not work with newer distributions. Ubuntu modified its version to work with ext4 but other vendors may not have. Grub2's os-prober finds most distributions and will directly boot them whether they have grub or grub2. Or you can manually create chain load entries like a Windows boot loader chain entry in grub2 to a grub legacy installed in a partition boot sector.

Best if having multiple installs to add a drive and have multiple MBRs, so you can have different boot loaders. 

The new UEFI while very complex with secure boot, offers an unlimited (only due to space) number of boot loaders in the efi partition. Each boot loader has its own folder and can be directly booted from that. No boot loader overwrites another. And you can more easily chain load from one to another with grub2.

---

