---
title: "Changing Partition"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by harrydawizard on 2013-02-06
So here's my issue: I have ubuntu 12.04.01 LTS. I intended to partition my 200 GB hard drive into roughly half. I want half for windows and half for ubuntu. Currently, my computer has quite a jumbo of partitions. I have 6 total. The second largest is 8.5 GB and the largest is 219.79 GB.  
So here's the problem: I have Ubuntu on a partition on 3.6 GB which is much smaller than I intended. So is there a way to repartition without reinstalling?
I installed ubuntu via USB.
Anyone know how to do this?
I tried using GParted but it wouldn't let me change my 219.79 GB partition. The minimum I could change it to is 225 061 MB and the maximum is 225 062 MB. 
Also, this same partition (219.79GB)  has a red ! warning. 
What to try next?

---

### Post by carl4926 on 2013-02-06
You need to take a screenshot of what you see in gparted and post it here

---

### Post by offgridguy on 2013-02-06
I am assuming that windows is already installed ?  Probably on the
219 gb partition, which is why you are seeing the warning flag.
Without a screenshot, we can only guess.:)

---

### Post by Mark Phelps on 2013-02-06
If your Windows version is newer than XP, I would strongly advise AGAINST using GParted to mess with any of the Windows filesystem partitions.  Instead, use the Windows Disk Management utility.

OR, better yet, download and burn the Minitool Partition Wizard Boot CD, boot from that, and use that to modify Windows filesystem partitions.

---

### Post by harrydawizard on 2013-02-06
Here is a screenshot of Gparted and one of the Warning.

Also, I currently have Windows 7, and installed Ubuntu from a USB because I have no optical drive.

Thanks for the speedy replies.

---

### Post by oldfred on 2013-02-06
Does Windows boot? I would try chkdsk first.

Then use Partition Wizard to repair and shrink the Windows partition.

       [http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

    Then with gparted delete your current Linux partitions and the extended partition. You can only have one extended and it is trapped into the small space. You then can create a new extended in the unallocated you create by shrinking Windows and can make as many loggical partitions for Linux and shared NTFS data partitions as you want.

---

### Post by carl4926 on 2013-02-06
@oldfred is correct

But I only ever use Gparted, well Parted Magic. But for me Windows is Not important, I never use it. And I never leave the original install of windows in place, because I have access to all the Full DVD's, so I always do a clean, untainted install and partition my HD as I like it.

Back to you though, you need to delete:
sda6
sda5
sda4

@oldfred asked if windows boots
BUT what I find odd is it's not showing any data on it? Which could be down to the error!? So there probably is data on it, unless you formatted it?

Anyway, with those partitions deleted you need to shrink sda3, from it's far right point to the left. Problem is we don't know how much we can shrink it. But we'll get back to that. Once you have freed up some space (you will see it as unallocated), fill it all with an extended partition. Then you can create logical partitions inside that space for swap and ext4 for / )

Back to windows. With sda4,5,6 deleted you should get windows back in order, working and booting normally, then backup and defrag it, and only then work on the partitioning for Ubuntu.

---

### Post by harrydawizard on 2013-02-07
Ok so here's where I'm at. I have been able to boot windows but have a problem with it freezing. I ran the chkdsk and it seems to have removed the warning sign in Gparted. I booted windows to run partitionwizard so that I could adjust the acer partition but it wouldn't allow me because partitionwizard wanted me to purchase the full program. BUT, I booted ubuntu and gparted now allowed me to adjust my acer ntfs. So now I have 122 GB unallocated but I can't follow the next step because if you look at this screen shot sda2, sda5 and sda6 all have the "key" symbol so I can't adjust/delete these partitions. I can't do it from windows without getting another program. What to do?

---

### Post by carl4926 on 2013-02-07
Wow
That's all changed

You need to delete
sda6
sda5
sda2
In that order and apply it.

Then you can create an extended space in the unallocated area. Just click to focus on it
This will give you a clue, but it's just to show you some of the principles, it's not specifically what you have to do
[https://dl.dropbox.com/u/10573557/win_lin_partitions.m4v](https://dl.dropbox.com/u/10573557/win_lin_partitions.m4v)

Once you have the extended space you can create logical partitions for ubuntu

---

### Post by arpanaut on 2013-02-07
@OP you cannot remove partitions while your system is booted to and mounted on those partitions.
You will need to boot from a live cd/usb and then un mount the swap partition then you will be able to delete the partitions as instructed above, then you can create an extended partition with the unallocated space then create logical partitions within that and install ubuntu there with plenty of space to spare.

---

### Post by harrydawizard on 2013-02-08
Ok so I've unmounted the swap, and then deleted 
sda 6
sda 5
sda 2
Here's a shot of what it looks like in gparted. Why do I have two unallocated spaces, and how do I conbine them? And if I conbine them where do I make my new extended partition?

---

### Post by offgridguy on 2013-02-08
> **harrydawizard said:**
> Ok so I've unmounted the swap, and then deleted 
sda 6
sda 5
sda 2
Here's a shot of what it looks like in gparted. Why do I have two unallocated spaces, and how do I conbine them? And if I conbine them where do I make my new extended partition?You don't have to combine them, one is only 4.41 mb anyway.  You can make your extended partition in the 122 gb unallocated space.

edit; I would try enlarging the sda1 to take in the small unallocated, just to clean up the partition table.

---

### Post by harrydawizard on 2013-02-08
One more question:
I have a swap partition equal size to my ram - 1GB
How large should my 2 ext4 logical partitions be? I have 120GB unallocated.

---

### Post by offgridguy on 2013-02-08
> **harrydawizard said:**
> One more question:
I have a swap partition equal size to my ram - 1GB
How large should my 2 ext4 logical partitions be? I have 120GB unallocated.Partition size is such a personal choice, but
here's what i am using,  screenshot.

The /dev/sda12 will eventually be a shared data partition.  I would suggest about 25 gb each.

---

### Post by carl4926 on 2013-02-08
> **offgridguy said:**
> Partition size is such a personal choice, but
here's what i am using,  screenshot.

The /dev/sda12 will eventually be a shared data partition.  I would suggest about 25 gb each.

This is a most unusual layout.
You should have explained that.

@harrydawizard
Ignore the small unallocated space
Create a Extended partition in the large unallocated space and Apply. Then inside the Extended create
swap 2GB
ext4 20GB
ext4 100GB (or as big as is possible)

Then during install set the 20GB to /
And the 100GB to /home

[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

---

### Post by harrydawizard on 2013-02-08
Ok I have created the neccesary partitions with gparted and now I'm in the installation for ubuntu. When given the option for:
'Install alongside windows'
'Format Windows'
'Something else'

I clicked on 'something else' and got the partitions listed. 
When I highlight the extension partition I created and click install it says something like "this is not a root folder" 
How do I actually get ubuntu on this new extension partition?

Also what do I select for "device for boot load installation"
Do I select my whole hard drive?

---

### Post by carl4926 on 2013-02-08
Inside the extended space
You should have used gparted to create LOGICAl partitions as I listed for
swap
/
/home

---

### Post by carl4926 on 2013-02-08
> Also what do I select for "device for boot load installation"
Do I select my whole hard drive?

Yes
It should be: sda

It is shown here
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

---

### Post by offgridguy on 2013-02-09
@ carl4926,  you are right, i should have explained the partition
table a bit. I multi-boot this laptop, all linux, at the moment
only 2 OS installed, usually I have 4-7.
The larger 25gb partition will be for shared data, placed where it
is so I can easily enlarge it.

---

