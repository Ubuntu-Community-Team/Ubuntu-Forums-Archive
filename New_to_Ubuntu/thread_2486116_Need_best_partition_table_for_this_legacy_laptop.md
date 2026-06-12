---
title: "Need best partition table for this legacy laptop?"
date: 2023-04-20
forum: New to Ubuntu
---

### Post by desatir73162 on 2023-04-20
Hi there, I have an old laptop and want to install ubuntu 23.04
what is best partition table for the config I attached?

I want to do this:
/ 80 GB
/swap RAM * 2 (12 GB)
/ home rest of  the sdd space

is it ok? 

thanks for your thoughts on this

---

### Post by oldfred on 2023-04-20
As Second Gen Intel it is both UEFI and BIOS boot.
If not using Windows in BIOS mode, better to use gpt partitioning whether Ubuntu is UEFI or BIOS.
If UEFI boot, you need an ESP - efi system partition FAT32 with boot,esp flags.
If BIOS boot, you need a bios_grub partition 1MB unformatted with bios_grub flag.
You do not need both, but if installing in BIOS mode, may want to have ESP, so you easily convert.
My early partitioning always was gpt but with ESP & bios_grub. Now having used UEFI for years, do not have a bios_grub except on one very old 2006 era BIOS only laptop.

Ubuntu now creates swap file of 2GB. Many suggest swap partition of 4GB.
Hibernation not recommended and old suggestions are mostly wrong now. The 2x RAM was back when you had 500MB or 1GB of RAM. If hibernating 1x RAM is required. 

I like to have ESP as first partition and swap as last partition, so the partitions that I really use are middle of drive. 
SSDs have dropped a lot in price, and upgrading to a SSD would greatly improve performance.

---

### Post by desatir73162 on 2023-04-20
Your answer was a little geeky for me and didnt understand swell but:
my laptop (dell n5110) does not support UEFI 
i only use ubuntu, not windows alongside or anything else, just ubuntu
i have 1 TB SSD and want to allocate most of the space for home partition

thanks you for your last reply, now by above information, what should I do !

---

### Post by ne29914 on 2023-04-20
30 GB is plenty for /
RAM + 25% is plenty for SWAP
Use the rest for /home

---

### Post by oldfred on 2023-04-20
I used to suggest 25 or 30GB for /, but my Kubuntu install which is somewhat smaller than Ubuntu is now 16GB and I do not allow snaps. 
I have seen some installs with snaps that use 20GB, just for the snaps.

Also if BIOS only system better to use a light weight flavor. Kubuntu is more middle weight, but I like it now over Ubuntu.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I typically have the current LTS version, now 22.04 as main working install. But like to install each 6 month release that is only valid for 9 months and then still have several obsolete installs as I have yet to overwrite them with new install.

---

### Post by desatir73162 on 2023-04-21
ok thanks
so just 3 partitions are needed? root, swap and home
is it enough? nothigng more?

---

### Post by yancek on 2023-04-21
If you are installing Ubuntu, it doesn't create a swap partition in a default install but rather a swap file.  Many new users use just one partition (/ the root filesystem) but other users like to have a separate /home partition.  That way, they can install a new version and not format their /home partition which simplifies things in some ways.  Some users prefer to use a /data partition rather than /home to keep personal files.  Your choice.

---

### Post by ActionParsnip on 2023-04-21
Yeah 80Gb for / is a lot. Can probably do 30Gb or 40Gb and be fine

---

### Post by ne29914 on 2023-04-21
> **desatir73162 said:**
> ok thanks
so just 3 partitions are needed? root, swap and home
is it enough? nothigng more?
Yes, that's enough. My Lubuntu 20.04 LTS currently uses 35% of 30 GB for /

Concerning swap: currently, Ubuntu seems to discourage using a swap partition; apparently some security "thing" is the reason. Until now, I've never seen an intelligently coherent description/explanation of the issue. It's either secret, or it doesn't really exist.

The question you need to ask yourself is: "do I need Hibernation?"
If yes, then you need a swap partition. If no, it's optional.

---

### Post by ActionParsnip on 2023-04-21
> **desatir73162 said:**
> ok thanks
so just 3 partitions are needed? root, swap and home
is it enough? nothigng more?

If you use UEFI you'd need a separate /boot partition

---

### Post by ne29914 on 2023-04-21
I think that's settled already (post #3).

---

### Post by grahammechanical on 2023-04-22
Have we talked about the drive's partition table? I do not think so. On a 1xterrabyte SSD it is best to use GUID Partition Table (GPT). It will allow a lot more partitions than the old ms-dos partition table which only allows four primary partitions. To have more than 4 partition with ms-dos partition table we need to put in place a work-around. This will complicate things.

With GPT and BIOS motherboard we need a 1MB BIOS-boot partition at the start of the drive. It will need to have the boot flag set. I am confirming what Old Fred said earlier.

> **BIOS-Boot or EFI partition (required on GPT disks)**
If you want to install Ubuntu on a **GPT disk**  (you can check it via the 'sudo parted -l' command), you will need  either an EFI partition (if your BIOS is set up in EFI mode) **or** a BIOS-Boot partition (if your BIOS is set up in Legacy mode). 

**BIOS-Boot partition:** 


[LIST]
[*]Mount point: none 
[*]Type: no filesystem 
[*]Description:  the BIOS-boot partition contains GRUB 2's core. It is necessary if you  install Ubuntu on a GPT disk, and if the firmware (BIOS) is set up in  Legacy (not EFI) mode. It must be located at the start of a GPT disk,  and have a "bios_grub" flag. 
[*]Size: 1MB. 
[/LIST]
**EFI partition:** 


