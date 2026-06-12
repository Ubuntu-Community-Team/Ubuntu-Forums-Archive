---
title: "Compaq Presario v5000 optimal configuration"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by animalprimate on 2008-05-13
**current hda**

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3430    27551443+   7  HPFS/NTFS
/dev/hda2            3431        3710     2249100   82  Linux swap / Solaris
/dev/hda3            3711        9448    46090485   83  Linux
/dev/hda4            9449        9729     2257132+  82  Linux swap / Solaris

**cpu info**

animalprimate@animalprimate-laptop:/$ head /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : Mobile AMD Sempron(tm) Processor 3300+
stepping        : 2
cpu MHz         : 800.000
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no

**mem info**

animalprimate@animalprimate-laptop:/$ head /proc/meminfo
MemTotal:       904012 kB
MemFree:         15732 kB
Buffers:        121072 kB
Cached:         463808 kB
SwapCached:          0 kB
Active:         453068 kB
Inactive:       315236 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       904012 kB

This is how I've come to install Ubuntu, i have windows xp install disk, gparted, and ubuntu install disk.  I'm unsure what the optimal way to install would be however for my notebook.  Based on this info what would you do to optimize performance, security, etc. in the way of partitioning/improving this **Compaq Presario v5000?**

p.s. my cpu frequency monitor goes up to 2g but its been low usually while i work like about 800 MHz.

thanks, absolutely
Animalprimate
p.e.a.c.e.

---

### Post by andrewski on 2008-06-11
I'm not sure what you're asking. You have Ubuntu on it now? You're looking to optimize performance from the computer? Can you describe?

---

### Post by Neil Purling on 2008-12-06
I have acquired my brother's Compaq V5000 laptop.
How can you get it's wireless feature working to connect with my wireless home network? Has anyone any experiences to offer?
I plugged in the network cable, and up came Google & I found my way here.
I thought that maybe this version of Ubuntu I installed V6.06 (Dapper Drake) does not support wireless devices.
I am looking to upgrade when I receive the CD-ROM of Intrepid Ibex from canonical. I don't want to have the same issue if I install that.

---

### Post by andrewski on 2008-12-07
There were a lot of changes between Dapper (6.06) and Hardy (8.04), since there were two years between them :), and Hardy solidified a lot of wireless support. So Hardy has become a really good baseline for wireless support. Intrepid should be the same in most respects (although I can't speak for the v5000) and you should be good to go.

Best advice: Boot to the LiveCD and see how the wireless support is. If it works, you'll be good to go, but if not, you *may* be able to get it working beyond that. Post back how it goes!

---

### Post by lkraemer on 2008-12-08
If your Compaqpario is a V5201US, I have some specific instructions
I can email that details how I got my Wifi working.  The Wifi button
even works and I just love running Ubuntu 8.04LTS on mine.  Maybe I
can help with other questions.?!

lkraemer

---

