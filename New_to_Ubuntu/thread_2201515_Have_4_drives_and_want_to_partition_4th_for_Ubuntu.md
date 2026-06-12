---
title: "Have 4 drives and want to partition 4th for Ubuntu and Swap space, but can't create 5"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by john145 on 2014-01-24
Couldn't really fit it all in the title, but I have 4 drives. 3 of them are being used by Windows and I'm trying to make my PC dual boot. The 4th drive (1 TB) is the one I want to install Ubuntu on, and when I try to do so, the installer recommends me to create a swap space drive. However, I can't create more than 4 drives. Is it possible for me to install Ubuntu without overwriting any of the 3 drives being used by Windows? 

Some optional questions/info:
i already partitioned my TB drive, and if I wanted to consolidate the partitioned 4th drive along with this "unusable" space I got when I partitioned it, how would I do so? Like which settings to choose. The drive was not in use, and was only for storage. And by settings, I mean this [http://i.imgur.com/qK0xgFC.jpg](http://i.imgur.com/qK0xgFC.jpg) I believe it was ntfs before but I can't seem to set it as that.

Thanks.

---

### Post by jeremy1138 on 2014-01-24
Create an extended partition on the 1TB drive and place your partition for Ubuntu within that along with your swap partition.

---

### Post by john145 on 2014-01-24
> **jeremy1138 said:**
> Create an extended partition on the 1TB drive and place your partition for Ubuntu within that along with your swap partition.

How do I place both on the same extended partition?

EDIT: oh wow, I see now, thank you.

---

### Post by Impavidus on 2014-01-25
Just to add that your usage of the word "drive" is very confusing. You can't be blamed for that, as Windows uses the word "drive" very confusingly. In Linux terminology, a drive is the physical device on which you store bytes. The parts of it that contain file systems are also called drives by Windows, but are only known in the Linux world under the name "partition". That's why we don't have to create drives on drives.

It seems that you already solved your problem. Could you mark the thread as solved? Click "thread tools" &#8594; "mark as solved".

---

