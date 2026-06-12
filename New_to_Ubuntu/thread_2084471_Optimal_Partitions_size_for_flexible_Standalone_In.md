---
title: "Optimal Partitions size for flexible Standalone Install 12.04"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by biswas on 2012-11-15
OK, I am getting there, I have tried Ubuntu on a live CD (without a Hard Drive in the laptop) and I like what I see.

I am planning to install Ubuntu 12.04 on a brand new 320GB HDD without Windows.

Yesterday **Bucky Ball** gave me this advice re installing Ubuntu:

[I]"For a manual partition, normal is:

/ = root partition, where the OS goes, 15-20Gb plenty;
/home = where your documents, vids, music, etc will go, large as you like;
/swap = same as Windows pagefile, 2Gb is fine, at end of disk or end of install.

That's it. Depending on your hardware, install can be a breeze or not. If things run fine from the CD, that is a good sign."[/I]

My Question is this:

[LIST]
[*]Is it advisable to leave some "free space" on the drive? 
[*]If I may want to install and test (play with) another version of Ubuntu later, should I create another partition for that purpose now?
[*]In my reading I see that some people have /var /tmp /data and other partitions - some as many as 10. What is the advantage of this?
[*]Can free space that is left at the install be used later for further partitions without disturbing the original  / /home and /swap?
[/LIST]

I would like the option of doing another install to this disk at some point in the future with as little hassle as possible. Shoud I create a /var partition?

Also, When Bucky Ball says to add the /swap partition at the end of the disk or the end of the install, what does this mean exactly? In this [Softpedia Article]("http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml") It says to create */swap* first, then */home* then */*

Thanks

---

### Post by jerome1232 on 2012-11-15
It's a whole lot of user prefrence and what your going to do with it. Everyone does it slighlty different, I kinda think you should just go with a big fat / a swap partition and leave it at that, definitly don't do more than /, /home, and swap, anything more and it's for very specific, speacilized reasons mostly not applicalbe to your standard destkop.

As for end of the disk begining of the disk. The begining of your disc is faster than the end of your disk, I would put my root at the begining, home middle swap at the end, you hardly ever dive into swap anyways.

I have to run to class and can't really address anything else at the moment.

---

### Post by Mr_JMM on 2012-11-15
Just /root (/root2) /home and /swap will be fine. The others aren't required unless you're running a server.

If you want to play then yes, set up a few spaces for root. 15-20GB each. Using an extended partition will help with later editing of partitions.

Make swap a primary partition. Maybe the main OS /root as primary too. THen in the extended put the other root partitions and home partition. Possibly not required unless you think you'll want more than two partitions for distros.

---

### Post by biswas on 2012-11-15
Ok, Thanks,

I just wanted to make sure I wasn't missing something.
I will create something like this:

/dev/sda1 - **/** - 20GB
/dev/sda2 - **/root2** - 20GB
/dev/sda3 - **/home**  - 260GB
/dev/dsa4 - **/swap**  - 4GB 

Make sense?

---

### Post by jerome1232 on 2012-11-15
Instead of a seperate home, I'd make a data partition, just for data, sharing home between distros or versions can cause problems

---

### Post by Mr_JMM on 2012-11-15
> **biswas said:**
> Ok, Thanks,

I just wanted to make sure I wasn't missing something.
I will create something like this:

/dev/sda1 - **/** - 20GB
/dev/sda2 - **/root2** - 20GB
/dev/sda3 - **/home**  - 260GB
/dev/dsa4 - **/swap**  - 4GB 

Make sense?
Yep, that would work.


> **jerome1232 said:**
> Instead of a seperate home, I'd make a data partition, just for data, sharing home between distros or versions can cause problems
Not wishing to argue with you but that goes against a lot of what I've been reading recently. The census seems to be that separate /data is a Windows thing and /home is Linux. You can happily run one home partition as long as you use separate usernames for each distro. I have several machines, some run four *buntu distros including a Linux Mint 14 and another with Ubuntu, Fedora and OpenSuse, all playing along nicely and that was before I had separate home folders for each distro e.g. /home/ubuntu/jimmy /home/fedora/jimmym etc.
but again, I don't mean to argue, I'm relatively noobish, so please do correct me if necessary. Maybe it's just personal experience / preference...

---

### Post by jerome1232 on 2012-11-15
> **Mr_JMM said:**
> Yep, that would work.



