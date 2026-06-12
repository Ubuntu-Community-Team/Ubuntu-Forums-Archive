---
title: "Partitioned disk with / root file system and /home"
date: 2024-02-15
forum: New to Ubuntu
---

### Post by rickiewalkson1 on 2024-02-15
Hi there,
while setting up my Ubuntu system I partitioned the system with the following partitions
/ root file system and /home

My intention was to LUKS encrypt one of these partitions. Since I am very new to Linux, I got some questions with this regards.
1. Does it make sense to encrypt / root file system? Does it make sense to encrypt /home? Does it make sense at all to partition in the manner I did?
2. Since I do not have a lot of knowledge to use the terminal yet, I was wondering whether I shall access the root file system via the file explorer 'nautilus' similar to Home and the other directories.

My main intention is to have one partition which is encrypted and is easily accessible via the file manager nautilus or similar.

Thank you so much
Rickie

---

### Post by grahammechanical on 2024-02-15
Most of your question I cannot answer. I can tell you this. When we have a /root partition and a separate /home partition we can re-install without overwriting the /home partition. This is how: 

Select the manual partitioning option. Select the present /root partition. Select "change" and mount it as / and also mark it to be formatted. This clears away any settings that may be causing problems.

Then, select the present /home partition. Select "change" and mount it as /home but do not mark it to be formatted. Then the installer will set up the system with separate /root and /home partitions and all your documents/files etc. will be untouched and available as usual. 

Remember, it is always wise to backup any data you cannot afford tom lose.

Regards

---

### Post by rickiewalkson1 on 2024-02-16
Thank you very much. As this all seems to be a bit complicated, I probably will go for a reinstall without partitioning and simply try to apply the installer built in encryption mechanism.
Best regards

---

### Post by ActionParsnip on 2024-02-16
Just keep a 2Gb file system for /boot and leave that unencrypted. The rest you can encrypt (Not sure about encrypted swap though, personally)

Been playing with Tang servers all day so.....yayyy #headache

---

### Post by TheFu on 2024-02-16
> **rickiewalkson1 said:**
> My intention was to LUKS encrypt one of these partitions. Since I am very new to Linux, I got some questions with this regards.

During the installation, there is a check box to encrypt the system.  Check that and accept the defaults.  It will wipe the disk, so you'll need to understand that. This will setup the partitions you need, create an excellent LUKS container for the 3rd partition, then put LVM inside that LUKS container.  Do the install and be happy.

If you want to split out different storage areas - and you should - then you'll need to learn LVM.  While I don't have LUKS installed, I do use LVM. Here's my setup for the OS
```
NAME                             TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL          MOUNTPOINT
nvme0n1                          disk                    931.5G                               
&#9500;&#9472;nvme0n1p1                      part  ext2                  1M                               
&#9500;&#9472;nvme0n1p2                      part  vfat                 50M   43.9M    12%                /boot/efi
&#9500;&#9472;nvme0n1p3                      part  ext4                700M  339.9M    42%                /boot
&#9492;&#9472;nvme0n1p4                      part  LVM2_member       930.8G                               
  &#9500;&#9472;vg01-swap01                  lvm   swap                4.1G                               [SWAP]
  &#9500;&#9472;vg01-root01                  lvm   ext4                 35G   25.2G    21%                /
  &#9500;&#9472;vg01-var01                   lvm   ext4                 20G   14.2G    22%                /var
  &#9500;&#9472;vg01-tmp01                   lvm   ext4                  4G    3.6G     0% tmp01          /tmp
  &#9492;&#9472;vg01-home01                  lvm   ext4                 20G    9.4G    47% home01         /home

```
I've edited it for simplicity.  Basically, all of partition #4 is for LVM, but you can think of that as the LUKS container. Those lines with "vg01" in them are LVM Logical Volumes.

By default, I think the LUKS+LVM install option will make a "root" LV and a "swap" LV. The root LV will be too large.  There are reasons to make it 35G, not larger.  It is best, immediately post-install, to reduce the root LV to 35G, create a small area for the home LV (perhaps 20G) and deal with the other areas later, when you need them.

Key ideas with LVM is that reducing the size of an LV is hard - about like reducing the size of a partition. It is a hassle.  However, increasing the size of an LV is trivial, requires zero downtime or even slowing down the running system.  It takes about 5 seconds, assuming the Volume Group, VG, has storage available.  Nobody is good at predicting the future. In 30 yrs, I've never gotten it correct, but with LVM, I don't need to be correct.
Not that my NVME is 1G, but my allocations are just what I need.  When I need more storage, I'll extend the LV where more storage is needed.  Very flexible.  This is important when storage is encrypted.    I try to actually allocate just the storage that will be used in the next 3 months.

