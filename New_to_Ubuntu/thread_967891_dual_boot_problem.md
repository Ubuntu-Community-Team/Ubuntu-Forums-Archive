---
title: "dual boot problem"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Silentzor on 2008-11-02
hi! I installed ubuntu on the same HDD with windows XP (hdb) and on hda I have installed windows vista... the problem is that when I boot there is no windows xp selection and when I try the windows vista selection a message apears saying:

> Starting up...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart

what should I do?:(

---

### Post by bumanie on 2008-11-02
In effect, if I read things correctly, you are trying to create a triple boot. It is quite possible to do this, but it needs to be done in a particular order to succeed without encountering problems as you now are. Are you prepared to reinstall some things to get it right? If so I will help, if not I fear it will be a bit of a nightmare getting the bootloaders right with all three OSes.

---

### Post by Silentzor on 2008-11-02
shoot :D

---

### Post by bumanie on 2008-11-02
I'm at work on a *hitty old windoze box, but the procedure was fairly straight forward. Vista is on the first partition of the hard drive - being hda. 
I will tell you the steps below, by the way I did this last week to a new laptop - I'm sure Hp would be horrified that there is no longer restore partition and two other OSes on the thing now :).
Vista is already there a is xp. we won't worry about ubuntu as yet - it comes later. The important is to get vista and xp's bootloader together, they recognize each other, but won't boot each other unless their bootloaders are 'merged'.
What I did to get it to work.
1) Vista preinstalled, shrunk vista and then installed xp.
2) Xp overwrote vista's bootloader and vista would not boot.
3) Reinstalled vista's bootloader with the vista repair disk from Neosmart technologies.
4) Downloaded easybcd bootmanager from neosmart technologies and with that, added xp's boot files to the vista boot files.
5) Checked that I could boot into both vista and xp - at boot, one is given the choice of booting vista or xp - it is a bit like grubs menu.
6) Installed ubuntu as normal, which picks up the vista install and chainloads vista as per a dual boot system - only difference being, is that when one chooses, vista, one has the choice of vista or xp. Of course if you choose ubuntu, it boots.

Triple boot, very easy.
I suspect you can probably start with reinstalling vista's bootloader and then go on to the easybcd step. The reason there is no bootmanager in vista is because xp has overwritten it. Reinstall the vista boot files - 'join' vista and xp together with easybcd and either A) reinstall ubuntu so that grub knows vista is there or B) edit /boot/grub menu.lst to reflect the vista installation. I f there is not much on ubuntu, I think I would choose the first option, as it is more simple.

Good luck and I hope this is enough info.

---

### Post by caljohnsmith on 2008-11-02
With all due respect, Bumanie, reinstalling all the OSes in order to accomplish a triple boot should not be necessary. :) Silentzor, how about booting your Live CD (in case you can't boot into Ubuntu), open a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -lu
```
We can work from there if you want.

---

### Post by Silentzor on 2008-11-02
Here goes:

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xacb5acb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976768064   488383008+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe485e485

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   208170269   104085103+   7  HPFS/NTFS
/dev/sdb2       212668470   312576704    49954117+  83  Linux
/dev/sdb3       208170270   212668469     2249100   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe244e244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed0eed0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   156280319    78140128+   7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-11-02
OK, that helps alot, you didn't mention that you actually have 4 HDDs. :) First, if you haven't all ready done so, can you set your BIOS to boot your Ubuntu sdb drive first on start up? That would be most ideal, and then it will be easy to boot Vista or XP from that drive, assuming Vista and XP are OK. If you can boot the sdb drive and get the Grub menu OK, then do the following to add XP and Vista to your Grub menu:
```
sudo mount /dev/sdb2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst

```
And add the following entries to the end of the menu.lst:
```
title	   Windows Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows Vista (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows Vista (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, make sure BIOS is set to boot the sdc drive, and let me know what happens when you select each of the Windows entries.

---

### Post by Silentzor on 2008-11-03
Great it works man! I just needed the "Windows XP" part, as vista will use XP's loader. It's kinda weird, but it works fine :P Thanks a lot!

---

### Post by caljohnsmith on 2008-11-03
> **Silentzor said:**
> Great it works man! I just needed the "Windows XP" part, as vista will use XP's loader. It's kinda weird, but it works fine :P Thanks a lot!
Glad to hear it worked. Cheers and have fun. :)

---

