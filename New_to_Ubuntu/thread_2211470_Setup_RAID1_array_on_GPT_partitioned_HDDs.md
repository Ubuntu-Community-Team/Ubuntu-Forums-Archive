---
title: "Setup RAID1 array on GPT partitioned HDDs"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by astrob0t on 2014-03-16
Hi,

I have two 4TB Seagate HDDs on which I want to setup a RAID1 array. I dont want to boot up from the RAID array. It would be just a media storage array. And finally this would be shared on a network.

Some googling around led me to some things like
1. For using >2TB HDDs, the disks should be formatted using **GPT **partition instead of MBR.
2. For settting up RAID, **mdadm **is the tool.
3. Samba would be used for sharing.

But I am not able to put all of this together to achieve the above.

Please help.

---

### Post by astrob0t on 2014-03-20
I somehow got through the first two points by following [this]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") tutorial. But i am unable to share the directory properly. 
i suspect there might be some wrong permission being set while mounting the raid partition fs (just a suspicion). please help.

---

### Post by Elfy on 2014-03-20
*Thread moved to **Absolute Beginners Section**.*

---