If all this seems complicated, you definitely aren't ready to manually do LUKS encryption.  It is 10x harder.

---

### Post by MAFoElffen on 2024-02-17
@Actionparsnip --
Since 22.04, it cam with grub2 version 2.06. That version and newer can read an encypted LUKS2 Boot partition. prior to that, with 20.04, you could have  LUKS2 partitions for / (root OS) and others (such as /home and /data) and encrypted /boot, if that partition was LUKS1.

The limitation of 22.04 with Grub2 2.06, is that if the /boot partition is LUKS2, you have to ensure that the key derivation is PBKDF2, not Argon2. Grub2 version 2.12rc1 added more support of LUKS2 but with similar limitations.

This is the post I direct people to for dong it for 20.04. For 22.04 is similar, but simpler, because you can do a LUKS2 /boot, but again, ensuring the key type is created with PBKDF2...
[https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144)

*** Those will only work with the Ubuntu Desktop Installers up to and including Jammy (22.04). After that, I have an open bug report on the partitioner in the newer installer, that it will not recognize LVM or LUKS volumes. So we lost that ability of doing installs like that after Jammy. It still works with the Server Edition Installer, but then all the typing is manually.

---

### Post by MAFoElffen on 2024-02-18
If you search on my User name in this forum, you will find instructions I posted on creating a LUKS encrypted volumes with booting from a USB key with the keyfile...

In those instructions where all the commands to do full disk encryption and how to add the volumes to the /etc/crypttsab, which there is where you would add a created keyfile entry for a separate home... I've work with those for a while ow, so is just a whole lot of typing. I usually make a recipe file, where I work everythig out it there first... Let s me see if I have one of those on this laptop...

