---
title: "Booted Lubuntu on External USB Disk, Next Windows 7 Boot Affected"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-05-29
I booted Lubuntu 14.04 installed on an external USB disk after attaching the disk to a Windows 7 64 bit computer.  The next boot of Win 7 was not normal with close to a minute of black screen but with working cursor before the desktop finally appeared.  Any theories on what might have caused this?   The USB disk was created on a 32 bit WinXP computer and generally used on that system.  Win 7 system has a brand new Gigabyte motherboard with UEFI capable BIOS but Secure Boot was not enabled for Win 7.

Here is the sequence.  Win 7 up and running and USB disk connected.  USB disk also has NTFS partitions which Windows recognized.  Restarted computer and entered BIOS to specify USB boot.  Boot starts and initially goes to Grub boot menu.  Lubuntu booted and ran fine and was then shut down with a restart.

Entered the BIOS again and removed the USB boot option.  Exited BIOS and Win 7 starts boot and goes to the login screen.  After proceeding wound up with a black screen and working cursor for nearly a minute before the desktop finally appeared.

Could the UEFI capable BIOS have done anything to modify the Win 7 boot?  Would running Lubuntu have had any impact on that next boot?

Thanks for any info.

---

### Post by sudodus on 2014-05-29
In old BIOS systems I would say, no, Ubuntu booted from an external drive should not tamper with the internal drive (unless you run some command on purpose). But UEFI is more complicated, and might be able to store something from the previous session, when you booted from an external drive. It could also be a delay due to a scheduled job to make the final changes for an update of Windows.

---

### Post by KAWill70 on 2014-05-29
> **sudodus said:**
> In old BIOS systems I would say, no, Ubuntu booted from an external drive should not tamper with the internal drive (unless you run some command on purpose). But UEFI is more complicated, and might be able to store something from the previous session, when you booted from an external drive. It could also be a delay due to a scheduled job to make the final changes for an update of Windows.
Thanks for the help.  I forgot to mention that the black screen problem remained and was not a one time event.

It was eventually fixed by removing several Windows updates dated 5/14 and then reinstalling them.  I can't believe the updates were actually the problem and wonder if just the process of removing updates, rebooting, reinstalling, and reconfiguring somehow cleaned up some boot related file.  As you know, Windows displays a message about reconfiguring Windows on the shutdown or reboot after installing or removing updates.  

The other interesting thing is that the amount of time the black screen was displayed was just about what you see during the Windows reconfiguring process.

If some file on the Windows disk was impacted, then you wonder if the BIOS code was somehow involved.  I wonder if either the BIOS or Windows detected the unknown and perhaps suspicious Linux boot and flagged it in some way.

---

### Post by KAWill70 on 2014-05-30
I had one other thought on this subject.  Every month Windows Update downloads an updated version of the Malicious Software Removal Tool.

Does anyone know if that file is kept around and run if any threat is detected?

That could explain the boot delay that I saw.  However, to do that something would have to prompt Windows to run the tool.  The issue may be whether the BIOS flagged the unknown Linux boot with EXT4 formatted drive as something suspicious.

---

