---
title: "dual boot with xp and partition - must answer pls"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by tavati on 2008-09-27
i was using xp with ubuntu for some time.
now i added a 320 GB harddisk as primary slave to my old 40 GB harddisk.
i made three primary partitions and one logical parttion using ubuntu setup on this new drive.
my idea was to have 10 GB partitions for each mount point like / /boot /usr etc and have 3 GB swap. 
i did it and then reinstalled ubuntu. i mounted my 8 GB primary ext3 partition from my old 40 gb disk on '/' for installing ubuntu and rest all mount points were on the new disk as i described earlier.
after successful installation i restarted my computer and expected my win xp and win 98 to boot. but now these wins would not boot and after few seconds the computer restarted again. i reinstalled win 98 which washed out my ubuntu. but even after that win 98 would not load but command promt only mode was loading. now i loaded win me and it is successfull. 
right now i am on win me.

MY question is : what is the relation of partions with win 98 and ubuntu and is there any limitation due to partitions on dual boot systems ? in need some answers and at least some leads to get this bug out of my mind. what happened when i did those partitions. i also got one error msg while xp failed that was -- " hal.dll file is missing or corrupted " help pls.

---

### Post by bhadotia on 2008-09-27
Hi. I don't have an answer to your primary question coz I never used Win98 , a second hard drive and never ran into this type of a problem:). But I want to enlighten you regarding some things that I know.
First of all you don't need a 3 GB swap even if you have a RAM of 3 GB. The USUALLY recommended swap size is, 2 times the RAM size for RAM < 1GB and 2/3 the RAM size for RAM >=1GB.
Also the idea of mounting the various major directories under / on different partitions as big as 10 GB is also not very good in my opinion. The partitions like /boot, /home and /etc hardly need more than 500 MB of space (/home needs more if you put your data in there). The best partitioning scheme in my opinion is (I use  it on my laptop 80 GB HDD) :
Partition size              Mount point                   
>10GB                      /
>3GB                        /home
>40GB                      /data (Manually created mount point for the partition where my data is kept)
~1GB                        SWAP (no mount point) (I have 1GB RAM)

---

### Post by tavati on 2008-09-28
thanks bhatodia . i will find out why it happened but thanks for that swap size rule i have 1.3 GB RAM and i used the x2 rule i didn't know the 2/3 rule.

---

### Post by quinnten83 on 2008-09-28
Also /etc HAS to be on the same partition as the boot partition, since it's files are needed at boot.

---

