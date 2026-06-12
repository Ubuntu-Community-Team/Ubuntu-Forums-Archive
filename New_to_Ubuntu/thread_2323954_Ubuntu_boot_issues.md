---
title: "Ubuntu boot issues"
date: 2016-05-09
forum: New to Ubuntu
---

### Post by caden3 on 2016-05-09
I am new to Ubuntu and am having issues reliably booting into the system. I have deleted Windows 10 and installed whatever the newest Ubuntu is as of 5/9/16. 
My issues is whenever I turn on my computer I get [h=1]Reboot and select proper boot device. Or insert boot media in selected boot device and press a key.[/h]A *temporary* fix I have got is to put the boot-repair media on a USB drive and run boot repair every boot. This allows me to open grub and select Ubuntu to boot in. After that if I restart the PC again, it gives me the same error. The boot-repair link I got is:
[http://paste.ubuntu.com/16324286/](http://paste.ubuntu.com/16324286/)

Any help is greatly appreciated.

---

### Post by oldfred on 2016-05-09
It says you have UEFI secure boot on, so surprised it boots at all.
BIOS boot should not work with Secure boot on.

You show a bios_grub partition, but formated FAT32 and grub installed to gpt's protective MBR for BIOS boot, but it also says no core.img in the bios_grub partition. So not correctly repaired for BIOS boot.
A bios_grub partition is normally 1 or 2MB **unformatted** for BIOS boot. It has bios_grub flag.
And an ESP - efi system partition is **FAT32 formatted with boot flag**. Windows is often 100MB, but we suggest larger like 300MB or more.
It may be possible to have both BIOS & UEFI, but you need both a bios_grub & an ESP as separate partitions.

But your fstab shows a mount of the ESP. So install was UEFI, but without ESP grub did not install in UEFI boot mode.

Which do you prefer UEFI or BIOS? You do need to be consistent and always boot Ubuntu & flash drive installers in the same mode all the time.
Boot-Repair says it was booted in UEFI mode.

I would change sda1 from bios_grub to ESP by changing flag to boot flag with gparted on live installer.
Then use Boot-Repair to install the UEFI version of grub. No need to erase grub in MBR, but it will never work and just give errors if you attempt to boot in BIOS mode.

Since you only have Ubuntu, what brand/model system. Some have no issue booting Ubuntu UEFI entry. Others modify UEFI to only boot Windows entry and we have to do work arounds.

---

### Post by caden3 on 2016-05-09
I have changed the flag, installed *probably improperly* grub with boot-repair and disabled secure boot in my BIOS or UEFI or whatever comes up when I hit Delete when booting.
I then re-booted and it booted to grub and then to Ubuntu just fine.
I rebooted for the second time just to test it and got the same error as before.
I used my boot-repair USB and got [http://paste.ubuntu.com/16324871/]("http://paste.ubuntu.com/16324286/")
Then I rebooted and Ubuntu loaded fine again, where I am now typing this message. If I where to reboot right now I am guessing I would get Reboot and select proper boot device.

---

### Post by oldrocker99 on 2016-05-09
> **caden3 said:**
> I have changed the flag, installed *probably improperly* grub with boot-repair and disabled secure boot in my BIOS or UEFI or whatever comes up when I hit Delete when booting.
I then re-booted and it booted to grub and then to Ubuntu just fine.
I rebooted for the second time just to test it and got the same error as before.
I used my boot-repair USB and got [http://paste.ubuntu.com/16324871/]("http://paste.ubuntu.com/16324286/")
Then I rebooted and Ubuntu loaded fine again, where I am now typing this message. If I where to reboot right now I am guessing I would get Reboot and select proper boot device.

My MSI motherboard needed me to select my SSD to boot from it, but I only had to do that a couple or three times, and it's booted properly ever since. Be patient.

Also, since you appear to have fixed your problem, please add [SOLVED] to the thread title, using Thread Tools.

---

### Post by caden3 on 2016-05-09
Also, when I reboot and hit DEL, it says Windows Boot Manager is my 1st option.

---

### Post by oldfred on 2016-05-09
I do not see any changes in new report.

It still shows sda1 as bios_grub. It needs to have boot flag, not bios_grub flag. Use gparted to change flag. 
What brand/model system?

This is what you show which is neither a bios_grub for BIOS boot nor an ESP/FAT32 with boot flag partition. It has to be one or the other.

```
 sda1: ______________________________________

 File system:       BIOS Boot partition
Boot sector type:  FAT32
Boot sector info:  


```

---

