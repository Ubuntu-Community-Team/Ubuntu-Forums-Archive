---
title: "Can't find my Windows OS after 12.04 install"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by tazz4vr on 2012-04-27
Hello again....
I have installed 12.04 LTS along side Windows.  In previous version of 11.10, I was able to see my Windows OS under the 'Devices' while in my Home folder, unfortunately I am unable to even find the Windows OS.... Help!

---

### Post by personaprospekt on 2012-04-27
Did you mount it? does the partition show up in /dev?

---

### Post by oldfred on 2012-04-27
Post this from terminal:

```
sudo fdisk -lu
```

---

### Post by tazz4vr on 2012-04-27
> **oldfred said:**
> Post this from terminal:

```
sudo fdisk -lu
```

Here is what I got...

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7950ddd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20973567    10485760   27  Hidden NTFS WinRE
/dev/sda2   *    20973568   166744063    72885248    7  HPFS/NTFS/exFAT
/dev/sda3       166744116   312575759    72915822    7  HPFS/NTFS/exFAT

```

---

### Post by Mark Phelps on 2012-04-27
In a wubi install, you don't Mount the Windows partition, it is already mounted for you.  Go to /host in the filesystem to see it.

---

### Post by oldfred on 2012-04-27
You do not have an along side or in a separate partition install. You must have wubi with is a folder inside the NTFS partition and wubi uses the Windows boot loader not grub2's boot loader in the MBR. You do get a grub menu after the Windows menu.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I believe that wubi shows the c: drive as /host in the left panel of Nautilus or file browser.

---

### Post by tazz4vr on 2012-04-27
Found it, thank you very much!

---

