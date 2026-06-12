---
title: "windows deleted my partitions, running from flash drive, &quot;invalid argument&quot; errors"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by evan3 on 2013-08-13
Hi,

I'm running an Acer netbook dual-boot with Windows XP and  Ubuntu 12.04. Or I was. While in Windows, I let a program make what I thought  was a minor adjustment to my partitions. I rebooted. Everything is gone.  First, I got a grub error "no such partition." So I booted with a flash  drive and took a look at my partitions with Gparted. It lists my entire  hard drive as "unallocated" and looking at details gives me the error  "invalid argument during seek for read on /dev/sda." fdisk gives me the  same "invalid argument." So do a lot of the other solutions I've looked  into. All of my data was on this drive so if I could recover any of it, I would be grateful. Thank you.

---

### Post by evan3 on 2013-08-13
So, I tried a few things on my own, which put the Windows partitions back into place, but I was unable to recover my old Ubuntu files. :(

Gdisk actually helped quite a bit. I was able to see that there were MBR partitions but no other types, and I let gdisk do its auto-correction. After that gparted was able to see my partitions... but there was a big gap. The Windows partitions were there but there was a big hole where Ubuntu used to be. I tried gpart and parted (and testdisk, but it kept saying it wasn't installed even though I installed it like 8 times). I thought about using some programs to recover the data, but nothing seemed to want to work with a live boot. So a gave up and reinstalled Ubuntu over the old partition, thus kilking my files. I'm trying to be Zen about it.

---

### Post by Brainwaste on 2013-08-13
Hello:
You need to resize/move the linux partition to fill the unallocated space. What does the fdisk output look like? Are you using a live disk with Gparted?

---

### Post by lukeiamyourfather on 2013-08-13
Sorry you lost some stuff. Now would be a good time to start a backup routine!

---

