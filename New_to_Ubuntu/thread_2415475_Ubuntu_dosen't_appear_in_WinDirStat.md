---
title: "Ubuntu dosen't appear in WinDirStat"
date: 2019-03-26
forum: New to Ubuntu
---

### Post by billy3xs on 2019-03-26
I shrank my Win 7 64 bit 120 GB SSD in my laptop. I read somewhere that I needed 20 GB for Ubuntu.
I also loaded a lite version without games, etc. because I was worried about room. 
So I cannot find how I managed to load it and it dosen't appear in WinDirStat. 
So far I've loaded Make, Anki, Synaptic, anyway I'm worried that Ubuntu is loaded incorrectly.

Now I'm getting an error: Low disk space  253 MB. 
The attached thumbnail shows WinDirStat and Ubuntu in the Recycle bin at 129 Bytes!

---

### Post by deadflowr on 2019-03-26
Windows cannot read Ubuntu's file system type, ext4. (and most other linux file systems.)
Ubuntu , however, can read Windows ntfs file systems.

In order to read a linux file system on Winodws you need to use a 3rd party utility such as Diskinternals linux reader app.
(Or any number of other apps that can do it)


Anyway, how'd you install Ubuntu?
(From installer media, or it is some odd program setup like WSL??)

---

### Post by billy3xs on 2019-03-26
I burned the Ubuntu 18.04 Desktop ISO to disk and loaded it from there.
There were two options and I  picked the no frills one.

I don't need to use WinDirStat , but I'm just switching to Ubuntu from Win 7, so it takes awhile to find stuff.

---

### Post by deadflowr on 2019-03-26
You can find disk usages in Ubuntu in
Disk usage analyzer,
System monitor >> file systems tab,
or Disks

Disk usage analyzer shows where space is being used.
The file systems tab in System Monitor show space used generally on devices currently mounted on the system.
Disks shows basic information about all devices currently connected to the machine (mounted or not mounted)
[s](Disks does not show information about current space usage, though)[/s]

Edit: strike that, Disks does show usage for device currently mounted.

---

### Post by billy3xs on 2019-03-26
Devices & Locations            

bill-W150--                            756 MB Available    
/                                            8.4 GB    Total    

Ubuntu                              12.3 GB Avail
/media/bill/Ubuntu              12.4 GB  Total

99 GB Volume                    9.9 GB  Avail
/media/bill/62827c1e82----99.0 GB Total

I don't think I have a screenshot tool installed yet.

---

### Post by deadflowr on 2019-03-26
> I don't think I have a screenshot tool installed yet.
Ubuntu comes with a screenshot utility already. (Or at least properly installed it should)
If you have a prntscrn button, or whatever the name on your keyboard is, clicking it will snap an image an automatically place it in the Pictures directory.
Depending on Ubuntu release it might have a Screenshot sub directory in the Pictures directory.
(Or I just created the directory myself and forgot. Time is a vicious mistress)

You can also invoke screenshot app from Ubuntu's menu system.
(Just click on Activities in the top panel to open the Overview and type Screenshot in the search bar.)

---

### Post by billy3xs on 2019-03-26
Ok found the screenshot tool and it filed in /pictures.
Does it look like I installed ubuntu on the desktop?
It looks like the Partition  Ubuntu didn't get the install.

---

### Post by billy3xs on 2019-03-26
That wasn't very clear. I thought I shrank the C drive partion and just added U drive partition called Ubuntu. It came out very small, so I messed with partitioning further, but the result looked ok.

---

### Post by deadflowr on 2019-03-26
The partition called Ubuntu is just a partition and has zero to do with Ubuntu's install.
That's because Ubuntu doesn't install to NTFS file systems.
Ubuntu is on the even smaller Partition 5. 
(With a whopping 8.6GB which puts it at the barest size for Ubuntu.)

Perhaps the easiest thing to do would be a start over and reset the partitions.
I'd recommend combining both the partition 3 and partition 5 which would create a usable 20+GB partition which is fairly adequate for Ubuntu.

---

### Post by billy3xs on 2019-03-26
Thank you, so I'll go back to windows, file partition, do something like unpartition and then extend partition 3. I might as well extend the C drive for a little more breathing room.
thank you for your time! And reinstall from boot DVD.

---

### Post by The Cog on 2019-03-26
Don't try to create the Ubuntu partition with windows. Windows can't create the kind of partition that Linux needs. It's probably best just to delete the partitions leaving unused space and let the Ubuntu installer install on the unused space. The installer will format the fight kind of partition.

---

### Post by billy3xs on 2019-03-26
Thank you for your help.  I must have misunderstood the directions for setting up a partition  for installation.

---

### Post by billy3xs on 2019-03-27
Cool! It worked! I deleted the partitions that I made. Stretched the C Drive giving win 7 10 GB of free space. Then installed the full version of Ubuntu.
I'm thinking I'm part of a wave of people using Win 7 on an old laptop migrating to Ubuntu! 
Joke of the week was when I ask Windows to upgrade to Win 10, the reply was to buy a new laptop AND there was, IMHO, a hilarious video featuring people trading in old stuff for new, like a car, a wallet, and a couch! I wish I could post it.
Thanks for all the help, I'm really getting on board with open source!

---

### Post by oldos2er on 2019-03-29
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It helps others find this solution if they need it.

---

