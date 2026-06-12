---
title: "Upgraded to 11.10: Read only file system, can't do anything!!"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by Lucypie on 2011-11-22
Okay, yesterday I got to upgrade and update everything on my system. Whoo! I like it all pretty well. I let the battery on my laptop die and today I plugged it in and started it up. All seemed normal. I was reading through my email and saw a message and tried to play a game: I realized I didn't have java. So I tried to install java from the website, I got something about "No suitable (???) /tmp folder" or something about the tmp folder. I thought "Well, I'll just go make one then!" I clicked places and then clicked system... and it said Unable to mount system, read only system.... What the hey! Tried to use the software center to install something.... some weird message about read only system and no temp folder... Please help... Lets see some stats, shall we? 

I use the ubuntu classic/ GNOME classic... theme with no effects. 
Using Sys Info, copying most everything I can...

Ubuntu 11.10 (oneiric)
Gnome 2.32.1 (Ubuntu 2011-04-14) (also have KDE and XFCE...)

CPU:
Genuine Intel
2 CPU
Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz

Memory: 2957 MiB (Actually, I have 4 Gigs but I use ubuntu 32b so it only recognizes 3. Any solutions (EXCEPT going to 64B) are appreciated!)
Swap 9107MiB


Storage:
ATA Hitachi HTS72503 Hard Drive SCSI1 -- 320G
And then the CDDVD drive

Host Bridge - Intel Corp Mobile 4 series chipset memory--- what good is all this? xD


Anyways... any help's appreciated :)

---

### Post by pierreyy on 2011-11-22
hello 

for the ram issue i ran the commands here:

[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)

it worked like a charm.

as for the file system problem ill let you know if i find an answer good luck!

---

### Post by pierreyy on 2011-11-22
[http://askubuntu.com/questions/47538/how-to-make-read-only-file-system-writable](http://askubuntu.com/questions/47538/how-to-make-read-only-file-system-writable)

check the replies,  they might of help

good luck

---

### Post by SeijiSensei on 2011-11-22
Linux mounts filesystems with errors as read-only.  You'll need to boot from a CD and run fsck against the partition.

---

### Post by Lucypie on 2011-11-22
I don't have a disk and I have problems using disks.. please help with another solution. 

PS, I have no idea why live cds never work....

--Pierreyy : Looking @ it now..

---

### Post by Lucypie on 2011-11-22
UPDATE: Fixed!


I did sudo fsck and it told me some error and said it was forcing a check. 
After a while it gave me about 4 or 5 errors and "Fix? y" after each. I did, and it told me "FILESYSTEM WAS MODIFIED"
"REBOOT LINUX"

So I did, It works fine. Thank you so much!!! I'll try the RAM and we'll see how that works. For now Im busy though :S!

---

### Post by Denver Dave on 2011-11-22
You're situation may be different, but just in case, you might glance at this tread where someone helped me resolved my issue with my 11.10 USB boot system that could not write to to NTFS drives.
[http://ubuntuforums.org/showthread.php?t=1881701](http://ubuntuforums.org/showthread.php?t=1881701)

---

### Post by pierreyy on 2011-11-22
thats great! let me know if the ram thingy turn out okay, and dont forget to mark as solved  enjoy!

---

### Post by SeijiSensei on 2011-11-23
> **Lucypie said:**
> I did sudo fsck and it told me some error and said it was forcing a check.

Did you run fsck against a mounted partition despite the warning not to do so?  If so, you were lucky that the filesystem corruption was probably very limited.  In general, running fsck on a mounted partition can lead to data loss.  That's why I recommended you run it from a CD (or USB) disk.

---

