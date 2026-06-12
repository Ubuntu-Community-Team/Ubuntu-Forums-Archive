---
title: "Ubuntu installation error"
date: 2019-03-29
forum: New to Ubuntu
---

### Post by user124334 on 2019-03-29
Hello, I am an absolute ubuntu begginer and I have an error at installing on an external hard drive. It haves 1 TB I have a hp laptop with windows 10 on it and 8 GB of ram. 
The error is something like "The partition /dev/sdb2 assigned to / starts at an offset of 3584 bytes from the minimum alignment for the disk, which may lead to very poor performance." And it says to correct the problem that I should delete the partition and recreate it again with the same setting,but I already done this and it still says the same thing.

---

### Post by Dennis N on 2019-03-29
Is this a USB drive? I would look at the current partitioning on the drive. From live media, run command [FONT=Courier New]sudo parted -l[/FONT] in terminal. What do you get? Then decide what to do. You may need to create a new partition table and partitions suitable for a Linux installation.

---

### Post by Rubi1200 on 2019-04-02
Hi and welcome to the forums :-)

I recommend using a LiveCD/USB to boot and then follow the instructions to create a summary report you can post here. Note, only create a report not run any repairs.

Once we see the report we will have a better idea of your partition setup and can advise you on the next steps.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

---

### Post by fightingjoe on 2019-04-04
Does the problem solve? I have the same thing

---

### Post by xbccoffee on 2019-04-04
[https://www.linuxliteos.com/forums/installing-linux-lite/partition-alignment-prompt-at-install/](https://www.linuxliteos.com/forums/installing-linux-lite/partition-alignment-prompt-at-install/) should help.

---

