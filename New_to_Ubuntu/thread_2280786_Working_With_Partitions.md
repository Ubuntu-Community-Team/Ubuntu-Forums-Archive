---
title: "Working With Partitions"
date: 2015-06-02
forum: New to Ubuntu
---

### Post by Stephan_H_Smith on 2015-06-02
Hi, folks, I'm back, this time with a question about partitions. Now, when I installed Ubuntu 14.04 LTS, I used a 500GB drive. I split it into 2 partitions, thinking I might want to dual boot later. I used the default options during install to create the partitions. Ubuntu on one, the other has been left alone. Now, I am wanting to reclaim the extra partition and add it to my Ubuntu partition, making the Ubuntu partition 500GB. What is the best way to do that without messing up my Ubuntu? I haven't worked with Gparted, or any partitioning software, in a long time. Thanks in advance!

---

### Post by oldfred on 2015-06-02
Easiest is just reformat it as ext4, create mount point and mount it as a data partition. I actually use small / (root) partitions of 25GB and data partition(s) for all my data.

Depends on where partition is on drive. If Ubuntu is first or left, you can easily delete second partition and expand Ubuntu right. But if partition is on left you have to move Ubuntu partition left and then expand right. The move left is one I do not like to do as it copies all the data and takes a long time. Any interruption corrupts data, so have good backups.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/images/computers/2009/gparted-create-extended.png](http://www.dedoimedo.com/images/computers/2009/gparted-create-extended.png)

---

### Post by Stephan_H_Smith on 2015-06-04
Thanks for that, OldFred! I looked at the drive in Gparted and the Ubuntu is on the right. Should I boot to a Gparted live CD or DVD to do the work? Or use the Gparted installed on my Ubuntu drive?

---

### Post by oldfred on 2015-06-04
You cannot work on mounted partitions. So you can only use gparted in your install on another drive.
If you only have sda, then you need to use the live installer's copy of gparted or download a gparted liveCD which may be somewhat newer. I have used both.

Also the Ubuntu live version usually mounts swap if found, so you have to click on swap and swapoff or unmount swap. I think the gparted live does not automatically mount swap, but otherwise not much difference. Any partition mounted in the extended partition mounts the entire extended partition, and swap normally is in the extended. If Linux ext4 partition not in extended you may not have to swap off.

---

### Post by Stephan_H_Smith on 2015-06-05
Ok, I downloaded the newest Gparted Live DVD and burned it to a DVD. I rebooted to it. I deleted the partition I wanted to expand to and did an expand and move on my Ubuntu partition. I also added the boot flag to my Ubuntu partition. It took about 45 minutes for all the operations to take place, but it seems to have worked because I had no trouble booting into Ubuntu. Thanks for your help, OldFred!

---

