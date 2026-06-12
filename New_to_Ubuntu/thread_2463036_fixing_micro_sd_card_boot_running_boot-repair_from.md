---
title: "fixing micro sd card boot running boot-repair from ubuntu vm"
date: 2021-06-01
forum: New to Ubuntu
---

### Post by oifii on 2021-06-01
Hi All,

I ran raspberry pi imager to put my ubuntu vm (raw disk image) onto a micro sd card so I can boot my raspberry pi 4 model b with this precise ubuntu install.
("D:\Users\docte\VirtualBox VMs\KUbuntu-2004-64bit-remotedroide-dev3-vm.img")

Now, running boot-repair from my ubuntu vm, I need to fix the boot of this micro sd card that appears as:
Disk /dev/sdb: 495.12 GiB, 531629080576 bytes, 1038338048 sectors
/dev/sdb1  *       2048  1050623  1048576  512M  b W95 FAT32
/dev/sdb2       1052670 61929471 60876802   29G  5 Extended
/dev/sdb5       1052672 61929471 60876800   29G 83 Linux

I am not certain how to do it without changing the boot of the ubuntu vm that is on /dev/sda disk and appears as:
Disk /dev/sda: 30 GiB, 32212254720 bytes, 62914560 sectors
/dev/sda1  *       2048  1050623  1048576  512M  b W95 FAT32
/dev/sda2       1052670 61929471 60876802   29G  5 Extended
/dev/sda5       1052672 61929471 60876800   29G 83 Linux

Anyone has a clue for preventing boot-repair to do any change to /dev/sda disk?

Or an alternative to running boot-repair from my ubuntu vm for repairing the boot of /dev/sdb disk only?

Here's my actual boot-repair summary info [https://paste.ubuntu.com/p/zQXrm4k3K8/](https://paste.ubuntu.com/p/zQXrm4k3K8/) 

Regards,

Steph

---

### Post by TheFu on 2021-06-02
It appears that sda and sdc are clones. They have the same UUIDs.  This cannot remain. It is confusing the system.
There is no way that grub-386 will ever be used on a raspberry pi.  ARM CPUs are not i386 compatible.  It just doesn't work that way. No programs compiled for x86 CPUs will work on ARM without a CPU virtualization layer - like a VM.

I wouldn't expect boot-repair to work on any ARM system today. ARM doesn't boot the same way that x86 boots. No EFI. No BIOS, well, not really.

When you say "precise ubuntu" - do you mean "exactly ubuntu" or the Ubuntu codename for 12.04 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) which hasn't been supported since 2017?  Also, to my knowledge, there was no 12.04 that worked on any ARM CPU.

---

