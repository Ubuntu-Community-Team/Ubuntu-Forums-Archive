---
title: "Ubuntu Partition Bigger"
date: 2017-02-13
forum: New to Ubuntu
---

### Post by cloned2 on 2017-02-13
So about a week ago I decided to make a partition of 25G on my extra HHD and put Xubuntu on it. I have since downloaded the Gnome interface - which I prefer - and am also falling head over heals in love with Linux as a whole. I want to make it all bigger. The OS, Root, Swap etc...
How do I do this? Any help would be really appreciated and please remember that I am new to this. So imagine you're talking to a monkey.

---

### Post by yancek on 2017-02-13
You do it with a partition manager booted from and installation DVD/flash drive or from a GParted iso burned to a CD.  I don't use Xubuntu so I'm not sure if GParted is on the install disk.   Can't give you specific advice without more information such as your current partition structure.  Since you don't mention having any other OS, it should be a fairly simple process.  The link below has a pretty detailed tutorial on using GParted.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by RobGoss on 2017-02-13
Hello and welcome, is this a single installation or dual boot?

You can create another partition as** allocated space** and extend the current one for 25-GB

You can read up on it if you need to by accessing the link below

[http://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/](http://www.howtogeek.com/114503/how-to-resize-your-ubuntu-partitions/)

---

### Post by Impavidus on 2017-02-14
It's difficult to give any details without knowing how things are partitioned now, but...

Instead of making the partition larger, it may be easier to add another partition. You could maybe add a /home partition, keeping the current 25GB partitions as a root partition.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Bucky Ball on 2017-02-14
Welcome. As above, need to see the way things are now, but some food for thought.

The /swap only needs to be 2Gb. If you intend hibernating then make as big as installed RAM. Your / partition (root) is just fine at 25Gb. Doesn't need to be bigger either. All you want now is one really big data partition and you're good to go. You can install Ubuntu and put /home on a partition instead of inside /, but if you've just started, IMHO, better to link to a big /data partition. Easier to back up and if you install on / dies, your data is not in there with it. It is on another partition and backup-able. ;)

Did you install Ubuntu with a separate /home on its own partition?

Anyhow, if you have Gparted installed or Disks, easy enough to take a screen shot of that to show us how things are and attach to a post here using the 'Adv Reply' button and the paperclip icon in the toolbar there.

PS: Glad you're loving it. ;)

---

