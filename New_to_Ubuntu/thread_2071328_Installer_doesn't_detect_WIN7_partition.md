---
title: "Installer doesn't detect WIN7 partition"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by arcsin on 2012-10-15
I'm trying to install ubuntu alongside windows 7 but the installer doesn't recognise the windows partition.

In windows I used the disk management tools to shrink my C: and then left the free space unallocated.

I then tried to install ubuntu using a usb stick, however it only gives me the options to completely wipe the hdd or customise the partitions (However when I go into the custom partitions it just shows the whole 1tb drive as being empty)

So I tried googling for a solution and found several different solutions (run chkdsk in windows, remove dmraid) and I have tried both of these but ubuntu still doesn't see the windows partition.

If I run sudo os-prober from terminal it outputs:

/dev/sda1:Windows 7 (loader):Windows:chain

I've also ran boot-repair and the paste is located here: [http://paste.ubuntu.com/1280830/](http://paste.ubuntu.com/1280830/)

---

### Post by NikTh on 2012-10-15
Hi , 

take a look at the warning here [quote="Boot info"]
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?[/quote]

I focus on that , but I cannot provide another solution more reliable than reinstall Windows.  Maybe a /fixmbr and /fixboot from Windows Repair DVD can do the job ,without reinstall them. If you want follow the guide [here](http://ubuntuforums.org/showthread.php?t=2066474) in 2nd post to restore the mbr in Windows and then try again to install Ubuntu. 

You can wait for someone with better idea. 

I guess that you corrupted the GPT signatures by modifying the partition in Windows. 

Thanks

---

### Post by aabed91 on 2012-10-15
when i install ubuntu i leave some free space unlocated .

but it's refuse to install alongside windows

finally, i discover that the free space should leaved in the last of the partitions.
if it's between tow partitions the Ubuntu can't discover this space i don't know why

---

### Post by oldfred on 2012-10-15
Drive was partitioned as gpt, but Windows only installs to gpt partitioned drives if using the new UEFI not BIOS to boot. So Windows converts gpt back to MBR to install in BIOS mode.

Gpt has a backup partition table at the end of the drive. Windows does not reformat that backup. But Linux tools see both MBR and gpt backup and get lost, not sure if it should be gpt or MBR.

First backup partition table from terminal in liveCD. copy parts.txt to some other drive, flash drive etc.
sudo sfdisk -d /dev/sda > parts.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

