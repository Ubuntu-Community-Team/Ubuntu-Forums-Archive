---
title: "Best Partition Setup"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by bbemmerful on 2012-03-31
Need to install ubuntu 11.10 64 bit on a system using two hard drives 1 60 GB SSD . The other a 1 TB standard. I'm not sure how to set them up to take advantage of the speed of the SSD, should I just set the SSD as / and the 1TB as /home and swap?

---

### Post by Cheesemill on 2012-03-31
I have a similar setup, 64GB SSD and 1TB HD.
I have the following partition setup:

***[COLOR=DarkRed]SDA - 64GB SSD GPT Partition table aligned to SSD[/COLOR]***
sda1 - GRUB2 Boot Partition (Type EF02) 2MB
sda2 - /          ext4     25GB
sda3 - /home  ext4     35GB

***[COLOR=DarkRed]SDB - 1TB HD[/COLOR]***
sdb1 - /data    ext4   930GB
sdb2 - swap    swap      8GB

I use GPT on the SSD so that all of the partitions are aligned to the correct boundaries, using BIOS + GPT means I have to have a GRUB2 boot partition.

/home is on the SSD so that all of my user configuration files take advantage of the speed of the SSD. All of the main storage directories in /home are symlinked to /data (Videos, Music, Pictures etc).

Swap is at the end of the HD as that is the fastest part although I don't think it is ever used (8GB RAM and swapiness set to 0) as I never hibernate, it's just there for when I'm really hammering the VM's.

A bit complicated I know, but hey, I know what I'm doing :)

Also if you are using a kernel >2.6.33 make sure you specify the discard option in /etc/fstab to take advantage of TRIM.

---

### Post by bbemmerful on 2012-03-31
Thankyou! I think you know what your doing.:lolflag:

---

### Post by Bucky Ball on 2012-03-31
> **bbemmerful said:**
>  should I just set the SSD as / and the 1TB as /home and swap?

Yes, unless you want to share with a Windows install. Then you will need an NTFS partition somewhere.

Cheesemill's partitioning obviously suits their needs but might not suit yours. If all you need is /, /home and /swap, then by all means do that just as you suggested originally ... ;)

[QUOTE=Cheesemill]Swap is at the end of the HD as that is the fastest part ...[/QUOTE]

This old chestnut. The outer edge (first partition) is actually the quickest. Closer to the centre gets slower. Nowadays it doesn't make a lot of (noticeable) difference.

---

