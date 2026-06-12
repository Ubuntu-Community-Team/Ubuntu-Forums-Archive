---
title: "No boot from new disk"
date: 2016-03-20
forum: New to Ubuntu
---

### Post by aray81 on 2016-03-20
Howdy.  I'm new to Linux and am trying to install 14.04 to a new disk but can't get it to boot.
I have Windows 10 on one disk and I installed 14 to a new disk. Windows sees the new disk and partitions in disk management.
In the bios I have disabled quick boot, rapid boot and secure boot.
Here is the problem:
I disable CSM and the only boot choices shown are the Windows disk and then below that it lists just the word Ubuntu then the same Ubuntu again and then my dvd drive. If I select either of the Ubuntus it boots to windows.
If I enable CSM and choose UEFI only I get as my boot choices the Windows disk, the Ubuntu disk and the dvd drive.  When I select the Ubuntu disk I get the message: Error 1962  No Operating System found.

I'm sure I have done something incorrectly and need y'all's guidance.

Thanks!

---

### Post by oldfred on 2016-03-20
What brand/model system?
Some systems need work arounds to boot Ubuntu.

Best to manually partition second drive with gpt and include an ESP - efi system partition.
But it may not be used in UEFI boot mode as grub with Ubuntu defaults to install to ESP on sda.
And then use Something Else to choose / (root) partition already created.

You want Ubuntu & Windows in same boot mode, either both UEFI or both BIOS.
Make sure Windows fast start up is off.

If already installed:
 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by aray81 on 2016-03-20
Thank you for the reply.

I'm running a Lenovo Ideacenter K410 with a first gen i7.

Here is the link for the Create Boot Info summary report:

[http://paste.ubuntu.com/15440596/](http://paste.ubuntu.com/15440596/)

---

### Post by oldfred on 2016-03-20
You have Ubuntu installed to MBR of sda for BIOS boot, but do not have the required 1 or 2MB unformatted partition with the bios_grub flag for grub to install correctly.
You also have Ubuntu installed for UEFI boot in sda1 and Windows UEFI boot files in sdb2 which should work.
But UEFI is only showing a BIOS boot option for ubuntu.

I would run Boot-Repairs suggested fix to reinstall grub-efi-amd64 for UEFI boot.
If then that UEFI boot entry does not work, we have to do a work around for booting Ubuntu in UEFI mode.
Several alternative work arounds are in link in my signature, if you want to read ahead.

If Boot-Repair does not work post link to new Summary report after it has run.

---

### Post by aray81 on 2016-03-20
Boot Repair made the necessary correction and all seems fine.

Thank you for your quick responses and info.

Now the learning begins.

---

