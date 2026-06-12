---
title: "[SOLVED] confused with partition/dual boot"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by johntravis on 2008-11-01
The more I read, the more I become confused. I am now using ubuntu 8.0.4, have burn 8.10 to a disk, looked at it on computer now would like to install. I would like to split my hdd into two partition, 80gb for 8.0.4 and 80gb for 8.10 (like having two hdd's). I look at partition manager in 8.10, now confusion(fear sets in). please explain how to do this--make 160g  hdd into two 80gb hdd and how to put 8.10 on one without touching 8.0.4 then explain how to boot from one or the other, in case of problems.

---

### Post by caljohnsmith on 2008-11-01
OK, open the Ubuntu partition editor in System > Admin > Partition Editor, select the correct HDD, then click on the existing Ubuntu 8.04 partition, and then you can resize it down to 80 GB. After that you can add another 80 GB partition for Ubuntu 8.10. If you would like more specifics, it would help if you could first post the following from a terminal (applications > accessories > terminal):
```
sudo fdisk -lu
```
That way we can see your existing partitions. Also, you may want to check out this link:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

A little way down the page, he talks about how to use the partition editor to set up your partitions, and it includes lots of good screen shots.

---

### Post by johntravis on 2008-11-02
Great article, it is what I needed,reassurance. Thank you.

---

