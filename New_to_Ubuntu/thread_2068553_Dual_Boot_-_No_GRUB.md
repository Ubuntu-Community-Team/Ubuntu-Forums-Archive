---
title: "Dual Boot - No GRUB"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by vinu_shukl on 2012-10-09
[LIST]
[*]I have Windows 7 installed in a primary partition and wanted to install Ubuntu 12.10 in a new partition. 
[*]Even before starting the installation, I knew that I might run into a few problems because the partition I was installing Ubuntu on was displayed **before** the W7 partition in the Disk Manager of Windows.
[*]After the install, I didn't get a GRUB menu on reboot but was directly booted into W7.
[*]A used a LiveUSB to boot into Ubuntu (Try Ubuntu) and ran the BootRepair software with the recommended settings. It showed an unsuccessful, [the result]("http://paste.ubuntu.com/1269285/").
[*]Now, I'm still directly booting to W7, but have access to the LiveUSB. Can someone guide me on how to have GRUB displayed on boot?

[*] Ran BootRepair again with Advanced settings...the [new results]("http://paste.ubuntu.com/1269349/")
[/LIST]

---

### Post by NikTh on 2012-10-09
> **"http://paste.ubuntu.com/1269285/"]

Reinstall the GRUB of sda1 into the MBR of sda /usr/sbin/grub-bios-setup: warning: **this LDM **has no Embedding Partition said:**
>  option.

I am not very sure , but I think Grub is incapable to read LDM partitions.

Also , this bug exits : [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1053793](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1053793)

not confirmed yet , but maybe has a relation to your problem. 

What I suggest ? 
To install syslinux instead of Grub. (until Grub BE capable to manage such partitions).

Thanks

---

### Post by vinu_shukl on 2012-10-09
Should I follow these instructions to install syslinux ?

[http://shallowsky.com/linux/extlinux.html](http://shallowsky.com/linux/extlinux.html)

---

### Post by oldfred on 2012-10-09
Boot-Repair will install syslinux if you just want to boot Windows.

But you installed grub2's boot loader to the MBR of sda1, a partition. You need to install grub2's boot loader to sda the drive. Boot Repair will do that.

---

