---
title: "Removing Ubuntu after double boot"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by ZeframCochrane on 2008-08-23
I have tried Ubuntu from Live CD, and I was thinking of advancing to the next step, and installing it to double boot along with Win Vista.

I was wondering, should I eventually decide to drop Ubuntu, and shift back to a 100% Windows computer, what is the correct procedure to reformat to NTFS the partition assigned to Ubuntu, merge it with the existing Windows one, and restoring correct boot functions?
Because I was about to go ahead and install Ubuntu, fairly sure that I could eventually reformat its partition, but I suddenly realised that this would also delete the GRUB loader, leaving the computer without a bootable disk. Or I may be (most probably) wrong.

In essence, what is the I-have-changed-my-mind-gimme-back-windows-as-it-was-before procedure, after having used double boot for a while?

---

### Post by Oldsoldier2003 on 2008-08-23
Basically what you'll do is:
1. delete the Ubuntu partition
2. restore the windows mbr 
3. and then either reformat the unallocated space that used to be Ubuntu, or merge it with your vista partition. 

Personally I would just format it as a separate data partition if I were in that situation.

---

### Post by sandysandy on 2008-08-23
u can use XP Cd to fix MBR.

or u can use super grub disk to restore windows MBR.

once MBR is restored, and u can boot to windows  u can delete ubuntu and reformat partition to NTFS.

see this

[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)



regards

---

### Post by ZeframCochrane on 2008-08-23
Thanks for the answer to both.

Would the Super Grub Disk work even if I have installed Ubuntu in a partition of an originally NTFS drive which is **not** the drive/partition where Vista is installed?
Let me be more clear:
I have a laptop, in which I see two drives, C: and D:. Whether these are two real physical drives or they are two partitions of the same drive, I do not know. Anyway, Vista is installed on drive ***C:***, and I wanted to install Ubuntu on a partition of drive ***D:***. Would using Super Grub Disk correctly restore boot from drive C: ? I realize I may be asking completely meaningless questions (I'm unsure whether the MBR is in a partition of its own, or if it's in a sector of an existing partition, etc..) so please bear with me :(

Moreover, once I have correctly restored windows booting, and I find myself with a smaller D: drive (since part of it is still partitioned as EXT3), could I have more details as to how to restore the EXT3 partition to an NTFS one and merge it to the existing D: drive? I thought this couldn't be done from inside Windows, 'cos I thought Windows couldn't read/recognise EXT3.

---

### Post by sandysandy on 2008-08-23
post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR] (from terminal of live CD)

regards

---

### Post by ZeframCochrane on 2008-08-23
Here is the result:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x961f8c5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20973567    10485760   27  Unknown
/dev/sda2   *    20973568   323055615   151041024    7  HPFS/NTFS
/dev/sda3       323055616   617705471   147324928    7  HPFS/NTFS
/dev/sda4       617705472   625139711     3717120   12  Compaq diagnostics

```

Am I right in interpreting that boot is done from device sda2? So, to rephrase my question, would the Super Grub Disk restore booting from sda2, even if Ubuntu is installed in a partition originally part of sda3?

---

### Post by sandysandy on 2008-08-23
>  Whether these are two real physical drives or they are two partitions of the same drive, 

in ur case these are partitions of same drive. sda 2 and sda3

> Am I right in interpreting that boot is done from device sda2?  

yes sda2 has the boot flag so boot is done from there.

> So, to rephrase my question, would the Super Grub Disk restore booting from sda2, even if Ubuntu is installed in a partition originally part of sda3?  

when u install ubuntu, u do get the option of either installing GRUB to MBR (Master Boot record) or to a partition. 

in case u choose to install GRUB to MBR and at a later stage want to get rid of it, u can try Super Grub Disk or the vista CD. for vista other options also exist like easyBCD [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

also see these threads

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

> i'm unsure whether the MBR is in a partition of its own, or if it's in a sector of an existing partition, etc.

see this link for more info on MBR

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record) 

regards

---

