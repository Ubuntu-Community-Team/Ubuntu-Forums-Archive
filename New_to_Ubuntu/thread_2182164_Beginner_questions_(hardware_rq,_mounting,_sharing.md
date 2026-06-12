---
title: "Beginner questions (hardware rq, mounting, sharing) in linux"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by Ryantoss on 2013-10-20
Hello community

My English is not really good thus i will make them short and easy. After couple of tries, i'm still no more than a noober

1. I have an old rig: Intel D-820, 2GB RAM, onboard VGA, 4TB of data
2. I'm currently using windows XP
3. I'm planning to use this one as data server (simply just sharing folder for LAN network with other computer, Windows 7 and Windows 8)
4. My PC have 2 partitions (C and D, C for OS, D for data)
5. Sharing in windows is way way way way way too easy. Just share and map network drive

Here is my question:

1. Can i install Lubuntu in C and share D (NTFS)
2. What is mount, i have no luck at understanding them, why not easy as windows
3. How can i share folder in Lubuntu to LAN network

Best regards :)

---

### Post by oldos2er on 2013-10-20
Lubuntu, like other distributions, needs to be installed to a Linux-native file system such as ext4, which is the default. NTFS and other Microsoft file systems don't support Linux file system permissions.

When you mount a partition, you make it available for the system to use, perform read/write operations, etc.

Why not as "easy" as Windows? Because [Linux isn't Windows]("http://linux.oneandoneis2.org/LNW.htm"), and is not intended to be a drop-in replacement for Windows.

---

### Post by Ryantoss on 2013-10-20
oldos2er, what i mean is can i install OS on first partition and don't touch second partition (leave them as NTFS with current data) and share them to my LAN network

regard

---

### Post by JKyleOKC on 2013-10-20
> **Ryantoss said:**
> oldos2er, what i mean is can i install OS on first partition and don't touch second partition (leave them as NTFS with current data) and share them to my LAN network

regardYes, you can do this, but it's a bit complicated for one who is used to the Windows way of doing things. And if something goes wrong, you could lose all the data, so I don't recommend it as a first-time action. You could install via WUBI, inside of the Windows system, and become familiar with the Linux ways first.

As for "mount" and "umount" (that's not misspelled, the command actually omits one "n") actions, Windows does them also but doesn't require that you do them yourself. That's why, in Windows, you have a fairly long wait between turning power off and the system actually going dark. Basically, disk drives are very slow compared to RAM memory, so all systems first copy things into RAM for use, and make all changes there. They don't actually write the changes out to the disk until later. The "mount" action brings the data in, and "umount" forces it back out to the drive. This is over-simplified, of course, but hopefully gives you the idea of what is going on.

Another confusing point is Windows' mis-use of the word "drive" to refer to a partition; Linux uses it to refer to the physical drive, which can have many partitions. If you have two physical drives, what you want to do would be much simpler, but many if not most "multi-drive" Windows systems have only one large physical drive, which is partitioned into several units that Windows calls drives but which are actually just partitions of the physical unit. You can view the setup of your machine from the Windows control panel's Disk Management area to see which is the case for you, or from Linux with "sudo fdisk -l" from a terminal (that's a lower-case L after fdisk, not a numeral one).

If you want to try anyway, let us know and we can give you step-by-step instructions, but whenever you make such major changes you need to have a full backup of anything you want to keep because things can always go wrong, and if they can, sooner or later they will.

---

### Post by stlsaint on 2013-10-20
Souds like you are wanting to dual boot linux and windows xp. Start here [0] and get familiar with the process first then you can move forward with the sharing of drives which is also very easy so try not to over complicate things. 

[0] [http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

---

