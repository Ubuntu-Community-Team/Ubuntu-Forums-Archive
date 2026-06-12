---
title: "[SOLVED] Moving Ubuntu 8.04"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by expatCM on 2008-09-03
I have a system which has two SATA drives used for storage and one 40GB ATA.  Ubuntu is running off the ATA drive.

I wish to retire the ATA drive ...  it is old and no doubt will fail sooner or later.  Is there any way I can migrate the operating system from the ATA drive to a new SATA drive?  I do not want to reinstall ... if possible ....

---

### Post by falcon61102 on 2008-09-03
You can perform a dd copy from your old drive to the new location.  I would recommend that before doing that you partition the new drive so it's ready.  You'll need the Ubuntu partition and a SWAP partition at a minimum and then if you have a seperate partition for /home, you'll have to create that as well.  If you boot up from the liveCD you can accomplish the partitioning and the copy.  

Once you've completed that you can perform the dd copy which should look something like:
```
sudo dd if=/dev/sda1 of=/dev/sdb1
```

Replacing /dev/sda1 and /dev/sdb1 with the actual parition names that you're using.

EDIT: Also, by specifying a larger block size, it will copy fast.  You can do that by adding "bs=128M" to the end of the string.  Further information on that can be found at:
[http://ubuntuforums.org/showthread.php?t=304926](http://ubuntuforums.org/showthread.php?t=304926)

Copying is going to take a while but once it's done, there are a couple changes that you're going to have to make before attempting to boot from the new drive.  One is going to be updating the GRUB and the second is the fstab.  Pretty much everything else will update automatically when you boot up.

At this point I would recommending removing the ATA drive since you have everything copied, you don't want to get confused while doing the next steps.  Remove it and boot back up with the LiveCD.  Then you can fix the GRUB with:
```
sudo grub
find /boot/grub/stage1
root (hdX,Y)
setup (hdX)
quit
```

When you run the find commmand it is going to output something like (hd0,1), that's what you use in place of (hdX,Y) and the for the setup command you just take the last number off of the result from the find command.  

Once that has finished you want to update your fstab so Ubuntu knows where to find it's root and SWAP at least, along with /home if you have a seperate one.
First get the UUIDs of your drives with:
```
sudo blkid
```
Now open your fstab with:
```
gksudo gedit /etc/fstab
```
Reading through that you should see some of you partitions listed.  You want to make sure you correct the UUID for the Root partition "/" and the SWAP partition as well as the /home partition if you are using a seperate one.  Save and close.  

Now when you reboot, just make sure that your BIOS is set to boot that HD and you should be good to go.

---

### Post by expatCM on 2008-09-03
I must say that looks reasonably brilliant.  Thank you so much for taking the time and responding in such detail.

I will try this over the weekend and report back .....

I imagine that others could find your response of value as well ... :)

---

### Post by falcon61102 on 2008-09-03
No problem.  Hope all goes well and I look forward to hearing your feedback.

---

### Post by expatCM on 2008-09-08
A new drive purchased and installed.  Getting the new fried drive replaced is a problem ...... it will take a few weeks at least .... 

I followed your instructions and did not have too many problems ...  it was all plain sailing until the very end.

The only problem was that the system renamed the drive identifications so sdb became sdc and so on.  A bit annoying.  I thought that this would be easy to fix by simply changing the path in fstab but actually that did not help.

To fix this I found that if I changed the drive reference from /dev/sdx to the UUID for each drive it worked (previously I had used only the UUID on the boot drive).

So a happy ending.  Thank you again for your help :)

---

### Post by falcon61102 on 2008-09-08
No problem.  Glad it worked out for you.

---

### Post by starcannon on 2008-09-08
> **falcon61102 said:**
> You can perform a dd copy from your old drive to the new location.  I would recommend that before doing that you partition the new drive so it's ready.  You'll need the Ubuntu partition and a SWAP partition at a minimum and then if you have a seperate partition for /home, you'll have to create that as well.  If you boot up from the liveCD you can accomplish the partitioning and the copy....


Thanks for that falcon61102, I can see now that my Ubuntu-fu will be well served to get a grep on dd, man pages here I come.

---

### Post by jeepers on 2008-09-11
```
You can perform a dd copy from your old drive to the new location. I would recommend that before doing that you partition the new drive so it's ready. You'll need the Ubuntu partition and a SWAP partition at a minimum and then if you have a seperate partition for /home, you'll have to create that as well. If you boot up from the liveCD you can accomplish the partitioning and the copy.
```

I thought dd cloned the existing partitions of the drive being cloned ?. I am about to attempt to clone my existing ubuntu to a new sata hdd that i have formatted to ext3, so do i need to add the partitions of my old drive. which are:

/dev/sdb1 linux partition
/dev/sdb2 extended partition
/dev/sdb5 swap partition

or will dd clone them to the new drive.

cheers

---

### Post by falcon61102 on 2008-09-11
You need to create the partitions before you clone the data to them.  Make sure the new partitions are at least the same size or bigger.  Once you copy the info over, you can then resize after that.

---

