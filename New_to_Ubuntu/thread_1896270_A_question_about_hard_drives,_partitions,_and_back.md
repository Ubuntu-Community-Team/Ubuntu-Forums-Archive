---
title: "A question about hard drives, partitions, and backups..."
date: 2011-12-16
forum: New to Ubuntu
---

### Post by Jack Nitro on 2011-12-16
Allow me to explain my situation:

Recently, my Dell Studio's internal hard drive went, as our German friends would say, kaput. Although it seemed fixable at first, each day proves such a feat ever more doubtful, and many of my closest friends and family are telling me that it's time to let go.

So! Linux it is. I was lucky and perhaps sensible enough to back up my hard drive about a month prior to the incident, but the hard drive that I backed it up to is the only other one that I have. If possible, I'd like to install Ubuntu to this hard drive, but without erasing everything on it. So what I'd like to know is:

[LIST=1]
[*]Is it possible to partition a HDD without formatting it - a.k.a. deleting everything already on it?
[*]If not, could I install to, lets say, an 8gb flash drive and transfer the system files to my HDD?
[*]If neither is possible, would I at least be able to run the OS off of this flash drive, using the HDD separately for every other file (Program Files, Documents, and pretty much everything)
[/LIST]

[LIST]
[*]I know that programs can run exclusively from a separate hard drive, I've done it before
[/LIST]
Any help would earn you eternal gratitude and potential brownie points. Maybe even cookies. Not browser cookies, but those little peanut butter cookies with the Hershey Kiss in the middle.

---

### Post by mikewhatever on 2011-12-16
Isn't there a way to get another hdd, and leave the one with backups for the backups?

---

### Post by jerome1232 on 2011-12-16
> **Jack Nitro said:**
> 
[LIST=1]
[*]Is it possible to partition a HDD without formatting it - a.k.a. deleting everything already on it?
Kind of, You can shrink the existing partition (assuming it has enough free space) and then create a new partition after it, the Ubuntu installer can do this automatically. (a Windows side-by-side with Ubuntu installation, known as a dual boot)
> **Jack Nitro said:**
> 
[*]If not, could I install to, lets say, an 8gb flash drive and transfer the system files to my HDD?
Yes, I keep one around for recovering other computers, you can find a how to at ubuntu.com, on the download page you should be able to find it.

> **Jack Nitro said:**
> 
[*]If neither is possible, would I at least be able to run the OS off of this flash drive, using the HDD separately for every other file (Program Files, Documents, and pretty much everything)
[/LIST]

You could do that, although it would be a bit complicated, obviously the other methods would be preferred.

---

### Post by Jack Nitro on 2011-12-16
Well, it's a fairly large hard drive, so I was using it both for backups and for extra space. It does have a few programs on it, too.

So yeah, I was hoping to start using the backup hard drive as a standard hard drive and start backing up with an online service, but the more I think about it, the more that does seem to sound like a waste of time.

Still, I don't want to spend loads of money on a new hard drive if I don't have to. In fact, I don't want to spend money. 

Would I be able to use a flash drive for the OS, like I said?

EDIT: Sorry, posted this before I saw [jerome1232]("http://ubuntuforums.org/member.php?u=453029")'s post. I guess so...

---

### Post by Jack Nitro on 2011-12-16
> **jerome1232 said:**
> Kind of, You can shrink the existing partition (assuming it has enough free space) and then create a new partition after it, the Ubuntu installer can do this automatically. (a Windows side-by-side with Ubuntu installation, known as a dual boot)

I don't have windows running on the aforementioned hard drive, I'm currently running from the Ubuntu install disk trial. Would I still be able to create a new partition? If so, would it be through the "Something Else" option, and how? Keep in mind that I know next to nothing about partitioning.

---

### Post by cortman on 2011-12-16
You should be able to shrink the backup partition with GParted, while running from the live CD. It should be quite safe and easy. Then you can add a partition on the free space when you go to install Ubuntu.
There shouldn't be any need to buy a second drive. Just be very, very careful.

---

### Post by Paqman on 2011-12-16
> **Jack Nitro said:**
> 
Would I be able to use a flash drive for the OS, like I said?


Yes, although it wouldn't be a good long-term solution. Flash drives aren't really designed for taking lots of sustained writes like you'll get running and OS, and you'll find that it would fail eventually. It might be fine for months, but a proper hard drive would be much more durable.

If your backup drive has 20GB or so of free space I'd just go ahead and install Ubuntu onto that. Backing up online will only really be practical if you're not backing up much data, the prices for backing up more than a few GB are pretty eye watering. I'd just pick up a cheap second hand drive off eBay for your backups.

