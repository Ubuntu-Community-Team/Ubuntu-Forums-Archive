---
title: "Where is SSD in gparted?"
date: 2014-01-21
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-01-21
While trying to better understand another problem by reading other threads, something just occurred to me. I have a dual boot with 12.04 system on SSD and Win 8 system on HDD on a newish HP computer. Grub works and I can select between the two from the grub menu.

From within Ubuntu, if I run gparted, it only shows one device and that is the HDD.

Where is SSD in gparted?

Wooops. The above got posted before I could add
```
sudo blkid -c /dev/null -o list

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    Windows RE tools (not mounted) CC944F7F944F6AD2
/dev/sda2  vfat    SYSTEM   (not mounted)  963D-3F74
/dev/sda4  ntfs    OS       (not mounted)  4CB24755B2474326
/dev/sda5  ntfs    Recovery Image (not mounted) 60CAB573CAB54656
/dev/sda6  ext4    /home    /mnt/newhome   33ad57b6-3c44-4444-a7e3-73f14f76f8b9
/dev/sda7  ext4             (not mounted)  7edaadf6-ebbd-4b9e-acc4-5e12e09213b0
/dev/sdb1  ext4             /              5c523eff-90ae-47f8-a810-aff90a07b0dd
/dev/sdb2  ext4             /home          428c5eb3-d21b-4bda-b50a-ab3755ff24a7
/dev/sdb3  vfat             /boot/efi      A403-1C37
/dev/sdb4  ext4             (not mounted)  a726522d-89c9-4e25-aefb-904f4a5fe3b6
robert@robert-HP:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb3 on /boot/efi type vfat (rw)
/dev/sdb2 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)
/dev/sda6 on /mnt/newhome type ext4 (rw)
robert@robert-HP:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5c523eff-90ae-47f8-a810-aff90a07b0dd /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
UUID=A403-1C37  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda2 during installation
UUID=428c5eb3-d21b-4bda-b50a-ab3755ff24a7 /home           ext4    defaults        0       2

```

```

sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa5830d20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 63.0 GB, 63023063040 bytes
255 heads, 63 sectors/track, 7662 cylinders, total 123091920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   123091919    61545959+  ee  GPT

```

---

### Post by philinux on 2014-01-21
From dash type in disks.

Run the app - what does it show?

---

### Post by sudodus on 2014-01-21
At the top right corner there is a small drop-down menu, where you can select which device to view and edit. I think you can find your SSD there (probably as **/dev/sdb**, while /dev/sda is shown by default, when you start gparted).

---

### Post by Odyssey1942 on 2014-01-21
Philinux, I think you are referring to the Unity Dash? I don't have it having reverted to Gnome (no effects)

Is there another way to do this?

---

### Post by Odyssey1942 on 2014-01-21
sudodus, yes I see it. Must be losing it as I called myself looking top and bottom for a way to find it. Good thing it wasn't a snake.

However the SSD is the boot drive. Shouldn't it show up as sda?

Also, sda does not appear to have logical partitions. Does UEFI not use these?

Further on this, the SSD has the 12.04 install and the HDD has the Win 8 install under UEFI. I am still a bit nervous about my own installation as evidenced by some strange stuff. The only one that I can think of to cite as an example is that of trying to apt-get install samba. It took four tries before it finally got through it where before on other computers, it has always breezed right through on the first try. 

Can you see anything in the terminal outputs above that might shed some light on this?

---

### Post by philinux on 2014-01-21
> **Odyssey1942 said:**
> Philinux, I think you are referring to the Unity Dash? I don't have it having reverted to Gnome (no effects)

Is there another way to do this?

The app disks should be in your menu system somewhere.

In a terminal what does this show.

```
sudo fdisk -l
```
and
```
sudo parted -l
```

---

### Post by Odyssey1942 on 2014-01-21
philinux, thanks. Please see above as yours probably crossed with mine.

Edit: missed your edit. Here is the other:
> sudo parted -l

