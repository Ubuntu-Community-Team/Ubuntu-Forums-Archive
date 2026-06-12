---
title: "&quot;Invalid EFI Path&quot;--Dual Boot Windows 8/8.1 and Ubuntu 12.04 lts."
date: 2013-12-15
forum: New to Ubuntu
---

### Post by sgrshknd on 2013-12-15
I had Windows 8.1 installed and I tried Ubuntu 13.10 with '***something else***' option during Ubuntu installation but that caused me hell lot of problems such as graphics issue and i ended up losing all my files, my android projects etc.
So I used TestDisk to recover few of them important files and started afresh with Windows 8 and Ubuntu 12.04 LTS.

I installed Windows 8 and using '***alongside it***' option of Ubuntu installation i installed Ubuntu 12.04 LTS with no problems in installation whatsoever.
Windows  8 booted well before Ubuntu installation but after installation it I get this error  '***Invalid EFI path***' whenever I select Windows 8 from Grub 2 menu at  startup.
Now I am new to Ubuntu and I might have done things horribily wrong.

Things I have tried are : _**Boot-Repair**_ and **_Refind_** boot manager.
I used '***recommended repair***' option of Boot-repair.
Here is the link to Boot-Repair ***logfile***.
[http://paste.ubuntu.com/6577981/](http://paste.ubuntu.com/6577981/)

In refined i couldn't see my windows just 5 options all with photos of Ubuntu and different things written below them.

Some errors i get in between are --- something along the lines of '***ramdisk error***' during startup and '***cannot write bytes - pipeline*** something' just before Ubuntu login page.

Also if relevant   ----  I use Hp pavilion 15e034tx laptop with i5 3230, 4 gb ram, 500 gb WD hdd, AMD Radeon 8670m.

Can anyone tell me what is wrong? I need guidance.

Thanks.

---

### Post by sgrshknd on 2013-12-15
This is my reply to my above post with partial solution.
Something pretty strange is going on. Somehow I have '**CLONED**' my hard disk with Windows on 1 hard drive and Ubuntu on second or cloned drive.
Let me explain in details.
Ever since I did my first gig of dual booting Windows 8.1 with Ubuntu 13.10 I started seeing my drive twice in BIOS Boot Order. I was confused totally.
Now in Ubuntu I opened couldn't see my partitions where window was installed and another partition with some files. So I again opened TestDisk and was shell-shocked to see that my partitions are available for re-writing even without searching for a second. 
So I selected my partitions and clicked on '**write' **option of TestDisk and rebooted.
Now what happened was that I booted straight into Windows with all my partitions back.

Totally blasted my mind with all of this. Someone, anyone please look into it.

---

### Post by oldfred on 2013-12-15
I see Windows efi files in sda1 and refind & Ubuntu efi files in sda5. Both say they are efi partitions. But  you can only have one efi partition per hard drive.
Copy all efi folders from sda5 to sda1 and with gparted take boot flag off of sda5 or use gdisk to change its partition type.
sudo apt-get install gdisk
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


Do you have Windows still hibernated or fast boot on. That always causes issues. It does not look like Windows partition is mounted and Linux NTFS driver will not mount NTFS partitions that are hibernated or need chkdsk. If you resized NTFS partition it also may need chkdsk which you can only do with Windows or Windows repairCD or flash drive.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by sgrshknd on 2013-12-15
I don't what have I done. I have reinstalled windows a number of times.
I still can see efi gpt partition. Is that normal. Also I installed windows 8 without efi and secure boot was disabled. But installed Ubuntu in efi mode.
Maybe that is what caused all these issues.
What I am doing now is run chkdsk using windows recovery and will try installing ubuntu without efi next time. Lets see what happens

---

### Post by oldfred on 2013-12-15
You do need to install both system in the same mode, either both BIOS or both UEFI.
Windows (and Ubuntu) only boots with BIOS from MBR drives, but Windows does not correctly convert a gpt drive to MBR. You have to use fixboot to remove the backup gpt partition table.
Windows only boots from gpt partitioned drives with UEFI.
Ubuntu will boot from a gpt partitioned drive with either UEFI or BIOS, and from UEFI menu how you choose to boot installer UEFI or BIOS is the boot mode it installs in.
Not sure if forcing install in wrong configuration works. 

It looks like drive is still gpt so Windows must be in UEFI mode. Then I would not install Ubuntu in BIOS mode.
But you need to undo the two efi partition issue.

---

### Post by sgrshknd on 2013-12-15
I have totally formatted my drive and have not efi gpt partition left.Then i installed windows 8 and formatted the drive in ntfs. Also i made 3 different partitions while installing windows. 
Now when i try to install Ubuntu i am unable to find my Windows and dont get the option to install ubuntu alongside windows.
Also in gparted i cant see my partitions and can only see a large chunk of unallocated space 465 gb in size which is the size of my hard disk.

---

### Post by mkmanifesto on 2013-12-15
If you have nothing on the hard drive that you need at this point I would blast the drive with Mengis boot 98.

PM me if you want it. It's only a 2.8mb iso that needs to be burned out to a bootable disc.

---

### Post by oldfred on 2013-12-15
If you install Windows in BIOS boot mode over a gpt partitioned drive, it converts it to MBR. But does not do it correctly. You have to also delete the backup gpt partition table.

       
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Then Ubuntu installer will not get confused on whether drive is really MBR or gpt. Be sure to boot installer in BIOS mode not UEFI mode. You want purple accessibility screen as show here:

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

In BIOS mode you use any key on tiny icons at bottom of screen and then f6 to add boot parameters.

---

### Post by sgrshknd on 2013-12-16
Below is the reason which caused all trouble.

> **oldfred said:**
> If you install Windows in BIOS boot mode over a gpt partitioned drive, it converts it to MBR. But does not do it correctly. You have to also delete the backup gpt partition table.

I installed Windows in BIOS and Ubuntu in EFI.

       > **oldfred said:**
> 
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Then Ubuntu installer will not get confused on whether drive is really MBR or gpt. Be sure to boot installer in BIOS mode not UEFI mode. You want purple accessibility screen as show here:

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

In BIOS mode you use any key on tiny icons at bottom of screen and then f6 to add boot parameters.

Thats it.  This --->[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)<--- is what I was looking for.
FixParts totally removed stray GPT partitions that I wasn't even able to see normally in windows.
And now I have **successfuly dual-booted Windows 8 and Ubuntu 12.04 LTS** on my laptop.
Thanks *mkmanifesto* for trying too help, but ***special thanks and appreciation to [[COLOR=#b22222]oldfred [/COLOR]]("http://ubuntuforums.org/member.php?u=852711")***[COLOR=#000000]for valuable guidance and constant replies.

I would also like to write a simple guide on dual-booting without any fuss for first-timers so that no one else end up loosing GB's of data like me.

Regards
Sagar.
[/COLOR]

---

### Post by oldfred on 2013-12-16
Glad you got it working. :)

The issue of UEFI with gpt partitioning and secure boot and BIOS with MBR partitioning has complicated installs a lot. Uers now have to learn which they have, which mode they boot in, and usually make several settings in UEFI/BIOS to set boot modes.
It used to be just BIOS with MBR and then it was "relatively" simple. Or was in hindsight compared to now.

---