Here you go. One of my recipes:
```

### Encryted LUKS with LVM2

# Become root
sudo su

# Create an alias variable, as a shortcut to typing it out each time
DISK=$(ls -l /dev/disk/by-id | awk '/sda/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
echo -e "Disk found: $DISK"


# This is a USB for my keyfile
USB=$(ls -l /dev/disk/by-id | awk '/usb/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
echo -e "USB found: $USB"


DEST=/keystore/luks.key
mkdir /keystore
mount $USB-part1 /keystore
openssl genrsa -out $DEST 4096
chmod -v 0400 $DEST
chown root:root $DEST


# Partition the disk 
sgdisk  -n1:1M:+750M -t1:EF00 -c1:EFI  $DISK  # Create EFI partition
sgdisk  -n2:0:+2G    -t2:8300 -c2:BOOT $DISK  # Create Boot partition
sgdisk  -n3:0:+25G   -t3:8309 -c3:ROOT $DISK  # Create Root partition
sgdisk  -n4:0:0      -t4:8309 -c4:HOME $DISK  # Create Home partition

# Display partition table
sgdisk -p $DISK


# Format EFI partition
mkfs.vfat -F 32 -s 1 -n EFI ${DISK}-part1

# Format Boot partition
mkfs.ext4 -L BOOT ${DISK}-part2


# Create LUKS2 container and format for ROOT (part3)
cryptsetup luksFormat --type luks2 -c aes-xts-plain64 -s 512 -h sha256 ${DISK}-part3

cryptsetup luksAddKey ${DISK}-part3 $DEST

cryptsetup luksConvertKey --key-slot 0 --pbkdf pbkdf2 ${DISK}-part3
cryptsetup luksConvertKey --key-slot 1 --key-file /keystore/luks.key --pbkdf pbkdf2 ${DISK}-part3


cryptsetup luksOpen ${DISK}-part3 luks1

# Create LUKS2 container and format for HOME (part4)
cryptsetup luksFormat --type luks2 -c aes-xts-plain64 -s 512 -h sha256 ${DISK}-part4

cryptsetup luksAddKey ${DISK}-part4 $DEST

# cryptsetup luksConvertKey --keyslot 0 --pbkdf pbkdf2 ${DISK}-part4
# cryptsetup luksConvertKey --keyslot 1 --key-file /keystore/luks.key --pbkdf pbkdf2 ${DISK}-part4

cryptsetup luksOpen ${DISK}-part4 luks2

# Encrypted LVM root and swap inside LVM lv_root

# Verify that keys are set in the keyslots
sudo cryptsetup luksDump ${DISK}-part3 
sudo cryptsetup luksDump ${DISK}-part4

# Create LVM2
pvcreate /dev/mapper/luks[2,3]

vgcreate vg_ubuntu /dev/mapper/luks1
vgcreate vg_home /dev/mapper/luks2

lvcreate -L+6G      -n lv_swap vg_ubuntu 
lvcreate -l 80%FREE -n lv_root vg_ubuntu
lvcreate -l 80%FREE -n lv_home vg_home

### 
# Leave that terminal session open...
#
# Start up installer. When it gets to the partition stage, choose "Something else"...
#
# Select /dev/sda1. Change. Use as EFI filesystem.
#
# Select /dev/sda2 (Linux device-mapper (crypt)). Change. Use as ext4, /boot.
#
# Select /dev/mapper/vg_ubuntu-lv_root (Linux device-mapper (crypt)). Change. Use as ext4, format, /.
#
# Select /dev/mapper/vg_home-lv_home. Change. Use as ext4, format, /home.
#
# Select /dev/mapper/vg_ubuntu-lv_swap. Change
#
# Continue Install. At completion, DO NOT REBOOT. Instead choose "Continue # Testing".
#
# Go back to the open terminal session, which you are still root...
###
mkdir -p /target
MapMount=$(ls /dev/mapper/vg_ubuntu-lv_root)
mount $MapMount /target
for DIR in proc sys dev /etc/resolv.conf; do mount --rbind /$DIR /target/$DIR; done
chroot /target
mount -a

## Reset Var's inside chroot
DISK=$(ls -l /dev/disk/by-id | awk '/sda/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
USB=$(ls -l /dev/disk/by-id | awk '/usb/ {print "/dev/disk/by-id/"$9}' | head -n 1 )


blkid | grep 'sda\|sdb' | grep -e 'crypto_LUKS\|SWAP' | awk '{print $1 " " $2 " " $4}' | sort
# copy that output to an editor...


## Add UUID's to crypttab
echo -e "# <name>  <device>     <password>     <options>" >> /etc/crypttab
echo -e "#luks1 UUID=\"$(blkid -s UUID -o value ${DISK}-part3)\" none luks" >> /etc/crypttab
echo -e "luks1 UUID=\"$(blkid -s UUID -o value ${DISK}-part3)\" /keystore/luks.key luks" >> /etc/crypttab 
echo -e "#luks2 UUID=\"$(blkid -s UUID -o value ${DISK}-part4)\" none luks" >> /etc/crypttab
echo -e "luks2 UUID=\"$(blkid -s UUID -o value ${DISK}-part4)\" /keystore/luks.key luks" >> /etc/crypttab

grep . /etc/crypttab


## fstab
mkdir /keystore
echo -e "UUID=$(blkid | awk -F [\ =] '/sda1/ {print $7}') /keystore     vfat  defaults,umask=0077  0 2" >> /etc/fstab
mount /keystore


## Add this line to /etc/default/grub
echo -e "GRUB_ENABLE_CRYPTODISK=y" >> /etc/default/grub
update-grub

sudo nano /etc/cryptsetup-initramfs/conf-hook
## Uncomment and change this line to:
KEYFILE_PATTERN="/keystore/*.key"


### RESCUE (chroot into system from LiveUSB)
sudo su

DISK=$(ls -l /dev/disk/by-id | awk '/sda/ {print "/dev/disk/by-id/"$9}' | head -n 1 )
USB=$(ls -l /dev/disk/by-id | awk '/usb/ {print "/dev/disk/by-id/"$9}' | head -n 1 )

mkdir /keystore
mount ${USB}-part1 /keystore
DEST=/keystore/luks.key

cryptsetup luksOpen ${DISK}-part3 luks1 --key-file $DEST
cryptsetup luksOpen ${DISK}-part4 luks2 --key-file $DEST

pvscan
vgscan
lvscan

mount /dev/mapper/vg_ubuntu-lv_root /mnt
for DIR in proc sys dev /etc/resolv.conf 
do 
    mount --rbind /$DIR /mnt/$DIR 
done
chroot /mnt

mount -a

####


# fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vg_root-lv_root /               ext4    errors=remount-ro 0       1
#/dev/mapper/luks1 /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=3B24-07E9  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/vg_home-lv_home /home           ext4    defaults        0       2
#/dev/mapper/vg_swap-lv_swap none            swap    sw              0       0
/dev/mapper/vg_swap-lv_swap none swap defaults 0 0
UUID=09660ab9-d621-4752-b1f7-fc1e7118979a  /boot       ext4    defaults      0       2
UUID="4987-2A68"    /keystore    vfat    defaults 0 2

nano /etc/cryptsetup-initramfs/conf-hook
KEYFILE_PATTERN="/keystore/*.key"

```
That shoudl get you started with how that can work for you. That may be a bit more to grasp if you are new... But enough to start looking at guides and man pages to see what is going on, and to learn how that works, and what the possibilities can be.

---