Model: ATA WDC WD10EZEX-60Z (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1074MB  1073MB  ntfs         Basic data partition          hidden, diag
 2      1074MB  1451MB  377MB   fat32        EFI system partition          boot
 3      1451MB  1585MB  134MB                Microsoft reserved partition  msftres
 4      1585MB  127GB   126GB   ntfs         Basic data partition
 6      127GB   569GB   442GB   ext4
 7      569GB   989GB   419GB   ext4
 5      989GB   1000GB  11.7GB  ntfs         Basic data partition          hidden


Model: ATA SanDisk SDSSDP06 (scsi)
Disk /dev/sdb: 63.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  23.0GB  23.0GB  ext4
 2      23.0GB  43.0GB  20.0GB  ext4
 3      43.0GB  43.1GB  34.6MB  fat32              boot
 4      43.1GB  63.0GB  20.0GB  ext4

---

### Post by oldfred on 2014-01-21
You may have Ubuntu/grub2's efi files in the efi partition on sda.
UEFI uses gpt. Fdisk does not work, better to install gdisk for gpt drives or just use parted.
With gpt there is only one type of partition essentially all primary. The soft limit is 128 partitions, but supposedly a user can change size of partition tables and make even more partitions. 

Often better to run BootInfo even if you do not need repairs. That shows lots of detail and where boot files are installed.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sudodus on 2014-01-21
> **Odyssey1942 said:**
> sudodus, yes I see it. Must be losing it as I called myself looking top and bottom for a way to find it. Good thing it wasn't a snake.

However the SSD is the boot drive. Shouldn't it show up as sda?

No, not necessarily. It is hard to control the device lettering (sda, sdb ...). This is why it is good to use the UUID to identify the partitions in /etc/fstab. See ```
man fstab
```
> 
Also, sda does not appear to have logical partitions. Does UEFI not use these?
(Already answered by *oldfred*: UEFI is always using GPT, which does not use logical partitions).

---

### Post by Odyssey1942 on 2014-01-21
Thanks for this. Can I just run boot-repair from terminal in a normally booted session (not from a live CD)? I am asking this because I am assuming that the reason for booting from a live CD is that the boot process is broken and the computer will not boot, which is not my case. OTOH, if a normal session obscures the results that might be better obtained from a live CD session, then happy to do it. Just wish to save time whenever possible by skipping unneeded steps.

Threw caution to the wind and tried it. Here is the result:

[http://paste.ubuntu.com/6792672/](http://paste.ubuntu.com/6792672/)

Note: Before offering the URL, a warning came up stating that EFI (or maybe GPT? Didn't write it down and my memory not great) was detected. Don't know how significant this might be in this exercise.

---

### Post by oldfred on 2014-01-21
The warning is just to make sure that you want UEFI not BIOS. 

You do have grub2's efi boot files in sdb3. And Windows efi boot files in sda2.

12.04 does not have the fixed os-prober and only finds Windows BIOS boot type entries not UEFI. You can use Boot-Repair to add correct entires, but HP has lots of efi files in your Windows efi partition. Boot-Repair also adds those which makes you grub menu very long. May be easier just to add your own, although you can run Boot-Repair and edit the 25_custom it creates. Instructions in link in my signature.

Shows manual entry you need to boot Windows.
 grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

If you run Boot-Repair say no to any "buggy" UEFI suggestion. That is only for those UEFI that only boot Windows from UEFI menu. Vendors are not supposed to modify UEFI to only boot Windows but some do.

---

### Post by Odyssey1942 on 2014-01-21
Thanks again. Looks from the referenced URL like lots of reading and following links for more reading (much of which I can see will be over my head, as much of yours is-hope with time this will improve for me.)

Can I ask you a Plan B/C question? If I am now able to boot into both 12.04 and Win 8 with the current setup, are there other issues that might demand that this be fixed sooner rather than later?

If so, due to the now much elevated pressure to give my wife's computer back to her, I could just remove the Win 8 HDD and replace it with another temporary HDD in hopes that she will stay with Ubuntu long enough for me to try to figure out how to deal with the current issues.

If not, I may just try to get the tar unpacked in the HDD and link the folders back to /home (may have additional questions once embarked). Once done, I can give it back to her and keep my fingers crossed.

---

### Post by oldfred on 2014-01-21
As long as you can boot both from UEFI, then it is not a big issue. Some just use the one time boot key (f12 on my system but varies) to choose what to boot.

---

