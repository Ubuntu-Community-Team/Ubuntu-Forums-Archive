---
title: "copy small partition to free space, now same UUID, same mount point"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by Morpholinux on 2012-02-22
ok I am new to this stuff (partitions )so...I'll try my best

1> installed Ubuntu 11.10 in the whole disk (few monts ago)
2> Shrinked Ubuntu's partition and installed Lubuntu 11.10 with 21 GiB

Yesterday my lubuntu partition was almost full 
```
df -h
``` gimme 97% used

I tried to make it bigger with gparted but did not work. (there was no free space at all)
So I shrinked Ubuntu again
And try to get a bigger partition for Lubuntu, but without luck
My logic was, "uhmmm ok I will copy my small partition of Lubuntu (21GiB) to this free space (48(GiB), then delete the original partition and this way I will get more space for Lubuntu"

Here is the gparted screenshot (attached)
After rebooting I think I was going to saw 3 entries, but no!
I think it was because I didnt do
```
update-grub
```
So I did that,
reboot again
I still saw only 2 entries
One is Lubuntu (48 Gib) and the other is Ubuntu (now 73GiB)
The problem is that both Lubuntu partitions confuse my system
It is an exact copy so they have same UUID, same Path where to  be mounted, same mount point etc
I want to delete the original partition of Lubuntu, because now I have the copy in a bigger partition, but gparted wont let me do it 

"The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually."

I am not sure what to do next...

here is  my fdisk ouput>
```
fmp@lillith:~/Desktop/tesis/dcds_low/npdbfrmt$ sudo fdisk -l
[sudo] password for fmp: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000021ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   154626047    77312000   83  Linux
/dev/sda2       256849918   312580095    27865089    5  Extended
/dev/sda3       154626048   256847871    51110912   83  Linux
/dev/sda5       306311168   312580095     3134464   82  Linux swap / Solaris
/dev/sda6       256849920   300038143    21594112   83  Linux
/dev/sda7       300040192   306294783     3127296   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Morpholinux on 2012-02-22
here is the image :P

---

### Post by oldfred on 2012-02-23
Post this to see UUIDs:

sudo blkid

You will have to change one or more UUIDs.

If you change UUIDs that system/partition will need changes to fstab and grub to make it work with new UUID. 

Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

---

### Post by Morpholinux on 2012-02-23
```

sudo blkid
/dev/sda1: LABEL="ubuntu" UUID="7ffe1375-a1a1-4e6d-bed4-e55c51134070" TYPE="ext4" 
/dev/sda3: LABEL="lubuntubig" UUID="211cb479-5440-461e-99ac-c2d5bef62a3d" TYPE="ext4" 
/dev/sda5: UUID="1f906c62-aa66-45a5-ad10-d055692289a9" TYPE="swap" 
/dev/sda6: UUID="211cb479-5440-461e-99ac-c2d5bef62a3d" TYPE="ext4" 
/dev/sda7: UUID="12b26a7e-bc00-4bf9-8f9e-986bda3503ca" TYPE="swap" 
/dev/sdb1: LABEL="MURPHOLINOX" UUID="1103-091D" TYPE="vfat"
----------------------------------------------------------------
sudo tune2fs -U fc44597d-6732-4a92-b66e-1a1bb3f4cd57 /dev/sda6
tune2fs 1.41.14 (22-Dec-2010)
----------------------------------------------------------------
sudo blkid
/dev/sda1: LABEL="ubuntu" UUID="7ffe1375-a1a1-4e6d-bed4-e55c51134070" TYPE="ext4" 
/dev/sda3: LABEL="lubuntubig" UUID="211cb479-5440-461e-99ac-c2d5bef62a3d" TYPE="ext4" 
/dev/sda5: UUID="1f906c62-aa66-45a5-ad10-d055692289a9" TYPE="swap" 
/dev/sda6: UUID="fc44597d-6732-4a92-b66e-1a1bb3f4cd57" TYPE="ext4" 
/dev/sda7: UUID="12b26a7e-bc00-4bf9-8f9e-986bda3503ca" TYPE="swap" 
/dev/sdb1: LABEL="MURPHOLINOX" UUID="1103-091D" TYPE="vfat" 


```

it worked!
now what? update-grub?

---

### Post by oldfred on 2012-02-24
Your grub in sda is probably booting from the old UUID or sda3. If you want to boot from sda6 you will have to manually edit fstab with the new UUID and edit the UUID for grub in sda6.

Boot into sda3 and run 
sudo update-grub

But it may also find the old wrong UUIDs if grub.cfg not yet updated. You may have to manually edit them to boot sda6.

You chould chroot into sda6, but it may just be easier to violate the rule of not editing grub.cfg. Then if you boot from the menu in sda3 and choose the install in sda6 you should be able to boot and another update-grub should find the new UUID. You proably have to rerun the sudo update grub in sda3.

If fstab is updated you could use this in the 40_custom of the install in sda3 to boot sda6.

#Add menu entry to 40_custom, change example from sda13 to your partition sda6.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober if you want to always boot from teh boot stanza in 40_custom
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub
sudo dpkg-reconfigure grub-pc

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

