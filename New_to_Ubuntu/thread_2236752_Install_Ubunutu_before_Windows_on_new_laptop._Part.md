---
title: "Install Ubunutu before Windows on new laptop. Partitioning help"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by Kristopher_Horn on 2014-07-28
I just bought a new laptop, Sager NP8278, but I did not buy any Windows OS. I am going to install Windows in the future, but right now I am in the process of installing Ubuntu. I have tried reading up and looking around but understanding partition is a bit confusing for me, so I would like to ask. What is the best set up to install Ubunut first and leave space to install Windows in the future. Along with Windows and Ubuntu, I would also like to have a shared partition between the two.

Whats I am having the most trouble with is, what file system should I use for each partition. I don't know why but NTFS is not an option. I can only choose between the ext's, btrfs, JFS, XFS and FAT16-32, as well as swap area, physical volume for encryption, and do not use the partition. The second major question is how do you make a shared partition? Does it require an OS or is it just free space where you can drag and drop files?

Some minor questions
a) logical or primary partition type?
b) location of the new partition, end or beginning of free space?
c) Mount point, /dos or /windows?
d) how much space should I use for shared partition? ( I have 1 TB of free space overall )

I am going through the Ubuntu install wizard

Thank You,

p.s I keep seeing that I should install windows first, but again, I do not have windows to install and will not get it for quite some time. So I would like to partition my laptop and get it ready for when I do get windows.

---

### Post by Kristopher_Horn on 2014-07-28
Update:

I am on [https://help.ubuntu.com/community/DiskSpace#Required_partitions](https://help.ubuntu.com/community/DiskSpace#Required_partitions), but it is still pretty confusing

---

### Post by Bashing-om on 2014-07-28
Kristopher_Horn; Hi ! Welcome to the forum .

It matters ! Is this new box UEFI enabled ? or is it the legacy bios ?
This is the determining factor in how the system(s) will boot and thus how the hard disk(s) are partitioned.
 
And no, I do not do Windows, it used to be that Windows had to be installed onto the 1st partitions, with UEFI I do not know if that is still true.

[INDENT][INDENT]a bit to try and help
[/INDENT][/INDENT]

---

### Post by Kristopher_Horn on 2014-07-28
Not sure but I found this [http://askubuntu.com/questions/162564/how-can-i-tell-if-my-system-was-booted-as-efi-uefi-or-bios](http://askubuntu.com/questions/162564/how-can-i-tell-if-my-system-was-booted-as-efi-uefi-or-bios)

I clicked on Try Ubuntu instead of install  and I ran " [COLOR=#000000][FONT=Ubuntu Mono][[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]d [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sys[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]firmware[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]efi [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]&&[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] echo UEFI [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]||[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] echo BIOS " in the terminal and it returned with BIOS. So I do not think UEFI is enabled[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-07-28
Kristopher_Horn; Welp.

Not good enough as that only indicated that you have booted up bios mode. I think - and that can be a cloudy issue - if you intend to install Win8 it must be UEFI. We still need to know if your main board is UEFI capable .

The only sure way I know to determine if UEFI capable is to consult the manufacturer's manual.

Long term usage, you do want UEFI .. beats bios all hollow 7 ways from Sunday. But, UEFI is a new thing and is different, we all have to learn to cope with it and get on the band wagon. 

[INDENT][INDENT][INDENT]I am still in the dark ages
[/INDENT][/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2014-07-28
Simple. Run Windows in VM. No need to worry about partition and UEFI (BTW if you get non OEM Windows I don't think you need to do UEFI as long as you have a BIOS option, but I can be wrong)

---

### Post by oldfred on 2014-07-28
The partition requirement are a lot different for UEFI with gpt partitioning and BIOS with MBR(msdos) partitioning.
Windows only boots from MBR with BIOS.
Windows only boots from gpt with UEFI.

With BIOS Windows typically installs to the first two primary MBR partitions. It has a small 100MB boot partition and the main install. If using BIOS you cannot create those partitions with the Ubuntu installer as it does not do Windows, but you can use gparted in advance or just create partitions leaving space at beginning of drive.
And install Ubuntu in logical partitions in one extended partition.

With UEFI Windows wants an efi partition (which will also be used by Ubuntu), a system reserved partition that must be just before the main NTFS partition. Typical installs from vendors include recovery partitions, but your install would not have those.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Kristopher_Horn on 2014-07-28
just found BIOS and UEFI Boot is currently disabled and I can enable it. Also my drive is MBR and not GPT.

---

### Post by Bashing-om on 2014-07-28
Kristopher_Horn; Outstanding !

Making good progress.

oldfred rules ... follow his recommendations.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Kristopher_Horn on 2014-07-28
OK, so, after what I have been reading I am guessing that to boot Ubuntu first and set up for a future install of windows I want to create these partitions in the install wizard.....

Enable UEFI Boot

Root Partition:
mount point: /
size: 25 GB
type: ext4

Swap Partition:
mount: (blank)
size: 25 GB I have 16GB RAM)
type: swap

Ubuntu Partition:
mount point: /home
size: 350 GB
type: ext4

Shared Partition:
mount point: /media/Shared
size: 100 GB
type: NTFS

Windows Partition: (Where I will install Windows)
size: freespace (500 GB)
type: NFTS

---

### Post by Vladlenin5000 on 2014-07-28
Just a remark:

With 16GB of RAM you don't need swap at all, unless you intend to hibernate in which case you need the same amount of RAM in GiB. Making it 25GB is overkill and a waste of space.

---

### Post by Kristopher_Horn on 2014-07-28
Well this seems pretty confusing so I don't think I am going to partition anything right now. I will let future me deal with everything when the time comes haha. If worst comes to worst. Ill just backup everything and do it the way everyone says to do it, with windows first. But Thank You everyone for the help. Just one last question. Should I create a partition to share files between my laptop and other computers/USB devices? Do I need to? My school works with only Windows.

---

### Post by Bashing-om on 2014-07-28
Kristopher_Horn;

If I may.

1) you will need an additional efi-boot partition for booting efi;
2) with 16GB of ram, swap will rarely if ever get touched ,, how about 2 gigs for swap ( a little bit is a good thing to have)
3) /home at 350GB is huge ( I run 10 Gigs, for instance and symlink to exterior directories) IF you are going to do lots of music/videos AND keep the default directories - you may have the better idea of 350 gigs for /home
4) I run a small light fast system " /dev/sda1       4.7G  2.0G  2.6G  44% /" 
for '/' I allocated 5 gigs and am using 44% of that space, Your Mileage Will Vary, but 25 Gigs is a bit excessive
-My system is three 500 Gig hard drives - multi booting-

For guidance:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) <-Installing Ubuntu Quickly and Easily; It shows pictures.

Try'n to get you onboard and
[INDENT][INDENT][INDENT]I hope this helps[/INDENT][/INDENT][/INDENT]

---