[LIST]
[*]Mount point: /boot/efi  (no need to set up this mount point as the installer will do it automatically) 
[*]Type: FAT (generally FAT32) 
[*]Description:  the EFI partition (also called ESP) contains some boot files. It is  necessary if the firmware (BIOS) is set up to boot the HDD in EFI mode  (which is default on more and more modern, > year 2011 computers). It  must be located at the start of a GPT disk, and have a "boot" flag. 


[*]Size: 100~250MB
[/LIST]


[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

We can use Gparted from the Ubuntu Try session to set the drive's partition table and to format the drive.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-create-partition-table](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-create-partition-table)

We can also use GParted to create the partitions. And later if we want to we can use GParted to shrink partitions and create new ones.

After setting the drive's partition table it will be easier to use the Ubuntu installer's Erase Disc and Install Ubuntu option and then afterward use GParted to create a Data partition. It will then be possible to edit the fstab file to automatically mount the Data partition when Ubuntu loads. But that is another question for another thread.

Regards

---

### Post by svein.e on 2023-04-22
Format as GPT disk[COLOR=#000000]

/boot (550 MiB) (In most cases  100-250 MiB is enough)
/ 50 GB[/COLOR]
[COLOR=#000000]/swap 8 GB (at least size of RAM to make [/COLOR]Hibernation work[COLOR=#000000])[/COLOR]
[COLOR=#000000]/ home rest of the sdd space

The needed size of "/" partition is very dependent on how much software you will install and if you are using SNAP/Flatpak or simular.
[/COLOR]

---

### Post by ronaldljohnson on 2023-04-23
In this day and age with the caveat that you have more hard drive space then you'll probably need, ie hard drive space is cheap, i find simply having a swap partition and a root partition. Simplicity is not  only intoxicating but in most cases the best way to do it.

Having said that, there are reasons and scenarios that I would chop a disk up. The above mentioned simplicity is biased in the way that that is the way I would set up all my home systems for 'general' use. A reason that I might have a separate /home partition is if the system is truly multi-user and there are many users. In this case my reasoning would be for backup purposes. Easier to restore /home and add the users to an existing or new system than on a whole new rebuild. In fact this is the primary reason I would carve up a disk for most intents, that is to make the backup (and restore/disaster recovery) process a little more seamless.\

Another important reason I  might carve up disks into multiple partitions is if there are difference n the underlying hardware disk. For example if a portion of the filesystem mounts a SAN partition, uses some sort of shared root, home, or any other shared disk technology again, for seamless integration. I've architected instances where mirrored root partitions was standard and separate high performance disks on the internal bus or internal server was desired mainly for performance reasons. 

In general, I like home systems and general purpose systems a single partition for ease of use and server or production systems to have multiple parititons to ease the burden on administraton, either for performance reasons, backup/restore/distaster recovery/.

---

### Post by mikodo on 2023-05-06
Hi there. 

Tis an older thread now, and OP may have installed already and not see this response. 

Ubuntu 23.04 is what is called an Interim Release. This means, it has support for only 9 months, from Apr/23 and then support stops in Jan/24. One would have to Upgrade or Install to a newer Ubuntu release before then.

Long Term Support (LTS) releases of Ubuntu have 5 years of support for each install. Most people choose these releases. 

Choosing an Interim release, as 23.04 is, is not wrong. It can be less stable although, than LTS releases, and of course there is more work having to install newer releases, sooner.

Most current LTS release of Ubuntu, is Ubuntu 22.04. It  has about 4 years of support remaining with it. You might want to consider installing Ubuntu 22.04 for longer support. 

Ubuntu Releases Information: 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by TheFu on 2023-05-06
> **ne29914 said:**
>  
The question you need to ask yourself is: "do I need Hibernation?"
If yes, then you need a swap partition. If no, it's optional.

Have "some" swap changes the way the kernel behaves and enables many performance options that ZERO swap would prevent.  Hibernation really shouldn't be used by most people.  Use standby instead, unless you routinely need to hibernate for 3+ days.  I will completely shutdown a computer anytime it leaves the current building, but this is to ensure the encrypted disk is completely at rest during high-risk activities ... like walking between buildings on a campus or being in public areas where theft is possible.  I've had a few friends run into a grocery store on the way home and had their vehicles broken into during that 3 minute period - laptop stolen.

On a 20.04 system built last fall, that isn't used with a GUI, I'm seeing:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root--00                   ext4   35G   31G  1.7G  95% /
/dev/nvme0n1p2                              ext4  574M  280M  252M  53% /boot
/dev/nvme0n1p1                              vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg00-var                        ext4   54G   16G   37G  30% /var
/dev/mapper/WDBLK_8T-jellyfin               ext4   20G  7.1G   12G  39% /var/lib/jellyfin
/dev/mapper/vg00-home                       ext4   26G  9.9G   15G  41% /home

```
And as you can see 
```
$ journalctl --disk-usage
Archived and active journals take up 122.0M in the file system. 
```
The space isn't taken by run-away logs.
Also note that I've setup a separate /var and /home ... so the OS and installed programs are using 31GB.  I use lxd, so that snap and required support snaps for it are installed, but no others.

I suppose, there count be some hidden disk used underneath some mounts.  I can see just 7G of storage used with this:
```
$ sudo du -xsh  --exclude=/d  /* 2> /dev/null |sort -h
...
4.0K    /misc
4.0K    /opt
4.0K    /srv
8.0K    /media
16K     /lost+found
28K     /snap
36K     /mnt
2.3M    /run
8.8M    /tmp
16M     /etc
25M     /root
280M    /boot # this is a separate file system
6.5G    /usr
9.9G    /home # this is a separate file system
16G     /var # this is a separate file system

```
So, where's the other 25G on that system?  IDK and the most likely way to find it would be to boot off a USB flash drive and look "under" the mount locations were other file systems are now.

---

