---
title: "failed secondary hard drive"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by wireman on 2008-05-07
Secondary hard drive containing backups has failed(stopped spinning).

The set up :-

80GB IDE with 3 partitions WinXP/software/store

320GB SATA with 5 partitions (from what I can remember)Ubuntu 7.10?/swap/fat32 store/ntfs store/ntfs backups 


All happily working using grub for dual boot.
Norton Ghost recently reported unable to access on a few occasions then seemed ok.
Suddenly this week, grub error 1.5 etc. unable to boot to anything.
After lots of searching for solutions and trying various things, decided to go with the following as all my university work on XP drive is essential.
Disconnected SATA and had to restore mbr to primary drive, now have access to it. (phew)
If SATA is connected XP won't boot. Then discoversd SATA was not spinning. In desperation, moved from gentle tap to 6" drop on hard surface. Success, drive now runs but have no idea how long for. Plugged it back in, grub error 1.5 etc.
Booted from Ubuntu DVD, no success restoring grub so re-installed to original partition. Grub menu now shows but will not boot to XP, booted to Ubuntu. 
Primary drive with XP is visible and accessible.
NTFS partitions on SATA give something like "device not cleanly unmounted" so are not accessible. There was an option to force mount but wasn't too sure if data would be lost.
Qtparted shows all partitions on SATA.

I want to get all files I can from the SATA before it stops for good.
For the moment I've had to disconnect it and restore mbr to primary drive again.

Any advice on how to quickly restore access to these partitions would be greatly appreciated. More than one attempt may not be possible.
Still very much an Ubuntu newbie so detailed instructions will be necessary.


Thanks,

Bob

---

### Post by njparton on 2008-05-08
You've written that post in a rush haven't you? :)
 
It's a bit difficult to decipher what you want to do/where your essential data is stored which is probably why you've not had a reply before now.
 
As I understand it you want to recover data from an NTFS (Windows) partition from within ubuntu but you can't mount it?
 
Why not recover it from within windows?
 
Forcing a mount shouldn't destroy the data (but I offer no guarantees).
 
To save your blood pressure in the future, once this episode is over please buy 2 new hard drives and setup a Raid 1 array to backup to :wink: Then if/when 1 fails you have redundancy in place. Never ever rely on a single hard drive for essential backups.

---

### Post by bumanie on 2008-05-08
I too have a little trouble understanding exactly what you want to save, however dd rrescue comes to mind. Unfortunately I am not an expert on using this very good tool. I can't suggest any syntax as I am not clear on to what medium/drive you are going to shift the data to ie the command lines need to be very specific as to which drive/partition the input is on and to where the output file is going. For a new person to linux dd is a bit complex.
Failing that force mounting the partition you want to access should be OK. The reason it won't mount is because it was not shut down cleanly from the windows environment and ubuntu sees it as still being in use. It may help if you give some more information re hdd and partition numbers etc. As you can boot into ubuntu post output of > sudo fdisk -l and try to point out what data needs to move from which partition to which partition/drive.

---

### Post by wireman on 2008-05-20
Thankyou for your reply. Sorry for delay in response, not had access for over a week.

> **njparton said:**
> 
 
It's a bit difficult to decipher what you want to do/where your essential data is stored which is probably why you've not had a reply before now.
 "I want to get all files I can from the SATA before it stops for good." 

> 
As I understand it you want to recover data from an NTFS (Windows) partition from within ubuntu but you can't mount it?
 Booted from Ubuntu "NTFS partitions on SATA give something like "device not cleanly unmounted" so are not accessible."

> Why not recover it from within windows?
 "If SATA is connected XP won't boot."

> To save your blood pressure in the future, once this episode is over please buy 2 new hard drives and setup a Raid 1 array to backup to :wink: Then if/when 1 fails you have redundancy in place. Never ever rely on a single hard drive for essential backups.
Backups are currently held on both drives, Raid 1 would be ideal for future.

Thanks for your assistance.

Bob

---

