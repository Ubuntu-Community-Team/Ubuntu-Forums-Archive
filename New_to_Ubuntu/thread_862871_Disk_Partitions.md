---
title: "Disk Partitions"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Witling on 2008-07-17
I want a setup that in DOS or Windows would be described as programs on the C: drive and data on the D: drive. I want both partitions to be mounted at startup and I want the data partition to be accessible to all users. How is this done?

The rest of this consists of a rant. I'm convinced of the basic superiority of the structure of a Unix type operating system. But, if one comes from a Windows background, it can be frustrating. In this case I used the big blue ? to look up help on partitioning. First major category for the help screen is Files, Folders, and Documents. Clicking on that I get to the second major category "Disks, Partitioning and Formatting." I have my choice of 8 categories. I pick 2.2 "Partitioning a device." In 2.2.1 I see that I can create a new partition by using System>Administration> Gnome Partition Editor. Great. The only problem is, there is no "Gnome Partition Editor in my System> Administration menu. Nor is there a Partition Editor. And, just for laughs I start the System>Preferences>Main Menu option to see if perhaps I'm just not making the Gnome Partition Manager appear on my menu. No joy in this check. It's not an option. The Synaptic Package Manager doesn't seem to know about this program either. :(

---

### Post by Theo148 on 2008-07-17
You probably need to install the Gnome partition editor. :)

```
sudo apt-get install gparted
```

After doing that you should be able to start gparted by going to System > Administration > Partition Editor

---

### Post by tyler_roach on 2008-07-17
Try this post:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Yeah, I agree with you; the help files that come with ubuntu are pretty useless (at least they were so for me. However, online help -- through these forums, etc. is usually excellent. (Try looking at the 'New to Ubuntu?' sticky post on this board) Another excellent way to solve issues is by Googling your problem; you're usually not the first one to have the problem.

---