---

### Post by oldfred on 2011-12-16
Any hard drive reorganizing has some risk. A power failure, cat/dog/kid/foot hitting power switch (all recent posts on how to recover all data lost) will cause major problems. That said it works and data is not usually lost.

I prefer to partition in advance so I have control over sizes. Some use the auto install and do not understand the use entire disk means just that and erase everything. 

If you partition in advance with gparted, you can shrink your existing partition(s), create / (root), swap and perhaps a separate /home or other data partitions. Then use manual install/Something Else to choose the partitions. You can do it as part of the install also.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by jerome1232 on 2011-12-16
Yes, there is a "manual partition" option where you can manually specify, shrink, create, and delete partitions. You need to have an idea of what you want and we need an idea of what your working with.

How big is this hard drive? How much space do you want to leave for other storage?

You'll want a root partition aka / (20GB will be more than comfy for the system, more than that depending on how much personal storage you need) and a small swap partition (at least = to ram if you want to hibernate)

You can always start the installation process and fire a screenshot of the manual partitioner our way to ask what do I do now?

---

### Post by Jack Nitro on 2011-12-16
> **cortman said:**
> You should be able to shrink the backup partition with GParted, while running from the live CD. It should be quite safe and easy. Then you can add a partition on the free space when you go to install Ubuntu.
There shouldn't be any need to buy a second drive. Just be very, very careful.

Okie-dokie, I took your advice on shrinking the existing partition. However, Gparted doesn't seem to support NTFS, so I had to use KDE Partition Manager instead. Still, it worked, and I was able to free up 20GB of unallocated space, thankfully, without losing any data. I'm going to need the jaws of life to help uncross my fingers.

So all that's left is to install Ubuntu to the leftover space, yes?

---

### Post by Jack Nitro on 2011-12-16
[img]http://img7.imageshack.us/img7/2064/screenshotat20111216212.png[/img]

Here's where I am right now - shall I proceed, or am I doing something horribly wrong?

---

### Post by jerome1232 on 2011-12-16
Looking good, you'll want to add a small swap partition, and your / partition, formated as ext4. Both inside that free space.

edit: and **do not** touch the "new partition table" button

---

### Post by cortman on 2011-12-16
> **Jack Nitro said:**
> Okie-dokie, I took your advice on shrinking the existing partition. However, Gparted doesn't seem to support NTFS, so I had to use KDE Partition Manager instead. Still, it worked, and I was able to free up 20GB of unallocated space, thankfully, without losing any data. I'm going to need the jaws of life to help uncross my fingers.

So all that's left is to install Ubuntu to the leftover space, yes?

Sounds right. IMPORTANT: When you install Ubuntu, make sure you choose to manually add the partition. DO NOT let it automatically install to whatsoever partition it desires. Create a new partition from the free space and install it there.
[Here's]("http://www.psychocats.net/ubuntu/installing") a link to installing, if you have any questions. You seem to be fairly intuitive with computers, so it should go fine.
Just remember: Create a new partition from FREE SPACE. (and like jerome1232 said, don't touch "new partition table")
And keep a jaws of life handy. Best wishes!

---

### Post by Jack Nitro on 2011-12-16
> **jerome1232 said:**
> Looking good, you'll want to add a small swap partition, and your / partition, formated as ext4. Both inside that free space.

edit: and **do not** touch the "new partition table" button

Do the "mount point" or "location for new partition" (I just assumed "end") matter? If so, what should I choose for each partition?

---

### Post by jerome1232 on 2011-12-16
Swap partition won't have a mount point, you'll just chose it's type as "swap area", the swap partition only needs to be as big as your physical ram. Your main system partition, known as root, will have a mount point of "/", you'll format it as ext4. That's all you need for a running system.

---

### Post by Jack Nitro on 2011-12-16
[img]http://img706.imageshack.us/img706/4660/57683894.png[/img]

Well, here goes nothing.

---

### Post by Jack Nitro on 2011-12-16
Well, it worked. Thanks to everyone here who helped. Cookies will be handed out shortly.

---

### Post by jerome1232 on 2011-12-16
You should've left the "device for bootloader installation" as the entire drive, I'm frankly surprised that you can boot with it set to /dev/sda3.

Well, it's an easy fix if it turns out your handing out cookies a little to soon.

---

### Post by cortman on 2011-12-17
> **Jack Nitro said:**
> Well, it worked. Thanks to everyone here who helped. Cookies will be handed out shortly.

Glad to help! +1 to cookies.

---

