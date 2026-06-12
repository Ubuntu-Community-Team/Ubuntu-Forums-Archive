---
title: "how to use unallocated space in harddisk???"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by jammu_d_gr8 on 2008-07-03
hi guys...
am a recenty installed ubuntu on my pc with a dual boot with windows xp.
i have a 80gb hard disk. i decided to use 20 gb for ubuntu. I installed xp by keeping 20 gb free. and then i installed ubuntu on d remaining space using manual configuration. since i donno much abt ubuntu i decided to use 7 gb for instalation and remaining for swap(i though it was for storage, just another format as in the case of windows(fat 32, ntfs). then while scrubbing about ubuntu i found that swap stands for virtual ram. so i decided to use gparted to delete swap. Now this is the state.
[IMG]http://img224.imageshack.us/img224/280/screenshotzh3.png[/IMG]
so tell me how to create swap and usefull starage space from it....
i did something with gpaeted. but none woked well. so i deleted it again.
so tell me a suitable amount of swap and lets use remaining for starage.
plese tell me the steps to do that...
thanks....
with hope jamesh...

---

### Post by hofa on 2008-07-03
Well I use 1 GB of swap but for me it's to much, I never get to the maximum. After you created the swap partition, you have to add it in the fstab (/etc/fstab) file I think.

This is what my entry looks like, but your UUID will be different
```
UUID=88764942-eac2-482c-9cb2-984339a62aa5 none            swap    sw              0       0
```

You can find the UUID when you go in to terminal and type 
```
sudo blkid
```
there you identify the partition which has the TYPE set to swap and you use that UUID to put in the fstab file

Then reboot and it just might work :)

ow and in case you don't know how to edit your fstab file: go in terminal and type
```
sudo gedit /etc/fstab
```

---

### Post by jammu_d_gr8 on 2008-07-03
k that helped me...
thanks...
now will u tell me which format should i use for the remaining space.
ex2 or ex3. (only logical partion is enabled.primary secondary options r not accesible). is der any editings like done b4???
thx.........

---

### Post by logos34 on 2008-07-03
Here's what I'd do:

Make a new /swap right before or after /.  Delete sda6.  Then make a big ext3 /home out of all the remaining space.  6-7 gigs is ordinarily plenty for root so long as you have a [separate /home]("http://www.psychocats.net/ubuntu/separatehome") or data partition.  Otherwise you'll soon find yourself out of room.

Get **fs-driver** for windows so you can access the linux side

---

### Post by hofa on 2008-07-03
So you've got the following partitions now:
- Windows: 10 GB
- Data: 20 GB
- Ubuntu: 6.67 GB
- Swap: 1 GB
- Another Data: 22.28 GB
- Unallocated: 14.6 GB

That's an awful lot of partitions

I would recommend you merge the two data partitions, give your Ubuntu installation a total of 10 GB and add the rest of the unallocated space to your Windows installation (so you have enough space install your programs)

** Do this after your partition fiddling **
You can then just put an entry for your data partition in the fstab file and it will be mounted automatically when Ubuntu boots, so you can use it in Ubuntu too. First you make a folder where you can mount the partition to:
```
sudo mkdir /media/data
```
then you put the following entry in your fstab
```
/dev/sda2       /media/data     ntfs    defaults        0       0
```
You can find the location of your data partition (/dev/sda2) with 'sudo blkid', just look for the second entry with TYPE="ntfs"

---

