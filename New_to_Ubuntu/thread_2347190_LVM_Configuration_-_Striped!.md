---
title: "LVM Configuration - Striped!"
date: 2016-12-22
forum: New to Ubuntu
---

### Post by faults2 on 2016-12-22
Hey,

My goal is to Pimp my Disk Performance high as possible. I was thinking just RAID 0, but I want to learn also something new and I heard about this new stuff called LVM2. (I know that Pure raid 0 might bit faster than LVM)


Steps what I have done: 1) On Ubuntu install I choosed LVM. After install I added my second SSD to that Ubuntu-vg.

**Physical Volumes:**
```
PV         VG        Fmt  Attr PSize   PFree
  /dev/sda3  ubuntu-vg lvm2 a--  231,91g    0 
  /dev/sdb1  ubuntu-vg lvm2 a--  223,57g    0 
```

**Volume Groups:**
```
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               455,47 GiB
  PE Size               4,00 MiB
  Total PE              116601
  Alloc PE / Size       116601 / 455,47 GiB
  Free  PE / Size       0 / 0   
  VG UUID               cuQikN-h39W-WYoP-gKLh-4SAH-AcPB-UDSjUy
```

**Logical Volumes:**
```
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                0WEqf8-eJ5Q-goG3-ezOg-IuZp-BL7O-4SRHen
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-12-20 17:28:26 +0200
  LV Status              available
  # open                 1
  LV Size                439,59 GiB
  Current LE             112536
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                WzV2vK-QXB1-MiBt-PMk1-3WQh-2bu7-gZFqAK
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-12-20 17:28:26 +0200
  LV Status              available
  # open                 1
  LV Size                15,88 GiB
  Current LE             4065
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
```

**Problem?**
```
  LV     VG        Attr       #Str Type   SSize  
  root   ubuntu-vg -wi-ao----    1 [COLOR=#ff0000]linear[/COLOR] 216,02g
  root   ubuntu-vg -wi-ao----    1 [COLOR=#ff0000]linear[/COLOR]  12,00m
  root   ubuntu-vg -wi-ao----    1 [COLOR=#ff0000]linear[/COLOR] 223,57g
  swap_1 ubuntu-vg -wi-ao----    1 [COLOR=#ff0000]linear[/COLOR]  15,88g
```



I think I have made a mistake on some point and I think my disks are not Striped? I tried to figure out what I should do to make LVM work as Striped mode and give me all Performance I can get from disks. Single Point of Failure is OK for me... no one lives forever. :)

In future I plan also add mSATA SSD to my Laptop so I can have 3x SSD disk in my pool.

What should I do next? Totally OK option is to do Full Reinstall also. I have very basic install of Ubuntu 16.10.



[B]My Spec:

```
System:    Host: mutteri Kernel: 4.8.0-32-generic x86_64 (64 bit gcc: 6.2.0)
           Desktop: Unity 7.5.0 (Gtk 3.20.9-1ubuntu2) Distro: Ubuntu 16.10
Machine:   System: LENOVO (portable) product: 4284W1T v: ThinkPad W520
           Mobo: LENOVO model: 4284W1T UEFI: LENOVO v: 8BET62WW (1.42 ) date: 07/26/2013
Battery    BAT0: charge: 81.1 Wh 99.9% condition: 81.2/93.6 Wh (87%) model: LGC 45N1011 status: N/A
CPU:       Quad core Intel Core i7-2820QM (-HT-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 18340
           clock speeds: max: 3400 MHz 1: 1158 MHz 2: 933 MHz 3: 1036 MHz 4: 1178 MHz 5: 1088 MHz 6: 1190 MHz
           7: 1186 MHz 8: 945 MHz
Graphics:  Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0
           Card-2: NVIDIA GF108GLM [Quadro 1000M] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: Quadro 1000M/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 340.101 Direct Rendering: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.8.0-32-generic
Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e v: 3.2.6-k port: 5080 bus-ID: 00:19.0
           IF: enp0s25 state: up speed: 1000 Mbps duplex: full mac: f0:de:f1:79:43:cd
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak] driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: down mac: 08:11:96:15:ba:94
Drives:    HDD Total Size: 490.1GB (37.1% used) ID-1: /dev/sda model: Samsung_SSD_850 size: 250.1GB temp: 0C
           ID-2: /dev/sdb model: KINGSTON_SHSS37A size: 240.1GB temp: 32C
Partition: ID-1: / size: 432G used: 154G (38%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 473M used: 137M (31%) fs: ext2 dev: /dev/sda2
           ID-3: swap-1 size: 17.05GB used: 0.21GB (1%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.0C mobo: N/A gpu: 0.0:43C
           Fan Speeds (in rpm): cpu: 2722
Info:      Processes: 301 Uptime: 2:29 Memory: 7832.3/15925.7MB Init: systemd runlevel: 5 Gcc sys: 6.2.0
           Client: Shell (bash 4.3.461) inxi: 2.3.1 

```
[/B]

---

### Post by TheFu on 2016-12-22
LVM isn't new. LVM2 was new in the early 2000s. New to you is one thing.  Lots of things are new to me. ;)

Showing the results without the actual commands used isn't very helpful. What commands did you enter for the pv/vg/lv creation?

