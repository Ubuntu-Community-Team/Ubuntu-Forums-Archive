---
title: "diskspace doesnt match up - &quot;missing&quot; 300GB"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by Fisshy on 2013-05-17
Hello, I'm new here and using ubuntu (or Linux for that matter). I've stumbled upon a problem I can't fix.

So the whole story;
I bought a new box which would serve as a server with different functions. I bought 2x 3TB discs to use in a LVM and I used fdisk first.

I noticed after a while that I only got 2TB per disc and decided to figure out how to get the additional 700GB / disc.
I found out that I had to use gdisk to do this, which I manage to do without a problem. I setup my LVM again with a new vg name (I removed the old one first) and started over with the files I had.
I made a share with smbd and decided to check the total discspace used and it said ~600GB used, but when I checked a webapp it said I had used roughly 900GB.

I then connected to the server and ran some commands; 
```
df -h
/dev/mapper/storage-storage  5,4T  614G  4,5T  12% /storage
```

As you can see, the 600GB, along with the % used matches up with what I could see, but if you check total space compared with available it's shy 300GB. I then checked vgdisplay lvdisplay pvdisplay and i could not see any traces of the old one, which i think is the culprit. 

Do anyone have any ideas where the 300GB could be used?
```
--- Logical volume ---
LV Path                /dev/storage/storage 
  LV Name                storage
  VG Name                storage
  LV UUID                xhPcHn-KzQM-kSyX-j8NS-KG72-80d8-YAj1nK
  LV Write Access        read/write
  LV Creation host, time xbmc, 2013-05-14 19:22:07 +0200
  LV Status              available
  # open                 1
  LV Size                5,40 TiB
  Current LE             1415578
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
```

```
 --- Volume group ---  
VG Name               storage
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               5,46 TiB
  PE Size               4,00 MiB
  Total PE              1430792
  Alloc PE / Size       1415578 / 5,40 TiB
  Free  PE / Size       15214 / 59,43 GiB
  VG UUID               Ir7D5B-kBO6-16NW-jpqJ-qm2h-doRQ-njLW3M



```

```
  --- Physical volume ---  
PV Name               /dev/sdc1
  VG Name               storage
  PV Size               2,73 TiB / not usable 3,44 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              715396
  Free PE               0
  Allocated PE          715396
  PV UUID               aJajek-qSUC-TspZ-YL2f-rw5E-qgGe-nJcz3W


  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               storage
  PV Size               2,73 TiB / not usable 3,44 MiB
  Allocatable           yes
  PE Size               4,00 MiB
  Total PE              715396
  Free PE               15214
  Allocated PE          700182
  PV UUID               gSN4sV-GsGj-yImW-4YHN-Ofqo-bOO1-qKb1hG



```


Thanks in advance!

---

### Post by Cheesemill on 2013-05-17
Is this an ext4 filesystem? If so then it's probably the reserved system space.

By default an ext4 filesystem reserves 5% of the available space for roots use only in case of emergencies, this was an OK value when drives were only MB's or GB's in size but in the modern era of TB arrays it works out as a lot of waisted space. You can find out if this is the case by running the following command...
```
sudo tune2fs -l /dev/storage/storage
```
and looking for the 'Reserved block count' line.

If you want to change the amount of reserved space then you can use the following command when the partition isn't mounted, for example...
```
sudo tune2fs -m 2 /dev/storage/storage
```
Would change the reserved block count to 2%.

If this is just going to be used as a storage partition, not as your / partition then it's safe enough to set it to 0%.

---

### Post by Fisshy on 2013-05-17
Hello,

Thanks for fast reply.
This was the cause, thanks a lot for your help!

No, I made a misstake and made it ext3. Can I safely change it to ext4 without losing data? If so, how?

Thanks in advance.

---

### Post by grahammechanical on 2013-05-17
This is what you can read. It has a section on converting Ext3 to Ext4. It is a one way only ride. Make back ups. I am not at all sure if it is good to try this under LVM. 

[https://ext4.wiki.kernel.org/index.php/Ext4_Howto](https://ext4.wiki.kernel.org/index.php/Ext4_Howto)

Regards

---

### Post by Fisshy on 2013-05-17
Thanks, I'll give it a read first. One last question regarding reservation of disk space.

If the filesystem takes ~5% as default, why is my disk reduced to 2,7TB from 3TB by default too? Is there a way to use all 3TB? Those 10% is pretty much still :)

Thanks in advance!

---

### Post by Cheesemill on 2013-05-17
Computers use GiB and TiB to measure the size of hard drives but HD manufacturers use GB and TB, this difference in units is all you are seeing. This difference is confused by the fact that when a computer displays disk usage it will use G to mean GiB instead of GB.

1TB = 0.91TiB so a 3TB drive has a capacity of 2.73TiB

For an explanation of the maths take a look at Wikipedia...
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

---

### Post by Fisshy on 2013-05-17
Thank you so much for your help, both of you.

---

