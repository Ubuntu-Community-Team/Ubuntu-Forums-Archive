---
title: "I don't know where to start. I messed up bad."
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-05-30
i started having problems with GRUB, and between the Hardy Heron Live DVD and super GRUB disk i became pretty sure i didn't know what i was doing (Seriously, the SGD could really do without the smilies and stuff.)

i figured that since i had my media on a seperate disk (i have my /home on a second hard drive) and i just installed Hardy a week or so ago, i could just wipe that first drive completely and install XP, then Hardy again.

sda1 is a 35Gb partition that XP called home, and i was trying to reinstall there. the windows installer was complaining when i just tried to install into the same partition, so i just deleted the windows partition. i created another partition right in it's place, same size and everything. it still didn't work, it was giving the same complaint.

i turned off my computer and popped in my Hardy Heron DVD, because you can never trust windows to do something Linux can do better. i fired up gparted and made a new NTFS partition, restarted with the XP disk in, and got the same thing.

i booted up the Hardy Heron DVD again and made a Fat32 partition, thinking maybe NTFS wasn't supported by the installer, but got the same result again.

i thought maybe these problems installing XP weren't related to the partition, but because GRUB was installed instead of the microsoft boot loader.

i booted into that recovery console (it's like the crippled windows terminal running from the installation CD) and entered **fixboot** and **fixmbr**, answering yes to both warnings (it's just going to remove GRUB right?)

well no, not exactly. to my horror when i restarted the computer and tried to install into the problem partition i noticed MY ENTIRE /HOME DIRECTORY HAD BEEN DELETED! there was now a fat32 partition in it's place, and i'm sure it didn't format in a way to preserve the data.

i was proven correct when i booted into the live DVD and mounted the partition. there were now just three files in it, with weird names. i'm sure they were something like file fragments of my family pictures i don't have backups of, the movies i have, all my music, the... videos... i have in a hidden directory. everything was gone.

is there any way i can get the data back?

---

### Post by Sonic Reducer on 2008-05-30
i guess i should mention, i'm not going to turn on my computer again until i know what i'm doing

---

### Post by wdaniels on 2008-05-30
I hate to say it, but I don't like your chances of getting the data back now :(

The only thing I can think to suggest you try is a program called [gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/") which is in the repos so you could boot the live CD, install and use it from there. Otherwise there are various commercial alternatives, but these things are always difficult (and usually impossible) to recover from so I wouldn't suggest shelling out cash for recovery software unless you have plenty to spare.

---

### Post by niteshifter on 2008-05-30
Hi,

Testdisk and / or PhotoRec from [here]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by Sonic Reducer on 2008-05-30
to be honest i don't need a program to guess the partitions, i know that sdb1 is the entire disk, and it's supposed to be ext3 (hopefully all my data is on it)

i think it's pertinent to mention that it didn't take very long to process when i did the fixmbr and fixboot, so i don't think it did a comprehensive formatting, so as far as i know and can tell (which is admittedly not very far in this department) my data might still be intact.

hopefully it's recoverable too =]

---

### Post by wdaniels on 2008-05-30
I must be misreading your post, I thought that you had tried to install Windows onto this partition?

Well, anyway, neither fixboot nor fixmbr format anything, so hopefully it's just the partition table that's been destroyed. If you know the start/end blocks as you say, then you should be able to just use fdisk from the live CD to delete the FAT32 partition then recreate the partition table as it was (remember to set the partition type, which is 83 for ext3).

---

### Post by Sonic Reducer on 2008-05-30
i tried to install XP onto /dev/sda1

my home directory is on /dev/sdb1 (which is the entire disk)

for some reason i fubared the wrong disk. losing sda would be a bad day (it has XP, hardy, and swap on it), losing sdb is a tradgedy.

---

### Post by wdaniels on 2008-05-30
I heard quite recently (though I forget from where exactly) that some older XP install CDs don't recognise Linux partitions and delete (or do something else destructive to) them so perhaps this is a symptom of the same problem somehow.

Anyway, if you use fdisk to put the partition table back the way I already described that ought to fix the problem, so long as you're correct about the original structure. fdisk doesn't touch the data, only the partition table so it should be safe to try this, though there is of course always some element of risk with these things.

Maybe you would prefer to wait for other input and consensus on the matter first? (I'm not claiming to be an expert so I won't be offended :D)

---

### Post by Sonic Reducer on 2008-05-30
WHAT THE HELL IS GOING ON!!!

i just booted up the live dvd, installed gpart (not garted) and ran the command **sudo gpart /dev/sdb1** and a half-hour into it there was a 5 minute power outage!

does god not want me to get my porn back or something?

---

### Post by wdaniels on 2008-05-30
> **Sonic Reducer said:**
> installed gpart (not garted) and ran the command **sudo gpart /dev/sdb1**

I don't know if it will make a difference, but it should be just /dev/sdb not /dev/sdb1. It's logical enough for gpart to ignore the 1 but who knows...

Don't worry, it would only have been scanning to look for the partitions, not writing/fixing anything.

---

