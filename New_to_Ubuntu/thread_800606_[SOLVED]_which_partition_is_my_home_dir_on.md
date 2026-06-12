---
title: "[SOLVED] which partition is my home dir on?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-20
Hi guys

I have been trying to move my /home/kim files to a second partition on my laptop. I made a mess of it, and finally resorted to reinstalling. When the partitioner asked me what to do with the two partitions I set sda1 as / and ticked reformat, I set sda3 as /home no reformat required, and sda5 is swap.

It went great, and on boot I had a working system again, however in the 'filesystem' there is only the 39gig 'filesystem' showing (apart from the cdrom that is) and that is the / root partition. When I click that there are all the expected system directories. But there is no second volume showing of 79 gigs which is the partition for /home (I hope) 

I cannot tell from the paths when I click on Home folder from Places as to which partition that is sitting on. 

I am presuming that because I cannot see it, it means that it mounts automatically at boot, and that my access to that partition is wholly through the Home folder link. Does that make sense, and is that what is supposed to have happened?

Thanks for any education coming my way :-)

---

### Post by Psyker7 on 2008-05-20
Try

```
sudo fstab -l
```

Should let you know where drives are mounted.... if it shows sda3 mounted at /home then you're set :D

---

### Post by Patb on 2008-05-20
Tropdoug, if Psyker's method doesn't work, from a terminal try:
```
cat /etc/fstab
```
and post the output.  That will show what is mounted and where at bootup.  

You could also post the output of:
```
sudo fdisk -l
```
That will list all your disk partitions.

Cheers, Pat.

---

### Post by tropdoug on 2008-05-20
Thanks guys, 

tried sudo fstab -l but that isnt a command apparantly 

so then did ```
# /etc/fstab: static file system information.
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 # /dev/sda1
 UUID=861a4e72-c6e7-4cab-a23a-726953a22437 /               ext3    defaults,errors=remount-ro 0       1
 # /dev/sda3
 UUID=296923bb-e411-4125-af64-1166dd02d6da /home           ext3    defaults        0       2
 # /dev/sda5
 UUID=586571b8-90b1-425e-a8ef-b91f6b31b7b7 none            swap    sw              0       0
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
 kim@laptop:~$ 


``````


kim@laptop:~$ sudo fdisk -l
[sudo] password for kim:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf89dfcaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda3            4463       14216    78349005   83  Linux
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order
kim@laptop:~$ 

```

So I am not sure if that tells me anything, other than sda3 is there, but is it the /home partition hmmmm!

---

### Post by hyper_ch on 2008-05-20
actually
```

df -l

```
shows what partition is mounted where currently.

---

### Post by tropdoug on 2008-05-20
Fantastic, my mind is now at rest, thank you very much

```
kim@laptop:~$ df -l
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda1             35278540   2294460  31192032   7% /
varrun                  517024       104    516920   1% /var/run
varlock                 517024         0    517024   0% /var/lock
udev                    517024        92    516932   1% /dev
devshm                  517024         0    517024   0% /dev/shm
lrm                     517024     34696    482328   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             77119204    470076  72731680   1% /home
kim@laptop:~$ 

```

sda3 is definately the /home partition. coool

---

