---
title: "New Build"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by daniell59 on 2008-10-04
I just finished my build. I have two hard drives. I have already installed Vista on one of the drives. I now want to install Ubuntu on the other drive. When I boot from the CD, will I be asked which HD I want to use? I am pretty much a newbie, and I do not want to mess up the Vista install.

Thanks in advance

---

### Post by Crafty Kisses on 2008-10-04
Yes, you will need to choose the "manual" option when it prompts you to partition, then you need to know what HDD Vista is on. It would also be helpful before you do this, post the results of the following command once you're on the LiveCD:
```
sudo fdisk -l
```

---

### Post by daniell59 on 2008-10-04
I have two different brands of HDs. Will I be able to make a determination on that basis?

---

### Post by Crafty Kisses on 2008-10-04
Yes.

---

### Post by Frak on 2008-10-04
> **daniell59 said:**
> I have two different brands of HDs. Will I be able to make a determination on that basis?
Yep.

---

### Post by kansasnoob on 2008-10-04
This guide should be helpful:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This part should fit your setup somewhat well:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

---

### Post by bobpur on 2008-10-04
I beg to differ with Codename in his initial answer to your post'

After you enter your info and the partitioning screen comes up, you'll be given three choices of how to format your drive. "Manual" being the third. You want the second choice. It'll give you the choice of which drive to partition and install Ubuntu on. Understand it'll be the WHOLE drive.

IMO using separate drives for a dualboot is the way to go. WINDOWS on "hda" or "sda" depending on whether or not your using PATA or SATA drives. Linux on "hdb" or "sdb."

Don't get me wrong, you can use "manual" but it's more work you don't need if your new to linux. Basically, what you're doing with "Use entire disk" is letting Ubuntu install a default partition scheme. What could be better? :)

Good Luck.

---

### Post by elmer_42 on 2008-10-04
I installed Ubuntu 8.04 only 5 hours ago onto a machine with two hard drives, one of which contained precious documents and photographs. I went with the surefire way to not overwrite this data. I unplugged the IDE and Molex cable that previously went to the drive with my data on it. After I installed it to the disk I wanted to, I turned off the computer and plugged in the hard disk that contained my files. Upon starting, it was detected successfully.

---

