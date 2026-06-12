---
title: "partition help"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by pacrep on 2008-04-27
Currently I have no OS, Tired of Vista and been using Ubuntu for about 3 months. I wanna keep the hidden factory partition which is Primary. So I need help with manual install.

Does the / "root" have to be Primary or can I use a Extended. /home is probably Primary. Agian with swap, does it need to be Primary?

I understand a hard drive can only have 4 primary partitions, but I want to create a couple more partitions for data and I guess those can be Extented.

---

### Post by CloudFX on 2008-04-27
Generally if your dual-booting, it's best to have all Windows partitions as Primary's, and keep Ubuntu as an Extended partition.  This is done by default, and you shouldn't notice a difference.

Also, you can only have 1 extended on top of the 4 primary.

---

### Post by pacrep on 2008-04-27
Thx for the fast reply, I'm not dual booting, I want to go Ubuntu 100% beside the Factory parition. So basically Ubuntu can be installed on Extened? And / "root" and swap can be Extended also?

---

### Post by Gambini on 2008-04-27
I would set the '/' partition as a primary, then make an extended partition and put your '/home' and '/swap' and whatever else you need in it. 

You probably won't need more than 20GB for the root. I had a ton of applications and they didn't even take up 10GB, so you can make up your own mind about that. Depending on where you are going to store your music or pictures is the factor for the size of the /home. If you want it to be shared between Vista and Ubuntu, then I would put all the music and pictures on an NTFS partition that can be accessed from the two OSes. 

Also another insight is that an extended partition takes up the space of a primary partition. So here is how I would do your drives.

```
Partition 1: Vista (NTFS)
Partition 2: '/' (EXT3)
Partition 3: |Extended|
     Partition 4: '/home' (EXT3)
     Partition 5: '/swap' (EXT3)
     Partition 6: Data stuff (NTFS)
One more primary partition for down the road when you want another distro to try.
```

EDIT: I am too slow at typing, so you got it before I did. Also, I thought that the root partition had to be a primary one to boot off of. If not, then throw everything into one extended partition for organization's sake. Also, since you are not dual booting, you can take out the 6th partition and just make your '/home' a lot larger.

---

### Post by CloudFX on 2008-04-27
If your installing Ubuntu 100%, then simply choose the option to overwrite the entire harddrive when you install Ubuntu.  It will do all of the work for you, and you won't have to bother with partitioning.

---

### Post by Tatty on 2008-04-27
Im pretty sure your root partition has to be primary.

---

### Post by Gambini on 2008-04-27
> **CloudFX said:**
> If your installing Ubuntu 100%, then simply choose the option to overwrite the entire harddrive when you install Ubuntu.  It will do all of the work for you, and you won't have to bother with partitioning.

pacrep wanted to keep one of the partitions, so that wouldn't work out too well. Of course, it would be too easy as well.:lolflag:

---

### Post by eldepeche on 2008-04-27
OK, no one seems to have read the original post. pacrep wants to hose Vista, but save the recovery partition. 

pacrep, can you paste the following command into the Terminal program and post the output in this thread?
```
sudo fdisk -l
```

---

### Post by pacrep on 2008-04-27
Well I can't do the whole hard drive because of the factory partition "just in case i need it". But I'm starting to get the  idea, "root" is Primary, /home can be Extented

---

### Post by pacrep on 2008-04-27
fdisk:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb0399a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         893     7168000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2             894        8723    62894475   83  Linux
/dev/sda3            8728       14081    43006005   83  Linux
/dev/sda4           14082       19457    43182720   83  Linux
ubuntu@ubuntu:~$ 

```

---

### Post by pacrep on 2008-04-27
Basically a work in progress, I wanna use the other partition so i can keep stuff oragnized.

---

### Post by pacrep on 2008-04-28
Well I set up my Ubuntu system manually 'good by vista' but could not setup up partitions the way I liked.

So I went ahead and created a Primary partition #2 as Ext3 for root, then made another partition as Extended for /home and swap.

/home is a Logical Ext3 partition as is swap, my question Is, Is the result
of my fdisk right?

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb0399a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         893     7168000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         894        2851    15727635   83  Linux
/dev/sda3            2852       19457   133387695    5  Extended
/dev/sda5            2852       18935   129194698+  83  Linux
/dev/sda6           18936       19457     4192933+  82  Linux swap / Solaris
commander@commander:~$
```

---

### Post by pacrep on 2008-04-28
Well can anyone help, because I'm ready to install drivers, music, etc. And for some reason grub menu shows up asking me to pick an OS. Vista loader still shows and when I click it, gives me recovery.dat window in big letters.

I would like ubuntu to load automatically.

---

### Post by alpdo on 2008-04-28
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

