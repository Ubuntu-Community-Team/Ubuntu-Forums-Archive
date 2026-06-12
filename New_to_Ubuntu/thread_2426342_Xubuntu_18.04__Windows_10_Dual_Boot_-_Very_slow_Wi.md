---
title: "Xubuntu 18.04 / Windows 10 Dual Boot - Very slow Windows boot"
date: 2019-09-07
forum: New to Ubuntu
---

### Post by numblat1 on 2019-09-07
[COLOR=#1A1A1B][FONT=&quot]I have installed Xubuntu 18.04 on a Asus ROG GL702VS laptop alongside Windows 10 on a 500GB SSD.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]Everything behaves/runs normally and Xubuntu boots extremely quickly however Windows 10 takes 30-45 seconds to boot and appears to freeze several times through the process. Once booted Windows runs normally.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]To solve this issue I have turned of Fast Boot but with no apparent change.[/FONT][/COLOR]

---

### Post by Autodave on 2019-09-07
I am assuming that you are running both OS on the same hard drive?  Fast boot should be turned off.  Understand that Win10 does not shut down as you think it does: it merely hibernates.  To have both installs on the same HD Win10 had to have had fast boot disabled in order for the installer to have access to the drive.  If Win is just hibernated, then the installer will not work since Win10 has control of the entire drive because it is only "hibernated".

---

### Post by mastablasta on 2019-09-10
45 secs is reasonable. though maybe not if you have SSD. i have this time on my 15 year old PC on linux with HDD. windows xp boots in about 10 minutes.
my work PC (i3 with HDD) has windows 10 installed and also takes a few minutes to boot.

---

### Post by oldfred on 2019-09-10
Windows boots slowly.
Part of work around to make it faster was to require new UEFI to skip its check of system for what hardware you have and write that to drive and just assume everything is the same. That is UEFI fast boot.
And part of work around is to automatically turn on hibernation (at least the boot part). That is called fast start up in Windows. But since that sets the hibernation flag on all NTFS partitions, the Linux NTFS driver will not automount the NTFS read/write. So that normally has to be off. Windows is known to turn it back on with updates, so if expecting to read/write NTFS shared data partition and it stops that may be the cause.

My old XP used to take 5 minutes to boot when Ubuntu took 40 sec. 
I ran chkdsk and it improved. Then I ran chkdsk from a Windows 7 repair disk and got boot down to 3 minutes.
I had to fix XP as the chkdsk from XP made it think it wanted to boot 7 and had to restore partition boot sector to boot XP.

Try running chkdsk on all NTFS partitions.

---

### Post by mastablasta on 2019-09-11
> **oldfred said:**
> 
Try running chkdsk on all NTFS partitions.

that + defragment the NTFS drive.

---

