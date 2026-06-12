---
title: "Install Grub"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by uchihaitachi on 2008-08-19
Post Edited to reflect current status / Added Information

I'm having trouble installing grub.

Current setup

Vista Loader > Vista NTLDR > ?? Can't install grub?? > Ubuntu

1 disk 3 partiions
dev/sda1 - Windows
dev/sda2 - Linux (Installed without installing grub bootloader)
dev/sda3 - Data

I have omitted a swap partition as I have 4GB RAM and I'm not willing to give up 8GB of HDD space for swap.

I would like to install Grub to partition 2 but I've always encountered errors. Could somebody guide me through what I can do?

Following Pro-reason's guide
When I type
find /boot/grub/stage1
I get Error 15: File not found

Moving on...
sudo /sbin/grub-install /dev/sda2

I get the error:
sudo: unable to resolve host ubuntu
sudo: /sbin/grub-install: command not found

If I apt-get grub
sudo: unable to resolve host ubuntu
You shouldn't call /sbin/grub-install. Please call /ur/sbin/grub-install instead!
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for boot: Not found or not a block device.

If I type
grub-install /dev/sda2
Could not find device for /boot: Not found or not a block device

I am getting the above errors from a live cd as I'm unable to boot into Ubuntu.

PS I have been able to boot into Ubuntu when installed with Wubi. However I'm looking for a true installation with ext3 and hibernation support etc.

---

### Post by Pro-reason on 2008-08-19
Have you looked at [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")?

---

### Post by satir.satir on 2008-08-19
and this :
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by uchihaitachi on 2008-08-19
Since I would like to preserve the Windows bootloader.

When I type
find /boot/grub/stage1
I get Error 15: File not found


Moving on...
sudo /sbin/grub-install /dev/sda2

I get the error:
sudo: unable to resolve host ubuntu
sudo: /sbin/grub-install: command not found

If I apt-get grub
sudo: unable to resolve host ubuntu
You shouldn't call /sbin/grub-install. Please call /ur/sbin/grub-install instead!
Probing devices to guess BIOS drives. THis may take a long time.
Could not find device for boot: Not found or not a block device.

---

### Post by dstew on 2008-08-19
Are you sure you have completely installed Ubuntu on the second partition? If not, then of course the grub shell from the Live CD cannot find /boot/grub/stage1. Is it possible that you aborted the installation?

---

### Post by caljohnsmith on 2008-08-19
> **uchihaitachi said:**
> I'm having trouble installing grub.

Current setup

Vista Loader > Vista NTLDR > ?? Can't install grub?? > Ubuntu

1 disk 3 partiions
dev/sda1 - Windows
dev/sda2 - Linux (Installed without installing grub bootloader)
dev/sda3 - Data

I would like to install Grub to partition 2 but I've always encountered errors. Could somebody guide me through what I can do?
When you say you get errors installing grub, exactly what errors do you get? That would greatly help in troubleshooting your problem. Also, from what you posted above, it doesn't appear you have a swap partition--any special reason you didn't set up swap partition? Or are you planning on setting up a swap file within your Ubuntu partition? 
> **uchihaitachi said:**
> 
Since I would like to preserve the Windows bootloader.

When I type
find /boot/grub/stage1
I get Error 15: File not found


Moving on...
sudo /sbin/grub-install /dev/sda2

I get the error:
sudo: unable to resolve host ubuntu
sudo: /sbin/grub-install: command not found

If I apt-get grub
sudo: unable to resolve host ubuntu
You shouldn't call /sbin/grub-install. Please call /ur/sbin/grub-install instead!
Probing devices to guess BIOS drives. THis may take a long time.
Could not find device for boot: Not found or not a block device.

Is this from a Live CD I presume, or did you manage to boot into Ubuntu on your HDD? You shouldn't see those kind of sudo errors from a Live CD--usually you get those kind of errors if the host name does not agree in both /etc/hosts/ and /etc/hostname.

---

### Post by uchihaitachi on 2008-08-19
I am getting those errors from running those commands in a live cd.
I've done without the swap partition as I believe I've sufficient RAM 4GB.

---

### Post by uchihaitachi on 2008-08-20
Does anybody know how Wubi managed to get the bootloading part correct?

---

