---
title: "Problem with dual boot setup"
date: 2022-04-20
forum: New to Ubuntu
---

### Post by freddieke on 2022-04-20
Hi everyone

I recently set up my laptop to dual boot Ubuntu by using a flash drive. This worked fine for several days until the boot stopped working and I was met with the GRUB screen upon start up.

I followed the steps here ([https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot/330852#330852](https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot/330852#330852)) to try and identify the boot config file, but without success. 

I then followed the boot repair steps here ([https://www.linux.com/training-tutorials/how-rescue-non-booting-grub-2-linux/](https://www.linux.com/training-tutorials/how-rescue-non-booting-grub-2-linux/)) by using the flash drive and running the recommended repair, but this did not solve the issue on restart. The paste bin I was given was [https://paste.ubuntu.com/p/ybYZV9CbJH/](https://paste.ubuntu.com/p/ybYZV9CbJH/).

Please could someone help me on what else to try? I'm happy to provide more info if need be.

---

### Post by oldfred on 2022-04-20
Lines 127 & 128 show Linpus Lite as default boot? And UEFI boot entry for a MBR(msdos) drive?
UEFI usually is gpt partitioned as your NVMe & sda drives are.
You only have one ext4 partition for Linux, sda4.
But UEFI boot entry grub.cfg in NVMe ESP looks for an UUID that does not exist?

Did you delete some partitions?
Did you install Linpus Lite?
Cannot tell what you have, but it does not look like you can just fix it. But what is sda4?
Best to reinstall & restore from your backups.

---

### Post by grahammechanical on 2022-04-21
> Lines 127 & 128 show Linpus Lite as default boot?

On my laptop the UEFI settings utility sees the Ubuntu USB memory stick as having Linpus Lite on it. I suspect that If I booted into a Ubuntu live session and installed Boot Repair and run the summary option it would should the first boot option as Linpus Lite.

I am just trying to avoid confusion distracting us.

Regards

---

