---
title: "How do I create a new partition  without formatting entire hdd?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by T2manner on 2008-07-15
I just bought a new laptop with vista and I want to set up a partition that I can run Ubuntu off of, but I don't want to loose vista.

---

### Post by Het Irv on 2008-07-15
Vista has its own Partition Tool, although I am not sure where it is, but that can be used to shrink your partition and clear some space for Ubuntu.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by falcon61102 on 2008-07-15
When you install Ubuntu, it's partitioner will allow you to resize your primary partition so that it won't erase Vista.  A smart thing to do prior to resizing would be to defrag your computer through Vista.  I used UltraDefrag (don't have link sorry) and ran that about 3 times just to make sure that all my data was at the beginning of the drive before I partitioned it.

Being that you just bought the laptop, your files shouldn't be fragmented anyway, so you won't have to worry about that.

---

### Post by sandysandy on 2008-07-15
have a look here

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by larryfroot on 2008-07-15
...and for future reference...just in case, always defrag windows partitions before doing anything else with them...a repeat of previous advice I know, but its very good advice indeed...

Have you thought about installing ubuntu directly "into" windows with wubi?

---

### Post by Inxsible on 2008-07-15
Are you planning to install Ubuntu within Windows using Wubi?

I don't think you need to partition anything in that case. You just double click the Wubi installer and BAM !!!

If you are planning to go for a dual boot, then have a look at these two links

[Partitioning]("http://www.psychocats.net/ubuntu/partitioning")  |  [Installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by T2manner on 2008-07-15
I got Ubuntu installed.
I just resized the partition in Vista and installed ubuntu on it.
Worked perfectly.

---

