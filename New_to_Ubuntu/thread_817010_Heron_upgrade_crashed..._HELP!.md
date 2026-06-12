---
title: "Heron upgrade crashed... HELP!"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Luffer on 2008-06-03
Just doing the Gutsy to Heron upgrade and with 2 minutes remaining the upgrade has crahsed. It's sat doing nothing for 15 minutes, the  most recent message in the Terminal window is:

```

installing new version of config file /etc/init.d/console-setup
```

I've left it for now because I don't know what to do! Please can someone help?

Regards,
James

---

### Post by Luffer on 2008-06-03
After leaving the upgrade running for an hour, I came back to see it had moved on and was asking me if it could remove redundant packages. I clicked remove, at which point the system shut itself down and went into a reboot which just hung on a blank screen. So I restarted in recovery mode at it got to here:

```
* starting Kernel Variable                       [OK]

BUG: soft lockup - CPU#1 stuck for 11s! [events/1:10]
BUG: soft lockup - CPU#1 stuck for 11s! [events/1:10]
BUG: soft lockup - CPU#1 stuck for 11s! [events/1:10]
```

And that message just continues to appear over and over again. What's happened and how on earth do I get my OS back?

---

### Post by louieb on 2008-06-03
Sounds like the upgrade failed big time. At this point I'd probably boot to a live CD, get my data copied off to a safe place, and reinstall.   

Fixing the problems you are having  is  one of the best reasons to have a separate /home partition. Or even better a separate data partition.  A separate /home and/or data partition makes backing up before making major changes easier. 

I use both a separate /home and  data partition. Just before I upgrade I'll use **partimage on the **[SystemRescueCd]("http://www.sysresccd.org/Main_Page")   to backup / (root) and /home to my data partition.  Do the upgrade - if it works fine. If not its an easy restore to put my PC back in a working condition.  

With an upgrade coming every 6 months or so. May want to look at how you installed Ubuntu and make some changes.  

To bad you are having problems. But some of us like me (been there - got the tee shirt) have to learn the hard way to backup before making major changes.

---

### Post by Luffer on 2008-06-04
Thanks, it's not a huge issue because I'd only had Gutsy on my machine for a few weeks and didn't put any data on it. A re-install isn't a problem at all.

I am interested in a separate /home partition though but I don't really understand what to do to achieve that. Is there a guide available somewhere to take me through it? I have a dual boot with Vista if that makes a difference.

How large should I make the OS partition for instance? It's all still a mystery to me, but I'm learning slowly.

---

### Post by philinux on 2008-06-04
> **Luffer said:**
> Thanks, it's not a huge issue because I'd only had Gutsy on my machine for a few weeks and didn't put any data on it. A re-install isn't a problem at all.

I am interested in a separate /home partition though but I don't really understand what to do to achieve that. Is there a guide available somewhere to take me through it? I have a dual boot with Vista if that makes a difference.

How large should I make the OS partition for instance? It's all still a mystery to me, but I'm learning slowly.


10 or 12 gig is enough for root. When the partitioner comes up choose manual and make / swap and /home.

---

### Post by Luffer on 2008-06-04
> **philinux said:**
> 10 or 12 gig is enough for root. When the partitioner comes up choose manual and make / swap and /home.

Okay, I'm ignorant here so please forgive me! I used the Vista partition manager before to create the original partition, can I create the extra partitions using that tool? It's just that I'm familiar with that and less likely to do something stupid.

Also, how many partitions should I make? 10Gb for root, then two more for /swap and /home? So three? How big for the other two? I have about 90Gb to play with.

---

### Post by louieb on 2008-06-04
Don't have VISTA so can't comment on its partitioner.  I don't  know of any reason not to use it.

If I had 90GB of hard drive space to play with: this is how Id chop it up.

[LIST]
[*]10GB / (root)
[*]5GB /home
[*]1GB swap
[*]Balance  a partition that you would mount at install time as /media/data
[/LIST]

Because of the limit of 4 primary partitions or 3 primary  + 1 extended partition. I would make the whole 90GB one large extended  partition.  Inside the extended partition  you make  the 4 logical partitions  I described above. 

Use Vista or whatever to create the partitions. Then when you install Ubuntu choose the manual partition option. There you edit the partition by telling the installer what file system to use and where to mount it. 

Its only hard the 1st time you do it.

---

### Post by Luffer on 2008-06-05
> **louieb said:**
> 
[LIST]
[*]10GB / (root)
[*]5GB /home
[*]1GB swap
[*]Balance  a partition that you would mount at install time as /media/data
[/LIST]

Because of the limit of 4 primary partitions or 3 primary  + 1 extended partition. I would make the whole 90GB one large extended  partition.  Inside the extended partition  you make  the 4 logical partitions  I described above. 


Eeek, you had me up until the "Balance a partition that you would mount at install time as /media/data. What does that mean?

Once I've set up the partitions and actually install Ubuntu again which one do I tell the OS to install to? I'm guessing it's /root, is that right?

Cheers.

---

### Post by louieb on 2008-06-05
Just a matter of learning a few file system terms. The Linux file system starts with a directory called / (root) and expands like a tree from there. 

When you mount a partition you are telling Linux I want to access this partition using this name.   

So yes when you tell the installer to mount / (root) on this partition you are saying install here.  

One branch of the tree is /home this is where the user configuration files go. When you add a user a new directory will be created ie..  /home/lou - user lou would find his personal  setting here. 

Another branch of the tree is /media  This is where things like CD drives, USB flash drives and other partitions on your computer get mounted. That is the name you use to access  the data on those devices. 

At install time if you choose the manual partitioning option, you will see a list of all your partitions. When you click on it and choose edit you will be able to instruct the installer to mount this partition on that part of the file system.   Some of the mount points such as /, /home, ... will be on a list you can select from. 

The partition you want to keep your data on will be listed too. If you do nothing it will get mounted on /media/<somename> That may be alright for you. But you can  give  it any mount point you want. I suggest that the mount point start with /media/.

:confused:Confused? I'll try and help sort things out later - gota go.

---

### Post by meborc on 2008-06-05
to get things clearer i suggest you read this - [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) it is a very good dual-boot guide by herman... and there is also a lot of good stuff about different partitions ;)

---