Not wishing to argue with you but that goes against a lot of what I've been reading recently. The census seems to be that separate /data is a Windows thing and /home is Linux. You can happily run one home partition as long as you use separate usernames for each distro.different user names would work. I am under the impression that a separate home was to share the data between os's which can be easier accomplished in my opinion with a data partition and symlinks from users home folders into the data partition. 

Like I said though, user preference, there are a variety of ways to accomplish these things.

---

### Post by Mr_JMM on 2012-11-15
> **jerome1232 said:**
> different user names would work. I am under the impression that a separate home was to share the data between os's which can be easier accomplished in my opinion with a data partition and symlinks from users home folders into the data partition.

If I may, I'd like to ask more about this in the guise that the OP will learn something too... *ahem*

I'm actually liking your idea; I've never thought about the idea of sharing data across os's before, mainly because my other OS's are just a playground. Perhaps both methods combined would suit. A separate /home because it makes life easier with upgrades / fresh plus /data for sharing. Thanks for that.

---

### Post by Dennis N on 2012-11-15
> **biswas said:**
> Ok, Thanks,

I just wanted to make sure I wasn't missing something.
I will create something like this:

/dev/sda1 - **/** - 20GB
/dev/sda2 - **/root2** - 20GB
/dev/sda3 - **/home**  - 260GB
/dev/dsa4 - **/swap**  - 4GB 

Make sense?

If you intend to expand with additional Linux OSes, you need to make an extended partition in here. In an MSDOS partition table there is a maximum of 4 primary partitions (1-4); one of those can instead be extended.

Suggestion:

/sda1 = primary partition for Ubuntu, mounted as /
/sda2 = extended partition using remainder of disk containing:
/sda5 = your swap partition (generally = size of RAM),
/sda6 to /sdax = logical partition(s) which can be added later one at a time without modifying what is already in place. These contain future installs of other Linux distros.

If you want a separate home partition, /sda6 can be used for that. All the linux OSes can use the same swap.

---

### Post by biswas on 2012-11-15
OK Well,

Lots to think about. I love posting here because the answers invariably tend to provide fertile ground for more research (read:  [I]educating myself./I])

One final ask: Which of these schemes will provide the best performance? - Or will it matter at all?

---

### Post by dFlyer on 2012-11-15
You can have a many extended partitions as you wish. My choice of a setup is:

/: 30 gig
/home: 280 gig
/swap: 8 gig

You really don't need anything more unless your running a server.

---

### Post by Dennis N on 2012-11-15
> **biswas said:**
> One final ask: Which of these schemes will provide the best performance? - Or will it matter at all?

Maybe there would be a slight difference, but I doubt you would be able to notice.

---

### Post by jerome1232 on 2012-11-15
> **biswas said:**
> OK Well,

Lots to think about. I love posting here because the answers invariably tend to provide fertile ground for more research (read:  [I]educating myself./I])

One final ask: Which of these schemes will provide the best performance? - Or will it matter at all?
[B]
Typically[/B] won't matter at all.


However that's actually one, of many reasons that advanced users or system admins might make a special partition with a specific file-system or the same file-system tuned to specific needs (Like a mail or newsfeed server deals with thousands upon thousands of small files, and so will want the partition that holds those files to be optimized for that task)

Perhaps more typical a standard desktop with 2 disks, one an ssd, my opt to have his root, or maybe even his home on the ssd, but seperate out a large data or home partion on a second traditional disk. This way you get the performance of the ssd for your system, while retaining a large amount of storage space for media on the traditional disk.

---

### Post by audiomick on 2012-11-15
My two cents. I have an SSD drive in my desktop for the / partition, the theory being that it will boot quicker and run snappier. I reckon this is the case.

I think about 15-20 GB for / is generous enough by current standards. I can remember when, a few years ago, 10 was more than enough.

If you want the hibernate function to work right, you should make your swap a bit bigger than the amount of RAM you have. Hibernate writes the contents of the RAM to the swap partition, and never worked for me until I had a bigger swap than the RAM.

---

### Post by BertN45 on 2012-11-15
I would never put the SWAP partition at the end, it is small so it does not require much space and if you need it e.g. using virtual box/virtual machines, it is essential that it is as fast as possible. I propose
1. Root 15GB
2. Swap, same size as RAM memory.
3. Reserved for any other OS 35GB (Enough for e.g. Windows 8 )
4. Extended Partition, the remainder of the disk
4.1. Data the remainder of the disk, but you could keep 15GB reserved at the end, it is relatively easy to add it to the data partition if needed and it could be nice for another Linux OS, like the development version 13.04.

---

### Post by biswas on 2012-11-16
Thank You all for your ideas. I will consider carefully.

---

