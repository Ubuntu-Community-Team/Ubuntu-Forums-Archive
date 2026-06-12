---
title: "Ubuntu boot loader not working"
date: 2018-01-30
forum: New to Ubuntu
---

### Post by sujal24 on 2018-01-30
I have tried multiple times but my grub is not loading properly.
I have also tried installing using boot-rescue but that also didn't work. Please help
Boot-rescue log file:-
[https://paste.ubuntu.com/26492952/](https://paste.ubuntu.com/26492952/)

---

### Post by yancek on 2018-01-31
You have Grub boot code in the MBR which should not be there as you are using an EFI system and it looks to the EFI partition (sda1) for boot files for windows and Ubuntu.

Your grub.cfg (boot menu file) shows only the Recovery partition for windows (sda7).  Try running "sudo update-grub" (without quotes) from an Ubuntu terminal.  Watch the output for another entry.
When you boot, you should see boot options and there should be an entry for windows or an option for 'boot from EFI file', select that and look for a windows option.

---

### Post by oldfred on 2018-01-31
It looks like you may have installed Ubuntu's boot loader grub to MBR at some point.
But you now show ubuntu/grub boot files in the ESP - efi system partition and the mount of the efi in fstab. So now configured for UEFI boot.

You show 16.10 which has now expired. Use 16.04.3 or 17.10 versions.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Only use Something Else install option and choose (change button) same / (root) as new / partition.
        [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
See also link below in my signature for more info on UEFI install.

But HP violates UEFI standards. 
UEFI says NOT to use description as part of boot. And of course the only valid description is "Windows Boot Manager". Various work arounds depending on configuration.
For dual boot the fallback or hard drive boot entry often works. Boot-Repair will create the file in the ESP with this option.,
 fix-windows-boot use-standard-efi-file 
That copies shimx64.efi to /EFI/Boot/bootx64.efi and backs up the current bootx64.efi which is usually just a copy of the Windows .efi boot file.

---

### Post by haplorrhine on 2018-01-31
> **oldfred said:**
> Boot-Repair will create the file in the ESP with this option.

*Boot-repair* solved my Grub troubles in the past! :KS

---

