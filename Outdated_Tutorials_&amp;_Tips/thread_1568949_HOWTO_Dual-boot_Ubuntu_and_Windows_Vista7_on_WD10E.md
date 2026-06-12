---
title: "HOWTO: Dual-boot Ubuntu and Windows Vista/7 on WD10EARS-22Y"
date: 2010-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by artir on 2010-09-06
So, you have just bought a PC with windows preinstalled running nicely and ubuntu just fails to install, crashes or if installed goes really realle slow on this ( WD10EARS-22Y ) hard drive.

What happens?
It happens that the HD is a liar, yep, that's right, it says to the OS "Hey! I have 512 bytes sectors" But it does have 4 Kb's , so the system getting installed creates what is called missaligned partitions. The slowdown, for me, was like running the system on a 256 mb pc with a PIV (and not even graphical acceleration, not even intel's), so really slow...

The solution:

To solve this I tried to install Ubuntu Lucid -It crashed (partman_server was the one crashing actually), Ubuntu Maverick 64-I got a daily version on a pen and that did install properly, but after running the OEM's recovery unit that came with the system (an accident, it appeared on the grub menu), the partition got somehow erased and well.. I had previously realised that I needed a 32 bit system to run an ndiswrapper driver for my card...

So Ubuntu Karmic was the only one installing nicely, but on missaligned partition.

Here is the original solution that I adapted: [http://ubuntuforums.org/showthread.php?p=9241023](http://ubuntuforums.org/showthread.php?p=9241023) , made by jeditech, kudos to him.

So step by step:
0. Windows has to be installed on the system

1. Burn a CD (or pendrive, but make sure that it boots properly) with the ultimate Boot CD ( [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) ).

2. Burn a CD or pendrive with ubuntu karmic.

3. Boot karmic and shrink the NTFS partition to whatever size you need.
    (And now create FAT32 partitions like it says on the solution, right? No!. Karmic fails doing that)

4. Boot the UltimadeBootCD and run PartedMagic from there. Open it's GParted and create FAT32 partitions as if you were creating the ones for ubuntu. i.e. a 3 Gb part for swap, a 500 Gb one for /home and a 7 Gb one for / .

5. Now, with those FAT32 partitions created, boot again into the UltimateBootCD, and from there run SuperGrubDisk2 and boot windodows. GRUB won't work because at this point there are no /boot partitions there.

6. In Windows, install WD Align utility from [http://www.wdc.com/sp/products/advancedformat/index.asp](http://www.wdc.com/sp/products/advancedformat/index.asp)

7. Run it and align the FAT32 partitions. It's quite quick.

8. Boot again PartitionMagic from the UCD and in gparted, format the fat32 partitions as ext4 and swap or whatever you want.

9. Boot Karmic and install on the specified partitions.

10. Enjoy!

---

