---
title: "[SOLVED] Merging partitions in GParted"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-10-08
Hello,

I have just used dd to clone my old 160Gb HDD onto a 750Gb HDD. The new drive now has a large unallocated space after both the 160 partition and the swap file. How can I enlarge the first partition taking space from the unallocated partition? GParted won't let me do that. Will Partition Magic work?

Many thanks.

---

### Post by Therion on 2008-10-08
I don't believe you can merge an existing partition with unallocated space.  

You'll need to partition all or part of the unallocated space and then, once you actually HAVE two partitions, merge them.

---

### Post by drs305 on 2008-10-08
> **Charlie Chick said:**
> Hello,

I have just used dd to clone my old 160Gb HDD onto a 750Gb HDD. The new drive now has a large unallocated space after both the 160 partition and the swap file. How can I enlarge the first partition taking space from the unallocated partition? GParted won't let me do that. Will Partition Magic work?

Many thanks.

Are you trying to do this from within ubuntu on the ubuntu partition? Gparted will not allow you to work on a mounted partition. If you can unmount that drive, you should be able to change the partition sizes. 

If it is an NFTS partition, you may have to install ntfsprogs or use one of the cd's below as they have a more advanced version of gparted than what is in the repository. In the past gparted couldn't deal with NTFS partitions but this has changed, at least on the cd's and by now maybe even in the repo version.

You should be able to do it by booting to the livecd, gparted cd, or systemrescue cd and then performing the operation.

To get the systemrescue cd, go here:
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by Charlie Chick on 2008-10-08
Thanks for your suggestions. I understand that I can't do it from within Ubuntu, I have to run a live CD. I have formatted the unallocated space as ext3. The problem is that the swap file is in the way of the two partitions that I want to merge. Can I move it, delete it, what? I just want to be able to use the entire 750Gb space.

Thanks,

---

### Post by drs305 on 2008-10-08
> **Charlie Chick said:**
> Thanks for your suggestions. I understand that I can't do it from within Ubuntu, I have to run a live CD. I have formatted the unallocated space as ext3. The problem is that the swap file is in the way of the two partitions that I want to merge. Can I move it, delete it, what? I just want to be able to use the entire 750Gb space.

Thanks,

Backup any critical data first.

From the livecd, you can delete the swap partiton and anything else you just created. I would then make a new swap partition and put it at the end of the remaining free space (so it doesn't interfere with similar operations later). You can then expand your existing partition to the desired size.

If you are working with an active swap partition (which you aren't from the livecd), you would turn it off and on with "sudo swapoff -a" and "sudo swapon -". This can also be done from within gparted with the swapoff command. Again, it won't be necessary when using the livecd.

---

### Post by Nasaki on 2008-10-08
I agree with DRS,

Boot your live CD, delete your swap partition, resize, and rereate you swap.

I may be misinformed but I don't think that "merge"ing partitions even exists.

---

### Post by Charlie Chick on 2008-10-08
Thanks for your response. So it's OK to delete the swap partition so that I have just 2 partitions - the cloned and the extra space? I then merge the two and create a partition the same size as the deleted swap partition at the end of the disk. Is that right?

Many thanks!

---

### Post by Charlie Chick on 2008-10-08
Just discovered the fly in this ointment - you can't merge partitions in Gparted! You can only reduce the size of partitions. Looks like I'm going to have to shell out 40GBP for Partition Magic.

---

### Post by bodhi.zazen on 2008-10-08
> **Charlie Chick said:**
> Just discovered the fly in this ointment - you can't merge partitions in Gparted! You can only reduce the size of partitions. Looks like I'm going to have to shell out 40GBP for Partition Magic.

No you can not "merge" partitions, but you can copy the data from one partition to another then resize ...

---

### Post by Charlie Chick on 2008-10-08
"No you can not "merge" partitions, but you can copy the data from one partition to another then resize ..!"

Sorry to be thick, but I don't understand this. If I can't merge partitions, how do I end up with just one partition for Ubuntu and a swap partition when I currently have 600Gb of unallocated space after the swap file?

Do I first format the unallocated space as ext3, then delete the swap partition. Then I copy partition 1 into the newly formatted space and then resize. The only problem is that GParted only allows me to make partitions smaller. If it would allow me to simply delete the swap partition and then merge the two remaining partitions then all would be well, but it doesn't. That's why I'm wondering whether to invest in Partition Magic which allows that and supports ext3.

Thanks again for your help.

---

### Post by Elfy on 2008-10-08
Gparted will allow you to increase the size of the partition. Delete and recreate the swap at the far right of the unallocated space. Then you can resize the existing partition to take the rest of the 600Gb of space.

The space that you want to use to increase the partition with doesn't need to be formatted.

You should end up with

Original partition |unallocated space |swap

Then resize

---

### Post by bodhi.zazen on 2008-10-08
gparted will resize partitions. You can make a partition larger or smaller. You can delete or move partitions.

Sometimes you need to do these things in more then one step, ie delete a partition => apply changes => resize a partition.

You do not "merge" or "add" or "combine" existing partitions. You add or subtract unallocated space.

so, do not format your unallocated space , move your partitions so the unallocated space is adjacent to the partition you wish to enlarge, then resize. It sounds as if you may need to move or delete your swap partition first. In that event, first move or delete your swap partition -> apply changes -> resize your Ubuntu partition by adding unallocated space.

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

It may help if you post a screen shot of garted showing us your current partitions.

---

### Post by Charlie Chick on 2008-10-08
Thank you both for your comments. I've printed them out and I'm going to try again!

---

### Post by philinux on 2008-10-08
Post a screenshot here of what gparted shows before you do anything.

---

### Post by Charlie Chick on 2008-10-08
Just want to say thank you to all of you for your help. I now understand how to use GParted. The key, for me, was in thinking in unallocated space rather than partitions. That way, I was able to re-size which I wasn't able to do before.

This forum is a really great resource for beginners like me and I'm grateful to all you experts who give freely of your time to help people like me out.

Thanks again!

Charlie

---