Google found this: [http://www.tldp.org/HOWTO/LVM-HOWTO/recipethreescsistripe.html](http://www.tldp.org/HOWTO/LVM-HOWTO/recipethreescsistripe.html)

The only trick is when creating the LV.
```
# lvcreate -i2 -I4 -L1G -nmy_logical_volume my_volume_group
```

From the **lvcreate** ***manpage***:
```
       -i, --stripes Stripes
              Gives the number of stripes.  This is equal to the number of physical  volumes  to
              scatter the logical volume.

       -I, --stripesize StripeSize
              Gives the number of kilobytes for the granularity of the stripes.
              StripeSize  must be 2^n (n = 2 to 9) for metadata in LVM1 format.  For metadata in
              LVM2 format, the stripe size may be a larger power of 2 but must  not  exceed  the
              physical extent size.

``` Always check the manpages on YOUR system. My system might have a different version of the tool, with different options.

---

### Post by faults2 on 2016-12-23
Thanks! Okey, LVM2 is what I use and new stuff to me... seems not new to rest. That good, I might get some proper help from experienced users! :) I have googled ALOT about guides of LVM2, but its still some parts to bit fuzzy and needs to get used to the idea of if which is brilliant!

What I did in order:

**1)** Installed Ubuntu with LVM switched on --> Auto-Created **ubuntu-vg** with one SSD included
**2)** I formated and created partition on my second SSD: /dev/sdb --> /dev/sdb1
**3) **pvcreate /dev/sdb1
**4)** vgextend /dev/sdb1
**5)** lvextend -l +100%FREE /dev/ubuntu-vg/root [COLOR=#ff0000]**( I should have included -i switch for Striping and -I stripesize ! )**[/COLOR]
**6)** resize2fs /dev/ubuntu-vg/root


I might need to remove fully the second disk and re-add it with stripe switch? Or... ?

---

### Post by TheFu on 2016-12-23
I've never done what you are trying to do.  My largest data loss incident was due to LVM extending a file system across 3 disks. 1 of those disks failed. Lost all the data across the other 2 drives too.

I didn't have backup religion back then. I do now.

Think the LV must be created with the correct stripe options.  Make sense?  If you only want a portion of the storage to be striped, that can make life easier, since the OS wouldn't be striped, just the data LV.  Then you could do it post-install. 

I find the **lsblk** and vgs, lvs, pvs commands very helpful.

CentOS has wonderful controls over RAID/striping during installation, but Ubuntu does not. IME. When setting up a new Ubuntu server, I really miss the CentOS storage management controls at install.

---

### Post by faults2 on 2016-12-23
I might have done it all wrong... my experience of LVM2 is limited.

I'm fully aware of single point of failure which leads to total data loss if even one disk gets broken. This is Laptop for Performance and I don't need redundancy. I have important data else where.


--> I think what I need to do next is Resize vg, remove /sdb1 and extend it back to vg with -i Stripe switch... does this sounds like a good way to do it?



lsblk is truely nice command!

---

### Post by TheFu on 2016-12-24
Since you don't have anything to loose, I'd just try it. See what happens.  No better way to learn. Looks like a reasonable method to me, but I think you need to remove the LV, remove sdb from the VG, then add sdb back to the VG, and lvcreate with the stripe option, create a file system and mount it.  If there is any issue, I'd boot off a live-CD/flash drive to do all this. 

Might be worth taking notes, so if it works, you have those for next time or can post the exact commands used to get help. If something bad happens, it isn't like more than 20 min is needed to load the OS and redo the LVM stuff.

HowToForge has a nice intro to LVM.  When you are knew to an OS, google isn't always your friend.  It takes experience to learn where the quality information can be found.  Plus it takes experience to learn which blog posts come from experienced people and which come from someone completely new who really doesn't know very much.  About 90% of the posts are the 2nd type, I'm afraid.

---

### Post by faults2 on 2016-12-27
Thank you from help.

I did Ubuntu full re-install with Gnome flavor. On install I choosed LVM and Install. After install I extended and I think I'm step closer, but still pretty far... I managed to Extend the LVM and new SSD is Striped. I assume that all new data will be Striped, but old one or old LVM pool stays Linear?

Looks like this now:

```
sudo lvs --segments
  LV     VG              Attr       #Str Type    SSize  
  root   ubuntu-gnome-vg -wi-ao----    1 linear  216,02g
  root   ubuntu-gnome-vg -wi-ao----    2 striped  24,00m
  swap_1 ubuntu-gnome-vg -wi-ao----    1 linear   15,88g
```


[B]If I want to polish this to level "PERFECT" I think I need to: 
1) Boot from Live USB --> Do the LVM config in there 
2) Install Ubuntu by using "Something else..." advanced option during the install. [/B]



openSUSE has built in tool during install for LVM... Yast thingy. What a great tool.

---

### Post by TheFu on 2016-12-27
The debian/ubuntu tools for LVM either during or after install have never impressed me. At least 1 contributor here has been working on a nice GUI LVM/partition manager.  The only issue is that "servers" don't have a GUI, so it isn't really all that useful to me. I'd rather have a curses interface, actually.

I've been totally screwed by CentOS LVM tools refusing to offer a "wipe everything" option if any LVM is discovered on the disk. Ended up booting tinycore and wiping the partition table before I could convince CentOS to let me do anything with it.

Haven't looked at SuSE in years - ran it for about a year before Ubuntu existed (after getting into RPM-hell with Redhat). Never had any issues with it. Actually know a former president of SuSE America (he's in my LUG and shows up about once a quarter to hang out). Nice, smart guy.

Anyway, I figure by now you know the correct answer and can post the steps to be followed.  Please post and mark thread as SOLVED to help everyone in the community.

---

