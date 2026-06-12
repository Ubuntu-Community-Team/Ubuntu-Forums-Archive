---
title: "Partition Help"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by conorfitzsimons on 2012-06-01
Hey guys,

Basically, I've been messing around with partitions the other day for various reasons and I've now run into a bit of trouble.

[ATTACH]219043[/ATTACH]

My Ubuntu OS is on /dev/sda6
and I want to merge it with /dev/sda1.

I tried formatting /sda1 and it wouldn't let me add on the unallocated space.

Do you have any suggestions how I can add the space that is on /sda1 to /sda6

Please let me know if anything is unclear.

Thanks

Conor

---

### Post by wilee-nilee on 2012-06-01
Do this from a live ubuntu cd make sure all partitions are unmounted, you should see no keys like those seen now. You can't resize a partition you are using.

Delete sda1, and the sda5, the term merge is actually incorrect, you are not merging, but taking up what will be unallocated space. Partitioning can not work as well when you don't have the partitions in numerical order the sda5 is a lower number then the sda6, and sda7, but after them.

Right click the sda2 in the list and then resize and expand it to the left, filling the space unallocated by the sda1 delete. This is a extended partition that is around the rest of the partitions

Then do the same for the sda6, right click resize and drag all the way to the left the front of the sda2 partition, up against it.

So since you have the sda5 removed you can remove the swap and move the sda6 to the right as well, leaving just the right unallocated to make another swap, which should be at the least equal to your ram amount if you want to use the hibernate. Move only one end of the sda6 partition at a time, I would not set it up to run consecutively just to be safe.

You may need to adjust the fstab to get the swap to be on if you remove it and make another.

to get the UUID of the new swap for the fstab run this command.
```
sudo blkid
```copy the UUID set of numbers and letters it will look some thing like this just copy the highlighted portion.
```
/dev/sda7: UUID="**ac5b2d02-d527-4680-bce9-d1f95589b5de**" TYPE="swap"
```Then open fstab with this command.
```
sudo gedit /etc/fstab
```Now insert the UUID from the blkid in place of the one there that is says swap.

Here is a example of what the swap in fstab will look like replace the highlighted section with the new UUID number you get from the blkid command

```
UUID=**ac5b2d02-d527-4680-bce9-d1f95589b5de** swap                    swap    defaults        0 0
```The two highlighted are the same number here as I used my own swap UUID as an example.

You may have to reload grub to the mbr to boot is all.

Use this tool the recommended repair to fix the no  boot if this occurs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by fantab on 2012-06-01
If reinstalling Ubuntu is an option then I suggest you reinstall after partitioning your HDD appropriately... It will simplify things for you.

Use [**GParted LiveCD**]("http://gparted.sourceforge.net/livecd.php") to manage your HDD partitions from boot... it is more efficient.

---

### Post by oldfred on 2012-06-01
Another alternative.

I usually suggest smaller / (root) partitions of 10 to 25GB and separate /home or data partition(s). So you could move /home to sda1 and or shrink sda6 and move the other way or create another data partiton.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by conorfitzsimons on 2012-06-04
@wilee-nilee Thank you! This fixed my partition problem.  I did get an error on reboot since the filesystem was moved.  But I just ran BootRepair and all is well now!

Thank you! =)

Conor

---

