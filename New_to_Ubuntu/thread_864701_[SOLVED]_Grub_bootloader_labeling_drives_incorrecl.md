---
title: "[SOLVED] Grub bootloader labeling drives incorrecly?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by The MAX on 2008-07-19
Hi So here's my previous story
[http://ubuntuforums.org/showthread.php?t=863843]("http://ubuntuforums.org/showthread.php?t=863843")

So heres the setup I have
a single 500GB sata drive with a Windows partition and an extra ntfs partition
a single 250GB sata drive with a 60GB linux partition and a swap

the 500GB drive is hd0(sda) and the 250gb is hd1(sdb)

here's my fdisk -l output

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdb7fdb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       60800   283579380    f  W95 Ext'd (LBA)
/dev/sda5           25497       60800   283579348+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfc9dfc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7295    58597056   83  Linux
/dev/sdb2            7296        8268     7815622+  82  Linux swap / Solaris

```

Now I wanted to keep everything Linux on the sdb drive and everything windows on the sda drive. So I installed the bootloader onto sdb. that way if anything happened my windows drive would still be able to boot properly by itself using the windows boot loader.
So that should allow me to use the second disk (sdb) as the primary boot disk, then go to windows on the first disk or linux on the second.
BUT linux gives me an error 17 and windows gives an error 13. Now I know what these errors are so I'm not too worried.
Go to the grub command prompt and I see this
```
grub> find /vmlinuz
hd(0,0)
```

thinks it and linux are on hd0!
I now have the grub loader on the 500GB disk and evrything works fine.
Tried changing device.map to hd0=sdb and hd1=sda and aswell changing things in the menu.lst and then booting from the 250gb but that allows linux to boot but not windows.

So what I'm really looking for is a solution to fix this is the actual Grub bootloader itself so it recognizes that its on the second hard disk along with linux.
Like I said the setup I have now works fine when grub is on the 500GB but I would like to preserve the boot sector on that disk to point to the windows loader.

Any help is gladly appreciated. :)

---

### Post by logos34 on 2008-07-19
Write Grub to the MBR of sdb:

sudo grub-install /dev/sdb 

Now reboot, enter the Bios and change the hard disk boot priority to:

1. sdb (250 GB)
2. sda (500 GB)

The grub menu should come up...press 'e' to edit the highlighted ubuntu kernel, 'e' again on the 'root' line and change to (hd**0**,0).  'b' to boot.  Make the change permanent once back in ubuntu by editing the menu.lst.

Your windows stanza at the bottom should look like this ([booting win on second disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")):

> title        Windows
root        (hd**1**,0)
[B]map        (hd0) (hd1)
map        (hd1) (hd0)[/B]
makeactive
chainloader    +1Restore windows bootoloader to sda with Super Grub Disk or windows install cd (**fixmbr**)

---

### Post by The MAX on 2008-07-20
i've fixed the windows mbr and made these changes in the menu.lst file and Linux boots fine. Also was able to update the sata drivers and now windows and linux will both boot in AHCI mode.

However windows will still not boot. It will boot if I only boot from the 500GB via the windows bootloader but it will not boot using this config
```
title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1 
```

in the menu.lst file. I will try again as I do not have a space between (hd0) and (hd1), but not at home right now. Are these map commands exact as I should have them or just an example?

Thanks for all the help.

---

### Post by louieb on 2008-07-20
Just a wild as guess. The map commands are there to fake windows into thinking it on the 1st hard drive. Since its on the 1st and your booting to the 2nd. 
Comment out the map lines, leave the root line (hd1,0) the same. and see if GRUB will boot windows that way.

---

### Post by The MAX on 2008-07-20
got it to work with the map commands, just needed that space between the hd codes! lol

Thanks again for the help.

---

### Post by logos34 on 2008-07-20
ok, glad to help. Mark thread as 'Solved' (>thread tools)

Enjoy!

---

