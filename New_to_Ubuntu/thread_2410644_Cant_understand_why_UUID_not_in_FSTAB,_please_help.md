---
title: "Cant understand why UUID not in FSTAB, please help"
date: 2019-01-18
forum: New to Ubuntu
---

### Post by robertzito on 2019-01-18
Can someone help explain this, I keep getting errors that FAT-fs (nvme0n1p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

From From sudo blkid

```

NAME          MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda             8:0    0 931.5G  0 disk  
&#9492;&#9472;sda1          8:1    0 931.5G  0 part  /media/rzito/ExtraDrive1
sdb             8:16   0   1.8T  0 disk  
nvme0n1       259:0    0   477G  0 disk  
&#9500;&#9472;nvme0n1p1   259:1    0   512M  0 part  /boot/efi
&#9500;&#9472;nvme0n1p2   259:2    0     4G  0 part  
&#9500;&#9472;nvme0n1p3   259:3    0 468.4G  0 part  /
&#9492;&#9472;nvme0n1p4   259:4    0     4G  0 part  
  &#9492;&#9472;cryptswap 253:0    0     4G  0 crypt [SWAP]

```

From sudo lsblk
```

/dev/nvme0n1p1: LABEL="EFI" UUID="9F47-041F" TYPE="vfat" PARTLABEL="primary" PARTUUID="e6013468-f017-4dc0-a663-e0e91054c2f5"
/dev/nvme0n1p2: LABEL="RECOVERY" UUID="9F4E-C543" TYPE="vfat" PARTLABEL="primary" PARTUUID="4fa95bb9-c43f-476c-968a-1a4b252e01a2"
/dev/nvme0n1p3: UUID="8f4cf8a5-ad93-4ada-96ab-69334ee70a7a" TYPE="ext4" PARTUUID="f9b7f0a8-1d57-417c-a73d-d21677936575"
/dev/nvme0n1p4: UUID="dcc9fa79-8269-47ee-99c7-985f33c8eca5" TYPE="swap" PARTLABEL="primary" PARTUUID="a55dea69-1b27-4fc5-a25d-33f276d9176f"
/dev/sda1: LABEL="ExtraDrive1" UUID="9b802392-fb1a-46d2-bb7a-11cb08da2440" TYPE="ext4" PARTLABEL="primary" PARTUUID="79e8a857-7536-4c83-9323-34c9b8852fe3"
/dev/mapper/cryptswap: UUID="5e73badc-3373-4150-8d25-3f69e61cf701" TYPE="swap"
/dev/sdb: LABEL="Disk 2" UUID="6ec02c60-d68c-4374-9a68-1e1822f950a7" TYPE="ext4"
/dev/nvme0n1: PTUUID="139ef9ba-b517-46a9-aa0a-d155a4ca9f7a" PTTYPE="gpt"


```

In FSTAB
```

 <file system>  <mount point>  <type>  <options>  <dump>  <pass>
UUID=9F47-041F  /boot/efi  vfat  umask=0077  0  0
UUID=8f4cf8a5-ad93-4ada-96ab-69334ee70a7a  /  ext4  noatime,errors=remount-ro  0  0
/dev/mapper/cryptswap  none  swap  defaults  0  0

```

In Cryptswap I am seeing this error:

```

mkswap[727]: no label, UUID=d1af842a-410b-48fb-bf3c-d55d0c74ef6e

```

---

### Post by TheFu on 2019-01-18
What is the point of having swap encrypted, when nothing else is too?
I would say that is useless.

---

### Post by robertzito on 2019-01-18
Thats the way the system came.. It is a System 76 laptop, linux was the only os no windows.

---

### Post by yancek on 2019-01-18
The partition referred to "nvme0n1p1" is the first partition on that device which is the EFI partition, a FAT32 filesystem.  If your Ubuntu system came pre-installed with EFI, did it work when you got it?  Did you make or try to make any changes which would have affected the EFI partition with boot files?  The message indicates it was not properly unmounted so??  I'm also wondering what the second vfat partition is if this is only Ubuntu.  It's common to have multiple windows vfat/ntfs partition on a windows install.  I'm not familiar wtih System76 computers so that may not be a problem.  You can try to run a filesystem check by following the instructions at the link below.  You might need to install the software referenced. 

[https://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system](https://askubuntu.com/questions/147228/how-to-repair-a-corrupted-fat32-file-system)

> mkswap[727]: no label, UUID=d1af842a-410b-48fb-bf3c-d55d0c74ef6e

I don't know what changes were made/attempted but if you look at the UUID referenced above, you will see that from your blkid output it does not exist.

---

### Post by The Cog on 2019-01-18
> **TheFu said:**
> What is the point of having swap encrypted, when nothing else is too?
I would say that is useless.

I think many programs these days keep decrypted keys and passwords in memory, or in /dev/shm to avoid committing them to disk. Encrypting swap prevents them being left unencrypted on disk if memory gets swapped out.

---

