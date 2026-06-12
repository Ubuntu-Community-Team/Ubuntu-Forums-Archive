---
title: "grub on SATA RAID while keeping old partitions?"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by ybp on 2013-06-05
Hi All,

New here... first post...

I have a box with SATA RAID 10 (four equal drives), was a Win XP, now moving to Ubuntu Server. RAID was partitioned as C: and E: - both NTFS, and some free space. Deleted C: and let Ubuntu installer place the two partitions, "/" and "swap" in that space. Would like to keep E:, because that is where all of the HTML and MySQL files are.

Thought grub would fit nicely on the new / partition, even turned on the Bootable flag.

While installing, pointed the grub installer to /dev/mapper/isw_cgaaeggagd_Boot5 and it installed without complaints. This is the location I got after my initial unsuccessful attempts to use generic partition names (/dev/sda, /dev/sda1) and finally conceding to install without a boot loader - I wrote down the location of the root partition as indicated by the installer, and I used that during the latest install attempt. The Ubuntu root partition is indeed #5 in the partition list.

Now, trying to reboot the machine, I get this:
   [FONT=courier new]No bootable device -- insert boot disk and press any key[/FONT]

Upon inserting the installer CD and selecting "Boot from first hard disk" I get this:
   [FONT=courier new]Booting from local disk...
   error: no such device: 3d571699-4ace-4092-9b4c-89acf63be024.
   grub rescue>
[/FONT]
Now:
   [FONT=courier new]grub rescue> set
   prefix=(hd0,5)/boot/grub
   root=hd0,5
   grub rescue> ls
   (hd0) (hd0,msdos6) (hd0,msdos5) (hd0, msdos2) (fd0)
   grub rescue> set root=(hd0,msdos5)
   grub rescue> insmod normal
   grub rescue> normal[/FONT]
 
That boots up the machine. So the question is, how do I fix the grub settings so the machine can boot up normally?

Looking in [FONT=courier new]/dev[/FONT], I see:
   [FONT=courier new]sda[/FONT], [FONT=courier new]sdb[/FONT], [FONT=courier new]sdc[/FONT] and [FONT=courier new]sdd[/FONT], among other things, but no [FONT=courier new]hd0[/FONT].

Looking in [FONT=courier new]/dev/disk/by-id[/FONT], there are:
   [FONT=courier new]dm-name-isw_cgaaeggagd_Boot5, dm-uuid-part5-DMRAID-isw_cgaaeggagd_Boot and raid-isw_cgaaeggagd_Boot-part5[/FONT], among other things.

Looking in [FONT=courier new]/dev/disk/by-uuid[/FONT], there are:
   [FONT=courier new]A6B01072B0104AE7, e131e761-2295-44ab-a985-d8d7d901a797[/FONT] and [FONT=courier new]a98105ec-294b-4d05-990f-3a1526dc2e67[/FONT] only.

Which of these do I need to specify, and how do I do it? I am lost in the GNU GRUB manual... Please help.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by ybp on 2013-06-05
OK, so looking at the link (thanks!), I see that I need to identify where Ubuntu is installed. Looking at the blkid output:

[FONT=courier new]/dev/mapper/isw_cgaaeggagd_Boot2: LABEL="Data" UUID="A6B01072B0104AE7" TYPE="ntfs" [/FONT]
[FONT=courier new]/dev/mapper/isw_cgaaeggagd_Boot5: UUID="e131e761-2295-44ab-a985-d8d7d901a797" TYPE="ext4" [/FONT]
[FONT=courier new]/dev/mapper/isw_cgaaeggagd_Boot6: UUID="a98105ec-294b-4d05-990f-3a1526dc2e67" TYPE="swap"

[/FONT]so the /dev/mapper path is the same as what I entered during the installation, but the UUID is not.

After looking at the [FONT=courier new]fdisk -l[/FONT] output, I actually made some progress! After trying the various disks and partitions listed:

[FONT=courier new]sudo grub-install /dev/mapper/isw_cgaaeggagd_Boot[/FONT]

installed without error. This points to the entire RAID when viewed as a single disk:

[FONT=courier new]Disk /dev/mapper/isw_cgaaeggagd_Boot: 640.1 GB, 640141230080 bytes[/FONT]

Now, I still get the initial [COLOR=#000000][FONT=courier new]No bootable device -- insert boot disk and press any key[/FONT][/COLOR] error, but upon inserting the installer CD and selecting "Boot from first hard disk" the machine boots up - no more grub rescue prompt!

That tells me that the only obstacle left is to get the BIOS to recognize grub.

Any suggestions?

---

