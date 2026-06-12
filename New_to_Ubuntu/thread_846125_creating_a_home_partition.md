---
title: "creating a /home partition"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by scotcella on 2008-07-01
Okay, I would like organise my home partition, but I'm not really sure about how much space I need to have for the partitions and what they should be called. I have been reading up about it but I'm trying to get my head around it- still a bit fuzzy, so this post might help me to think out loud.

My laptop is dual booted with Vista and Hardy- 80GB each. I said previously, I have done some research but there are some things I'm a little fuzzy about, so would appreciate some feedback from people who have had more experience in these matters. I've done fresh installations etc many times, this is my first attempt to resize partitions and making a separate /home partition.

One of the reading up on materials I have been looking at is [psychocats.net]("http://www.psychocats.net/ubuntu/partitioning.") on partitioning. 

I don't want to have a shared drive /home partition with Vista/Ubuntu.
I use Vista very occasionally for work purposes- mostly screenshots etc, so I don't save any docs or files there, all my work files are saved onto a portable HDD and taken to work.

Personal files are saved in Ubuntu or on another portable HDD for backup in case hell breaks loose. So  I would like to have 40GB for the /home partition. 

Which leaves me with the other bits like swap and ext3 or what ever it is called. But I don't know what I'm supposed to name them and how big they should be.

Any feedback is appreciated, many thanks in advance.

---

### Post by drs305 on 2008-07-01
The general consensus (if there is such a thing) is 10-15GB for / (root), 2 times your ram for the /swap, and the rest for /home.

If you are installing or reinstalling, you have to have a root / and a /swap partition. During the install you can also create the /home partition - when the install gets to partitioning, choose to set up your partitions manually.

---

### Post by Claus7 on 2008-07-01
Hello,

this I think should solve many of your queries:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Regards!

---

### Post by nick_h on 2008-07-01
> Which leaves me with the other bits like swap and ext3 or what ever it is called. But I don't know what I'm supposed to name them and how big they should be.
You should generally allocate a swap partition of between 1.5 and 2.5 times the amount of pysical ram.  This will depend on the amount of ram you have and what you will be using your machine for.

10GB should be OK for your root partition.  Use the remainder for /home.

The root and /home partitions will be ext3.  You don't have to name the partitions.

---

### Post by Tatty on 2008-07-01
If you have already installed Ubuntu then the installer should have created a swap partition for you.  But if you do need to create one manually It is usually recommended to make it 2x or 3x the size of your RAM.

Usually you want at least 10Gb for the root partition, although This really does depend on how much software you plan on installing to it.  My root currently has a 14Gb partition with 9Gb free.

As home is where you will be storing your documents,videos,songs,etc. you will want to make this large, But you could probably figure out how large you need it based on what you do.

I used that psychocats tutorial to create a separate home partition on my laoptop once. I did encounter one small problem after it though which i was able to rectify, as a lot of the file ownerships got messed up. 
So afterwards I had to chown all the files back to me.  After that I had to search through the backup home folder (keep your backups until everything works fine!) for any file which were owned by root, then chown them back to root in my new home folder.

To find all files owned by root simply cd to your old home directory and run ```
ls -lR | grep root
```

---

### Post by scotcella on 2008-07-01
Thanks everyone for your replies!!!

Still getting around it, I think i have a better understanding now.

How do i know the partition sizes and how big they are. Is there a way I can find out via the terminal?

---

### Post by nick_h on 2008-07-01
> How do i know the partition sizes and how big they are. Is there a way I can find out via the terminal?
You can list all your partitions with:
```
sudo fdisk -l
```
If you want to see usage and mount points use:
```
df -h
```

---

### Post by Tatty on 2008-07-01
```
sudo fdisk -l
```  Will show you in a CLI.

---

### Post by scotcella on 2008-07-01
> **drs305 said:**
> The general consensus (if there is such a thing) is 10-15GB for / (root), 2 times your ram for the /swap, and the rest for /home.

If you are installing or reinstalling, you have to have a root / and a /swap partition. During the install you can also create the /home partition - when the install gets to partitioning, choose to set up your partitions manually.

Okay, after reading all the posts, thank you to everyone that responded to my enquiries. I appreciate the help.

So; working with 80GB for my ubuntu partition- my thinking is,

/ (root) it will be 15GB
/swap will be 25GB

which leaves me with 40GB for /home.

Does this sound about right? I'm still trying to get my maths and head around the paritions and division of the numbers. Sorry if I sound so blond! :lolflag:

---

### Post by a fenderson on 2008-07-01
25 gb swap is way too much.  Try 1-2 gb.

---

### Post by drs305 on 2008-07-01
a fenderson is correct. make your swap no larger than 2gb and increase /home. other than that, your plan looks correct. and when you are setting up your partitions, put the swap partition at the 'end'. it's one of the things the ubuntu setup will ask.

---

### Post by Hooya on 2008-07-01
And just so you are aware, ext3 is a type of file system you can use for your / and /home partitions, it's not a partition label in and of itself.  They're options in the Linux world of fat32 and NTFS.  You should use ext2 or ext3 for those partitions.  Swap gets its own file system type.

---

### Post by nick_h on 2008-07-02
> make your swap no larger than 2gb
If it is a desktop PC with 2GB or less of RAM then I would agree.  If the OP requires hibernate functionality then they will have to have as much swap space as memory.

---

