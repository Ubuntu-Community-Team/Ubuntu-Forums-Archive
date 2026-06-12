---
title: "VPS Hard Drives"
date: 2017-02-11
forum: New to Ubuntu
---

### Post by leeryanrs on 2017-02-11
Hi There!

I'm pretty new to the linux area but i can usually get around. However i've just bought a VPS online for a little project and having some issues. I need a single drive on my machine and when doing lsblk, i get the below output.

[ATTACH=CONFIG]273643[/ATTACH]

Can someone explain what I have here? I'm supposed to just have a 70GB drive. I'm sure i'm mis-understanding something here, because I'm saying I have a 30GB, a 40GB drive and another 70GB drive?

---

### Post by ajgreeny on 2017-02-11
I never fully understand the output of lsblk so can you please show the output from ```
sudo parted -l
```
However it looks as if you have used LVM partitioning, which again is something I do not use nor understand
Please use **Code-Tags** for terminal output as copied text, rather than an image. See my signature below for a **How-to**.

---

### Post by leeryanrs on 2017-02-11
Hi there! Check the below, LVM is used as it seems to be their way of installing the OS. I have a simple dashboard where i choose to install the OS and it takes care of the rest. I cannot choose or guide the installation as it's the providers templates.

```
root@vps:~# sudo parted -lModel: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vps--vg-swap_1: 2147MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:


Number  Start  End     Size    File system     Flags
 1      0.00B  2147MB  2147MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vps--vg-root: 72.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:


Number  Start  End     Size    File system  Flags
 1      0.00B  72.5GB  72.5GB  xfs




Model: Virtio Block Device (virtblk)
Disk /dev/vda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  512MB   511MB   primary   ext2         boot
 2      513MB   32.2GB  31.7GB  extended
 5      513MB   32.2GB  31.7GB  logical                lvm




Error: /dev/vdb: unrecognised disk label
Model: Virtio Block Device (virtblk)
Disk /dev/vdb: 42.9GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:



```

---

