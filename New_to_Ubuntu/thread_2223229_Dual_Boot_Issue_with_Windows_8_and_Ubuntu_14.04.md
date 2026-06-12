---
title: "Dual Boot Issue with Windows 8 and Ubuntu 14.04"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by recalm on 2014-05-10
I recently upgraded from Ubuntu 13.04 to 14.04 and was unable to see Windows 8 in Grub. I used Boot Repair disk and attempted to fix the issue, but it made the problem worse as I couldn't boot into either OS. I found a solution that allowed me to boot straight into Windows 8, but now I cannot get back into Ubuntu and I'm afraid if I try to repair Grub with the Boot Disk I'll end up with the same problem. Can someone please help me?

Boot Info Summary: [http://paste.ubuntu.com/7444673/](http://paste.ubuntu.com/7444673/)

---

### Post by oldfred on 2014-05-10
Post link to BootInfo summary.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What computer, model & video card/chip?

---

### Post by recalm on 2014-05-10
> **oldfred said:**
> Post link to BootInfo summary.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What computer, model & video card/chip?

Custom built PC with Intel i5 2500K on ASRock Z68 Pro3 board and MSI Twin Frozr III 7870

Boot Info Summary: [http://paste.ubuntu.com/7444673/](http://paste.ubuntu.com/7444673/)

---

### Post by oldfred on 2014-05-10
Do not run any auto fix from Boot-Repair as that just puts the grub2 boot loader into the MBR of every drive. You want to keep the Windows boot loader in the MBR of sda, so you can directly boot it if grub entry is not working.
You should be able to use the advanced mode in Boot-Repair and choose Ubuntu and choose drive that is sdb.

Did you turn off fast boot or the always on hibernation in Windows 8? You cannot boot from grub with that on.

Note on line 445, that your boot files are scattered all over drive. A few BIOS do not like boot files beyond 137GB. Mostly an issue with USB drives or really old systems. Is BIOS set for AHCI not IDE?
The IDE setting may emulate the old issue.

I prefer smaller / (root) partition of 20 or 25GB and large /home or data partition for the rest of the drive.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Your system is new enough to have UEFI, but Windows is in BIOS mode and Ubuntu is also in BIOS mode. Do not boot Boot-Repair in UEFI mode as it says you did for BootInfo report. You just need to be consistently BIOS boot unless you want to convert entire system to UEFI boot. But then really good backups would be required.

---

### Post by recalm on 2014-05-10
> **oldfred said:**
> Do not run any auto fix from Boot-Repair as that just puts the grub2 boot loader into the MBR of every drive. You want to keep the Windows boot loader in the MBR of sda, so you can directly boot it if grub entry is not working.
You should be able to use the advanced mode in Boot-Repair and choose Ubuntu and choose drive that is sdb.

Did you turn off fast boot or the always on hibernation in Windows 8? You cannot boot from grub with that on.

Note on line 445, that your boot files are scattered all over drive. A few BIOS do not like boot files beyond 137GB. Mostly an issue with USB drives or really old systems. Is BIOS set for AHCI not IDE?
The IDE setting may emulate the old issue.

I prefer smaller / (root) partition of 20 or 25GB and large /home or data partition for the rest of the drive.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Your system is new enough to have UEFI, but Windows is in BIOS mode and Ubuntu is also in BIOS mode. Do not boot Boot-Repair in UEFI mode as it says you did for BootInfo report. You just need to be consistently BIOS boot unless you want to convert entire system to UEFI boot. But then really good backups would be required.

I'm not familiar with the system end of things. I pretty much followed guides that I found through google at an attempt to fix the problems without knowing what I was actually doing to it. Probably explains why you found those issues, lol. I assumed UEFI boot was the term for booting through the USB drive. That's how it was labelled through the boot menu of the BIOS.

As for Windows hibernation/fast boot. I don't recall messing with any of those options, but Windows 8 does boot a lot faster than when I was running Windows 7. I'll try to see if I did turn those options on.

I'm pretty much screwed on backups, I don't have enough external space to hold everything.

> You should be able to use the advanced mode in Boot-Repair and choose Ubuntu and choose drive that is sdb.

I will try this and report back. Thank you for all your help!

---

### Post by oldfred on 2014-05-11
If Windows is hibernated or still has fast boot on, you have to in BIOS boot directly from sda. Grub will not boot a hibernated Windows.
Then when you turn that off, you can set BIOS to boot sdb by default and grub should have both Ubuntu & Windows in boot menu that will work.

If you want you can use your systems one time boot key often f12, but varies by vendor to chose which system to boot. Then you may be able to keep the fast boot on. But since hibernated you will not be able to read the NTFS partition from Ubuntu. And never attempt to write into a NTFS partition that is hibernated as data will just be lost.

---

### Post by recalm on 2014-05-13
> **oldfred said:**
> If Windows is hibernated or still has fast boot on, you have to in BIOS boot directly from sda. Grub will not boot a hibernated Windows.
Then when you turn that off, you can set BIOS to boot sdb by default and grub should have both Ubuntu & Windows in boot menu that will work.

If you want you can use your systems one time boot key often f12, but varies by vendor to chose which system to boot. Then you may be able to keep the fast boot on. But since hibernated you will not be able to read the NTFS partition from Ubuntu. And never attempt to write into a NTFS partition that is hibernated as data will just be lost.

Not sure what I'm doing wrong, but the Grub menu isn't showing up. I installed it on sdb and set the BIOS to sda and when that didn't work I switched it to sdb to be sure, but it still booted straight into Windows.

Here is the Boot Info summary: [http://paste.ubuntu.com/7457275/](http://paste.ubuntu.com/7457275/)

---

### Post by oldfred on 2014-05-13
System will not boot Windows from sdb. Only if it does not see a boot file in MBR of sdb, then if you have sda as next in BIOS boot order would it then auto change to boot sda.
Windows will only boot from sda.

Are you sure you are updating the grub in sdb and not sdb1?
 You also have grub installed to sdb1, which will never be used.

IF you unplug one drive or the other does it boot each separately?

---

### Post by recalm on 2014-05-27
> **oldfred said:**
> System will not boot Windows from sdb. Only if it does not see a boot file in MBR of sdb, then if you have sda as next in BIOS boot order would it then auto change to boot sda.
Windows will only boot from sda.

Are you sure you are updating the grub in sdb and not sdb1?
 You also have grub installed to sdb1, which will never be used.

IF you unplug one drive or the other does it boot each separately?

Sorry it took me so long to get to this. I tried the above and disabled hibernation in Windows 8.1 using the powercfg -h off but it still boots straight into Windows. Would it be possible to install Ubuntu 13.04 (previously working) on a partition and then copied my files over then delete the old Ubuntu 14.04 partition? Thank you for your advice.

---

### Post by oldfred on 2014-05-27
In my 640GB drive I must have 10 installs of mostly Ubuntu. Many obsolete, several current and one Utopic 14.10.
So you can just create another 20 or 25GB / partition, install and boot that.
I do have all data in separate /mnt/data partition(s) so I can use the same data in all installs, but have differnt user configurations.

---

