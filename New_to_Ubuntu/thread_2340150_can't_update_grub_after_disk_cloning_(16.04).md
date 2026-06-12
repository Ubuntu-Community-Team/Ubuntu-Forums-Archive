---
title: "can't update grub after disk cloning (16.04)"
date: 2016-10-16
forum: New to Ubuntu
---

### Post by rafalrafath on 2016-10-16
[FONT=arial]Hello everyone![/FONT]
[FONT=arial]I was using a hard drive with dual boot Win7 and Ubuntu, but as bad sectors appeared I decided to get a new one and try cloning systems on it. Sadly, I only managed to clone ubuntu and its storage, clone app refused to go on when encountered bad sectors on Win7 partitions. Ubuntu works fine on a new drive, Win7 is not booting obviously. I don't need win7 that much anymore, I just thought I could use it sometimes and try booting from the external drive. I reckoned it would be possible just to change the partition letter in the grub so that grub knows that Win7 is not on sda anymore but on sdb. I didn't find that option though. But as I was making some minor changes to grub it turned out I cannot update grub.
As I try to update grub from the terminal it just gets stuck. The last line it displays is this:
[/FONT]

```
Found memtest86+ image: /boot/memtest86+.bin

```
in "grub customizer" it takes no effect either saying "loading script 6/9 (os-prober")

in Boot-repair it stucks too. The last line in terminal are like this

```
=> [[ PY ]] => [debug]Delete the content of TMP_FOLDER_TO_BE_CLEARED and put os-prober in memory
=> [[ PY ]] => SET@_progressbar1.pulse()
=> [[ PY ]] => SET@_progressbar1.pulse()
=> [[ PY ]] => SET@_progressbar1.pulse()
=> [[ PY ]] => SET@_progressbar1.pulse()
=> [[ PY ]] => SET@_progressbar1.pulse()
=> [[ PY ]] => SET@_progressbar1.pulse()
=> [[ PY ]] => SET@_progressbar1.pulse()
=> [[ PY ]] => SET@_progressbar1.pulse()
=> [[ PY ]] => SET@_progressbar1.pulse()

```
and it goes on forever..


here's the partition list on my drive

```
Device Boot     Start    End   Sectors   Size Id System
/dev/sda1  *            2048    411647    409600   200M  7 HPFS/NTFS/exFAT
/dev/sda2             411648 838576934 838165287 399,7G  7 HPFS/NTFS/exFAT
/dev/sda3          945829888 976773167  30943280  14,8G  2 XENIX root
/dev/sda4          838578174 942018559 103440386  49,3G  f W95 Rozsz. (LBA)
/dev/sda5          941776896 942018559    241664   118M 82 Linux swap / Solaris
/dev/sda6          838578176 941776895 103198720  49,2G 83 Linux


Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.








Disk /dev/sdb: 15 GiB, 16039018496 bytes, 31326208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0dfaebf4


Device Start Start   End  Sectors Size Id System
/dev/sdb1  *        2048 31326207 31324160  15G  c W95 FAT32 (LBA)




Disk /dev/mapper/cryptswap1: 117,5 MiB, 123207680 bytes, 240640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes



```


Frankly, I have no idea what to do now..

---

### Post by oldfred on 2016-10-16
Do you know what this is or was? I think it may be the issue as Xenix is very uncommon, or probably says you have bad data in partition table.
>  /dev/sda3          945829888 976773167  30943280  14,8G  2 XENIX root 



       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT.txt

You may be able to use disks or command line to change partition type without reformatting which might erase any data you had in it.
But if it really was not a partition but part of one of your other partitions, then it may have data, that you may lose anyway.

---

### Post by rafalrafath on 2016-10-16
Thank you! I used this command and the grub update got unlocked, so to speak :) However, I don't see any changes to the grub on system startup despite the fact that I did some minor visual changes and they're reflected in the grub config file. That's not so important, what is important is the fact that I wanna make grub to load win7 from an external disk /dev/sdb not /dev/sda as it was before when the drive was inside the computer. Can I just change hd0 to hd1 in Grub Customizer in sections relating to Windows?

here's the bootinfo from the Boot Repair [http://paste2.org/sKZGzULm](http://paste2.org/sKZGzULm)

---

### Post by oldfred on 2016-10-16
Windows will not boot from an external drive unless really e-SATA, so seen as an internal.

This adds or updates grub menu.
sudo update-grub

---

